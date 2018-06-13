---
title: '&lt;オフ&gt;bypasslist (ネットワーク設定) の要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9297b68a31117aabfa45328954ccb9c7cdac66c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742193"
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="fdf00-102">&lt;オフ&gt;bypasslist (ネットワーク設定) の要素</span><span class="sxs-lookup"><span data-stu-id="fdf00-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="fdf00-103">プロキシ バイ パスの一覧をクリアします。</span><span class="sxs-lookup"><span data-stu-id="fdf00-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="fdf00-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fdf00-104">\<configuration></span></span>  
<span data-ttu-id="fdf00-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fdf00-105">\<system.net></span></span>  
<span data-ttu-id="fdf00-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="fdf00-106">\<defaultProxy></span></span>  
<span data-ttu-id="fdf00-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="fdf00-107">\<bypasslist></span></span>  
<span data-ttu-id="fdf00-108">\<オフ ></span><span class="sxs-lookup"><span data-stu-id="fdf00-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf00-109">構文</span><span class="sxs-lookup"><span data-stu-id="fdf00-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdf00-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fdf00-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fdf00-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fdf00-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdf00-112">属性</span><span class="sxs-lookup"><span data-stu-id="fdf00-112">Attributes</span></span>  
 <span data-ttu-id="fdf00-113">なし。</span><span class="sxs-lookup"><span data-stu-id="fdf00-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fdf00-114">子要素</span><span class="sxs-lookup"><span data-stu-id="fdf00-114">Child Elements</span></span>  
 <span data-ttu-id="fdf00-115">なし。</span><span class="sxs-lookup"><span data-stu-id="fdf00-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdf00-116">親要素</span><span class="sxs-lookup"><span data-stu-id="fdf00-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fdf00-117">**要素**</span><span class="sxs-lookup"><span data-stu-id="fdf00-117">**Element**</span></span>|<span data-ttu-id="fdf00-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="fdf00-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fdf00-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="fdf00-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="fdf00-120">プロキシを使用しないアドレスを記述する正規表現のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="fdf00-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf00-121">コメント</span><span class="sxs-lookup"><span data-stu-id="fdf00-121">Remarks</span></span>  
 <span data-ttu-id="fdf00-122">`clear`要素は、バイパス リストからすべてのエントリをクリアします。</span><span class="sxs-lookup"><span data-stu-id="fdf00-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fdf00-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="fdf00-123">Configuration Files</span></span>  
 <span data-ttu-id="fdf00-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fdf00-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf00-125">例</span><span class="sxs-lookup"><span data-stu-id="fdf00-125">Example</span></span>  
 <span data-ttu-id="fdf00-126">次の例では、バイパス リストをクリアし、バイパス リストに 2 つのアドレスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="fdf00-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="fdf00-127">1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 番目は、すべてのサーバーの IP アドレスが始まる 192.168.*.* でプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="fdf00-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdf00-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdf00-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="fdf00-129">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="fdf00-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
