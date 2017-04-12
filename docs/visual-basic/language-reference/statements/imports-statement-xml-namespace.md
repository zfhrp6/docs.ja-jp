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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 546168994973d19336f86f4b4e9ec566f0b9dd91
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-xml-namespace"></a>Imports ステートメント (XML 名前空間)
XML リテラルと XML 軸プロパティで使用するための XML 名前空間プレフィックスをインポートします。  
  
## <a name="syntax"></a>構文  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 省略可能です。 XML 要素と属性を参照できます文字列`xmlNamespaceName`します。 いない場合`xmlNamespacePrefix`は既定の XML 名前空間がインポート済みの XML 名前空間を指定します。 有効な XML 識別子である必要があります。 詳細については、次を参照してください。[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。  
  
 `xmlNamespaceName`  
 必須です。 インポートされる XML 名前空間を識別する文字列。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Imports`ステートメントに渡されるパラメーターの XML リテラルと XML 軸プロパティを使用できるグローバルの XML 名前空間を定義する、`GetXmlNamespace`演算子。 (使用方法について、`Imports`型の名前を使用するコードでは、使用できるエイリアスをインポートするステートメントを参照してください[Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md))。使用して XML 名前空間を宣言する構文、`Imports`ステートメントは XML で使用される構文と同じです。 そのため、XML ファイルから名前空間宣言をコピーしで使用する`Imports`ステートメントです。  
  
 XML 名前空間プレフィックスは、同じ名前空間にある XML 要素を繰り返し作成する場合に役立ちます。 XML 名前空間プレフィックスが宣言された、`Imports`ステートメントがファイル内のすべてのコードで使用可能であるという意味でグローバルです。 XML 要素リテラルと XML 軸プロパティにアクセスするときに作成するときに使用することができます。 詳細については、次を参照してください。 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)します。  
  
 名前空間プレフィックスなしのグローバルな XML 名前空間を定義するかどうか (たとえば、 `Imports <xmlns="http://SomeNameSpace>"`)、その名前空間が既定の XML 名前空間と見なされます。 任意の XML 要素リテラルまたは XML 属性軸プロパティ名前空間を明示的に指定されていない既定の XML 名前空間が使用されます。 指定した名前空間が空の名前空間場合、既定の名前空間が使用されます (つまり、 `xmlns=""`)。 既定の XML 名前空間は、XML リテラル内の XML 属性または名前空間がない XML 属性軸プロパティには適用されません。  
  
 XML 名前空間は XML リテラルで定義されていると呼ばれる*ローカルの XML 名前空間*、XML 名前空間で定義されているよりも優先、`Imports`グローバルとしてステートメントです。 XML 名前空間で定義されている、`Imports`ステートメント、Visual Basic プロジェクトにインポートされた XML 名前空間よりも優先されます。 XML リテラルには、XML 名前空間が定義されている場合、そのローカル名前空間は、組み込み式には適用されません。  
  
 グローバル名前空間は XML では、.NET Framework 名前空間と同じスコープと定義規則に従います。 その結果を含めることができます、`Imports`グローバル XML 名前空間を定義するステートメント、.NET Framework 名前空間をインポートする任意の場所。 これには、コード ファイルおよびプロジェクト レベル インポートされた名前空間の両方が含まれます。 プロジェクト レベル インポートされた名前空間については、次を参照してください。[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。 これらのオプションを宣言をなどください、`Option Strict`ステートメント、およびそれらの前に指定プログラミング要素を宣言など`Module`または`Class`ステートメントです。  
  
## <a name="example"></a>例  
 次の例は、既定の XML 名前空間とプレフィックスで識別される XML 名前空間をインポート`ns`します。 両方の名前空間を使用する XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples #&45;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>例  
 次の例は、XML 名前空間プレフィックスをインポート`ns`します。 名前空間プレフィックスを使用し、要素の最終的な形式を表示する XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラが、ローカル プレフィックス定義へのグローバル プレフィックスから XML 名前空間プレフィックスを変換されたことに注意してください。  
  
## <a name="example"></a>例  
 次の例は、XML 名前空間プレフィックスをインポート`ns`します。 その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples&#19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [GetXmlNamespace 演算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
