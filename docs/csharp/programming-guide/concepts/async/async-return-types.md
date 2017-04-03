---
title: "非同期の戻り値の型 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c1bab99fc1139f03e5f754cfecaee392b947171
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-c"></a>非同期の戻り値の型 (C#)
非同期メソッドの戻り値には、<xref:System.Threading.Tasks.Task%601> 型、<xref:System.Threading.Tasks.Task> 型、void 型の 3 つの型があります。 Visual Basic では、void の戻り値の型は [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) プロシージャとして作成されます。 非同期メソッドの詳細については、「[Async および Await を使用した非同期プログラミング (C#)](../../../../csharp/programming-guide/concepts/async/index.md)」を参照してください。  
  
 それぞれの戻り値の型は、次のセクションの 1 つで確認でき、トピックの最後で 3 種類のすべてを使用する例を参照できます。  
  
> [!NOTE]
>  この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。  
  
##  <a name="BKMK_TaskTReturnType"></a>Task(T) 型  
 `TResult` 型のオペランドを持つ [return](../../../../csharp/language-reference/keywords/return.md) (C#) ステートメントを含む非同期メソッドでは、戻り値の型に <xref:System.Threading.Tasks.Task%601> を使用します。  
  
 次の例では、`TaskOfT_MethodAsync` 非同期メソッドには整数を返す return ステートメントが含まれます。 そのため、メソッド宣言では、戻り値の型を `Task<int>` と指定する必要があります。  
  
```cs  
// TASK<T> EXAMPLE  
async Task<int> TaskOfT_MethodAsync()  
{  
    // The body of the method is expected to contain an awaited asynchronous  
    // call.  
    // Task.FromResult is a placeholder for actual work that returns a string.  
    var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
    // The method then can process the result in some way.  
    int leisureHours;  
    if (today.First() == 'S')  
        leisureHours = 16;  
    else  
        leisureHours = 5;  
  
    // Because the return statement specifies an operand of type int, the  
    // method must have a return type of Task<int>.  
    return leisureHours;  
}  
```  
  
 `TaskOfT_MethodAsync` が await 式の中から呼び出されると、await 式は `leisureHours` から返されるタスクに格納されている整数値 (`TaskOfT_MethodAsync` の値) を取得します。 await 式の詳細については、「[await](../../../../csharp/language-reference/keywords/await.md)」を参照してください。  
  
 次のコードは、`TaskOfT_MethodAsync` メソッドを呼び出して待機します。 結果は `result1` 変数に割り当てられます。  
  
```cs  
// Call and await the Task<T>-returning async method in the same statement.  
int result1 = await TaskOfT_MethodAsync();  
```  
  
 次のコードに示すように、`TaskOfT_MethodAsync` の呼び出しと、`await` の適用を分離すると、この仕組みをよく理解できます。 メソッドの宣言から予想されるように、直ちに待機しない `TaskOfT_MethodAsync` メソッドの呼び出しは、`Task<int>` を返します。 タスクは、この例の `integerTask` 変数に割り当てられます。 `integerTask` は <xref:System.Threading.Tasks.Task%601> であるため、`TResult` 型の <xref:System.Threading.Tasks.Task%601.Result> プロパティが含まれています。 この場合、TResult が整数型を表します。 `await` が `integerTask` に適用されると、`integerTask` の <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティの内容が await 式の評価となります。 この値は `result2` 変数に割り当てられます。  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは Blocking プロパティです。 タスクが終了する前にアクセスしようとすると、現在アクティブなスレッドは、タスクが完了して値が使用可能になるまで、ブロックされます。 多くの場合、プロパティに直接アクセスする代わりに、`await` を使用して値にアクセスする必要があります。  
  
```cs  
// Call and await in separate statements.  
Task<int> integerTask = TaskOfT_MethodAsync();  
  
// You can do other work that does not rely on integerTask before awaiting.  
textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
int result2 = await integerTask;  
```  
  
 次のコードの表示ステートメントは、`result1` 変数、`result2` 変数、および `Result` プロパティの値が同じであることを確認します。 `Result` プロパティは Blocking プロパティであり、タスクが待機される前にアクセスしないように注意してください。  
  
```cs  
// Display the values of the result1 variable, the result2 variable, and  
// the integerTask.Result property.  
textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
```  
  
##  <a name="BKMK_TaskReturnType"></a>Task 型  
 return ステートメントを含まない非同期メソッド、またはオペランドを返さない return ステートメントを含む非同期メソッドでは、通常は戻り値の型に <xref:System.Threading.Tasks.Task> を指定します。 そのようなメソッドは、同期的に実行するように作成されている場合に void を返すメソッドです。 非同期メソッドに戻り値の型 `Task` を使用した場合、呼び出し元のメソッドは await 演算子を使って、呼び出された async のメソッドが終了するまで、呼び出し元の完了を中断します。  
  
 次の例では、非同期メソッド `Task_MethodAsync` には、return ステートメントが含まれていません。 したがって、`Task` を待機させるメソッドに、戻り値の型 `Task_MethodAsync` を指定します。 `Task` 型の定義は、戻り値を格納する `Result` プロパティを含みません。  
  
```cs  
// TASK EXAMPLE  
async Task Task_MethodAsync()  
{  
    // The body of an async method is expected to contain an awaited   
    // asynchronous call.  
    // Task.Delay is a placeholder for actual work.  
    await Task.Delay(2000);  
    // Task.Delay delays the following line by two seconds.  
    textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
    // This method has no return statement, so its return type is Task.    
}  
```  
  
 `Task_MethodAsync` は、void を返す同期メソッドを呼び出す場合と同様に、await 式でなく、await ステートメントを使用して呼び出され、待機します。 この場合、await 演算子の適用によって値は生成されません。  
  
 次のコードは、`Task_MethodAsync` メソッドを呼び出して待機します。  
  
```cs  
// Call and await the Task-returning async method in the same statement.  
await Task_MethodAsync();  
```  
  
 前の <xref:System.Threading.Tasks.Task%601> の例のように、次のコードに示すとおり、`Task_MethodAsync` の呼び出しを await 演算子の適用と分離することができます。 ただし `Task` は `Result` プロパティを持たないこと、また await 演算子が `Task` に適用されるときに値は生成されないことに注意します。  
  
 次のコードは `Task_MethodAsync` の呼び出しを `Task_MethodAsync` が返すタスクの待機から分離します。  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a> Void 型  
 戻り値の型に void を主に使用するのは、void 型の戻り値を必要とするイベント ハンドラーです。 void である戻り値は、void を返すメソッドを上書きするためにも使われます。または「ファイア アンド フォーゲット (撃ち放し)」と分類されるアクティビティを実行するメソッドに対して使われます。 ただし、void を返す非同期メソッドを待機することはできないため、できる限り `Task` を返す必要があります。 このようなメソッドの呼び出し元は、呼び出した非同期メソッドが完了するのを待たずに、完了まで継続できる必要があります。また呼び出し元は、非同期メソッドが生成する値または例外とは無関係である必要があります。  
  
 void を返す非同期メソッドの呼び出し元は、メソッドがスローする例外をキャッチすることはできません。そのようなハンドルされない例外によって、アプリケーションが失敗する可能性が高くなります。 <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返す非同期メソッドで例外が発生すると、例外は返されたタスクに格納され、タスクが待機するときに再スローされます。 したがって、例外を生成する可能性がある非同期メソッドについては、戻り値の型が <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> であること、またメソッドの呼び出しが待機することを確認します。  
  
 非同期のメソッドで例外をキャッチする方法の詳細については、「[try-catch](../../../../csharp/language-reference/keywords/try-catch.md)」を参照してください。  
  
 次のコードは非同期のイベント ハンドラーを定義します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a>コード例全体  
 次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。  
  
 このプロジェクトを実行するには、次の手順を実行します。  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **[インストール済み]**、**[テンプレート]** カテゴリ、[Visual C#]、**[Windows]** の順にクリックします。 プロジェクトの種類の一覧から **[WPF アプリケーション]** をクリックします。  
  
4.  プロジェクトの名前として「`AsyncReturnTypes`」と入力し、**[OK]** をクリックします。  
  
     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。  
  
5.  Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。  
  
     タブが表示されない場合は、**ソリューション エクスプローラー**で MainWindow.xaml のショートカット メニューを開き、**[開く]** をクリックします。  
  
6.  MainWindow.xaml の **[XAML]** ウィンドウで、コードを次のコードに置き換えます。  
  
    ```cs  
    <Window x:Class="AsyncReturnTypes.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     テキスト ボックスとボタンを含むシンプルなウィンドウが、MainWindow.xaml の **[デザイン]** ウィンドウに表示されます。  
  
7.  **ソリューション エクスプローラー**で MainWindow.xaml.cs のショートカット メニューを開き、**[コードの表示]** を選択します。  
  
8.  MainWindow.xaml.cs のコードを次のコードに置き換えます。  
  
    ```cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    namespace AsyncReturnTypes  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            // VOID EXAMPLE  
            private async void button1_Click(object sender, RoutedEventArgs e)  
            {  
                textBox1.Clear();  
  
                // Start the process and await its completion. DriverAsync is a   
                // Task-returning async method.  
                await DriverAsync();  
  
                // Say goodbye.  
                textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
            }  
  
            async Task DriverAsync()  
            {  
                // Task<T>   
                // Call and await the Task<T>-returning async method in the same statement.  
                int result1 = await TaskOfT_MethodAsync();  
  
                // Call and await in separate statements.  
                Task<int> integerTask = TaskOfT_MethodAsync();  
  
                // You can do other work that does not rely on integerTask before awaiting.  
                textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
                int result2 = await integerTask;  
  
                // Display the values of the result1 variable, the result2 variable, and  
                // the integerTask.Result property.  
                textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
                textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
                textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
  
                // Task  
                // Call and await the Task-returning async method in the same statement.  
                await Task_MethodAsync();  
  
                // Call and await in separate statements.  
                Task simpleTask = Task_MethodAsync();  
  
                // You can do other work that does not rely on simpleTask before awaiting.  
                textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
                await simpleTask;  
            }  
  
            // TASK<T> EXAMPLE  
            async Task<int> TaskOfT_MethodAsync()  
            {  
                // The body of the method is expected to contain an awaited asynchronous  
                // call.  
                // Task.FromResult is a placeholder for actual work that returns a string.  
                var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
                // The method then can process the result in some way.  
                int leisureHours;  
                if (today.First() == 'S')  
                    leisureHours = 16;  
                else  
                    leisureHours = 5;  
  
                // Because the return statement specifies an operand of type int, the  
                // method must have a return type of Task<int>.  
                return leisureHours;  
            }  
  
            // TASK EXAMPLE  
            async Task Task_MethodAsync()  
            {  
                // The body of an async method is expected to contain an awaited   
                // asynchronous call.  
                // Task.Delay is a placeholder for actual work.  
                await Task.Delay(2000);  
                // Task.Delay delays the following line by two seconds.  
                textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
                // This method has no return statement, so its return type is Task.    
            }  
        }  
    }  
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
 <xref:System.Threading.Tasks.Task.FromResult%2A>   
 [チュートリアル: Async と Await を使用した Web へのアクセス (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [非同期プログラムにおける制御フロー (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [async](../../../../csharp/language-reference/keywords/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)
