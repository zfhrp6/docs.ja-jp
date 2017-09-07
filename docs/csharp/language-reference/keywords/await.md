---
title: "await (C# リファレンス)"
ms.date: 2017-05-22
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 28be25d2f467ea5df4de50516bfa03347c77081e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="await-c-reference"></a>await (C# リファレンス)
`await` 演算子は非同期メソッドのタスクに適用され、中断ポイントを挿入することで、メソッドの実行を、待機中のタスクが完了するまで中断します。 このタスクは、進行中の作業を表します。  
  
`await` は、[async](../../../csharp/language-reference/keywords/async.md) キーワードによって変更された非同期メソッドでのみ使用できます。 このようなメソッド (`async` 修飾子を使用して定義され、通常 1 つ以上の `await` 式を含むメソッド) が、"*非同期メソッド*" と呼ばれます。  
  
> [!NOTE]
>  `async` キーワードおよび `await` キーワードは、C# 5 で導入されました。 非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」をご覧ください。  
  
`await` 演算子を適用するタスクは、通常、[タスク ベースの非同期パターン](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)を実装するメソッド呼び出しによって返されます。 たとえば、<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、および `System.Threading.Tasks.ValueType<TResult>` オブジェクトを返すメソッドです。  

  
 次の例では、<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=fullName> メソッドは `Task<byte[]>` を返します。 これにより、タスクが完了したときに実際のバイト配列が生成されることが保証されます。 `await` 演算子は、<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> メソッドの処理が完了するまで実行を中断します。 その間、コントロールは `GetPageSizeAsync` の呼び出し元に戻されます。 タスクの実行が終了すると、`await` 式はバイト配列に評価されます。  

[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。 Microsoft Web サイトの[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)からサンプルをダウンロードできます。 この例は AsyncWalkthrough_HttpClient プロジェクトにあります。  
  
前の例で示したように、`Task<TResult>` を返すメソッド呼び出しの結果に `await` を適用する場合、`await` 式の型は `TResult` です。 `Task` を返すメソッド呼び出しの結果に `await` が適用されている場合、`await` 式の型は `void` になります。 この違いを次の例に示します。  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` 式は、自身が実行されているスレッドをブロックするのではなく、 非同期メソッドの残りの部分が待機中のタスクの継続として登録されるようにします。 これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。 タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。  
  
`await` 式は、`async` 修飾子でマークする必要がある外側のメソッド、ラムダ式、または匿名メソッドの本体でのみ使用できます。 *await* という用語がキーワードとして機能するのはこのコンテキストだけです。 他の場所では、識別子として解釈されます。 メソッド、ラムダ式、または匿名メソッド内では、`await` 式は、同期関数、クエリ式、[lock ステートメント](../../../csharp/language-reference/keywords/lock-statement.md)のブロック、または [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストの本体では使用できません。  
  
## <a name="exceptions"></a>例外  
大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。 返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。 `await` 演算子は、`GetAwaiter` メソッドによって返されたオブジェクトでメソッドを呼び出して、こうしたプロパティにアクセスします。  
  
タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`await` 演算子はその例外を再スローします。  
  
タスクを返す非同期メソッドを待機しているときにそのメソッドが取り消された場合、`await` 演算子は <xref:System.OperationCanceledException> を再スローします。  
  
障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。 たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果になることがあります。 このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。 ただし、どの例外が再スローされるかを予測することはできません。  
  
非同期メソッドのエラー処理の例については、「[try-catch](../../../csharp/language-reference/keywords/try-catch.md)」をご覧ください。  
  
## <a name="example"></a>例  
次の例では、URL がコマンド ラインの引数として渡されたページの合計文字数を返します。 この例は、`async` キーワードでマークされた `GetPageLengthsAsync` メソッドを呼び出しています。 その後、`GetPageLengthsAsync` メソッドは `await` キーワードを使用して、<xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=fullName> メソッドへの呼び出しを待ちます。  

[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

アプリケーション エントリ ポイントでの `async` および `await` の使用はサポートされていないため、`async` 属性は `Main` メソッドに適用できません。また、`GetPageLengthsAsync` メソッド呼び出しを待つこともできません。 非同期操作が完了するのを `Main` メソッドが確実に待つようにするには、<xref:System.Threading.Tasks.Task%601.Result?displayProperty=fullName> プロパティの値を取得します。 値を返さないタスクについては、<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> メソッドを呼び出すことができます。 

## <a name="see-also"></a>関連項目  
[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)   
[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[async](../../../csharp/language-reference/keywords/async.md)

