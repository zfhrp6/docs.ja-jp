---
title: "&lt;オフ&gt;bypasslist (ネットワーク設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 620197065a8e689997b4081b3d90169aa0e3c6c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="b693c-102">&lt;オフ&gt;bypasslist (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="b693c-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="b693c-103">プロキシ バイ パスの一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="b693c-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="b693c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b693c-104">\<configuration></span></span>  
<span data-ttu-id="b693c-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="b693c-105">\<system.net></span></span>  
<span data-ttu-id="b693c-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="b693c-106">\<defaultProxy></span></span>  
<span data-ttu-id="b693c-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="b693c-107">\<bypasslist></span></span>  
<span data-ttu-id="b693c-108">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="b693c-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b693c-109">構文</span><span class="sxs-lookup"><span data-stu-id="b693c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b693c-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b693c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b693c-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b693c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b693c-112">属性</span><span class="sxs-lookup"><span data-stu-id="b693c-112">Attributes</span></span>  
 <span data-ttu-id="b693c-113">なし。</span><span class="sxs-lookup"><span data-stu-id="b693c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b693c-114">子要素</span><span class="sxs-lookup"><span data-stu-id="b693c-114">Child Elements</span></span>  
 <span data-ttu-id="b693c-115">なし。</span><span class="sxs-lookup"><span data-stu-id="b693c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b693c-116">親要素</span><span class="sxs-lookup"><span data-stu-id="b693c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b693c-117">**要素**</span><span class="sxs-lookup"><span data-stu-id="b693c-117">**Element**</span></span>|<span data-ttu-id="b693c-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="b693c-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b693c-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="b693c-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="b693c-120">プロキシを使用しないアドレスを記述する正規表現のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="b693c-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b693c-121">コメント</span><span class="sxs-lookup"><span data-stu-id="b693c-121">Remarks</span></span>  
 <span data-ttu-id="b693c-122">`clear`要素は、バイパス リストからすべてのエントリをクリアします。</span><span class="sxs-lookup"><span data-stu-id="b693c-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b693c-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="b693c-123">Configuration Files</span></span>  
 <span data-ttu-id="b693c-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b693c-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b693c-125">例</span><span class="sxs-lookup"><span data-stu-id="b693c-125">Example</span></span>  
 <span data-ttu-id="b693c-126">次の例では、バイパス リストをクリアし、バイパス リストに 2 つのアドレスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="b693c-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="b693c-127">1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 番目は、すべてのサーバーの IP アドレスが始まる 192.168.*.* でプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="b693c-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="b693c-128">参照</span><span class="sxs-lookup"><span data-stu-id="b693c-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="b693c-129">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b693c-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
