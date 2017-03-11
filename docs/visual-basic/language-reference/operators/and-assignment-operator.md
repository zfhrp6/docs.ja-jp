---
title: "&amp;= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.&="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operator &="
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "&= operator [Visual Basic]"
  - "compound assignment statements"
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# &amp;= Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列 \(`String`\) 式を文字列型 \(`String`\) の変数またはプロパティに連結し、その結果を変数またはプロパティに代入します。  
  
## 構文  
  
```  
  
variableorproperty &= expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  文字列 \(`String`\) の変数またはプロパティを指定します。  
  
 `expression`  
 必ず指定します。  任意のブール型 \(`String`\) の式を指定します。  
  
## 解説  
 `&=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  `&=` の演算子は `String` の変数に対する `String` の式を左辺のプロパティを連結しその結果を左辺の変数またはプロパティに代入します。  
  
## オーバーロード  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  `&` 演算子のオーバーロードは、`&=` 演算子の動作に影響を与えます。  コード内で、`&` をオーバーロードするクラスや構造体で `&=` が使用されている場合は、再定義された後の動作を必ず理解するようにしてください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`&=` 演算子を使って、2 つの文字列型 \(`String`\) の変数を連結し、結果を最初の変数に代入します。  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/and-assignment-operator_1.vb)]  
  
## 参照  
 [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)   
 [\+\= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)