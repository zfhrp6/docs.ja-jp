---
title: "How to: Implement a Producer-Consumer Dataflow Pattern | Microsoft Docs"
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
  - "TPL dataflow library, implementing producer-consumer pattern"
  - "Task Parallel Library, dataflows"
  - "producer-consumer patterns, implementing [TPL]"
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Implement a Producer-Consumer Dataflow Pattern
このドキュメントでは、プロデューサー\/コンシューマー パターンを実装するために TPL データ フローのライブラリを使用する方法について説明します。  このパターンでは、*プロデューサー*がメッセージをメッセージ ブロックに送信し、*コンシューマー*がそのブロックからメッセージを読み取ります。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## 使用例  
 次の例は、データ フローを使用する基本的な生産者コンシューマー モデルです。  `Produce` のメソッドは <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=fullName> オブジェクトにデータの任意のバイトが含まれ、`Consume` のメソッドが <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=fullName> オブジェクトからバイトを読み取る配列を作成します。  、派生型ではなく <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> と <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> インターフェイスの機能によって、さまざまなデータ フロー ブロック型で動作できる再利用可能なコードを記述できます。  この例では <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスを使用します。  <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスは、ソース ブロックとターゲット ブロックとして機能するため、プロデューサーおよびコンシューマーは転送データの共有オブジェクトを使用できます。  
  
 `Produce` のメソッドの呼び出し同期的にターゲット ブロックにデータを書き込むループの <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> のメソッド。  `Produce` のメソッドはターゲット ブロックにすべてのデータを作成したら、ブロックには使用できる追加データがないことを示すために <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> のメソッドを呼び出します。  `Consume` のメソッドは [async](../Topic/async%20\(C%23%20Reference\).md) と [待機します。](../Topic/await%20\(C%23%20Reference\).md) の演算子 \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の[Async](../Topic/Async%20\(Visual%20Basic\).md) と [待機します。](../Topic/Await%20Operator%20\(Visual%20Basic\).md)\) 非同期的に <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトから受け取ったバイト数の合計を計算します。  ソース ブロックに使用できるデータがある場合に、ソース ブロックには使用できる追加のデータがない場合は、非同期的に機能するには、`Consume` のメソッドの呼び出し通知を受け取る <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> のメソッド。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DataflowProducerConsumer.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DataflowProducerConsumer.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## 信頼性の高いプログラミング  
 この例では、ソース データを処理するために、1 個のコンシューマーを使用します。  アプリケーションで複数のコンシューマーがある場合は、次の例に示すように、ソース ブロックからデータを読み取るために、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> のメソッドを使用します。  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 データを使用できない場合に <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドの戻り `False`。  複数のときにコンシューマーがデータが <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>の呼び出し後にまだ利用できるという保証この機能のソース ブロックに同時にアクセスする必要があります。  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)