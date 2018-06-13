---
title: Imports ステートメント (XML 名前空間)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: ba7475416d8a4e2eb3c892d457c03eeb695045eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604563"
---
# <a name="imports-statement-xml-namespace"></a>Imports ステートメント (XML 名前空間)
XML リテラルおよび XML 軸のプロパティで使用するための XML 名前空間プレフィックスをインポートします。  
  
## <a name="syntax"></a>構文  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>指定項目  
 `xmlNamespacePrefix`  
 任意。 XML 要素と属性を参照できます文字列`xmlNamespaceName`です。 いない場合`xmlNamespacePrefix`は既定の XML 名前空間がインポートされた XML 名前空間を指定します。 有効な XML 識別子である必要があります。 詳細については、次を参照してください。[宣言されている XML 要素の名前および属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。  
  
 `xmlNamespaceName`  
 必須。 インポートされる XML 名前空間を識別する文字列。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Imports`を XML リテラルおよび XML 軸のプロパティ、またはに渡されるパラメーターとして使用できるグローバルの XML 名前空間を定義するステートメント、`GetXmlNamespace`演算子。 (使用方法について、`Imports`型の名前を使用する、コードで使用できるエイリアスをインポートするステートメントを参照してください[Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md))。使用して XML 名前空間を宣言するための構文、`Imports`ステートメントは、XML で使用される構文と同じです。 したがって、XML ファイルから名前空間宣言をコピーしで使用する、`Imports`ステートメントです。  
  
 XML 名前空間プレフィックスは、同じ名前空間からの XML 要素を繰り返し作成するときに役立ちます。 XML 名前空間プレフィックスが宣言された、`Imports`ステートメントがファイル内のすべてのコードで使用可能であるという意味でグローバルです。 XML 要素リテラルおよび XML 軸のプロパティにアクセスするときに作成するときに使用することができます。 詳細については、次を参照してください。 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)と[XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)です。  
  
 名前空間プレフィックスなしのグローバル XML 名前空間を定義するかどうか (たとえば、 `Imports <xmlns="http://SomeNameSpace>"`)、その名前空間には、既定の XML 名前空間と見なされます。 任意の XML 要素リテラルまたは名前空間が明示的に指定されていない XML 属性軸プロパティの既定の XML 名前空間を使用します。 指定した名前空間は空の名前空間の場合、既定の名前空間が使用されます (つまり、 `xmlns=""`)。 既定の XML 名前空間は、XML リテラル内の XML 属性または名前空間がない XML 属性軸プロパティには適用されません。  
  
 XML 名前空間、XML リテラルで定義されていると呼ばれる*XML 名前空間をローカル*、によって定義されている XML 名前空間よりも優先、`Imports`グローバルとしてステートメントです。 によって定義されている XML 名前空間、`Imports`ステートメント、Visual Basic プロジェクトのインポートされた XML 名前空間よりも優先されます。 XML リテラルには、XML 名前空間が定義されている場合、そのローカル名前空間は、埋め込み式には適用されません。  
  
 グローバル名前空間は XML では、.NET Framework 名前空間と同じスコープと定義規則に従います。 その結果、含めることができますが、`Imports`をグローバル XML 名前空間を定義するステートメント、.NET Framework 名前空間をインポートする任意の場所。 これには、コード ファイルおよびプロジェクト レベル インポートされた名前空間の両方が含まれます。 プロジェクト レベル インポートされた名前空間については、次を参照してください。[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)です。  
  
 各ソース ファイルは、任意の数を含めることができます`Imports`ステートメントです。 これらに従う必要ありますオプション宣言など、`Option Strict`ステートメント、およびそれらの前に指定プログラミング要素を宣言など`Module`または`Class`ステートメントです。  
  
## <a name="example"></a>例  
 次の例は、既定の XML 名前空間とプレフィックスで識別される XML 名前空間をインポート`ns`です。 両方の名前空間を使用する XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>例  
 次の例では、XML 名前空間プレフィックス`ns`です。 名前空間プレフィックスを使用し、要素の最終的なフォームを表示する XML リテラルが作成されます。  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラが、ローカル プレフィックス定義へのグローバル プレフィックスから XML 名前空間プレフィックスを変換されたことに注意してください。  
  
## <a name="example"></a>例  
 次の例では、XML 名前空間プレフィックス`ns`です。 その後、この名前空間のプレフィックスを使用して XML リテラルを作成し、修飾名 `ns:name` を持つ最初の子ノードにアクセスします。  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>関連項目  
 [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace 演算子](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
