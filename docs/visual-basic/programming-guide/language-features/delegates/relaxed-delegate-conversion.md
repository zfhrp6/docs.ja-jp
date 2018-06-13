---
title: 厳密でないデリゲート変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: c4a41bf74716a6ea7d3c1139651834acccf27657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650830"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>厳密でないデリゲート変換 (Visual Basic)
厳密でないデリゲート変換を使用すると、サブと関数は、それぞれの署名が同一ではない場合でも、ハンドラーまたはデリゲートを割り当てることができます。 そのため、デリゲートへのバインディングは、メソッドの呼び出しを既に許可されているバインディングで一貫性のあるになります。  
  
## <a name="parameters-and-return-type"></a>パラメーターと戻り値の型  
 正確なシグネチャの一致の代わりに厳密でない変換が必要です、次の条件が満たされているときに`Option Strict`に設定されている`On`:  
  
-   各デリゲート パラメーターのデータ型から、対応する関数のパラメーター、割り当て済みのデータ型への拡大変換が存在する必要がありますまたは`Sub`です。 次の例では、デリゲート`Del1`1 つのパラメーターを持ち、`Integer`です。 パラメーター`m`式に割り当てられているラムダからの拡大変換がある対象のデータ型である必要があります`Integer`など`Long`または`Double`です。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     縮小変換が許可される場合にのみ`Option Strict`に設定されている`Off`です。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   割り当てられている関数の戻り値の型から反対方向に拡大変換が存在する必要がありますまたは`Sub`デリゲートの戻り値の型にします。 次の例では、各割り当てられているラムダ式の本体必要がありますを拡大するデータ型に評価される`Integer`戻り値の型のため`del1`は`Integer`します。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 場合`Option Strict`に設定されている`Off`では、双方向でが削除されて制限を拡大します。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>パラメーターの仕様を省略すること  
 厳密でないデリゲートでは、割り当てられているメソッドのパラメーターの仕様を完全に省略することができます。  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 いくつかのパラメーターを指定およびその他を省略できませんに注意してください。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 パラメーターを省略する機能は、いくつかの複雑なパラメーターが含まれて、イベント ハンドラーを定義するなどの状況で役立ちます。 一部のイベント ハンドラーの引数は使用されません。 代わりに、ハンドラーをイベントが登録し、その引数を無視コントロールの状態に直接アクセスします。 厳密でないデリゲートを使用するときに何の結果もあいまいさは、このような宣言の引数を省略できます。 次の例では、完全に指定されたメソッドで`OnClick`として書き直すことができます`RelaxedOnClick`です。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 例  
 ラムダ式は、型の関係を簡単に参照して、前の例で使用されます。 ただし、同じリラクゼーションを使用するデリゲートの割り当て用に許可されて`AddressOf`、 `Handles`、または`AddHandler`です。  
  
 次の例では、次のように機能します。 `f1`、 `f2`、 `f3`、および`f4`すべてに代入できます`Del1`です。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 次の例は、有効な場合にのみ`Option Strict`に設定されている`Off`です。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>関数の戻り値を削除します。  
 厳密でないデリゲート変換は、機能を割り当てることができます、`Sub`デリゲート、効果的に関数の戻り値は無視されます。 ただし、割り当てることはできません、`Sub`を関数デリゲート。 次の例では、関数のアドレスで`doubler`に割り当てられている`Sub`委任`Del3`です。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
