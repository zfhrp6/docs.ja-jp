---
title: '&lt;basicHttpBinding&gt; の &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 7f543a91f1d11575df239267a6a8a0b244d99cb3
ms.sourcegitcommit: 378f0e075030239d8259a92a6a0193dd6faf54b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2018
ms.locfileid: "33366048"
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="e1422-102">&lt;basicHttpBinding&gt; の &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="e1422-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="e1422-103">メッセージ レベル セキュリティの設定を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)します。</span><span class="sxs-lookup"><span data-stu-id="e1422-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="e1422-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e1422-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e1422-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e1422-105">\<bindings></span></span>  
<span data-ttu-id="e1422-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e1422-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="e1422-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="e1422-107">\<binding></span></span>  
<span data-ttu-id="e1422-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="e1422-108">\<security></span></span>  
<span data-ttu-id="e1422-109">\<message></span><span class="sxs-lookup"><span data-stu-id="e1422-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1422-110">構文</span><span class="sxs-lookup"><span data-stu-id="e1422-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1422-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e1422-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e1422-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1422-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1422-113">属性</span><span class="sxs-lookup"><span data-stu-id="e1422-113">Attributes</span></span>  
  
|<span data-ttu-id="e1422-114">属性</span><span class="sxs-lookup"><span data-stu-id="e1422-114">Attribute</span></span>|<span data-ttu-id="e1422-115">説明</span><span class="sxs-lookup"><span data-stu-id="e1422-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1422-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="e1422-116">algorithmSuite</span></span>|<span data-ttu-id="e1422-117">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="e1422-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="e1422-118">この属性は、アルゴリズムとキー サイズを指定する <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="e1422-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="e1422-119">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="e1422-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="e1422-120">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="e1422-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="e1422-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e1422-121">clientCredentialType</span></span>|<span data-ttu-id="e1422-122">メッセージ ベースのセキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1422-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="e1422-123">既定値は、`UserName` です。</span><span class="sxs-lookup"><span data-stu-id="e1422-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e1422-124">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="e1422-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e1422-125">値</span><span class="sxs-lookup"><span data-stu-id="e1422-125">Value</span></span>|<span data-ttu-id="e1422-126">説明</span><span class="sxs-lookup"><span data-stu-id="e1422-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1422-127">UserName</span><span class="sxs-lookup"><span data-stu-id="e1422-127">UserName</span></span>|<span data-ttu-id="e1422-128">-ユーザー名資格情報を使用してサーバーにクライアントを認証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1422-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="e1422-129">この資格情報を使用して指定する必要があります、 [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)します。</span><span class="sxs-lookup"><span data-stu-id="e1422-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="e1422-130">WCF は、パスワード ダイジェストの送信、またはパスワードを使用して、このようなキーを使用して、メッセージ セキュリティのためのキーの派生をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1422-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="e1422-131">そのため、WCF トランスポートは、UserName 資格情報を使用する場合にセキュリティで保護することを強制します。</span><span class="sxs-lookup"><span data-stu-id="e1422-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="e1422-132">`basicHttpBinding` の場合は、SSL チャネルの設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1422-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="e1422-133">証明書</span><span class="sxs-lookup"><span data-stu-id="e1422-133">Certificate</span></span>|<span data-ttu-id="e1422-134">証明書を使用してクライアントをサーバーに認証するように要求します。</span><span class="sxs-lookup"><span data-stu-id="e1422-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="e1422-135">ここでクライアント資格情報を使用して指定する必要があります[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)と[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)します。</span><span class="sxs-lookup"><span data-stu-id="e1422-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="e1422-136">さらに、メッセージのセキュリティ モードを使用する場合は、クライアントにサービス証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1422-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="e1422-137">ここでサービス資格情報を使用して指定する必要があります<xref:System.ServiceModel.Description.ClientCredentials>クラスまたは`ClientCredentials`動作の要素と、サービスの指定を使用して証明書の[ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)します。</span><span class="sxs-lookup"><span data-stu-id="e1422-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1422-138">子要素</span><span class="sxs-lookup"><span data-stu-id="e1422-138">Child Elements</span></span>  
 <span data-ttu-id="e1422-139">なし</span><span class="sxs-lookup"><span data-stu-id="e1422-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1422-140">親要素</span><span class="sxs-lookup"><span data-stu-id="e1422-140">Parent Elements</span></span>  
  
|<span data-ttu-id="e1422-141">要素</span><span class="sxs-lookup"><span data-stu-id="e1422-141">Element</span></span>|<span data-ttu-id="e1422-142">説明</span><span class="sxs-lookup"><span data-stu-id="e1422-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1422-143">\<security></span><span class="sxs-lookup"><span data-stu-id="e1422-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="e1422-144">セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)します。</span><span class="sxs-lookup"><span data-stu-id="e1422-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1422-145">例</span><span class="sxs-lookup"><span data-stu-id="e1422-145">Example</span></span>  
 <span data-ttu-id="e1422-146">このサンプルでは、basicHttpBinding とメッセージ セキュリティを使用するアプリケーションを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e1422-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="e1422-147">サービスの次の構成例では、エンドポイント定義によって basicHttpBinding が指定され、`Binding1` という名前のバインディング構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="e1422-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="e1422-148">サービスがクライアントに対してサービス自体を認証するために使用する証明書は、`behaviors` 要素の下にある構成ファイルの `serviceCredentials` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="e1422-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="e1422-149">クライアントがサービスに対してクライアント自体を認証するために使用する証明書に適用される検証モードも、`behaviors` 要素の下にある `clientCertificate` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="e1422-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="e1422-150">同じバインディングとセキュリティの詳細が、クライアントの構成ファイルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="e1422-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1422-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1422-151">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [<span data-ttu-id="e1422-152">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="e1422-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e1422-153">バインディング</span><span class="sxs-lookup"><span data-stu-id="e1422-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e1422-154">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="e1422-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e1422-155">バインドを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="e1422-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e1422-156">\<binding></span><span class="sxs-lookup"><span data-stu-id="e1422-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
