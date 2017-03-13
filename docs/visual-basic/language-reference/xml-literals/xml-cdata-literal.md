---
title: "XML CDATA Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralCdata"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDATA literal [Visual Basic]"
  - "XML CDATA literal [Visual Basic]"
  - "XML literals [Visual Basic], CDATA"
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# XML CDATA Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.Xml.Linq.XCData> オブジェクトを表すリテラルです。  
  
## 構文  
  
```  
<![CDATA[content]]>  
```  
  
## 指定項目  
 `<![CDATA[`  
 必ず指定します。  XML CDATA セクションの開始を示します。  
  
 `content`  
 必ず指定します。  XML CDATA セクションのテキストの内容です。  
  
 `]]>`  
 必ず指定します。  セクションの最後を示します。  
  
## 戻り値  
 <xref:System.Xml.Linq.XCData> オブジェクト。  
  
## 解説  
 XML CDATA セクションは、そのセクションを含む XML と共に格納する必要のある \(ただし、解析されない\) 生のテキストを含みます。  XML CDATA セクションには、任意のテキストを格納できます。  これには、XML の予約文字も含まれます。  XML CDATA セクションは、"\]\]\>" で終了します。  これには以下のような条件があります。  
  
-   埋め込み式の区切り記号は XML CDATA の有効な内容なので、XML CDATA リテラルの中で埋め込み式を使用することはできません。  
  
-   XML CDATA セクションは、入れ子にできません。これは、`content` に値 "\]\]\>" を格納できないためです。  
  
 XML CDATA リテラルは、変数に代入できます。または、XML 要素リテラルに含めることができます。  
  
> [!NOTE]
>  XML リテラルは、行継続文字なしで複数の行に記述できます。  これにより、XML ドキュメントから内容をコピーし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プログラムに直接貼り付けることができます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、XML CDATA リテラルを、<xref:System.Xml.Linq.XCData.%23ctor%2A> コンストラクターの呼び出しに変換します。  
  
## 使用例  
 "Can contain literal \<XML\> tags" というテキストを含む CDATA セクションを作成する例を次に示します。  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## 参照  
 <xref:System.Xml.Linq.XCData>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)