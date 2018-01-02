---
title: "&lt;CompatSortNLSVersion&gt;要素"
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
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 613c02abd7d200bd2e1bf10f85a1aa84994583f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="9a3a1-102">&lt;CompatSortNLSVersion&gt;要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="9a3a1-103">文字列比較の実行時に、ランタイムがレガシ並べ替え順序を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="9a3a1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9a3a1-104">\<configuration></span></span>  
<span data-ttu-id="9a3a1-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="9a3a1-105">\<runtime></span></span>  
<span data-ttu-id="9a3a1-106">\<CompatSortNLSVersion > 要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3a1-107">構文</span><span class="sxs-lookup"><span data-stu-id="9a3a1-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a3a1-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9a3a1-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a3a1-110">属性</span><span class="sxs-lookup"><span data-stu-id="9a3a1-110">Attributes</span></span>  
  
|<span data-ttu-id="9a3a1-111">属性</span><span class="sxs-lookup"><span data-stu-id="9a3a1-111">Attribute</span></span>|<span data-ttu-id="9a3a1-112">説明</span><span class="sxs-lookup"><span data-stu-id="9a3a1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9a3a1-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9a3a1-114">並べ替え順序が使用されるロケール ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9a3a1-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="9a3a1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9a3a1-116">値</span><span class="sxs-lookup"><span data-stu-id="9a3a1-116">Value</span></span>|<span data-ttu-id="9a3a1-117">説明</span><span class="sxs-lookup"><span data-stu-id="9a3a1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9a3a1-118">4096</span><span class="sxs-lookup"><span data-stu-id="9a3a1-118">4096</span></span>|<span data-ttu-id="9a3a1-119">代替の並べ替え順序を表すロケール ID。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="9a3a1-120">この場合、4096 は、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] およびそれ以前のバージョンの並べ替え順序を表します。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a3a1-121">子要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-121">Child Elements</span></span>  
 <span data-ttu-id="9a3a1-122">なし。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a3a1-123">親要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9a3a1-124">要素</span><span class="sxs-lookup"><span data-stu-id="9a3a1-124">Element</span></span>|<span data-ttu-id="9a3a1-125">説明</span><span class="sxs-lookup"><span data-stu-id="9a3a1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9a3a1-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9a3a1-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a3a1-128">コメント</span><span class="sxs-lookup"><span data-stu-id="9a3a1-128">Remarks</span></span>  
 <span data-ttu-id="9a3a1-129">文字列比較、並べ替え、および大文字と小文字の操作によって実行されるため、<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>クラス内で、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]などの Unicode 5.1 規格、文字列比較メソッドの結果に準拠している<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>と<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>異なる場合があります.NET Framework の以前のバージョン。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="9a3a1-130">アプリケーションがレガシ動作に依存している場合は、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 要素をアプリケーションの構成ファイルに含めることで、`<CompatSortNLSVersion>` およびそれ以前のバージョンで使用されていた文字列の比較および並べ替えの規則を復元できます。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a3a1-131">文字列の比較および並べ替えのレガシ規則を復元する場合は、ローカル システムで sort00001000.dll ダイナミック リンク ライブラリも使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="9a3a1-132">アプリケーション ドメインを作成するときに、文字列 "NetFx40_Legacy20SortingBehavior" を <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> メソッドに渡すことで、文字列の比較および並べ替えのレガシ規則を特定のアプリケーション ドメインで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a3a1-133">例</span><span class="sxs-lookup"><span data-stu-id="9a3a1-133">Example</span></span>  
 <span data-ttu-id="9a3a1-134">次の例では、2 つの <xref:System.String> オブジェクトをインスタンス化して、<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> メソッドを呼び出し、現在のカルチャの規則を使用してそれらのオブジェクトを比較する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="9a3a1-135">[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] で例を実行すると、次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="9a3a1-136">これは、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] で例を実行したときに表示される出力とはまったく異なります。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="9a3a1-137">ただし、例のディレクトリに次の構成ファイルを追加し、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] で例を実行すると、[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] で例を実行した場合と同じ出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a3a1-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a3a1-138">参照</span><span class="sxs-lookup"><span data-stu-id="9a3a1-138">See Also</span></span>  
 [<span data-ttu-id="9a3a1-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="9a3a1-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="9a3a1-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9a3a1-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
