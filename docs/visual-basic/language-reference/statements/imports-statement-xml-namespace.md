---
title: "Imports ステートメント (XML Namespace) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImportsXmlns
dev_langs:
- VB
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 66ac2bd947328dab9df812709525b43fb27145ac
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017

---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="fef07-102">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="fef07-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="fef07-103">XML リテラルと XML 軸プロパティで使用するための XML 名前空間プレフィックスをインポートします。</span><span class="sxs-lookup"><span data-stu-id="fef07-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef07-104">構文</span><span class="sxs-lookup"><span data-stu-id="fef07-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="fef07-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fef07-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="fef07-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="fef07-106">Optional.</span></span> <span data-ttu-id="fef07-107">XML 要素と属性を参照できます文字列`xmlNamespaceName`します。</span><span class="sxs-lookup"><span data-stu-id="fef07-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="fef07-108">いない場合`xmlNamespacePrefix`は既定の XML 名前空間がインポート済みの XML 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="fef07-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="fef07-109">有効な XML 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fef07-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="fef07-110">詳細については、次を参照してください。[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="fef07-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="fef07-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="fef07-111">Required.</span></span> <span data-ttu-id="fef07-112">インポートされる XML 名前空間を識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="fef07-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fef07-113">コメント</span><span class="sxs-lookup"><span data-stu-id="fef07-113">Remarks</span></span>  
 <span data-ttu-id="fef07-114">使用することができます、`Imports`ステートメントに渡されるパラメーターの XML リテラルと XML 軸プロパティを使用できるグローバルの XML 名前空間を定義する、`GetXmlNamespace`演算子。</span><span class="sxs-lookup"><span data-stu-id="fef07-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="fef07-115">(使用方法について、`Imports`型の名前を使用するコードでは、使用できるエイリアスをインポートするステートメントを参照してください[Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md))。使用して XML 名前空間を宣言する構文、`Imports`ステートメントは XML で使用される構文と同じです。</span><span class="sxs-lookup"><span data-stu-id="fef07-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="fef07-116">そのため、XML ファイルから名前空間宣言をコピーしで使用する`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fef07-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="fef07-117">XML 名前空間プレフィックスは、同じ名前空間にある XML 要素を繰り返し作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fef07-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="fef07-118">XML 名前空間プレフィックスが宣言された、`Imports`ステートメントがファイル内のすべてのコードで使用可能であるという意味でグローバルです。</span><span class="sxs-lookup"><span data-stu-id="fef07-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="fef07-119">XML 要素リテラルと XML 軸プロパティにアクセスするときに作成するときに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fef07-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="fef07-120">詳細については、次を参照してください。 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)します。</span><span class="sxs-lookup"><span data-stu-id="fef07-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="fef07-121">名前空間プレフィックスなしのグローバルな XML 名前空間を定義するかどうか (たとえば、 `Imports <xmlns="http://SomeNameSpace>"`)、その名前空間が既定の XML 名前空間と見なされます。</span><span class="sxs-lookup"><span data-stu-id="fef07-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="fef07-122">任意の XML 要素リテラルまたは XML 属性軸プロパティ名前空間を明示的に指定されていない既定の XML 名前空間が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="fef07-123">指定した名前空間が空の名前空間場合、既定の名前空間が使用されます (つまり、 `xmlns=""`)。</span><span class="sxs-lookup"><span data-stu-id="fef07-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="fef07-124">既定の XML 名前空間は、XML リテラル内の XML 属性または名前空間がない XML 属性軸プロパティには適用されません。</span><span class="sxs-lookup"><span data-stu-id="fef07-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="fef07-125">XML 名前空間は XML リテラルで定義されていると呼ばれる*ローカルの XML 名前空間*、XML 名前空間で定義されているよりも優先、`Imports`グローバルとしてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fef07-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="fef07-126">XML 名前空間で定義されている、`Imports`ステートメント、Visual Basic プロジェクトにインポートされた XML 名前空間よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="fef07-127">XML リテラルには、XML 名前空間が定義されている場合、そのローカル名前空間は、組み込み式には適用されません。</span><span class="sxs-lookup"><span data-stu-id="fef07-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="fef07-128">グローバル名前空間は XML では、.NET Framework 名前空間と同じスコープと定義規則に従います。</span><span class="sxs-lookup"><span data-stu-id="fef07-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="fef07-129">その結果を含めることができます、`Imports`グローバル XML 名前空間を定義するステートメント、.NET Framework 名前空間をインポートする任意の場所。</span><span class="sxs-lookup"><span data-stu-id="fef07-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="fef07-130">これには、コード ファイルおよびプロジェクト レベル インポートされた名前空間の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fef07-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="fef07-131">プロジェクト レベル インポートされた名前空間については、次を参照してください。[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="fef07-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="fef07-132">各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fef07-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="fef07-133">これらのオプションを宣言をなどください、`Option Strict`ステートメント、およびそれらの前に指定プログラミング要素を宣言など`Module`または`Class`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="fef07-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fef07-134">例</span><span class="sxs-lookup"><span data-stu-id="fef07-134">Example</span></span>  
 <span data-ttu-id="fef07-135">次の例は、既定の XML 名前空間とプレフィックスで識別される XML 名前空間をインポート`ns`します。</span><span class="sxs-lookup"><span data-stu-id="fef07-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="fef07-136">両方の名前空間を使用する XML リテラルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-136">It then creates XML literals that use both namespaces.</span></span>  
  
 <span data-ttu-id="fef07-137">[!code-vb[VbXMLSamples #&45;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fef07-137">[!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]</span></span>  
  
 <span data-ttu-id="fef07-138">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-138">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="fef07-139">例</span><span class="sxs-lookup"><span data-stu-id="fef07-139">Example</span></span>  
 <span data-ttu-id="fef07-140">次の例は、XML 名前空間プレフィックスをインポート`ns`します。</span><span class="sxs-lookup"><span data-stu-id="fef07-140">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="fef07-141">名前空間プレフィックスを使用し、要素の最終的な形式を表示する XML リテラルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-141">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 <span data-ttu-id="fef07-142">[!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fef07-142">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]</span></span>  
  
 <span data-ttu-id="fef07-143">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-143">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="fef07-144">コンパイラが、ローカル プレフィックス定義へのグローバル プレフィックスから XML 名前空間プレフィックスを変換されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fef07-144">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fef07-145">例</span><span class="sxs-lookup"><span data-stu-id="fef07-145">Example</span></span>  
 <span data-ttu-id="fef07-146">次の例は、XML 名前空間プレフィックスをインポート`ns`します。</span><span class="sxs-lookup"><span data-stu-id="fef07-146">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="fef07-147">その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="fef07-147">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="fef07-148">[!code-vb[VbXMLSamples&#19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="fef07-148">[!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]</span></span>  
  
 <span data-ttu-id="fef07-149">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fef07-149">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="fef07-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="fef07-150">See Also</span></span>  
 <span data-ttu-id="fef07-151">[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="fef07-151">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="fef07-152"> [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="fef07-152"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="fef07-153"> [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="fef07-153"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="fef07-154"> [GetXmlNamespace 演算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fef07-154"> [GetXmlNamespace Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</span></span>
