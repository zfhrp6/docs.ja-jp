---
title: ラムダ式はこのイベント ハンドラーから削除されません
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 69228bbb5f659a8e500e85dea1ef87cb43b0356e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590168"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>ラムダ式はこのイベント ハンドラーから削除されません
ラムダ式は、このイベント ハンドラーから削除されません。 変数をラムダ式を割り当てる、変数を使用して追加およびイベントを削除します。  
  
 イベント ハンドラーにラムダ式を使用している場合は、意図した動作が見えない可能性があります。 コンパイラでは、同一である場合でも、各ラムダ式の定義用の新しいメソッドが生成されます。 したがって、次のコードが表示されます`False`です。  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 イベント ハンドラーにラムダ式を使用している場合、予期しない結果が発生する可能性があります。 次の例では、ラムダ式の追加によって`AddHandler`では削除されませんが、`RemoveHandler`ステートメントです。  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 既定では、このメッセージは警告です。 警告を非表示または警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC42326  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   警告を回避し、ラムダ式を削除する、ラムダ式を変数に代入し、両方の変数を使用して、`AddHandler`と`RemoveHandler`ステートメント、次の例で示すようにします。  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
