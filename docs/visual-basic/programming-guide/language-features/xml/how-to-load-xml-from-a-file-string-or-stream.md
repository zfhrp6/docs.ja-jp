---
title: "How to: Load XML from a File, String, or Stream (Visual Basic) | Microsoft Docs"
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
  - "XML [Visual Basic], loading"
  - "LINQ to XML [Visual Basic], loading XML from files"
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Load XML from a File, String, or Stream (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)を作成し、いくつかのメソッドを使用して、ファイル、文字列、ストリームなどの外部ソースからコンテンツを取得できます。  このようなメソッドを次の例に示します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### ファイルから XML を読み込むには  
  
-   <xref:System.Xml.Linq.XElement> オブジェクトや <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルをファイルから取得するには、`Load` メソッドを使用します。  このメソッドには、ファイル パス、テキスト ストリーム、または XML ストリームを入力として渡すことができます。  
  
     次のコード例は、<xref:System.Xml.Linq.XDocument.Load%28System.String%29> メソッドを使用して、テキスト ファイルから <xref:System.Xml.Linq.XDocument> オブジェクトに XML を取得する方法を示しています。  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### 文字列から XML を読み込むには  
  
-   <xref:System.Xml.Linq.XElement> オブジェクトや <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルを文字列から取得するには、`Parse` メソッドを使用できます。  
  
     次のコード例は、<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName> メソッドを使用して、文字列から <xref:System.Xml.Linq.XDocument> オブジェクトに XML を取得する方法を示しています。  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### ストリームから XML を読み込むには  
  
-   <xref:System.Xml.Linq.XElement> オブジェクトや <xref:System.Xml.Linq.XDocument> オブジェクトなどの XML リテラルをストリームから取得するには、`Load` メソッドまたは <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> メソッドを使用できます。  
  
 次のコード例は、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを使用して、XML ストリームから <xref:System.Xml.Linq.XDocument> オブジェクトに XML を取得する方法を示しています。  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## 参照  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)