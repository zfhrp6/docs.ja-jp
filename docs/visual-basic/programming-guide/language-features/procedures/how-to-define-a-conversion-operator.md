---
title: "How to: Define a Conversion Operator (Visual Basic) | Microsoft Docs"
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
  - "procedures, defining"
  - "operators [Visual Basic], defining"
  - "procedures, operator"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "operator overloading"
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Define a Conversion Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

定義されたクラスまたは構造体がある場合、その型と別のデータ型 \(`Integer`、`Double`、または `String`\) の間の型変換演算子を定義できます。  
  
 型変換はクラスまたは構造体の内部に [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) プロシージャとして定義します。  すべての変換プロシージャは `Public Shared` であることが必要です。また、それぞれに [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) または [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) を指定する必要があります。  
  
 クラスまたは構造体で演算子を定義することを、演算子を*オーバーロード*するといいます。  
  
## 使用例  
 構造体  `digit`  と `Byte` の間の変換演算子を定義する例は次のようになります。  
  
 [!code-vb[VbVbcnProcedures#27](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 構造体 `digit` を、次のコードを使用してテストしてください。  
  
 [!code-vb[VbVbcnProcedures#28](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## 参照  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Call an Operator Procedure](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)