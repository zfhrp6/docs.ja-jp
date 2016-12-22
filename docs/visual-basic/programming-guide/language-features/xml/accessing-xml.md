---
title: "Accessing XML in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "LINQ to XML [Visual Basic], accessing XML"
  - "Visual Basic code, XML"
  - "accessing XML [Visual Basic], axis properties"
  - "XML [Visual Basic], axis properties"
  - "XML [Visual Basic], accessing"
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 構造体へのアクセスとナビゲーションを行うための XML 軸プロパティが用意されています。  これらのプロパティは、特殊な構文を使用することで、XML の名前を指定して要素と属性にアクセスできるようにします。  
  
 次の表は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で XML の要素と属性へのアクセスを可能にする言語機能の一覧です。  
  
### XML 軸プロパティ  
  
|プロパティの説明|例|Description|  
|--------------|-------|-----------------|  
|*子軸*|`contact.<phone>`|`contact` 要素の子要素であるすべての `phone` 要素を取得します。|  
|*属性軸*|`phone.@type`|`phone` 要素のすべての `type` 属性を取得します。|  
|*子孫軸*|`contacts...<name>`|要素が出現する階層の深さに関係なく、`contacts` 要素のすべての `name` 要素を取得します。|  
|*拡張インデクサー*|`contacts...<name>(0)`|シーケンスから最初の `name` 要素を取得します。|  
|*value*|`contacts...<name>.Value`|シーケンスの最初のオブジェクトの文字列表現を取得します。シーケンスが空の場合は `Nothing` です。|  
  
## このセクションの内容  
 [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 子孫軸プロパティを使用して、指定した名前を持ち、指定した XML 要素に含まれる、すべての XML 要素にアクセスする方法を示します。  
  
 [How to: Access XML Child Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 子の軸プロパティを使用して、ある XML 要素内で指定した名前を持つすべての XML 子要素にアクセスする方法を示します。  
  
 [How to: Access XML Attributes](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 属性の軸プロパティを使用して、ある XML 要素内で指定した名前を持つすべての XML 属性にアクセスする方法を示します。  
  
 [How to: Declare and Use XML Namespace Prefixes](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 XML 名前空間プレフィックスを宣言し、それを使用して XML 要素を作成し、それにアクセスする方法を示します。  
  
## 関連項目  
 [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 さまざまな XML アクセス プロパティについて説明するセクションへのリンクを示します。  
  
 [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Visual Basic での [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の使用の概要について説明します。  
  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Visual Basic での XML リテラルの使用の概要について説明します。  
  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Visual Basic での XML の読み込みと変更に関するセクションへのリンクを示します。  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Visual Basic での [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の使用方法について説明するセクションへのリンクを示します。