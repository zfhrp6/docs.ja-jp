---
title: "async (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8734f639e45f12ddd987a1c34e7f3ac38aa7d73f
ms.lasthandoff: 03/13/2017

---
# <a name="async-c-reference"></a>async (C# リファレンス)
`async` 修飾子を使用して、メソッド、[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)、または[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)が非同期であることを指定します。 この修飾子が使用されているメソッドまたは式を、非同期メソッドと呼びます。  
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 非同期プログラミングに慣れていない場合、または、非同期メソッドで `await` キーワードを使って、実行時間が長くなる可能性のある処理を、呼び出し元のスレッドをブロックすることなく実行する方法を理解していない場合は、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」の概要をご覧ください。  
  
```  
string contents = await contentsTask;  
```  
  
 メソッドは、最初の `await` 式に到達するまで同期的に実行されますが、この時点で、待機していたタスクが完了するまで中断されます。 次のセクションの例で示すように、その間はメソッドの呼び出し元に制御が戻ります。  
  
 `async` キーワードで修飾されているメソッドに `await` 式またはステートメントが含まれていない場合、メソッドは同期的に実行されます。 `await` が含まれていない非同期メソッドが存在する場合は、その状態がエラーを示す可能性があるため、コンパイラによって警告が通知されます。 「[コンパイラの警告 (レベル 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md)」をご覧ください。  
  
 `async` は、メソッド、ラムダ式、または匿名メソッドを修飾する場合にのみキーワードとなるため、コンテキスト キーワードです。 それ以外の場合は、識別子として解釈されます。  
  
## <a name="example"></a>例  
 次の例は、非同期のイベント ハンドラー `StartButton_Click` と非同期メソッド `ExampleMethodAsync` との間の制御構造および制御フローを示しています。 非同期メソッドの結果は、ダウンロードされた web サイトの長さです。 このコードは、[!INCLUDE[vs_dev12](../../../csharp/getting-started/includes/vs_dev12_md.md)] で Windows Presentation Foundation (WPF) アプリまたは Windows ストア アプリを作成する場合に適しています。アプリの設定に関するコード内のコメントを参照してください。  
  
```csharp  
// You can run this code in Visual Studio 2013 as a WPF app or a Windows Store app.  
// You need a button (StartButton) and a textbox (ResultsTextBox).  
// Remember to set the names and handler so that you have something like this:  
// <Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
//         Click="StartButton_Click" Name="StartButton"/>  
// <TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
//          Text="TextBox" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
  
// To run the code as a WPF app:  
//    paste this code into the MainWindow class in MainWindow.xaml.cs,  
//    add a reference to System.Net.Http, and  
//    add a using directive for System.Net.Http.  
  
// To run the code as a Windows Store app:  
//    paste this code into the MainPage class in MainPage.xaml.cs, and  
//    add using directives for System.Net.Http and System.Threading.Tasks.  
  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ExampleMethodAsync returns a Task<int>, which means that the method  
    // eventually produces an int result. However, ExampleMethodAsync returns  
    // the Task<int> value as soon as it reaches an await.  
    ResultsTextBox.Text += "\n";  
    try  
    {  
        int length = await ExampleMethodAsync();  
        // Note that you could put "await ExampleMethodAsync()" in the next line where  
        // "length" is, but due to when '+=' fetches the value of ResultsTextBox, you  
        // would not see the global side effect of ExampleMethodAsync setting the text.  
        ResultsTextBox.Text += String.Format("Length: {0}\n", length);  
    }  
    catch (Exception)  
    {  
        // Process the exception if one occurs.  
    }  
}  
  
public async Task<int> ExampleMethodAsync()  
{  
    var httpClient = new HttpClient();  
    int exampleInt = (await httpClient.GetStringAsync("http://msdn.microsoft.com")).Length;  
    ResultsTextBox.Text += "Preparing to finish ExampleMethodAsync.\n";  
    // After the following return statement, any method that's awaiting  
    // ExampleMethodAsync (in this case, StartButton_Click) can get the   
    // integer result.  
    return exampleInt;  
}  
// Output:  
// Preparing to finish ExampleMethodAsync.  
// Length: 53292  
  
```  
  
> [!IMPORTANT]
>  タスクの詳細、およびタスクを待機している間に実行されるコードの詳細については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」をご覧ください。 同様の要素を使用する WPF 例の完全版については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。 チュートリアル コードは、[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkId=255191)のページからダウンロードできます。  
  
## <a name="return-types"></a>戻り値の型  
 非同期メソッドの戻り値の型としては、<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、または [void](../../../csharp/language-reference/keywords/void.md) を指定できます。 メソッドで [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターを宣言することはできませんが、これらのパラメーターを持つメソッドを呼び出すことはできます。  
  
 メソッドの [return](../../../csharp/language-reference/keywords/return.md) ステートメントで `TResult` 型のオペランドを指定している場合、非同期メソッドの戻り値の型として `Task<TResult>` を指定します。 メソッドの完了時に意味のある値を返さない場合は、`Task` を使用します。 これにより、メソッドの呼び出しでは `Task` が返されますが、`Task` の完了時に、`await` を待機している `Task` 式はすべて、`void` に評価されます。  
  
 戻り値の型 `void` は主として、戻り値の型が必要なイベント ハンドラーの定義に使用されます。 `void` を返す非同期メソッドの呼び出し元は、このメソッドを待機できず、このメソッドがスローする例外をキャッチできません。  
  
 使用例を含む詳細については、「[非同期の戻り値の型](../../../csharp/programming-guide/concepts/async/async-return-types.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [await](../../../csharp/language-reference/keywords/await.md)   
 [チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)
