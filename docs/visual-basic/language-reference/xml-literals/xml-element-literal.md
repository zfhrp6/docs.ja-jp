---
title: XML 要素リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 55d5d1410a65ea8c800bbd2b310907a6d6a61c61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605135"
---
# <a name="xml-element-literal-visual-basic"></a>XML 要素リテラル (Visual Basic)

表すリテラル、<xref:System.Xml.Linq.XElement>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>指定項目  
  
-   `<`  
  
     必須。 要素の開始タグを開きます。  
  
-   `name`  
  
     必須。 要素名 形式では、次のいずれかです。  
  
    -   形式の要素名のリテラル テキスト`[ePrefix:]eName`、場所。  
  
        |パーツ|説明|  
        |---|---|  
        |`ePrefix`|任意。 要素の XML 名前空間プレフィックス。 グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、ファイルまたはプロジェクト レベル、またはこの要素または親要素で定義されているローカル XML 名前空間。|  
        |`eName`|必須。 要素名 形式では、次のいずれかです。<br /><br /> -リテラル テキスト。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。<br />形式の式を埋め込み`<%= eNameExp %>`です。 型`eNameExp`する必要があります`String`または型に暗黙的に変換できる<xref:System.Xml.Linq.XName>です。|  
  
    -   形式の式を埋め込む`<%= nameExp %>`です。 型`nameExp`する必要があります`String`または型に暗黙的に変換<xref:System.Xml.Linq.XName>です。 埋め込み式は、要素の終了タグでは許可されません。  
  
-   `attributeList`  
  
     任意。 属性の一覧は、リテラルで宣言します。  
  
     `attribute [ attribute ... ]`  
  
     各`attribute`が次の構文のいずれか。  
  
    -   属性の割り当て、フォームの`[aPrefix:]aName=aValue`、場所。  
  
        |パーツ|説明|  
        |---|---|  
        |`aPrefix`|任意。 属性の XML 名前空間プレフィックス。 グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、またはこの要素または親要素で定義されているローカルの XML 名前空間。|  
        |`aName`|必須。 属性の名前。 形式では、次のいずれかです。<br /><br /> -リテラル テキスト。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。<br />形式の式を埋め込み`<%= aNameExp %>`です。 型`aNameExp`する必要があります`String`または型に暗黙的に変換できる<xref:System.Xml.Linq.XName>です。|  
        |`aValue`|任意。 属性の値です。 形式では、次のいずれかです。<br /><br /> 、引用符で囲まれたリテラル テキスト。<br />形式の式を埋め込み`<%= aValueExp %>`です。 任意の型は許可されています。|  
  
    -   形式の式を埋め込む`<%= aExp %>`です。  
  
-   `/>`  
  
     任意。 要素が空の要素、コンテンツがない状態であることを示します。  
  
-   `>`  
  
     必須。 開始タグまたは空要素タグを終了します。  
  
-   `elementContents`  
  
     任意。 要素のコンテンツ。  
  
     `content [ content ... ]`  
  
     各`content`次のいずれかになります。  
  
    -   リテラル テキスト。 内のすべての空白`elementContents`リテラル テキストがある場合に重要になります。  
  
    -   形式の式を埋め込む`<%= contentExp %>`です。  
  
    -   XML 要素リテラルです。  
  
    -   XML コメント リテラルです。 参照してください[XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)です。  
  
    -   XML 処理命令リテラルです。 参照してください[XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)です。  
  
    -   XML CDATA リテラルです。 参照してください[XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)です。  
  
-   `</[name]>`  
  
     任意。 要素の終了タグを表します。 省略可能な`name`埋め込み式の結果である場合、パラメーターは許可されません。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XElement> オブジェクト。  
  
## <a name="remarks"></a>コメント  
 作成する XML 要素リテラルの構文を使用することができます<xref:System.Xml.Linq.XElement>コード内のオブジェクト。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数行にまたがることができます。 この機能を使用すると、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。  
  
 形式の式を埋め込む`<%= exp %>`を使用すると、XML 要素リテラルに動的な情報を追加します。 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。  
  
 Visual Basic コンパイラへの呼び出しにリテラルの XML 要素に変換して、<xref:System.Xml.Linq.XElement.%23ctor%2A>コンス トラクターと、必要な場合、<xref:System.Xml.Linq.XAttribute.%23ctor%2A>コンス トラクターです。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 XML 名前空間プレフィックスは、コードに何度も同じ名前空間からの要素の XML リテラルを作成する必要がある場合に便利です。 使用して定義するグローバルの XML 名前空間プレフィックスを使用することができます、`Imports`ステートメント、またはローカルのプレフィックスを使用して定義する、`xmlns:xmlPrefix="xmlNamespace"`属性構文です。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。  
  
 XML 名前空間のスコープの規則に従ってローカル プレフィックスはグローバル プレフィックスに優先します。 ただし、XML リテラルには、XML 名前空間が定義されている場合はその名前空間は、組み込み式に表示される式を使用できません。 埋め込み式は、グローバルの XML 名前空間のみにアクセスできます。  
  
 Visual Basic コンパイラでは、各グローバル生成されたコード内のローカルの名前空間の定義を 1 つに、XML リテラルで使用される XML 名前空間に変換します。 使用されていないグローバルの XML 名前空間は、生成されたコードには表示されません。  
  
## <a name="example"></a>例  
 次の例では、次の 2 つの入れ子になった空要素を持つ単純な XML 要素を作成する方法を示します。  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 この例では、次のテキストを表示します。 リテラルが空の要素の構造を維持することに注意してください。  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>例  
 次の例では、組み込み式を使用して要素の名前を指定し、属性を作成する方法を示します。  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 XML リテラルを作成する名前空間のプレフィックスを使用し、要素の最終的なフォームを表示します。  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラが XML 名前空間のプレフィックス定義にグローバル XML 名前空間のプレフィックスを変換することに注意してください。 \<Ns:middle > 要素の XML 名前空間プレフィックスを再定義、 \<ns:inner1 > 要素。 ただし、 \<ns:inner2 > 要素で定義された名前空間を使用して、`Imports`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
