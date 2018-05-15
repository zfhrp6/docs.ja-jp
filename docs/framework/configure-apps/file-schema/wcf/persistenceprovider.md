---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 3c7fd74a84184ddbf8cc8db90141174ed84e5774
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="73ff4-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="73ff4-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="73ff4-103">使用する永続化プロバイダーの実装の型と、永続化操作に使用するタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="73ff4-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="73ff4-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73ff4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73ff4-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="73ff4-105">\<behaviors></span></span>  
<span data-ttu-id="73ff4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="73ff4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="73ff4-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="73ff4-107">\<behavior></span></span>  
<span data-ttu-id="73ff4-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="73ff4-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ff4-109">構文</span><span class="sxs-lookup"><span data-stu-id="73ff4-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73ff4-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="73ff4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73ff4-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="73ff4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73ff4-112">属性</span><span class="sxs-lookup"><span data-stu-id="73ff4-112">Attributes</span></span>  
  
|<span data-ttu-id="73ff4-113">属性</span><span class="sxs-lookup"><span data-stu-id="73ff4-113">Attribute</span></span>|<span data-ttu-id="73ff4-114">説明</span><span class="sxs-lookup"><span data-stu-id="73ff4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73ff4-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="73ff4-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="73ff4-116">永続化動作に使用するタイムアウトを指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="73ff4-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="73ff4-117">既定値は"00: 00:30"です。</span><span class="sxs-lookup"><span data-stu-id="73ff4-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="73ff4-118">型</span><span class="sxs-lookup"><span data-stu-id="73ff4-118">type</span></span>|<span data-ttu-id="73ff4-119">使用する永続化プロバイダー ファクトリの型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="73ff4-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73ff4-120">子要素</span><span class="sxs-lookup"><span data-stu-id="73ff4-120">Child Elements</span></span>  
 <span data-ttu-id="73ff4-121">なし。</span><span class="sxs-lookup"><span data-stu-id="73ff4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73ff4-122">親要素</span><span class="sxs-lookup"><span data-stu-id="73ff4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73ff4-123">要素</span><span class="sxs-lookup"><span data-stu-id="73ff4-123">Element</span></span>|<span data-ttu-id="73ff4-124">説明</span><span class="sxs-lookup"><span data-stu-id="73ff4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73ff4-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="73ff4-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="73ff4-126">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="73ff4-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73ff4-127">コメント</span><span class="sxs-lookup"><span data-stu-id="73ff4-127">Remarks</span></span>  
 <span data-ttu-id="73ff4-128">この要素は、WCF サービスの状態をシリアル化するために使用される永続化プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="73ff4-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="73ff4-129">HTTP ヘッダーに状態情報を渡す `wsHttpContextBinding` と一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73ff4-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ff4-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="73ff4-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
