---
title: "&lt;追加&gt;schemeSettings (Uri 設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ce4cc33d054e74fc9868a16764e744daf260c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="c695e-102">&lt;追加&gt;schemeSettings (Uri 設定) の要素</span><span class="sxs-lookup"><span data-stu-id="c695e-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="c695e-103">スキーム名にスキームの設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="c695e-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="c695e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c695e-104">\<configuration></span></span>  
<span data-ttu-id="c695e-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="c695e-105">\<uri></span></span>  
<span data-ttu-id="c695e-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="c695e-106">\<schemeSettings></span></span>  
<span data-ttu-id="c695e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c695e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c695e-108">構文</span><span class="sxs-lookup"><span data-stu-id="c695e-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c695e-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c695e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c695e-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c695e-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c695e-111">属性</span><span class="sxs-lookup"><span data-stu-id="c695e-111">Attributes</span></span>  
  
|<span data-ttu-id="c695e-112">属性</span><span class="sxs-lookup"><span data-stu-id="c695e-112">Attribute</span></span>|<span data-ttu-id="c695e-113">説明</span><span class="sxs-lookup"><span data-stu-id="c695e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c695e-114">name</span><span class="sxs-lookup"><span data-stu-id="c695e-114">name</span></span>|<span data-ttu-id="c695e-115">スキーム名は、この設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c695e-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="c695e-116">だけでサポートされる値は名前 ="http"、name ="https"。</span><span class="sxs-lookup"><span data-stu-id="c695e-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="c695e-117">{属性名}属性</span><span class="sxs-lookup"><span data-stu-id="c695e-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="c695e-118">値</span><span class="sxs-lookup"><span data-stu-id="c695e-118">Value</span></span>|<span data-ttu-id="c695e-119">説明</span><span class="sxs-lookup"><span data-stu-id="c695e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c695e-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="c695e-120">genericUriParserOptions</span></span>|<span data-ttu-id="c695e-121">このスキーム パーサー オプション。</span><span class="sxs-lookup"><span data-stu-id="c695e-121">The parser options for this scheme.</span></span> <span data-ttu-id="c695e-122">のみサポートされている値が genericUriParserOptions ="DontUnescapePathDotsAndSlashes"です。</span><span class="sxs-lookup"><span data-stu-id="c695e-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c695e-123">子要素</span><span class="sxs-lookup"><span data-stu-id="c695e-123">Child Elements</span></span>  
 <span data-ttu-id="c695e-124">なし</span><span class="sxs-lookup"><span data-stu-id="c695e-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c695e-125">親要素</span><span class="sxs-lookup"><span data-stu-id="c695e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c695e-126">要素</span><span class="sxs-lookup"><span data-stu-id="c695e-126">Element</span></span>|<span data-ttu-id="c695e-127">説明</span><span class="sxs-lookup"><span data-stu-id="c695e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c695e-128">\<schemeSettings> 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="c695e-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="c695e-129"><xref:System.Uri> が特定のスキームに解析される方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="c695e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c695e-130">コメント</span><span class="sxs-lookup"><span data-stu-id="c695e-130">Remarks</span></span>  
 <span data-ttu-id="c695e-131">既定では、<xref:System.Uri?displayProperty=nameWithType>クラス エスケープを解除 % は、パスの圧縮を実行する前にパスの区切り記号をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="c695e-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="c695e-132">これは、次のような攻撃に対するセキュリティ機構として実装されていました。</span><span class="sxs-lookup"><span data-stu-id="c695e-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c695e-133">この URI が渡される場合は、モジュール % は処理されません。 エンコードした文字を正しく、サーバーにより実行されている次のコマンドを可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c695e-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="c695e-134">このため、<xref:System.Uri?displayProperty=nameWithType>クラスの最初のエスケープを解除パス区切り記号とパスの圧縮を適用します。</span><span class="sxs-lookup"><span data-stu-id="c695e-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="c695e-135">上への悪意のある URL を渡した結果<xref:System.Uri?displayProperty=nameWithType>クラスのコンス トラクターの結果で、次の URI:</span><span class="sxs-lookup"><span data-stu-id="c695e-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="c695e-136">いないエスケープ解除パーセント エンコードされたパスの区切り記号 schemeSettings 構成オプションを使用して、特定のスキームには、この既定の動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="c695e-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c695e-137">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="c695e-137">Configuration Files</span></span>  
 <span data-ttu-id="c695e-138">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c695e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c695e-139">例</span><span class="sxs-lookup"><span data-stu-id="c695e-139">Example</span></span>  
 <span data-ttu-id="c695e-140">次の例で使用する構成を示しています、 <xref:System.Uri> http スキームのパーセントでエンコードされたパスの区切り記号をエスケープしないをサポートするクラス。</span><span class="sxs-lookup"><span data-stu-id="c695e-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c695e-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="c695e-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="c695e-142">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c695e-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
