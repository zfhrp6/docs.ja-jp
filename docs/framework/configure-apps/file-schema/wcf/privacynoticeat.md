---
title: '&lt;privacyNoticeAt&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63501539db4dc01d86eb675c28001dc960f1bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="cd2f5-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="cd2f5-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="cd2f5-103">`wsFederationHttp` バインディングで使用されるプライバシーに関する声明を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="cd2f5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cd2f5-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-105">\<bindings></span></span>  
<span data-ttu-id="cd2f5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-106">\<customBinding></span></span>  
<span data-ttu-id="cd2f5-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-107">\<binding></span></span>  
<span data-ttu-id="cd2f5-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2f5-109">構文</span><span class="sxs-lookup"><span data-stu-id="cd2f5-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="cd2f5-110">型</span><span class="sxs-lookup"><span data-stu-id="cd2f5-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd2f5-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cd2f5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cd2f5-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd2f5-113">属性</span><span class="sxs-lookup"><span data-stu-id="cd2f5-113">Attributes</span></span>  
  
|<span data-ttu-id="cd2f5-114">属性</span><span class="sxs-lookup"><span data-stu-id="cd2f5-114">Attribute</span></span>|<span data-ttu-id="cd2f5-115">説明</span><span class="sxs-lookup"><span data-stu-id="cd2f5-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="cd2f5-116">プライバシーに関する声明の場所を示す URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="cd2f5-117">このプライバシーに関する声明のバージョンを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd2f5-118">子要素</span><span class="sxs-lookup"><span data-stu-id="cd2f5-118">Child Elements</span></span>  
 <span data-ttu-id="cd2f5-119">なし。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd2f5-120">親要素</span><span class="sxs-lookup"><span data-stu-id="cd2f5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cd2f5-121">要素</span><span class="sxs-lookup"><span data-stu-id="cd2f5-121">Element</span></span>|<span data-ttu-id="cd2f5-122">説明</span><span class="sxs-lookup"><span data-stu-id="cd2f5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd2f5-123">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cd2f5-124">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd2f5-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd2f5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd2f5-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="cd2f5-126">バインディング</span><span class="sxs-lookup"><span data-stu-id="cd2f5-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cd2f5-127">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="cd2f5-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cd2f5-128">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="cd2f5-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cd2f5-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cd2f5-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
