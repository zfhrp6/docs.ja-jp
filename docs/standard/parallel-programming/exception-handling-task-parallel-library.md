---
title: "例外処理 (タスク並列ライブラリ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e62498376d321d8ff22a53315b9d5f18a8865056
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling-task-parallel-library"></a>例外処理 (タスク並列ライブラリ)
タスク内で実行中のユーザー コードによってスローされた、ハンドルされない例外は、呼び出し元のスレッドに反映されます。ただし、このトピックの後半で説明している特定の状況を除きます。 静的のいずれかを使用すると、例外が反映されますまたはインスタンス<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>または<!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  -->`Wait`メソッドを処理して、それらの呼び出しを囲んで、 `try` / `catch`ステートメントです。 タスクが、アタッチされた子タスクの親である場合、または複数のタスクを待機している場合、複数の例外がスローされることがあります。  
  
 呼び出し元のスレッドにすべての例外を反映するために、Task インフラストラクチャが例外を <xref:System.AggregateException> インスタンスにラップします。 <xref:System.AggregateException> 例外には、スローされた元のすべての例外を調べるために列挙できる <xref:System.AggregateException.InnerExceptions%2A> プロパティがあり、個々に処理したり未処理にしたりできます。 使用して、元の例外を処理することもできます、<xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>メソッドです。  
  
 例外が 1 つだけスローされた場合でも、次の例のように <xref:System.AggregateException> 例外にラップされます。  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 ハンドルされない例外は、 <xref:System.AggregateException> をキャッチして、内部例外を確認しないことで回避できます。 ただし、並列でない状況で基本的な <xref:System.Exception> の種類をキャッチする場合と類似しているため、この操作はお勧めしません。 特定の操作を取得することなく例外をキャッチして回復しようとすると、プログラムが中間状態のままになるおそれがあります。  
  
 呼び出すしたくない場合、<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>または<!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  -->`Wait`タスクの完了を待つメソッド取得することも、<xref:System.AggregateException>から、タスクの例外<xref:System.Threading.Tasks.Task.Exception%2A>次の例のように、プロパティです。 詳細については、このトピックの「 [Task.Exception プロパティによる例外の確認](#ExceptionProp) 」セクションを参照してください。  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 例外を反映するタスクを待機しない場合、またはタスクの <xref:System.Threading.Tasks.Task.Exception%2A> プロパティにアクセスする場合、例外はタスクがガベージ コレクトされるときに .NET の例外ポリシーに従ってエスカレートされます。  
  
 連結しているスレッドへ例外が上方向に通知されると、例外が発生した後も、タスクによって一部の項目の処理が続行される可能性があります。  
  
> [!NOTE]
>  [マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。 F5 キーを押して続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール]** メニューの [オプション]、[デバッグ] の順にクリックし、[全般] で **[マイ コードのみを有効にする]**チェック ボックスをオフにします。  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>アタッチされた子タスクと入れ子の AggregateExceptions  
 タスクに、例外をスローする子タスクがアタッチされている場合、その例外は親タスクに反映される前に <xref:System.AggregateException> でラップされます。つまり、呼び出し元のスレッドに反映される前に、その例外が固有の <xref:System.AggregateException> でラップされるということです。 このような場合、<xref:System.AggregateException.InnerExceptions%2A>のプロパティ、<xref:System.AggregateException>でキャッチされた例外、<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>または<!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  -->`Wait`または<xref:System.Threading.Tasks.Task.WaitAny%2A>または<xref:System.Threading.Tasks.Task.WaitAll%2A>メソッドは、1 つ以上含まれています<xref:System.AggregateException>インスタンスできません、。エラーの原因となった元の例外。 反復処理しなくて済むように入れ子になった<xref:System.AggregateException>の例外を除き、行うこともできます、<xref:System.AggregateException.Flatten%2A>すべてを削除するメソッド、入れ子になった<xref:System.AggregateException>の例外を除き、ように、<xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType>プロパティには、元の例外が含まれています。 次の例では、入れ子の <xref:System.AggregateException> インスタンスが 1 つのループで平坦化され、処理されています。  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 使用することも、<xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType>複数から内部例外を再スローするメソッド<xref:System.AggregateException>インスタンス 1 つの複数のタスクによってスローされた<xref:System.AggregateException>インスタンス、次の例を示します。  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>デタッチされた子タスクの例外  
 既定では、子タスクはデタッチされた状態で作成されます。 デタッチされたタスクからスローされた例外は、処理されるか、直接の親に再スローされる必要があります。これらの例外は、アタッチされた子タスクが反映されるのとは異なる方法で、呼び出し元のスレッドに反映されます。 最上位の親では、デタッチされた子からの例外を手動で再スローすることで、 <xref:System.AggregateException> にラップして、呼び出し元のスレッドに反映させることができます。  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 子タスク内の例外を確認するために継続を使用する場合でも、親タスクによって例外を確認する必要があります。  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>他の処理との連携によるキャンセル処理を示す例外  
 タスク内のユーザー コードがキャンセル要求に応答する場合の正しいプロシージャは、その要求が伝えられたキャセル トークンに渡すために <xref:System.OperationCanceledException> をスローすることです。 例外が反映される前に、タスク インスタンスによって、例外内のトークンがそのタスクが作成されたときに渡されたトークンと比較されます。 それらが同じである場合、タスクは <xref:System.Threading.Tasks.TaskCanceledException> でラップされた <xref:System.AggregateException>を反映します。これは、内部例外を調べると確認できます。 ただし、呼び出し元のスレッドがタスクを待機していない場合、このような特定の例外は反映されません。 詳細については、「 [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md)」を参照してください。  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>内部例外をフィルター処理する Handle メソッドの使用  
 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> メソッドを使用すると、"処理済み" として扱うことのできる例外をフィルターで除外できます。追加のロジックを使用する必要はありません。 用意されているユーザー デリゲートで、<xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType>メソッド、例外の種類を調べることができます、<xref:System.Exception.Message%2A>プロパティ、またはその他の情報に問題があるかどうかを判断するために使用します。 デリゲートを返す任意の例外`false`新しいで再スローされます<xref:System.AggregateException>インスタンス化した直後、<xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>メソッドを返します。  
  
 次の例は機能的には、内の各例外を調べるこのトピックの最初の例は、<xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType>コレクション。  この例外ハンドラーを呼び出す代わりに、<xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>各例外と例外に対してのみ再スローされないメソッド オブジェクト`CustomException`インスタンス。  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 使用するより詳細な例を次に示します、<xref:System.AggregateException.Handle%2A?displayProperty=nameWithType>に対して特別な処理を提供するメソッドを<xref:System.UnauthorizedAccessException>ファイルを列挙中に例外が発生します。  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>Task.Exception プロパティによる例外の確認  
 タスクが <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> 状態で完了した場合、その <xref:System.Threading.Tasks.Task.Exception%2A> プロパティを調べることで違反の原因となった例外を見つけることができます。 <xref:System.Threading.Tasks.Task.Exception%2A> プロパティを確認する場合は、次の例に示すように、継続元タスクが違反した場合にのみ実行される継続を使用することをお勧めします。  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 実際のアプリケーションでは、継続のデリゲートで例外に関する詳細情報を記録して、新しいタスクを作成して例外から回復することが考えられます。  
  
## <a name="unobservedtaskexception-event"></a>UnobservedTaskException イベント  
 信頼関係のないプラグインをホストするときなど、シナリオによっては、問題のない例外がよく発生する場合や、難しすぎてすべてを手動で観察できなくなる場合があります。 このような場合、<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> イベントを処理できます。 ハンドラーに渡される <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> インスタンスを使用して、観察されない例外が連結しているスレッドに反映されないようにすることができます。  
  
## <a name="see-also"></a>関連項目  
 [タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
