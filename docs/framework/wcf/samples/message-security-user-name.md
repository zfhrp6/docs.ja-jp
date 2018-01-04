---
title: "メッセージ セキュリティ ユーザー名"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4df9b3d5c1f073b1b2348220ac1a77efbe797311
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-user-name"></a><span data-ttu-id="ae960-102">メッセージ セキュリティ ユーザー名</span><span class="sxs-lookup"><span data-stu-id="ae960-102">Message Security User Name</span></span>
<span data-ttu-id="ae960-103">このサンプルでは、クライアントのユーザー名認証による WS-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509v3 証明書を使用するサーバー認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae960-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="ae960-104">クライアント/サーバー間のすべてのアプリケーション メッセージは署名され、暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="ae960-105">既定では、クライアントによって提供されるユーザー名とパスワードが、有効な Windows アカウントへのログオンに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="ae960-106">このサンプルがに基づいて、 [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae960-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="ae960-107">このサンプルは、クライアント コンソール プログラム (Client.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (Service.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ae960-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="ae960-108">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="ae960-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae960-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ae960-110">このサンプルでは、さらに次の方法も示します。</span><span class="sxs-lookup"><span data-stu-id="ae960-110">This sample also demonstrates:</span></span>  
  
-   <span data-ttu-id="ae960-111">追加の承認を実行できるようにするための、Windows アカウントへの既定のマッピング。</span><span class="sxs-lookup"><span data-stu-id="ae960-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
-   <span data-ttu-id="ae960-112">サービス コードから呼び出し元の ID 情報にアクセスする方法。</span><span class="sxs-lookup"><span data-stu-id="ae960-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="ae960-113">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル Web.config で定義します。エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="ae960-114">標準バインディングの構成は[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティを使用して既定値です。</span><span class="sxs-lookup"><span data-stu-id="ae960-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="ae960-115">このサンプルでは、標準設定[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)クライアント ユーザー名認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae960-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="ae960-116">この動作により、サービス認証でユーザーの資格情報が使用されることが指定されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="ae960-117">サーバー証明書のサブジェクト名と同じ値を含める必要があります、`findValue`属性、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae960-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ae960-118">クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="ae960-119">クライアント バインディングは、適切な `securityMode` と `authenticationMode` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="ae960-120">複数コンピューターのシナリオで実行する場合は、サービスのエンドポイント アドレスを適切に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae960-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ae960-121">クライアント実装では、使用するユーザー名とパスワードが設定されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-121">The client implementation sets the user name and password to use.</span></span>  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="ae960-122">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ae960-123">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ae960-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="ae960-124">MessageSecurity サンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、証明書ベースのセキュリティを必要とするホスト アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ae960-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="ae960-125">バッチ ファイルの実行には 2 つのモードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ae960-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="ae960-126">バッチ ファイルを単一コンピューター モードで実行するには、コマンド ラインに「`setup.bat`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ae960-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="ae960-127">サービス モードで実行するには、「`setup.bat service`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ae960-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="ae960-128">このサンプルを複数のコンピューターで実行している場合は、このモードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ae960-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="ae960-129">詳細については、このトピック末尾のセットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="ae960-130">次に、バッチ ファイルの各セクションの概要を簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="ae960-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="ae960-131">サーバー証明書の作成</span><span class="sxs-lookup"><span data-stu-id="ae960-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="ae960-132">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="ae960-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="ae960-133">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae960-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="ae960-134">証明書は LocalMachine ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="ae960-135">Setup.bat バッチ ファイルの実行にサービスの引数 (`setup.bat service` など) が使用された場合、%SERVER_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae960-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="ae960-136">それ以外の場合、既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="ae960-136">Otherwise it defaults to localhost.</span></span>  
  
-   <span data-ttu-id="ae960-137">クライアントの信頼された証明書ストアへのサーバー証明書のインストール</span><span class="sxs-lookup"><span data-stu-id="ae960-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="ae960-138">次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="ae960-139">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="ae960-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ae960-140">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="ae960-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="ae960-141">証明書の秘密キーに関する権限の付与</span><span class="sxs-lookup"><span data-stu-id="ae960-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="ae960-142">Setup.bat バッチ ファイルの次の行は、LocalMachine ストアに保存されたサーバー証明書を [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ワーカー プロセス アカウントでアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="ae960-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] worker process account.</span></span>  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ae960-143">英語 (米国) 以外の言語で Windows を使用している場合は、Setup.bat ファイルを編集し、`NT AUTHORITY\NETWORK SERVICE` アカウント名を現在の地域に適した名前に変更してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae960-144">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ae960-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ae960-145">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae960-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ae960-146">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ae960-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="ae960-147">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="ae960-147">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="ae960-148">Makecert.exe と FindPrivateKey.exe が含まれているフォルダーがパスに含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ae960-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2.  <span data-ttu-id="ae960-149">管理特権を使用して Visual Studio コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae960-149">Run Setup.bat from the sample install folder in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ae960-150">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ae960-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ae960-151">Setup.bat バッチ ファイルは、Visual Studio コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="ae960-151">The Setup.bat batch file is designed to be run from a Visual Studio Command Prompt.</span></span> <span data-ttu-id="ae960-152">path 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae960-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="ae960-153">この環境変数は、Visual Studio コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-153">This environment variable is automatically set within a Visual Studio Command Prompt.</span></span>  
  
3.  <span data-ttu-id="ae960-154">サービスへのアクセスを検証します。ブラウザーにアドレス「http://localhost/servicemodelsamples/service.svc」を入力します。</span><span class="sxs-lookup"><span data-stu-id="ae960-154">Verify access to the service using a browser by entering the address http://localhost/servicemodelsamples/service.svc.</span></span>  
  
4.  <span data-ttu-id="ae960-155">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="ae960-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ae960-156">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae960-156">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="ae960-157">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-157">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="ae960-158">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="ae960-158">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="ae960-159">サービス コンピューターにディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae960-159">Create a directory on the service computer.</span></span> <span data-ttu-id="ae960-160">インターネット インフォメーション サービス管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae960-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2.  <span data-ttu-id="ae960-161">サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="ae960-162">ファイルのコピー先が \bin サブディレクトリであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ae960-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="ae960-163">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="ae960-164">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae960-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4.  <span data-ttu-id="ae960-165">クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="ae960-166">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="ae960-167">サーバー上で管理特権を使用して Visual Studio コマンド プロンプトを開き、`setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae960-167">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ae960-168">実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="ae960-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="ae960-169">Web.config を編集して、新しい証明書名 (serviceCertificate 要素の findValue 属性) を反映します。これは、コンピューターの完全修飾ドメイン名と同じです。`.`</span><span class="sxs-lookup"><span data-stu-id="ae960-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7.  <span data-ttu-id="ae960-170">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ae960-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="ae960-171">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="ae960-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="ae960-172">クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae960-172">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="ae960-173">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae960-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="ae960-174">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="ae960-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="ae960-175">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-175">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ae960-176">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="ae960-176">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="ae960-177">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae960-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ae960-178">このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="ae960-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="ae960-179">複数のコンピューターで証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルを実行した場合は、CurrentUser - TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。</span><span class="sxs-lookup"><span data-stu-id="ae960-179">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="ae960-180">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="ae960-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae960-181">参照</span><span class="sxs-lookup"><span data-stu-id="ae960-181">See Also</span></span>
