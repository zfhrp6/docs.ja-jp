---
title: "Operator Precedence in Visual Basic | Microsoft Docs"
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
  - "arithmetic operators, precedence"
  - "operator precedence"
  - "logical operators, precedence"
  - "operators [Visual Basic], associativity"
  - "operators [Visual Basic], resolution"
  - "associativity of operators"
  - "operators [Visual Basic], precedence"
  - "precedence, of operators"
  - "comparison operators, precedence"
  - "math operators"
  - "order of precedence"
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Operator Precedence in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

1 つの式の中で複数の演算が実行されるとき、式の各部分の演算子は一定の順序に従って評価され、演算が実行されます。この順序を*演算子の優先順位*と呼びます。  
  
## 優先順位の規則  
 異なる種類の演算子が 1 つの式の中で使用されているとき、各演算子は次の規則に従って評価されます。  
  
-   算術演算子および文字列連結演算子の優先順位については後で説明しますが、どちらも比較演算子、論理演算子、およびビット処理演算子よりも優先順位は高くなっています。  
  
-   すべての比較演算子は優先順位が等しく、論理演算子およびビット処理演算子よりも優先順位が高くなっていますが、算術演算子および文字列連結演算子よりは優先順位が低くなっています。  
  
-   論理演算子およびビット処理演算子の優先順位については後で説明しますが、どちらも算術演算子、文字列連結演算子、および比較演算子よりも優先順位は低くなっています。  
  
-   優先順位の等しい演算子は、式の中の位置に基づいて左から右の順序で評価されます。  
  
## 優先順位  
 演算子は、次の優先順位で評価されます。  
  
### 演算子を待機します。  
 Await  
  
### 算術演算子および文字列連結演算子  
 指数演算 \(`^`\)  
  
 単項恒等演算および否定演算 \(`+`, `–`\)  
  
 乗算および浮動小数点除算 \(`*`, `/`\)  
  
 整数除算 \(`\`\)  
  
 剰余演算 \(`Mod`\)  
  
 加算と減算 \(`+`、`–`\)  
  
 文字列連結 \(`&`\)  
  
 算術ビット シフト \(`<<`、`>>`\)  
  
### 比較演算子  
 すべての比較演算子 \(`=`、`<>`、`<`、`<=`、`>`、`>=`、`Is`、`IsNot`、`Like`、`TypeOf`...`Is`\)。  
  
### 論理演算子およびビット処理演算子  
 否定 \(`Not`\)  
  
 積 \(`And`、`AndAlso`\)  
  
 包括的論理和 \(`Or`、`OrElse`\)  
  
 排他的論理和 \(`Xor`\)  
  
### コメント  
 `=` 演算子は、比較演算子 \(等号\) としてのみ機能し、代入演算子としては使用しません。  
  
 文字列連結演算子 \(`&`\) は算術演算子ではありませんが、優先順位は算術演算子と同じです。  
  
 `Is` 演算子および `IsNot` 演算子は、オブジェクト参照比較演算子です。  この演算子は、2 つのオブジェクトの値を比較しません。2 つのオブジェクト変数が同じオブジェクトを参照しているかどうかを調べるだけです。  
  
## 結合規則  
 乗算と除算など、1 つの式の中で同じ優先順位の演算子が同時に使用されるときは、左から右の順で各演算子が評価されます。  次に例を示します。  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 最初の式は、96 \/ 8 \(結果は 12\) という除算を評価し、次に 12 \/ 4 \(結果は 3\) を評価します。  コンパイラは `n1` の演算を左から右へ評価するため、評価は、この順序を `n2` に明示的に指定した場合とまったく同じになります。  `n1` と `n2` の両方で、結果は 3 になります。  一方、`n3` ではかっこによって 8 \/ 4 が最初に評価されるので、結果は 48 です。  
  
 このような動作から、演算子は [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では*左結合*であると言われます。  
  
## 優先順位と結合規則をオーバーライドする  
 式の一部を他の部分よりも先に評価するには、かっこを使用します。  これによって、優先順位と左結合がオーバーライドされることがあります。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、の前にかっこの外で囲まれた操作を常に実行されます。ただし、かっこ内では、かっこ内のかっこを使用する、通常の優先順位と結合規則を保持します。  次に例を示します。  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## 参照  
 [\= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)