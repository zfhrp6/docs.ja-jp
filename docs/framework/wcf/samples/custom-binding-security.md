---
title: "カスタム バインド セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
caps.latest.revision: "30"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 94c43586606f42cca120ded59637a998d113d229
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="custom-binding-security"></a><span data-ttu-id="a8255-102">カスタム バインド セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a8255-102">Custom Binding Security</span></span>
<span data-ttu-id="a8255-103">このサンプルでは、カスタム バインドを使用してセキュリティを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8255-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="a8255-104">カスタム バインドを使用して、セキュリティで保護されたトランスポートと共にメッセージ レベルのセキュリティを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8255-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="a8255-105">これは、クライアントとサービス間でメッセージを転送する際にセキュリティで保護されたトランスポートが必要であると同時に、そのメッセージをメッセージ レベルでセキュリティ保護する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a8255-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="a8255-106">この構成は、システム指定のバインディングではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a8255-106">This configuration is not supported by system-provided bindings.</span></span>  
  
 <span data-ttu-id="a8255-107">このサンプルは、クライアント コンソール プログラム (EXE) とサービス コンソール プログラム (EXE) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="a8255-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="a8255-108">サービスは、双方向コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="a8255-108">The service implements a duplex contract.</span></span> <span data-ttu-id="a8255-109">このコントラクトは `ICalculatorDuplex` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="a8255-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="a8255-110">`ICalculatorDuplex` インターフェイスを使用することにより、クライアントは算術演算を実行し、セッション経由で実行結果を計算できます。</span><span class="sxs-lookup"><span data-stu-id="a8255-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="a8255-111">サービスは、`ICalculatorDuplexCallback` インターフェイスで結果を個別に返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a8255-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="a8255-112">コンテキストを確立して、クライアントとサービスの間で送信される一連のメッセージを相互に関連付ける必要があるため、二重のコントラクトにはセッションが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8255-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="a8255-113">カスタム バインディングは、双方向通信をサポートしてセキュリティで保護されるよう定義されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-113">A custom binding is defined that supports duplex communication and is secure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8255-114">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8255-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a8255-115">サービス構成では、次をサポートするカスタム バインディングが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-115">The service configuration defines a custom binding that supports the following:</span></span>  
  
-   <span data-ttu-id="a8255-116">TLS/SSL プロトコルを使用して保護される TCP 通信。</span><span class="sxs-lookup"><span data-stu-id="a8255-116">TCP communication protected by using the TLS/SSL protocol.</span></span>  
  
-   <span data-ttu-id="a8255-117">Windows メッセージ セキュリティ。</span><span class="sxs-lookup"><span data-stu-id="a8255-117">Windows message security.</span></span>  
  
 <span data-ttu-id="a8255-118">カスタム バインドの構成により、トランスポートのセキュリティ保護が有効になると同時に、メッセージ レベルのセキュリティも有効になります。</span><span class="sxs-lookup"><span data-stu-id="a8255-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="a8255-119">バインド要素の順序は重要では、カスタム バインディングを定義するため、チャネル スタック内のレイヤーを表します (を参照してください[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md))。</span><span class="sxs-lookup"><span data-stu-id="a8255-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="a8255-120">カスタム バインドはサービスとクライアントの構成ファイルで定義されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8255-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>  
  
```xml  
<bindings>  
  <!-- Configure a custom binding. -->  
  <customBinding>  
    <binding name="Binding1">  
      <security authenticationMode="SecureConversation"  
                 requireSecurityContextCancellation="true">  
      </security>  
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
      <sslStreamSecurity requireClientCertificate="false"/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="a8255-121">カスタム バインドはサービス証明書を使用して、トランスポート レベルでサービスを認証し、クライアントとサービス間で転送中のメッセージを保護します。</span><span class="sxs-lookup"><span data-stu-id="a8255-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="a8255-122">これは `sslStreamSecurity` バインディング要素によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="a8255-123">サービスの証明書は、サービス動作を使用して構成されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8255-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="a8255-124">さらに、カスタム バインディングは Windows 資格情報の種類 (既定の資格情報の種類) によるメッセージ セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8255-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="a8255-125">これは `security` バインディング要素によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="a8255-126">Kerberos 認証機構が利用できる場合は、クライアントとサービスはどちらもメッセージ レベルのセキュリティを使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="a8255-127">サンプルを Active Directory 環境で実行する場合、この認証が行われます。</span><span class="sxs-lookup"><span data-stu-id="a8255-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="a8255-128">Kerberos 認証機構が利用できない場合は、NTLM 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="a8255-129">NTLM はサービスに対してクライアントを認証しますが、クライアントに対するサービスの認証は行いません。</span><span class="sxs-lookup"><span data-stu-id="a8255-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="a8255-130">`security`を使用するバインド要素が構成されている`SecureConversation``authenticationType`、その結果は、クライアントとサービスの両方でセキュリティ セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8255-130">The `security` binding element is configured to use `SecureConversation``authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="a8255-131">これは、サービスの双方向コントラクトを動作させるために必要です。</span><span class="sxs-lookup"><span data-stu-id="a8255-131">This is required to enable the service's duplex contract to work.</span></span>  
  
 <span data-ttu-id="a8255-132">このサンプルを実行する場合は、操作要求および応答はクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="a8255-133">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a8255-133">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="a8255-134">サンプルを実行すると、クライアントに戻ってきたメッセージがサービスから送信されたコールバック インターフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="a8255-135">それぞれの中間結果が表示され、その後にすべての操作が完了したときの数式全体が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="a8255-136">Enter キーを押してクライアントをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="a8255-136">Press ENTER to shut down the client.</span></span>  
  
 <span data-ttu-id="a8255-137">サンプルに用意されている Setup.bat ファイルを使用すると、適切なサービス証明書を使用してクライアントとサーバーを構成し、証明書ベースのセキュリティを必要とするホスト アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a8255-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="a8255-138">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8255-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="a8255-139">次に、このサンプルに適用されるバッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="a8255-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="a8255-140">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="a8255-140">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="a8255-141">Setup.bat ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8255-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="a8255-142">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="a8255-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="a8255-143">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8255-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a8255-144">このバッチ ファイルでのサーバー名の既定は localhost です。</span><span class="sxs-lookup"><span data-stu-id="a8255-144">This batch file defaults the server name to localhost.</span></span>  
  
     <span data-ttu-id="a8255-145">Web ホスト サービスの場合、証明書は CurrentUser ストアに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="a8255-146">クライアントの信頼された証明書ストアへのサーバー証明書のインストール。</span><span class="sxs-lookup"><span data-stu-id="a8255-146">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="a8255-147">Setup.bat ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8255-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a8255-148">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="a8255-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a8255-149">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="a8255-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a8255-150">Setup.bat バッチ ファイルは、Visual Studio 2010 コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="a8255-151">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8255-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a8255-152">この環境変数は、Visual Studio 2010 コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8255-153">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a8255-153">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8255-154">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a8255-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8255-155">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a8255-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a8255-156">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a8255-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a8255-157">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="a8255-157">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="a8255-158">管理特権を使用して Visual Studio コマンド プロンプト ウィンドウを開き、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-158">Open a Visual Studio Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="a8255-159">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a8255-159">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8255-160">Setup.bat バッチ ファイルは、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-160">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="a8255-161">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルが格納されているディレクトリを指しています。</span><span class="sxs-lookup"><span data-stu-id="a8255-161">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="a8255-162">Service.exe を \service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="a8255-162">Launch Service.exe from \service\bin.</span></span>  
  
3.  <span data-ttu-id="a8255-163">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="a8255-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a8255-164">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-164">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="a8255-165">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="a8255-165">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a8255-166">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="a8255-166">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a8255-167">サービス コンピューター上で次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-167">On the service computer:</span></span>  
  
    1.  <span data-ttu-id="a8255-168">サービス コンピューターで、servicemodelsamples という仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8255-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2.  <span data-ttu-id="a8255-169">サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8255-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="a8255-170">ファイルのコピー先が \bin サブディレクトリであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8255-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3.  <span data-ttu-id="a8255-171">Setup.bat ファイルと Cleanup.bat ファイルをサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8255-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4.  <span data-ttu-id="a8255-172">Visual Studio コマンド プロンプトで次のコマンドは、管理者特権で開いた実行:`Setup.bat service`です。</span><span class="sxs-lookup"><span data-stu-id="a8255-172">Run the following command in a Visual Studio command prompt opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="a8255-173">これにより、バッチ ファイルが実行されたコンピューターの名前と一致するサブジェクト名を持つ、サービス証明書が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a8255-174">Setup.bat バッチ ファイルは、Visual Studio 2010 コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="a8255-175">path 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8255-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a8255-176">この環境変数は、Visual Studio 2010 コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="a8255-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>  
  
    5.  <span data-ttu-id="a8255-177">変更、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)前の手順で生成された証明書のサブジェクト名を反映するように Service.exe.config ファイル内で。</span><span class="sxs-lookup"><span data-stu-id="a8255-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>  
  
    6.  <span data-ttu-id="a8255-178">コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="a8255-178">Run Service.exe from a command prompt.</span></span>  
  
2.  <span data-ttu-id="a8255-179">クライアント コンピューター上で次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-179">On the client computer:</span></span>  
  
    1.  <span data-ttu-id="a8255-180">クライアント プログラム ファイルを、\client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8255-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="a8255-181">Cleanup.bat ファイルもコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8255-181">Also copy the Cleanup.bat file.</span></span>  
  
    2.  <span data-ttu-id="a8255-182">Cleanup.bat を実行して、前のサンプルから古い証明書を削除します。</span><span class="sxs-lookup"><span data-stu-id="a8255-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>  
  
    3.  <span data-ttu-id="a8255-183">サービス コンピューターで、管理特権を使用して Visual Studio コマンド プロンプトを開き、次のコマンドを実行して、サービスの証明書をエクスポートします (`%SERVER_NAME%` は、サービスが実行されているコンピューターの完全修飾名に置き換えてください)。</span><span class="sxs-lookup"><span data-stu-id="a8255-183">Export the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer  
        ```  
  
    4.  <span data-ttu-id="a8255-184">%SERVER_NAME%.cer をクライアント コンピューターにコピーします (%SERVER_NAME% は、サービスが実行されているコンピューターの完全修飾名に置き換えてください)。</span><span class="sxs-lookup"><span data-stu-id="a8255-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>  
  
    5.  <span data-ttu-id="a8255-185">クライアント コンピューターで、管理特権を使用して Visual Studio コマンド プロンプトを開き、次のコマンドを実行して、サービスの証明書をインポートします (%SERVER_NAME% は、サービスが実行されているコンピューターの完全修飾名に置き換えてください)。</span><span class="sxs-lookup"><span data-stu-id="a8255-185">Import the service's certificate by opening a Visual Studio command prompt with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>  
  
        ```  
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople  
        ```  
  
         <span data-ttu-id="a8255-186">証明書が信頼できる発行元から発行されている場合は、手順 c.、d.、および e. は不要です。</span><span class="sxs-lookup"><span data-stu-id="a8255-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>  
  
    6.  <span data-ttu-id="a8255-187">次のようにクライアントの App.config ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="a8255-187">Modify the client’s App.config file as follows:</span></span>  
  
        ```xml  
        <client>  
            <endpoint name="default"  
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"   
                binding="customBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"  
        behaviorConfiguration="CalculatorClientBehavior" />  
        </client>  
        ```  
  
    7.  <span data-ttu-id="a8255-188">ドメイン環境でサービスが NetworkService または LocalSystem 以外のアカウントで実行されている場合は、クライアントの App.config ファイル内のサービス エンドポイントのエンドポイント ID を変更し、サービスの実行に使用されているアカウントに基づいて、適切な UPN または SPN を設定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8255-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="a8255-189">エンドポイントの id に関する詳細については、次を参照してください。、[サービス Id と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="a8255-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>  
  
    8.  <span data-ttu-id="a8255-190">コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="a8255-190">Run Client.exe from a command prompt.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a8255-191">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="a8255-191">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="a8255-192">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8255-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8255-193">参照</span><span class="sxs-lookup"><span data-stu-id="a8255-193">See Also</span></span>
