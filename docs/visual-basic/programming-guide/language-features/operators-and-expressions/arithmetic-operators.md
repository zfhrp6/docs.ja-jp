---
title: "Visual Basic における算術演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators
- bit-shift operators
- zero, division by zero
- operators [Visual Basic], arithmetic
- division, by zero
- Visual Basic code, operators
- arithmetic operators, about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c724bf8b6794e71d49b32c7d3ce9e010f541f68f
ms.lasthandoff: 03/13/2017

---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic における算術演算子
算術演算子を使用して、リテラル、変数、その他の式、関数とプロパティの呼び出し、および定数で表される数値の計算に関連する一般的な算術演算の多くを実行できます。 算術演算子にも分類は、オペランドのビットごとのレベルで動作し、ビット パターンを左または右にシフトするビット シフト演算子です。  
  
## <a name="arithmetic-operations"></a>算術演算  
 と共に式の中で&2; つの値を追加することができます、 [+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)、または減算一方から他方に、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)、次の例で示すようにします。  
  
 [!code-vb[VbVbalrOperators #&57;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 否定を使用しても、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)が&1; つだけのオペランドでとして次の例を示します。  
  
 [!code-vb[VbVbalrOperators #&58;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 乗算と除算の使用、 [* 演算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)と[/演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)、それぞれに、次の例に示します。  
  
 [!code-vb[VbVbalrOperators #&59;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 指数演算を使用して、 [^ 演算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)、次の例に示します。  
  
 [!code-vb[VbVbalrOperators&#60;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 使用整数の除算が実行される、 [\ 演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)します。 整数除算の商を返します、つまり、回数の合計を表す整数除数できます除算被除数の残りの部分について十分に考慮せずにします。 除数と被除数の両方が整数型にする必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、および`ULong`) オペレーターのです。 他のすべての型は、整数型へ最初に変換する必要があります。 次の例では、整数の除算を示します。  
  
 [!code-vb[VbVbalrOperators&#61;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 使用して剰余演算を実行、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)します。 この演算子は、整数回数、被除数を除数で割った剰余を返します。 除数と被除数の両方が整数型の場合、返される値は整数です。 除数と被除数が浮動小数点型の場合、返される値が浮動小数点型もします。 次の例では、この動作を示します。  
  
 [!code-vb[VbVbalrOperators #&62;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators #&63;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>0 による除算  
 0 による除算には、関連するデータ型によって異なる結果があります。 In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</xref:System.DivideByZeroException> 除算の操作、`Decimal`または`Single`データ型、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]もスロー、<xref:System.DivideByZeroException>例外</xref:System.DivideByZeroException>。  
  
 浮動小数点の部署が関係する、`Double`データ型は、例外はスローされませんし、結果を表すクラスのメンバーは、 <xref:System.Double.NaN>、 <xref:System.Double.PositiveInfinity>、または<xref:System.Double.NegativeInfinity>被除数によって異なります</xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></xref:System.Double.NaN>。 次の表に、除算の結果、 `Double`&0; の値。  
  
|被除数のデータ型|除数のデータ型|被除数の値|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(数学的に定義された番号ではない)</xref:System.Double.NaN>|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity></xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity></xref:System.Double.NegativeInfinity>|  
  
 <xref:System.DivideByZeroException>例外、それを処理するためには、そのメンバーを使用して</xref:System.DivideByZeroException>をキャッチします。 たとえば、<xref:System.Exception.Message%2A>プロパティは例外のメッセージ テキストを保持します</xref:System.Exception.Message%2A>。 詳細については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。  
  
## <a name="bit-shift-operations"></a>ビット シフト演算  
 ビット シフト演算は、ビット パターン上で算術シフトを実行します。 パターンは、左側のオペランドで含まれているし、右側のオペランドがパターンをシフトする位置の数を指定します。 パターンをシフトすると、右側にすることができます、 [>> 演算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)を使用して、左、 [ <> </>](../../../../visual-basic/language-reference/operators/left-shift-operator.md)します。  
  
 パターンのオペランドのデータ型である必要があります`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`です。 Shift キーを押し量オペランドのデータ型である必要があります`Integer`に拡大変換する必要がありますか`Integer`します。  
  
 算術シフトは、循環ので、もう一方の end にシフトし、結果の&1; つ溢れたビットは行われません。 シフトによって空いたビット位置は、次のように設定されます。  
  
-   算術左シフトの場合は&0;  
  
-   正の数値の算術演算の右シフトで&0;  
  
-   署名されていないデータ型の算術右シフトでは&0; (`Byte`、 `UShort`、 `UInteger`、 `ULong`)  
  
-   負の数値の算術右シフトの場合は&1; (`SByte`、 `Short`、 `Integer`、または`Long`)  
  
 次の例戻して、`Integer`左側と右側の両方の値します。  
  
 [!code-vb[VbVbalrOperators #&64;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
## <a name="bitwise-operations"></a>ビット処理演算  
 論理演算子だけでなく`Not`、 `Or`、 `And`、および`Xor`も数値で使用する場合のビットごとの演算を実行します。 詳細については、ビットごと「操作」を参照してください[論理と Visual Basic ではビットごとの演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)します。  
  
## <a name="type-safety"></a>タイプ セーフ  
 オペランドは、同じ型の通常でする必要があります。 などの追加を行う場合、`Integer`変数に追加する別`Integer`して、変数は、型の変数に結果を割り当てる必要があります`Integer`もします。  
  
 適切なタイプ セーフのことを確認する方法の&1; つコーディングの推奨手順を使用するが、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)します。 設定した場合`Option Strict On`、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]が自動的に実行*タイプセーフ*変換します。 追加しようとする場合など、`Integer`変数を`Double`変数値を代入し、`Double`変数、操作は正常に続行、ため、`Integer`に値を変換できる`Double`データを失うことがなく。 型の安全でない変換では、その一方とコンパイラ エラーが発生する`Option Strict On`です。 追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Integer`変数、コンパイラ エラー結果、ため、`Double`変数を型に暗黙的に変換できません`Integer`します。  
  
 設定した場合`Option Strict Off`、ただし、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]予期しないデータまたは精度の損失で発生する可能性が発生する暗黙的な縮小変換を使用します。 このため、使用をお勧めする`Option Strict On`実稼働コードを記述する場合。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。  
  
## <a name="see-also"></a>関連項目  
 [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [ビット シフト演算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)   
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Visual Basic での論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
