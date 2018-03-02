---
title: "チュートリアル: カスタム データフロー ブロックの型の作成"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54882ce5f646e9e790703e0951459a9fceac3bb6
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="d6241-102">チュートリアル: カスタム データフロー ブロックの型の作成</span><span class="sxs-lookup"><span data-stu-id="d6241-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="d6241-103">TPL データ フロー ライブラリには、さまざまな機能が有効になるいくつかのデータフロー ブロックの種類が用意されていますが、カスタム ブロックの種類を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6241-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="d6241-104">このドキュメントでは、カスタム動作を実装するデータフロー ブロックの種類を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6241-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d6241-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d6241-105">Prerequisites</span></span>  
 <span data-ttu-id="d6241-106">[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)に関するページを読んでからこのドキュメントをお読みください。</span><span class="sxs-lookup"><span data-stu-id="d6241-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="d6241-107">スライディング ウィンドウのデータフロー ブロックを定義する</span><span class="sxs-lookup"><span data-stu-id="d6241-107">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="d6241-108">入力値をバッファリングしてからスライディング ウィンドウ方法で出力することを要求するデータフロー アプリケーションを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="d6241-108">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="d6241-109">たとえば、入力値が {0, 1 ,2, 3, 4, 5} でウィンドウ サイズが 3 の場合、スライディング ウィンドウのデータフロー ブロックは {0, 1, 2}、{1, 2, 3 }、{2, 3, 4}、および {3, 4, 5} という出力配列になります。</span><span class="sxs-lookup"><span data-stu-id="d6241-109">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="d6241-110">以下のセクションでは、このカスタム動作を実装するデータフロー ブロックの種類を作成する 2 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6241-110">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="d6241-111">最初の方法では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> メソッドを使用して <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> オブジェクトと <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> オブジェクトの機能を 1 つの伝達子ブロックに結合します。</span><span class="sxs-lookup"><span data-stu-id="d6241-111">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="d6241-112">2 番目の方法では、<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> から派生し、既存の機能を組み合わせてカスタム動作を実行するクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d6241-112">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="d6241-113">カプセル化メソッドを使用してスライディング ウィンドウのデータフロー ブロックを定義する</span><span class="sxs-lookup"><span data-stu-id="d6241-113">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="d6241-114">次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> メソッドを使用して、ターゲットとソースから伝達子ブロックを作成します。</span><span class="sxs-lookup"><span data-stu-id="d6241-114">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="d6241-115">伝達子ブロックを使用すると、ソース ブロックとターゲット ブロックはデータの受信側と送信側として機能します。</span><span class="sxs-lookup"><span data-stu-id="d6241-115">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="d6241-116">この手法は、カスタムのデータフロー機能が必要で、追加のメソッド、プロパティ、またはフィールドを提供する種類は必要ない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d6241-116">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="d6241-117">IPropagatorBlock から派生してスライディング ウィンドウのデータフロー ブロックを定義する</span><span class="sxs-lookup"><span data-stu-id="d6241-117">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="d6241-118">`SlidingWindowBlock` クラスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d6241-118">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="d6241-119">このクラスは <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> から派生しているので、データのソースとターゲットの両方として機能することができます。</span><span class="sxs-lookup"><span data-stu-id="d6241-119">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="d6241-120">前の例と同様に、`SlidingWindowBlock` クラスは既存のデータフロー ブロックの種類に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="d6241-120">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="d6241-121">ただし、`SlidingWindowBlock` クラスは、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>、および <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> インターフェイスで必要なメソッドも実装しています。</span><span class="sxs-lookup"><span data-stu-id="d6241-121">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="d6241-122">これらのメソッドはすべて、処理を定義済みデータフロー ブロックの種類のメンバーに転送します。</span><span class="sxs-lookup"><span data-stu-id="d6241-122">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="d6241-123">たとえば、`Post` メソッドは <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> オブジェクトでもある `m_target` データ メンバーに処理を委任します。</span><span class="sxs-lookup"><span data-stu-id="d6241-123">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="d6241-124">この手法は、カスタムのデータフロー機能が必要で、追加のメソッド、プロパティ、またはフィールドを提供する種類も必要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d6241-124">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="d6241-125">たとえば、`SlidingWindowBlock` クラスは <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> メソッドと <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> メソッドを提供できるように <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> からも派生しています。</span><span class="sxs-lookup"><span data-stu-id="d6241-125">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="d6241-126">`SlidingWindowBlock` クラスには、`WindowSize` プロパティがあることからもその拡張性がわかります。このプロパティを使用すると、スライディング ウィンドウ内の要素の数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d6241-126">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="d6241-127">完全な例</span><span class="sxs-lookup"><span data-stu-id="d6241-127">The Complete Example</span></span>  
 <span data-ttu-id="d6241-128">次の例は、このチュートリアルのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="d6241-128">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="d6241-129">また、ブロックに書き込み、そこから読み取り、結果をコンソールに出力するメソッドで、両方のスライディング ウィンドウ ブロックを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6241-129">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d6241-130">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d6241-130">Compiling the Code</span></span>  
 <span data-ttu-id="d6241-131">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`SlidingWindowBlock.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `SlidingWindowBlock.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d6241-131">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="d6241-132">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="d6241-132">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="d6241-133">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="d6241-133">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  

## <a name="see-also"></a><span data-ttu-id="d6241-134">参照</span><span class="sxs-lookup"><span data-stu-id="d6241-134">See Also</span></span>  
 [<span data-ttu-id="d6241-135">データフロー</span><span class="sxs-lookup"><span data-stu-id="d6241-135">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
