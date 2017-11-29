---
title: "XML 属性軸プロパティ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a286c70f57128d0406b3a300610fea5e1c44b32d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="351fb-102">XML 属性軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="351fb-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="351fb-103">属性の値にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素をまたは<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="351fb-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="351fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="351fb-104">Syntax</span></span>  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="351fb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="351fb-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="351fb-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="351fb-106">Required.</span></span> <span data-ttu-id="351fb-107"><xref:System.Xml.Linq.XElement>オブジェクトのコレクションまたは<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="351fb-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="351fb-108">.@</span><span class="sxs-lookup"><span data-stu-id="351fb-108">.@</span></span>  
 <span data-ttu-id="351fb-109">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="351fb-109">Required.</span></span> <span data-ttu-id="351fb-110">属性軸プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="351fb-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="351fb-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="351fb-111">Optional.</span></span> <span data-ttu-id="351fb-112">属性の名前の先頭を示すとき`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="351fb-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="351fb-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="351fb-113">Required.</span></span> <span data-ttu-id="351fb-114">アクセスする場合、フォームの属性の名前 [`prefix`:]`name`です。</span><span class="sxs-lookup"><span data-stu-id="351fb-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="351fb-115">パーツ</span><span class="sxs-lookup"><span data-stu-id="351fb-115">Part</span></span>|<span data-ttu-id="351fb-116">説明</span><span class="sxs-lookup"><span data-stu-id="351fb-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="351fb-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="351fb-117">Optional.</span></span> <span data-ttu-id="351fb-118">属性の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="351fb-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="351fb-119">`Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="351fb-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="351fb-120">必須です。</span><span class="sxs-lookup"><span data-stu-id="351fb-120">Required.</span></span> <span data-ttu-id="351fb-121">ローカルの属性名です。</span><span class="sxs-lookup"><span data-stu-id="351fb-121">Local attribute name.</span></span> <span data-ttu-id="351fb-122">参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。</span><span class="sxs-lookup"><span data-stu-id="351fb-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="351fb-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="351fb-123">Optional.</span></span> <span data-ttu-id="351fb-124">属性の名前の終了を示すとき`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="351fb-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="351fb-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="351fb-125">Return Value</span></span>  
 <span data-ttu-id="351fb-126">値を含む文字列`attribute`です。</span><span class="sxs-lookup"><span data-stu-id="351fb-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="351fb-127">属性名が存在しない場合`Nothing`が返されます。</span><span class="sxs-lookup"><span data-stu-id="351fb-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="351fb-128">コメント</span><span class="sxs-lookup"><span data-stu-id="351fb-128">Remarks</span></span>  
 <span data-ttu-id="351fb-129">名を使用して、属性の値にアクセスする XML 属性軸プロパティを使用することができます、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素から、または<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="351fb-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="351fb-130">名前、属性値を取得またはスコアで始まる新しい名前を指定することによって要素に新しい属性を追加することができます、@ 識別子。</span><span class="sxs-lookup"><span data-stu-id="351fb-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="351fb-131">XML 属性を使用して、参照するとき、文字列として @ 識別子、属性の値が返され、明示的に指定する必要はありません、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="351fb-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="351fb-132">XML 属性の名前付け規則の名前付け規則が異なる[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]識別子。</span><span class="sxs-lookup"><span data-stu-id="351fb-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] identifiers.</span></span> <span data-ttu-id="351fb-133">有効な Visual Basic 識別子ではない名前を持つ XML 属性にアクセスする名前は山かっこで囲みます (\<および >)。</span><span class="sxs-lookup"><span data-stu-id="351fb-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="351fb-134">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="351fb-134">XML Namespaces</span></span>  
 <span data-ttu-id="351fb-135">属性軸プロパティの名前を使用してグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="351fb-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="351fb-136">XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。</span><span class="sxs-lookup"><span data-stu-id="351fb-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="351fb-137">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。</span><span class="sxs-lookup"><span data-stu-id="351fb-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="351fb-138">例</span><span class="sxs-lookup"><span data-stu-id="351fb-138">Example</span></span>  
 <span data-ttu-id="351fb-139">次の例は、という名前の XML 属性の値を取得する方法を示しています。`type`という XML 要素のコレクションから`phone`です。</span><span class="sxs-lookup"><span data-stu-id="351fb-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 <span data-ttu-id="351fb-140">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="351fb-140">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="351fb-141">例</span><span class="sxs-lookup"><span data-stu-id="351fb-141">Example</span></span>  
 <span data-ttu-id="351fb-142">次の例は、宣言の一部として、XML では、動的のインスタンスに属性を追加することで、両方の XML 要素の属性を作成する方法を示します、<xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="351fb-142">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="351fb-143">`type`属性が宣言によって作成されると、`owner`属性が動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="351fb-143">The `type` attribute is created declaratively and the `owner` attribute is created dynamically.</span></span>  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 <span data-ttu-id="351fb-144">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="351fb-144">This code displays the following text:</span></span>  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="351fb-145">例</span><span class="sxs-lookup"><span data-stu-id="351fb-145">Example</span></span>  
 <span data-ttu-id="351fb-146">次の例では、山かっこ構文を使用してという名前の XML 属性の値を取得`number-type`、有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="351fb-146">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 <span data-ttu-id="351fb-147">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="351fb-147">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="351fb-148">例</span><span class="sxs-lookup"><span data-stu-id="351fb-148">Example</span></span>  
 <span data-ttu-id="351fb-149">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="351fb-149">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="351fb-150">使用して、名前空間のプレフィックスを XML リテラルを作成し、アクセスの修飾名を持つ最初の子ノード"`ns:name`"です。</span><span class="sxs-lookup"><span data-stu-id="351fb-150">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 <span data-ttu-id="351fb-151">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="351fb-151">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="351fb-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="351fb-152">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="351fb-153">XML 軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="351fb-153">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="351fb-154">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="351fb-154">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="351fb-155">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="351fb-155">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="351fb-156">宣言する XML 要素と属性の名前</span><span class="sxs-lookup"><span data-stu-id="351fb-156">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
