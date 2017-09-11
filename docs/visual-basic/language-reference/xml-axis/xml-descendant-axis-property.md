---
title: "XML 子孫軸プロパティ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
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
ms.openlocfilehash: e84a8bb989ebbed57595ebf93cef620027a04328
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="769b4-102">XML 子孫軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="769b4-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="769b4-103">次の子孫へのアクセスを提供:<xref:System.Xml.Linq.XElement>オブジェクト、 <xref:System.Xml.Linq.XDocument>、オブジェクトのコレクション<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="769b4-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="769b4-104">構文</span><span class="sxs-lookup"><span data-stu-id="769b4-104">Syntax</span></span>  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="769b4-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="769b4-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="769b4-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="769b4-106">Required.</span></span> <span data-ttu-id="769b4-107"><xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、一連の<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="769b4-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="769b4-108">...<</span><span class="sxs-lookup"><span data-stu-id="769b4-108">...<</span></span>  
 <span data-ttu-id="769b4-109">必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="769b4-109">Required.</span></span> <span data-ttu-id="769b4-110">子孫軸プロパティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="769b4-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="769b4-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="769b4-111">Required.</span></span> <span data-ttu-id="769b4-112">アクセスして、フォームの子孫ノードの名前 [`prefix``:`]`name`します。</span><span class="sxs-lookup"><span data-stu-id="769b4-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="769b4-113">パーツ</span><span class="sxs-lookup"><span data-stu-id="769b4-113">Part</span></span>|<span data-ttu-id="769b4-114">説明</span><span class="sxs-lookup"><span data-stu-id="769b4-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="769b4-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="769b4-115">Optional.</span></span> <span data-ttu-id="769b4-116">子孫ノードの XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="769b4-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="769b4-117">グローバル XML 名前空間を使用して定義されている必要があります、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="769b4-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="769b4-118">必須です。</span><span class="sxs-lookup"><span data-stu-id="769b4-118">Required.</span></span> <span data-ttu-id="769b4-119">子孫ノードのローカル名。</span><span class="sxs-lookup"><span data-stu-id="769b4-119">Local name of the descendant node.</span></span> <span data-ttu-id="769b4-120">参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="769b4-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="769b4-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="769b4-121">Required.</span></span> <span data-ttu-id="769b4-122">子孫軸プロパティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="769b4-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="769b4-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="769b4-123">Return Value</span></span>  
 <span data-ttu-id="769b4-124">コレクション<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="769b4-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="769b4-125">コメント</span><span class="sxs-lookup"><span data-stu-id="769b4-125">Remarks</span></span>  
 <span data-ttu-id="769b4-126">XML 子孫軸プロパティを使用するには名を使用して子孫ノードにアクセスする、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクトのコレクションから、または<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="769b4-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="769b4-127">XML を使用して`Value`返されるコレクション内の最初の子孫ノードの値にアクセスするプロパティです。</span><span class="sxs-lookup"><span data-stu-id="769b4-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="769b4-128">詳細については、次を参照してください。 [XML Value プロパティ](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。</span><span class="sxs-lookup"><span data-stu-id="769b4-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="769b4-129">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、子孫軸プロパティを変換への呼び出しに、<xref:System.Xml.Linq.XContainer.Descendants%2A>メソッド</xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="769b4-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="769b4-130">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="769b4-130">XML Namespaces</span></span>  
 <span data-ttu-id="769b4-131">子孫軸プロパティの名前でグローバルに宣言された XML 名前空間だけを使用できます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="769b4-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="769b4-132">XML 要素リテラル内にローカルに宣言されている XML 名前空間は使用できません。</span><span class="sxs-lookup"><span data-stu-id="769b4-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="769b4-133">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="769b4-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="769b4-134">例</span><span class="sxs-lookup"><span data-stu-id="769b4-134">Example</span></span>  
 <span data-ttu-id="769b4-135">次の例は、という名前の最初の子孫ノードの値にアクセスする方法を示しています。`name`という名前のすべての子孫ノードの値と`phone`から、`contacts`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="769b4-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 <span data-ttu-id="769b4-136">[!code-vb[VbXMLSamples&#25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="769b4-136">[!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="769b4-137">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="769b4-137">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="769b4-138">例</span><span class="sxs-lookup"><span data-stu-id="769b4-138">Example</span></span>  
 <span data-ttu-id="769b4-139">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="769b4-139">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="769b4-140">使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードの値にアクセス`ns:name`します。</span><span class="sxs-lookup"><span data-stu-id="769b4-140">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="769b4-141">[!code-vb[VbXMLSamples #&26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="769b4-141">[!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="769b4-142">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="769b4-142">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="769b4-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="769b4-143">See Also</span></span>  
 <span data-ttu-id="769b4-144"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="769b4-144"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="769b4-145"> [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="769b4-145"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="769b4-146"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="769b4-146"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="769b4-147"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="769b4-147"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="769b4-148"> [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="769b4-148"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
