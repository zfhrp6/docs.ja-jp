---
title: "Efficient Combination of Operators (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressions [Visual Basic], parentheses"
  - "operators [Visual Basic], associativity"
  - "expressions [Visual Basic], operators"
  - "operators [Visual Basic], precedence"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "operators [Visual Basic], complex expressions"
  - "expressions [Visual Basic], complex"
  - "parentheses, complex expressions"
  - "numeric expressions"
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Efficient Combination of Operators (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

複合式では、さまざまな演算子を使用できます。  次に例を示します。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 演算子の優先順位の規則を完全に理解していないと、この例に示したような複合式は作成できません。  詳細については、「[Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)」を参照してください。  
  
## かっこを使った式  
 演算子の優先順位によって決まっている順序とは違う順序で演算を実行することもできます。  例を次に示します。  
  
 `x = z * y + 4`  
  
 この例では、`z` を `y` と掛けた後、その結果を `4` に足しています。  しかし、`y` と `4` を先に足してから、その結果を `z` に掛ける必要がある場合は、かっこを使って通常の演算子の優先順位をオーバーライドできます。  式をかっこで囲むと、演算子の優先順位に関係なく、かっこで囲んだ式が最初に計算されます。  上記の例で加算を先に実行するには、次のように式を書き直します。  
  
 `x = z * (y + 4)`  
  
 この例では、`y` と `4` を足した後で、その結果を `z` に掛けます。  
  
### かっこで入れ子にした式  
 かっこを複数のレベルで使って式を入れ子にすると、優先順位をさらにオーバーライドできます。  最も深いかっこの中にある式が最初に評価され、2 番目に深いかっこ内の式が次に評価されます。この手順が、最も外側のかっこまで続けられ、最後にかっこの外部にある式が評価されます。  次に例を示します。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 この例では、`z + 2` が最初に評価され、次に他のかっこ内の式が評価されます。  指数演算は、通常ならば加算や乗算より優先順位は上ですが、他の式がすべてかっこで囲まれているため、この例では最後に計算されます。  
  
## 参照  
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [How to: Calculate Numeric Values](../Topic/How%20to:%20Calculate%20Numeric%20Values%20\(Visual%20Basic\).md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)