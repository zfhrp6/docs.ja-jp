---
title: "方法: データフロー ブロックに対してメッセージの読み取りと書き込みを行う"
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
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf609a8c350a44fc802cce0ec10693431bbf4f42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>方法: データフロー ブロックに対してメッセージの読み取りと書き込みを行う
このドキュメントでは、TPL データフロー ライブラリを使用して、データフロー ブロックとの間でメッセージを読み書きする方法を説明します。 TPL データフロー ライブラリには、データフロー ブロックへのメッセージの書き込みとデータフロー ブロックからのメッセージの読み取りのための、同期と非同期の両方のメソッドが用意されています。 このドキュメントでは、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>クラスです。 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスがメッセージをバッファーして、メッセージ ソースとして、メッセージのターゲットとしてが動作します。  
  
> [!TIP]
>  TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。 インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>データフロー ブロックへの同期書き込みとデータフロー ブロックからの同期読み取り  
 次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>メソッドへの書き込みを<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>データフローのブロックと<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>メソッドを同じオブジェクトから読み取る。  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 使用することも、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>次の例で示すように、データ フロー ブロックの読み取ります。 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドは、現在のスレッドをブロックしませんし、場合によってはデータをポーリングする場合に便利です。  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>メソッドは同期的に、機能、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 2 番目のループは、データを読み取る前に、前の例のオブジェクトがすべてのデータを受信します。 次の例では、最初の例を拡張を使用して<xref:System.Threading.Tasks.Parallel.Invoke%2A>からの読み取りと同時に書き込み、メッセージ ブロックにします。 <xref:System.Threading.Tasks.Parallel.Invoke%2A>操作を実行します同時に、値には書き込まれません、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>特定の順序でのオブジェクト。  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>データフロー ブロックへの非同期書き込みとデータフロー ブロックからの非同期読み取り  
 次の例で、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>メソッドを非同期的に書き込む、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトおよび<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>を非同期的に、同じオブジェクトから読み取るメソッドです。 この例では、[async](~/docs/csharp/language-reference/keywords/async.md) 演算子と [await](~/docs/csharp/language-reference/keywords/await.md) 演算子 (Visual basic では [Async](~/docs/visual-basic/language-reference/modifiers/async.md) と [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) を使用して、ターゲット ブロックへのデータの送信とターゲット ブロックからのデータの読み取りを非同期的に行います。 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>メソッドはメッセージを延期するデータフロー ブロックを有効にする必要があります。 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>メソッドは、そのデータに使用可能な場合にデータを操作する場合に便利です。 メッセージ ブロック間でメッセージが伝達されるしくみの詳細については、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)に関するページの「Message Passing (メッセージ パッシング)」のセクションを参照してください。  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>コード例全体  
 次の例は、このドキュメントのコード全体を示しています。  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowReadWrite.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowReadWrite.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>次の手順  
 この例は、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを直接行う方法を示しています。 データフロー ブロックを接続して、データフロー ブロックのリニア シーケンスである "*パイプライン*" を作成するか、またはデータフロー ブロックのグラフである "*ネットワーク*" を作成することもできます。 パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。 基本的なデータフロー パイプラインを作成する例については、「[Walkthrough: Creating a Dataflow Pipeline (チュートリアル: データフロー パイプラインの作成)](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)」を参照してください。 さらに複雑なデータフロー ネットワークを作成する例については、「[Walkthrough: Using Dataflow in a Windows Forms Application (チュートリアル: Windows フォーム アプリケーションでのデータフローの使用)](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
