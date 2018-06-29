---
title: XML Value プロパティ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 927158f940d9b96cd06873c7d3e710be91b887e9
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071619"
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="8e15b-102">XML Value プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e15b-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="8e15b-103">コレクションの最初の要素の値にアクセスできるように<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e15b-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e15b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8e15b-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="8e15b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="8e15b-105">Parts</span></span>  
  
|<span data-ttu-id="8e15b-106">用語</span><span class="sxs-lookup"><span data-stu-id="8e15b-106">Term</span></span>|<span data-ttu-id="8e15b-107">定義</span><span class="sxs-lookup"><span data-stu-id="8e15b-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="8e15b-108">必須。</span><span class="sxs-lookup"><span data-stu-id="8e15b-108">Required.</span></span> <span data-ttu-id="8e15b-109"><xref:System.Xml.Linq.XElement> オブジェクトのコレクション。</span><span class="sxs-lookup"><span data-stu-id="8e15b-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="8e15b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8e15b-110">Return Value</span></span>  
 <span data-ttu-id="8e15b-111">A `String` 、コレクションの最初の要素の値を格納しているか、`Nothing`コレクションが空の場合。</span><span class="sxs-lookup"><span data-stu-id="8e15b-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e15b-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="8e15b-112">Remarks</span></span>  
 <span data-ttu-id="8e15b-113"><xref:System.Xml.Linq.XElement.Value%2A>プロパティでは、最初の要素のコレクション内の値にアクセスする簡単な<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e15b-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8e15b-114">まず、このプロパティは、コレクションに少なくとも 1 つのオブジェクトが含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e15b-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="8e15b-115">このプロパティを返しますのかどうか、コレクションが空、`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="8e15b-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="8e15b-116">このプロパティがの値を返しますそれ以外の場合、<xref:System.Xml.Linq.XElement.Value%2A>コレクションの最初の要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e15b-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e15b-117">使用して XML 属性の値にアクセスするときに、'\@' 識別子、属性が返される値として、`String`を明示的に指定する必要はありませんし、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e15b-117">When you access the value of an XML attribute using the '\@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="8e15b-118">コレクション内の他の要素にアクセスするには、XML 拡張インデクサー プロパティを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="8e15b-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="8e15b-119">詳細については、次を参照してください。[拡張インデクサー プロパティ](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="8e15b-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="8e15b-120">継承</span><span class="sxs-lookup"><span data-stu-id="8e15b-120">Inheritance</span></span>  
 <span data-ttu-id="8e15b-121">ほとんどのユーザーが実装する必要はありません<xref:System.Collections.Generic.IEnumerable%601>、およびそのためこのセクションを無視することができます。</span><span class="sxs-lookup"><span data-stu-id="8e15b-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="8e15b-122"><xref:System.Xml.Linq.XElement.Value%2A>拡張機能を実装する型のプロパティは、`IEnumerable(Of XElement)`です。</span><span class="sxs-lookup"><span data-stu-id="8e15b-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="8e15b-123">拡張メソッドのバインディングと同様には、この拡張機能プロパティのバインディング: 型、インターフェイスの 1 つを実装して"Value"という名前を持つプロパティが定義されて、そのプロパティが優先順位、拡張機能のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e15b-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="8e15b-124">つまり、この<xref:System.Xml.Linq.XElement.Value%2A>プロパティを実装するクラスの新しいプロパティを定義することによりオーバーライドできます`IEnumerable(Of XElement)`です。</span><span class="sxs-lookup"><span data-stu-id="8e15b-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e15b-125">例</span><span class="sxs-lookup"><span data-stu-id="8e15b-125">Example</span></span>  
 <span data-ttu-id="8e15b-126">次の例を使用する方法を示しています、<xref:System.Xml.Linq.XElement.Value%2A>プロパティのコレクションの最初のノードへのアクセスを<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e15b-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="8e15b-127">例では、すべての子ノードがという名前のコレクションを取得する子軸プロパティを使用して`phone`内にある、`contact`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e15b-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="8e15b-128">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e15b-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="8e15b-129">例</span><span class="sxs-lookup"><span data-stu-id="8e15b-129">Example</span></span>  
 <span data-ttu-id="8e15b-130">次の例は、のコレクションから、XML 属性の値を取得する方法を示しています。<xref:System.Xml.Linq.XAttribute>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8e15b-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="8e15b-131">この例の値を表示する属性軸プロパティを使用して、`type`のすべての属性、`phone`要素。</span><span class="sxs-lookup"><span data-stu-id="8e15b-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="8e15b-132">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e15b-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="8e15b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e15b-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="8e15b-134">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e15b-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="8e15b-135">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="8e15b-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="8e15b-136">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="8e15b-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="8e15b-137">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="8e15b-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="8e15b-138">拡張インデクサー プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e15b-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="8e15b-139">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e15b-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="8e15b-140">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8e15b-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
