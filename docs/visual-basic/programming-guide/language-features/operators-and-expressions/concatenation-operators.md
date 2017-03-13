---
title: "Concatenation Operators in Visual Basic | Microsoft Docs"
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
  - "& operator [Visual Basic], concatenation"
  - "concatenation operators"
  - "operators [Visual Basic], concatenation"
  - "Visual Basic code, operators"
  - "+ operator [Visual Basic], concatenation"
  - "concatenation operators, Visual Basic strings"
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Concatenation Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

連結演算子は、複数の文字列を結合して 1 つの文字列にします。  連結演算子には、`+` と `&` の 2 つがあります。  どちらの演算子も、次の例に示すように基本的な連結演算を行います。  
  
 [!CODE [Dim x As String = "Mic" & "ro" & "soft" Dim y As String = "Mic" + "ro" + "soft" ' The preceding statements set both x and y to "Microsoft".](Dim x As String = "Mic" & "ro" & "soft" Dim y As String = "Mic" + "ro" + "soft" ' The preceding statements set both x and y to "Microsoft".)]  
  
 これらの演算子は、次のように `String` 型の変数を連結することもできます。  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## 2 つの連結演算子の相違点  
 [\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) の基本的な機能は、2 つの数値を加算することです。  ただし、数値オペランドを文字列オペランドに連結することもできます。  `+` 演算子は、一連の複雑な規則に従って、加算、連結、コンパイル エラーのシグナルの送信、ランタイム <xref:System.InvalidCastException> 例外のスローのどれを行うかを決定します。  
  
 [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) は、`String` オペランドに対してだけ定義されており、`Option Strict` の設定に関係なく、常にオペランドを `String` に拡大変換します。  文字列の連結には `&` 演算子を使用することをお勧めします。この演算子は文字列専用として定義されているため、意図しない変換が発生する可能性を減らすことができます。  
  
## パフォーマンス: 文字列と StringBuilder  
 連結、削除、置換などの文字列操作を何度も行う場合は、<xref:System.Text> 名前空間の <xref:System.Text.StringBuilder> クラスを使用するとパフォーマンスが向上します。  <xref:System.Text.StringBuilder> オブジェクトを作成して初期化するには追加の命令が必要であり、最終的な値を `String` に変換するにはまた別の命令が必要になりますが、<xref:System.Text.StringBuilder> は高速に実行できるため、この時間を埋め合わせることができます。  
  
## 参照  
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)