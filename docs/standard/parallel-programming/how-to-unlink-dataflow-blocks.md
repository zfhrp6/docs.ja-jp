---
title: "方法: データフロー ブロックのリンクを解除する"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db3c0d3a6d94e2e9eb65046267f14feff0c056cb
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="b9266-102">方法: データフロー ブロックのリンクを解除する</span><span class="sxs-lookup"><span data-stu-id="b9266-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="b9266-103">このドキュメントでは、ソースからターゲット データフロー ブロックのリンクを解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9266-103">This document describes how to unlink a target dataflow block from its source.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="b9266-104">例</span><span class="sxs-lookup"><span data-stu-id="b9266-104">Example</span></span>  
 <span data-ttu-id="b9266-105">次の例では、3 つの <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトを作成し、それぞれのオブジェクトが値を計算する `TrySolution` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9266-105">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="b9266-106">この例は、完了させるために、`TrySolution` に対する最初の呼び出しからの結果のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="b9266-106">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="b9266-107">完了した最初の <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> オブジェクトの結果を受信するために、この例では `ReceiveFromAny(T)` メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9266-107">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="b9266-108">`ReceiveFromAny(T)` メソッドは、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトの配列を受け取り、これらの各オブジェクトと <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトをリンクさせます。</span><span class="sxs-lookup"><span data-stu-id="b9266-108">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="b9266-109"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドを使用してソース データフロー ブロックをターゲット ブロックにリンクさせると、データが使用可能になったときにソースがターゲットにメッセージを反映させます。</span><span class="sxs-lookup"><span data-stu-id="b9266-109">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="b9266-110"><xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> クラスは提供される最初のメッセージのみを受け取るため、`ReceiveFromAny(T)` メソッドは <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> メソッドを呼び出して、その結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="b9266-110">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="b9266-111">これにより、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトに提供される最初のメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b9266-111">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="b9266-112"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> メソッドには、<xref:System.Boolean> パラメーターを取得するオーバーロードされたバージョンがあり (`unlinkAfterOne`)、`True` に設定された場合は、ターゲットがソースからメッセージを 1 つ受信した後に、ソース ブロックがターゲットからリンクを解除するように指示します。</span><span class="sxs-lookup"><span data-stu-id="b9266-112">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="b9266-113">ソースの配列と <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトの関係は、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトがメッセージを受信した後は必要なくなるため、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> オブジェクトにはそのソースからリンクを解除することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b9266-113">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="b9266-114">いずれかで値を計算した後に、`TrySolution` への残りの呼び出しを終了できるようにするには、`TrySolution` メソッドは `ReceiveFromAny(T)` への呼び出しが返された後にキャンセルされる、<xref:System.Threading.CancellationToken> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9266-114">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="b9266-115"><xref:System.Threading.SpinWait.SpinUntil%2A> メソッドは、この <xref:System.Threading.CancellationToken> オブジェクトがキャンセルされたときに返されます。</span><span class="sxs-lookup"><span data-stu-id="b9266-115">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9266-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b9266-116">Compiling the Code</span></span>  
 <span data-ttu-id="b9266-117">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowReceiveAny.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowReceiveAny.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b9266-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="b9266-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="b9266-118">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="b9266-119">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="b9266-119">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="b9266-120">参照</span><span class="sxs-lookup"><span data-stu-id="b9266-120">See Also</span></span>  
 [<span data-ttu-id="b9266-121">データフロー</span><span class="sxs-lookup"><span data-stu-id="b9266-121">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
