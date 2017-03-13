---
title: "Constant and Literal Data Types (Visual Basic) | Microsoft Docs"
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
  - "declaring constants, literal data types"
  - "data types [Visual Basic], declaring"
  - "constants, declaring"
  - "explicit declarations"
  - "literals, coercing data type"
  - "declarations, data types"
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Constant and Literal Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

リテラルは、変数の値または式の結果としてではなく、数字の 3 や文字列 "Hello" などのように、そのままの形で表される値です。  定数は、リテラルの代わりに使用される有効な名前であり、値が変化する変数とは対照的に、プログラム全体をとおして同じ値を保持します。  
  
 [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) が `Off` で、[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) が `On` である場合、明示的にデータ型を指定してすべての定数を宣言する必要があります。  次の例では、`MyByte` のデータ型が、データ型 `Byte` として明示的に宣言されています。  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 `Option Infer` が `On`、または `Option Strict` が `Off` である場合、`As` 句でデータ型を指定せずに定数を宣言する必要があります。  コンパイラにより、式の種類から定数の型が決定されます。  整数リテラルは、既定で整数型 \(`Integer`\) にキャストされます。  浮動小数点数の既定のデータ型は `Double` であり、キーワード `True` と `False` は `Boolean` 定数を指定します。  
  
## リテラルと型の自動変換  
 大きな整数リテラル値を `Decimal` の変数に代入する場合など、リテラルを特定のデータ型に強制的に変換することが必要な場合があります。  次の例では、エラーが発生します。  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 このエラーの原因は、リテラルの表現にあります。  `Decimal` データ型はこの大きさの値を格納できますが、リテラルは暗黙的に、この大きさの値を格納できない `Long` として表されています。  
  
 リテラルを特定のデータ型に自動的に変換するには、2 つの方法があります。リテラルに型文字を追加する方法と、リテラルを囲み文字の間に配置する方法です。  型文字や囲み文字は定数の直前、直後に指定する必要があります。間にはどのような文字も空白も指定しないでください。  
  
 前の例を修正するには、リテラルの末尾に型文字 `D` を追加します。これにより、リテラルが `Decimal` として表されるようになります。  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 型文字と囲み文字の正しい使用方法を次の例に示します。  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 次の表は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で使用できる囲み文字と型文字の一覧です。  
  
||||  
|-|-|-|  
|データ型|囲み文字|末尾の型文字|  
|`Boolean`|\(なし\)|\(なし\)|  
|`Byte`|\(なし\)|\(なし\)|  
|`Char`|"|C|  
|`Date`|\#|\(なし\)|  
|`Decimal`|\(なし\)|D または @|  
|`Double`|\(なし\)|R または \#|  
|`Integer`|\(なし\)|I または %|  
|`Long`|\(なし\)|L または &|  
|`Short`|\(なし\)|S|  
|`Single`|\(なし\)|F または \!|  
|`String`|"|\(なし\)|  
  
## 参照  
 [User\-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)