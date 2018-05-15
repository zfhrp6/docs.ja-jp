---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a86e1aae7ddd5389f098e532ae2c2cc67f4085e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="bbbbc-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="bbbbc-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="bbbbc-103">SSL ストリームを使用してチャネル セキュリティをサポートするカスタム バインド要素を表します。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="bbbbc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bbbbc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bbbbc-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bbbbc-105">\<bindings></span></span>  
<span data-ttu-id="bbbbc-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-106">\<customBinding></span></span>  
<span data-ttu-id="bbbbc-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-107">\<binding></span></span>  
<span data-ttu-id="bbbbc-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="bbbbc-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbbc-109">構文</span><span class="sxs-lookup"><span data-stu-id="bbbbc-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbbbc-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bbbbc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bbbbc-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbbbc-112">属性</span><span class="sxs-lookup"><span data-stu-id="bbbbc-112">Attributes</span></span>  
  
|<span data-ttu-id="bbbbc-113">属性</span><span class="sxs-lookup"><span data-stu-id="bbbbc-113">Attribute</span></span>|<span data-ttu-id="bbbbc-114">説明</span><span class="sxs-lookup"><span data-stu-id="bbbbc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbbbc-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="bbbbc-115">requireClientCertificate</span></span>|<span data-ttu-id="bbbbc-116">クライアント証明書がこのバインディングに必要かどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="bbbbc-117">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-117">The default is `false`.</span></span>|  
|<span data-ttu-id="bbbbc-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="bbbbc-118">sslProtocols</span></span>|<span data-ttu-id="bbbbc-119">どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="bbbbc-120">既定値は Ssl3&#124;Tls&#124;Tls11&#124;Tls12 です。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbbbc-121">子要素</span><span class="sxs-lookup"><span data-stu-id="bbbbc-121">Child Elements</span></span>  
 <span data-ttu-id="bbbbc-122">なし。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbbbc-123">親要素</span><span class="sxs-lookup"><span data-stu-id="bbbbc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bbbbc-124">要素</span><span class="sxs-lookup"><span data-stu-id="bbbbc-124">Element</span></span>|<span data-ttu-id="bbbbc-125">説明</span><span class="sxs-lookup"><span data-stu-id="bbbbc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbbbc-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bbbbc-127">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="bbbbc-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbbbc-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbbbc-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="bbbbc-129">バインディング</span><span class="sxs-lookup"><span data-stu-id="bbbbc-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bbbbc-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="bbbbc-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bbbbc-131">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="bbbbc-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bbbbc-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bbbbc-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
