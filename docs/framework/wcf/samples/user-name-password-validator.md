---
title: "ユーザー名パスワード検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07083d7a92f6b4de68cd1d618d57291f64bef0fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="user-name-password-validator"></a><span data-ttu-id="802f6-102">ユーザー名パスワード検証</span><span class="sxs-lookup"><span data-stu-id="802f6-102">User Name Password Validator</span></span>
<span data-ttu-id="802f6-103">このサンプルでは、カスタム UserNamePassword 検証を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="802f6-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="802f6-104">これは、アプリケーションの要件に適した組み込みの UserNamePassword 検証モードがない場合に便利です。たとえば、ユーザー名とパスワードの組み合わせがデータベースなどの外部ストアに保存されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="802f6-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="802f6-105">このサンプルでは、2 つの特定のユーザー名とパスワードの組み合わせをチェックする、カスタム検証を備えたサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="802f6-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="802f6-106">クライアントはそのようなユーザー名とパスワードの組み合わせを使用して、サービスに対する認証を行います。</span><span class="sxs-lookup"><span data-stu-id="802f6-106">The client uses such a username/password pair to authenticate to the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="802f6-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="802f6-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="802f6-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="802f6-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="802f6-109">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="802f6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="802f6-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
>  <span data-ttu-id="802f6-111">カスタム検証が許可するユーザー名とパスワードの組み合わせを使用する UserName 資格情報は、どのユーザーでも作成できるので、このサービスは、標準の UserNamePassword 検証によって提供される既定の動作よりも安全性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="802f6-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="802f6-112">標準の UserNamePassword 検証は、指定されたユーザー名とパスワードの組み合わせを Windows アカウントにマップするよう試みます。マップできなかった場合は、認証が失敗します。</span><span class="sxs-lookup"><span data-stu-id="802f6-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="802f6-113">このサンプルのカスタム UserNamePassword 検証は、製品版のコードでは使用しないでください。このサンプルは、デモンストレーションのためだけに作成されています。</span><span class="sxs-lookup"><span data-stu-id="802f6-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>  
  
 <span data-ttu-id="802f6-114">このサンプルで示す処理の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="802f6-114">In summary this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="802f6-115">クライアントはユーザー名トークンを使用して認証される。</span><span class="sxs-lookup"><span data-stu-id="802f6-115">The client can be authenticated using a Username Token.</span></span>  
  
-   <span data-ttu-id="802f6-116">サーバーはクライアント資格情報をカスタム UserNamePassword 検証と照合し、カスタム エラーをユーザー名とパスワードの検証ロジックからクライアントに伝達する。</span><span class="sxs-lookup"><span data-stu-id="802f6-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>  
  
-   <span data-ttu-id="802f6-117">サーバーがそのサーバーの X.509 証明書を使用して認証される。</span><span class="sxs-lookup"><span data-stu-id="802f6-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="802f6-118">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (App.config) で定義します。エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="802f6-119">標準バインディングの構成は`wsHttpBinding`WS Securityand ユーザー名認証を使用して既定値です。</span><span class="sxs-lookup"><span data-stu-id="802f6-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Securityand username authentication.</span></span> <span data-ttu-id="802f6-120">サービス動作では、クライアントのユーザー名とパスワードの組み合わせを検証するための `Custom` モード、および検証クラスの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="802f6-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="802f6-121">さらに、`serviceCertificate` 要素を使用しているサーバー証明書も指定します。</span><span class="sxs-lookup"><span data-stu-id="802f6-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="802f6-122">サーバー証明書が同じ値を格納するが、`SubjectName`として、`findValue`で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)です。</span><span class="sxs-lookup"><span data-stu-id="802f6-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <!-- use host/baseAddresses to configure base address provided by host -->  
      <host>  
        <baseAddresses>  
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />  
        </baseAddresses>  
      </host>  
      <!-- use base address specified above, provide one endpoint -->  
      <endpoint address="username"  
                binding="wsHttpBinding"  
                bindingConfiguration="Binding"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- username binding -->  
      <binding name="Binding">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceDebug includeExceptionDetailInFaults ="true"/>  
        <serviceCredentials>  
          <!--   
          The serviceCredentials behavior allows one to   
          specify a custom validator for username/password  
          combinations.  
          -->  
          <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="802f6-123">クライアント エンドポイント構成は、構成名、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="802f6-124">クライアント バインディングは、適切なモードおよびメッセージ `clientCredentialType` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- Username based endpoint -->  
      <endpoint name="Username"  
address="http://localhost:8001/servicemodelsamples/service/username"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding"   
                behaviorConfiguration="ClientCertificateBehavior"  
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- Username binding -->  
        <binding name="Binding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="802f6-125">クライアント実装では、ユーザー名とパスワードの入力がユーザーに対して求められます。</span><span class="sxs-lookup"><span data-stu-id="802f6-125">The client implementation prompts the user to enter a username and password.</span></span>  
  
```  
// Get the username and password  
Console.WriteLine("Username authentication required.");  
Console.WriteLine("Provide a username.");  
Console.WriteLine("   Enter username: (test1)");  
string username = Console.ReadLine();  
Console.WriteLine("   Enter password:");  
string password = "";  
ConsoleKeyInfo info = Console.ReadKey(true);  
while (info.Key != ConsoleKey.Enter)  
{  
    if (info.Key != ConsoleKey.Backspace)  
    {  
        if (info.KeyChar != '\0')  
        {  
            password += info.KeyChar;  
        }  
        info = Console.ReadKey(true);  
    }  
    else if (info.Key == ConsoleKey.Backspace)  
    {  
        if (password != "")  
        {  
            password = password.Substring(0, password.Length - 1);  
        }  
        info = Console.ReadKey(true);  
    }  
}  
for (int i = 0; i < password.Length; i++)  
{  
    Console.Write("*");  
}  
Console.WriteLine();  
// Create a proxy with Certificate endpoint configuration  
CalculatorProxy proxy = new CalculatorProxy("Username")  
try  
{  
  proxy.ClientCredentials.Username.Username = username;  
  proxy.ClientCredentials.Username.Password = password;  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = proxy.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  }  
  catch (Exception e)  
  {  
      Console.WriteLine("Call failed:");  
      while (e != null)  
      {  
          Console.WriteLine("\t{0}", e.Message);  
          e = e.InnerException;  
      }  
      proxy.Abort();  
  }  
}  
```  
  
 <span data-ttu-id="802f6-126">このサンプルではカスタム UserNamePassword 検証を使用して、ユーザー名とパスワードの組み合わせを検証します。</span><span class="sxs-lookup"><span data-stu-id="802f6-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="802f6-127">サンプルは、`CustomUserNamePasswordValidator` から派生する <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="802f6-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="802f6-128">詳細については、<xref:System.IdentityModel.Selectors.UserNamePasswordValidator> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="802f6-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="802f6-129">特定のカスタム検証を使用しているこのサンプルは、2 つの特定のユーザー名とパスワードの組み合わせを許可する `Validate` メソッドを実装しています。次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="802f6-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>  
  
```  
public class CustomUserNameValidator : UserNamePasswordValidator  
{  
 // This method validates users. It allows in two users,  
 // test1 and test2 with passwords 1tset and 2tset respectively.  
 // This code is for illustration purposes only and  
 // MUST NOT be used in a production environment because it  
 // is NOT secure.  
 public override void Validate(string userName, string password)  
 {  
  if (null == userName || null == password)  
  {  
   throw new ArgumentNullException();  
  }  
  
  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))  
  {  
   throw new FaultException("Unknown Username or Incorrect Password");  
   }  
  }  
 }  
```  
  
 <span data-ttu-id="802f6-130">サービス コードに検証を実装した場合、使用する検証インスタンスをサービス ホストに通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="802f6-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="802f6-131">これは次のコードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-131">This is done using the following code.</span></span>  
  
```  
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();  
```  
  
 <span data-ttu-id="802f6-132">または、構成で次のように指定することで、同じことを実現できます。</span><span class="sxs-lookup"><span data-stu-id="802f6-132">Or you can do the same thing in configuration as follows.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="CalculatorServiceBehavior">  
  ...  
   <serviceCredentials>  
    <!--   
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.  
    -->  
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />  
   ...  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="802f6-133">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="802f6-134">クライアントはすべてのメソッドを問題なく呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="802f6-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="802f6-135">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="802f6-135">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="802f6-136">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="802f6-136">Setup Batch File</span></span>  
 <span data-ttu-id="802f6-137">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="802f6-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="802f6-138">このバッチ ファイルは、別のコンピューターを使用する場合または自己ホスト型の場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="802f6-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>  
  
 <span data-ttu-id="802f6-139">次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="802f6-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="802f6-140">サーバー証明書の作成 :</span><span class="sxs-lookup"><span data-stu-id="802f6-140">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="802f6-141">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="802f6-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="802f6-142">%SERVER_NAME% 変数はサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="802f6-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="802f6-143">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="802f6-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="802f6-144">既定値は、localhost です。</span><span class="sxs-lookup"><span data-stu-id="802f6-144">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="802f6-145">サーバー証明書のクライアントの信頼された証明書ストアへのインストール。</span><span class="sxs-lookup"><span data-stu-id="802f6-145">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="802f6-146">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="802f6-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="802f6-147">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="802f6-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="802f6-148">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="802f6-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="802f6-149">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="802f6-149">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="802f6-150">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="802f6-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="802f6-151">サンプルを単一コンピューター構成で実行するか、複数コンピューター構成で実行するかに応じて、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="802f6-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="802f6-152">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="802f6-152">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="802f6-153">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="802f6-153">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt.</span></span> <span data-ttu-id="802f6-154">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="802f6-154">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="802f6-155">Setup.bat バッチ ファイルは、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="802f6-155">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="802f6-156">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルが格納されているディレクトリを指しています。</span><span class="sxs-lookup"><span data-stu-id="802f6-156">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="802f6-157">Service.exe を service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="802f6-157">Launch Service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="802f6-158">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="802f6-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="802f6-159">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-159">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="802f6-160">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="802f6-160">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="802f6-161">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="802f6-161">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="802f6-162">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="802f6-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2.  <span data-ttu-id="802f6-163">サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="802f6-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="802f6-164">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="802f6-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="802f6-165">コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="802f6-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="802f6-166">新しい証明書名を反映するには、サーバーの構成ファイルを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="802f6-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4.  <span data-ttu-id="802f6-167">サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="802f6-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="802f6-168">このようにする必要があるのは、サーバー証明書が信頼できる発行元から発行されていない場合のみです。</span><span class="sxs-lookup"><span data-stu-id="802f6-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="802f6-169">サービス コンピューターの App.config ファイルで、ベース アドレスの値を localhost から完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="802f6-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="802f6-170">サービス コンピューターで、コマンド プロンプト ウィンドウから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="802f6-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7.  <span data-ttu-id="802f6-171">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="802f6-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8.  <span data-ttu-id="802f6-172">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="802f6-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="802f6-173">クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="802f6-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="802f6-174">クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="802f6-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="802f6-175">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="802f6-175">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="802f6-176">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="802f6-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="802f6-177">これにより、証明書ストアからサーバー証明書が削除されます。</span><span class="sxs-lookup"><span data-stu-id="802f6-177">This removes the server certificate from the certificate store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="802f6-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="802f6-178">See Also</span></span>
