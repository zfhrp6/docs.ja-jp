---
title: "Imports Statement (XML Namespace) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ImportsXmlns"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML namespace [Visual Basic], importing"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "namespaces [Visual Basic], importing"
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Imports Statement (XML Namespace)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

XML リテラルと XML 軸プロパティで使用する XML 名前空間プレフィックスをインポートします。  
  
## 構文  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## 指定項目  
 `xmlNamespacePrefix`  
 省略可能です。  XML 要素と XML 属性が `xmlNamespaceName` を参照するために使用する文字列です。  `xmlNamespacePrefix` の指定がない場合は、既定の XML 名前空間がインポートされます。  有効な XML 識別子を指定する必要があります。  詳細については、「[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)」を参照してください。  
  
 `xmlNamespaceName`  
 必ず指定します。  インポートされる XML 名前空間を識別する文字列です。  
  
## 解説  
 `Imports` ステートメントを使用すると、グローバル XML 名前空間を定義して、XML リテラルや XML 軸プロパティで使用したり、`GetXmlNamespace` 演算子に渡すパラメーターとして使用したりできます。  `Imports` ステートメントによって、コード内で型名が使用される場所で使用できるエイリアスをインポートする方法の詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。`Imports` ステートメントを使用して XML 名前空間を宣言するための構文は、XML で使用される構文と同じです。  したがって、XML ファイルから名前空間宣言をコピーし、それを `Imports` ステートメントで使用できます。  
  
 XML 名前空間プレフィックスは、同一の名前空間から XML 要素を繰り返し作成する場合に役立ちます。  `Imports` を使用して宣言される XML 名前空間プレフィックスは、ファイル内のすべてのコードで使用できるという意味でグローバルです。  XML 名前空間は、XML 要素のリテラルの作成時および XML 軸プロパティへのアクセス時に使用できます。  詳細については、「[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」および「[XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)」を参照してください。  
  
 名前空間プレフィックスのないグローバル XML 名前空間 \(たとえば `Imports <xmlns="http://SomeNameSpace">`\) を定義した場合、その名前空間は既定の XML 名前空間と見なされます。  既定の XML 名前空間は、名前空間を明示的に指定しないすべての XML 要素のリテラルまたは XML 属性の軸プロパティに対して使用されます。  また、指定された名前空間が空の名前空間である場合 \(つまり `xmlns=""` の場合\) にも、既定の名前空間が使用されます。  既定の XML 名前空間は、XML リテラル内の XML 属性や、名前空間を持たない XML 属性の軸プロパティには適用されません。  
  
 XML リテラル内に定義された XML 名前空間は、*ローカル XML 名前空間*と呼ばれ、`Imports` ステートメントによってグローバルに定義された XML 名前空間より優先されます。  `Imports` ステートメントで定義された XML 名前空間は、Visual Basic プロジェクトにインポートされた XML 名前空間より優先されます。  XML リテラルで XML 名前空間を定義する場合、そのローカル名前空間は、埋め込まれた式には適用されません。  
  
 グローバル XML 名前空間は、.NET Framework 名前空間と同じスコープと定義規則に従います。  したがって、.NET Framework 名前空間をインポートできる場所であればどこでも、`Imports` ステートメントを使用してグローバル XML 名前空間を定義できます。  これには、コード ファイルと、プロジェクト レベルでインポートされる名前空間が含まれます。  プロジェクト レベルでインポートされる名前空間の詳細については、「[\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)」を参照してください。  
  
 1 つのファイルで使用できる `Imports` ステートメントの数に制限はありません。  これらのステートメントは、`Option Strict` ステートメントなどのオプションの宣言よりも後で、`Module` ステートメントや `Class` ステートメントなどのプログラミング要素の宣言よりも前に記述する必要があります。  
  
## 使用例  
 次の例では、既定の XML 名前空間と、プレフィックス `ns` で識別される XML 名前空間をインポートします。  その後、両方の名前空間を使用する XML リテラルを作成します。  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_1.vb)]  
  
 このコードは、次のテキストを表示します。  
  
```  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## 使用例  
 次の例では、XML 名前空間プレフィックス `ns` をインポートします。  次に、この名前空間プレフィックスを使用する XML リテラルを作成し、要素の最終的な形式を表示します。  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_2.vb)]  
  
 このコードは、次のテキストを表示します。  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラにより、XML 名前空間プレフィックスがグローバル プレフィックスからローカル プレフィックス定義に変換されたことに注意してください。  
  
## 使用例  
 次の例では、XML 名前空間プレフィックス `ns` をインポートします。  その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/imports-statement-xml-na_3.vb)]  
  
 このコードは、次のテキストを表示します。  
  
 `Patrick Hines`  
  
## 参照  
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [GetXmlNamespace Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)