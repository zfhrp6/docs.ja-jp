---
title: "Await Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Await"
helpviewer_keywords: 
  - "Await operator [Visual Basic]"
  - "Await [Visual Basic]"
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Await Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Await` 演算子は、非同期のメソッドまたはラムダ式のオペランドに適用されて、待機中のタスクが完了するまでメソッドの実行を中断します。  このタスクは、進行中の作業を表します。  
  
 `Await` を使用するメソッドには [Async](../../../visual-basic/language-reference/modifiers/async.md) 修飾子が必要です。  このようなメソッド \(`Async` 修飾子を使用して定義され、通常 1 つ以上の `Await` 式を含むメソッド\) を*非同期メソッド*と呼びます。  
  
> [!NOTE]
>  `Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。  非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 `Await` 演算子を適用するタスクは、通常、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847) \(<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601>\) を実装するメソッド呼び出しの戻り値です。  
  
 次のコードでは、<xref:System.Net.Http.HttpClient> メソッドの <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> が `getContentsTask` \(`Task(Of Byte())`\) を返します。  これにより、操作が完了したときに実際のバイト配列が生成されることが保証されます。  `Await` 演算子が `getContentsTask` に適用されているため、`getContentsTask` が完了するまで `SumPageSizesAsync` の実行が中断されます。  その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。  `getContentsTask` が終了すると、`Await` 式がバイト配列に評価されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  コード例全体については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  Microsoft Web サイトで[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) からサンプルをダウンロードできます。  この例は AsyncWalkthrough\_HttpClient プロジェクトにあります。  
  
 `Task(Of TResult)` を返すメソッド呼び出しの結果に `Await` が適用されている場合、`Await` 式の型は TResult になります。  `Task` を返すメソッド呼び出しの結果に `Await` が適用されている場合、`Await` 式は値を返しません。  この違いを次の例に示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `Await` 式またはステートメントは、自身が実行されているスレッドをブロックするのではなく、  非同期メソッドの残りの部分が待機中のタスクの継続として `Await` 式の後に登録されるようにします。  これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。  タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。  
  
 `Await` 式は、`Async` 修飾子で修飾されたすぐ外側のメソッドまたはラムダ式の本体でのみ使用できます。  *Await* という用語がキーワードとして機能するのはこのコンテキストだけです。  他の場所では、識別子として解釈されます。  非同期のメソッドまたはラムダ式に含まれるクエリ式、[Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) ステートメントの `catch` ブロックまたは `finally` ブロック、`For` ループまたは `For Each` ループのループ コントロール変数式、および [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) ステートメントの本体で `Await` 式を使用することはできません。  
  
## 例外  
 大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。  返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。  `Await` 演算子は、これらのプロパティにアクセスします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`Await` 演算子はその例外を再スローします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドがキャンセルされた場合、`Await` 演算子は <xref:System.OperationCanceledException> を再スローします。  
  
 障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果になることがあります。  このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。  ただし、どの例外が再スローされるかを予測することはできません。  
  
 非同期メソッドのエラー処理の例については、「[Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
## 使用例  
 次に示す Windows フォームの例では、`WaitAsynchronouslyAsync` という非同期メソッドで `Await` が使用されています。  このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。  `WaitSynchronously` には `Await` 演算子がないため、定義で `Async` 修飾子が使用されていて、本体で <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> が呼び出されているにもかかわらず、同期的に実行されます。  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## 参照  
 [Async および Await を使用した非同期プログラミング](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [チュートリアル: Async と Await を使用した Web へのアクセス](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)