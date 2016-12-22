---
title: "How to: Refer to an Enumeration Member (Visual Basic) | Microsoft Docs"
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
  - "enumerations [Visual Basic], referring to"
  - "values, associating constant values with names"
  - "enumeration members"
  - "constants, enumerated"
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Refer to an Enumeration Member (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

複数の関連する定数を操作する場合や、複数の定数値に名前を関連付ける場合は、列挙型を使うと便利です。  たとえば、一連の整数型の定数を曜日に関連付けて列挙型として宣言すると、整数値の代わりに曜日名を使うことができます。  
  
 `Imports` ステートメントによって、完全修飾名の使用を回避できます。  詳細については、「[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)」を参照してください。  
  
### 列挙型のメンバーを参照するには  
  
-   メンバー名を列挙型で修飾します。  たとえば次の例では、変数 `DayValue` に、`FirstDayOfWeek` 列挙型の `Saturday` メンバーを割り当てます。  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## 参照  
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)