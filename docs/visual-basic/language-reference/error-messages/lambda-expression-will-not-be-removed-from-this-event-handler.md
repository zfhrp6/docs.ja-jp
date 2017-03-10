---
title: "Lambda expression will not be removed from this event handler | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42326"
  - "vbc42326"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42326"
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Lambda expression will not be removed from this event handler
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ラムダ式はこのイベント ハンドラーから削除されません。ラムダ式を変数に割り当て、その変数を使用してイベントを追加および削除してください。  
  
 ラムダ式をイベント ハンドラーで使用した場合、意図した動作にならない場合があります。  コンパイラは、各ラムダ式の定義に対して、たとえそれが同一のものでも新しいメソッドを生成します。  したがって、次のコードでは `False` が表示されます。  
  
```vb#  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 ラムダ式をイベント ハンドラーで使用する場合、予期しない結果が発生する可能性があります。  次の例では、`AddHandler` によって追加されたラムダ式が `RemoveHandler` ステートメントによって削除されません。  
  
```vb#  
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
  
 既定では、このメッセージは警告です。  警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC42326  
  
### このエラーを解決するには  
  
-   警告を回避し、ラムダ式を削除するためには、次の式に示されているように、ラムダ式を変数に割り当て、その変数を `AddHandler` ステートメントと `RemoveHandler` ステートメントの両方で使用するようにします。  
  
    ```vb#  
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
  
## 参照  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)