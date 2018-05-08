---
title: XML での埋め込み式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: f99735df2512fd4b1477bab9126e18f5afbbfa8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML での埋め込み式 (Visual Basic)
埋め込み式を使用すると、実行時に評価される式が含まれる XML リテラルを作成できます。 埋め込み式の構文は、 `<%=` `expression` `%>`で使用される構文と同じであるが[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]です。  
  
 たとえば、作成 XML 要素リテラル、リテラル テキストの内容を含む埋め込み式を組み合わせることです。  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 場合`isbnNumber`12345 整数が含まれると`modifiedDate`日付を含む 3/5/2006、ときにこのコードの実行の値`book`は。  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>埋め込み式の位置と検証  
 埋め込み式は、XML リテラル式内で特定の場所にしか表示されないことができます。 式の型を式の場所のコントロールを返すことができます、どのように`Nothing`処理されます。 次の表は、許可されている場所と埋め込み式の型について説明します。  
  
|リテラル内の場所|式の型|処理 `Nothing`|  
|---|---|---|  
|XML 要素名|<xref:System.Xml.Linq.XName>|Error|  
|XML 要素のコンテンツ|`Object` またはの配列 `Object`|無視|  
|XML 要素の属性名|<xref:System.Xml.Linq.XName>|エラー、属性値もしない限り、 `Nothing`|  
|XML 要素の属性値|`Object`|属性宣言は無視されます。|  
|XML 要素の属性|<xref:System.Xml.Linq.XAttribute> またはのコレクション <xref:System.Xml.Linq.XAttribute>|無視|  
|XML ドキュメントのルート要素|<xref:System.Xml.Linq.XElement> 1 つのコレクションまたは<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト|無視|  
  
-   XML 要素の名前の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   XML 要素のコンテンツの埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   XML 要素属性の名前の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   XML 要素の属性値内の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   XML 要素の属性の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   XML ドキュメントのルート要素の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 有効にした場合`Option Strict`コンパイラは各埋め込み式の型が必要な型に拡大変換ことを確認します。 唯一の例外では、コードの実行時に検証される XML ドキュメントのルート要素です。 せずにコンパイルする場合`Option Strict`、型の式を埋め込むことができます`Object`およびそれらの種類の実行時に確認します。  
  
 コンテンツが、省略可能な場所で埋め込み式を含む`Nothing`は無視されます。 つまり、その要素のコンテンツの属性値を確認する必要はありませんし、配列要素ではありません`Nothing`XML リテラルを使用する前にします。 必要な要素と属性の名などの値にすることはできません`Nothing`です。  
  
 詳細については、リテラルの特定の型の埋め込み式を使用して、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。  
  
## <a name="scoping-rules"></a>スコープの規則  
 コンパイラは、各 XML リテラルを適切なリテラルの型のコンス トラクターの呼び出しに変換します。 XML リテラルでの埋め込み式とリテラルの内容は、コンス トラクターに引数として渡されます。 つまり、すべて Visual Basic のプログラミング要素、XML リテラルに使用可能なも、埋め込み式を使用できます。  
  
 XML リテラル内でプレフィックスが宣言された XML 名前空間にアクセスすることができます、`Imports`ステートメントです。 新しい XML 名前空間プレフィックスを宣言または要素を使用して、既存 XML 名前空間プレフィックスをシャドウすることができます、`xmlns`属性。 新しい名前空間は、組み込み式内の XML リテラルではなく、その要素の子ノードに使用可能なです。  
  
> [!NOTE]
>  使用して XML 名前空間プレフィックスを宣言する場合、`xmlns`名前空間の属性、属性値が文字列定数を指定する必要があります。 この点を使用して、`xmlns`属性は、使用するように、 `Imports` XML 名前空間を宣言するステートメント。 埋め込み式を使用して、XML 名前空間の値を指定することはできません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
