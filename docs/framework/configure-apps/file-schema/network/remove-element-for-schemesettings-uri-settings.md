---
title: '&lt;削除&gt;schemeSettings (Uri 設定) の要素'
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8e01f82a476286e27129e4b1a47fefc1ac77c2b5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744162"
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="95f01-102">&lt;削除&gt;schemeSettings (Uri 設定) の要素</span><span class="sxs-lookup"><span data-stu-id="95f01-102">&lt;remove&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="95f01-103">スキーム名にスキームの設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="95f01-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="95f01-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="95f01-104">\<configuration></span></span>  
<span data-ttu-id="95f01-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="95f01-105">\<uri></span></span>  
<span data-ttu-id="95f01-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="95f01-106">\<schemeSettings></span></span>  
<span data-ttu-id="95f01-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="95f01-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f01-108">構文</span><span class="sxs-lookup"><span data-stu-id="95f01-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95f01-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="95f01-109">Attributes and Elements</span></span>  
 <span data-ttu-id="95f01-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="95f01-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95f01-111">属性</span><span class="sxs-lookup"><span data-stu-id="95f01-111">Attributes</span></span>  
  
|<span data-ttu-id="95f01-112">属性</span><span class="sxs-lookup"><span data-stu-id="95f01-112">Attribute</span></span>|<span data-ttu-id="95f01-113">説明</span><span class="sxs-lookup"><span data-stu-id="95f01-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95f01-114">name</span><span class="sxs-lookup"><span data-stu-id="95f01-114">name</span></span>|<span data-ttu-id="95f01-115">スキーム名は、この設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="95f01-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="95f01-116">だけでサポートされる値は名前 ="http"、name ="https"。</span><span class="sxs-lookup"><span data-stu-id="95f01-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95f01-117">子要素</span><span class="sxs-lookup"><span data-stu-id="95f01-117">Child Elements</span></span>  
 <span data-ttu-id="95f01-118">なし。</span><span class="sxs-lookup"><span data-stu-id="95f01-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95f01-119">親要素</span><span class="sxs-lookup"><span data-stu-id="95f01-119">Parent Elements</span></span>  
  
|<span data-ttu-id="95f01-120">要素</span><span class="sxs-lookup"><span data-stu-id="95f01-120">Element</span></span>|<span data-ttu-id="95f01-121">説明</span><span class="sxs-lookup"><span data-stu-id="95f01-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95f01-122">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="95f01-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="95f01-123"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="95f01-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95f01-124">コメント</span><span class="sxs-lookup"><span data-stu-id="95f01-124">Remarks</span></span>  
 <span data-ttu-id="95f01-125">既定では、<xref:System.Uri?displayProperty=nameWithType>クラス エスケープを解除 % は、パスの圧縮を実行する前にパスの区切り記号をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="95f01-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="95f01-126">これは、次のような攻撃に対するセキュリティ機構として実装されていました。</span><span class="sxs-lookup"><span data-stu-id="95f01-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="95f01-127">この URI が渡される場合は、モジュール % は処理されません。 エンコードした文字を正しく、サーバーにより実行されている次のコマンドを可能性があります。</span><span class="sxs-lookup"><span data-stu-id="95f01-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="95f01-128">このため、<xref:System.Uri?displayProperty=nameWithType>クラスの最初のエスケープを解除パス区切り記号とパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="95f01-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="95f01-129">上への悪意のある URL を渡した結果<xref:System.Uri?displayProperty=nameWithType>クラスのコンス トラクターの結果で、次の URI:</span><span class="sxs-lookup"><span data-stu-id="95f01-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="95f01-130">いないエスケープ解除パーセント エンコードされたパスの区切り記号 schemeSettings 構成オプションを使用して、特定のスキームには、この既定の動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="95f01-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="95f01-131">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="95f01-131">Configuration Files</span></span>  
 <span data-ttu-id="95f01-132">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="95f01-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f01-133">例</span><span class="sxs-lookup"><span data-stu-id="95f01-133">Example</span></span>  
 <span data-ttu-id="95f01-134">次の例で使用する構成を示しています、 <xref:System.Uri> http スキームのすべての構成設定を削除するクラス。</span><span class="sxs-lookup"><span data-stu-id="95f01-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95f01-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="95f01-135">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="95f01-136">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="95f01-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
