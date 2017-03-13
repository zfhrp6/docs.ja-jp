---
title: "How to: Call an Operator Procedure (Visual Basic) | Microsoft Docs"
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
  - "operator procedures, calling"
  - "procedures, operator"
  - "procedure calls, operator overloading"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "return values, Operator procedures"
  - "overloaded operators, calling"
  - "operator overloading"
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Call an Operator Procedure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

演算子プロシージャを呼び出すには、式の中で演算子記号を使用します。  変換演算子のプロシージャの場合は、[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)を呼び出して、あるデータ型の値を別のデータ型に変換します。  
  
 演算子プロシージャを明示的に呼び出すことはありません。  演算子を通常どおりに使用するのと同じ方法で、演算子や `CType` 関数を代入ステートメントまたは式に定義すると、  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって演算子プロシージャが呼び出されます。  
  
 クラスまたは構造体で演算子を定義することを、演算子を*オーバーロード*するといいます。  
  
### 演算子プロシージャを呼び出すには  
  
1.  通常の方法で、演算子記号を式の中に記述します。  
  
2.  演算子のオペランドのデータ型が適切であること、またオペランドの順序が正しいことを確認します。  
  
3.  演算子によって、式の値が適切に処理されます。  
  
### 変換演算子プロシージャを呼び出す  
  
1.  式の中で `CType` を使用します。  
  
2.  変換処理のオペランドのデータ型が適切であること、またオペランドの順序が正しいことを確認します。  
  
3.  `CType` が変換演算子プロシージャを呼び出し、変換された値を返します。  
  
## 使用例  
 次の例は、2 つの <xref:System.TimeSpan> 構造体を作成し、この 2 つを足し合わせて、結果を 3 つ目の <xref:System.TimeSpan> 構造体に格納します。  <xref:System.TimeSpan> 構造体には演算子プロシージャが定義され、複数の標準演算子をオーバーロードしています。  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 上の例では <xref:System.TimeSpan> で標準の `+` 演算子がオーバーロードされているため、`combinedSpan` の値を計算するときに演算子プロシージャが呼び出されます。  
  
 変換演算子プロシージャを呼び出す例については、「[How to: Use a Class that Defines Operators](../../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)」を参照してください。  
  
## コードのコンパイル  
 使用しているクラスまたは構造体が、必要な演算子を定義していることを確認してください。  
  
## 参照  
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)