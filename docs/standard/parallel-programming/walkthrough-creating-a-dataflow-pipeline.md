---
title: "Walkthrough: Creating a Dataflow Pipeline | Microsoft Docs"
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
  - "dataflow pipelines, creating with TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, creating dataflow pipeline"
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Walkthrough: Creating a Dataflow Pipeline
<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=fullName> の各メソッドを使用すると、ソース ブロックからメッセージを受信できますが、メッセージ ブロックに接続して*データフロー パイプライン*を形成することもできます。  データフロー パイプラインは一連のコンポーネント、または*データフロー ブロック*です。それぞれがより大きな目標を達成するための特定のタスクを実行します。  データフロー パイプラインのすべてのデータフロー ブロックは、他のデータフロー ブロックからメッセージを受け取ったときに処理を実行します。  これは、自動車製造の組み立てラインに例えることができます。  各車両が組み立てラインを通過する際、あるステーションではフレームを組み立て、次のステーションではエンジンを設置するなどです。  組み立てラインでは、複数の車両を同時に組み立てることができるため、一度に車両全体を組み立てるよりスループットが向上します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
 このドキュメントでは、Web サイトから書籍『*The Iliad of Homer*』 \(ホメロスのイリアッド\) をダウンロードしてから、個々の単語と一致するテキストを、最初の単語の文字を逆方向にして検索するデータフロー パイプラインについて説明します。  このドキュメントでは、データフロー パイプラインは、次の手順で構成しています。  
  
1.  パイプラインに参加しているデータフロー ブロックを作成します。  
  
2.  各データフロー ブロックを、パイプラインの次のブロックに接続します。  各ブロックは、入力として、パイプラインの前のブロックの出力を受信します。  
  
3.  各データフロー ブロックでは、前のブロックの終了後、次のブロックで完了状態に設定する継続タスクを作成します。  
  
4.  データをパイプラインの先頭に送信します。  
  
5.  パイプラインの先頭を完了としてマークします。  
  
6.  パイプラインのすべての作業が完了するまで待機します。  
  
## 必須コンポーネント  
 このチュートリアルを開始する前に、「[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)」をお読みください。  
  
## コンソール アプリケーションの作成  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)] または [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] コンソール アプリケーション プロジェクトを作成します。  System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
 別の方法として、ファイルを作成し、名前を `ReverseWords.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の場合は `ReverseWords.vb`\) と指定します。続いて、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行して、プロジェクトをコンパイルします。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 次のコードをプロジェクトに追加して、基本のアプリケーションを作成します。  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## データフロー ブロックの作成  
 次のコードを `Main` メソッドに追加して、パイプラインに参加するデータフロー ブロックを作成します。  次の表は、パイプラインの各メンバーの役割をまとめたものです。  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|メンバー|型|説明|  
|----------|-------|--------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Web から書籍のテキストをダウンロードします。|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|書籍のテキストを単語の配列に区切ります。|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|単語の配列から短い単語を削除し、結果として得られる単語をアルファベット順に並べ、重複部分を削除します。|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|フィルター処理した単語の配列のコレクションにある全単語のうち、逆方向の単語の配列も発生するものを検索します。|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|単語と、関連する逆方向の単語をコンソールに表示します。|  
  
 この例のデータフロー パイプラインの複数の手順を 1 つの手順に結合することができますが、この例では、大規模なタスクを実行するために複数の独立したデータ フロー タスクを構成する概念を示します。  この例では、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> を使用して、パイプラインの各メンバーが入力データで操作を実行し、結果をパイプラインの次の手順に送ることができるようにします。  パイプラインの `findReversedWords` のメンバーは、各入力に複数の独立した出力を生成するため、<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> オブジェクトになります。  パイプラインの末尾の `printReversedWords` は、入力で操作を実行しますが、結果を生成しないため、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトになります。  
  
## パイプラインの形成  
 各ブロックをパイプラインの次のブロックに接続するには、次のコードを追加します。  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> メソッドを呼び出してソース データフロー ブロックをターゲット データフロー ブロックに接続すると、データが使用可能になったときにソース データフロー ブロックがターゲット ブロックにデータを反映させます。  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## 完了タスクの作成  
 すべてのデータを処理した後、各データフロー ブロックが最後の操作を実行できるようにするには、次のコードを追加します。  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 パイプラインを介して完了を反映させるには、各完了タスクで次のデータフロー ブロックを完了状態に設定します。  たとえば、パイプラインの先頭が完了状態に設定されると、残りのバッファーに格納されたメッセージがすべて処理され、その後完了タスクが実行されます。完了タスクでは、パイプラインの 2 番目のメンバーを完了状態に設定します。  同様に、パイプラインの 2 番目のメンバーでバッファーに格納された残りのメッセージがすべて処理され、その後完了タスクが実行されます。完了タスクでは、パイプラインの 3 番目のメンバーを完了状態に設定します。  このプロセスは、パイプラインのすべてのメンバーが完了するまで続行します。  この例では、キーワード `delegate` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Function`\) を使用して継続タスクを定義します。  
  
## パイプラインへのデータの送信  
 書籍『*The Iliad of Homer*』\(ホメロスのイリアッド\) の URL をデータフローのパイプラインの先頭に送信するには、次のコードを追加します。  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 この例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=fullName> を使用して、同期的にパイプラインの先頭にデータを送信します。  データフロー ノードにデータを非同期的に送信する必要がある場合は、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=fullName> メソッドを使用します。  
  
## パイプラインのアクティビティの完了  
 パイプラインの先頭を完了済みとしてマークするには、次のコードを追加します。  パイプラインの先頭では、バッファに格納されているすべてのメッセージを処理した後、継続タスクが実行されます。  この継続タスクは、パイプラインを介して完了の状態を反映します。  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 この例では、処理するために 1 つの URL をデータフロー パイプラインを介して送信します。  パイプラインを介して複数の入力を送信する場合は、すべての入力を送信した後に <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=fullName> メソッドを呼び出します。  アプリケーションに、適切に定義されたポイントがない \(データが使用できなくなっているか、アプリケーションがパイプラインの終了を待つ必要がない\) 場合は、この手順を省略できます。  
  
## パイプラインの終了までの待機  
 パイプラインの終了まで待機するには、次のコードを追加します。  この例では、継続タスクを使用して、パイプラインを介して完了を反映させるため、全体の操作はパイプラインの末尾が終了したときに終了します。  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 データフローの完了は、いずれかのスレッドから、または複数のスレッドから同時に待つことができます。  
  
## 完全な例  
 次の例は、このチュートリアルのコード全体を示しています。  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## 次の手順  
 この例では、データフロー パイプラインを介して処理するために 1 つの URL を送信しています。  パイプラインを介して複数の入力値を送信する場合は、自動車工場で部品が通過する方法に似た並列処理の形式をアプリケーションに導入することができます。  パイプラインの最初のメンバーが結果を 2 番目のメンバーに送信する場合、最初のメンバーは、2 番目のメンバーが最初のメンバーの結果を処理するときに、並行して別のアイテムを処理できます。  
  
 データフロー パイプラインを使用して実現されるを並列処理は、*粒度の粗い並列処理*として知られています。これは一般に、より少なくて大きいタスクを構成するためです。  データフロー パイプラインでは、より小さく実行時間の短いタスクによる、より*粒度の細かい並列処理*も行えます。  この例では、パイプラインの `findReversedWords` メンバーは、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> メソッドを使用して、作業リストの複数の項目を並行して処理します。  粒度の粗いパイプラインで粒度の細かい並列処理を行うと、全体のスループットが向上します。  
  
 また、ソース データフロー ブロックを複数のターゲット ブロックに接続すると、*データフロー ネットワーク*を作成することができます。  オーバー ロードされたバージョンの <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> メソッドは、ターゲット ブロックがその値に基づいて各メッセージを受け入れるかどうかを定義する <xref:System.Predicate%601> オブジェクトを受け取ります。  ソースとして動作するほとんどのデータフロー ブロック型では、接続されたすべてのターゲット ブロックにメッセージを提供します。これは、いずれかのブロックがそのメッセージを受け入れるまで、ターゲット ブロックが接続された順序で行われます。  このフィルター機構を使用すると、特定のデータはあるパスを通り、その他のデータは別のパスを通るように仕向ける、接続されたデータフロー ブロックの体系を作成することができます。  フィルター処理を使用してデータフロー ネットワークを作成する例については、「[Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)