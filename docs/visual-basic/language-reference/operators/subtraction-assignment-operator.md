---
title: "\= Operator | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "\="
  - "vb.\="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "\= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator \= [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# \= Operator
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティの値を式の値で除算し、その結果の整数値を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty \= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式を指定します。  
  
## 解説  
 `\=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `\=` 演算子は、の値を左側の変数またはプロパティの値を分割し、変数に整数の結果を、左側にプロパティを割り当てる  
  
 整数除算の詳細については、「[\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)」を参照してください。  
  
## オーバーロード  
 `\` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `\` 演算子のオーバーロードは、`\=` 演算子の動作に影響を与えます。  コード内で、`\` をオーバーロードするクラスや構造体で `\=` が使用されている場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`\=` 演算子を使って、最初の整数型 \(`Integer`\) の変数を 2 番目の整数型の変数で除算し、整数の結果を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#19](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/subtraction-assignment-o_2_1.vb)]  
  
## 参照  
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)