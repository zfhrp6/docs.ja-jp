---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d93a9ea8614f98c968d499c2f95dcd3962f0020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="5a1fe-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="5a1fe-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="5a1fe-103">使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="5a1fe-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a1fe-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-105">\<behaviors></span></span>  
<span data-ttu-id="5a1fe-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5a1fe-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-107">\<behavior></span></span>  
<span data-ttu-id="5a1fe-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a1fe-109">構文</span><span class="sxs-lookup"><span data-stu-id="5a1fe-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a1fe-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5a1fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a1fe-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a1fe-112">属性</span><span class="sxs-lookup"><span data-stu-id="5a1fe-112">Attributes</span></span>  
  
|<span data-ttu-id="5a1fe-113">属性</span><span class="sxs-lookup"><span data-stu-id="5a1fe-113">Attribute</span></span>|<span data-ttu-id="5a1fe-114">説明</span><span class="sxs-lookup"><span data-stu-id="5a1fe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a1fe-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="5a1fe-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="5a1fe-116">永続化動作に使用するタイムアウトを指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="5a1fe-117">既定値は"00: 00:30"です。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="5a1fe-118">型</span><span class="sxs-lookup"><span data-stu-id="5a1fe-118">type</span></span>|<span data-ttu-id="5a1fe-119">使用する永続化プロバイダー ファクトリの型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a1fe-120">子要素</span><span class="sxs-lookup"><span data-stu-id="5a1fe-120">Child Elements</span></span>  
 <span data-ttu-id="5a1fe-121">なし。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a1fe-122">親要素</span><span class="sxs-lookup"><span data-stu-id="5a1fe-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a1fe-123">要素</span><span class="sxs-lookup"><span data-stu-id="5a1fe-123">Element</span></span>|<span data-ttu-id="5a1fe-124">説明</span><span class="sxs-lookup"><span data-stu-id="5a1fe-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a1fe-125">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="5a1fe-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5a1fe-126">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a1fe-127">コメント</span><span class="sxs-lookup"><span data-stu-id="5a1fe-127">Remarks</span></span>  
 <span data-ttu-id="5a1fe-128">この要素は、WCF サービスの状態をシリアル化するために使用される永続化プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="5a1fe-129">HTTP ヘッダーに状態情報を渡す `wsHttpContextBinding` と一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a1fe-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a1fe-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a1fe-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
