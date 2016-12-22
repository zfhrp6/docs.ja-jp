---
title: "How to: Access XML Descendant Elements (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML descendent axis property [Visual Basic]"
  - "XML axis [Visual Basic], descendent"
  - "descendent axis property [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Access XML Descendant Elements (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

この例では、子孫軸プロパティを使用して、ある XML 要素に含まれる、指定した名前を持つすべての XML 要素にアクセスする方法を示します。  具体的には、`Value` プロパティを使用して、`name` 子孫軸プロパティが返すコレクション内の最初の要素の値を取得します。  `name` 子孫軸プロパティは、`contacts` オブジェクトに含まれる `name` という名前の要素をすべて取得します。  また、この例では、`phone` 子孫軸プロパティを使用して、`contacts` オブジェクトに含まれる `phone` という名前のすべての子孫にもアクセスします。  
  
## 使用例  
 [!CODE [VbXMLSamples#31](../CodeSnippet/VS_Snippets_VBCSharp/VbXMLSamples#31)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System.Xml.Linq> 名前空間への参照。  
  
## 参照  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName>   
 [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)   
 [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)   
 [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)