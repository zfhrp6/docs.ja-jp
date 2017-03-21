---
title: "非同期の戻り値の型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 703d3fc3f503017edf38521d77f9b15a92d0ebf3
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-visual-basic"></a>非同期の戻り値の型 (Visual Basic)
非同期のメソッドがある&3; つの戻り値の型: <xref:System.Threading.Tasks.Task%601>、 <xref:System.Threading.Tasks.Task>、および void</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> 。 Visual Basic では、void の戻り値の型として書き込まれる、 [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)プロシージャです。 非同期のメソッドの詳細については、次を参照してください。 [Async と Await (Visual Basic) を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。  
  
 それぞれの戻り値の型は、次のセクションの&1; つで確認でき、トピックの最後で&3; 種類のすべてを使用する例を参照できます。  
  
> [!NOTE]
>  例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。  
  
##  <a name="BKMK_TaskTReturnType"></a>戻り値の型を task (t)  
 <xref:System.Threading.Tasks.Task%601>戻り値の型を含む非同期メソッドに使用、[返す](../../../../visual-basic/language-reference/statements/return-statement.md)ステートメントのオペランドが型を持つ`TResult`</xref:System.Threading.Tasks.Task%601>。  
  
 次の例では、`TaskOfT_MethodAsync` 非同期メソッドには整数を返す return ステートメントが含まれます。 このため、メソッドの宣言での戻り値の型を指定する必要があります`Task(Of Integer)`します。  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 `TaskOfT_MethodAsync` が await 式の中から呼び出されると、await 式は `leisureHours` から返されるタスクに格納されている整数値 (`TaskOfT_MethodAsync` の値) を取得します。 詳細については、await 式を参照してください[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)します。  
  
 次のコードは、`TaskOfT_MethodAsync` メソッドを呼び出して待機します。 結果は `result1` 変数に割り当てられます。  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 呼び出しを分割することによりこのしくみをよく理解できます`TaskOfT_MethodAsync`のアプリケーションから`Await`次のコードを示します。 メソッドの呼び出しを`TaskOfT_MethodAsync`直ちに待機返しますではない、`Task(Of Integer)`メソッドの宣言から予想されるように、します。 タスクは、この例の `integerTask` 変数に割り当てられます。 `integerTask`は、<xref:System.Threading.Tasks.Task%601>が含まれている、<xref:System.Threading.Tasks.Task%601.Result>型のプロパティ`TResult`</xref:System.Threading.Tasks.Task%601.Result></xref:System.Threading.Tasks.Task%601>。 この場合、TResult が整数型を表します。 `Await`に適用される`integerTask`、await 式の評価の内容が、<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティの`integerTask`</xref:System.Threading.Tasks.Task%601.Result%2A>。 この値は `result2` 変数に割り当てられます。  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A>プロパティは blocking プロパティです</xref:System.Threading.Tasks.Task%601.Result%2A>。 タスクが終了する前にアクセスしようとすると、現在アクティブなスレッドは、タスクが完了して値が使用可能になるまで、ブロックされます。 ほとんどの場合を使用して値にアクセスする必要があります`Await`プロパティに直接アクセスする代わりにします。  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 次のコードの表示ステートメントは、`result1` 変数、`result2` 変数、および `Result` プロパティの値が同じであることを確認します。 `Result` プロパティは Blocking プロパティであり、タスクが待機される前にアクセスしないように注意してください。  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a>タスクの戻り値の型  
 Return ステートメントを含まないまたはオペランドに通常返さない return ステートメントを含む非同期メソッドがある<xref:System.Threading.Tasks.Task>。</xref:System.Threading.Tasks.Task>の戻り値の型 このようなメソッドになります[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)プロシージャが作成されている場合に同期的に実行します。 使用する場合、`Task`型を返す非同期メソッドの呼び出し方法を使用することができます、`Await`呼び出した非同期メソッドが終了するまで、呼び出し元の完了を中断する演算子です。  
  
 次の例では、非同期メソッド `Task_MethodAsync` には、return ステートメントが含まれていません。 したがって、`Task` を待機させるメソッドに、戻り値の型 `Task_MethodAsync` を指定します。 `Task` 型の定義は、戻り値を格納する `Result` プロパティを含みません。  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 `Task_MethodAsync` は、同期 `Sub` または void を返すメソッドを呼び出す場合と同様に、await 式でなく、await ステートメントを使って呼び出され、待機されます。 アプリケーション、`Await`演算子はこの場合、値を生成しません。  
  
 次のコードは、`Task_MethodAsync` メソッドを呼び出して待機します。  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 以前と同様に<xref:System.Threading.Tasks.Task%601>例では、呼び出しを分離することができます`Task_MethodAsync`のアプリケーションから、`Await`演算子は、次のコードに示すようにします</xref:System.Threading.Tasks.Task%601>。 ただし `Task` は `Result` プロパティを持たないこと、また await 演算子が `Task` に適用されるときに値は生成されないことに注意します。  
  
 次のコードは `Task_MethodAsync` の呼び出しを `Task_MethodAsync` が返すタスクの待機から分離します。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a>戻り値の型を無効にします。  
 主な用途`Sub`手順は、イベント ハンドラーの戻り値の型を (その他の言語に void 戻り値の型と呼ばれます) が存在しません。 void である戻り値は、void を返すメソッドを上書きするためにも使われます。または「ファイア アンド フォーゲット (撃ち放し)」と分類されるアクティビティを実行するメソッドに対して使われます。 ただし、void を返す非同期メソッドを待機することはできないため、できる限り `Task` を返す必要があります。 このようなメソッドの呼び出し元は、呼び出した非同期メソッドが完了するのを待たずに、完了まで継続できる必要があります。また呼び出し元は、非同期メソッドが生成する値または例外とは無関係である必要があります。  
  
 void を返す非同期メソッドの呼び出し元は、メソッドがスローする例外をキャッチすることはできません。そのようなハンドルされない例外によって、アプリケーションが失敗する可能性が高くなります。 返す非同期メソッドで例外が発生したかどうか、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>、例外が返されるタスクに格納され、タスクが待機するときに再度スローされます</xref:System.Threading.Tasks.Task%601></xref:System.Threading.Tasks.Task>。 そのため、例外を生成できる非同期のメソッドの戻り値の型があることを確認して行って<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>メソッドの呼び出しが待機している</xref:System.Threading.Tasks.Task%601></xref:System.Threading.Tasks.Task>。  
  
 非同期のメソッドで例外をキャッチする方法の詳細については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。  
  
 次のコードは非同期のイベント ハンドラーを定義します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a>コード例を全体します。  
 次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。  
  
 このプロジェクトを実行するには、次の手順を実行します。  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされている**、**テンプレート**カテゴリで、選択**Visual Basic**、にして**Windows**します。 選択**WPF アプリケーション**プロジェクトの種類の一覧からです。  
  
4.  入力`AsyncReturnTypes`として、プロジェクトの名前を選択し、 **ok**  ボタンをクリックします。  
  
     新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。  
  
5.  Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。  
  
     MainWindow.xaml のショートカット メニューを開き、タブが表示されていない場合は、**ソリューション エクスプ ローラー**、にして**開く**します。  
  
6.  **XAML** MainWindow.xaml のウィンドウは、次のコードで、コードを置き換えます。  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     テキスト ボックスとボタンを含む簡単なウィンドウに表示、**デザイン**MainWindow.xaml のウィンドウです。  
  
7.  **ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。  
  
8.  MainWindow.xaml.vb のコードを次のコードに置き換えます。  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。  
  
     次の出力が表示されます。  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Tasks.Task.FromResult%2A></xref:System.Threading.Tasks.Task.FromResult%2A>   
 [チュートリアル: Async を使用して Web へのアクセスと Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [(Visual Basic) の非同期プログラムにおける制御フロー](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [非同期](../../../../visual-basic/language-reference/modifiers/async.md)   
 [Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)
