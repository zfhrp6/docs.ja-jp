---
title: 拡張インデクサー プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a7718a4aa85a000d0c83e8c9556a448ceaf13c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603471"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="44320-102">拡張インデクサー プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44320-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="44320-103">コレクション内の個々の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="44320-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44320-104">構文</span><span class="sxs-lookup"><span data-stu-id="44320-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="44320-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="44320-105">Parts</span></span>  
  
|<span data-ttu-id="44320-106">用語</span><span class="sxs-lookup"><span data-stu-id="44320-106">Term</span></span>|<span data-ttu-id="44320-107">定義</span><span class="sxs-lookup"><span data-stu-id="44320-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="44320-108">必須。</span><span class="sxs-lookup"><span data-stu-id="44320-108">Required.</span></span> <span data-ttu-id="44320-109">クエリ可能なコレクションです。</span><span class="sxs-lookup"><span data-stu-id="44320-109">A queryable collection.</span></span> <span data-ttu-id="44320-110">実装するコレクションである、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>です。</span><span class="sxs-lookup"><span data-stu-id="44320-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="44320-111">(</span><span class="sxs-lookup"><span data-stu-id="44320-111">(</span></span>|<span data-ttu-id="44320-112">必須。</span><span class="sxs-lookup"><span data-stu-id="44320-112">Required.</span></span> <span data-ttu-id="44320-113">インデクサー プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="44320-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="44320-114">必須。</span><span class="sxs-lookup"><span data-stu-id="44320-114">Required.</span></span> <span data-ttu-id="44320-115">コレクションの要素の 0 から始まる位置を示す整数式。</span><span class="sxs-lookup"><span data-stu-id="44320-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="44320-116">)</span><span class="sxs-lookup"><span data-stu-id="44320-116">)</span></span>|<span data-ttu-id="44320-117">必須。</span><span class="sxs-lookup"><span data-stu-id="44320-117">Required.</span></span> <span data-ttu-id="44320-118">インデクサー プロパティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="44320-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="44320-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="44320-119">Return Value</span></span>  
 <span data-ttu-id="44320-120">コレクション内の指定された場所からオブジェクトまたは`Nothing`場合は、インデックスが範囲外です。</span><span class="sxs-lookup"><span data-stu-id="44320-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44320-121">コメント</span><span class="sxs-lookup"><span data-stu-id="44320-121">Remarks</span></span>  
 <span data-ttu-id="44320-122">拡張インデクサー プロパティを使用して、コレクション内の個々 の要素にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="44320-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="44320-123">このインデクサー プロパティは、通常の出力 XML 軸プロパティの使用です。</span><span class="sxs-lookup"><span data-stu-id="44320-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="44320-124">XML 子と XML 子孫軸プロパティのコレクションを返す<xref:System.Xml.Linq.XElement>オブジェクトまたは属性の値。</span><span class="sxs-lookup"><span data-stu-id="44320-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="44320-125">Visual Basic コンパイラでは、拡張機能インデクサー プロパティを変換への呼び出しを`ElementAtOrDefault`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="44320-125">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="44320-126">配列インデクサーとは異なり、`ElementAtOrDefault`メソッドを返します。`Nothing`場合は、インデックスが範囲外です。</span><span class="sxs-lookup"><span data-stu-id="44320-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="44320-127">この動作は、コレクション内の要素の数を容易に判別できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="44320-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="44320-128">実装するコレクションの拡張機能プロパティのように、このインデクサー プロパティは<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>: コレクションは、インデクサーまたは既定のプロパティを持たない場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="44320-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="44320-129">コレクションの最初の要素の値にアクセスする<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、XML を使用する`Value`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="44320-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="44320-130">詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="44320-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44320-131">例</span><span class="sxs-lookup"><span data-stu-id="44320-131">Example</span></span>  
 <span data-ttu-id="44320-132">次の例は、拡張機能インデクサーを使用して、2 番目の子ノードのコレクションにアクセスする方法を示しています。<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="44320-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="44320-133">コレクションには、すべての子要素がという名前を取得する子軸プロパティを使用してアクセス`phone`で、`contact`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="44320-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="44320-134">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44320-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="44320-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="44320-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="44320-136">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="44320-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="44320-137">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="44320-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="44320-138">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="44320-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="44320-139">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="44320-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
