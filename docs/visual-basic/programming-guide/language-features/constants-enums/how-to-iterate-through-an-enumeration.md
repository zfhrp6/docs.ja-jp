---
title: "How to: Iterate Through An Enumeration in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arrays [Visual Basic], iterating"
  - "enumerations [Visual Basic], iterating"
  - "ListBox control [Windows Forms], populating from an enumeration"
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# How to: Iterate Through An Enumeration in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

複数の関連する定数を操作する場合や、複数の定数値に名前を関連付ける場合は、列挙型を使うと便利です。  列挙型を反復処理するために、<xref:System.Enum.GetValues%2A> メソッドを使用して、列挙型を配列に移動できます。  また、`For...Each` ステートメントを使用したり、<xref:System.Enum.GetNames%2A> メソッドまたは <xref:System.Enum.GetValues%2A> メソッドを使用して文字列や数値を抽出したりして、列挙型を反復処理することもできます。  
  
### 列挙型を反復処理するには  
  
-   他の変数で行うように、配列を渡す前に、配列を宣言し、<xref:System.Enum.GetValues%2A> メソッドを使用して列挙型を変換します。  次の例は、列挙体 <xref:Microsoft.VisualBasic.FirstDayOfWeek> を繰り返し処理して、列挙体の各メンバーを表示します。  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#7)]  
  
## 参照  
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)