---
title: "WS 2007 フェデレーション HTTP バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b04984ad1e21da4bc86760046029d3b94b70758
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="cadcf-102">WS 2007 フェデレーション HTTP バインディング</span><span class="sxs-lookup"><span data-stu-id="cadcf-102">WS 2007 Federation HTTP Binding</span></span>
<span data-ttu-id="cadcf-103">このサンプルでは、<xref:System.ServiceModel.WS2007FederationHttpBinding> の使用例を示します。これは、WS-Trust 仕様のバージョン 1.3 に対応したフェデレーション シナリオを構築するための標準のバインディングです。</span><span class="sxs-lookup"><span data-stu-id="cadcf-103">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cadcf-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cadcf-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cadcf-105">このサンプルは、コンソール ベースのプログラム (Client.exe)、コンソール ベースのセキュリティ トークン サービス プログラム (Securitytokenservice.exe)、およびコンソール ベースのサービス プログラム (Service.exe) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="cadcf-105">The sample consists of a console-based client program (Client.exe), a console-based security token service program (Securitytokenservice.exe), and a console-based service program (Service.exe).</span></span> <span data-ttu-id="cadcf-106">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-106">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="cadcf-107">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (`Add`、`Subtract`、`Multiply`、`Divide`) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="cadcf-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="cadcf-108">クライアントは、セキュリティ トークンをセキュリティ トークン サービス (STS) から取得し、指定された算術演算を実行する同期要求をサービスに対して行います。</span><span class="sxs-lookup"><span data-stu-id="cadcf-108">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="cadcf-109">サービスが応答し、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-109">The service then replies with the result.</span></span> <span data-ttu-id="cadcf-110">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-110">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="cadcf-111">このサンプルは、`ICalculator` 要素を使用して `ws2007FederationHttpBinding` コントラクトを利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cadcf-111">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="cadcf-112">このバインディングのクライアント側の構成は、次のコードに示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="cadcf-112">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="cadcf-113">[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)、`security`値は、どのセキュリティ モードを使用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-113">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="cadcf-114">このサンプルで`message`セキュリティを使用すると、その理由は、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)内側で指定されて、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="cadcf-114">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="cadcf-115">[\<発行者 >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)内の要素、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)クライアントが実行できるように、クライアントに、セキュリティ トークンを発行する STS のバインディングとアドレスを指定します認証、`ICalculator`サービス。</span><span class="sxs-lookup"><span data-stu-id="cadcf-115">The [\<issuer>](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>  
  
 <span data-ttu-id="cadcf-116">このバインディングのサービス側の構成は、次のコードに示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="cadcf-116">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="cadcf-117">[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)、`security`値は、どのセキュリティ モードを使用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-117">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="cadcf-118">このサンプルで`message`セキュリティを使用すると、その理由は、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)内側で指定されて、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="cadcf-118">In this sample, `message` security is used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="cadcf-119">[ \<IssuerMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)要素の`ws2007FederationHttpBinding`内、 [\<メッセージ >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md)アドレスと取得に使用できるエンドポイントの id を指定しますSTS のメタデータ。</span><span class="sxs-lookup"><span data-stu-id="cadcf-119">The [\<issuerMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>  
  
 <span data-ttu-id="cadcf-120">このサービスの動作を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-120">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="cadcf-121">[ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> により、サービス クライアントが認証時に提示できるトークンに関する制約を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-121">The [\<issuedTokenAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="cadcf-122">この構成の指定では、サブジェクト名が CN=STS である証明書によって署名されたトークンがサービスによって受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-122">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="cadcf-123">STS は、標準の <xref:System.ServiceModel.WS2007HttpBinding> を使用して、単一のエンドポイントを利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cadcf-123">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="cadcf-124">このサービスは、クライアントからのトークンの要求に応答し、</span><span class="sxs-lookup"><span data-stu-id="cadcf-124">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="cadcf-125">クライアントが Windows アカウントを使用して認証されている場合は、クライアントのユーザー名がクレームとして含まれているトークンを発行します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-125">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="cadcf-126">STS は、トークン作成の一環として、CN=STS 証明書に関連付けられている秘密キーを使用して、トークンに署名します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-126">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="cadcf-127">また、対称キーを作成し、CN=localhost 証明書に関連付けられている秘密キーを使用して暗号化します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-127">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="cadcf-128">STS は、トークンをクライアントに返すときに、対称キーも返します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-128">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="cadcf-129">クライアントは、発行されたトークンを `ICalculator` サービスに提示し、対称キーを使用してメッセージに署名することで対称キーを認識していることを証明します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-129">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
 <span data-ttu-id="cadcf-130">サンプルを実行すると、セキュリティ トークン要求が STS のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-130">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="cadcf-131">操作要求と応答は、クライアントとサービスのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-131">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="cadcf-132">いずれかのコンソール ウィンドウで Enter キーを押すと、アプリケーションがシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="cadcf-132">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
 `Add(100,15.99) = 115.99`  
  
 `Subtract(145,76.54) = 68.46`  
  
 `Multiply(9,81.25) = 731.25`  
  
 `Divide(22,7) = 3.14285714285714`  
  
 `Press <ENTER> to terminate client.`  
  
 <span data-ttu-id="cadcf-133">このサンプルに用意されている Setup.bat ファイルを使用すると、適切な証明書を使用してサーバーと STS を構成し、自己ホスト型アプリケーションを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cadcf-133">The Setup.bat file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="cadcf-134">このバッチ ファイルにより、LocalMachine/TrustedPeople 証明書ストアに 2 つの証明書が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-134">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="cadcf-135">片方の証明書は CN=STS のサブジェクト名を持ち、クライアントに発行するセキュリティ トークンを署名するために STS が使用します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-135">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="cadcf-136">もう片方の証明書は CN=localhost のサブジェクト名を持ち、サービスが暗号化を解除できるようにシークレットを暗号化するために STS が使用します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-136">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cadcf-137">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="cadcf-137">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cadcf-138">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="cadcf-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cadcf-139">管理特権を使用して Visual Studio コマンド プロンプトを開き、Setup.bat ファイルを実行して必要な証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="cadcf-139">Open a Visual Studio command prompt with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>  
  
 <span data-ttu-id="cadcf-140">このバッチ ファイルでは、Windows SDK と共に配布される Certmgr.exe および Makecert.exe が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-140">This batch file uses Certmgr.exe and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="cadcf-141">ただし、スクリプトでこれらのツールを見つけるには、Visual Studio のコマンド プロンプト内から Setup.bat を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cadcf-141">However, you must run Setup.bat from within a Visual Studio  command prompt to enable the script to find these tools.</span></span>  
  
1.  <span data-ttu-id="cadcf-142">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="cadcf-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="cadcf-143">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="cadcf-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="cadcf-144">使用している場合[!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]Service.exe、Client.exe を実行する必要があります、および SecurityTokenService.exe をシステム特権 (ファイルを右クリックし、をクリックして**管理者として実行**)。</span><span class="sxs-lookup"><span data-stu-id="cadcf-144">If you are using [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must run Service.exe, Client.exe, and SecurityTokenService.exe with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cadcf-145">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="cadcf-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cadcf-146">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cadcf-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cadcf-147">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="cadcf-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cadcf-148">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cadcf-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a><span data-ttu-id="cadcf-149">参照</span><span class="sxs-lookup"><span data-stu-id="cadcf-149">See Also</span></span>
