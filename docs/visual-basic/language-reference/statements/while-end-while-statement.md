---
title: While...End While ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 9f46a6ec65faef4448bdd25e30a6cc0c605cd0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604732"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While ステートメント (Visual Basic)
指定された条件が限りは、一連のステートメントを実行`True`です。  
  
## <a name="syntax"></a>構文  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`condition`|必須。 `Boolean` 式。 場合`condition`は`Nothing`、Visual Basic として扱います`False`です。|  
|`statements`|任意。 1 つまたは複数のステートメント次`While`、たびに実行される`condition`は`True`します。|  
|`Continue While`|任意。 次のイテレーションに制御を転送、`While`ブロックします。|  
|`Exit While`|任意。 うちの制御を転送、`While`ブロックします。|  
|`End While`|必須。 `While` ブロックの定義を終了します。|  
  
## <a name="remarks"></a>コメント  
 使用して、`While...End While`条件が限り回数、不特定数のステートメントのセットを繰り返したいときに`True`です。 方がよい場合に、その条件をテストするか、結果の判定をより柔軟にテストする場合、[操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。 セット回数だけ、ステートメントを繰り返し使用する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は通常、ことをお勧めします。  
  
> [!NOTE]
>  `While`キーワードでも使用、[操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)と[Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)です。  
  
 場合`condition`は`True`、すべての`statements`まで実行、`End While`ステートメントが見つかりました。 制御を返します、`While`ステートメント、および`condition`が再度チェックします。 場合`condition`まだ`True`プロセスが繰り返されます。 `False`、これに続くステートメントにパスを制御、`End While`ステートメントです。  
  
 `While`ステートメントは常には、ループを開始する前に、条件をチェックします。 条件がループが継続`True`です。 場合`condition`は`False`一度も実行しない、ループを最初に入力したときにします。  
  
 `condition`が 2 つの値の比較からの結果に評価される任意の式は、通常、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。 この式は、数値型に変換されているなどの別のデータ型の値を含めることができます`Boolean`です。  
  
 入れ子にすることができます`While`別内で 1 つのループを配置することでループします。 さまざまな種類の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。  
  
## <a name="exit-while"></a>中に終了  
 [終了中に](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する別の方法を提供できます、`While`ループします。 `Exit While` すぐに続くステートメントに制御を転送、`End While`ステートメントです。  
  
 通常使用`Exit While`いくつかの条件が評価された後 (たとえば、`If...Then...Else`構造) です。 不要な値が間違っているか、終了要求など、繰り返し処理を続行不可能になったりする条件を検出した場合、ループを終了する可能性があります。 使用することができます`Exit While`原因となる条件をテストするとき、*無限ループ*、これは、非常に大規模なまたは無限も可能回数だけ実行できるループします。 使用してできます`Exit While`ループをエスケープするためにします。  
  
 任意の数を配置する`Exit While`内の任意の場所のステートメント、`While`ループします。  
  
 使用すると内で入れ子になった`While`ループ、`Exit While`最も内側のループ外と入れ子の上位のレベルに制御を転送します。  
  
 `Continue While`ステートメントはすぐに、ループの次のイテレーションに制御を移します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)です。  
  
## <a name="example"></a>例  
 次の例では、ループ内のステートメントするまで引き続き実行、`index`変数が 10 より大きくします。  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、使用、`Continue While`と`Exit While`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、テキスト ファイルのすべての行を読み取ります。 <xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開きを返します、<xref:System.IO.StreamReader>文字を読み取る。 `While`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`ファイルに追加の文字が含まれるかどうかを判断します。  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)
