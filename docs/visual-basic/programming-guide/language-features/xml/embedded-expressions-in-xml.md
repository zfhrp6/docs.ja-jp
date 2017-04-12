---
title: "XML (Visual Basic) での埋め込み式 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: e5cd40e55ec23de3ad1bb2f5f065762c893d9cb3
ms.lasthandoff: 03/13/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML での埋め込み式 (Visual Basic)
組み込み式を使用すると、実行時に評価される式が含まれる XML リテラルを作成できます。 埋め込み式の構文は`<%=` `expression` `%>`で使用するための構文は同じ[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]します。  
  
 などを作成する XML 要素リテラル、埋め込み式のリテラル テキストの内容とを組み合わせることです。  
  
 [!code-vb[VbXMLSamples #&27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 場合`isbnNumber`12345 整数が含まれると`modifiedDate`日付を含む 3/5/2006 を実行すると次のコードの値`book`は。  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>埋め込み式の位置と検証  
 埋め込み式は、XML リテラル式の中で特定の場所にしか表示されないことができます。 式の型を式の場所のコントロールを返すことができ、どのように`Nothing`処理されます。 次の表は、許可されている場所と組み込み式の種類について説明します。  
  
|リテラル内の場所|式の型|処理`Nothing`|  
|---|---|---|  
|XML 要素名|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|Error|  
|XML 要素の内容|`Object`またはの配列`Object`|無視|  
|XML 要素の属性名|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|エラー、属性値もしない限り、`Nothing`|  
|XML 要素の属性値|`Object`|属性宣言は無視されます。|  
|XML 要素の属性|<xref:System.Xml.Linq.XAttribute>またはのコレクション<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>|無視|  
|XML ドキュメントのルート要素|<xref:System.Xml.Linq.XElement>またはの&1; つの<xref:System.Xml.Linq.XElement>オブジェクトと任意の数<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction>の</xref:System.Xml.Linq.XElement>コレクション</xref:System.Xml.Linq.XElement>|無視|  
  
-   XML 要素名での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples&#32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   XML 要素のコンテンツ内の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples #&33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   XML 要素の属性名での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples #&34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   XML 要素の属性値内の埋め込み式の例:  
  
     [!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   XML 要素の属性での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples&#36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   XML ドキュメントのルート要素での埋め込み式の例:  
  
     [!code-vb[VbXMLSamples #&37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 有効にした場合`Option Strict`コンパイラは各埋め込み式の型が必要な型に拡大変換ことを確認します。 コードの実行時に検証される XML ドキュメントのルート要素は唯一の例外です。 せずにコンパイルする場合`Option Strict`、型の式を埋め込むことができます`Object`でその型が実行時に確認します。  
  
 コンテンツが、省略可能な場所で埋め込み式を含む`Nothing`は無視されます。 つまり、その要素の内容の属性の値を確認する必要はありませんし、配列の要素ではありません`Nothing`XML リテラルを使用する前にします。 要素と属性名などの値ができないために必要な`Nothing`です。  
  
 リテラルの特定の種類で、組み込み式を使用する方法の詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。  
  
## <a name="scoping-rules"></a>スコープの規則  
 コンパイラは、各 XML リテラルを適切なリテラルの型のコンス トラクターの呼び出しに変換します。 XML リテラルでの埋め込み式とリテラルの内容は、コンス トラクターを引数として渡されます。 つまり、このすべて[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルで使用できるプログラミングの要素も、埋め込み式を使用できます。  
  
 XML リテラル内では、XML 名前空間で宣言されたプレフィックスをアクセスできる、`Imports`ステートメントです。 新しい XML 名前空間プレフィックスを宣言するかを使用して要素に、既存 XML 名前空間プレフィックスをシャドウ、`xmlns`属性です。 新しい名前空間は、組み込み式内の XML リテラルではなく、その要素の子ノードに使用可能なです。  
  
> [!NOTE]
>  使用して XML 名前空間プレフィックスを宣言する場合、`xmlns`名前空間の属性、属性値は定数文字列を指定する必要があります。 この点を使用して、`xmlns`属性は、使用するように、 `Imports` XML 名前空間を宣言するステートメントです。 組み込み式を使用して、XML 名前空間の値を指定することはできません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
