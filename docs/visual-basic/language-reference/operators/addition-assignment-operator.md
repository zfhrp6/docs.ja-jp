---
title: "+= Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.+="
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "+= operator [Visual Basic]"
  - "assignment statements, compound"
  - "statements [Visual Basic], compound assignment"
  - "+= operator [Visual Basic], appending strings"
  - "compound assignment statements"
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# += Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

数式の値を、数値型の変数またはプロパティの値に加算し、その結果を変数またはプロパティに代入します。  これを利用して、`String` 式を `String` 変数またはプロパティに連結し、その結果を変数またはプロパティに代入することもできます。  
  
## 構文  
  
```  
  
variableorproperty += expression  
```  
  
## 指定項目  
 `variableorproperty`  
 必ず指定します。  任意の数値または `String` の変数またはプロパティです。  
  
 `expression`  
 必ず指定します。  任意の数式または文字列 \(`String`\) 式を指定します。  
  
## 解説  
 `+=` 演算子の左側には、スカラー変数、プロパティ、配列の要素なども指定できます。  変数またはプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) にすることはできません。  
  
 変数に `+=` の演算子は右辺の値を左辺のプロパティを追加しその結果を左辺の変数またはプロパティに代入します。  または `+=` の演算子が `String` の変数に対する `String` の式を左辺のプロパティを連結するために使用できる結果を左辺の変数またはプロパティに代入します。  
  
> [!NOTE]
>  `+=` 演算子を使用すると、加算と文字列連結のどちらが行われるのか、事前にはわかりにくい場合があります。  連結に `&=` 演算子を使用することで、あいまいさがなくなり、プログラムの可読性が向上します。  
  
 コンパイル環境に厳密な型指定規則が設定されている場合、この代入演算子は、縮小変換ではなく、暗黙的に拡大変換を実行します。  これらの変換の詳細については、「[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  厳密な型指定規則と寛容な型指定規則の詳細については、「[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。  
  
 寛容な型指定規則が適用される場合、`+=` 演算子は、`+` 演算子と同様に、文字列と数値の暗黙の変換を実行します。  各変換の詳細については、「[\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)」を参照してください。  
  
## オーバーロード  
 `+` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  `+` 演算子をオーバーロードすると、`+=` 演算子の動作に影響します。  `+` をオーバーロードしているクラスまたは構造体で `+=` を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 次の例では、`+=` 演算子を使って 2 つの変数の値を結合します。  前半では、`+=` を使って最初の数値変数の値を 2 番目の数値変数の値に加算します。  後半では、`+=` を使って最初の `String` 変数の値を 2 番目の `String` 変数の値に連結します。  どちらの場合も、結果は最初の変数に代入されます。  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-assignment-oper_1_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/addition-assignment-oper_1_2.vb)]  
  
 `num1` の値は 13 になり、`str1` の値は "103" になります。  
  
## 参照  
 [\+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md)   
 [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)