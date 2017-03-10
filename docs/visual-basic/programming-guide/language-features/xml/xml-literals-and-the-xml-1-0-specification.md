---
title: "XML Literals and the XML 1.0 Specification (Visual Basic) | Microsoft Docs"
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
  - "XML literals [Visual Basic], XML 1.0 specification"
ms.assetid: 46f046e5-293c-41a3-b893-4e5f6e32e78a
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# XML Literals and the XML 1.0 Specification (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] における XML リテラルの構文は、XML \(Extensible Markup Language\) 1.0 仕様の大部分をサポートします。  XML 1.0 仕様の詳細については、W3C Web サイトの「[Extensible Markup Language \(XML\) 1.0](http://go.microsoft.com/fwlink/?LinkId=73927)」を参照してください。  
  
## Visual Basic のサポート対象外  
  
-   XML リテラルの中にドキュメント型定義 \(DTD: Document Type Definition\) は指定できません。  
  
-   XML ドキュメント リテラルは、XML ドキュメント宣言から始める必要があります。  
  
-   XML リテラルでは、1 行に 65,535 を越える文字は使用できません。  
  
-   XML 名前空間プレフィックス、要素名、および属性名では、1,024 文字を越える文字は使用できません。  
  
## Visual Basic がサポートする追加機能  
  
-   ドキュメント リテラルと要素リテラルで使用できる埋め込み式の構文は、XML では有効ではありません。  
  
## 参照  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)