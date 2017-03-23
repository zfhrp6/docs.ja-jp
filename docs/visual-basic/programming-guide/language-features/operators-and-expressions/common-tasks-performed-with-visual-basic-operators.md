---
title: "Common Tasks Performed with Visual Basic Operators | Microsoft Docs"
ms.custom: ""
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
  - "operators [Visual Basic], logical"
  - "operators [Visual Basic], string concatenation"
  - "operators [Visual Basic], bitwise"
  - "operators [Visual Basic], bit-shift"
  - "operators [Visual Basic], arithmetic"
  - "operators [Visual Basic], string comparison"
  - "operators [Visual Basic], concatenation"
  - "Visual Basic code, operators"
  - "operators [Visual Basic], comparison"
  - "operators [Visual Basic], short-circuiting logical"
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Common Tasks Performed with Visual Basic Operators
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

演算子は、*オペランド*と呼ばれる 1 つまたは複数の式を使用してさまざまな演算を実行します。  
  
## 算術演算子とビット シフト演算子  
 使用可能な算術演算子とビット シフト演算子を次の表に使します。  
  
|||  
|-|-|  
|目的|参照項目|  
|一方の数値を他方の数値に足す|[\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md)|  
|一方の数値を他方の数値から引く|[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|数値の符号を反転させる|[\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|一方の数値に他方の数値を掛ける|[\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md)|  
|一方の数値を他方の数値で割る|[\/ Operator](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)|  
|一方の数値を他方の数値で割ったときの商を求める \(剰余は求めない\)|[\\ Operator](../../../../visual-basic/language-reference/operators/integer-division-operator.md)|  
|一方の数値を他方の数値で割ったときの剰余を求める \(商は求めない\)|[Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)|  
|一方の数値を他方の数値で累乗する|[^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)|  
|数値のビット パターンを左にシフトする|[\<\< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md)|  
|数値のビット パターンを右にシフトする|[\>\> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md)|  
  
## 比較演算子  
 使用可能な比較演算子を次の表に示します。  
  
|||  
|-|-|  
|目的|参照項目|  
|2 つの値が等しいことを確認する|`=` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|2 つの値が等しくないことを確認する|`<>` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|一方の値が他方の値より小さいことを確認する|`<` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|一方の値が他方の値より大きいことを確認する|`>` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|一方の値が他方の値以下であることを確認する|`<=` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|一方の値が他方の値以上であることを確認する|`>=` 演算子 \([Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)\)|  
|2 つのオブジェクト変数が同じオブジェクト インスタンスを参照していることを確認する|[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)|  
|2 つのオブジェクト変数が別のオブジェクト インスタンスを参照していることを確認する|[IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)|  
|オブジェクトが特定の型であることを確認する|[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)|  
  
## 連結演算子  
 使用可能な連結演算子を次の表に示します。  
  
|||  
|-|-|  
|目的|参照項目|  
|複数の文字列を 1 つの文字列に結合する|`&` 演算子 \([Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)\)|  
|数値を文字列値に結合する|`+` 演算子 \([Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)\)|  
  
## 論理演算子とビット処理演算子  
 使用可能な論理演算子とビット処理演算子を次の表に示します。  
  
|||  
|-|-|  
|目的|参照項目|  
|ブール値の論理否定を求める|[Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md)|  
|2 つのブール値の論理積を求める|[And Operator](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|2 つのブール値の包括的論理和を求める|[Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|2 つのブール値の排他的論理和を求める|[Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|2 つのブール値の論理積をショートサーキットで求める|[AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md)|  
|2 つのブール値の包括的論理和をショート サーキットで求める|[OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md)|  
|2 つの整数値のビットごとの論理積を求める|[And Operator](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|2 つの整数値のビットごとの包括的論理和を求める|[Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|2 つの整数値のビットごとの排他的論理和を求める|[Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|整数値のビットごとの論理否定を求める|[Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md)|  
  
## 参照  
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operators Listed by Functionality](../../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)