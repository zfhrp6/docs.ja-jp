---
title: "&lt;netHttpBinding&gt; の &lt;message&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9ee45fe84a7134eea442b19a6f3e123a464cbb5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltnethttpbindinggt"></a><span data-ttu-id="febe1-102">&lt;netHttpBinding&gt; の &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="febe1-102">&lt;message&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="febe1-103">メッセージ レベルのセキュリティの設定を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="febe1-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="febe1-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="febe1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="febe1-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="febe1-105">\<bindings></span></span>  
<span data-ttu-id="febe1-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="febe1-106">\<netHttpBinding></span></span>  
<span data-ttu-id="febe1-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="febe1-107">\<binding></span></span>  
<span data-ttu-id="febe1-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="febe1-108">\<security></span></span>  
<span data-ttu-id="febe1-109">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="febe1-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febe1-110">構文</span><span class="sxs-lookup"><span data-stu-id="febe1-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="febe1-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="febe1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="febe1-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="febe1-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="febe1-113">属性</span><span class="sxs-lookup"><span data-stu-id="febe1-113">Attributes</span></span>  
  
|<span data-ttu-id="febe1-114">属性</span><span class="sxs-lookup"><span data-stu-id="febe1-114">Attribute</span></span>|<span data-ttu-id="febe1-115">説明</span><span class="sxs-lookup"><span data-stu-id="febe1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="febe1-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="febe1-116">algorithmSuite</span></span>|<span data-ttu-id="febe1-117">メッセージの暗号化とキー ラップ アルゴリズムを設定します。</span><span class="sxs-lookup"><span data-stu-id="febe1-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="febe1-118">この属性は、アルゴリズムとキー サイズを指定する <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 型です。</span><span class="sxs-lookup"><span data-stu-id="febe1-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="febe1-119">これらのアルゴリズムは、Security Policy Language (WS-SecurityPolicy) の仕様で指定されているアルゴリズムに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="febe1-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="febe1-120">既定値は `Basic256` です。</span><span class="sxs-lookup"><span data-stu-id="febe1-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="febe1-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="febe1-121">clientCredentialType</span></span>|<span data-ttu-id="febe1-122">メッセージ ベースのセキュリティを使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="febe1-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="febe1-123">既定値は、`UserName` です。</span><span class="sxs-lookup"><span data-stu-id="febe1-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="febe1-124">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="febe1-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="febe1-125">値</span><span class="sxs-lookup"><span data-stu-id="febe1-125">Value</span></span>|<span data-ttu-id="febe1-126">説明</span><span class="sxs-lookup"><span data-stu-id="febe1-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="febe1-127">UserName</span><span class="sxs-lookup"><span data-stu-id="febe1-127">UserName</span></span>|<span data-ttu-id="febe1-128">-UserName 資格情報を使用してサーバーにクライアントの認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="febe1-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="febe1-129">この資格情報は、<`clientCredentials`> 要素を使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="febe1-129">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="febe1-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]パスワード ダイジェストの送信、またはパスワードを使用して、そのようなキーを使用して、メッセージ セキュリティのためのキーの派生はサポートしません。</span><span class="sxs-lookup"><span data-stu-id="febe1-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="febe1-131">そのため、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] では UserName 資格情報を使用する場合は、トランスポートが強制的にセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="febe1-131">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="febe1-132">`basicHttpBinding` の場合は、SSL チャネルの設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="febe1-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="febe1-133">証明書</span><span class="sxs-lookup"><span data-stu-id="febe1-133">Certificate</span></span>|<span data-ttu-id="febe1-134">証明書を使用してクライアントをサーバーに認証するように要求します。</span><span class="sxs-lookup"><span data-stu-id="febe1-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="febe1-135">この場合のクライアント資格情報は、<`clientCredentials`> および <`clientCertificate`> を使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="febe1-135">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="febe1-136">さらに、メッセージのセキュリティ モードを使用する場合は、クライアントにサービス証明書を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="febe1-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="febe1-137">ここではサービスの資格情報を使用して指定する必要があります<xref:System.ServiceModel.Description.ClientCredentials>クラスまたは`ClientCredentials`動作要素をサービスを指定することを使用して証明書、 \<serviceCertificate > serviceCredentials の要素。</span><span class="sxs-lookup"><span data-stu-id="febe1-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="febe1-138">子要素</span><span class="sxs-lookup"><span data-stu-id="febe1-138">Child Elements</span></span>  
 <span data-ttu-id="febe1-139">なし</span><span class="sxs-lookup"><span data-stu-id="febe1-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="febe1-140">親要素</span><span class="sxs-lookup"><span data-stu-id="febe1-140">Parent Elements</span></span>  
  
|<span data-ttu-id="febe1-141">要素</span><span class="sxs-lookup"><span data-stu-id="febe1-141">Element</span></span>|<span data-ttu-id="febe1-142">説明</span><span class="sxs-lookup"><span data-stu-id="febe1-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="febe1-143"><`security`> の要素 <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="febe1-143"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="febe1-144"><`netHttpBinding`> 要素のセキュリティ機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="febe1-144">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="febe1-145">例</span><span class="sxs-lookup"><span data-stu-id="febe1-145">Example</span></span>  
 <span data-ttu-id="febe1-146">このサンプルでは、basicHttpBinding とメッセージ セキュリティを使用するアプリケーションを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="febe1-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="febe1-147">サービスの次の構成例では、エンドポイント定義によって basicHttpBinding が指定され、`Binding1` という名前のバインディング構成が参照されます。</span><span class="sxs-lookup"><span data-stu-id="febe1-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="febe1-148">サービスがクライアントに対してサービス自体を認証するために使用する証明書は、`behaviors` 要素の下にある構成ファイルの `serviceCredentials` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="febe1-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="febe1-149">クライアントがサービスに対してクライアント自体を認証するために使用する証明書に適用される検証モードも、`behaviors` 要素の下にある `clientCertificate` セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="febe1-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="febe1-150">同じバインディングとセキュリティの詳細が、クライアントの構成ファイルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="febe1-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="febe1-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="febe1-151">See Also</span></span>  
 [<span data-ttu-id="febe1-152">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="febe1-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="febe1-153">バインディング</span><span class="sxs-lookup"><span data-stu-id="febe1-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="febe1-154">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="febe1-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="febe1-155">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="febe1-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="febe1-156">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="febe1-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
