---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5c801562339f02ff983bb5a755fda6718185ba5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="f5755-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="f5755-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="f5755-103">SSL ストリームを使用してチャネル セキュリティをサポートするカスタム バインド要素を表します。</span><span class="sxs-lookup"><span data-stu-id="f5755-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="f5755-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f5755-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f5755-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f5755-105">\<bindings></span></span>  
<span data-ttu-id="f5755-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f5755-106">\<customBinding></span></span>  
<span data-ttu-id="f5755-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f5755-107">\<binding></span></span>  
<span data-ttu-id="f5755-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="f5755-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5755-109">構文</span><span class="sxs-lookup"><span data-stu-id="f5755-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5755-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f5755-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f5755-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5755-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5755-112">属性</span><span class="sxs-lookup"><span data-stu-id="f5755-112">Attributes</span></span>  
  
|<span data-ttu-id="f5755-113">属性</span><span class="sxs-lookup"><span data-stu-id="f5755-113">Attribute</span></span>|<span data-ttu-id="f5755-114">説明</span><span class="sxs-lookup"><span data-stu-id="f5755-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5755-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="f5755-115">requireClientCertificate</span></span>|<span data-ttu-id="f5755-116">クライアント証明書がこのバインディングに必要かどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="f5755-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="f5755-117">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="f5755-117">The default is `false`.</span></span>|  
|<span data-ttu-id="f5755-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="f5755-118">sslProtocols</span></span>|<span data-ttu-id="f5755-119">どの SslProtocols がサポートされているのかを指定する SslProtocols 列挙型フラグの値。</span><span class="sxs-lookup"><span data-stu-id="f5755-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="f5755-120">既定値は Ssl3 &#124;です。Tls &#124;です。Tls11 &#124; Tls12 です。</span><span class="sxs-lookup"><span data-stu-id="f5755-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5755-121">子要素</span><span class="sxs-lookup"><span data-stu-id="f5755-121">Child Elements</span></span>  
 <span data-ttu-id="f5755-122">なし。</span><span class="sxs-lookup"><span data-stu-id="f5755-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5755-123">親要素</span><span class="sxs-lookup"><span data-stu-id="f5755-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f5755-124">要素</span><span class="sxs-lookup"><span data-stu-id="f5755-124">Element</span></span>|<span data-ttu-id="f5755-125">説明</span><span class="sxs-lookup"><span data-stu-id="f5755-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5755-126">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f5755-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f5755-127">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="f5755-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5755-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5755-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="f5755-129">バインディング</span><span class="sxs-lookup"><span data-stu-id="f5755-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f5755-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="f5755-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f5755-131">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="f5755-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f5755-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f5755-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
