---
title: "If...Then...Else ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else ステートメント (Visual Basic)
式の値に応じてステートメント グループを条件付きで実行します。  
  
## <a name="syntax"></a>構文  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a>指定項目  
 `condition`  
 必須です。 式。 評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。  
  
 式の場合、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)、条件として扱われます式ではありません`True`、および`Else`ブロックは、実行されます。  
  
 `Then`  
 単一行の構文では必須複数行の構文でオプションです。  
  
 `statements`  
 省略可能です。 1 つまたは複数のステートメント次`If`しています.`Then`場合に実行されている`condition`に評価される`True`です。  
  
 `elseifcondition`  
 場合は必須`ElseIf`が存在します。 式。 評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。  
  
 `elseifstatements`  
 省略可能です。 1 つまたは複数のステートメント次`ElseIf`しています.`Then`場合に実行されている`elseifcondition`に評価される`True`です。  
  
 `elsestatements`  
 省略可能です。 ない場合に実行される 1 つまたは複数のステートメント`condition`または`elseifcondition`式に評価される`True`です。  
  
 `End If`  
 終了、`If`しています.`Then`...`Else`ブロックします。  
  
## <a name="remarks"></a>コメント  
  
## <a name="multiple-line-syntax"></a>複数行の構文  
 ときに、`If`しています.`Then`...`Else`ステートメントが見つかりましたが、`condition`をテストします。 場合`condition`は`True`、次のステートメント`Then`実行されます。 場合`condition`は`False`、各`ElseIf`ステートメント (存在する場合) が順番に評価します。 ときに、`True``elseifcondition`が見つかると、すぐに、関連付けられている次のステートメント`ElseIf`実行されます。 ない場合は`elseifcondition`に評価`True`がある場合、またはなし`ElseIf`ステートメント、次のステートメント`Else`実行されます。 次のステートメントを実行した後`Then`、 `ElseIf`、または`Else`、ステートメントに次の実行が続行`End If`です。  
  
 `ElseIf`と`Else`句は、どちらも省略可能です。 多くとして持つことができます`ElseIf`で必要なときと句、`If`しています.`Then`...`Else`ステートメントがない`ElseIf`句の後に、`Else`句。 `If`...`Then`...`Else`ステートメントは互いに入れ子にすることができます。  
  
 複数行の構文では、`If`ステートメントは、最初の行で唯一のステートメントである必要があります。 `ElseIf`、 `Else`、および`End If`ステートメントの前の行ラベルにのみです。 `If`しています.`Then`...`Else`ブロックがで終了する必要があります、`End If`ステートメントです。  
  
> [!TIP]
>  [を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)をいくつかの値を持つ 1 つの式を評価する際に役に立つ場合があります。  
  
## <a name="single-line-syntax"></a>単一行の構文  
 Short、単純なテストの単一行構文を使用することができます。 ただし、複数行の構文詳細の構造と柔軟性を提供され、読み取り、保守、およびデバッグする方が簡単です。  
  
 次のようにどのような`Then`キーワードが単一行、ステートメントがあるかどうかを調べて確認`If`です。 後にコメント以外の何かが表示された場合`Then`、同じ行には、ステートメントは単一行として扱われます`If`ステートメントです。 場合`Then`が存在しない場合は、複数行の開始をする必要があります`If`しています.`Then`...`Else`.  
  
 単一行の構文では、複数のステートメントの結果として実行することが、`If`しています.`Then`意思決定します。 すべてのステートメントでは、同じ行にある必要があり、コロンで区切っています。  
  
## <a name="example"></a>例  
 次の例の複数行の構文の使用方法を示しています、`If`しています.`Then`...`Else`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例を含む入れ子になった`If`しています.`Then`...`Else`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、単一行の構文の使用を示します。  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [条件判断構造](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)
