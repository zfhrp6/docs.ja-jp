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
ms.workload: dotnet
ms.openlocfilehash: a43801f4c45d7ac518c3b24cadc58ffbec40adb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="f1461-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="f1461-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="f1461-103">サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。</span><span class="sxs-lookup"><span data-stu-id="f1461-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="f1461-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f1461-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1461-105">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="f1461-105">\<diagnostic></span></span>  
<span data-ttu-id="f1461-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="f1461-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1461-107">構文</span><span class="sxs-lookup"><span data-stu-id="f1461-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1461-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f1461-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f1461-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1461-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1461-110">属性</span><span class="sxs-lookup"><span data-stu-id="f1461-110">Attributes</span></span>  
  
|<span data-ttu-id="f1461-111">属性</span><span class="sxs-lookup"><span data-stu-id="f1461-111">Attribute</span></span>|<span data-ttu-id="f1461-112">説明</span><span class="sxs-lookup"><span data-stu-id="f1461-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="f1461-113">アクティビティのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="f1461-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="f1461-114">メッセージ フローのトレースが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="f1461-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="f1461-115">伝達属性が true に設定されているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="f1461-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1461-116">子要素</span><span class="sxs-lookup"><span data-stu-id="f1461-116">Child Elements</span></span>  
 <span data-ttu-id="f1461-117">なし。</span><span class="sxs-lookup"><span data-stu-id="f1461-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1461-118">親要素</span><span class="sxs-lookup"><span data-stu-id="f1461-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f1461-119">要素</span><span class="sxs-lookup"><span data-stu-id="f1461-119">Element</span></span>|<span data-ttu-id="f1461-120">説明</span><span class="sxs-lookup"><span data-stu-id="f1461-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1461-121">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="f1461-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="f1461-122">管理者が行うランタイムの検査と管理の WCF 設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="f1461-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1461-123">参照</span><span class="sxs-lookup"><span data-stu-id="f1461-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="f1461-124">エンドツーエンドのトレース</span><span class="sxs-lookup"><span data-stu-id="f1461-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
