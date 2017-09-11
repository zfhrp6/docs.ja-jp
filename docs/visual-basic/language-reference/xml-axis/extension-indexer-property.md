---
title: "拡張インデクサー プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 71c16d3f1b93647154bdead4a85d1117b5f6c463
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="aa4ec-102">拡張インデクサー プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa4ec-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="aa4ec-103">コレクション内の個々の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa4ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa4ec-104">Syntax</span></span>  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="aa4ec-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="aa4ec-105">Parts</span></span>  
  
|<span data-ttu-id="aa4ec-106">用語</span><span class="sxs-lookup"><span data-stu-id="aa4ec-106">Term</span></span>|<span data-ttu-id="aa4ec-107">定義</span><span class="sxs-lookup"><span data-stu-id="aa4ec-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="aa4ec-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-108">Required.</span></span> <span data-ttu-id="aa4ec-109">クエリ可能なコレクションです。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-109">A queryable collection.</span></span> <span data-ttu-id="aa4ec-110"><xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>を実装するコレクションは、</span><span class="sxs-lookup"><span data-stu-id="aa4ec-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="aa4ec-111">(</span><span class="sxs-lookup"><span data-stu-id="aa4ec-111">(</span></span>|<span data-ttu-id="aa4ec-112">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-112">Required.</span></span> <span data-ttu-id="aa4ec-113">インデクサーの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="aa4ec-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-114">Required.</span></span> <span data-ttu-id="aa4ec-115">コレクションの要素の&0; から始まる位置を示す整数式。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="aa4ec-116">)</span><span class="sxs-lookup"><span data-stu-id="aa4ec-116">)</span></span>|<span data-ttu-id="aa4ec-117">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-117">Required.</span></span> <span data-ttu-id="aa4ec-118">インデクサーの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="aa4ec-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa4ec-119">Return Value</span></span>  
 <span data-ttu-id="aa4ec-120">コレクション内の指定された場所からオブジェクトまたは`Nothing`場合は、インデックスが範囲外です。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa4ec-121">コメント</span><span class="sxs-lookup"><span data-stu-id="aa4ec-121">Remarks</span></span>  
 <span data-ttu-id="aa4ec-122">拡張インデクサー プロパティを使用して、コレクション内の個々 の要素にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="aa4ec-123">このインデクサーは通常、XML 軸プロパティの出力時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="aa4ec-124">XML 子と XML 子孫軸プロパティのコレクションを返す<xref:System.Xml.Linq.XElement>オブジェクトまたは属性の値</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="aa4ec-125">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、拡張機能インデクサー プロパティを変換への呼び出しが、`ElementAtOrDefault`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts extension indexer properties to calls to the`ElementAtOrDefault` method.</span></span> <span data-ttu-id="aa4ec-126">配列のインデクサーとは異なり、`ElementAtOrDefault`メソッドが返す`Nothing`場合は、インデックスが範囲外です。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-126">Unlike an array indexer, the`ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="aa4ec-127">この動作は、コレクション内の要素の数を簡単に判断できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="aa4ec-128">このインデクサーを実装するコレクションのための拡張機能プロパティのように、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>: コレクションには、インデクサーまたは既定のプロパティがあるない場合にのみに使用されます</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="aa4ec-129">コレクションの最初の要素の値にアクセスする<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、XML を使用する`Value`プロパティ</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="aa4ec-130">詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa4ec-131">例</span><span class="sxs-lookup"><span data-stu-id="aa4ec-131">Example</span></span>  
 <span data-ttu-id="aa4ec-132">次の例は、拡張機能インデクサーを使用して、2 番目の子ノードのコレクションにアクセスする方法を示しています<xref:System.Xml.Linq.XElement>オブジェクト。</xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="aa4ec-133">という名前のすべての子要素を取得する子軸プロパティを使用して、コレクションにアクセス`phone`で、`contact`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 <span data-ttu-id="aa4ec-134">[!code-vb[VbXMLSamples #&24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="aa4ec-134">[!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]</span></span>  
  
 <span data-ttu-id="aa4ec-135">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa4ec-135">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="aa4ec-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa4ec-136">See Also</span></span>  
 <span data-ttu-id="aa4ec-137"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="aa4ec-137"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="aa4ec-138"> [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="aa4ec-138"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="aa4ec-139"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="aa4ec-139"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="aa4ec-140"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="aa4ec-140"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="aa4ec-141"> [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span><span class="sxs-lookup"><span data-stu-id="aa4ec-141"> [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)</span></span>
