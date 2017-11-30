---
title: "チュートリアル: カスタム データフロー ブロックの型の作成"
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
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 809b21fa6e1470890011604792d849998dd03ede
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a><span data-ttu-id="f38dc-102">チュートリアル: カスタム データフロー ブロックの型の作成</span><span class="sxs-lookup"><span data-stu-id="f38dc-102">Walkthrough: Creating a Custom Dataflow Block Type</span></span>
<span data-ttu-id="f38dc-103">TPL データ フロー ライブラリは、さまざまな機能を有効にするいくつかのデータ フロー ブロックの型を提供しますが、カスタムのブロックの型を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f38dc-103">Although the TPL Dataflow Library provides several dataflow block types that enable a variety of functionality, you can also create custom block types.</span></span> <span data-ttu-id="f38dc-104">このドキュメントでは、カスタム動作を実装するデータフロー ブロックの型を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-104">This document describes how to create a dataflow block type that implements custom behavior.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f38dc-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f38dc-105">Prerequisites</span></span>  
 <span data-ttu-id="f38dc-106">読み取り[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)このドキュメントを読む前にします。</span><span class="sxs-lookup"><span data-stu-id="f38dc-106">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you read this document.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f38dc-107">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="f38dc-107">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="f38dc-108">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="f38dc-108">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="defining-the-sliding-window-dataflow-block"></a><span data-ttu-id="f38dc-109">スライディング ウィンドウのデータ フロー ブロックを定義します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-109">Defining the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="f38dc-110">入力値のバッファリング、スライディング ウィンドウで、出力が必要なデータフロー アプリケーションを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f38dc-110">Consider a dataflow application that requires that input values be buffered and then output in a sliding window manner.</span></span> <span data-ttu-id="f38dc-111">たとえば、{0、1、2、3、4, 5} の入力値と 3 つのウィンドウ サイズは、スライディング ウィンドウのデータ フロー ブロックが生成されます {0、1, 2} の出力配列 {1、2、3}、{2、3、4} と {3, 4, 5}。</span><span class="sxs-lookup"><span data-stu-id="f38dc-111">For example, for the input values {0, 1, 2, 3, 4, 5} and a window size of three, a sliding window dataflow block produces the output arrays {0, 1, 2}, {1, 2, 3}, {2, 3, 4}, and {3, 4, 5}.</span></span> <span data-ttu-id="f38dc-112">次のセクションでは、このカスタム動作を実装するデータフロー ブロックの型を作成する 2 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-112">The following sections describe two ways to create a dataflow block type that implements this custom behavior.</span></span> <span data-ttu-id="f38dc-113">最初の手法を使用して、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>の機能を結合する方法、<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>オブジェクトおよび<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>オブジェクトを 1 つの伝達子ブロックにします。</span><span class="sxs-lookup"><span data-stu-id="f38dc-113">The first technique uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to combine the functionality of an <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object and an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object into one propagator block.</span></span> <span data-ttu-id="f38dc-114">派生するクラスを定義する 2 番目の手法<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>カスタム動作を実行する既存の機能を組み合わせたものとします。</span><span class="sxs-lookup"><span data-stu-id="f38dc-114">The second technique defines a class that derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> and combines existing functionality to perform custom behavior.</span></span>  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="f38dc-115">使用して、スライディング ウィンドウのデータ フロー ブロックを定義するメソッドをカプセル化</span><span class="sxs-lookup"><span data-stu-id="f38dc-115">Using the Encapsulate Method to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="f38dc-116">次の例では、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A>メソッドをターゲットとソースから伝達子ブロックを作成します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-116">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> method to create a propagator block from a target and a source.</span></span> <span data-ttu-id="f38dc-117">伝達子ブロックには、ソース ブロックと受信者およびデータの送信者として機能する、ターゲット ブロックが実行できます。</span><span class="sxs-lookup"><span data-stu-id="f38dc-117">A propagator block enables a source block and a target block to act as a receiver and sender of data.</span></span>  
  
 <span data-ttu-id="f38dc-118">この手法は、カスタム データ フロー機能が必要な追加のメソッド、プロパティ、またはフィールドを提供する型を必要としない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f38dc-118">This technique is useful when you require custom dataflow functionality, but you do not require a type that provides additional methods, properties, or fields.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a><span data-ttu-id="f38dc-119">スライディング ウィンドウのデータ フロー ブロックを定義する IPropagatorBlock から派生します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-119">Deriving from IPropagatorBlock to Define the Sliding Window Dataflow Block</span></span>  
 <span data-ttu-id="f38dc-120">次の例は、`SlidingWindowBlock`クラスです。</span><span class="sxs-lookup"><span data-stu-id="f38dc-120">The following example shows the `SlidingWindowBlock` class.</span></span> <span data-ttu-id="f38dc-121">このクラスから派生<xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602>ソースとデータのターゲットの両方として動作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f38dc-121">This class derives from <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> so that it can act as both a source and a target of data.</span></span> <span data-ttu-id="f38dc-122">前の例のように、`SlidingWindowBlock`クラスは、既存のデータ フロー ブロックの型に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="f38dc-122">As in the previous example, the `SlidingWindowBlock` class is built on existing dataflow block types.</span></span> <span data-ttu-id="f38dc-123">ただし、`SlidingWindowBlock`もクラスで必要なメソッド、 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>、 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>、および<xref:System.Threading.Tasks.Dataflow.IDataflowBlock>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f38dc-123">However, the `SlidingWindowBlock` class also implements the methods that are required by the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, and <xref:System.Threading.Tasks.Dataflow.IDataflowBlock> interfaces.</span></span> <span data-ttu-id="f38dc-124">これらのメソッドをすべて転送は、定義済みのデータ フロー ブロックの型のメンバーに動作します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-124">These methods all forward work to the predefined dataflow block type members.</span></span> <span data-ttu-id="f38dc-125">たとえば、`Post`メソッドへの作業を延期する、`m_target`データ メンバーは、これはでも、<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f38dc-125">For example, the `Post` method defers work to the `m_target` data member, which is also an <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> object.</span></span>  
  
 <span data-ttu-id="f38dc-126">この手法は、カスタム データ フロー機能を必要としも 追加のメソッド、プロパティ、またはフィールドを提供する型が必要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f38dc-126">This technique is useful when you require custom dataflow functionality, and also require a type that provides additional methods, properties, or fields.</span></span> <span data-ttu-id="f38dc-127">たとえば、`SlidingWindowBlock`からも派生<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601>に提供できるように、<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>と<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f38dc-127">For example, the `SlidingWindowBlock` class also derives from <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> so that it can provide the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> and <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A> methods.</span></span> <span data-ttu-id="f38dc-128">`SlidingWindowBlock`クラスが提供することによっても拡張機能を示します、`WindowSize`プロパティで、スライディング ウィンドウ内の要素の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-128">The `SlidingWindowBlock` class also demonstrates extensibility by providing the `WindowSize` property, which retrieves the number of elements in the sliding window.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a><span data-ttu-id="f38dc-129">完全な例</span><span class="sxs-lookup"><span data-stu-id="f38dc-129">The Complete Example</span></span>  
 <span data-ttu-id="f38dc-130">次の例は、このチュートリアルのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="f38dc-130">The following example shows the complete code for this walkthrough.</span></span> <span data-ttu-id="f38dc-131">また、ブロックを書き込みますから読み取り、結果をコンソールに出力するメソッドで、両方スライディング ウィンドウ ブロックを使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-131">It also demonstrates how to use the both sliding window blocks in a method that writes to the block, reads from it, and prints the results to the console.</span></span>  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f38dc-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f38dc-132">Compiling the Code</span></span>  
 <span data-ttu-id="f38dc-133">コード例をコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付けます`SlidingWindowBlock.cs`(`SlidingWindowBlock.vb`の[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) および Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f38dc-133">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `SlidingWindowBlock.cs` (`SlidingWindowBlock.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="f38dc-134">**csc.exe/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span><span class="sxs-lookup"><span data-stu-id="f38dc-134">**csc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="f38dc-135">**vbc.exe/r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span><span class="sxs-lookup"><span data-stu-id="f38dc-135">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll SlidingWindowBlock.vb**</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f38dc-136">次の手順</span><span class="sxs-lookup"><span data-stu-id="f38dc-136">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f38dc-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f38dc-137">See Also</span></span>  
 [<span data-ttu-id="f38dc-138">データフロー</span><span class="sxs-lookup"><span data-stu-id="f38dc-138">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
