---
title: "Await 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a>Await 演算子 (Visual Basic)
`Await` 演算子は、非同期のメソッドまたはラムダ式のオペランドに適用されて、待機中のタスクが完了するまでメソッドの実行を中断します。 このタスクは、進行中の作業を表します。  
  
 メソッドに`Await`は使用が必要、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子です。 このような定義されたメソッドを使用して、`Async`修飾子、および通常含まれる&1; つまたは複数`Await`式と呼ばれます、 *async メソッド*します。  
  
> [!NOTE]
>  `Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。 非同期のプログラミングの概要については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)します。  
  
 適用するタスクでは通常、`Await`演算子を実装するメソッドの呼び出しからの戻り値は、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847)、つまり、 <xref:System.Threading.Tasks.Task>、または<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 次のコードで、<xref:System.Net.Http.HttpClient>メソッド<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>返します`getContentsTask`、 `Task(Of Byte())`</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient> 。 タスクにより、操作が完了したときに実際のバイト配列が生成されることが保証されます。 `Await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。 その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。 `getContentsTask` が終了すると、`Await` 式がバイト配列に評価されます。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
> [!IMPORTANT]
>  完全な例を参照してください。[チュートリアル: を使用して Async と Await による Web にアクセスする](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。 サンプルをダウンロードすることも[デベロッパー サンプル コード集](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)Microsoft web サイトです。 この例は AsyncWalkthrough_HttpClient プロジェクトにあります。  
  
 `Await` を返すメソッド呼び出しの結果に `Task(Of TResult)` が適用されている場合、`Await` 式の型は TResult になります。 `Await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`Await` 式は値を返しません。 この違いを次の例に示します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `Await` 式またはステートメントは、自身が実行されているスレッドをブロックするのではなく、 非同期メソッドの残りの部分が待機中のタスクの継続として `Await` 式の後に登録されるようにします。 これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。 タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。  
  
 `Await` 式は、`Async` 修飾子で修飾されたすぐ外側のメソッドまたはラムダ式の本体でのみ使用できます。 用語*Await*そのコンテキストでのみキーワードとして機能します。 他の場所では、識別子として解釈されます。 非同期のメソッドまたはラムダ式に含まれる、`Await`式は、クエリ式で発生することはできません、`catch`または`finally`のブロック、[しようとしています.キャッチしてください.最後に](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)のループ コントロール変数式、ステートメント、`For`または`For Each`、ループの本体で、または、 [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)ステートメントです。  
  
## <a name="exceptions"></a>例外  
 大半の非同期メソッドを返す、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> 返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。 `Await` 演算子は、これらのプロパティにアクセスします。  
  
 タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`Await` 演算子はその例外を再スローします。  
  
 取り消されたタスクを返す非同期メソッドを待機する場合、`Await`演算子<xref:System.OperationCanceledException>.</xref:System.OperationCanceledException>を再スロー  
  
 障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。  タスクが<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>への呼び出しの結果になる可能性があります、 このようなタスクを待機すると、await 操作によって&1; つの例外のみが再スローされます。 ただし、どの例外が再スローされるかを予測することはできません。  
  
 非同期のメソッドのエラー処理の例については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。  
  
## <a name="example"></a>例  
 次に示す Windows フォームの例では、`Await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。 このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。 なし、`Await`演算子、 `WaitSynchronously` 、使用されているにもかかわらず、同期的に実行、`Async`修飾子を呼び出すと、その定義を<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>本体にです</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>。  
  
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
  
## <a name="see-also"></a>関連項目  
 [非同期プログラミングを Async と Await](../../../visual-basic/programming-guide/concepts/async/index.md)   
 [チュートリアル: Async を使用して、Web にアクセスして Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Async](../../../visual-basic/language-reference/modifiers/async.md)
