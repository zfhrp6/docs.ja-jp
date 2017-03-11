---
title: "*= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.*="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator *="
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "*= operator [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# *= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数またはプロパティの値を式で指定された値で乗算し、その結果を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty *= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式を指定します。  
  
## 解説  
 `*=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `*=` 演算子は、変数またはプロパティの値によって最初に式の値 （）演算子の右辺に増加します （演算子の左側）。  演算子は、変数またはプロパティに、その操作の結果を代入します。  
  
## オーバーロード  
 [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  `*` 演算子をオーバーロードすると、`*=` 演算子の動作に影響します。  `*` をオーバーロードしているクラスまたは構造体で `*=` を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`*=` 演算子を使って、最初の整数型 \(`Integer`\) の変数を 2 番目の整数型 \(`Integer`\) の変数で乗算し、結果を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/multiplication-assignmen_1_1.vb)]  
  
## 参照  
 [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)