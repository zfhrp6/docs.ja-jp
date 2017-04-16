---
title: "How to: Use JoinBlock to Read Data From Multiple Sources | Microsoft Docs"
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
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, joining blocks in"
  - "dataflow blocks, joining in TPL"
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Use JoinBlock to Read Data From Multiple Sources
データを複数のソースから使用できる場合は、このドキュメントにアクションを実行するために <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> クラスを使用する方法を示します。  、複数を有効にするには、非最長一致モードを使用する方法を示します。データ ソースを効率的に共有するブロックを示します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## 使用例  
 次の例では、リソースが使用できるようになると 3 リソースの種類、`NetworkResource`、`FileResource`と `MemoryResource`を定義し、操作を実行したものです。  この例では、最初の操作と 2 番目の操作を実行するに `FileResource` と `MemoryResource` のペアを実行するに `NetworkResource` と `MemoryResource` のペアが必要です。  必要なすべてのリソースを使用するときに、これらの操作を実行できるようにするため、この例では <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> クラス。  <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> オブジェクトはすべてのソースからデータを受け取ると、この例の <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトであるターゲットにそのデータを反映させます。  `MemoryResource` の共有プールから読み取り <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> オブジェクトは、どちらも表示します。  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 `MemoryResource` オブジェクトの共有プールを効率的に使用できるようにするために、この例では、非最長一致モードで動作する <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> オブジェクトを作成する `False` に <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> のプロパティ セットを持つ <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> オブジェクトを示します。  最短一致の結合ブロックは 1 が各ソースから使用できるようになるまですべての受信メッセージを遅らせます。  遅延メッセージのいずれかが別のブロックを受け入れた場合は、join ブロックはプロセスを再起動します。  非最長一致モードを有効にする他のブロックとしてある場合にデータを待たせる一つ以上のソース ブロックを共有するブロックを結合します。  この例では、`MemoryResource` オブジェクトが `memoryResources` のプールに追加した場合、1 番目と 2 番目のデータ ソースを受け取るようにブロックを前方作業を進めることができます。  この例では、既定では最長一致のモードを使用すると、1 がブロックを `MemoryResource` オブジェクトを受け取り、使用できるようにするには、2 番目のリソースを待機することがあります結合します。  ただし、他の `MemoryResource` join オブジェクトが他に結合するブロックを以降にブロックに使用できる 2 番目のデータ ソースがある場合は行うことができません。  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DataflowNonGreedyJoin.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DataflowNonGreedyJoin.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## 信頼性の高いプログラミング  
 最短一致の結合の使用は、アプリケーションでデッドロックを防止できます。  ソフトウェア アプリケーションで、2 つ以上のプロセスがそれぞれリソースを確保し、別のプロセスがリソースを解放するのをお互いに待機すると、*デッドロック*が発生します。  <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> の 2 種類のオブジェクトを定義するアプリケーションがあるとします。  オブジェクトは、それぞれ 2 とおりの共有ソース ブロックからデータを読み取ります。  最長モードでは、この 1 つが join ブロックは最初のソースから読み取り、リソースを解放するために両方のブロックを相互に待機する他を結合するため、2 番目は、二つ目のソースからブロックを読み取り、アプリケーション デッドロックの可能性がある結合します。  非最長一致モードでは、各ソースからは、すべてのデータを使用して、デッドロックの危険性が削除された場合だけブロックを読み取ります結合します。  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)