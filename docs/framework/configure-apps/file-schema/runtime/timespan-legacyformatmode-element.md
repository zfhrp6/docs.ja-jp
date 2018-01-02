---
title: "&lt;TimeSpan_LegacyFormatMode&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be4b26cdc79cef0854221172b8dea0bcc0f50981
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttimespanlegacyformatmodegt-element"></a><span data-ttu-id="6f43a-102">&lt;TimeSpan_LegacyFormatMode&gt;要素</span><span class="sxs-lookup"><span data-stu-id="6f43a-102">&lt;TimeSpan_LegacyFormatMode&gt; Element</span></span>
<span data-ttu-id="6f43a-103">ランタイムが書式設定の操作での従来の動作を保持するかどうかを判断<xref:System.TimeSpan?displayProperty=nameWithType>値。</span><span class="sxs-lookup"><span data-stu-id="6f43a-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="6f43a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6f43a-104">\<configuration></span></span>  
<span data-ttu-id="6f43a-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="6f43a-105">\<runtime></span></span>  
<span data-ttu-id="6f43a-106">< TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="6f43a-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f43a-107">構文</span><span class="sxs-lookup"><span data-stu-id="6f43a-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f43a-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6f43a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f43a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f43a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f43a-110">属性</span><span class="sxs-lookup"><span data-stu-id="6f43a-110">Attributes</span></span>  
  
|<span data-ttu-id="6f43a-111">属性</span><span class="sxs-lookup"><span data-stu-id="6f43a-111">Attribute</span></span>|<span data-ttu-id="6f43a-112">説明</span><span class="sxs-lookup"><span data-stu-id="6f43a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6f43a-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6f43a-114">ランタイムと従来の書式設定動作を使用しているかどうかを示す<xref:System.TimeSpan?displayProperty=nameWithType>値。</span><span class="sxs-lookup"><span data-stu-id="6f43a-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6f43a-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="6f43a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6f43a-116">値</span><span class="sxs-lookup"><span data-stu-id="6f43a-116">Value</span></span>|<span data-ttu-id="6f43a-117">説明</span><span class="sxs-lookup"><span data-stu-id="6f43a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6f43a-118">ランタイムは、従来の書式設定動作を復元できません。</span><span class="sxs-lookup"><span data-stu-id="6f43a-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="6f43a-119">ランタイムは、従来の書式設定動作を復元します。</span><span class="sxs-lookup"><span data-stu-id="6f43a-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f43a-120">子要素</span><span class="sxs-lookup"><span data-stu-id="6f43a-120">Child Elements</span></span>  
 <span data-ttu-id="6f43a-121">なし。</span><span class="sxs-lookup"><span data-stu-id="6f43a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f43a-122">親要素</span><span class="sxs-lookup"><span data-stu-id="6f43a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6f43a-123">要素</span><span class="sxs-lookup"><span data-stu-id="6f43a-123">Element</span></span>|<span data-ttu-id="6f43a-124">説明</span><span class="sxs-lookup"><span data-stu-id="6f43a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6f43a-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6f43a-126">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="6f43a-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f43a-127">コメント</span><span class="sxs-lookup"><span data-stu-id="6f43a-127">Remarks</span></span>  
 <span data-ttu-id="6f43a-128">以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 <xref:System.TimeSpan?displayProperty=nameWithType> implements 構造体、<xref:System.IFormattable>インターフェイスと書式設定の標準およびカスタムの書式指定文字列の操作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6f43a-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="6f43a-129">解析方法には、サポートされていない書式指定子または書式指定文字列が検出されると、スロー、<xref:System.FormatException>です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="6f43a-130">.NET Framework の以前のバージョンで、<xref:System.TimeSpan>構造体が実装されていない<xref:System.IFormattable>し、書式指定文字列をサポートしていませんでした。</span><span class="sxs-lookup"><span data-stu-id="6f43a-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="6f43a-131">ただし、多くの開発者誤ってと想定<xref:System.TimeSpan>書式指定文字列のセットをサポートして、使用される[複合書式指定操作](../../../../../docs/standard/base-types/composite-formatting.md)などのメソッドと<xref:System.String.Format%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f43a-132">通常は、型が実装する場合<xref:System.IFormattable>書式指定文字列、文字列が通常スローをサポートされていない形式で書式指定メソッドの呼び出しをサポートしていると、<xref:System.FormatException>です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="6f43a-133">ただし、ため<xref:System.TimeSpan>実装されていない<xref:System.IFormattable>、ランタイムは、書式指定文字列は無視され、代わりに呼び出されます、<xref:System.TimeSpan.ToString?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6f43a-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6f43a-134">これには、書式指定文字列に書式設定操作には影響はありません、その存在しなかったになることを意味する<xref:System.FormatException>です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="6f43a-135">場合はレガシ コードが、複合書式指定メソッドと、無効な形式の文字列を渡すし、そのコードを再コンパイルすることはできませんが、使用することができます、`<TimeSpan_LegacyFormatMode>`要素、従来の復元を<xref:System.TimeSpan>動作します。</span><span class="sxs-lookup"><span data-stu-id="6f43a-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="6f43a-136">設定すると、`enabled`にするには、この要素の属性`true`、複合書式指定メソッドの結果への呼び出しで<xref:System.TimeSpan.ToString?displayProperty=nameWithType>なく<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>、および<xref:System.FormatException>はスローされません。</span><span class="sxs-lookup"><span data-stu-id="6f43a-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f43a-137">例</span><span class="sxs-lookup"><span data-stu-id="6f43a-137">Example</span></span>  
 <span data-ttu-id="6f43a-138">次の例のインスタンスを作成、<xref:System.TimeSpan>オブジェクトを使用して書式試みます、<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>メソッドでサポートされていない標準書式指定文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="6f43a-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="6f43a-139">例を実行すると、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]または以前のバージョンで、次の出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="6f43a-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="6f43a-140">これとは異なります著しく出力例を実行する場合、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="6f43a-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="6f43a-141">ただしの例を次の構成ファイルを追加する場合のディレクトリで例を実行し、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]以降のバージョンが、出力は、例は、実行時に生成されるものと同じまたは[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6f43a-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f43a-142">参照</span><span class="sxs-lookup"><span data-stu-id="6f43a-142">See Also</span></span>  
 [<span data-ttu-id="6f43a-143">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6f43a-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6f43a-144">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="6f43a-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
