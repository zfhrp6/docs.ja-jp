---
title: "/= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb./="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "/= operator [Visual Basic]"
  - "operator /="
  - "compound assignment statements"
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# /= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティの値を式で指定された値で除算し、その浮動小数点の結果を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty /= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式を指定します。  
  
## 解説  
 `/=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `/=` 演算子が式の値で初めて変数またはプロパティの値 （演算子の左側で除算演算子 （）の右辺に）。  演算子は、変数またはプロパティに、その操作の浮動小数点結果を代入します。  
  
 このステートメントは、変数に `Double` 値を左側にプロパティを割り当てます。  `Option Strict` が `On` の場合、`variableorproperty` は `Double` である必要があります。  `Option Strict` が `Off` の場合、暗黙の型変換が行われ、その結果の値を、実行時にエラーがあればそのエラーと共に `variableorproperty` に割り当てます。  詳細については、「[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」および「[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
## オーバーロード  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  `/` 演算子をオーバーロードすると、`/=` 演算子の動作に影響します。  `/` をオーバーロードしているクラスまたは構造体で `/=` を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`/=` 演算子を使って、最初の整数型 \(`Integer`\) の変数を 2 番目の整数型 \(`Integer`\) の変数で除算し、商を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/floating-point-division-_0_1.vb)]  
  
## 参照  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)