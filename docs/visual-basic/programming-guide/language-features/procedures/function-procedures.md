---
title: Function プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655536"
---
# <a name="function-procedures-visual-basic"></a>Function プロシージャ (Visual Basic)
A`Function`プロシージャは、一連の Visual Basic ステートメントで囲まれた、`Function`と`End Function`ステートメントです。 `Function`手順がタスクを実行し、呼び出し元のコードにコントロールを返します。 コントロールが返されたときにも、呼び出し元のコードに値を返します。  
  
 プロシージャが呼び出されるたびに、そのステートメントの実行、以降の後に実行可能ファイルの最初のステートメントで、`Function`ステートメントと最初で終了するまで`End Function`、 `Exit Function`、または`Return`ステートメントが発生しました。  
  
 定義することができます、`Function`モジュール、クラスまたは構造体」の手順です。 `Public`どこからでも呼び出すことを意味する既定では、モジュール、クラス、またはそれを定義する構造体へのアクセス権を持つアプリケーションでします。  
  
 A`Function`プロシージャは、定数、変数、または式で、呼び出し元のコードに渡されるなどの引数を渡すことができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Function`手順のとおりです。  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *修飾子*アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。 詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
 各パラメーターを宣言すると、同様の操作を行う[Sub プロシージャ](./sub-procedures.md)です。  
  
### <a name="data-type"></a>データの種類  
 各`Function`手順では、データ型か、単にすべての変数です。 このデータ型がで指定された、`As`句、`Function`ステートメント、およびその呼び出し元のコードに関数が返す値のデータ型が決まります。 次の宣言の例では、この問題を説明します。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 詳細についてを参照してください「部分」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
## <a name="returning-values"></a>値を返す  
 値、`Function`プロシージャが呼び出し元のコードには、戻り値と呼ばれるを送信します。 プロシージャは、2 つの方法のいずれかでこの値を返します。  
  
-   使用して、`Return`を返し、戻り値を指定するステートメントを呼び出し元のプログラムをすぐに制御します。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   プロシージャの 1 つまたは複数のステートメントで独自の関数名に値を割り当てます。 までの呼び出し元のプログラムに制御を返さない、`Exit Function`または`End Function`ステートメントを実行します。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 関数名 に戻り値を割り当てることの利点は、コントロールを返さないプロシージャから検出するまで、`Exit Function`または`End Function`ステートメントです。 これにより、一時的な値を割り当てるし、必要に応じて後で調整することができます。  
  
 値を取得する方法の詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。 配列を取得する方法については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Function`名前と右側にある、式または代入ステートメントのいずれかの引数を含めることによってプロシージャです。 省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。  
  
 呼び出しの構文、`Function`手順のとおりです。  
  
 *左辺値*`=`*functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *関数は functionname* `[(` *argumentlist* `)] / 3) <=`*式* `) Then`  
  
 呼び出すと、`Function`手順がありません、戻り値を使用します。 そうしないと場合、は、関数のすべてのアクションが実行されますが、戻り値は無視されます。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 多くの場合、この方法で呼び出されます。  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`hypotenuse`です。  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [方法 : 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)  
 [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)  
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
