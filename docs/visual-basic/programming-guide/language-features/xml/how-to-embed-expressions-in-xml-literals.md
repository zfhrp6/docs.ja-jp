---
title: "How to: Embed Expressions in XML Literals (Visual Basic) | Microsoft Docs"
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
  - "embedded expressions [Visual Basic]"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Embed Expressions in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

XML リテラルと埋め込み式を組み合わせて、実行時に作成される内容を格納する XML ドキュメント、XML フラグメント、または XML 要素を作成できます。  以下の例では、埋め込み式を使用して、要素の内容、属性、および要素名を実行時に設定する方法を示します。  
  
 埋め込み式の構文は `<%=` `exp` `%>` です。これは、[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] で使用される構文と同じです。詳細については、「[Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] API を使用して [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトを作成することもできます。  詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。  
  
## 手順  
  
#### テキストを要素の内容として挿入するには  
  
-   次の例は、`contactName` 変数に格納されているテキストを、開始名前要素と終了名前要素の間に挿入する方法を示します。  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_1.vb)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### テキストを属性値として挿入するには  
  
-   次の例は、`phoneType` 変数に格納されたテキストを、`type` 属性の値として挿入する方法を示します。  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_2.vb)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### 要素名のテキストを挿入するには  
  
-   次の例は、`elementName` 変数に格納されたテキストを、要素の名前として挿入する方法を示します。  
  
     この方法で要素を作成するときは、\<\/\> タグで閉じる必要があります。  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-embed-expressions_3.vb)]  
  
     この例を実行すると、次の出力が生成されます。  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## 参照  
 [How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)