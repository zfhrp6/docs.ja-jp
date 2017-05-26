---
title: "await (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 3656141c32a04e3a32a2992185f4c418c6915482
ms.contentlocale: ja-jp
ms.lasthandoff: 03/24/2017

---
# <a name="await-c-reference"></a>await (C# リファレンス)
`await` 演算子は、待機中のタスクが完了するまでメソッドの実行を中断するために、非同期メソッドのタスクに適用します。 このタスクは、進行中の作業を表します。  
  
 `await` が使われている非同期メソッドは、[async](../../../csharp/language-reference/keywords/async.md) キーワードによって変更する必要があります。 このようなメソッド (`async` 修飾子を使用して定義され、通常 1 つ以上の `await` 式を含むメソッド) を "*非同期メソッド*" と呼びます。  
  
> [!NOTE]
>  `async` キーワードおよび `await` キーワードは、Visual Studio 2012 で導入されました。 非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」をご覧ください。  
  
 `await` 演算子を適用するタスクは通常、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847)を実装するメソッド呼び出しの戻り値です。 たとえば、<xref:System.Threading.Tasks.Task> 型や <xref:System.Threading.Tasks.Task%601> 型の値です。  
  
 次のコードで、<xref:System.Net.Http.HttpClient> クラスの <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> メソッドは、`Task\<byte[]>` 型の `getContentsTask` を返します。 これにより、タスクが完了したときに実際のバイト配列が生成されることが保証されます。 `await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。 その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。 `getContentsTask` が終了すると、`await` 式がバイト配列に評価されます。  
  
```csharp  
private async Task SumPageSizesAsync()  
{  
    // To use the HttpClient type in desktop apps, you must include a using directive and add a   
    // reference for the System.Net.Http namespace.  
    HttpClient client = new HttpClient();  
    // . . .  
    Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
    byte[] urlContents = await getContentsTask;  
  
    // Equivalently, now that you see how it works, you can write the same thing in a single line.  
    //byte[] urlContents = await client.GetByteArrayAsync(url);  
    // . . .  
}  
```  
  
> [!IMPORTANT]
>  完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。 Microsoft Web サイトの[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)からサンプルをダウンロードできます。 この例は AsyncWalkthrough_HttpClient プロジェクトにあります。  
  
 前の例で示したように、`await` を返すメソッド呼び出しの結果に `Task<TResult>` を適用する場合、`await` 式の型は TResult です。 `await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`await` 式の型は void になります。 この違いを次の例に示します。  
  
```csharp  
// Keyword await used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// Keyword await used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  
```  
  
 `await` 式は、自身が実行されているスレッドをブロックするのではなく、 非同期メソッドの残りの部分が待機中のタスクの継続として登録されるようにします。 これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。 タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。  
  
 `await` 式は、`async` 修飾子で修飾されたすぐ外側のメソッド、ラムダ式、または匿名メソッドの本体でのみ使用できます。 *await* という用語がキーワードとして機能するのはこのコンテキストだけです。 他の場所では、識別子として解釈されます。 メソッド、ラムダ式、または匿名メソッド内では、`await` 式は、同期関数、クエリ式、[lock ステートメント](../../../csharp/language-reference/keywords/lock-statement.md)のブロック、または [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストの本体では使用できません。  
  
## <a name="exceptions"></a>例外  
 ほとんどの非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。 返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。 `await` 演算子は、これらのプロパティにアクセスします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`await` 演算子はその例外を再スローします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドが取り消された場合、`await` 演算子は <xref:System.OperationCanceledException> を再スローします。  
  
 障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。 たとえば、タスクが <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果である場合があります。 このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。 ただし、どの例外が再スローされるかを予測することはできません。  
  
 非同期メソッドのエラー処理の例については、「[try-catch](../../../csharp/language-reference/keywords/try-catch.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次に示す Windows フォームの例では、`await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。 このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。 `await` 演算子を適用しないと、`WaitSynchronously` は、定義で `async` 修飾子が使われていて、本体で <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> が呼び出されていても、同期的に実行されます。  
  
```csharp  
private async void button1_Click(object sender, EventArgs e)  
{  
    // Call the method that runs asynchronously.  
    string result = await WaitAsynchronouslyAsync();  
  
    // Call the method that runs synchronously.  
    //string result = await WaitSynchronously ();  
  
    // Display the result.  
    textBox1.Text += result;  
}  
  
// The following method runs asynchronously. The UI thread is not  
// blocked during the delay. You can move or resize the Form1 window   
// while Task.Delay is running.  
public async Task<string> WaitAsynchronouslyAsync()  
{  
    await Task.Delay(10000);  
    return "Finished";  
}  
  
// The following method runs synchronously, despite the use of async.  
// You cannot move or resize the Form1 window while Thread.Sleep  
// is running because the UI thread is blocked.  
public async Task<string> WaitSynchronously()  
{  
    // Add a using directive for System.Threading.  
    Thread.Sleep(10000);  
    return "Finished";  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)   
 [チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [async](../../../csharp/language-reference/keywords/async.md)

