---
title: "&lt;requestCaching&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2737e67fe1fe1e33b2600f448b02321f6ce1888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="c6e78-102">&lt;requestCaching&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="c6e78-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c6e78-103">ネットワーク要求のキャッシュ メカニズムを制御します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="c6e78-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c6e78-104">\<configuration></span></span>  
<span data-ttu-id="c6e78-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="c6e78-105">\<system.net></span></span>  
<span data-ttu-id="c6e78-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="c6e78-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e78-107">構文</span><span class="sxs-lookup"><span data-stu-id="c6e78-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6e78-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c6e78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c6e78-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6e78-110">属性</span><span class="sxs-lookup"><span data-stu-id="c6e78-110">Attributes</span></span>  
  
|<span data-ttu-id="c6e78-111">属性</span><span class="sxs-lookup"><span data-stu-id="c6e78-111">Attribute</span></span>|<span data-ttu-id="c6e78-112">説明</span><span class="sxs-lookup"><span data-stu-id="c6e78-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="c6e78-113">キャッシュはさまざまなユーザーの情報との間の分離を提供するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="c6e78-114">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="c6e78-114">The default value is `true`.</span></span> <span data-ttu-id="c6e78-115">この値は、`false`中間層アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c6e78-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="c6e78-116">キャッシュとが無効にすべての Web 応答のプログラムではオーバーライドできませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="c6e78-117"><xref:System.Net.Cache.RequestCacheLevel> 列挙値の値の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="c6e78-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="c6e78-118">既定値は `BypassCache` です。</span><span class="sxs-lookup"><span data-stu-id="c6e78-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="c6e78-119">その後、コンテンツを期限切れとマークは、既定の時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="c6e78-120">policyLevel 属性</span><span class="sxs-lookup"><span data-stu-id="c6e78-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="c6e78-121">値</span><span class="sxs-lookup"><span data-stu-id="c6e78-121">Value</span></span>|<span data-ttu-id="c6e78-122">説明</span><span class="sxs-lookup"><span data-stu-id="c6e78-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="c6e78-123">リソースが新しい場合は、コンテンツの長さが、精度は有効期限、変更、およびコンテンツの長さの属性が存在は、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="c6e78-124">サーバーからリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="c6e78-125">コンテンツの長さが存在し、エントリのサイズと一致する場合は、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="c6e78-126">コンテンツの長さが指定されたエントリのサイズと一致する場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、サーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="c6e78-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="c6e78-127">キャッシュされたリソースのタイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、キャッシュに格納されている、サーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="c6e78-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="c6e78-128">サーバーからリソースをダウンロード、キャッシュに格納し、呼び出し元にリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="c6e78-129">キャッシュされたリソースが存在する場合は削除されます。</span><span class="sxs-lookup"><span data-stu-id="c6e78-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="c6e78-130">リソースは、サーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="c6e78-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="c6e78-131">タイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して、要求に応じます。それ以外の場合、リソースは、呼び出し元に表示される、サーバーからダウンロードされ、キャッシュに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6e78-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6e78-132">子要素</span><span class="sxs-lookup"><span data-stu-id="c6e78-132">Child Elements</span></span>  
  
|<span data-ttu-id="c6e78-133">要素</span><span class="sxs-lookup"><span data-stu-id="c6e78-133">Element</span></span>|<span data-ttu-id="c6e78-134">説明</span><span class="sxs-lookup"><span data-stu-id="c6e78-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6e78-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="c6e78-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="c6e78-136">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="c6e78-136">Optional element.</span></span><br /><br /> <span data-ttu-id="c6e78-137">かどうか HTTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="c6e78-138">\<defaultFtpCachePolicy > 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="c6e78-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="c6e78-139">省略可能な要素です。</span><span class="sxs-lookup"><span data-stu-id="c6e78-139">Optional element.</span></span><br /><br /> <span data-ttu-id="c6e78-140">かどうか FTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6e78-141">親要素</span><span class="sxs-lookup"><span data-stu-id="c6e78-141">Parent Elements</span></span>  
  
|<span data-ttu-id="c6e78-142">要素</span><span class="sxs-lookup"><span data-stu-id="c6e78-142">Element</span></span>|<span data-ttu-id="c6e78-143">説明</span><span class="sxs-lookup"><span data-stu-id="c6e78-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6e78-144">system.net</span><span class="sxs-lookup"><span data-stu-id="c6e78-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="c6e78-145">.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6e78-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c6e78-146">例</span><span class="sxs-lookup"><span data-stu-id="c6e78-146">Example</span></span>  
 <span data-ttu-id="c6e78-147">次の例では、すべてのキャッシュを無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6e78-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6e78-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6e78-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="c6e78-149">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c6e78-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
