---
title: Exit ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 05a65dd84a00478f52c8cd7d8b46341644512718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605278"
---
# <a name="exit-statement-visual-basic"></a>Exit ステートメント (Visual Basic)
プロシージャまたはブロックを終了し、プロシージャ呼び出しまたはブロックの定義を次のステートメントに制御を直ちに転送します。  
  
## <a name="syntax"></a>構文  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>ステートメント  
 `Exit Do`  
 すぐに終了させる、`Do`ループが表示されます。 ステートメントに次の実行が続行、`Loop`ステートメントです。 `Exit Do` 内でのみ使用できます、`Do`ループします。 使用すると内で入れ子になった`Do`ループ、`Exit Do`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。  
  
 `Exit For`  
 すぐに終了させる、`For`ループが表示されます。 ステートメントに次の実行が続行、`Next`ステートメントです。 `Exit For` 内でのみ使用できます、`For`しています.`Next`または`For Each`しています.`Next`ループします。 使用すると内で入れ子になった`For`ループ、`Exit For`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。  
  
 `Exit Function`  
 すぐに終了させる、`Function`が表示される手順です。 呼び出したステートメントの次のステートメントと実行が継続、`Function`プロシージャです。 `Exit Function` 内でのみ使用できます、`Function`プロシージャです。  
  
 戻り値を指定するには前に、の行に関数名に値を割り当てることができます、`Exit Function`ステートメントです。 戻り値を代入し、1 つのステートメント内で、関数の終了、代わりに使用できます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。  
  
 `Exit Property`  
 すぐに終了させる、`Property`が表示される手順です。 呼び出したステートメントと実行が継続、`Property`手順、つまり、要求またはプロパティの値を設定するステートメントを使用します。 `Exit Property` プロパティの内部でのみ使用できます`Get`または`Set`プロシージャです。  
  
 戻り値を指定する、`Get`プロシージャ前に、の行に関数名に値を割り当てることができます、`Exit Property`ステートメントです。 戻り値および終了に割り当てる、 `Get` 1 つのステートメントでプロシージャを使用する、`Return`ステートメントです。  
  
 `Set`プロシージャ、`Exit Property`ステートメントは等価、`Return`ステートメントです。  
  
 `Exit Select`  
 すぐに終了させる、`Select Case`ブロックが表示されます。 ステートメントに次の実行が続行、`End Select`ステートメントです。 `Exit Select` 内でのみ使用できます、`Select Case`ステートメントです。  
  
 `Exit Sub`  
 すぐに終了させる、`Sub`が表示される手順です。 呼び出したステートメントの次のステートメントと実行が継続、`Sub`プロシージャです。 `Exit Sub` 内でのみ使用できます、`Sub`プロシージャです。  
  
 `Sub`プロシージャ、`Exit Sub`ステートメントは等価、`Return`ステートメントです。  
  
 `Exit Try`  
 すぐに終了させる、`Try`または`Catch`ブロックが表示されます。 実行が継続、 `Finally` 、1 つを使用する必要がある場合、またはステートメントに次のブロック、`End Try`ステートメントがそれ以外の場合。 `Exit Try` 内でのみ使用できます、`Try`または`Catch`ブロックといない内側、`Finally`ブロックします。  
  
 `Exit While`  
 すぐに終了させる、`While`ループが表示されます。 ステートメントに次の実行が続行、`End While`ステートメントです。 `Exit While` 内でのみ使用できます、`While`ループします。 使用すると内で入れ子になった`While`ループ、`Exit While`ループ ループの 1 つの入れ子になったレベルに制御を移します場所`Exit While`が発生します。  
  
## <a name="remarks"></a>コメント  
 混同しないでください`Exit`ステートメントと`End`ステートメントです。 `Exit` ステートメントの末尾を一切定義しません。  
  
## <a name="example"></a>例  
 次の例では、ループの条件は、ループを停止するときに、`index`変数が 100 より大きい。 `If` 、ループ内のステートメントがただし、により、`Exit Do`インデックス変数が 10 よりも大きい場合に、ループを停止するステートメント。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、戻り値を割り当てて、関数名に`myFunction`、しを使用して`Exit Function`関数から返される。  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)を戻り値を代入し、関数を終了します。  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Stop ステートメント](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
