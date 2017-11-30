---
title: "タスク ベースの非同期パターンの実装"
ms.date: 06/14/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: fab6bd41-91bd-44ad-86f9-d8319988aa78
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e61b0c94b1512509008d67017389fa11f938999
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-task-based-asynchronous-pattern"></a>タスク ベースの非同期パターンの実装
タスク ベースの非同期パターン (TAP) は、3 つの方法 (Visual Studio の C# および Visual Basic コンパイラを使用する方法、手動で行う方法、またはコンパイラと手動による方法を組み合わせた方法) で実装できます。 以下のセクションでは、それぞれの方法について詳しく説明します。 TAP パターンを使用して、計算主体と O バインドの両方の非同期操作を実装することができます。 [ワークロード](#workloads)各種の操作について説明します。

## <a name="generating-tap-methods"></a>TAP メソッドの生成

### <a name="using-the-compilers"></a>コンパイラを使用
以降で[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、属性が設定されているメソッド、`async`キーワード (`Async` Visual Basic で) 非同期メソッド、および c# および Visual Basic コンパイラを実装するために必要な変換を実行すると見なされますが、TAP を使用して非同期メソッドです。 非同期メソッドは、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトまたは <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> オブジェクトを返す必要があります。 後者の関数の本体を返す必要があります、 `TResult`、コンパイラにより、この結果は、結果として得られるタスク オブジェクトで使用できるとします。 同様に、メソッド本体で処理されない例外は、出力タスクにマーシャリングされ、結果として得られるタスクが <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> 状態で終了する原因となります。 例外は、<xref:System.OperationCanceledException> (または派生型) がハンドルされない場合で、結果として得られるタスクは <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> 状態で終了します。

### <a name="generating-tap-methods-manually"></a>TAP メソッドを手動で生成します。
TAP パターンは、実装の制御を強化するために手動で実装することができます。 コンパイラは、<xref:System.Threading.Tasks?displayProperty=nameWithType> 名前空間から公開されるパブリック アクセス機能および <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間でサポートされている型に依存します。 TAP を実装するには、<xref:System.Threading.Tasks.TaskCompletionSource%601> オブジェクトを作成して非同期操作を実行し、それが完了したら、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>、または <xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> メソッド、またはそのいずれかのメソッドの `Try` バージョンを呼び出します。 TAP メソッドを手動で実装する場合には、表現されている非同期操作の完了時に、結果として得られるタスクを完了する必要があります。 例:

[!code-csharp[Conceptual.TAP_Patterns#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#1)]
[!code-vb[Conceptual.TAP_Patterns#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#1)]

### <a name="hybrid-approach"></a>ハイブリッド手法
 TAP パターンは手動で実装しても、コア ロジックはコンパイラの実装に委譲すると便利な場合があります。 たとえば、例外を <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトを使用して公開するのではなく、メソッドの直接の呼び出し元にエスケープするように、コンパイラが生成した非同期メソッドの外部で引数を検証する場合は、ハイブリッド手法を使用します。

 [!code-csharp[Conceptual.TAP_Patterns#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#2)]
 [!code-vb[Conceptual.TAP_Patterns#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#2)]

 また、このような委譲が便利なもう 1 つのケースとして、高速パスの最適化を実装し、キャッシュされたタスクを返す場合を挙げられます。

## <a name="workloads"></a>作業負荷
計算主体および I/O バインドの非同期操作は、いずれも、TAP のメソッドとして実装することができます。 ただし、TAP メソッドがライブラリから公開される場合には、TAP メソッドは、I/O バインド操作 (計算が含まれていても、純粋な計算ではない) を含む作業負荷にのみ指定する必要があります。 メソッドが純粋に計算主体の場合は、同期実装としてのみ公開する必要があります。 利用するコードにはタスクまたは並列処理を実現するために別のスレッドに作業をオフロードするには、その同期メソッドの呼び出しをラップするかどうかを選択がされます。 非同期実装としてのみ公開するか、メソッドは IO バウンドである場合。

### <a name="compute-bound-tasks"></a>計算主体のタスク
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスは、計算を集中的に行う操作の表現に適しています。 既定では、このクラスは、<xref:System.Threading.ThreadPool> クラス内の特別なサポートを利用します。また、いつ、どこで、どのように非同期計算を実行するかを細かく制御することもできます。

計算主体のタスクは、次の方法で生成できます。

- .NET Framework 4 では、デリゲート (通常、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> または <xref:System.Action%601>) の非同期実行を許容する <xref:System.Func%601> メソッドを使用します。 <xref:System.Action%601> のデリゲートを指定する場合、メソッドはデリゲートの非同期実行を表す <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトを返します。 <xref:System.Func%601> のデリゲートを指定する場合、メソッドは <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> オブジェクトを返します。 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> メソッドのオーバーロードは、キャンセル トークン (<xref:System.Threading.CancellationToken>)、タスクの作成オプション (<xref:System.Threading.Tasks.TaskCreationOptions>)、およびタスク スケジューラ (<xref:System.Threading.Tasks.TaskScheduler>) を受け取ります。 たとえば、<xref:System.Threading.Tasks.Task.Factory%2A> など、現在のタスク スケジューラをターゲットとするファクトリ インスタンスを、<xref:System.Threading.Tasks.Task> クラスの静的プロパティ (`Task.Factory.StartNew(…)`) として使用できます。

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (.NET Core と .NET Standard を含む) 以降のバージョンでは、静的なを使用して<xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>メソッドへのショートカットとして<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>です。 スレッド プールをターゲットとする計算主体のタスクを簡単に起動するには、<xref:System.Threading.Tasks.Task.Run%2A> を使用します。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]計算主体のタスクを起動するための推奨メカニズムは、これ以降のバージョンとします。 使用して`StartNew`直接行う場合のみ、タスクをより細かく管理します。

- タスクを個別に生成およびスケジュールする場合は、`Task` 型のコンストラクターまたは `Start` メソッドを使用します。 パブリック メソッドは、既に開始されているタスクのみを返す必要があります。

- <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> メソッドのオーバーロードを使用します。 このメソッドは、別のタスクが完了したときにスケジュールされる新しいタスクを作成します。 一部の <xref:System.Threading.Tasks.Task.ContinueWith%2A> オーバーロードは、キャンセル トークン、継続オプション、およびタスク スケジューラを受け取るため、継続タスクのスケジュール設定と実行を細かく制御することができます。

- 使用して、<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>と<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType>メソッドです。 これらのメソッドは、指定された一連のタスクのすべてまたは一部の完了時にスケジュールされる新しいタスクを作成します。 これらのメソッドは、これらのタスクの実行と、スケジュール設定を制御するオーバー ロードも提供します。

計算主体のタスクでは、実行開始前に取り消し要求を受信した場合に、スケジュール済みのタスクがシステムによって実行されないようにすることができます。 したがって、キャンセル トークン (<xref:System.Threading.CancellationToken> オブジェクト) を指定すると、そのトークンを監視する非同期コードにそのトークンを渡すことができます。 また、`StartNew` や `Run` など、前述のメソッドのいずれかにそのトークンを指定し、`Task` ランタイムによって、そのトークンが監視されるようにもできます。

たとえば、イメージをレンダリングする非同期メソッドを考えます。 タスクの本体によってキャンセル トークンをポーリングすることで、レンダリングの実行中に取り消し要求を受信した場合にコードを早期に終了できるようにします。 また、取り消し要求がレンダリングの開始前に発生した場合、レンダリング処理が行われないようにします。

[!code-csharp[Conceptual.TAP_Patterns#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#3)]
[!code-vb[Conceptual.TAP_Patterns#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#3)]

計算主体のタスクは、次の条件のうち最低でも 1 つが true の場合に <xref:System.Threading.Tasks.TaskStatus.Canceled> 状態で終了します。

- 取り消し要求は、タスクが <xref:System.Threading.CancellationToken> 状態に遷移する前に、引数として作成メソッド (`StartNew` や `Run` など) に渡される <xref:System.Threading.Tasks.TaskStatus.Running> オブジェクトを使用して受け取ります。

- このようなタスクの本体では、<xref:System.OperationCanceledException> 例外がハンドルされなくなります。この例外にはタスクに渡されたのと同じ <xref:System.Threading.CancellationToken> が含まれていて、このトークンは取り消しが要求されていることを示します。

別の例外がそのタスク本体でハンドルされないと、タスクは <xref:System.Threading.Tasks.TaskStatus.Faulted> 状態で終了し、タスクでの待機または結果へのアクセスが試みられると例外をスローします。

### <a name="io-bound-tasks"></a>O バインドのタスク
スレッドの実行全体に対してスレッドによって直接サポートされないタスクを作成するには、<xref:System.Threading.Tasks.TaskCompletionSource%601> 型を使用します。 この型は、関連する <xref:System.Threading.Tasks.TaskCompletionSource%601.Task%2A> インスタンスを返す <xref:System.Threading.Tasks.Task%601> プロパティを公開します。 このタスクの有効期間は、<xref:System.Threading.Tasks.TaskCompletionSource%601>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetException%2A>、<xref:System.Threading.Tasks.TaskCompletionSource%601.SetCanceled%2A> バリアントなどの `TrySet` メソッドによって制御されます。

指定時間が経過すると完了するタスクを作成する場合を考えてみます。 たとえば、ユーザー インターフェイスでアクティビティを遅延させる場合などです。 <xref:System.Threading.Timer?displayProperty=nameWithType> クラスには、一定時間経過後にデリゲートを非同期に呼び出す機能、また、<xref:System.Threading.Tasks.TaskCompletionSource%601> を使用して、タイマーの前に <xref:System.Threading.Tasks.Task%601> を配置する機能が用意されています。次に例を示します。

[!code-csharp[Conceptual.TAP_Patterns#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#4)]
[!code-vb[Conceptual.TAP_Patterns#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#4)]

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、このような目的のために <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> メソッドが用意されており、別の非同期メソッド内で使用して、たとえば、非同期ポーリング ループを実装することもできます。

[!code-csharp[Conceptual.TAP_Patterns#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#5)]
[!code-vb[Conceptual.TAP_Patterns#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#5)]

<xref:System.Threading.Tasks.TaskCompletionSource%601> クラスには、非ジェネリック クラスがありません。 ただし、<xref:System.Threading.Tasks.Task%601> から <xref:System.Threading.Tasks.Task> が派生されるため、単純にタスクを返す I/O バインド メソッドに対してジェネリックな <xref:System.Threading.Tasks.TaskCompletionSource%601> オブジェクトを使用できます。 これを行うには、ソースをダミー `TResult` と共に使用します (<xref:System.Boolean> は適切な既定の選択肢ですが、<xref:System.Threading.Tasks.Task> のユーザーがそれを <xref:System.Threading.Tasks.Task%601> にダウンキャストすることが懸念される場合は、代わりにプライベートな `TResult` を使用することもできます)。 たとえば、前の例の `Delay` メソッドは、結果として得られるオフセット (`Task<DateTimeOffset>`) と共に現在時間を返します。 このような結果値が不要である場合、メソッドのコードは次のように記述できます (戻り値の型と <xref:System.Threading.Tasks.TaskCompletionSource%601.TrySetResult%2A> の引数が変化することに注意してください)。

[!code-csharp[Conceptual.TAP_Patterns#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#6)]
[!code-vb[Conceptual.TAP_Patterns#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#6)]

### <a name="mixed-compute-bound-and-io-bound-tasks"></a>計算主体と O バインドのタスクの混在
非同期メソッドは、計算主体の操作や I/O バインド操作に限らず、この 2 つを混在させた操作を表現できます。 実際、複数の非同期操作は、しばしばより規模の大きな混合操作に合成されます。 たとえば、前の例の `RenderAsync` メソッドでは、いくつかの入力 `imageData` に基づいて、計算を集中的に行う操作を実行してイメージをレンダリングしました。 この `imageData` は、非同期にアクセスする Web サービスから次のように取得される場合があります。

[!code-csharp[Conceptual.TAP_Patterns#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.tap_patterns/cs/patterns1.cs#7)]
[!code-vb[Conceptual.TAP_Patterns#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.tap_patterns/vb/patterns1.vb#7)]

また、この例では、単一のキャンセル トークンが複数の非同期操作でどのようにスレッド化されるかも示します。 詳細については、キャンセルの使用」を参照してください。[タスクベースの非同期パターンの利用](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)です。

## <a name="see-also"></a>関連項目
 [タスク ベースの非同期パターン (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [タスク ベースの非同期パターンの利用](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)  
 [他の非同期パターンと型との相互運用](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)  
