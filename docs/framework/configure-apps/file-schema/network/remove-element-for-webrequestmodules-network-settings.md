---
title: "&lt;削除&gt;webRequestModules (ネットワーク設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 391e5f2a7d9d8076ba9e9a3057e3d8899e2ce672
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="ltremovegt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="6b9da-102">&lt;削除&gt;webRequestModules (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="6b9da-102">&lt;remove&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="6b9da-103">アプリケーションからカスタム Web 要求のモジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="6b9da-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="6b9da-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6b9da-104">\<configuration></span></span>  
<span data-ttu-id="6b9da-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6b9da-105">\<system.net></span></span>  
<span data-ttu-id="6b9da-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="6b9da-106">\<webRequestModules></span></span>  
<span data-ttu-id="6b9da-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="6b9da-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9da-108">構文</span><span class="sxs-lookup"><span data-stu-id="6b9da-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b9da-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6b9da-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6b9da-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b9da-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b9da-111">属性</span><span class="sxs-lookup"><span data-stu-id="6b9da-111">Attributes</span></span>  
  
|<span data-ttu-id="6b9da-112">**属性**</span><span class="sxs-lookup"><span data-stu-id="6b9da-112">**Attribute**</span></span>|<span data-ttu-id="6b9da-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="6b9da-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="6b9da-114">この Web 要求モジュールによって処理される要求の URI プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="6b9da-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b9da-115">子要素</span><span class="sxs-lookup"><span data-stu-id="6b9da-115">Child Elements</span></span>  
 <span data-ttu-id="6b9da-116">なし。</span><span class="sxs-lookup"><span data-stu-id="6b9da-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b9da-117">親要素</span><span class="sxs-lookup"><span data-stu-id="6b9da-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6b9da-118">**要素**</span><span class="sxs-lookup"><span data-stu-id="6b9da-118">**Element**</span></span>|<span data-ttu-id="6b9da-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="6b9da-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6b9da-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="6b9da-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="6b9da-121">使用してネットワークのホストから情報を要求するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b9da-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b9da-122">コメント</span><span class="sxs-lookup"><span data-stu-id="6b9da-122">Remarks</span></span>  
 <span data-ttu-id="6b9da-123">`remove`要素が指定した URI プレフィックスの登録済みの Web 要求のモジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="6b9da-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="6b9da-124">値、`prefix`属性が有効な URI: たとえば、"http"の先頭の文字にする必要がありますか"http://www.contoso.com"です。</span><span class="sxs-lookup"><span data-stu-id="6b9da-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "http", or "http://www.contoso.com".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6b9da-125">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="6b9da-125">Configuration Files</span></span>  
 <span data-ttu-id="6b9da-126">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6b9da-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b9da-127">例</span><span class="sxs-lookup"><span data-stu-id="6b9da-127">Example</span></span>  
 <span data-ttu-id="6b9da-128">次の例では、HTTP の場合、既存の Web 要求のモジュールを削除し、www.contoso.com への HTTP 要求のカスタム Web 要求の新しいモジュールを登録します。</span><span class="sxs-lookup"><span data-stu-id="6b9da-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to www.contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b9da-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b9da-129">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="6b9da-130">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6b9da-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
