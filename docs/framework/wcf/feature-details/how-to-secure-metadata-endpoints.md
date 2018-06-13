---
title: '方法 : セキュリティで保護されたメタデータ エンドポイント'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 659291975902ec78c1484ac77f898b4486000e8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497179"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="fcbf6-102">方法 : セキュリティで保護されたメタデータ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fcbf6-102">How to: Secure Metadata Endpoints</span></span>
<span data-ttu-id="fcbf6-103">サービスのメタデータには、悪意のあるユーザーに利用される可能性がある、アプリケーションに関する機密情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="fcbf6-104">また、サービスのコンシューマーにも、サービスのメタデータを取得するためのセキュリティで保護された機構が必要です。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="fcbf6-105">したがって、状況に応じて、セキュリティで保護されたエンドポイントを使用してメタデータを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>  
  
 <span data-ttu-id="fcbf6-106">メタデータ エンドポイントは、Windows Communication Foundation (WCF) で定義されているアプリケーション エンドポイントをセキュリティで保護する標準的なセキュリティ メカニズムを使用して一般的に保護されます。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="fcbf6-107">(詳細については、次を参照してください[セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)。)。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-107">(For more information, see [Security Overview](../../../../docs/framework/wcf/feature-details/security-overview.md).)</span></span>  
  
 <span data-ttu-id="fcbf6-108">ここでは、SSL (Secure Sockets Layer) 証明書によって保護されたエンドポイント (つまり、HTTPS エンドポイント) を作成する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="fcbf6-109">セキュリティで保護された HTTPS GET メタデータ エンドポイントをコードで作成するには</span><span class="sxs-lookup"><span data-stu-id="fcbf6-109">To create a secure HTTPS GET metadata endpoint in code</span></span>  
  
1.  <span data-ttu-id="fcbf6-110">適切な X.509 証明書を使用してポートを構成します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="fcbf6-111">この証明書は信頼された証明機関から発行され、かつ "サービス承認" の用途に使用される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="fcbf6-112">証明書をポートに関連付けるには、HttpCfg.exe ツールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="fcbf6-113">参照してください[する方法: SSL 証明書でポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)です。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="fcbf6-114">証明書またはそのドメイン ネーム システム (DNS: Domain Name System) のサブジェクトが、コンピューターの名前と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="fcbf6-115">これは、HTTPS 機構が最初に実行する手順に、呼び出されたアドレスと同じ URI (Uniform Resource Identifier) に対して証明書が発行されているかどうかのチェックが含まれるために必要です。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>  
  
2.  <span data-ttu-id="fcbf6-116"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>  
  
3.  <span data-ttu-id="fcbf6-117"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> クラスの <xref:System.ServiceModel.Description.ServiceMetadataBehavior> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>  
  
4.  <span data-ttu-id="fcbf6-118"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを適切な URL に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="fcbf6-119">絶対アドレスを指定する場合、URL は "https://" で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-119">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="fcbf6-120">相対アドレスを指定する場合は、サービス ホストに HTTPS ベースのアドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="fcbf6-121">このプロパティが設定されていない場合、既定のアドレスは ""、またはサービスに HTTPS ベースのアドレスを直接指定したものになります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
5.  <span data-ttu-id="fcbf6-122">作成したインスタンスを、<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> クラスの <xref:System.ServiceModel.Description.ServiceDescription> プロパティから返される動作コレクションに追加します。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="fcbf6-123">セキュリティで保護された HTTPS GET メタデータ エンドポイントを構成で作成するには</span><span class="sxs-lookup"><span data-stu-id="fcbf6-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>  
  
1.  <span data-ttu-id="fcbf6-124">追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素を[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)サービスの構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>  
  
2.  <span data-ttu-id="fcbf6-125">追加、 [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)要素を[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="fcbf6-126">追加、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)要素を`<serviceBehaviors>`要素。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>  
  
4.  <span data-ttu-id="fcbf6-127">`name` 要素の `<behavior>` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="fcbf6-128">`name` 属性は必須です。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-128">The `name` attribute is required.</span></span> <span data-ttu-id="fcbf6-129">下の例では、`mySvcBehavior` を値として使用しています。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-129">The example below uses the value `mySvcBehavior`.</span></span>  
  
5.  <span data-ttu-id="fcbf6-130">追加、 [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)を`<behavior>`要素。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>  
  
6.  <span data-ttu-id="fcbf6-131">`httpsGetEnabled` 要素の `<serviceMetadata>` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>  
  
7.  <span data-ttu-id="fcbf6-132">`httpsGetUrl` 要素の `<serviceMetadata>` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="fcbf6-133">絶対アドレスを指定する場合、URL は "https://" で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-133">Note that if you specify an absolute address, the URL must begin with the scheme "https://".</span></span> <span data-ttu-id="fcbf6-134">相対アドレスを指定する場合は、サービス ホストに HTTPS ベースのアドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="fcbf6-135">このプロパティが設定されていない場合、既定のアドレスは ""、またはサービスに HTTPS ベースのアドレスを直接指定したものになります。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>  
  
8.  <span data-ttu-id="fcbf6-136">サービスと、動作を使用して、設定、`behaviorConfiguration`の属性、 [\<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)動作要素の name 属性の値を要素。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="fcbf6-137">完全な構成コードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-137">The following configuration code shows a complete example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="mySvcBehavior">  
         <serviceMetadata httpsGetEnabled="true"   
              httpsGetUrl="https://localhost:8036/calcMetadata" />  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
     <services>  
      <service behaviorConfiguration="mySvcBehavior"   
            name="Microsoft.Security.Samples.Calculator">  
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"  
       binding="wsHttpBinding" bindingConfiguration=""     
       contract="Microsoft.Security.Samples.ICalculator" />  
      </service>  
     </services>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
## <a name="example"></a><span data-ttu-id="fcbf6-138">例</span><span class="sxs-lookup"><span data-stu-id="fcbf6-138">Example</span></span>  
 <span data-ttu-id="fcbf6-139">次の例では、<xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成して、エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="fcbf6-140">次に、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスのインスタンスを作成し、プロパティを設定してセキュリティで保護された Metadata Exchange ポイントを作成しています。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fcbf6-141">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fcbf6-141">Compiling the Code</span></span>  
 <span data-ttu-id="fcbf6-142">このコード例では、次の名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="fcbf6-142">The code example uses the following namespaces:</span></span>  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="fcbf6-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcbf6-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [<span data-ttu-id="fcbf6-144">方法 : SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="fcbf6-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="fcbf6-145">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="fcbf6-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="fcbf6-146">メタデータを使用する場合のセキュリティ上の考慮事項</span><span class="sxs-lookup"><span data-stu-id="fcbf6-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [<span data-ttu-id="fcbf6-147">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="fcbf6-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
