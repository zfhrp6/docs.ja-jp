---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="8639c-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="8639c-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="8639c-103">サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。</span><span class="sxs-lookup"><span data-stu-id="8639c-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="8639c-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8639c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8639c-105">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="8639c-105">\<diagnostic></span></span>  
<span data-ttu-id="8639c-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="8639c-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8639c-107">構文</span><span class="sxs-lookup"><span data-stu-id="8639c-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8639c-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8639c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8639c-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8639c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8639c-110">属性</span><span class="sxs-lookup"><span data-stu-id="8639c-110">Attributes</span></span>  
  
|<span data-ttu-id="8639c-111">属性</span><span class="sxs-lookup"><span data-stu-id="8639c-111">Attribute</span></span>|<span data-ttu-id="8639c-112">説明</span><span class="sxs-lookup"><span data-stu-id="8639c-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="8639c-113">アクティビティのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="8639c-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="8639c-114">メッセージ フローのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="8639c-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="8639c-115">伝達属性が true に設定されているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="8639c-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8639c-116">子要素</span><span class="sxs-lookup"><span data-stu-id="8639c-116">Child Elements</span></span>  
 <span data-ttu-id="8639c-117">なし。</span><span class="sxs-lookup"><span data-stu-id="8639c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8639c-118">親要素</span><span class="sxs-lookup"><span data-stu-id="8639c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8639c-119">要素</span><span class="sxs-lookup"><span data-stu-id="8639c-119">Element</span></span>|<span data-ttu-id="8639c-120">説明</span><span class="sxs-lookup"><span data-stu-id="8639c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8639c-121">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="8639c-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="8639c-122">管理者が行うランタイムの検査と管理の WCF 設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="8639c-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8639c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8639c-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="8639c-124">エンド ツー エンドのトレース</span><span class="sxs-lookup"><span data-stu-id="8639c-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
