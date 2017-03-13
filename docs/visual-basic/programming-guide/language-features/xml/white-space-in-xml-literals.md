---
title: "White Space in XML Literals (Visual Basic) | Microsoft Docs"
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
  - "white space [XML in Visual Basic]"
  - "XML literals [Visual Basic], white space"
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# White Space in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトを作成するときに、XML リテラルから意味のある空白文字のみを組み込みます。  意味のない空白文字は組み込まれません。  
  
## 意味のある空白文字と意味のない空白文字  
 XML リテラル内の空白文字は、次の 3 つの領域でのみ意味があります。  
  
-   属性値に含まれる場合。  
  
-   要素のテキスト内容の一部であり、テキストに他の文字も含まれる場合。  
  
-   要素のテキスト内容の埋め込み式に含まれる場合。  
  
 これら以外の場合は、コンパイラは空白文字を意味のないものとして扱い、リテラルに対する [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] オブジェクトには含めません。  
  
 意味のない空白文字を XML リテラルに含めるには、空白文字のある文字列リテラルを含む埋め込み式を使用します。  
  
> [!NOTE]
>  `xml:space` 属性が XML 要素リテラル内にある場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラはこの属性を <xref:System.Xml.Linq.XElement> オブジェクトに組み込みますが、この属性を追加しても、コンパイラによる空白文字の処理方法は変わりません。  
  
## 例  
 次の例には、2 つの XML 要素 outer と inner が含まれています。  どちらの要素も、テキスト内容に空白文字を含みます。  outer 要素は空白文字と XML 要素のみを含むので、outer 要素内の空白文字は意味がありません。  inner 要素は空白文字とテキストを含むので、inner 要素内の空白文字は意味があります。  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 このコードを実行すると、次のようなテキストが表示されます。  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## 参照  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)