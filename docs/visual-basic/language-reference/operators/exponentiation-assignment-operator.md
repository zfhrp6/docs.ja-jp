---
title: "^= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.^="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "^= operator [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# ^= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティに対する式のべき乗を求め、その結果を変数またはプロパティに戻します。  
  
## 構文  
  
```  
  
variableorproperty ^= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式を指定します。  
  
## 解説  
 `^=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `^=` 演算子の 1 番目の式の値の電源に変数またはプロパティの値 （演算子の左側で）発生します （演算子の右辺に）。  演算子は、変数またはプロパティに再度その操作の結果を代入します。  
  
 Visual Basic は、すべての指数演算を [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md) で行います。  これ以外の型のオペランドはすべて `Double` に変換され、結果は必ず `Double` 型になります。  
  
 `expression` の値には、小数や負の数 \(またはその両方\) を指定できます。  
  
## オーバーロード  
 [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `^` 演算子のオーバーロードは、`^=` 演算子の動作に影響を与えます。  コード内で、`^` をオーバーロードするクラスや構造体で `^=` が使用されている場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`^=` 演算子を使って、最初の整数型 \(`Integer`\) の変数の n 乗 \(n \= 2 番目の変数の値\) を求め、結果を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## 参照  
 [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)