---
title: "XML Comment Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comment literal [Visual Basic]"
  - "XML comments, adding [Visual Basic]"
  - "XML comment literal [Visual Basic]"
  - "XML literals [Visual Basic], comment"
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# XML Comment Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XComment> オブジェクトを表すリテラルです。  
  
## 構文  
  
```  
<!-- content -->  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`<!--`|必ず指定します。  XML コメントの開始を示します。|  
|`content`|必ず指定します。  XML コメント内の表示テキスト。  2 つの連続するハイフン \(\-\-\) は使用できません。また、終了タグの直前にはハイフンを指定できません。|  
|`-->`|必ず指定します。  XML コメントの終了を示します。|  
  
## 戻り値  
 <xref:System.Xml.Linq.XComment> オブジェクト。  
  
## 解説  
 XML コメント リテラルには、ドキュメントの内容は記述しません。ドキュメントに関する情報を記述します。  XML コメント セクションは、"\-\-\>" で終了します。  これには以下のような条件があります。  
  
-   埋め込み式の区切り記号は XML コメントの有効な内容なので、XML コメント リテラルの中で埋め込み式を使用することはできません。  
  
-   XML コメント セクションは、入れ子にできません。これは、`content` に値 "\-\-\>" を格納できないためです。  
  
 XML コメント リテラルは、変数に代入できます。または XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字なしで複数の行に記述できます。  この機能により、XML ドキュメントで内容をコピーし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラムに直接貼り付けることができます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、XML コメント リテラルを<xref:System.Xml.Linq.XComment.%23ctor%2A> コンストラクターの呼び出しに変換します。  
  
## 使用例  
 "This is a comment" というテキストを含む XML コメントを作成する例を次に示します。  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## 参照  
 <xref:System.Xml.Linq.XComment>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)