---
title: Visual Basic における算術演算子
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cef1e3610d885a0f3a2bae718641f7b8ca1062dc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic における算術演算子
算術演算子は、多くのリテラル、変数、その他の式、関数とプロパティの呼び出し、および定数で表される数値の計算を含む一般的な算術演算の実行に使用されます。 オペランドのビットごとのレベルで動作し、ビット パターンを左または右にシフトするビット シフト演算子は、算術演算子を含む分類もします。  
  
## <a name="arithmetic-operations"></a>算術演算  
 と共に式の中で 2 つの値を追加することができます、 [+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)、または減算を別の 1 つ、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)次の例で示すように、します。  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 否定にも使用されます、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)が、1 つだけのオペランドで次の例として示します。  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 乗算と除算の使用、 [* 演算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)と[/演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)、それぞれに、次の例に示します。  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 指数演算を使用して、 [^ 演算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)、次の例に示します。  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 整数の除算を使用して実行、 [\ 演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)です。 整数除算の商を返します、つまり、回数を表す整数除数できます除算小数部分を考慮せず被除数をします。 除数と被除数の両方が整数型にする必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、および`ULong`) この演算子。 他のすべての種類は、最初、整数型に変換する必要があります。 次の例では、整数の除算を示します。  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 使用して、剰余演算が実行される、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)です。 この演算子は、整数回数、被除数を除数で割った剰余を返します。 除数と被除数の両方が整数型の場合、返される値は整数です。 除数と被除数が浮動小数点型の場合、返される値は浮動小数点もです。 次の例では、この動作を示します。  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>0 による除算  
 0 による除算では、関連するデータ型に応じて異なる結果があります。 整数の区分で (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`) では、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]スロー、<xref:System.DivideByZeroException>例外。 除算の操作、`Decimal`または`Single`データ型、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]もスロー、<xref:System.DivideByZeroException>例外。  
  
 関係する浮動小数点の区分で、`Double`データ型、例外がスローされないと、結果は、クラスのメンバーを表す<xref:System.Double.NaN>、 <xref:System.Double.PositiveInfinity>、または<xref:System.Double.NegativeInfinity>被除数に応じて、します。 次の表に、さまざまな除算の結果、 `Double` 0 での値。  
  
|被除数のデータ型|除数のデータ型|被除数の値|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (非数学的に定義されている数)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 キャッチする場合、<xref:System.DivideByZeroException>例外、それを処理するためのメンバーを使用することができます。 たとえば、<xref:System.Exception.Message%2A>プロパティは、例外のメッセージ テキストを保持します。 詳しくは、「[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。  
  
## <a name="bit-shift-operations"></a>ビット シフト演算  
 ビット シフト操作は、ビット パターンに対して算術、シフトを実行します。 パターンは、左側のオペランドで含まれているし、右側のオペランドがパターンをシフトする位置の数を指定します。 右側に、パターンを移すことができます、 [>> 演算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)または左側に、 [<< 演算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)です。  
  
 パターンのオペランドのデータ型でなければなりません`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`です。 Shift キーを押し量オペランドのデータ型である必要があります`Integer`に拡大変換する必要がありますまたは`Integer`です。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。 シフトによって空いたビット位置は、次のように設定されます。  
  
-   算術左シフトの場合は 0  
  
-   正の数の算術右シフトの場合は 0  
  
-   署名されていないデータ型の算術右シフトの場合は 0 (`Byte`、 `UShort`、 `UInteger`、 `ULong`)  
  
-   負の数値の算術右シフトの 1 (`SByte`、 `Short`、 `Integer`、または`Long`)  
  
 次の例のシフト、`Integer`左と右の両方の値します。  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
## <a name="bitwise-operations"></a>ビット処理演算  
 論理演算子は、だけでなく`Not`、 `Or`、 `And`、および`Xor`も数値を使用する場合にビットごとの演算を実行します。 詳細については、「ビットごとの操作」を参照してください[論理および Visual Basic でビットごとの演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)です。  
  
## <a name="type-safety"></a>タイプ セーフ  
 オペランドは、同じ型の通常する必要があります。 などの追加を行う場合、`Integer`変数、する必要がありますに追加する別`Integer`して、変数は、型の変数に結果を割り当てる必要があります`Integer`もします。  
  
 適切なタイプ セーフなことを確認する方法の 1 つコーディングの推奨手順を使用するが、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)です。 設定した場合`Option Strict On`、Visual Basic が自動的に実行*タイプ セーフ*変換します。 追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Double`変数、処理は正常、ため、`Integer`値に変換できる`Double`データの損失なし。 タイプ セーフの変換では、その一方とコンパイラ エラーが発生する`Option Strict On`です。 追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Integer`変数で、コンパイラ エラーが発生、ため、`Double`変数を型に暗黙的に変換することはできません`Integer`です。  
  
 設定した場合`Option Strict Off`、ただし、Visual Basic では発生する暗黙的な縮小変換が、予期しないデータまたは精度の損失があります。 このため、使用をお勧めする`Option Strict On`実稼働コードを記述する場合。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [ビット シフト演算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Visual Basic における論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
