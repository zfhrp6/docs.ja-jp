---
title: "Function プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 11baaa6985f0681aa9c67c4f2470fb9917db5b78
ms.lasthandoff: 03/13/2017

---
# <a name="function-procedures-visual-basic"></a>Function プロシージャ (Visual Basic)
A`Function`プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]で囲まれたステートメント、`Function`と`End Function`ステートメントです。 `Function`プロシージャは、タスクを実行し、呼び出し元のコードに制御を戻します。 制御を戻す場合も、呼び出し元のコードに値を返します。  
  
 プロシージャが呼び出されるたび、そのステートメントの実行後の最初の実行可能ステートメントから始まる、`Function`ステートメントおよび&1; つ目で終了するまで`End Function`、 `Exit Function`、または`Return`ステートメントが発生しました。  
  
 定義する、`Function`モジュール、クラスまたは構造体のプロシージャです。 `Public`どこからでも呼び出すことができますが意味を既定では、モジュール、クラス、または、定義された構造体へのアクセス権を持つアプリケーションでします。  
  
 A`Function`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数を渡すことができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Function`手順は、次のようにします。  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *修飾子*アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。 詳細については、次を参照してください。 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
 各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)します。  
  
### <a name="data-type"></a>データの種類  
 各`Function`手順では、データ型、単にすべての変数ではサポートされます。 このデータ型が指定された、`As`句、`Function`ステートメント、およびその呼び出し元のコードに、関数が返す値のデータ型を決定します。 次の宣言の例では、これを示しています。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 詳細については、「部分」を参照してください[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
## <a name="returning-values"></a>値を返す  
 値、`Function`プロシージャが呼び出し元のコードには、戻り値と呼ばれるを送信します。 プロシージャは、2 つの方法のいずれかでこの値を返します。  
  
-   使用して、`Return`を返します。 戻り値を指定するステートメントを呼び出し元のプログラムをすぐに制御します。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   プロシージャの&1; つまたは複数のステートメントで独自の関数名 に値を割り当てます。 まで呼び出し元のプログラムに制御が戻らない、`Exit Function`または`End Function`ステートメントを実行します。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 関数名 に戻り値を割り当てることの利点は、制御を返さないこと、手順からに到達するまで、`Exit Function`または`End Function`ステートメントです。 これにより、一時的な値を割り当てるし、必要に応じて後で調整することができます。  
  
 値を取得する方法の詳細については、次を参照してください。 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。 配列を取得する方法については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Function`名前と、代入ステートメントまたは式の右側にあるいずれかの引数を含めることによってプロシージャです。 省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数がない場合は、かっこを省略することができます。  
  
 呼び出しの構文、`Function`手順は、次のようにします。  
  
 *左辺値*`=`*functionname* `[(` *argumentlist*    `)]`  
  
 `If ((`*functionname* `[(` *argumentlist* `)] / 3) <=`*式*  `) Then`  
  
 呼び出すと、`Function`の手順がありません、戻り値を使用します。 そうしない場合は、関数のすべての動作が実行されますが、戻り値が無視されます。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>多くの場合、この方法で呼び出されます。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Function`プロシージャは、最も長い辺または他の&2; つの値を指定された直角三角形の斜辺を計算します。  
  
 [!code-vb[VbVbcnProcedures&#1;](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 次の例では、一般的な呼び出しを`hypotenuse`します。  
  
 [!code-vb[VbVbcnProcedures&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md)   
 [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)   
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
