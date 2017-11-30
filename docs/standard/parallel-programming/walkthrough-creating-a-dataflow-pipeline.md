---
title: "チュートリアル: データフロー パイプラインの作成"
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
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d63fb872382bfc0a3ba3b8637c7357ab65c58fbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>チュートリアル: データフロー パイプラインの作成
使用できますが、 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>、 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>、および<xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType>からメッセージを受信するメソッドのソース ブロック、フォームに、メッセージ ブロックを接続することも、*データフロー パイプライン*です。 データフロー パイプラインは一連のコンポーネント、または*データフロー ブロック*より大きな目標を達成する特定のタスクそれぞれを実行します。 データフロー パイプラインのすべてのデータフロー ブロックは、他のデータフロー ブロックからメッセージを受け取ったときに処理を実行します。 これは、自動車製造の組み立てラインに例えることができます。 各車両が組み立てラインを通過する際、あるステーションではフレームを組み立て、次のステーションではエンジンを設置するなどです。 組み立てラインでは、複数の車両を同時に組み立てることができるため、一度に車両全体を組み立てるよりスループットが向上します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
 このドキュメントは、ブックをダウンロードするデータ フロー パイプラインを示します*Homer の The Iliad* web サイトと検索から個々 の単語と一致するテキストを単語を逆方向の最初の単語の文字です。 このドキュメントでは、データフロー パイプラインは、次の手順で構成しています。  
  
1.  パイプラインに参加しているデータフロー ブロックを作成します。  
  
2.  各データフロー ブロックを、パイプラインの次のブロックに接続します。 各ブロックは、入力として、パイプラインの前のブロックの出力を受信します。  
  
3.  各データフロー ブロックでは、前のブロックの終了後、次のブロックで完了状態に設定する継続タスクを作成します。  
  
4.  データをパイプラインの先頭に送信します。  
  
5.  パイプラインの先頭を完了としてマークします。  
  
6.  パイプラインのすべての作業が完了するまで待機します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを開始する前に、「[Dataflow (データフロー)](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)」をお読みください。  
  
## <a name="creating-a-console-application"></a>コンソール アプリケーションの作成  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)] または [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] コンソール アプリケーション プロジェクトを作成します。 System.Threading.Tasks.Dataflow.dll への参照を追加します。  
  
 また、ファイルを作成し、名前を付けます`ReverseWords.cs`(`ReverseWords.vb`の[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、プロジェクトをコンパイルする Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe/r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe/r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 次のコードをプロジェクトに追加して、基本のアプリケーションを作成します。  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>データフロー ブロックの作成  
 次のコードを `Main` メソッドに追加して、パイプラインに参加するデータフロー ブロックを作成します。 次の表は、パイプラインの各メンバーの役割をまとめたものです。  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|メンバー|型|説明|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Web から書籍のテキストをダウンロードします。|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|書籍のテキストを単語の配列に区切ります。|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|単語の配列から短い単語を削除し、結果として得られる単語をアルファベット順に並べ、重複部分を削除します。|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|フィルター処理した単語の配列のコレクションにある全単語のうち、逆方向の単語の配列も発生するものを検索します。|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|単語と、関連する逆方向の単語をコンソールに表示します。|  
  
 この例のデータフロー パイプラインの複数の手順を 1 つの手順に結合することができますが、この例では、大規模なタスクを実行するために複数の独立したデータ フロー タスクを構成する概念を示します。 この例では、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602> を使用して、パイプラインの各メンバーが入力データで操作を実行し、結果をパイプラインの次の手順に送ることができるようにします。 パイプラインの `findReversedWords` のメンバーは、各入力に複数の独立した出力を生成するため、<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> オブジェクトになります。 パイプラインの末尾の `printReversedWords` は、入力で操作を実行しますが、結果を生成しないため、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトになります。  
  
## <a name="forming-the-pipeline"></a>パイプラインの形成  
 各ブロックをパイプラインの次のブロックに接続するには、次のコードを追加します。  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> メソッドを呼び出してソース データフロー ブロックをターゲット データフロー ブロックに接続すると、データが使用可能になったときにソース データフロー ブロックがターゲット ブロックにデータを反映させます。  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="creating-the-completion-tasks"></a>完了タスクの作成  
 すべてのデータを処理した後、各データフロー ブロックが最後の操作を実行できるようにするには、次のコードを追加します。  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 パイプラインを介して完了を反映させるには、各完了タスクで次のデータフロー ブロックを完了状態に設定します。 たとえば、パイプラインの先頭が完了状態に設定されると、残りのバッファーに格納されたメッセージがすべて処理され、その後完了タスクが実行されます。完了タスクでは、パイプラインの 2 番目のメンバーを完了状態に設定します。 同様に、パイプラインの 2 番目のメンバーでバッファーに格納された残りのメッセージがすべて処理され、その後完了タスクが実行されます。完了タスクでは、パイプラインの 3 番目のメンバーを完了状態に設定します。 このプロセスは、パイプラインのすべてのメンバーが完了するまで続行します。 この例では、キーワード `delegate` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Function`) を使用して継続タスクを定義します。  
  
## <a name="posting-data-to-the-pipeline"></a>パイプラインへのデータの送信  
 次のコードを book の URL をポスト追加*Homer の The Iliad*データフロー パイプラインの先頭にします。  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 この例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> を使用して、同期的にパイプラインの先頭にデータを送信します。 データフロー ノードにデータを非同期的に送信する必要がある場合は、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> メソッドを使用します。  
  
## <a name="completing-pipeline-activity"></a>パイプラインのアクティビティの完了  
 パイプラインの先頭を完了済みとしてマークするには、次のコードを追加します。 パイプラインの先頭では、バッファに格納されているすべてのメッセージを処理した後、継続タスクが実行されます。 この継続タスクは、パイプラインを介して完了の状態を反映します。  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 この例では、処理するために 1 つの URL をデータフロー パイプラインを介して送信します。 パイプラインを介して複数の入力を送信する場合は、すべての入力を送信した後に <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> メソッドを呼び出します。 アプリケーションに、適切に定義されたポイントがない (データが使用できなくなっているか、アプリケーションがパイプラインの終了を待つ必要がない) 場合は、この手順を省略できます。  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>パイプラインの終了までの待機  
 パイプラインの終了まで待機するには、次のコードを追加します。 この例では、継続タスクを使用して、パイプラインを介して完了を反映させるため、全体の操作はパイプラインの末尾が終了したときに終了します。  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 データフローの完了は、いずれかのスレッドから、または複数のスレッドから同時に待つことができます。  
  
## <a name="the-complete-example"></a>完全な例  
 次の例は、このチュートリアルのコード全体を示しています。  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>次の手順  
 この例では、データフロー パイプラインを介して処理するために 1 つの URL を送信しています。 パイプラインを介して複数の入力値を送信する場合は、自動車工場で部品が通過する方法に似た並列処理の形式をアプリケーションに導入することができます。 パイプラインの最初のメンバーが結果を 2 番目のメンバーに送信する場合、最初のメンバーは、2 番目のメンバーが最初のメンバーの結果を処理するときに、並行して別のアイテムを処理できます。  
  
 データフロー パイプラインを使用して実現される並列処理と呼ばれる*粒度の粗い並列処理*のため、通常、少なくて大きいタスクで構成されます。 詳細を使用することもできます。*粒度の細かい並列処理*データフロー パイプラインのタスクを、より小さく実行時間が短いのです。 この例では、パイプラインの `findReversedWords` メンバーは、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> メソッドを使用して、作業リストの複数の項目を並行して処理します。 粒度の粗いパイプラインで粒度の細かい並列処理を行うと、全体のスループットが向上します。  
  
 作成する複数のターゲット ブロックにソース データフロー ブロックを接続することも、*データフロー ネットワーク*です。 オーバー ロードされたバージョンの <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> メソッドは、ターゲット ブロックがその値に基づいて各メッセージを受け入れるかどうかを定義する <xref:System.Predicate%601> オブジェクトを受け取ります。 ソースとして動作するほとんどのデータフロー ブロック型では、接続されたすべてのターゲット ブロックにメッセージを提供します。これは、いずれかのブロックがそのメッセージを受け入れるまで、ターゲット ブロックが接続された順序で行われます。 このフィルター機構を使用すると、特定のデータはあるパスを通り、その他のデータは別のパスを通るように仕向ける、接続されたデータフロー ブロックの体系を作成することができます。 フィルター処理を使用してデータフロー ネットワークを作成する例は、次を参照してください。[チュートリアル: Windows フォーム アプリケーションでのデータフローの使用](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)です。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
