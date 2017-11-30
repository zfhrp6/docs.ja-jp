---
title: "方法: データフロー ブロックのリンクを解除する"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="5e7f1-102">方法: データフロー ブロックのリンクを解除する</span><span class="sxs-lookup"><span data-stu-id="5e7f1-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="5e7f1-103">このドキュメントでは、ターゲット データ フロー ブロックをソースからのリンクを解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-103">This document describes how to unlink a target dataflow block from its source.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="5e7f1-104">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-104">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="5e7f1-105">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-105">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e7f1-106">例</span><span class="sxs-lookup"><span data-stu-id="5e7f1-106">Example</span></span>  
 <span data-ttu-id="5e7f1-107">次の例では、3 つが作成されます<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>呼び出しの各オブジェクト、`TrySolution`値を計算するメソッド。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-107">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="5e7f1-108">この例は、最初の呼び出しからの結果だけを必要と`TrySolution`を完了します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-108">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="5e7f1-109">最初の値を受け取る<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>が完了するとオブジェクトの場合は、この例で定義、`ReceiveFromAny(T)`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-109">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="5e7f1-110">`ReceiveFromAny(T)`メソッドの配列を受け取る<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクトし、これらの各オブジェクトにリンク、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-110">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="5e7f1-111">使用すると、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>ソースをターゲット ブロックにソース データフロー ブロックをリンクするメソッドは、データが利用可能になったにターゲットにメッセージを伝達します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-111">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="5e7f1-112"><xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>クラスは、提供される最初のメッセージだけを受け取り、`ReceiveFromAny(T)`メソッドを呼び出してその結果を生成する、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-112">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="5e7f1-113">これに提供される最初のメッセージが生成されます、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-113">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="5e7f1-114"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドを受け取るオーバー ロードされたバージョンには、<xref:System.Boolean>パラメーター、`unlinkAfterOne`に設定すると`True`ターゲットがソースから 1 つのメッセージを受信した後、ターゲットからリンクを解除するソース ブロックするよう指示します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-114">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="5e7f1-115">必要があります、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>ためにそのソースからリンクを解除するオブジェクト ソースの配列の間のリレーションシップと<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>後にオブジェクトが不要、<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>オブジェクトがメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-115">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="5e7f1-116">残りの呼び出しを有効にする`TrySolution`終了後、値が計算うちの 1 つに、`TrySolution`メソッドは、<xref:System.Threading.CancellationToken>オブジェクトへの呼び出し後に取り消された`ReceiveFromAny(T)`を返します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-116">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="5e7f1-117"><xref:System.Threading.SpinWait.SpinUntil%2A>メソッドが返すときにこの<xref:System.Threading.CancellationToken>オブジェクトが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-117">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e7f1-118">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5e7f1-118">Compiling the Code</span></span>  
 <span data-ttu-id="5e7f1-119">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowReceiveAny.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `DataflowReceiveAny.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e7f1-119">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="5e7f1-120">**csc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="5e7f1-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="5e7f1-121">**vbc.exe/r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="5e7f1-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5e7f1-122">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="5e7f1-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7f1-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e7f1-123">See Also</span></span>  
 [<span data-ttu-id="5e7f1-124">データフロー</span><span class="sxs-lookup"><span data-stu-id="5e7f1-124">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
