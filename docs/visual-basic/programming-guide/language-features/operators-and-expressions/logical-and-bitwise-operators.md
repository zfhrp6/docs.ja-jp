---
title: "Logical and Bitwise Operators in Visual Basic | Microsoft Docs"
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
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "operators [Visual Basic], logical"
  - "AndAlso operator"
  - "Not operator [Visual Basic], Boolean expressions"
  - "Xor operator [Visual Basic], Boolean expressions"
  - "And operator [Visual Basic], logical operators"
  - "logical operators"
  - "expressions [Visual Basic], Boolean"
  - "Or operator, logical operators"
  - "Visual Basic code, operators"
  - "short-circuiting, logical operators"
  - "logical operators, short-circuiting"
  - "Visual Basic code, expressions"
  - "logical operators, binary"
  - "OrElse operator [Visual Basic]"
  - "logical operators, unary"
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Logical and Bitwise Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

論理演算子は、`Boolean` 式を比較し、結果として `Boolean` 値を返します。  `And`、`Or`、`AndAlso`、`OrElse`、および `Xor` 演算子は、オペランドを 2 つ取るので*二項*演算子と呼ばれます。一方、`Not` 演算子は、オペランドを 1 つ取るので*単項*演算子と呼ばれます。  これらの演算子の中には、整数値に対してビットごとの論理演算を実行できるものもあります。  
  
## 単項論理演算子  
 [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) は、`Boolean` 式の*論理否定*を求めます。  これにより、オペランドの論理上の逆の値が得られます。  式の評価が `True` の場合、`Not` は `False` を返します。式の評価が `False` の場合、`Not` は `True` を返します。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_1.vb)]  
  
## 二項論理演算子  
 [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) は、2 つの `Boolean` 式の*論理積*を求めます。  両方の式の評価が `True` の場合、`And` は `True` を返します。  少なくとも一方の式の評価が `False` の場合、`And` は `False` を返します。  
  
 [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) は、2 つの `Boolean` 式の*論理和*または*包含*を実行します。  いずれかの式の評価が `True` の場合、または両方の式の評価が `True` の場合は、`Or` は `True` を返します。  どちらの式の評価も `True` でない場合は、`Or` は `False` を返します。  
  
 [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) は、2 つの `Boolean` 式の*排他的論理和*を求めます。  どちらか一方の式の評価が `True` で、もう一方はそうでない場合は、`Xor` は `True` を返します。  両方の式の評価が `True` の場合、または両方の式の評価が `False` の場合は、`Xor` は `False` を返します。  
  
 `And`、`Or`、および `Xor` 演算子の例を次に示します。  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_2.vb)]  
  
## 論理演算子のショートサーキット  
 [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md)は、2 つの `Boolean` 式の論理積を求めるという点では `And` 演算子によく似ています。  両者の大きな違いは、`AndAlso` は*ショートサーキット*の動作を示すという点にあります。  `AndAlso` 式の 1 番目の式の評価が `False` の場合は、2 番目の式の評価がどうなっても最終的な結果は変わらないので、2 番目の式は評価されないまま、`AndAlso` は `False` を返します。  
  
 同様に、[OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md)は、ショートサーキット評価で 2 つの `Boolean` 式の論理和を求めます。  `OrElse` 式の 1 番目の式の評価が `True` の場合は、2 番目の式の評価がどうなっても最終的な結果は変わらないので、2 番目の式は評価されないまま、`OrElse` は `True` を返します。  
  
### ショートサーキットの長所と短所  
 ショートサーキットを使用すると、論理演算の最終的な結果に影響しない式は評価されないので、パフォーマンスが向上します。  しかし、その式で追加の処理を実行していた場合は、ショートサーキットによりその処理がスキップされます。  たとえば、その式に `Function` プロシージャの呼び出しが含まれている場合は、その式がショートサーキットされるとプロシージャが呼び出されないので、`Function` プロシージャ内の追加コードが実行されません。  したがって、関数が実行されることがほとんどなく、正しくテストされないことがあります。  また、プログラム ロジックが `Function` 内のコードに依存している場合もあります。  
  
 次の例は、`And` と `Or`、さらにそのショートサーキット版の演算子の違いを示しています。  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/logical-and-bitwise-oper_5.vb)]  
  
 上記の例では、`checkIfValid()` の呼び出しがショートサーキットされると、このプロシージャ内の重要なコードが実行されないという点に注意してください。  1 つ目の `If` ステートメントは、`12 > 45` が `False` を返すときでも `checkIfValid()` を呼び出します。なぜなら、`And` はショートサーキットを行わないからです。  2 つ目の `If` ステートメントは、`checkIfValid()` を呼び出しません。`12 > 45` が `False` を返すので、`AndAlso` が 2 つ目の式をショートサーキットするからです。  3 つ目の `If` ステートメントは、`12 < 45` が `True` を返すときでも `checkIfValid()` を呼び出します。なぜなら、`Or` はショートサーキットを行わないからです。  4 つ目の `If` ステートメントは、`checkIfValid()` を呼び出しません。`12 < 45` が `True` を返すので、`OrElse` が 2 つ目の式をショートサーキットするからです。  
  
## ビット処理演算  
 ビット処理演算子は、2 つの整数値をバイナリ \(基数 2\) の形式で評価します。  対応する位置のビットを比較し、比較結果に基づいて値を割り当てます。  次に `And` 演算子の例を示します。  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/visualbasic/logical-and-bitwise-oper_6.vb)]  
  
 この例では、`x` の値が 1 に設定されます。  このような結果になる理由は次のとおりです。  
  
-   2 つの値がバイナリとして扱われます。  
  
     バイナリ形式の 3 \= 011  
  
     バイナリ形式の 5 \= 101  
  
-   `And` 演算子は、このバイナリ表現を 1 桁 \(1 ビット\) ずつ比較します。  ある位置のビットが両方とも 1 だった場合は、結果の同じ位置に 1 が配置されます。  いずれかが 0 だった場合は、その位置に 0 が配置されます。  したがって、上の例は次のように評価されます。  
  
     011 \(バイナリ形式の 3\)  
  
     101 \(バイナリ形式の 5\)  
  
     001 \(バイナリ形式の結果\)  
  
-   この結果は 10 進数として扱われます。  001 という値は 1 のバイナリ表現なので、`x` \= 1 となります。  
  
 ビットごとの `Or` 演算も同様です。ただし、その場合は、比較するビットの一方または両方が 1 のときに結果ビットが 1 になります。  `Xor` では、比較するビットのいずれか一方だけが 1 のときのみ、結果ビットが 1 になります。  `Not` のオペランドは 1 つだけであり、そのすべてのビット \(符号ビットを含む\) を反転させた値が結果になります。  つまり、符号付き正数を与えると `Not` は必ず負数を返し、負数を与えると `Not` は必ず正数または 0 の値を返します。  
  
 `AndAlso` 演算子と `OrElse` 演算子はビット処理演算をサポートしません。  
  
> [!NOTE]
>  ビット処理演算を実行できるのは整数型だけです。  浮動小数点値に対してビット処理演算を実行するには、事前に整数型に変換する必要があります。  
  
## 参照  
 [Logical\/Bitwise Operators](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)