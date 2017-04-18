---
title: "XML 要素リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
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
ms.openlocfilehash: c77a1ec3621d056a814b298cd5ee6b8c44c52ec2
ms.lasthandoff: 03/13/2017

---
# <a name="xml-element-literal-visual-basic"></a>XML 要素リテラル (Visual Basic)
表すリテラル、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
## <a name="syntax"></a>構文  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>指定項目  
  
-   `<`  
  
     必須です。 要素の開始タグを開きます。  
  
-   `name`  
  
     必須です。 要素名 形式は、次のいずれかを示します。  
  
    -   リテラル テキストの形式の要素名を [`ePrefix``:`]`eName`、場所。  
  
        |パーツ|説明|  
        |---|---|  
        |`ePrefix`|省略可能です。 要素の XML 名前空間プレフィックス。 グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、ファイルまたはプロジェクト レベルまたはこの要素または親要素で定義されているローカル XML 名前空間。|  
        |`eName`|必須です。 要素名 形式は、次のいずれかを示します。<br /><br /> リテラル テキスト。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。<br />形式の式を埋め込み`<%=`e`NameExp` `%>`します。 型`eNameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換できる型|  
  
    -   形式の式を埋め込む`<%=` `nameExp` `%>`します。 型`nameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換の種類 要素の終了タグで、組み込み式を設定することはできません。  
  
-   `attributeList`  
  
     省略可能です。 属性の一覧は、リテラルで宣言します。  
  
     `attribute [ attribute ... ]`  
  
     各`attribute`が次の構文のいずれか。  
  
    -   属性を割り当てる、フォームの [`aPrefix``:`]`aName``=``aValue`、場所。  
  
        |パーツ|説明|  
        |---|---|  
        |`aPrefix`|省略可能です。 属性の XML 名前空間プレフィックス。 グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、またはこの要素または親要素で定義されているローカル XML 名前空間。|  
        |`aName`|必須です。 属性の名前。 形式は、次のいずれかを示します。<br /><br /> リテラル テキスト。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。<br />形式の式を埋め込み`<%=` `aNameExp` `%>`します。 型`aNameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換できる型|  
        |`aValue`|省略可能です。 属性の値です。 形式は、次のいずれかを示します。<br /><br /> の引用符で囲むリテラル テキスト。<br />形式の式を埋め込み`<%=` `aValueExp` `%>`します。 任意の型を許可します。|  
  
    -   形式の式を埋め込む`<%=` `aExp` `%>`します。  
  
-   `/>`  
  
     省略可能です。 要素がコンテンツのない、空の要素であることを示します。  
  
-   `>`  
  
     必須です。 以降、または空要素タグを終了します。  
  
-   `elementContents`  
  
     省略可能です。 要素の内容。  
  
     `content [ content ... ]`  
  
     各`content`次のいずれかになります。  
  
    -   リテラル テキスト。 内のすべての空白`elementContents`リテラル テキストがある場合に有効になります。  
  
    -   形式の式を埋め込む`<%=` `contentExp` `%>`します。  
  
    -   XML 要素リテラルです。  
  
    -   XML コメント リテラルです。 参照してください[XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)します。  
  
    -   XML 処理命令リテラルです。 参照してください[XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)します。  
  
    -   XML CDATA リテラルです。 参照してください[XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)します。  
  
-   `</`[`name`]`>`  
  
     省略可能です。 要素の終了タグを表します。 省略可能な`name`の埋め込み式の結果になる場合、パラメーターは許可されません。  
  
## <a name="return-value"></a>戻り値  
 <xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
## <a name="remarks"></a>コメント  
 作成する XML 要素リテラルの構文を使用する<xref:System.Xml.Linq.XElement>、コード内のオブジェクト</xref:System.Xml.Linq.XElement>。  
  
> [!NOTE]
>  XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。 この機能を使用すると、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。  
  
 形式の式を埋め込む`<%=` `exp` `%>`を使用すると、XML 要素リテラルに動的な情報を追加します。 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラへの呼び出しにリテラルの XML 要素に変換して、<xref:System.Xml.Linq.XElement.%23ctor%2A>コンス トラクターと、必要な場合、<xref:System.Xml.Linq.XAttribute.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A> 。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 XML 名前空間プレフィックスは、コードに何度も同じ名前空間の要素を含む XML リテラルを作成する必要がある場合に役立ちます。 使用して定義するグローバルの XML 名前空間プレフィックスを使用する、`Imports`ステートメント、またはローカルのプレフィックスは、使用して定義する、 `xmlns:``xmlPrefix`="`xmlNamespace`"属性構文です。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。  
  
 XML 名前空間のスコープの規則に従ってローカル プレフィックスはグローバル プレフィックスに優先します。 ただし、XML リテラルには、XML 名前空間が定義されている場合はその名前空間は、組み込み式に出現する式を使用できません。 埋め込み式は、グローバルの XML 名前空間のみにアクセスできます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが各グローバル生成されたコード内のローカルの名前空間の定義を&1; つに、XML リテラルで使用される XML 名前空間に変換します。 使用されていないグローバルの XML 名前空間は、生成されたコードには表示されません。  
  
## <a name="example"></a>例  
 次の例では、2 つの入れ子になった空要素を持つ単純な XML 要素を作成する方法を示します。  
  
 [!code-vb[VbXMLSamples&#20;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 この例では、次のテキストを表示します。 リテラルは、空の要素の構造を維持することを確認します。  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>例  
 次の例では、組み込み式を使用して、要素の名前を指定し、属性を作成する方法を示します。  
  
 [!code-vb[VbXMLSamples #&21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 XML リテラルを作成する名前空間のプレフィックスを使用し、要素の最終的なフォームを表示します。  
  
 [!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 コンパイラが XML 名前空間のプレフィックス定義にグローバルの XML 名前空間のプレフィックスを変換することに注意してください。 \<Ns:middle > 要素の XML 名前空間プレフィックスを再定義、 \<ns:inner1 > 要素。 ただし、 \<ns:inner2 > 要素によって定義された名前空間を使用して、`Imports`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>   
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)   
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
