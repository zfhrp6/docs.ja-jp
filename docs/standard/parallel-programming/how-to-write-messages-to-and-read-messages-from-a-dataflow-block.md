---
title: "How to: Write Messages to and Read Messages from a Dataflow Block | Microsoft Docs"
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
  - "TPL dataflow library, reading and writing messages"
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Write Messages to and Read Messages from a Dataflow Block
このドキュメントでは、メッセージを書き込んでデータ フローのブロックからメッセージを読み取るために TPL データ フローのライブラリを使用する方法について説明します。  TPL データ フローのライブラリには、メッセージをへの書き込み、データ フローのブロックからメッセージを読み取ります。に同期および非同期のメソッドを提供します。  ここでは <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=fullName> クラスを使用します。  <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> クラスはメッセージをバッファーに格納し、メッセージ ソースとターゲット メッセージとして機能します。  
  
> [!TIP]
>  TPL データ フローのライブラリ \(<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> 名前空間\) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。  <xref:System.Threading.Tasks.Dataflow> 名前空間をインストールするには、[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] でプロジェクトを開き、\[プロジェクト\] メニューの **\[NuGet パッケージの管理\]** をクリックし、`Microsoft.Tpl.Dataflow` パッケージをオンラインで検索します。  
  
## への同期的に書き込み、データ フローのブロックから読み取ります。  
 次の例では、同じオブジェクトからの読み取り <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> のデータ フローのブロックと <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドの書き込みに <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> のメソッドを使用します。  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 また、次の例に示すように、データ フローのブロックから、読み取りに <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> のメソッドを使用できます。  <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> のメソッドは、データとしてときどきポーリングするときに現在のスレッドをブロックする場合に便利です。  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> のメソッドが同期的に動作するため、前の例の <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトは、2 番目のループがデータを読み込んだりする前にすべてのデータが表示されます。  次の例では <xref:System.Threading.Tasks.Parallel.Invoke%2A> を使用してから読み取り、メッセージ ブロックに同時に書き込みを行うために最初の例を拡張します。  <xref:System.Threading.Tasks.Parallel.Invoke%2A> が操作を同時に実行するため、これらの値は、特定の順序に <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトに書き込まれません。  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## への非同期的に書き込み、データ フローのブロックから読み取ります。  
 次の例は、非同期的に非同期的に同じからオブジェクトの読み取り <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> オブジェクトと <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> メソッドの書き込みに <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> のメソッドを使用します。  この例では、非同期的にデータを送信し、ターゲット ブロックからデータを読み取るために [async](../Topic/async%20\(C%23%20Reference\).md) と [待機します。](../Topic/await%20\(C%23%20Reference\).md) の演算子 \(Visual Basic で[Async](../Topic/Async%20\(Visual%20Basic\).md) と [待機します。](../Topic/Await%20Operator%20\(Visual%20Basic\).md)\) を使用します。  <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> のメソッドは、データ フローのブロックがメッセージを延期するようにする必要がある場合に便利です。  <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> のメソッドがそのデータが使用できるようになるとデータに適用する場合に便利です。  メッセージをメッセージ ブロック間に反映させるか詳細については、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)セクションのメッセージ パッシングを参照します。  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## 完全なコード例  
 次の例では、このドキュメントの完全なコードを示しています。  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## コードのコンパイル  
 プログラム例をコピーし、Visual Studio のプロジェクトに貼り付けるか、`DataflowReadWrite.cs` \([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]の`DataflowReadWrite.vb`\) という、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行してファイルに貼り付けます。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## 次の手順  
 この例からの読み込みメッセージ ブロックに直接書き込む方法を示します。  データ フローのブロックのリニア シーケンスである、または *ネットワーク*接続してフォームのデータ フローのブロックのグラフである *パイプライン*からデータ フローのブロックを区切ります。  パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。  基本的なデータフロー パイプラインを作成する方法の例については、[Walkthrough: Creating a Dataflow Pipeline](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)を参照してください。  より複雑なデータ フロー ネットワークを作成する例については、[Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)を参照してください。  
  
## 参照  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)