---
title: "How to: Determine the String Associated with an Enumeration Value (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic]"
  - "strings [Visual Basic], enumeration values"
  - "values, enumeration members"
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Determine the String Associated with an Enumeration Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:System.Enum.GetValues%2A> および <xref:System.Enum.GetNames%2A> メソッドを使用すると、列挙値のメンバーに関連付けられている文字列と値を確認できます。  
  
### 列挙値に関連付けられている文字列を確認するには  
  
-   <xref:System.Enum.GetNames%2A> メソッドを使用して、列挙値のメンバーに関連付けられている文字列を取得します。  この例では、列挙型 `flavorEnum` を宣言し、次に <xref:System.Enum.GetNames%2A> メソッドを使用して各メンバーに関連付けられている文字列を表示します。  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## 参照  
 <xref:System.Enum.GetValues%2A>   
 <xref:System.Enum.GetNames%2A>   
 <xref:System.Enum>   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)