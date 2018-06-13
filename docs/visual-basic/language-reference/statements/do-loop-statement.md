---
title: Do...Loop ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: e12cdc1ae405b877d4d27d1947c98dcb51938ba7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604940"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop ステートメント (Visual Basic)
ときにステートメント ブロックを繰り返します、`Boolean`条件が`True`、条件になるまで、または`True`です。  
  
## <a name="syntax"></a>構文  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`Do`|必須。 定義を開始、`Do`ループします。|  
|`While`|`Until` を使用しない場合に、必ず指定します。 までループを繰り返す`condition`は`False`します。|  
|`Until`|`While` を使用しない場合に、必ず指定します。 までループを繰り返す`condition`は`True`します。|  
|`condition`|任意。 `Boolean` 式。 場合`condition`は`Nothing`、Visual Basic として扱います`False`です。|  
|`statements`|任意。 1 つ以上のステートメント、または、まで繰り返される`condition`は`True`します。|  
|`Continue Do`|任意。 次のイテレーションに制御を転送、`Do`ループします。|  
|`Exit Do`|任意。 うちの制御を転送、`Do`ループします。|  
|`Loop`|必須。 定義を終了、`Do`ループします。|  
  
## <a name="remarks"></a>コメント  
 使用して、`Do...Loop`一連の条件が満たされるまで何度で不特定数のステートメントを繰り返し使用するときにします。 セット回数だけ、ステートメントを繰り返し使用する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は通常、ことをお勧めします。  
  
 いずれかを使用する`While`または`Until`を指定する`condition`、両方は使用しません。  
  
 テストすることができます`condition`先頭またはループの終了のいずれか 1 つだけの時間。 テストする場合は`condition`、ループの開始時 (で、`Do`ステートメント)、ループが 1 つでも時間が実行されません。 ループの最後にテストする場合 (で、`Loop`ステートメント)、ループは、少なくとも 1 つの時間を常に実行されます。  
  
 条件は、通常 2 つの値の比較から結果します、に評価される任意の式であることができます、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。 これには、数値型に変換されているなどの他のデータ型の値が含まれます`Boolean`です。  
  
 入れ子にすることができます`Do`別内で 1 つのループを記述することによってループします。 さまざまな種類の他の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。  
  
> [!NOTE]
>  `Do...Loop`構造体より高い柔軟性を提供する、[中.End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)ループを終了するかどうかを決定することができるためとき`condition`停止されている`True`最初になったときまたは`True`です。 テストすることもできます`condition`先頭またはループの終了のいずれか。  
  
## <a name="exit-do"></a>操作を終了します。  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する代替方法を提供できる、`Do…Loop`です。 `Exit Do` 続くステートメントに直ちに制御を移します、`Loop`ステートメントです。  
  
 `Exit Do` たとえば、いくつかの条件が評価された後は、よく使用、`If...Then...Else`構造体。 不要な値が間違っているか、終了要求など、繰り返し処理を続行不可能になったりする条件を検出した場合、ループを終了する可能性があります。 用途の 1 つ`Exit Do`を引き起こす可能性のある条件をテストするには、*無限ループ*、これは、大規模なまたは無限も可能回数だけ実行できるループします。 使用することができます`Exit Do`ループをエスケープするためにします。  
  
 任意の数を含めることができます`Exit Do`内の任意の場所のステートメント、`Do…Loop`です。  
  
 使用すると内で入れ子になった`Do`ループ、`Exit Do`最も内側のループ外と入れ子の上位のレベルに制御を転送します。  
  
## <a name="example"></a>例  
 次の例では、ループ内のステートメントするまで引き続き実行、`index`変数が 10 より大きくします。 `Until`句は、ループの最後にします。  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、`While`句の代わりに、`Until`句、および`condition`最後の代わりに、ループの開始時にテストします。  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、`condition`ループを停止するときに、`index`変数が 100 より大きい。 `If` 、ループ内のステートメントがただし、により、`Exit Do`インデックス変数が 10 よりも大きい場合に、ループを停止するステートメント。  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、テキスト ファイルのすべての行を読み取ります。 <xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開きを返します、<xref:System.IO.StreamReader>文字を読み取る。 `Do...Loop`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`を超える文字数があるかどうかを決定します。  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
