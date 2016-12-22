---
title: "-= Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.-="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "operator -="
  - "compound assignment statements"
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# -= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変数またはプロパティの値から式で指定された値を減算し、その結果を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty -= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式を指定します。  
  
## 解説  
 `-=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 `-=` 演算子の 1 番目の変数またはプロパティの値から式の値 （演算子の右辺で減算 （）演算子の左側）。  演算子は、変数またはプロパティに、その操作の結果を代入します。  
  
## オーバーロード  
 [\- Operator](../../../visual-basic/language-reference/operators/subtraction-operator.md) は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `-` 演算子のオーバーロードは、`-=` 演算子の動作に影響を与えます。  コード内で、`-` をオーバーロードするクラスや構造体で `-=` が使用されている場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`-=` 演算子を使って、最初の整数型 \(`Integer`\) の変数から 2 番目の整数型 \(`Integer`\) の変数を減算し、結果を 1 番目の変数に代入します。  
  
 [!CODE [VbVbalrOperators#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#11)]  
  
## 参照  
 [\- Operator](../../../visual-basic/language-reference/operators/subtraction-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)