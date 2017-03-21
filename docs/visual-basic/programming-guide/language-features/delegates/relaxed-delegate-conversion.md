---
title: "デリゲート変換 (Visual Basic)、緩和 |Microsoft ドキュメント"
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
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c0160165d3df9755481b89570b4cd135b3a990a2
ms.lasthandoff: 03/13/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a>厳密でないデリゲート変換 (Visual Basic)
厳密でないデリゲート変換を使用すると、そのシグネチャが同一でない場合でも、デリゲートやハンドラーにサブルーチンや関数を割り当てることができます。 そのため、デリゲートへのバインディングは、メソッド呼び出しで既に認められているバインディングと一致になります。  
  
## <a name="parameters-and-return-type"></a>パラメーターと戻り値の型  
 正確に一致するシグネチャの代わりに厳密でない変換が必要です、次の条件が満たされているときに`Option Strict`に設定されている`On`:  
  
-   デリゲートの各パラメーターのデータ型から割り当てられている関数の対応するパラメーターのデータ型への拡大変換が存在する必要がありますか`Sub`します。 次の例では、デリゲート`Del1`1 つのパラメーター、`Integer`です。 パラメーター`m`で割り当てられているラムダ式がありますがから拡大変換が存在するデータ型`Integer`など`Long`または`Double`です。  
  
     [!code-vb[VbVbalrRelaxedDelegates&#1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates&#2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     縮小変換が許可される場合にのみ`Option Strict`に設定されている`Off`します。  
  
     [!code-vb[VbVbalrRelaxedDelegates&#8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   割り当てられている関数の戻り値の型から反対方向に拡大変換が存在する必要がありますか`Sub`デリゲートの戻り値の型にします。 次の例については、各割り当てられているラムダ式の本体を拡大変換後のデータ型に評価する必要があります`Integer`戻り値の型のため`del1`は`Integer`です。  
  
     [!code-vb[VbVbalrRelaxedDelegates&#3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 場合`Option Strict`に設定されている`Off`、双方向でが削除されて制限を拡大します。  
  
 [!code-vb[VbVbalrRelaxedDelegates&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>パラメーターの指定を省略すること  
 厳密でないデリゲートを使用して、割り当てられているメソッドのパラメーターの仕様を完全に省略することもします。  
  
 [!code-vb[VbVbalrRelaxedDelegates&#5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 いくつかのパラメーターを指定し、他のユーザーを省略できないに注意してください。  
  
 [!code-vb[VbVbalrRelaxedDelegates&#15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 パラメーターを省略する機能は、いくつかの複雑なパラメーターが関係している、イベント ハンドラーを定義するような状況で役立ちます。 いくつかのイベント ハンドラーの引数は使用されません。 代わりに、ハンドラーは、イベントが登録されているし、する引数を無視コントロールの状態を直接アクセスします。 厳密でないデリゲートを使用すると、ときに何のあいまいさの結果は、このような宣言の引数を省略することができます。 次の例では、完全に指定したメソッドで`OnClick`として書き直すことが`RelaxedOnClick`です。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 例  
 ラムダ式は、表示する型の関係を簡単に、前の例で使用されます。 ただし、同じリラクゼーションは許可されますを使用するデリゲートの割り当ての`AddressOf`、 `Handles`、または`AddHandler`です。  
  
 次の例では、機能`f1`、 `f2`、 `f3`、および`f4`に割り当てられるすべて`Del1`です。  
  
 [!code-vb[VbVbalrRelaxedDelegates&#1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates&#7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates&#9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 次の例は、有効な場合にのみ`Option Strict`に設定されている`Off`します。  
  
 [!code-vb[VbVbalrRelaxedDelegates&#14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>関数の戻り値を削除します。  
 厳密でないデリゲート変換を使用すると、機能を割り当てる、`Sub`デリゲート、事実上、関数の戻り値を無視します。 ただし、割り当てることはできません、`Sub`を関数デリゲート。 次の例では、関数のアドレスで`doubler`に割り当てられている`Sub`委任`Del3`します。  
  
 [!code-vb[VbVbalrRelaxedDelegates&#10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates&#11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
