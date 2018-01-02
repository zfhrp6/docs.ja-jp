---
title: "&lt;netMsmqBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c6f0f2a6da3b5bc5cb33d20118c135b3b7652986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="5f932-102">&lt;netMsmqBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="5f932-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="5f932-103">MSMQ バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="5f932-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="5f932-104">トランスポートまたは SOAP セキュリティが有効であるかどうか、および有効である場合は、どの認証モードと保護レベルを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f932-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="5f932-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5f932-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5f932-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="5f932-106">\<bindings></span></span>  
<span data-ttu-id="5f932-107">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="5f932-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="5f932-108">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="5f932-108">\<binding></span></span>  
<span data-ttu-id="5f932-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="5f932-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f932-110">構文</span><span class="sxs-lookup"><span data-stu-id="5f932-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f932-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5f932-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5f932-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f932-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f932-113">属性</span><span class="sxs-lookup"><span data-stu-id="5f932-113">Attributes</span></span>  
  
|<span data-ttu-id="5f932-114">属性</span><span class="sxs-lookup"><span data-stu-id="5f932-114">Attribute</span></span>|<span data-ttu-id="5f932-115">説明</span><span class="sxs-lookup"><span data-stu-id="5f932-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f932-116">モード</span><span class="sxs-lookup"><span data-stu-id="5f932-116">mode</span></span>|<span data-ttu-id="5f932-117">整合性、機密性、および認証を制御するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f932-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="5f932-118">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="5f932-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5f932-119">-なし: 無効になりますセキュリティ。</span><span class="sxs-lookup"><span data-stu-id="5f932-119">-   None: This disables security.</span></span><br /><span data-ttu-id="5f932-120">-Transport: 保護と認証は、トランスポートによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="5f932-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="5f932-121">これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="5f932-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="5f932-122">アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="5f932-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="5f932-123">既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。</span><span class="sxs-lookup"><span data-stu-id="5f932-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="5f932-124">-メッセージ: は、エンド ツー エンドのアプリケーションのセキュリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="5f932-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="5f932-125">トランスポート層で提供されるセキュリティありません。</span><span class="sxs-lookup"><span data-stu-id="5f932-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="5f932-126">これは、他の標準バインディングによって提供されたセキュリティと同様です。</span><span class="sxs-lookup"><span data-stu-id="5f932-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="5f932-127">-両方:、トランスポートと SOAP メッセージング レイヤーの両方でセキュリティを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5f932-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="5f932-128">同じ資格情報が、両方のレベルで要求されます。</span><span class="sxs-lookup"><span data-stu-id="5f932-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="5f932-129">既定値は、Transport です。</span><span class="sxs-lookup"><span data-stu-id="5f932-129">The default value is Transport.</span></span> <span data-ttu-id="5f932-130">この属性は <xref:System.ServiceModel.NetMsmqSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="5f932-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f932-131">子要素</span><span class="sxs-lookup"><span data-stu-id="5f932-131">Child Elements</span></span>  
  
|<span data-ttu-id="5f932-132">要素</span><span class="sxs-lookup"><span data-stu-id="5f932-132">Element</span></span>|<span data-ttu-id="5f932-133">説明</span><span class="sxs-lookup"><span data-stu-id="5f932-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f932-134">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="5f932-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="5f932-135">SOAP メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="5f932-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="5f932-136">この要素は <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="5f932-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="5f932-137">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="5f932-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="5f932-138">MSMQ トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="5f932-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="5f932-139">この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="5f932-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f932-140">親要素</span><span class="sxs-lookup"><span data-stu-id="5f932-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5f932-141">要素</span><span class="sxs-lookup"><span data-stu-id="5f932-141">Element</span></span>|<span data-ttu-id="5f932-142">説明</span><span class="sxs-lookup"><span data-stu-id="5f932-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f932-143">バインド</span><span class="sxs-lookup"><span data-stu-id="5f932-143">binding</span></span>|<span data-ttu-id="5f932-144">バインド要素、 [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5f932-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f932-145">参照</span><span class="sxs-lookup"><span data-stu-id="5f932-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [<span data-ttu-id="5f932-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5f932-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5f932-147">バインディング</span><span class="sxs-lookup"><span data-stu-id="5f932-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5f932-148">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="5f932-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5f932-149">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="5f932-149">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5f932-150">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="5f932-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="5f932-151">WCF のキュー</span><span class="sxs-lookup"><span data-stu-id="5f932-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
