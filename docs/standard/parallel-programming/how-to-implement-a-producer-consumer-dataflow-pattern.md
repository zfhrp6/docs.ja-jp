---
title: "方法: プロデューサー/コンシューマーのデータフロー パターンを実装する"
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
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="42e61-102">方法: プロデューサー/コンシューマーのデータフロー パターンを実装する</span><span class="sxs-lookup"><span data-stu-id="42e61-102">How to: Implement a Producer-Consumer Dataflow Pattern</span></span>
<span data-ttu-id="42e61-103">このドキュメントでは、TPL データフロー ライブラリを使用して、プロデューサー/コンシューマー パターンを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="42e61-103">This document describes how to use the TPL Dataflow Library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="42e61-104">このパターンでは、"*プロデューサー*" がメッセージをメッセージ ブロックに送信し、"*コンシューマー*" がそのブロックからメッセージを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="42e61-104">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="42e61-105">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="42e61-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="42e61-106">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="42e61-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42e61-107">例</span><span class="sxs-lookup"><span data-stu-id="42e61-107">Example</span></span>  
 <span data-ttu-id="42e61-108">次の例では、データフローを使用する基本的なプロデューサー/コンシューマー モデルを示します。</span><span class="sxs-lookup"><span data-stu-id="42e61-108">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="42e61-109">`Produce`メソッドは、データのランダム バイトを含む配列を書き込みます、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType>オブジェクトおよび`Consume`メソッドがからバイトを読み取り、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="42e61-109">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="42e61-110">操作を実行して、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>と<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>その派生型ではなく、インターフェイスのさまざまなデータ フロー ブロックの型で動作できる再利用可能なコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="42e61-110">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="42e61-111">この例では、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスです。</span><span class="sxs-lookup"><span data-stu-id="42e61-111">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="42e61-112"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601>クラスは、両方のソースとして機能をブロックし、ターゲット ブロック、プロデューサーおよびコンシューマーを使用して、共有されたオブジェクト データを転送します。</span><span class="sxs-lookup"><span data-stu-id="42e61-112">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>  
  
 <span data-ttu-id="42e61-113">`Produce`メソッドの呼び出し、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>ターゲット ブロックにデータを同期的に記述するループ内のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="42e61-113">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="42e61-114">後に、`Produce`メソッドは呼び出しのターゲット ブロックにすべてのデータを書き込みます、<xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>を示す、ブロックが使用可能なその他のデータを持つことはありません。</span><span class="sxs-lookup"><span data-stu-id="42e61-114">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="42e61-115">`Consume`メソッドを使用、 [async](~/docs/csharp/language-reference/keywords/async.md)と[await](~/docs/csharp/language-reference/keywords/await.md)演算子 ([Async](~/docs/visual-basic/language-reference/modifiers/async.md)と[Await](~/docs/visual-basic/language-reference/operators/await-operator.md)で[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) に非同期的にから受信されるバイトの合計数を計算、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="42e61-115">The `Consume` method uses the [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) operators ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="42e61-116">非同期的に動作する、`Consume`メソッドの呼び出し、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>メソッド、ソース ブロックがあり、使用可能なデータと、ソース ブロックには使用可能なその他のデータはないときに通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="42e61-116">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42e61-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="42e61-117">Compiling the Code</span></span>  
 <span data-ttu-id="42e61-118">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowProducerConsumer.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowProducerConsumer.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="42e61-118">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="42e61-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span><span class="sxs-lookup"><span data-stu-id="42e61-119">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="42e61-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span><span class="sxs-lookup"><span data-stu-id="42e61-120">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="42e61-121">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="42e61-121">Robust Programming</span></span>  
 <span data-ttu-id="42e61-122">この例では、1 つのコンシューマーのみを使用してソース データを処理します。</span><span class="sxs-lookup"><span data-stu-id="42e61-122">This example uses just one consumer to process the source data.</span></span> <span data-ttu-id="42e61-123">アプリケーションで複数のコンシューマーがあればを使用して、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドを次の例で示すように、ソース ブロックからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="42e61-123">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <span data-ttu-id="42e61-124"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>メソッドを返します。`False`データが使用できない場合。</span><span class="sxs-lookup"><span data-stu-id="42e61-124">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="42e61-125">このメカニズムでは、データは、呼び出しの後に引き続き使用できます保証複数のコンシューマーは、ソース ブロックを同時にアクセスする必要がある場合、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>です。</span><span class="sxs-lookup"><span data-stu-id="42e61-125">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e61-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="42e61-126">See Also</span></span>  
 [<span data-ttu-id="42e61-127">データフロー</span><span class="sxs-lookup"><span data-stu-id="42e61-127">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
