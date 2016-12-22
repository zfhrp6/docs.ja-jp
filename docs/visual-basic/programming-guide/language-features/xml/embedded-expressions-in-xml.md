---
title: "Embedded Expressions in XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlEmbeddedExpression"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "embedded expressions [Visual Basic]"
  - "LINQ to XML [Visual Basic], embedded expressions"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Embedded Expressions in XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

埋め込み式を使用すると、実行時に評価される式を含む XML リテラルを作成できます。  埋め込み式の構文は `<%=` `expression` `%>` であり、これは [!INCLUDE[vstecasp](../../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] で使用される構文と同じです。  
  
 たとえば、XML 要素リテラルを作成し、埋め込み式とリテラル テキストの内容を結合できます。  
  
 [!CODE [VbXMLSamples#27](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#27)]  
  
 `isbnNumber` に整数 12345 が含まれ、`modifiedDate` に日付 3\/5\/2006 が含まれる場合、このコードを実行すると、`book` の値は次のようになります。  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## 埋め込み式の位置と検証  
 XML リテラル式の中で埋め込み式を使用できる位置は決まっています。  式の位置により、式が返すことのできる型と、`Nothing` の処理方法が決まります。  埋め込み式を使用できる位置と式の型を次の表に示します。  
  
||||  
|-|-|-|  
|リテラルでの位置|式の型|`Nothing` の処理|  
|XML 要素名|<xref:System.Xml.Linq.XName>|エラー|  
|XML 要素の内容|`Object` または `Object` の配列|無視|  
|XML 要素の属性名|<xref:System.Xml.Linq.XName>|属性値も `Nothing` である場合以外はエラー|  
|XML 要素の属性値|`Object`|属性宣言は無視されます|  
|XML 要素の属性|<xref:System.Xml.Linq.XAttribute> または <xref:System.Xml.Linq.XAttribute> のコレクション|無視|  
|XML ドキュメントのルート要素|<xref:System.Xml.Linq.XElement> または 1 つの <xref:System.Xml.Linq.XElement> オブジェクトのコレクションと、任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクトおよび <xref:System.Xml.Linq.XComment> オブジェクト|無視|  
  
-   XML 要素名での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#32](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#32)]  
  
-   XML 要素の内容での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#33](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#33)]  
  
-   XML 要素の属性名での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#34](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#34)]  
  
-   XML 要素の属性値での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#35](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#35)]  
  
-   XML 要素の属性での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#36](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#36)]  
  
-   XML のドキュメント ルート要素での埋め込み式の例:  
  
     [!CODE [VbXMLSamples#37](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#37)]  
  
 `Option Strict` を有効にすると、コンパイラは、必要な型に拡大された各埋め込み式の型をチェックします。  唯一の例外は XML ドキュメントのルート要素の場合で、コードの実行時に検証されます。  `Option Strict` を指定しないでコンパイルする場合は、`Object` 型の式を埋め込むことができ、型は実行時に検証されます。  
  
 内容が省略可能な位置では、`Nothing` を含む埋め込み式は無視されます。  つまり、XML リテラルを使用する前に、要素の内容、属性値、および配列要素が `Nothing` でないことをチェックする必要はありません。  要素名や属性名などの必須の値には、`Nothing` を指定できません。  
  
 特定の型のリテラルにおける埋め込み式の使用の詳細については、「[XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)」および「[XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」を参照してください。  
  
## スコープ規則  
 コンパイラは、各 XML リテラルを、適切なリテラル型に対するコンストラクター呼び出しに変換します。  XML リテラルのリテラル内容と埋め込み式が、引数としてコンストラクターに渡されます。  つまり、XML リテラルに使用できるすべての [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラミング要素を、埋め込み式にも使用できます。  
  
 XML リテラル内では、`Imports` ステートメントで宣言されている XML 名前空間プレフィックスにアクセスできます。  `xmlns` 属性を使用して、要素内で、新しい XML 名前空間プレフィックスを宣言したり、既存の XML 名前空間プレフィックスをシャドウしたりできます。  新しい名前空間は、その要素の子ノードには使用できますが、埋め込み式内の XML リテラルには使用できません。  
  
> [!NOTE]
>  `xmlns` 名前空間属性を使用して XML 名前空間プレフィックスを宣言する場合、属性値を文字列定数にする必要があります。  この点について、`xmlns` 属性を使用することは、`Imports` ステートメントを使用して XML 名前空間を宣言することと似ています。  埋め込み式を使用して、XML 名前空間の値を指定することはできません。  
  
## 参照  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)