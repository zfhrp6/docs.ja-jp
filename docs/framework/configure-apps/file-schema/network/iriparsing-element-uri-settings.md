---
title: "&lt;iriParsing&gt;要素 (Uri 設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6cd69df9ccba39520cca26bb7042dc2932565336
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="41f6d-102">&lt;iriParsing&gt;要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="41f6d-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="41f6d-103">International Resource Identifier (IRI) 解析が、<xref:System.Uri> に適用されるかどうか、および IRI の解析規則が適用されるどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="41f6d-104">スキーマの階層</span><span class="sxs-lookup"><span data-stu-id="41f6d-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="41f6d-105">\<configuration> 要素</span><span class="sxs-lookup"><span data-stu-id="41f6d-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="41f6d-106">\<Uri > 要素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="41f6d-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="41f6d-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="41f6d-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="41f6d-108">構文</span><span class="sxs-lookup"><span data-stu-id="41f6d-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f6d-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="41f6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="41f6d-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f6d-111">属性</span><span class="sxs-lookup"><span data-stu-id="41f6d-111">Attributes</span></span>  
  
|<span data-ttu-id="41f6d-112">**要素**</span><span class="sxs-lookup"><span data-stu-id="41f6d-112">**Element**</span></span>|<span data-ttu-id="41f6d-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="41f6d-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="41f6d-114">IRI 解析が有効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="41f6d-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="41f6d-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41f6d-116">子要素</span><span class="sxs-lookup"><span data-stu-id="41f6d-116">Child Elements</span></span>  
 <span data-ttu-id="41f6d-117">なし</span><span class="sxs-lookup"><span data-stu-id="41f6d-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f6d-118">親要素</span><span class="sxs-lookup"><span data-stu-id="41f6d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="41f6d-119">**要素**</span><span class="sxs-lookup"><span data-stu-id="41f6d-119">**Element**</span></span>|<span data-ttu-id="41f6d-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="41f6d-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="41f6d-121">uri</span><span class="sxs-lookup"><span data-stu-id="41f6d-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="41f6d-122">.NET Framework での web アドレスの uniform resource identifier (Uri) を使用して表現の処理方法を指定する設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="41f6d-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f6d-123">コメント</span><span class="sxs-lookup"><span data-stu-id="41f6d-123">Remarks</span></span>  
 <span data-ttu-id="41f6d-124">既存の<xref:System.Uri>クラスが .NET Framework 3.5 で拡張されています。</span><span class="sxs-lookup"><span data-stu-id="41f6d-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="41f6d-125">3.0 SP1、および 2.0 SP1 国際リソース識別子 (IRI) および国際化ドメイン名 (IDN) のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="41f6d-126">ユーザーは、IDN を明確にする場合を除きは、現在のユーザーには、.NET Framework 2.0 の動作から変更は表示されませんをサポートします。</span><span class="sxs-lookup"><span data-stu-id="41f6d-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="41f6d-127">これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="41f6d-128">IRI のサポートを有効にするのには、次の 2 つの変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="41f6d-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="41f6d-129">.NET Framework 2.0 ディレクトリ下にある machine.config ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="41f6d-130">IRI 解析規則を適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="41f6d-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="41f6d-131">これは、machine.config ファイルまたは app.config ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="41f6d-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="41f6d-132">IRI 解析を有効にする (有効になっている iriParsing = `true`) 正規化を行うし、RFC 3987 ルールに従って最新 IRI チェック文字です。</span><span class="sxs-lookup"><span data-stu-id="41f6d-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="41f6d-133">既定値は`false`が正規化を行うし、(IPv6 のリテラル) の RFC 2396 に従ってチェックおよび RFC 3986 の文字です。</span><span class="sxs-lookup"><span data-stu-id="41f6d-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="41f6d-134">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="41f6d-134">Configuration Files</span></span>  
 <span data-ttu-id="41f6d-135">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="41f6d-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f6d-136">例</span><span class="sxs-lookup"><span data-stu-id="41f6d-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="41f6d-137">説明</span><span class="sxs-lookup"><span data-stu-id="41f6d-137">Description</span></span>  
 <span data-ttu-id="41f6d-138">次の例で使用する構成を示しています、 <xref:System.Uri> IRI 解析と IDN 名をサポートするクラス。</span><span class="sxs-lookup"><span data-stu-id="41f6d-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="41f6d-139">コード</span><span class="sxs-lookup"><span data-stu-id="41f6d-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41f6d-140">参照</span><span class="sxs-lookup"><span data-stu-id="41f6d-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="41f6d-141">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="41f6d-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
