---
title: '&lt;serviceTimeouts&gt;'
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: a0f0725bffe0c3c83e412348dea97b16736ef3a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743473"
---
# <a name="ltservicetimeoutsgt"></a><span data-ttu-id="e1123-102">&lt;serviceTimeouts&gt;</span><span class="sxs-lookup"><span data-stu-id="e1123-102">&lt;serviceTimeouts&gt;</span></span>
<span data-ttu-id="e1123-103">サービスのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="e1123-103">Specifies the timeout for a service.</span></span>  
  
 <span data-ttu-id="e1123-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e1123-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e1123-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e1123-105">\<behaviors></span></span>  
<span data-ttu-id="e1123-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e1123-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e1123-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e1123-107">\<behavior></span></span>  
<span data-ttu-id="e1123-108">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="e1123-108">\<serviceTimeouts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1123-109">構文</span><span class="sxs-lookup"><span data-stu-id="e1123-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />  
```  
  
## <a name="type"></a><span data-ttu-id="e1123-110">型</span><span class="sxs-lookup"><span data-stu-id="e1123-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1123-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e1123-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e1123-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1123-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1123-113">属性</span><span class="sxs-lookup"><span data-stu-id="e1123-113">Attributes</span></span>  
  
|<span data-ttu-id="e1123-114">属性</span><span class="sxs-lookup"><span data-stu-id="e1123-114">Attribute</span></span>|<span data-ttu-id="e1123-115">説明</span><span class="sxs-lookup"><span data-stu-id="e1123-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="e1123-116">クライアントからサーバーへのトランザクションが発生するまでに待機できる時間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="e1123-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="e1123-117">既定値は"00: 00:00"です。</span><span class="sxs-lookup"><span data-stu-id="e1123-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1123-118">子要素</span><span class="sxs-lookup"><span data-stu-id="e1123-118">Child Elements</span></span>  
 <span data-ttu-id="e1123-119">なし。</span><span class="sxs-lookup"><span data-stu-id="e1123-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1123-120">親要素</span><span class="sxs-lookup"><span data-stu-id="e1123-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1123-121">要素</span><span class="sxs-lookup"><span data-stu-id="e1123-121">Element</span></span>|<span data-ttu-id="e1123-122">説明</span><span class="sxs-lookup"><span data-stu-id="e1123-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1123-123">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e1123-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e1123-124">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1123-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1123-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1123-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
