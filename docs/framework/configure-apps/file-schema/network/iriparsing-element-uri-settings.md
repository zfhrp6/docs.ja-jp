---
title: '&lt;iriParsing&gt;要素 (Uri 設定)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f05f7e35d69f789d3ebb371689aafbc84004b732
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743304"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="63c15-102">&lt;iriParsing&gt;要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="63c15-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="63c15-103">International Resource Identifier (IRI) 解析が、<xref:System.Uri> に適用されるかどうか、および IRI の解析規則が適用されるどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="63c15-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="63c15-104">スキーマの階層</span><span class="sxs-lookup"><span data-stu-id="63c15-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="63c15-105">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="63c15-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="63c15-106">\<Uri > 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="63c15-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="63c15-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="63c15-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="63c15-108">構文</span><span class="sxs-lookup"><span data-stu-id="63c15-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c15-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="63c15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="63c15-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="63c15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c15-111">属性</span><span class="sxs-lookup"><span data-stu-id="63c15-111">Attributes</span></span>  
  
|<span data-ttu-id="63c15-112">**要素**</span><span class="sxs-lookup"><span data-stu-id="63c15-112">**Element**</span></span>|<span data-ttu-id="63c15-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="63c15-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="63c15-114">IRI 解析が有効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="63c15-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="63c15-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="63c15-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63c15-116">子要素</span><span class="sxs-lookup"><span data-stu-id="63c15-116">Child Elements</span></span>  
 <span data-ttu-id="63c15-117">なし</span><span class="sxs-lookup"><span data-stu-id="63c15-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63c15-118">親要素</span><span class="sxs-lookup"><span data-stu-id="63c15-118">Parent Elements</span></span>  
  
|<span data-ttu-id="63c15-119">**要素**</span><span class="sxs-lookup"><span data-stu-id="63c15-119">**Element**</span></span>|<span data-ttu-id="63c15-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="63c15-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="63c15-121">Uri</span><span class="sxs-lookup"><span data-stu-id="63c15-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="63c15-122">.NET Framework での web アドレスの uniform resource identifier (Uri) を使用して表現の処理方法を指定する設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="63c15-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c15-123">コメント</span><span class="sxs-lookup"><span data-stu-id="63c15-123">Remarks</span></span>  
 <span data-ttu-id="63c15-124">既存の<xref:System.Uri>クラスが .NET Framework 3.5 で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="63c15-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="63c15-125">3.0 SP1、および 2.0 SP1 国際リソース識別子 (IRI) および国際化ドメイン名 (IDN) のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="63c15-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="63c15-126">ユーザーは、IDN を明確にする場合を除きは、現在のユーザーには、.NET Framework 2.0 の動作から変更は表示されませんをサポートします。</span><span class="sxs-lookup"><span data-stu-id="63c15-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="63c15-127">これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。</span><span class="sxs-lookup"><span data-stu-id="63c15-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="63c15-128">IRI のサポートを有効にするのには、次の 2 つの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="63c15-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="63c15-129">.NET Framework 2.0 ディレクトリ下にある machine.config ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="63c15-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="63c15-130">IRI 解析規則を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="63c15-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="63c15-131">これは、machine.config ファイルまたは app.config ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="63c15-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="63c15-132">IRI 解析を有効にする (有効になっている iriParsing = `true`) 正規化を行うし、RFC 3987 ルールに従って最新 IRI チェック文字です。</span><span class="sxs-lookup"><span data-stu-id="63c15-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="63c15-133">既定値は`false`が正規化を行うし、(IPv6 のリテラル) の RFC 2396 に従ってチェックおよび RFC 3986 の文字です。</span><span class="sxs-lookup"><span data-stu-id="63c15-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="63c15-134">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="63c15-134">Configuration Files</span></span>  
 <span data-ttu-id="63c15-135">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="63c15-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c15-136">例</span><span class="sxs-lookup"><span data-stu-id="63c15-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="63c15-137">説明</span><span class="sxs-lookup"><span data-stu-id="63c15-137">Description</span></span>  
 <span data-ttu-id="63c15-138">次の例で使用する構成を示しています、 <xref:System.Uri> IRI 解析と IDN 名をサポートするクラス。</span><span class="sxs-lookup"><span data-stu-id="63c15-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="63c15-139">コード</span><span class="sxs-lookup"><span data-stu-id="63c15-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63c15-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="63c15-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="63c15-141">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="63c15-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
