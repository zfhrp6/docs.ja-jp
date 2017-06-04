---
title: "データフロー (タスク並列ライブラリ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "タスク並列ライブラリ、データフロー"
  - "TPL データフロー ライブラリ"
ms.assetid: 643575d0-d26d-4c35-8de7-a9c403e97dd6
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# データフロー (タスク並列ライブラリ)
<a name="top"></a>タスク並列ライブラリ (TPL) は、同時実行対応アプリケーションの堅牢性を強化するためにデータ フロー コンポーネントを提供します。 これらのデータ フロー コンポーネントと総称として、 *TPL データフロー ライブラリ*します。 データ フロー モデルは、粒度の粗いデータ フローおよびパイプライン処理タスクのためのインプロセス メッセージ パッシングを提供し、アクター ベースのプログラミング モデルを推進します。 データ フロー コンポーネントは、TPL の種類とスケジュール インフラストラクチャの上でビルドされ、C#、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]、および同期プログラミングの F# 言語のサポートを統合します。 相互に非同期通信を行う必要がある複数の操作を行う場合、またはデータが使用可能になったときにデータを処理する場合に、これらのデータ フロー コンポーネントは役立ちます。 たとえば、Web カメラからのイメージ データを処理するアプリケーションを考えてみます。 データ フロー モデルを使用すると、イメージ フレームが使用可能になったときに、それをアプリケーションで処理できます。 場合は、アプリケーションは、イメージ フレームを向上させる、たとえば、輝度修正や赤目補正などを実行することによって作成、*パイプライン*データ フロー コンポーネントのです。 パイプラインの各ステージは、イメージを変換するために、TPL が提供する機能のような、粒度の粗い並列機能を使用する場合があります。  
  
 ここでは、TPL データ フロー ライブラリの概要を示します。 プログラミング モデル、定義済みのデータ フロー ブロックの型、およびアプリケーションの特定の要件を満たすためのデータ フロー ブロックの構成方法を説明します。  
  
> [!TIP]
>  TPL データフロー ライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName>名前空間) と一緒に配布されませんが、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]です。 インストールする、 <xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開きます[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニュー オンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージです。  
  
 このドキュメントは、次のトピックに分かれています。  
  
-   [プログラミング モデル](#model)  
  
-   [定義済みのデータ フロー ブロックの型](#predefined_types)  
  
-   [データ フロー ブロックの動作を構成します。](#behavior)  
  
-   [カスタム データ フロー ブロック](#custom)  
  
<a name="model"></a>   
## <a name="programming-model"></a>プログラミング モデル  
 TPL データ フロー ライブラリはメッセージ パッシングおよび、並列化され、CPU 負荷が高く、I/O 負荷が高く、スループットが高く、待機時間が短いアプリケーションのための基盤を提供します。 また、システム上でのデータのバッファリング方法や移動について、明示的に制御できます。 データ フロー プログラミング モデルの理解を深めるため、非同期的にディスクからイメージを読み込み、それらの合成イメージを作成するアプリケーションを考えてみます。 従来のプログラミング モデルでは、通常、タスクを協調させ、共有データにアクセスするには、コールバックおよびロックなどの同期オブジェクトを使用する必要があります。 データ フロー プログラミング モデルを使用すると、イメージがディスクから読み込まれたときにそれを処理する、データ フロー オブジェクトを作成できます。 データ フロー モデルでは、データが使用可能になったときの処理方法と、データ間の依存関係を宣言します。 ランタイムがデータ間の依存関係を管理するため、通常は共有データへのアクセスの同期要件を回避できます。 さらに、ランタイムのスケジュールは非同期のデータの到着に基づいて動作するため、基になるスレッドを効率的に管理することによって、データ フローの応答性とスループットが向上します。 データ フロー プログラミング モデルを使用して Windows フォーム アプリケーションでイメージ処理を実装する例を[チュートリアル: Windows フォーム アプリケーションでのデータ フローを使用して](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)します。  
  
### <a name="sources-and-targets"></a>ソースとターゲット  
 TPL データ フローのライブラリから成る*データフロー ブロック*バッファリングと処理データ構造体でデータがあります。 TPL データ フロー ブロックの&3; 種類の定義:*ソース ブロック*、*ターゲット ブロック*、および*伝達子ブロック*します。 ソース ブロックはデータのソースとして機能し、それを読み取ることができます。 ターゲット ブロックはデータのレシーバーとして機能し、それに書き込むことができます。 伝達子ブロックは、ソース ブロックとターゲット ブロックのどちらとしても機能し、読み取りも書き込みもできます。 TPL を定義、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=fullName>ソースを表し、インターフェイス<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=fullName>ターゲットを表し、および<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602?displayProperty=fullName>によって伝達子を表す</TInput, TOutput>。 <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>両方から継承<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、および<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>します。\</TInput, TOutput>  
  
 TPL データ フローのライブラリを実装するいくつかの定義済みのデータ フロー ブロックの型を提供する、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>、および<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>インターフェイス\</TInput, TOutput>。 これらのデータ フロー ブロックの型が、セクションでは、このドキュメントで説明されている[データ フロー ブロックの型の定義済みの](#predefined_types)です。  
  
### <a name="connecting-blocks"></a>ブロックの接続  
 フォームにデータ フロー ブロックを接続することができます*パイプライン*、データ フロー ブロックのリニア シーケンスであるまたは*ネットワーク*、データ フロー ブロックのグラフであります。 パイプラインは、ネットワークの&1; つの形態です。 パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=fullName>メソッドは、ターゲット ブロックにソース データフロー ブロックをリンクします。 ソースは、ターゲットにリンクしないか、または複数のターゲットにリンクできます。ターゲットはソースからリンクされないか、または複数のソースからリンクできます。 パイプラインまたはネットワークとの間でデータ フロー ブロックを同時に追加または削除できます。 定義済みのデータ フロー ブロックの型は、リンクとリンク解除のすべてのスレッド セーフな側面を処理します。  
  
 例の基本的なパイプラインを作成するデータ フロー ブロックを接続する場合は、次を参照してください。[チュートリアル: データフロー パイプラインの作成](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)します。 複雑なネットワークを形成するデータフロー ブロックを接続する例を参照してください。[チュートリアル: Windows フォーム アプリケーションでのデータ フローを使用して](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)します。 ソースは、メッセージをターゲットに提供した後、元のターゲットをリンク解除は、次を参照してください。[方法: データフロー ブロックのリンクを解除](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)します。  
  
#### <a name="filtering"></a>フィルター処理  
 呼び出すと、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A?displayProperty=fullName>を対象のソースをリンクする方法、ターゲット ブロックが受け入れるか、そのメッセージの値に基づいてメッセージが拒否されたかどうかを決定するデリゲートを指定することができます。 このフィルター機構は、データ フロー ブロックが特定の値のみを確実に受信するために便利な方法です。 定義済みのデータ フロー ブロックの型のほとんどの場合に、ソース ブロックが複数のターゲット ブロックに接続されている場合は、ターゲット ブロックがメッセージを拒否すると、ソースはそのメッセージを次のターゲットに提供します。 ソースがターゲットにメッセージを提供する順序はソースによって定義され、ソースの種類によって異なる場合があります。 1 つのターゲットがメッセージを受け入れると、ほとんどのソース ブロックの型がメッセージの提供を停止します。 この規則の例外は、 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>クラスは、いくつかのターゲットがメッセージを拒否する場合でも、各メッセージをすべてのターゲットを提供します。 例のフィルタ リングを使用して、特定のメッセージのみを処理する場合は、次を参照してください。[チュートリアル: Windows フォーム アプリケーションでのデータ フローを使用して](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)します。  
  
> [!IMPORTANT]
>  それぞれの定義済みのソースのデータ フロー ブロックの型は、メッセージを受信した順にそれが伝達されることを保証するため、ソース ブロックは各メッセージを読み取ってから、次のメッセージを処理する必要があります。 したがって、フィルター処理を使用して複数のターゲットをソースに接続する場合、各メッセージを少なくとも&1; つのターゲット ブロックが受信するようにします。 そうしない場合、アプリケーションでデッドロックが発生する可能性があります。  
  
### <a name="message-passing"></a>メッセージ パッシング  
 概念に関連するデータ フロー プログラミング モデル*メッセージ パッシング*メッセージを送信するプログラムの独立したコンポーネントを相互通信、です。 アプリケーション コンポーネント間でメッセージを伝達する方法の&1; つを呼び出すことです、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>と<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=fullName>をターゲット データ フロー ブロック ポストにメッセージを送信する方法 (<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>同期します。<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>非同期的に動作)、および<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>、 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>と<xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A>メソッドのソース ブロックからメッセージを受信します。 入力データをヘッド ノード (ターゲット ブロック) に送信し、出力データをパイプラインのターミナル ノードまたはネットワーク (1 つ以上のソース ブロック) のターミナル ノードから受信することにより、これらのメソッドとデータ フロー パイプラインまたはネットワークを結合することができます。 使用することも、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Choose%2A>メソッドの先頭から読み取り、使用可能なデータがあり、そのデータに対して操作を実行する指定されたソースのです。  
  
 ソース ブロックでは、ターゲット ブロックにデータを提供を呼び出して、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A?displayProperty=fullName>メソッドです。 ターゲット ブロックは、提供されたメッセージに、3 つの方法のうちの&1; つで応答します。メッセージを受け入れるか、メッセージを拒否するか、またはメッセージを延期できます。 ターゲットがメッセージを受け入れるときに、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>メソッドが返す<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>します。 ターゲットがメッセージを拒否すると、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>メソッドが返す<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>します。 ターゲットは、元のすべてのメッセージを受信しないことが必要な場合<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>返します<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>します。 その戻り値を受信した後は、定義済みのソース ブロックの型は、リンクされたターゲットにメッセージを提供せず、自動的にそのターゲットからリンク解除します。  
  
 ターゲット ブロックが後で使用できるメッセージを延期すると、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601.OfferMessage%2A>メソッドが返す<xref:System.Threading.Tasks.Dataflow.DataflowMessageStatus>します。 メッセージを延期したターゲット ブロックはそれ以降の呼び出し、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReserveMessage%2A?displayProperty=fullName>メソッドを提供されたメッセージを予約しようとしています。 この時点で、メッセージはまだ使用できてターゲット ブロックから使用できるか、または他のターゲットに取得されています。 ターゲット ブロックがメッセージを後で必要または必要としないメッセージを呼び出し、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=fullName>または<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ReleaseReservation%2A>メソッドをそれぞれします。 通常は、メッセージの予約は、最短一致のモードで動作するデータ フロー ブロックの型で使用されます。 最短一致のモードについては、このドキュメントの後で説明します。 延期されたメッセージを予約せずに、ターゲット ブロックは使用することも、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.ConsumeMessage%2A?displayProperty=fullName>メソッドを直接延期されたメッセージを使用しようとしています。  
  
### <a name="dataflow-block-completion"></a>データ フロー ブロックの完了  
 データ フロー ブロックの概念をサポートも*完了*します。 完了した状態にあるデータ フロー ブロックは、処理を実行しません。 各データフロー ブロックが関連付けられている<xref:System.Threading.Tasks.Task?displayProperty=fullName>と呼ばれるオブジェクト、*完了タスク*ブロックの完了ステータスを表します。 待つため、<xref:System.Threading.Tasks.Task>オブジェクトの完了タスクを使用して終了するには、1 つを待機できるまたはデータフローの以上のターミナル ノードが終了するネットワークです。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>インターフェイスを定義、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>メソッドで、データ フロー ブロックの要求を完了するを通知するには、および<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>プロパティで、データ フロー ブロックの完了タスクを返します。 両方とも<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>と<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>継承、 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>インターフェイスです。  
  
 データ フロー ブロックがエラーなしで完了したか、1 つのエラーが発生したか、複数のエラーが発生したか、取り消されたかを知る&2; つの方法があります。 最初の方法は、 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName>完了タスクでのメソッド、 `try` - `catch`ブロック (`Try` - `Catch` Visual Basic で)。 次の例を作成し、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトをスローする<xref:System.ArgumentOutOfRangeException> 、入力値が&0; よりも小さい場合です。 <xref:System.AggregateException>この例を呼び出す場合にスローされる<xref:System.Threading.Tasks.Task.Wait%2A>完了タスクです。 <xref:System.ArgumentOutOfRangeException>を通じてアクセス、 <xref:System.AggregateException.InnerExceptions%2A>のプロパティ、 <xref:System.AggregateException>オブジェクトです。  
  
 [!code-csharp[TPLDataflow_Overview#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#10)]
 [!code-vb[TPLDataflow_Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#10)]  
  
 この例は、例外が実行データ フロー ブロックのデリゲートで処理されない場合を示します。 そのようなブロックの本体で例外を処理することをお勧めします。 そのようにできない場合は、ブロックはそれが取り消されたように動作し、受信メッセージを処理しません。  
  
 データ フロー ブロックが明示的に取り消されたときに、 <xref:System.AggregateException>オブジェクトを含む<xref:System.OperationCanceledException>で、 <xref:System.AggregateException.InnerExceptions%2A>プロパティです。 データ フローの取り消しの詳細については、このドキュメントの後の「取り消しの有効化」を参照してください。  
  
 データ フロー ブロックの完了ステータスを決定する&2; 番目の方法は、完了タスクの継続を使用するか、または C# と Visual Basic の非同期言語機能を使用して、完了したタスクを非同期的に待つことです。 提供するデリゲート、 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=fullName>メソッドには、<xref:System.Threading.Tasks.Task>継続元タスクを表すオブジェクト。 場合、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>プロパティを継続のデリゲートは完了タスクを受け取ります。 次の例似ていますが、1 つ前を使用して、 <xref:System.Threading.Tasks.Task.ContinueWith%2A>データ フロー操作全体の状態を出力する完了タスクを作成する方法です。  
  
 [!code-csharp[TPLDataflow_Overview#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#11)]
 [!code-vb[TPLDataflow_Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#11)]  
  
 などのプロパティを使用することもできます。 <xref:System.Threading.Tasks.Task.IsCanceled%2A>データ フロー ブロックの完了ステータスに関する追加情報を決定する継続タスクの本体にです。 継続タスクと取り消し処理およびエラー処理に関係の詳細については、次を参照してください。[を使用して継続タスクをタスクの連結](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)、[タスクのキャンセル](../../../docs/standard/parallel-programming/task-cancellation.md)、[例外処理](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)、および[NIB: 方法: タスクがスローした例外を処理](http://msdn.microsoft.com/ja-jp/d6c47ec8-9de9-4880-beb3-ff19ae51565d)します。  
  
 [[go to top](#top)]  
  
<a name="predefined_types"></a>   
## <a name="predefined-dataflow-block-types"></a>定義済みのデータ フロー ブロックの型  
 TPL データ フロー ライブラリは、いくつかの定義済みのデータ フロー ブロックの型を提供します。 これらの型は&3; つのカテゴリに分けられます。*バッファリング ブロック*、*実行ブロック*、および*ブロックをグループ化*します。 次のセクションでは、これらの種類を構成するブロックの型について説明します。  
  
### <a name="buffering-blocks"></a>バッファリング ブロック  
 バッファリング ブロックはデータ コンシューマーが使用するデータを保持します。 TPL データ フロー ライブラリは、3 つのバッファリング ブロックの型を提供します。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=fullName>、 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601?displayProperty=fullName>、および<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601?displayProperty=fullName>します。  
  
#### <a name="bufferblockt"></a>BufferBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスは汎用的な非同期メッセージング構造体を表します。 このクラスでは、複数のソースが書き込むことができるメッセージ、または複数のターゲットが読み取ることができるメッセージの先入れ先出し (FIFO) のキューを格納します。 ターゲットがからのメッセージを受信すると、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクト、そのメッセージはメッセージ キューから削除します。 したがって、ですが、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトは、複数のターゲットを持つことが、1 つだけのターゲットは各メッセージを受信します。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスは、複数のメッセージを別のコンポーネントに渡すし、そのコンポーネントは、各メッセージを受信する必要がある場合に便利です。  
  
 次の基本的な例がいくつか投稿<xref:System.Int32>値を<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトし、そのオブジェクトからそれらの値を読み取ります。  
  
 [!code-csharp[TPLDataflow_Overview#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#1)]
 [!code-vb[TPLDataflow_Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#1)]  
  
 メッセージの読み取りし、書き込みにする方法を示すコード例全体について、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトは、「[する方法: メッセージを記述し、データ フロー ブロックからメッセージの読み取り](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)します。  
  
#### <a name="broadcastblockt"></a>BroadcastBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>クラスは、別のコンポーネントを複数のメッセージを渡す必要がありますが、そのコンポーネントには、最新の値のみが必要がある場合に便利です。 また、このクラスは、メッセージを複数のコンポーネントにブロードキャストする場合にも便利です。  
  
 次の基本的な例の投稿、<xref:System.Double>値を<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>オブジェクトと、そのオブジェクトから複数回読み込みます、値の読み取り。 値はから削除されないため<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>オブジェクト毎回同じ値を使用できるで読み取られた後。  
  
 [!code-csharp[TPLDataflow_Overview#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#2)]
 [!code-vb[TPLDataflow_Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#2)]  
  
 使用する方法を示すコード例全体について<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>複数のターゲット ブロックにメッセージを送信するを参照してください。[方法: データフロー ブロックでタスク スケジューラを指定する](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)します。  
  
#### <a name="writeonceblockt"></a>WriteOnceBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>クラスに似ています、 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>クラスのことを除いて、 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトに&1; 回しか書き込むことができます。 考えることができます<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> c# に似ている[読み取り専用](../Topic/readonly%20\(C%23%20Reference\).md)([読み取り専用](../Topic/ReadOnly%20\(Visual%20Basic\).md)で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) ことを除いて、キーワード、 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトを変更できなくなるは、構築時にの代わりに値を受信後します。 ように、 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>クラス、ターゲットからメッセージを受信するときに、 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクト、そのメッセージはそのオブジェクトから削除されません。 そのため、複数のターゲットがメッセージのコピーを受信します。 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>クラスは、複数のメッセージの最初のだけを伝達する場合に便利です。  
  
 次の基本的な例を複数ポストバック<xref:System.String>値を<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトとし、その値をそのオブジェクトから読み込みます。 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトは、1 回に書き込むことが後にのみ、 <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトがメッセージを受け取り、それ以降のメッセージを破棄します。  
  
 [!code-csharp[TPLDataflow_Overview#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#3)]
 [!code-vb[TPLDataflow_Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#3)]  
  
 使用する方法を示すコード例全体について<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>に終了した最初の操作の値を提供するには、次を参照してください。[方法: データフロー ブロックのリンクを解除](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)します。  
  
### <a name="execution-blocks"></a>実行ブロック  
 実行ブロックは、受け取ったデータのそれぞれに、ユーザーが指定したデリゲートを呼び出します。 TPL データ フロー ライブラリは、次の&3; つの実行ブロックの型: <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=fullName>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=fullName>.\</TInput, TOutput> \</TInput, TOutput>  
  
#### <a name="actionblockt"></a>ActionBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>クラスは、データを受け取るとデリゲートを呼び出すターゲット ブロックです。 考えてみてください、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトとしてデータに使用可能な場合に非同期的に実行できるデリゲートです。 提供するデリゲート、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトは、型であることができます<xref:System.Action>または型`System.Func\<TInput, Task>`します。 使用すると、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトを<xref:System.Action>、各入力要素の処理は、デリゲートが返されたときに完了したと見なされます。 使用すると、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトを`System.Func\<TInput, Task>`、各入力要素の処理が完了した場合にのみと見なさ返された<xref:System.Threading.Tasks.Task>オブジェクトが終了しました。 これら&2; つのメカニズムを使用すると、使用することができます<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>各入力要素の同期および非同期で処理するためです。  
  
 次の基本的な例を複数ポストバック<xref:System.Int32>値を<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトです。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクトは、コンソールにそれらの値を出力します。 次にこの例では、ブロックを完了した状態に設定し、すべてのデータ フロー タスクの終了を待機します。  
  
 [!code-csharp[TPLDataflow_Overview#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#4)]
 [!code-vb[TPLDataflow_Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#4)]  
  
 デリゲートを使用する方法を説明する完全な例については、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>を参照してください[方法: 実行アクションと、データ フロー ブロックでデータを受信](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)します。  
  
#### <a name="transformblocktinput-toutput"></a>TransformBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>クラスに似ています、 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>クラスをターゲットとして、両方のソースとして動作する点が異なります\</TInput, TOutput>。 デリゲートに渡すことが、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトが型の値を返す`TOutput`</TInput, TOutput>。 提供するデリゲート、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトは、型であることができます`System.Func<TInput, TOutput>`または型`System.Func<TInput, Task>`\</TInput, TOutput>。 使用すると、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトを`System.Func\<TInput, TOutput>`、各入力要素の処理は、デリゲートが返されたときに完了したと見なされます</TInput, TOutput>。 使用すると、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトと共に使用`System.Func<TInput, Task<TOutput>>`、各入力要素の処理が完了した場合にのみと見なさ返された<xref:System.Threading.Tasks.Task>オブジェクトが終了した\</TInput, TOutput>。 同様に<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、これら&2; つのメカニズムを使用すると、使用することができます<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>各入力要素の同期および非同期で処理するためです\</TInput, TOutput>。  
  
 次の基本的な例を作成し、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>入力の平方根を計算するオブジェクト</TInput, TOutput>。 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>オブジェクトは<xref:System.Int32>入力として値を生成<xref:System.Double>出力としての値\</TInput, TOutput>。  
  
 [!code-csharp[TPLDataflow_Overview#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#5)]
 [!code-vb[TPLDataflow_Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#5)]  
  
 使用する完全な例について<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>では、Windows フォーム アプリケーションでイメージ処理を実行するデータ フロー ブロックのネットワーク、[チュートリアル: Windows フォーム アプリケーションでのデータ フローを使用して](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)\</TInput, TOutput>。  
  
#### <a name="transformmanyblocktinput-toutput"></a>TransformManyBlock(TInput, TOutput)  
 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>クラスに似ています、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>クラスのことを除いて<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>各入力値に値を出力&1; つのみの代わりに、値を入力ごとに&0; 個以上の出力値を生成します</TInput, TOutput></TInput, TOutput></TInput, TOutput>。 提供するデリゲート、 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>オブジェクトは、型であることができます`System.Func<TInput, IEnumerable<TOutput>>`または`type System.Func<TInput, Task<IEnumerable<TOutput>>>`\</TInput, TOutput>。 使用すると、 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>オブジェクトを`System.Func<TInput, IEnumerable<TOutput>>`、各入力要素の処理は、デリゲートが返されたときに完了したと見なされます</TInput, TOutput>。 使用すると、 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>オブジェクトを`System.Func<TInput, Task<IEnumerable<TOutput>>>`、各入力要素の処理が完了される場合にのみと見なさ返された`System.Threading.Tasks.Task<IEnumerable<TOutput>>`オブジェクトが終了した\</TInput, TOutput>。  
  
 次の基本的な例を作成し、 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>を個々 の文字のシーケンスに文字列を分割するオブジェクト</TInput, TOutput>。 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>オブジェクトは<xref:System.String>入力として値を生成<xref:System.Char>出力としての値\</TInput, TOutput>。  
  
 [!code-csharp[TPLDataflow_Overview#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#6)]
 [!code-vb[TPLDataflow_Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#6)]  
  
 使用する完全な例について<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>データフロー パイプラインの各入力に複数の独立した出力を生成するを参照してください[チュートリアル: データフロー パイプラインの作成](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)。\</TInput, TOutput> 。  
  
#### <a name="degree-of-parallelism"></a>並列化の次数  
 各<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>ブロックが処理できるようになるまで、オブジェクトのバッファーがメッセージを入力します</TInput, TOutput></TInput, TOutput>。 既定では、これらのクラスはメッセージを受信した順序で、一度に&1; つずつ処理します。 有効にする並列処理の次数を指定することも<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>と<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>同時に複数のメッセージを処理するオブジェクト\</TInput, TOutput>\</TInput, TOutput>。 同時実行に関する詳細については、このドキュメントの後の「並列化の次数の指定」のセクションを参照してください。 例については、同時に複数のメッセージを処理する、実行データフロー ブロックを有効にする並列処理の次数を設定する、次を参照してください。[方法: データフロー ブロックで並列処理の次数を指定](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)します。  
  
#### <a name="summary-of-delegate-types"></a>デリゲート型の概要  
 次の表に、デリゲート型を提供できる<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>のオブジェクト\</TInput, TOutput>\</TInput, TOutput>。 このテーブルでは、デリゲート型が同期的または非同期的に動作するかどうかについても示しています。  
  
|型|同期的なデリゲート型|非同期的なデリゲート型|  
|----------|-------------------------------|--------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|`System.Action`|`System.Func\<TInput, Task>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602></TInput, TOutput>|`System.Func\<TInput, TOutput>`2`|`System.Func<TInput, Task<TOutput>>`|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602></TInput, TOutput>|`System.Func<TInput, IEnumerable<TOutput>>`|`System.Func<TInput, Task<IEnumerable<TOutput>>>`|  
  
 実行ブロックの型を使用する場合にラムダ式を使用することもできます。 実行ブロックでラムダ式を使用する方法を示しています。 たとえば、次を参照してください。[方法: 実行アクションと、データ フロー ブロックでデータを受信](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)します。  
  
### <a name="grouping-blocks"></a>グループ化ブロック  
 グループ化ブロックは、さまざまな制約の下で&1; つ以上のソースからデータをまとめます。 TPL データ フロー ライブラリは、3 つの結合ブロックの型: <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>、および<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>.\</T1, T2> \</T1, T2>  
  
#### <a name="batchblockt"></a>BatchBlock(T)  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>クラスは、出力データの配列に、バッチと呼ばれる入力データのセットを結合します。 作成するときに、各バッチのサイズを指定する、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトです。 ときに、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトは、指定した数の入力要素を受け取ると、それらの要素を格納する配列を非同期的に伝達します。 場合、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトは、完了状態に設定されていますが、バッチを形成するための十分な要素を含んでいない、残りの入力要素を含む最終的な配列を伝達します。  
  
 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>クラスは、どちらかで動作*最長一致*または*最短*モードです。 既定では最長一致モードで、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトすべてメッセージを受け取り、提供される、指定した数の要素を受け取った後に、配列を伝達します。 最短一致モードで、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトは、十分なソースが、バッチを形成するブロックへのメッセージを提供するまで、すべての受信メッセージを延期します。 最長一致モードでは通常、最短一致モードよりも処理のオーバーヘッドが低いため、パフォーマンスがよくなります。 ただし、アトミックな方法で複数のソースの使用量を調整する必要がある場合、最短一致モードを使用できます。 最短一致モードを設定して指定<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A>に`False`で、`dataflowBlockOptions`内のパラメーター、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601.%23ctor%2A>コンス トラクターです。  
  
 次の基本的な例がいくつか投稿<xref:System.Int32>値を<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>バッチに&10; 個の要素を保持するオブジェクト。 すべての値が伝達されることを保証するために、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>、この例では、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>メソッドです。 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>メソッドのセット、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトを完了した状態にあり、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトは残りの要素を最終バッチとして伝達します。  
  
 [!code-csharp[TPLDataflow_Overview#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#7)]
 [!code-vb[TPLDataflow_Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#7)]  
  
 使用するコード例全体について<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>データベース挿入操作の効率を向上させるために、次を参照してください。[チュートリアル: BatchBlock および BatchedJoinBlock 効率の向上に使用](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)します。  
  
#### <a name="joinblockt1-t2-"></a>JoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>と<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>クラスが入力要素を収集し、それを反映<xref:System.Tuple%602?displayProperty=fullName>または<xref:System.Tuple%603?displayProperty=fullName>をそれらの要素を含むオブジェクト\</T1, T2, T3>\</T1, T2>\</T1, T2, T3>\</T1, T2>。 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>と<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>からクラスを継承しない<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.</T1, T2, T3> </T1, T2> 代わりに、プロパティを提供する<xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target1%2A>、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602.Target2%2A>、および<xref:System.Threading.Tasks.Dataflow.JoinBlock%603.Target3%2A>を実装する<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>します。  
  
 ような<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>と<xref:System.Threading.Tasks.Dataflow.JoinBlock%603> 、最長一致モードまたは最短一致モードで動作します</T1, T2, T3></T1, T2>。 既定では最長一致モードで、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>または<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>オブジェクトが提供され、各ターゲットには、少なくとも&1; つのメッセージを受信した後、タプルを伝達して、すべてのメッセージを受け取り</T1, T2, T3></T1, T2>。 最短一致モードで、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>または<xref:System.Threading.Tasks.Dataflow.JoinBlock%603>タプルを作成するために必要なデータがすべてのターゲットに提供されるまで、オブジェクトがすべての受信メッセージを延期します\</T1, T2, T3>\</T1, T2>。 この時点で、ブロックは&2; フェーズ コミット プロトコルによって、ソースからすべての必要な項目をアトミックに取得します。 この延期により、他のエンティティは当面の間データを使用でき、システム全体が進行できます。  
  
 次の基本的な例をケースを示しています、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603>オブジェクトが複数のデータ値を計算する必要があります</T1, T2, T3>。 この例で作成、 <xref:System.Threading.Tasks.Dataflow.JoinBlock%603>&2; を必要とするオブジェクト<xref:System.Int32>値と<xref:System.Char>算術演算を実行するために\</T1, T2, T3>。  
  
 [!code-csharp[TPLDataflow_Overview#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#8)]
 [!code-vb[TPLDataflow_Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#8)]  
  
 使用するコード例全体について<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>協調的なリソースを共有する最短一致モードでのオブジェクトを参照してください[方法: JoinBlock を使用して複数のソースからのデータ読み取りに](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)\</T1, T2>。  
  
#### <a name="batchedjoinblockt1-t2-"></a>BatchedJoinBlock(T1, T2, ...)  
 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>と<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%603>クラスは入力要素のバッチを収集し、それを反映`System.Tuple(IList(T1), IList(T2))`または`System.Tuple(IList(T1), IList(T2), IList(T3))`をそれらの要素を含むオブジェクト\</T1, T2, T3>\</T1, T2>。 考えてみてください<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>の組み合わせとして<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>と<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>.</T1, T2> </T1, T2> 作成するときに、各バッチのサイズを指定する<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>オブジェクト\</T1, T2>。 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>プロパティも提供<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A>と<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>を実装する<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>します。\</T1, T2> 指定した数の入力要素がすべてのターゲット間でから受信したときに、 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>オブジェクトは非同期的に伝達、`System.Tuple(IList(T1), IList(T2))`をそれらの要素を含むオブジェクト\</T1, T2>。  
  
 次の基本的な例を作成し、 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 、結果を保持するオブジェクト<xref:System.Int32>値、およびエラーである<xref:System.Exception>のオブジェクト</T1, T2>。 この例は、複数の操作を実行し、結果を書き込む、 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target1%2A>プロパティ、およびエラーを<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602.Target2%2A>プロパティの<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>オブジェクト\</T1, T2>。 操作の成功と失敗の数はわからないため、事前に、 <xref:System.Collections.Generic.IList%601>オブジェクトは、0 個以上の値を受け取り、各ターゲットを有効にします。  
  
 [!code-csharp[TPLDataflow_Overview#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_overview/cs/program.cs#9)]
 [!code-vb[TPLDataflow_Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_overview/vb/program.vb#9)]  
  
 使用するコード例全体について<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>結果と、プログラムがデータベースから読み取るときに発生したすべての例外の両方をキャプチャするを参照してください[チュートリアル: BatchBlock および BatchedJoinBlock 効率の向上に使用](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)。\</T1, T2> 。  
  
 [[go to top](#top)]  
  
<a name="behavior"></a>   
## <a name="configuring-dataflow--block-behavior"></a>データフロー ブロックの動作を構成する  
 提供することによって追加のオプションを有効にすることができます、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=fullName>データ フロー ブロックの型のコンス トラクターにオブジェクトです。 これらのオプションは、基になるタスクと並列化の次数を管理するスケジューラなどの動作を制御します。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>派生は、特定のデータ フロー ブロックの型に固有の動作を指定する型があります。 各データ フロー ブロックの型に関連付けられているオプション型の概要を次の表に示します。  
  
|データ フロー ブロックの型|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>型|  
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>|<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>\</TInput, TOutput>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>\</TInput, TOutput>|<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>\</T1, T2>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
|<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>\</T1, T2>|<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>|  
  
 ブロックのオプションで使用可能な重要なデータ フローに関する追加情報を提供する次のセクションで、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions?displayProperty=fullName>、 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions?displayProperty=fullName>、および<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions?displayProperty=fullName>クラスです。  
  
### <a name="specifying-the-task-scheduler"></a>タスク スケジューラの指定  
 すべての定義済みのデータ フロー ブロックは TPL タスク スケジューリング メカニズムを使って、ターゲットへのデータの伝達、ソースからのデータの受け取り、データが使用可能になったときのユーザー定義のデリゲートの実行、などのアクティビティを実行します。 <xref:System.Threading.Tasks.TaskScheduler>タスクのスレッドにキューに配置するタスク スケジューラを表す抽象クラスです。 既定のタスク スケジューラ<xref:System.Threading.Tasks.TaskScheduler.Default%2A>を使用して、 <xref:System.Threading.ThreadPool>クラスをキューにして、作業を実行します。 既定のタスク スケジューラを設定して上書きできます、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>プロパティのデータ フロー ブロック オブジェクトを構築するとき。  
  
 同じタスク スケジューラが複数のデータ フロー ブロックを管理する場合、それらにポリシーを強制的に適用できます。 たとえば、複数のデータ フロー ブロックはそれぞれ同じの排他スケジューラを対象とする構成<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>オブジェクトに、これらのブロックにわたって実行をシリアル化するすべての作業です。 同様に、これらのブロックが同一の同時スケジューラをターゲットに構成されている場合<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>オブジェクト、およびそのスケジューラが設定されている最大同時実行レベルは、これらのブロックのすべての操作が同時操作の数に制限されます。 使用する例については、 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>を並列で発生しますが、書き込み操作に他のすべての操作ののみ発生する可能性は、「の読み取り操作を有効にするクラス[方法: データフロー ブロックでタスク スケジューラを指定する](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)です。 TPL のタスク スケジューラに関する詳細については、次を参照してください。、 <xref:System.Threading.Tasks.TaskScheduler>クラスに関するトピック。  
  
### <a name="specifying-the-degree-of-parallelism"></a>並列化の次数の指定  
 既定では、TPL データフロー ライブラリが提供する&3; つの実行ブロックの型<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>、一度に&1; つのメッセージを処理します\</TInput, TOutput>\</TInput, TOutput>。 これらのデータ フロー ブロックの型は、メッセージを受け取った順番でそれを処理します。 これらのデータ フロー ブロックがメッセージを同時に処理を有効にするには設定、 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=fullName>プロパティのデータ フロー ブロック オブジェクトを構築するとき。  
  
 既定値の<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>は 1 で、データ フロー ブロックが一度に 1 つのメッセージを処理することを保証します。 このプロパティに 1 を超える値に設定すると、データ フロー ブロックは複数のメッセージを同時に処理できます。 このプロパティを設定<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=fullName>により、基になるタスク スケジューラは最大同時実行の程度を管理します。  
  
> [!IMPORTANT]
>  並列処理の最大範囲に 1 を超える数を指定すると、複数のメッセージを同時に処理するため、メッセージが受信した順序で処理されない場合があります。 ただし、ブロックからメッセージが出力される順序は正しく並べ替えられます。  
  
 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>プロパティは並列処理の最大限度を表しますは、データ フロー ブロックは、指定より低い並列化の度合いで実行可能性があります。 機能要件を満たすため、または使用可能なシステム リソースの不足のため、データ フロー ブロックは、より低い並列化の度合いを使う場合があります。 データ フロー ブロックは、指定より大きな並列化を選択することはありません。  
  
 値、 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>プロパティは、各データ フロー ブロックのオブジェクトに排他的です。 たとえば、4 つのデータ フロー ブロックのオブジェクトが並列処理の最大範囲にそれぞれ 1 を指定した場合、4 つすべてのデータ フロー ブロック オブジェクトを並列に実行できる場合もあります。  
  
 例の並列で実行する時間のかかる操作を有効にする並列処理の最大限度を設定する場合は、次を参照してください。[方法: データフロー ブロックで並列処理の次数を指定](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)します。  
  
### <a name="specifying-the-number-of-messages-per-task"></a>タスクごとのメッセージ数の指定  
 定義済みのデータ フロー ブロックの型は、複数の入力要素を処理するタスクを使用します。 これによって、データを処理するために必要なタスクのオブジェクトの数を最小限に抑えることができ、アプリケーションを効率的に実行できます。 ただし、一連のデータ フロー ブロックのタスクがデータを処理する場合、他のデータ フロー ブロックのタスクはメッセージをキューに置いて処理の時間を待機する必要がある場合があります。 データ フロー タスク間での高い公平性を有効にするには設定、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>プロパティです。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>に設定されている<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded?displayProperty=fullName>、既定値は、データ フロー ブロックが使用するタスクが、使用可能な限り多くのメッセージを処理します。 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>以外の値に設定されて<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.Unbounded>、最大でこのあたりのメッセージの数を処理、データ フロー ブロック<xref:System.Threading.Tasks.Task>オブジェクトです。 設定が、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.MaxMessagesPerTask%2A>プロパティは、タスク間で公平性を向上できますその場合は、必要以上のタスクを作成するには、システムがあり、パフォーマンスが低下することができます。  
  
### <a name="enabling-cancellation"></a>取り消しの有効化  
 TPL はタスクが協調的な方法によって取り消しの調整をできる機構を提供します。 この取り消し機構に参加するデータフロー ブロックを有効にするには設定、 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティです。 ときにこの<xref:System.Threading.CancellationToken>オブジェクトが取り消された状態に設定されている場合、このトークンを監視するすべてのデータ フロー ブロックは、現在の項目の実行を完了しますが、後続の項目は開始されません。 また、これらのデータ フロー ブロックはすべてのバッファリングされたメッセージをクリアし、すべてのソースとターゲット ブロックへの接続を解放し、取り消し状態に遷移します。 取り消し状態に遷移すると、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Completion%2A>プロパティには、<xref:System.Threading.Tasks.Task.Status%2A>プロパティに設定<xref:System.Threading.Tasks.TaskStatus>処理中に例外が発生した場合を除き、します。 その場合は、<xref:System.Threading.Tasks.Task.Status%2A>に設定されている<xref:System.Threading.Tasks.TaskStatus>します。  
  
 例については、Windows フォーム アプリケーションで取り消しを使用する方法については、次を参照してください。[方法: データフロー ブロックをキャンセル](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)します。 TPL での取り消し処理の詳細については、次を参照してください。[タスクのキャンセル](../../../docs/standard/parallel-programming/task-cancellation.md)します。  
  
### <a name="specifying-greedy-versus-non-greedy-behavior"></a>最長一致と最短一致の動作の指定  
 複数のグループ化データ フロー ブロックの型は、どちらかで動作できる*最長一致*または*最短*モードです。 既定では、定義済みのデータ フロー ブロックの型は、最長一致モードで動作します。  
  
 結合などのブロック<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>、最長一致モードでは、結合に使用する、対応するデータがまだ使用できない場合でも、ブロックがそのデータを即座に受け入れることを意味します</T1, T2>。 最短一致モードは、ターゲットのそれぞれで結合が完了できるように使用可能になるまで、ブロックがすべての受信メッセージを延期することを意味します。 延期されたメッセージのいずれかが使用できなくなった場合、結合ブロックは延期されたすべてのメッセージを解放し、プロセスを再起動します。 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>クラス、最長一致と最短一致の動作は似ていますが、最短一致モードでは、下にあることを除いて、 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>オブジェクトが、バッチを完了する別のソースから利用可能なために十分なするまで、すべての受信メッセージを延期します。  
  
 データ フロー ブロックに最短一致モードを指定する<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A>に`False`します。 例については、最短一致モードを使用して、データ ソースをより効率的に共有する複数の結合ブロックを有効にする方法については、次を参照してください。[方法: JoinBlock を使用して複数のソースからのデータ読み取りを](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)します。  
  
 [[go to top](#top)]  
  
<a name="custom"></a>   
## <a name="custom-dataflow-blocks"></a>カスタム データ フロー ブロック  
 TPL データ フロー ライブラリは多くの定義済みブロックの型を提供しますが、カスタム動作を実行する追加のブロックの型を作成できます。 実装、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>または<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>インターフェイスを直接またはを使用して、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>既存のブロックの型の動作をカプセル化する複雑なブロックを構築するメソッド\</TInput, TOutput>。 カスタム データ フロー ブロックの機能を実装する方法を示す例については、次を参照してください。[チュートリアル: カスタム データフロー ブロックの型を作成する](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)です。  
  
 [[go to top](#top)]  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[方法: メッセージを書き込むし、データ フロー ブロックからメッセージを読み取る](../../../docs/standard/parallel-programming/how-to-write-messages-to-and-read-messages-from-a-dataflow-block.md)|メッセージを書き込むし、メッセージを読み取る方法を示しています、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトです。|  
|[方法: プロデューサー/コンシューマーのデータフロー パターンを実装します。](../../../docs/standard/parallel-programming/how-to-implement-a-producer-consumer-dataflow-pattern.md)|データ フロー モデルを使ってプロデューサー/コンシューマー パターンを実装し、プロデューサーがデータ フロー ブロックにメッセージを送信して、コンシューマーがそのブロックからメッセージを読み取る方法を示します。|  
|[方法: データフロー ブロックがデータを受信すると、操作を実行](../../../docs/standard/parallel-programming/how-to-perform-action-when-a-dataflow-block-receives-data.md)|実行データ フロー ブロックの型にデリゲートを提供する方法について説明<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>、および<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>.\</TInput, TOutput> \</TInput, TOutput>|  
|[チュートリアル: データフロー パイプラインの作成](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)|Web からテキストをダウンロードし、そのテキストの操作を実行する、データ フロー パイプラインを作成する方法について説明します。|  
|[方法: データフロー ブロックのリンクを解除](../../../docs/standard/parallel-programming/how-to-unlink-dataflow-blocks.md)|使用する方法を示しています、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>ソースをターゲットにメッセージを提供した後、ソースからターゲット ブロックのリンクを解除するメソッドです。|  
|[チュートリアル: Windows フォーム アプリケーションでのデータ フローの使用](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)|Windows フォーム アプリケーションでイメージ処理を実行する、データ フロー ブロックのネットワークを作成する方法を示します。|  
|[方法: データフロー ブロックをキャンセル](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)|Windows フォーム アプリケーションで取り消しを使う方法を説明します。|  
|[方法: JoinBlock を使用して、複数のソースからデータを読み取る](../../../docs/standard/parallel-programming/how-to-use-joinblock-to-read-data-from-multiple-sources.md)|使用する方法について説明します<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>最短一致モードを使用して、データ ソースをより効率的に共有する複数の結合ブロックを有効にする方法と、複数のソースからデータがある場合、操作を実行するクラス\</T1, T2>。|  
|[方法: データフロー ブロックで並列処理の次数を指定](../../../docs/standard/parallel-programming/how-to-specify-the-degree-of-parallelism-in-a-dataflow-block.md)|設定する方法について説明します、 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A>プロパティを同時に複数のメッセージを処理する、実行データフロー ブロックを有効にします。|  
|[方法: データフロー ブロックでタスク スケジューラを指定します。](../../../docs/standard/parallel-programming/how-to-specify-a-task-scheduler-in-a-dataflow-block.md)|アプリケーションでデータ フローを使用する場合に特定のタスク スケジューラを関連付ける方法を示します。|  
|[チュートリアル: BatchBlock および BatchedJoinBlock を効率を向上させるために使用します。](../../../docs/standard/parallel-programming/walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency.md)|使用する方法について説明します<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>データベースの効率を向上させるためにクラスの挿入操作、および使用する方法、 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>結果と、プログラムがデータベースから読み取るときに発生したすべての例外の両方をキャプチャするクラス\</T1, T2>。|  
|[チュートリアル: カスタム データフロー ブロックの型を作成します。](../../../docs/standard/parallel-programming/walkthrough-creating-a-custom-dataflow-block-type.md)|カスタム動作を実装するデータ フロー ブロックの型を作成する&2; とおりの方法を示します。|  
|[タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アプリケーションの並列処理と並列プログラミングを簡略化するライブラリである TPL を紹介します。|