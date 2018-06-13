---
title: x:XData 組み込み XAML 型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565364"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="c4651-102">x:XData 組み込み XAML 型</span><span class="sxs-lookup"><span data-stu-id="c4651-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="c4651-103">XAML の運用環境での XML データ アイランドの配置を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c4651-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="c4651-104">内の XML 要素`x:XData`機能を実行する既定の XAML 名前空間の一部、またはその他の XAML 名前空間かのように XAML プロセッサで扱うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c4651-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="c4651-105">`x:XData` 整形式の任意の XML を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c4651-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c4651-106">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="c4651-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c4651-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="c4651-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="c4651-108">囲まれたデータ アイランドの単一のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c4651-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="c4651-109">ほとんどの最終的なコンシューマーの単一のルートがない XML が無効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c4651-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="c4651-110">具体的には、単一のルートは、必要な場合、`x:XData`では、XML データ ソースの WPF または他の多くのテクノロジにも、XML ソース データ バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="c4651-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="c4651-111">任意。</span><span class="sxs-lookup"><span data-stu-id="c4651-111">Optional.</span></span> <span data-ttu-id="c4651-112">XML データを表す XML です。</span><span class="sxs-lookup"><span data-stu-id="c4651-112">XML that represents the XML data.</span></span> <span data-ttu-id="c4651-113">要素のデータとして格納できる要素の任意の数と、入れ子になった要素は、他の要素に含まれていることができます。ただし、XML の一般的な規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="c4651-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4651-114">コメント</span><span class="sxs-lookup"><span data-stu-id="c4651-114">Remarks</span></span>  
 <span data-ttu-id="c4651-115">内の XML 要素、`x:XData`オブジェクトには、すべての可能な名前空間およびプレフィックス内でデータを含む XMLDOM の再を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c4651-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="c4651-116">XML データにプログラムでアクセスし、`x:XData`組み込み XAML 型を .NET Framework XAML サービスでは、<xref:System.Windows.Markup.XData>クラスです。</span><span class="sxs-lookup"><span data-stu-id="c4651-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="c4651-117">WPF の使用上の注意</span><span class="sxs-lookup"><span data-stu-id="c4651-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="c4651-118">`x:XData`オブジェクトは、主の子オブジェクトとして使用、 <xref:System.Windows.Data.XmlDataProvider>、または別の方法としての子オブジェクトとして、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>プロパティ (XAML では、これは通常構文で表されるプロパティ要素)。</span><span class="sxs-lookup"><span data-stu-id="c4651-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="c4651-119">データは、新しい既定の XML 名前空間 (空の文字列に設定) にデータ アイランド内のベースの XML 名前空間を再定義しなければなりません通常します。</span><span class="sxs-lookup"><span data-stu-id="c4651-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="c4651-120">これは、単純なデータ諸島ための最も簡単な<xref:System.Windows.Data.Binding.XPath%2A>参照およびデータにバインドするために使用する式は、プレフィックスを含めることを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="c4651-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="c4651-121">複雑なデータ アイランドは、データの複数のプレフィックスを定義して、ルートにある XML 名前空間の特定のプレフィックスを使用して可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c4651-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="c4651-122">この場合、すべて<xref:System.Windows.Data.Binding.XPath%2A>式の参照は、適切な名前空間マッピング プレフィックスを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4651-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="c4651-123">詳しくは、「 [データ バインディングの概要](../../../docs/framework/wpf/data/data-binding-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c4651-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c4651-124">技術的には、`x:XData`型のプロパティの内容として使用できる<xref:System.Xml.Serialization.IXmlSerializable>です。</span><span class="sxs-lookup"><span data-stu-id="c4651-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="c4651-125">ただし、<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>のみ著名な実装です。</span><span class="sxs-lookup"><span data-stu-id="c4651-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4651-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4651-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="c4651-127">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="c4651-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c4651-128">バインドのマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="c4651-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
