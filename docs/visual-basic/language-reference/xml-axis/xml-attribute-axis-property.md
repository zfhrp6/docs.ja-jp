---
title: "XML 属性軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
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
ms.openlocfilehash: a3c327f4448287bcf6c45b9b6e26a1ef9ba13c16
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="a93a0-102">XML 属性軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a93a0-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="a93a0-103">属性の値にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素に、または<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a93a0-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a93a0-104">構文</span><span class="sxs-lookup"><span data-stu-id="a93a0-104">Syntax</span></span>  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="a93a0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a93a0-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="a93a0-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-106">Required.</span></span> <span data-ttu-id="a93a0-107"><xref:System.Xml.Linq.XElement>オブジェクトまたは一連の<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a93a0-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="a93a0-108">.@</span><span class="sxs-lookup"><span data-stu-id="a93a0-108">.@</span></span>  
 <span data-ttu-id="a93a0-109">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-109">Required.</span></span> <span data-ttu-id="a93a0-110">属性軸プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="a93a0-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-111">Optional.</span></span> <span data-ttu-id="a93a0-112">属性の名前の先頭を示しますと`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="a93a0-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-113">Required.</span></span> <span data-ttu-id="a93a0-114">フォームにアクセスする属性の名前 [`prefix`:]`name`します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="a93a0-115">パーツ</span><span class="sxs-lookup"><span data-stu-id="a93a0-115">Part</span></span>|<span data-ttu-id="a93a0-116">説明</span><span class="sxs-lookup"><span data-stu-id="a93a0-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="a93a0-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-117">Optional.</span></span> <span data-ttu-id="a93a0-118">属性の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="a93a0-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="a93a0-119">`Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a93a0-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="a93a0-120">必須です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-120">Required.</span></span> <span data-ttu-id="a93a0-121">属性のローカル名。</span><span class="sxs-lookup"><span data-stu-id="a93a0-121">Local attribute name.</span></span> <span data-ttu-id="a93a0-122">参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="a93a0-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-123">Optional.</span></span> <span data-ttu-id="a93a0-124">属性の名前の末尾を示すときに`attribute`で有効な識別子ではありません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a93a0-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="a93a0-125">Return Value</span></span>  
 <span data-ttu-id="a93a0-126">値を含む文字列`attribute`します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="a93a0-127">属性名が存在しない場合`Nothing`が返されます。</span><span class="sxs-lookup"><span data-stu-id="a93a0-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a93a0-128">コメント</span><span class="sxs-lookup"><span data-stu-id="a93a0-128">Remarks</span></span>  
 <span data-ttu-id="a93a0-129">XML 属性軸プロパティを使用するには名を使用して属性の値にアクセスする、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素から、または<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a93a0-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="a93a0-130">名前で属性値を取得またはスコアで始まる新しい名前を指定することによって要素に新しい属性を追加することができます、@ 識別子。</span><span class="sxs-lookup"><span data-stu-id="a93a0-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="a93a0-131">使用する XML 属性を参照するとき、@ 識別子、属性の値が文字列として返され、明示的に指定する必要はありません、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティ</xref:System.Xml.Linq.XAttribute.Value%2A>。</span><span class="sxs-lookup"><span data-stu-id="a93a0-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="a93a0-132">XML 属性の名前付け規則と名前付け規則について異なる[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]識別子。</span><span class="sxs-lookup"><span data-stu-id="a93a0-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identifiers.</span></span> <span data-ttu-id="a93a0-133">Visual Basic の有効な識別子ではない名前を持つ XML 属性にアクセスするには、山かっこで名前を囲む (\<と >)。</span><span class="sxs-lookup"><span data-stu-id="a93a0-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="a93a0-134">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="a93a0-134">XML Namespaces</span></span>  
 <span data-ttu-id="a93a0-135">属性軸プロパティの名前は、XML 名前空間プレフィックスだけを使用して、グローバルに宣言を使用できます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="a93a0-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="a93a0-136">XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a93a0-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="a93a0-137">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93a0-138">例</span><span class="sxs-lookup"><span data-stu-id="a93a0-138">Example</span></span>  
 <span data-ttu-id="a93a0-139">次の例は、XML 属性の名前付きの値を取得する方法を示しています。`type`という XML 要素のコレクションから`phone`します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 <span data-ttu-id="a93a0-140">[!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a93a0-140">[!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="a93a0-141">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a93a0-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="a93a0-142">例</span><span class="sxs-lookup"><span data-stu-id="a93a0-142">Example</span></span>  
 <span data-ttu-id="a93a0-143">次の例では、両方の XML 要素の属性の宣言の一部として、XML では、動的に、属性のインスタンスを追加して作成する方法、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a93a0-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="a93a0-144">`type`属性が宣言によって作成されると、 `owne`r 属性を動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-144">The `type` attribute is created declaratively and the `owne`r attribute is created dynamically.</span></span>  
  
 <span data-ttu-id="a93a0-145">[!code-vb[VbXMLSamples #&44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a93a0-145">[!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="a93a0-146">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a93a0-146">This code displays the following text:</span></span>  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="a93a0-147">例</span><span class="sxs-lookup"><span data-stu-id="a93a0-147">Example</span></span>  
 <span data-ttu-id="a93a0-148">次の例では、山かっこでは構文を使用してという名前の XML 属性の値を取得`number-type`で有効な識別子ではない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-148">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="a93a0-149">[!code-vb[VbXMLSamples&#13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a93a0-149">[!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="a93a0-150">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a93a0-150">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="a93a0-151">例</span><span class="sxs-lookup"><span data-stu-id="a93a0-151">Example</span></span>  
 <span data-ttu-id="a93a0-152">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="a93a0-152">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="a93a0-153">使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードへのアクセス"`ns:name`"です。</span><span class="sxs-lookup"><span data-stu-id="a93a0-153">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 <span data-ttu-id="a93a0-154">[!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a93a0-154">[!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span></span>  
  
 <span data-ttu-id="a93a0-155">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a93a0-155">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="a93a0-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="a93a0-156">See Also</span></span>  
 <span data-ttu-id="a93a0-157"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="a93a0-157"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="a93a0-158"> [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a93a0-158"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="a93a0-159"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="a93a0-159"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="a93a0-160"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a93a0-160"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="a93a0-161"> [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a93a0-161"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
