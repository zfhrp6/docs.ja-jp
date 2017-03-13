---
title: "- Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Negate"
  - "vb.-"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "- operator [Visual Basic]"
  - "operators [Visual Basic], subtraction"
  - "operators [Visual Basic], difference"
  - "negation operator"
  - "operators [Visual Basic], arithmetic"
  - "subtraction operator, syntax"
  - "arithmetic operators, subtraction"
  - "difference operator"
  - "math operators"
  - "operators [Visual Basic], negation"
  - "minus operator [Visual Basic]"
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# - Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つの数式の差、または、数式の負の値を返します。  
  
## 構文  
  
```  
  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## 指定項目  
 `expression1`  
 必ず指定します。  任意の数式を指定します。  
  
 `expression2`  
 `–` 演算子が負の値を計算している場合を除き、必ず指定します。  任意の数式を指定します。  
  
## 結果  
 結果は、`expression1` と `expression2` の差、または `expression1` を否定した値です。  
  
 結果のデータ型は、`expression1` と `expression2` のデータ型に適した数値型です。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。  
  
## サポートされている型  
 すべての数値型。  これには、符号なし、浮動小数点、`Decimal` が含まれます。  
  
## 解説  
 この構文の最初の使用例では、`–` 演算子が、2 つの数式の差を求める*二項の*減算演算子として使用されています。  
  
 2 つ目の使用例では、`–` 演算子は、式の負の値を求める*単項の*否定演算子として使用されています。  この場合、否定は `expression1` の符号を反転させるので、`expression1` が負の場合、結果は正になります。  
  
 いずれかの式が [Nothing](../../../visual-basic/language-reference/nothing.md) と評価される場合、`–` 演算子はこれを 0 と見なします。  
  
> [!NOTE]
>  `–` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`–` 演算子を使用して 2 つの数値の差を求め、結果を返し、その後、数値を否定します。  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 これらのステートメントを実行した後では、`binaryResult` には 124.45、`unaryResult` には –334.90 が含まれます。  
  
## 参照  
 [\-\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)