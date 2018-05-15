---
title: '&lt;bypasslist&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d2076ee5e95ab722fe828ee625392671a6281c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="48e9a-102">&lt;bypasslist&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="48e9a-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="48e9a-103">プロキシを使用しないアドレスを記述する正規表現のセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="48e9a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="48e9a-104">\<configuration></span></span>  
<span data-ttu-id="48e9a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="48e9a-105">\<system.net></span></span>  
<span data-ttu-id="48e9a-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="48e9a-106">\<defaultProxy></span></span>  
<span data-ttu-id="48e9a-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="48e9a-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e9a-108">構文</span><span class="sxs-lookup"><span data-stu-id="48e9a-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48e9a-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="48e9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48e9a-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48e9a-111">属性</span><span class="sxs-lookup"><span data-stu-id="48e9a-111">Attributes</span></span>  
 <span data-ttu-id="48e9a-112">なし。</span><span class="sxs-lookup"><span data-stu-id="48e9a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48e9a-113">子要素</span><span class="sxs-lookup"><span data-stu-id="48e9a-113">Child Elements</span></span>  
  
|<span data-ttu-id="48e9a-114">**要素**</span><span class="sxs-lookup"><span data-stu-id="48e9a-114">**Element**</span></span>|<span data-ttu-id="48e9a-115">**説明**</span><span class="sxs-lookup"><span data-stu-id="48e9a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="48e9a-116">add</span><span class="sxs-lookup"><span data-stu-id="48e9a-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="48e9a-117">プロキシ バイ パス一覧に IP アドレスまたは DNS 名を追加します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="48e9a-118">clear</span><span class="sxs-lookup"><span data-stu-id="48e9a-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="48e9a-119">バイパス リストをクリアします。</span><span class="sxs-lookup"><span data-stu-id="48e9a-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="48e9a-120">remove</span><span class="sxs-lookup"><span data-stu-id="48e9a-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="48e9a-121">プロキシ バイ パス一覧から IP アドレスまたは DNS 名を削除します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48e9a-122">親要素</span><span class="sxs-lookup"><span data-stu-id="48e9a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="48e9a-123">**要素**</span><span class="sxs-lookup"><span data-stu-id="48e9a-123">**Element**</span></span>|<span data-ttu-id="48e9a-124">**説明**</span><span class="sxs-lookup"><span data-stu-id="48e9a-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="48e9a-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="48e9a-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="48e9a-126">ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e9a-127">コメント</span><span class="sxs-lookup"><span data-stu-id="48e9a-127">Remarks</span></span>  
 <span data-ttu-id="48e9a-128">バイパス リストを含む Uri を表す正規表現を<xref:System.Net.WebRequest>インスタンスは、プロキシ サーバーを直接の代わりにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="48e9a-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="48e9a-129">この要素に正規表現を指定する場合は、注意を使用してください。</span><span class="sxs-lookup"><span data-stu-id="48e9a-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="48e9a-130">正規表現"[a ~ z] +\\.contoso\\.com"contoso.com ドメイン内の任意のホストと一致する contoso.com.cpandl.com ドメイン内のどのホストにも一致します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="48e9a-131">Contoso.com ドメイン内のホストのみを一致するには、アンカー (「$」) を使用します。"[a ~ z] +\\.contoso\\.com$"です。</span><span class="sxs-lookup"><span data-stu-id="48e9a-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="48e9a-132">正規表現の詳細についてを参照してください。[.NET framework 正規表現](../../../../../docs/standard/base-types/regular-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="48e9a-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="48e9a-133">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="48e9a-133">Configuration Files</span></span>  
 <span data-ttu-id="48e9a-134">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="48e9a-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e9a-135">例</span><span class="sxs-lookup"><span data-stu-id="48e9a-135">Example</span></span>  
 <span data-ttu-id="48e9a-136">次の例では、バイパス リストに 2 つのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="48e9a-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="48e9a-137">1 つ目は、contoso.com ドメイン内のすべてのサーバーでプロキシをバイパスします。2 番目は、すべてのサーバーの IP アドレスを持つ開始 192.168.*.* でプロキシをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="48e9a-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48e9a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="48e9a-138">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="48e9a-139">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="48e9a-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
