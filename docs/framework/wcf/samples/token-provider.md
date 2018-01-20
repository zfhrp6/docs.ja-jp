---
title: "トークン プロバイダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bd6b0983dcb4a0f7cdbabc5b391cca2000f9d16d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="token-provider"></a><span data-ttu-id="07d0f-102">トークン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="07d0f-102">Token Provider</span></span>
<span data-ttu-id="07d0f-103">このサンプルでは、カスタム トークン プロバイダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="07d0f-104">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のトークン プロバイダーは、資格情報をセキュリティ インフラストラクチャに提供するために使用します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="07d0f-105">一般的に、トークン プロバイダーは、ターゲットをチェックし、適切な証明書を発行して、セキュリティ インフラストラクチャがメッセージのセキュリティを保護できるようにします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="07d0f-106"> には、既定の Credential Manager Token Provider が付属しています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-106"> ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="07d0f-107">また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、[!INCLUDE[infocard](../../../../includes/infocard-md.md)] トークン プロバイダーも付属しています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="07d0f-108">カスタム トークン プロバイダーは、次の場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="07d0f-109">トークン プロバイダーが連携動作できない資格情報ストアがある場合。</span><span class="sxs-lookup"><span data-stu-id="07d0f-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="07d0f-110">資格情報をユーザーが詳細を提供した時点から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント フレームワークが資格情報を使用した時点に変換するための、独自のカスタム メカニズムを提供する場合。</span><span class="sxs-lookup"><span data-stu-id="07d0f-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="07d0f-111">カスタム トークンを構築している場合。</span><span class="sxs-lookup"><span data-stu-id="07d0f-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="07d0f-112">このサンプルでは、ユーザーの入力を別の形式に変換するカスタム トークン プロバイダーを構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>  
  
 <span data-ttu-id="07d0f-113">このサンプルに示されている手順の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="07d0f-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="07d0f-114">クライアントがユーザー名/パスワードの組み合わせを使用して認証する方法。</span><span class="sxs-lookup"><span data-stu-id="07d0f-114">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="07d0f-115">クライアントをカスタム トークン プロバイダーを使用して構成する手順。</span><span class="sxs-lookup"><span data-stu-id="07d0f-115">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="07d0f-116">サーバーが、ユーザー名とパスワードが一致していることを検証するカスタム <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> とパスワードを使用して、クライアント資格情報を検証する手順。</span><span class="sxs-lookup"><span data-stu-id="07d0f-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>  
  
-   <span data-ttu-id="07d0f-117">サーバーがクライアントによってサーバーの X.509 証明書を使用して認証される手順。</span><span class="sxs-lookup"><span data-stu-id="07d0f-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="07d0f-118">さらにこのサンプルでは、カスタム トークン認証システムの処理後に、呼び出し元の ID にアクセスするための方法も示します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="07d0f-119">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは App.config 構成ファイルで定義します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="07d0f-120">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="07d0f-121">バインディングの構成には、標準の `wsHttpBinding` が使用されます。これは既定でメッセージ セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="07d0f-122">このサンプルは、クライアント ユーザー名認証を使用するように標準の `wsHttpBinding`を設定します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="07d0f-123">また、サービスは serviceCredentials 動作を使用してサービス証明書の構成も行います。</span><span class="sxs-lookup"><span data-stu-id="07d0f-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="07d0f-124">serviceCredentials 動作を使用すると、サービス証明書を構成できます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="07d0f-125">クライアントはサービス証明書を使用して、サービスを認証し、メッセージを保護します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="07d0f-126">次の構成では、次のセットアップ手順で説明しているサンプル セットアップでインストールされる localhost 証明書を参照しています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="07d0f-127">クライアント エンドポイント構成は、構成名、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="07d0f-128">クライアント バインディングは、適切な `Mode` およびメッセージ `clientCredentialType` で構成されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="http://localhost:8000/servicemodelsamples/service"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator">  
    </endpoint>  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="07d0f-129">カスタム トークン プロバイダーを開発して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティ フレームワークに統合する方法を、次の手順に示します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-129">The following steps show how to develop a custom token provider and integrate it with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security framework:</span></span>  
  
1.  <span data-ttu-id="07d0f-130">カスタム トークン プロバイダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-130">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="07d0f-131">サンプルでは、ユーザー名とパスワードを取得するカスタム トークン プロバイダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="07d0f-132">パスワードは、このユーザー名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-132">The password must match this username.</span></span> <span data-ttu-id="07d0f-133">このカスタム トークン プロバイダーは、デモンストレーション用にのみ作成されたものです。実環境に展開することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="07d0f-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>  
  
     <span data-ttu-id="07d0f-134">このタスクを実行するため、カスタム トークン プロバイダーは <xref:System.IdentityModel.Selectors.SecurityTokenProvider> クラスを派生し、<xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="07d0f-135">このメソッドは、新しい `UserNameSecurityToken` を作成して返します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>  
  
    ```  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
        // obtain username and password from the user using console window  
        string username = GetUserName();  
        string password = GetPassword();  
        Console.WriteLine("username: {0}", username);  
  
        // return new UserNameSecurityToken containing information obtained from user  
        return new UserNameSecurityToken(username, password);  
    }  
    ```  
  
2.  <span data-ttu-id="07d0f-136">カスタム セキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-136">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="07d0f-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> は、特定の <xref:System.IdentityModel.Selectors.SecurityTokenProvider> (<xref:System.IdentityModel.Selectors.SecurityTokenRequirement> メソッドで渡されます) に対する `CreateSecurityTokenProvider` を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="07d0f-138">セキュリティ トークン マネージャーは、トークン認証システムとトークン シリアライザーの作成にも使用されますが、このサンプルでは扱っていません。</span><span class="sxs-lookup"><span data-stu-id="07d0f-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="07d0f-139">このサンプルでは、カスタム セキュリティ トークン マネージャーは <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> クラスを継承し、渡されたトークンの要件でユーザー名プロバイダーが必要であることが示されている場合に、`CreateSecurityTokenProvider` メソッドをオーバーライドして、カスタムのユーザー名トークン プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>  
  
    ```  
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager  
    {  
        MyUserNameClientCredentials myUserNameClientCredentials;  
  
        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)  
            : base(myUserNameClientCredentials)  
        {  
            this.myUserNameClientCredentials = myUserNameClientCredentials;  
        }  
  
        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)  
        {  
            // if token requirement matches username token return custom username token provider  
            // otherwise use base implementation  
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)  
            {  
                return new MyUserNameTokenProvider();  
            }  
            else  
            {  
                return base.CreateSecurityTokenProvider(tokenRequirement);  
            }  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="07d0f-140">カスタム クライアント資格情報を作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-140">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="07d0f-141">クライアント資格情報クラスは、クライアント プロキシ用に構成された資格情報を表すために使用され、トークン認証システム、トークン プロバイダー、およびトークン シリアライザーの取得に使用されるセキュリティ トークン マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>  
  
    ```  
    public class MyUserNameClientCredentials : ClientCredentials  
    {  
        public MyUserNameClientCredentials()  
            : base()  
        {  
        }  
  
        protected override ClientCredentials CloneCore()  
        {  
            return new MyUserNameClientCredentials();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            // return custom security token manager  
            return new MyUserNameSecurityTokenManager(this);  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="07d0f-142">カスタム クライアント資格情報を使用するようクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-142">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="07d0f-143">クライアントがカスタム クライアント資格情報を使用するため、サンプルでは既定のクライアント資格情報を削除し、新しいクライアント資格情報クラスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
    static void Main()  
    {  
        // ...  
           // Create a client with given client endpoint configuration  
          CalculatorClient client = new CalculatorClient();  
  
          // set new credentials  
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));  
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());  
       // ...  
    }  
    ```  
  
 <span data-ttu-id="07d0f-144">サービス側で呼び出し元の情報を表示するには、次のコード例に示すように <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="07d0f-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> には、現在のユーザーに関する情報が保持されています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 <span data-ttu-id="07d0f-146">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="07d0f-147">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-147">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="07d0f-148">セットアップ バッチ ファイル</span><span class="sxs-lookup"><span data-stu-id="07d0f-148">Setup Batch File</span></span>  
 <span data-ttu-id="07d0f-149">このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="07d0f-150">このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="07d0f-151">次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="07d0f-152">サーバー証明書の作成。</span><span class="sxs-lookup"><span data-stu-id="07d0f-152">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="07d0f-153">Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="07d0f-154">`%SERVER_NAME%` 変数はサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="07d0f-155">この変数を変更して、使用するサーバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="07d0f-156">このバッチ ファイルでの既定値は localhost です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-156">The default value in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="07d0f-157">クライアントの信頼された証明書ストアへのサーバー証明書のインストール。</span><span class="sxs-lookup"><span data-stu-id="07d0f-157">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="07d0f-158">Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="07d0f-159">この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。</span><span class="sxs-lookup"><span data-stu-id="07d0f-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="07d0f-160">マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="07d0f-161">Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="07d0f-162">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="07d0f-163">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="07d0f-164">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="07d0f-164">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="07d0f-165">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="07d0f-166">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="07d0f-167">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="07d0f-167">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="07d0f-168">管理特権で [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-168">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="07d0f-169">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-169">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07d0f-170">Setup.bat バッチ ファイルは、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-170">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="07d0f-171">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプト内で設定された PATH 環境変数は、Setup.bat スクリプトで必要な実行可能ファイルが格納されているディレクトリを指しています。</span><span class="sxs-lookup"><span data-stu-id="07d0f-171">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="07d0f-172">service.exe を \service\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="07d0f-173">Client.exe を \client\bin で起動します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="07d0f-174">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="07d0f-175">username プロンプトに対してユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="07d0f-176">password プロンプトに対して、username プロンプトで入力したものと同じ文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="07d0f-177">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-177">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="07d0f-178">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="07d0f-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="07d0f-179">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="07d0f-180">サービス プログラム ファイルを、サービス コンピューターのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="07d0f-181">Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="07d0f-182">コンピューターの完全修飾ドメイン名を含むサブジェクト名を持つサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="07d0f-183">新しい証明書名を反映するには、Service.exe.config ファイルを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="07d0f-184">サーバー証明書を作成するには、Setup.bat バッチ ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="07d0f-185">setup.bat ファイルは、管理特権を使用して開いた Visual Studio コマンド プロンプトから実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="07d0f-186">`%SERVER_NAME%` 変数には、サービスをホストするコンピューターの完全修飾ホスト名を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07d0f-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="07d0f-187">サーバー証明書をクライアントの CurrentUser-TrustedPeople ストアにコピーします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="07d0f-188">この操作は、サーバー証明書の発行元をクライアントが信頼できる場合は不要です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="07d0f-189">サービス コンピューターの Service.exe.config ファイルで、ベース アドレスの値を localhost から完全修飾コンピューター名に変更します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="07d0f-190">サービス コンピューターで、コマンド プロンプトから service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="07d0f-191">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="07d0f-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="07d0f-192">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="07d0f-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="07d0f-193">クライアント コンピューターで、コマンド プロンプト ウィンドウから `Client.exe` を起動します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="07d0f-194">クライアントとサービスできない場合は通信するためを参照してください。[トラブルシューティングのヒント](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b)です。</span><span class="sxs-lookup"><span data-stu-id="07d0f-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="07d0f-195">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="07d0f-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="07d0f-196">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="07d0f-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d0f-197">参照</span><span class="sxs-lookup"><span data-stu-id="07d0f-197">See Also</span></span>
