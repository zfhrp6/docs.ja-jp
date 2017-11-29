---
title: "時間ベースのキャッシュ ポリシー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4cfa67d7fba06140838e04bdbff71102a2a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="b4b09-102">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b4b09-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="b4b09-103">時間ベースのキャッシュ ポリシーは、リソースの取得時間、リソースと共に返されたヘッダー、現在時刻を利用し、キャッシュされているエントリの更新の確認間隔を定義します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="b4b09-104">時間ベースのキャッシュ ポリシーを設定するとき、<xref:System.Net.Cache.HttpRequestCacheLevel.Default> 時間ベース キャッシュ ポリシーを利用するか、カスタマイズした時間ベース ポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="b4b09-105">ハイパーテキスト転送プロトコル (HTTP) を利用して取得されるリソースに既定の時間ベース ポリシーを利用するとき、厳密なキャッシュ動作は、キャッシュされている応答に含まれているヘッダーと、RFC 2616 のセクション 13 とセクション 14 に指定されている動作で決定されます。RFC 2616 は [http://www.ietf.org](http://www.ietf.org/) で確認できます。HTTP リソースの既定の時間ベース ポリシーを設定する方法を示すコード例については、「[How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md)」(方法: アプリケーションの既定の時間ベースのキャッシュ ポリシーを設定する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b09-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="b4b09-106">キャッシュ ポリシーを作成し、利用する方法を示すコード例については、「[ネットワーク アプリケーションでのキャッシュの構成](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b09-106">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="b4b09-107">キャッシュされたエントリの更新の確認間隔を決定する基準</span><span class="sxs-lookup"><span data-stu-id="b4b09-107">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="b4b09-108">時間ベースのキャッシュ ポリシーをカスタマイズするとき、次の条件を 1 つまたは複数利用し、キャッシュされているエントリの更新の確認間隔を決定するように指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-108">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
-   <span data-ttu-id="b4b09-109">最大有効期間</span><span class="sxs-lookup"><span data-stu-id="b4b09-109">Maximum age</span></span>  
  
-   <span data-ttu-id="b4b09-110">最大期限延長</span><span class="sxs-lookup"><span data-stu-id="b4b09-110">Maximum staleness</span></span>  
  
-   <span data-ttu-id="b4b09-111">最小鮮度</span><span class="sxs-lookup"><span data-stu-id="b4b09-111">Minimum freshness</span></span>  
  
-   <span data-ttu-id="b4b09-112">キャッシュ同期日付</span><span class="sxs-lookup"><span data-stu-id="b4b09-112">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4b09-113">既定の時間ベース キャッシュ ポリシーを使用することと、アプリケーションの既定のキャッシュ ポリシーを設定することを混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4b09-113">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="b4b09-114">既定の時間ベース ポリシーは、要求またはアプリケーション レベルで利用できる特定のポリシーです。</span><span class="sxs-lookup"><span data-stu-id="b4b09-114">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="b4b09-115">アプリケーションの既定のキャッシュ ポリシーは、要求にポリシーが設定されていないときに有効なポリシーです (場所ベースまたは時間ベース)。</span><span class="sxs-lookup"><span data-stu-id="b4b09-115">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="b4b09-116">アプリケーションの既定のキャッシュ ポリシーを設定する方法については、「<xref:System.Net.WebRequest.DefaultCachePolicy%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4b09-116">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="b4b09-117">最大有効期間</span><span class="sxs-lookup"><span data-stu-id="b4b09-117">Maximum Age</span></span>  
 <span data-ttu-id="b4b09-118">最大有効期間というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-118">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="b4b09-119">そのリソースのキャッシュ済みコピーが指定された時間より古い場合、サーバーのコンテンツに対して確認し、リソースを再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4b09-119">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="b4b09-120">最大有効期間で、失効後にリソースの利用が許可される場合、最大期限延長も指定されない限り、この基準は守られません。</span><span class="sxs-lookup"><span data-stu-id="b4b09-120">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="b4b09-121">最大期限延長</span><span class="sxs-lookup"><span data-stu-id="b4b09-121">Maximum Staleness</span></span>  
 <span data-ttu-id="b4b09-122">最大期限延長というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間をコンテンツの失効後に指定します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-122">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="b4b09-123">これは、失効後、リソースの利用を許可する唯一のキャッシュ ポリシー基準です。</span><span class="sxs-lookup"><span data-stu-id="b4b09-123">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="b4b09-124">最小鮮度</span><span class="sxs-lookup"><span data-stu-id="b4b09-124">Minimum Freshness</span></span>  
 <span data-ttu-id="b4b09-125">最小鮮度というポリシー基準は、リソースのキャッシュ済みコピーを利用できる時間をコンテンツの失効前に指定します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-125">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="b4b09-126">このポリシーにより、有効期限前にキャッシュ エントリが失効します。最小鮮度と最大期限延長は互いに排他的になります。</span><span class="sxs-lookup"><span data-stu-id="b4b09-126">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="b4b09-127">キャッシュ同期日付</span><span class="sxs-lookup"><span data-stu-id="b4b09-127">Cache Synchronization Date</span></span>  
 <span data-ttu-id="b4b09-128">キャッシュ同期日付というポリシー基準は、サーバーのコンテンツに対して確認することで、リソースのキャッシュ済みコピーを再検証するタイミングを決定します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-128">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="b4b09-129">アイテムのキャッシュ後にコンテンツが変更された場合、そのコンテンツはサーバーから取得され、キャッシュに保存され、アプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-129">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="b4b09-130">コンテンツが変わっていない場合、そのタイムスタンプが更新され、アプリケーションはキャッシュ済みコンテンツを取得します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-130">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="b4b09-131">キャッシュ同期日付を利用し、キャッシュ済みコンテンツを再検証する絶対的日付を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-131">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="b4b09-132">新しいキャッシュ エントリが最後に再検証されたのがキャッシュ同期日付より前であれば、サーバーにより再検証が発生します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-132">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="b4b09-133">キャッシュ同期日付後にキャッシュ エントリが再検証されたとき、キャッシュ済みエントリを無効にする、付加的な更新確認要件またはサーバー再検証要件がなければ、キャッシュからのエントリが利用されます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-133">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="b4b09-134">キャッシュ同期日付が未来の日付に設定されている場合、キャッシュ同期日付が過ぎるまで、要求のたびにエントリが再検証されます。</span><span class="sxs-lookup"><span data-stu-id="b4b09-134">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="b4b09-135">後続のトピックでは、時間ベース キャッシュ ポリシー基準の組み合わせについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b4b09-135">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
-   [<span data-ttu-id="b4b09-136">キャッシュ ポリシーの相互作用 - 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="b4b09-136">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [<span data-ttu-id="b4b09-137">キャッシュ ポリシーの相互作用 - 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="b4b09-137">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="b4b09-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4b09-138">See Also</span></span>  
 [<span data-ttu-id="b4b09-139">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="b4b09-139">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="b4b09-140">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b4b09-140">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="b4b09-141">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b4b09-141">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="b4b09-142">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="b4b09-142">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="b4b09-143">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="b4b09-143">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
