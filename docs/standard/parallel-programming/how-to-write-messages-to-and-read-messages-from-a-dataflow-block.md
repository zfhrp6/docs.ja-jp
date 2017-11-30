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
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a><span data-ttu-id="dc353-102">方法: データフロー ブロックに対してメッセージの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="dc353-102">How to: Write Messages to and Read Messages from a Dataflow Block</span></span>
<span data-ttu-id="dc353-103">このドキュメントでは、TPL データフロー ライブラリを使用して、データフロー ブロックとの間でメッセージを読み書きする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dc353-103">This document describes how to use the TPL Dataflow Library to write messages to and read messages from a dataflow block.</span></span> <span data-ttu-id="dc353-104">TPL データフロー ライブラリには、データフロー ブロックへのメッセージの書き込みとデータフロー ブロックからのメッセージの読み取りのための、同期と非同期の両方のメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="dc353-104">The TPL Dataflow Library provides both synchronous and asynchronous methods for writing messages to and reading messages from a dataflow block.</span></span> <span data-ttu-id="dc353-105">このドキュメントでは、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="dc353-105">This document uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="dc353-106"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスがメッセージをバッファーして、メッセージ ソースとして、メッセージのターゲットとしてが動作します。</span><span class="sxs-lookup"><span data-stu-id="dc353-106">The <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class buffers messages and behaves as both a message source and as a message target.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="dc353-107">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="dc353-107">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="dc353-108">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="dc353-108">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a><span data-ttu-id="dc353-109">データフロー ブロックへの同期書き込みとデータフロー ブロックからの同期読み取り</span><span class="sxs-lookup"><span data-stu-id="dc353-109">Writing to and Reading from a Dataflow Block Synchronously</span></span>  
 <span data-ttu-id="dc353-110">次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>メソッドへの書き込みを<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>データフローのブロックと<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>メソッドを同じオブジェクトから読み取る。</span><span class="sxs-lookup"><span data-stu-id="dc353-110">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method to write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dataflow block and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method to read from the same object.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 <span data-ttu-id="dc353-111">使用することも、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>次の例で示すように、データ フロー ブロックの読み取ります。</span><span class="sxs-lookup"><span data-stu-id="dc353-111">You can also use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read from a dataflow block, as shown in the following example.</span></span> <span data-ttu-id="dc353-112"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドは、現在のスレッドをブロックしませんし、場合によってはデータをポーリングする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="dc353-112">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method does not block the current thread and is useful when you occasionally poll for data.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <span data-ttu-id="dc353-113"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>メソッドは同期的に、機能、 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 2 番目のループは、データを読み取る前に、前の例のオブジェクトがすべてのデータを受信します。</span><span class="sxs-lookup"><span data-stu-id="dc353-113">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method acts synchronously, the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in the previous examples receives all data before the second loop reads data.</span></span> <span data-ttu-id="dc353-114">次の例では、最初の例を拡張を使用して<xref:System.Threading.Tasks.Parallel.Invoke%2A>からの読み取りと同時に書き込み、メッセージ ブロックにします。</span><span class="sxs-lookup"><span data-stu-id="dc353-114">The following example extends the first example by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> to read from and write to the message block concurrently.</span></span> <span data-ttu-id="dc353-115"><xref:System.Threading.Tasks.Parallel.Invoke%2A>操作を実行します同時に、値には書き込まれません、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>特定の順序でのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dc353-115">Because <xref:System.Threading.Tasks.Parallel.Invoke%2A> performs actions concurrently, the values are not written to the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in any specific order.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a><span data-ttu-id="dc353-116">データフロー ブロックへの非同期書き込みとデータフロー ブロックからの非同期読み取り</span><span class="sxs-lookup"><span data-stu-id="dc353-116">Writing to and Reading from a Dataflow Block Asynchronously</span></span>  
 <span data-ttu-id="dc353-117">次の例で、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>メソッドを非同期的に書き込む、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>オブジェクトおよび<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>を非同期的に、同じオブジェクトから読み取るメソッドです。</span><span class="sxs-lookup"><span data-stu-id="dc353-117">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method to asynchronously write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method to asynchronously read from the same object.</span></span> <span data-ttu-id="dc353-118">この例では、[async](~/docs/csharp/language-reference/keywords/async.md) 演算子と [await](~/docs/csharp/language-reference/keywords/await.md) 演算子 (Visual basic では [Async](~/docs/visual-basic/language-reference/modifiers/async.md) と [Await](~/docs/visual-basic/language-reference/operators/await-operator.md)) を使用して、ターゲット ブロックへのデータの送信とターゲット ブロックからのデータの読み取りを非同期的に行います。</span><span class="sxs-lookup"><span data-stu-id="dc353-118">This example uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously send data to and read data from the target block.</span></span> <span data-ttu-id="dc353-119"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>メソッドはメッセージを延期するデータフロー ブロックを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc353-119">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method is useful when you must enable a dataflow block to postpone messages.</span></span> <span data-ttu-id="dc353-120"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>メソッドは、そのデータに使用可能な場合にデータを操作する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="dc353-120">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method is useful when you want to act on data when that data becomes available.</span></span> <span data-ttu-id="dc353-121">メッセージ ブロック間でメッセージが伝達されるしくみの詳細については、[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)に関するページの「Message Passing (メッセージ パッシング)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc353-121">For more information about how messages propagate among message blocks, see the section Message Passing in [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a><span data-ttu-id="dc353-122">コード例全体</span><span class="sxs-lookup"><span data-stu-id="dc353-122">A Complete Example</span></span>  
 <span data-ttu-id="dc353-123">次の例は、このドキュメントのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc353-123">The following example shows the complete code for this document.</span></span>  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc353-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="dc353-124">Compiling the Code</span></span>  
 <span data-ttu-id="dc353-125">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowReadWrite.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowReadWrite.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="dc353-125">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReadWrite.cs` (`DataflowReadWrite.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="dc353-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**</span><span class="sxs-lookup"><span data-stu-id="dc353-126">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="dc353-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**</span><span class="sxs-lookup"><span data-stu-id="dc353-127">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="dc353-128">次の手順</span><span class="sxs-lookup"><span data-stu-id="dc353-128">Next Steps</span></span>  
 <span data-ttu-id="dc353-129">この例は、メッセージ ブロックからの読み取りとメッセージ ブロックへの書き込みを直接行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="dc353-129">This example shows how to read from and write to a message block directly.</span></span> <span data-ttu-id="dc353-130">データフロー ブロックを接続して、データフロー ブロックのリニア シーケンスである "*パイプライン*" を作成するか、またはデータフロー ブロックのグラフである "*ネットワーク*" を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc353-130">You can also connect dataflow blocks to form *pipelines*, which are linear sequences of dataflow blocks, or *networks*, which are graphs of dataflow blocks.</span></span> <span data-ttu-id="dc353-131">パイプラインまたはネットワークでは、データが使用可能になると、ソースはターゲットに非同期的にデータを伝達します。</span><span class="sxs-lookup"><span data-stu-id="dc353-131">In a pipeline or network, sources asynchronously propagate data to targets as that data becomes available.</span></span> <span data-ttu-id="dc353-132">基本的なデータフロー パイプラインを作成する例については、「[Walkthrough: Creating a Dataflow Pipeline (チュートリアル: データフロー パイプラインの作成)](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc353-132">For an example that creates a basic dataflow pipeline, see [Walkthrough: Creating a Dataflow Pipeline](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md).</span></span> <span data-ttu-id="dc353-133">さらに複雑なデータフロー ネットワークを作成する例については、「[Walkthrough: Using Dataflow in a Windows Forms Application (チュートリアル: Windows フォーム アプリケーションでのデータフローの使用)](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc353-133">For an example that creates a more complex dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc353-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc353-134">See Also</span></span>  
 [<span data-ttu-id="dc353-135">データフロー</span><span class="sxs-lookup"><span data-stu-id="dc353-135">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
