---
title: "= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Assign"
  - "vb.="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "= operator [Visual Basic]"
  - "= assignment statements [Visual Basic]"
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# = Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

値を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty = value  
```  
  
## 指定項目  
 `variableorproperty`  
 任意の書き込み可能な変数または任意のプロパティを指定します。  
  
 `value`  
 任意のリテラル、定数、数式のいずれかを指定します。  
  
## 解説  
 等号 \(`=`\) の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  `=` 演算子は、右側の値を左側の変数またはプロパティに代入します。  
  
> [!NOTE]
>  `=` 演算子は、比較演算子としても使用されます。  詳細については、「[Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)」を参照してください。  
  
## オーバーロード  
 `=` 演算子は比較演算子としてのみオーバーロードできます。代入演算子としてはオーバーロードできません。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 代入演算子の例を次に示します。  右側の値が左側の変数に代入されます。  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/assignment-operator_1.vb)]  
  
## 参照  
 [&\= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [\*\= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [\-\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [^\= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)