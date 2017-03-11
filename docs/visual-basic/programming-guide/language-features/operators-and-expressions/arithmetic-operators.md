---
title: "Arithmetic Operators in Visual Basic | Microsoft Docs"
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
  - "type safety"
  - "operators [Visual Basic], bitwise"
  - "operators [Visual Basic], bit-shift"
  - "bitwise operators"
  - "bit-shift operators"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "division, by zero"
  - "Visual Basic code, operators"
  - "arithmetic operators, about arithmetic operators"
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Arithmetic Operators in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

算術演算子を使うと、リテラル、変数、その他の式、関数やプロパティの呼び出し、および定数によって表される数値の計算を含む一般的な算術演算を実行できます。  また、ビット シフト演算子も算術演算子に分類されます。ビット シフト演算子はオペランドの個々のビットを操作し、オペランドのビット パターンを左または右にシフトします。  
  
## 算術演算  
 式の中の 2 つの値を足す場合は [\+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) を使い、一方の値からもう一方の値を引く場合は [\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md) を使います。次に例を示します。  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_1.vb)]  
  
 否定にも [\- Operator](../../../../visual-basic/language-reference/operators/subtraction-operator.md) を使いますが、1 つのオペランドにのみ使います。次に例を使用します。  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_2.vb)]  
  
 乗算には [\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) を使い、除算には [\/ Operator](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md) を使います。次に例を示します。  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_3.vb)]  
  
 指数演算には [^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md) を使います。次に例を示します。  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_4.vb)]  
  
 整数の除算には [\\ Operator](../../../../visual-basic/language-reference/operators/integer-division-operator.md) を使用します。  整数の除算は商を返します。商とは、被除数を除数で割った値を、余りを無視して表した整数です。  この演算子の場合、除数と被除数はどちらも整数型 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`\) であることが必要です。  他のデータ型を使用する場合は、先に整数型に変換する必要があります。  次に整数の除算の例を示します。  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_5.vb)]  
  
 剰余演算には [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md) を使います。  この演算子は、被除数を除数で割った余りを返します。  除数と被除数が両方とも整数型の場合、戻り値は整数型になります。  除数と被除数が両方とも浮動小数点型の場合、戻り値は浮動小数点型になります。  次にコード例を示します。  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_7.vb)]  
  
### 0 による除算  
 0 による除算の結果は、含まれているデータ型によって異なります。  整数の除算 \(`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`\) では、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] は <xref:System.DivideByZeroException> 例外をスローします。  除算演算子を `Decimal` データ型や `Single` データ型に使用した場合も、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] は <xref:System.DivideByZeroException> 例外をスローします。  
  
 `Double` データ型を含む浮動小数点の除算では、例外はスローされず、結果は被除数に応じて <xref:System.Double.NaN>、<xref:System.Double.PositiveInfinity>、または <xref:System.Double.NegativeInfinity> のいずれかを表すクラス メンバーになります。  `Double` 値を 0 で除算しようとした結果を表にまとめると、次のようになります。  
  
|||||  
|-|-|-|-|  
|被除数のデータ型|除数のデータ型|被除数の値|結果|  
|`Double`|`Double`|0|<xref:System.Double.NaN> \(数学的に定義された数値ではない\)。|  
|`Double`|`Double`|\> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 <xref:System.DivideByZeroException> 例外をキャッチした場合は、そのメンバーを例外の処理に利用できます。  たとえば、<xref:System.Exception.Message%2A> プロパティには例外のメッセージ テキストが格納されています。  詳細については、「[Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
## ビット シフト演算  
 ビット シフト演算は、ビット パターン上で算術シフトを実行します。  パターンは左側のオペランドに指定し、右側のオペランドにはパターンをシフトする位置の数を指定します。  パターンを右へシフトする場合は [\>\> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) を使い、左へシフトする場合は [\<\< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md) を使います。  
  
 左側のオペランドのデータ型は `SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong` である必要があります。  右側のオペランドのデータ型は `Integer` または `Integer` を拡張したデータ型であることが必要です。  
  
 数値のシフトは、循環的には行われません。つまり、一方の端からはみ出したビットが、もう一方の端に補われることはありません。  シフトによって空いたビット位置は、次のように設定されます。  
  
-   算術左シフトでは 0  
  
-   正の数の算術右シフトでは 0  
  
-   符号のないデータ型の算術右シフトでは 0 \(`Byte`、`UShort`、`UInteger`、`ULong`\)  
  
-   負の数 \(`SByte`、`Short`、`Integer`、または `Long`\) の算術右シフトでは 1  
  
 次の例は `Integer` 値を左シフトおよび右シフトします。  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/arithmetic-operators_8.vb)]  
  
 数値のシフトではオーバーフロー例外は発生しません。  
  
## ビット処理演算  
 `Not`、`Or`、`And`、`Xor` の各演算子は、論理演算子として機能する他に、数値に対して使用された場合はビットごとの算術演算子としても機能します。  詳細については、「[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)」の「ビット処理演算」を参照してください。  
  
## タイプ セーフ  
 オペランドは、通常同じ型である必要があります。  たとえば、`Integer` 型の変数を加算するときには、この変数を別の `Integer` 変数に加算し、結果も同じく `Integer` 型の変数に代入する必要があります。  
  
 コードをタイプ セーフに保つための 1 つの方法として、[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) を使用できます。  `Option Strict On` を設定すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は*タイプ セーフ*な変換を自動的に実行します。  たとえば、`Integer` 型の変数を `Double` 型の変数に加算し、その値を `Double` 型の変数に代入する場合は、`Integer` 値から `Double` 型への変換ではデータが失われる可能性がないため、演算は正常に処理されます。  一方、タイプ セーフではない変換の場合は、`Option Strict On` を設定してしているとコンパイラ エラーが発生します。  たとえば、`Integer`型 の変数を `Double` 型の変数に加算し、その値を `Integer` 型の変数に代入しようとすると、`Double` の変数を暗黙的に `Integer` 型に変換できないため、コンパイラ エラーが発生します。  
  
 一方、`Option Strict Off` を設定していると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は暗黙の縮小変換を許可します。ただし、これによって予測不可能なデータまたは精度の欠落が起こる可能性があります。  このため、実稼動用のコードを作成する際には、`Option Strict On` を設定することをお勧めします。  詳細については、「[Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## 参照  
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Bit Shift Operators](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)