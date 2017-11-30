---
title: "方法: JoinBlock を使用して複数のソースからデータを読み込む"
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
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41445e4874b94809840ecf9ebda6f27ccc955c9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>方法: JoinBlock を使用して複数のソースからデータを読み込む
このドキュメントの使用方法を説明します、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>クラスを複数のソースからデータがある場合、操作を実行します。 最短一致モードを使用して、データ ソースをより効率的に共有する複数の結合ブロックを有効にする方法も示します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="example"></a>例  
 次の例では、次の 3 つのリソースの種類、 `NetworkResource`、 `FileResource`、および`MemoryResource`、し、リソースが使用可能になるときに、操作を実行します。 この例は、`NetworkResource`と`MemoryResource`最初の操作を実行するためにペアと`FileResource`と`MemoryResource`ペアが 2 番目の操作を実行するためにします。 この例ではすべての必要なリソースが利用可能なときに発生するこれらの操作を有効にする、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>クラスです。 ときに、<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>オブジェクトは、すべてのソースからデータを受け取るをターゲットにあり、この例では、そのデータを伝達する<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>オブジェクト。 両方<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>の共有プールからオブジェクトを読み取る`MemoryResource`オブジェクト。  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 共有プールの効率的な使用を有効にする`MemoryResource`オブジェクトをこの例で指定、<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions>を持つオブジェクト、<xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A>プロパティに設定`False`を作成する<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>最短一致モードで動作するオブジェクト。 最短一致の結合ブロックは、各ソースから 1 つが読み取られるまで、すべての受信メッセージを延期します。 延期されたメッセージのいずれかが別のブロックによって受け入れられて、結合ブロックは、プロセスを再起動します。 最短一致モードでは、共有する他のブロックがデータを待つ進行する 1 つまたは複数のソース ブロックの結合ブロックを有効します。 この例では場合、`MemoryResource`にオブジェクトが追加、`memoryResources`プール、最初の結合が 2 番目のデータ ソースを受信するブロックが進行することができます。 この例では、最長一致モードを使用したは、既定では、1 つの結合ブロックがかかると、`MemoryResource`オブジェクトし、第 2 のリソース使用可能になるまで待機します。 ただし、他の結合ブロックに使用可能な 2 番目のデータ ソースがある場合は、ことはできません進行のため、`MemoryResource`オブジェクトが、その他の結合ブロックによって取得されています。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowNonGreedyJoin.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowNonGreedyJoin.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 最短一致の結合の使用は、アプリケーションでデッドロックを防止できます。 ソフトウェア アプリケーションで*デッドロック*2 つ以上のプロセスの各リソースを保持して、その他のリソースを解放する別のプロセスをお互いに待機するときに発生します。 2 つを定義するアプリケーションを考えてみます<xref:System.Threading.Tasks.Dataflow.JoinBlock%602>オブジェクト。 両方のオブジェクトは各は、次の 2 つの共有ソース ブロックからデータを読み取ります。 最長一致モードで場合は、最初のソースから 1 つの結合ブロックを読み取り、2 番目のソースから 2 番目の結合ブロックを読み取りでアプリケーションのリソースを解放する、他の両方の結合ブロックが相互に待機するためデッドロック可能性があります。 最短一致モードで各結合ブロックのすべてのデータが、使用可能な場合にのみ、そのソースおよびそのため、デッドロックの危険性からの読み取りが排除されます。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
