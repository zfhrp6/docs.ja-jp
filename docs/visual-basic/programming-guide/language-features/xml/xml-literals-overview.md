---
title: "XML Literals Overview (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML literals [Visual Basic], about XML literals"
  - "declaring XML literals [Visual Basic]"
  - "LINQ to XML [Visual Basic], XML literals"
  - "literals [Visual Basic], XML"
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML Literals Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*XML リテラル*を使用すると、XML を [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コードに直接組み込むことができます。XML リテラルの構文は [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトを表し、XML 1.0 の構文に似ています。記述するコードは最終的な XML と同じ構造になるため、XML 要素と XML ドキュメントをプログラムによって容易に作成できるようになります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、XML リテラルを [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトにコンパイルします。  [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] には、XML の作成と操作を行うための単純なオブジェクト モデルが用意されており、このモデルは、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] と密接に統合しています。  詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
 XML リテラルに、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 式を埋め込むことができます。  アプリケーションの実行時、リテラルごとに [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトが作成され、埋め込まれた式の値が取り込まれます。  これにより、XML リテラルの中に動的な内容を指定できます。  詳細については、「[Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。  
  
 XML リテラルの構文と XML 1.0 の構文の相違点の詳細については、「[XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)」を参照してください。  
  
## 単純なリテラル  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コード内に有効な XML を入力するか渡すことによって、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトを作成できます。  XML 要素リテラルは、<xref:System.Xml.Linq.XElement> オブジェクトを返します。  詳細については、「[XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)」および「[XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)」を参照してください。  次の例は、複数の子要素を持つ XML 要素を作成します。  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 XML リテラルを `<?xml version="1.0"?>` から始めることで、XML ドキュメントを作成できます。次に例を示します。  XML ドキュメント リテラルは、<xref:System.Xml.Linq.XDocument> オブジェクトを返します。  詳細については、「[XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)」を参照してください。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] での XML リテラルの構文は、XML 1.0 仕様と一致しません。  詳細については、「[XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)」を参照してください。  
  
## 行の継続  
 XML リテラルは、行継続文字 \(空白とアンダースコアを入力して改行するシーケンス\) を使用することなく複数の行にわたって記述できます。  これにより、コード内の XML リテラルを XML ドキュメントと簡単に比較できます。  
  
 コンパイラは、行継続文字を XML リテラルの一部として処理します。  したがって、空白とアンダースコアを入力して改行というシーケンスは、それが [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトの一部の場合のみ使用します。  
  
 ただし、埋め込み式の中に複数の行がある場合は、行継続文字が必要です。  詳細については、「[Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。  
  
## XML リテラルへのクエリの埋め込み  
 埋め込み式の中で、クエリを使用できます。  これを行うと、クエリで返された要素が XML 要素に追加されます。  これにより、ユーザーのクエリの結果などの動的な内容を XML リテラルに追加できます。  
  
 たとえば、次のコードでは、埋め込まれたクエリを使用して `phoneNumbers2` 配列のメンバーから XML 要素を作成し、それらの要素を `contact2` の子として追加します。  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## コンパイラによる XML リテラルからのオブジェクトの作成方法  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、XML リテラルを対応する [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] コンストラクターへの呼び出しに変換して [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトを構築します。  たとえば、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、次のコード例を、XML バージョン命令用の <xref:System.Xml.Linq.XProcessingInstruction> コンストラクターへの呼び出し、`<contact>`、`<name>`、および `<phone>` の各要素用の <xref:System.Xml.Linq.XElement> コンストラクターへの呼び出し、および `type` 属性用の <xref:System.Xml.Linq.XAttribute> コンストラクターへの呼び出しに変換します。  特に、次の例の属性の場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> コンストラクターを 2 回呼び出します。  1 回目の呼び出しでは、`name` パラメーターの値 `type` と、`value` パラメーターの値 `home` を渡します。  2 回目の呼び出しでも `name` パラメーターの値 `type` を渡しますが、`value` パラメーターの値 `work` は渡しません。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## 参照  
 <xref:System.Xml.Linq.XElement>   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)