---
title: "await (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "await_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "await [C#]"
  - "await キーワード [C#]"
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 36
---
# await (C# リファレンス)
`await` 演算子は、待機中のタスクが完了するまでメソッドの実行を中断するために、非同期メソッドのタスクに適用します。  このタスクは、進行中の作業を表します。  
  
 `await` を使用する非同期メソッドは、[async](../../../csharp/language-reference/keywords/async.md) キーワードによって変更する必要があります。  このようなメソッド \(`async` 修飾子を使用して定義され、通常 1 つ以上の `await` 式を含むメソッド\) を*非同期メソッド*と呼びます。  
  
> [!NOTE]
>  `async` キーワードおよび `await` キーワードは、Visual Studio 2012 で導入されました。  非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 `await` 演算子を適用するタスクは通常、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847) を実装するメソッド呼び出しの戻り値です。  この例では、型 <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> の値が含まれます。  
  
 次のコードでは、<xref:System.Net.Http.HttpClient> メソッドの <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> が `Task\<byte[]>` \(`getContentsTask`\) を返します。  これにより、タスクが完了したときに実際のバイト配列が生成されることが保証されます。  `await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。  その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。  `getContentsTask` が終了すると、`await` 式がバイト配列に評価されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  サンプルは、Microsoft Web サイトで[開発者コード サンプルのページ](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)からダウンロードできます。  この例は AsyncWalkthrough\_HttpClient プロジェクトにあります。  
  
 前の例で示したように、`await` を返すメソッド呼び出しの結果に `Task<TResult>` を適用する場合、`await` 式の型は TResult です。  `await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`await` 式の型は void になります。  この違いを次の例に示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `await` 式は、自身が実行されているスレッドをブロックするのではなく、  非同期メソッドの残りの部分が待機中のタスクの継続として登録されるようにします。  これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。  タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。  
  
 `await` 式は、`async` 修飾子で修飾されたすぐ外側のメソッド、ラムダ式、または匿名メソッドの本体でのみ使用できます。  *await* という用語がキーワードとして機能するのはこのコンテキストだけです。  他の場所では、識別子として解釈されます。  メソッド、ラムダ式、または匿名メソッド内では、`await` 式は、同期関数、クエリ式、[lock ステートメント](../../../csharp/language-reference/keywords/lock-statement.md)のブロック、または [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストの本体では使用できません。  
  
## 例外  
 大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。  返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。  `await` 演算子は、これらのプロパティにアクセスします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`await` 演算子はその例外を再スローします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドが取り消された場合、`await` 演算子は <xref:System.OperationCanceledException> を再スローします。  
  
 障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。  たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果になることがあります。  このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。  ただし、どの例外が再スローされるかを予測することはできません。  
  
 非同期メソッドのエラー処理の例については、「[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)」を参照してください。  
  
## 使用例  
 次に示す Windows フォームの例では、`await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。  このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。  `await` にはタスクに適用される `WaitSynchronously` 演算子がないため、定義で `async` 修飾子が使用されていて、本体で <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> が呼び出されているにもかかわらず、同期的に実行されます。  
  
```c#  
  
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
  
## 参照  
 [Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [チュートリアル: Async と Await を使用した Web へのアクセス](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [async](../../../csharp/language-reference/keywords/async.md)