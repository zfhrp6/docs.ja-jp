---
title: "&lt;defaultFtpCachePolicy&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6b9a5fb2f62c27d278570ad789deab30917bc432
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="3f554-102">&lt;defaultFtpCachePolicy&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="3f554-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3f554-103">かどうか FTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f554-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="3f554-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3f554-104">\<configuration></span></span>  
<span data-ttu-id="3f554-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="3f554-105">\<system.net></span></span>  
<span data-ttu-id="3f554-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="3f554-106">\<requestCaching></span></span>  
<span data-ttu-id="3f554-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="3f554-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f554-108">構文</span><span class="sxs-lookup"><span data-stu-id="3f554-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f554-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3f554-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f554-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f554-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f554-111">属性</span><span class="sxs-lookup"><span data-stu-id="3f554-111">Attributes</span></span>  
  
|<span data-ttu-id="3f554-112">属性</span><span class="sxs-lookup"><span data-stu-id="3f554-112">Attribute</span></span>|<span data-ttu-id="3f554-113">説明</span><span class="sxs-lookup"><span data-stu-id="3f554-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="3f554-114">FTP のキャッシュ ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3f554-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="3f554-115">既定値は `Default` です。</span><span class="sxs-lookup"><span data-stu-id="3f554-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="3f554-116">policyLevel 属性</span><span class="sxs-lookup"><span data-stu-id="3f554-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="3f554-117">値</span><span class="sxs-lookup"><span data-stu-id="3f554-117">Value</span></span>|<span data-ttu-id="3f554-118">説明</span><span class="sxs-lookup"><span data-stu-id="3f554-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="3f554-119">リソースが新しい場合は、コンテンツの長さが、精度は有効期限、変更、およびコンテンツの長さの属性が存在は、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="3f554-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="3f554-120">サーバーからリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="3f554-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="3f554-121">コンテンツの長さが存在し、エントリのサイズと一致する場合は、キャッシュされたリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="3f554-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="3f554-122">コンテンツの長さが指定されたエントリのサイズと一致する場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、サーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="3f554-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3f554-123">キャッシュされたリソースのタイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返しますそれ以外の場合、リソース サーバーからダウンロード、キャッシュに格納されているを呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="3f554-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="3f554-124">サーバーからリソースをダウンロード、キャッシュに格納し、呼び出し元にリソースを返します。</span><span class="sxs-lookup"><span data-stu-id="3f554-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="3f554-125">キャッシュされたリソースが存在する場合は削除されます。</span><span class="sxs-lookup"><span data-stu-id="3f554-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="3f554-126">リソースは、サーバーからダウンロードされ、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="3f554-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3f554-127">タイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して、要求に応じます。それ以外の場合、リソースはサーバーからダウンロード、呼び出し元に表示される、キャッシュに格納されています。</span><span class="sxs-lookup"><span data-stu-id="3f554-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f554-128">子要素</span><span class="sxs-lookup"><span data-stu-id="3f554-128">Child Elements</span></span>  
 <span data-ttu-id="3f554-129">なし。</span><span class="sxs-lookup"><span data-stu-id="3f554-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f554-130">親要素</span><span class="sxs-lookup"><span data-stu-id="3f554-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3f554-131">要素</span><span class="sxs-lookup"><span data-stu-id="3f554-131">Element</span></span>|<span data-ttu-id="3f554-132">説明</span><span class="sxs-lookup"><span data-stu-id="3f554-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f554-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="3f554-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="3f554-134">ネットワーク要求のキャッシュ メカニズムを制御します。</span><span class="sxs-lookup"><span data-stu-id="3f554-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f554-135">コメント</span><span class="sxs-lookup"><span data-stu-id="3f554-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f554-136">例</span><span class="sxs-lookup"><span data-stu-id="3f554-136">Example</span></span>  
 <span data-ttu-id="3f554-137">次の例は、FTP キャッシュのポリシーを指定する方法を示しています。`NoCacheNoStore`です。</span><span class="sxs-lookup"><span data-stu-id="3f554-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f554-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f554-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="3f554-139">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3f554-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
