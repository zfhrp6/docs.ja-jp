---
title: '方法: データフロー ブロックで並列処理の範囲を指定する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4239e57087cc6eb3b644dbcd8d25a0e1adb1ed0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="f5337-102">方法: データフロー ブロックで並列処理の範囲を指定する</span><span class="sxs-lookup"><span data-stu-id="f5337-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="f5337-103">このドキュメントでは、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> プロパティを設定して、実行データフロー ブロックが一度に複数のメッセージを処理できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5337-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="f5337-104">実行時間の長い計算を実行し、並行してメッセージの処理からメリットを得るデータ フロー ブロックがある場合は、これを行うと役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f5337-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="f5337-105">この例では、<xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> クラスを使用して、同時に複数のデータフローの操作を実行しますが、TPL データフロー ライブラリが提供する定義済みの実行ブロック <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>、および <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> のいずれかで並列処理の最大範囲を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f5337-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="f5337-106">例</span><span class="sxs-lookup"><span data-stu-id="f5337-106">Example</span></span>  
 <span data-ttu-id="f5337-107">次の例では、2 つのデータ フローの計算を実行し、それぞれの計算に必要な経過時間を出力します。</span><span class="sxs-lookup"><span data-stu-id="f5337-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="f5337-108">最初の計算では、既定である、並列処理の最大範囲 1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="f5337-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="f5337-109">並列処理の最大範囲 1 を指定すると、データフロー ブロックが順番にメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="f5337-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="f5337-110">2 番目の計算は、使用可能なプロセッサの数に相当する並列処理の最大範囲を指定する点以外は、最初の計算と似ています。</span><span class="sxs-lookup"><span data-stu-id="f5337-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="f5337-111">これにより、データフフロー ブロックは複数の操作を並行して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f5337-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5337-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f5337-112">Compiling the Code</span></span>  
 <span data-ttu-id="f5337-113">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`DataflowDegreeOfParallelism.cs` (Visual Basic では `DataflowDegreeOfParallelism.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f5337-113">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="f5337-114">Visual C#</span><span class="sxs-lookup"><span data-stu-id="f5337-114">Visual C#</span></span>  
  
 <span data-ttu-id="f5337-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="f5337-115">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 <span data-ttu-id="f5337-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5337-116">Visual Basic</span></span>  
  
 <span data-ttu-id="f5337-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="f5337-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f5337-118">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f5337-118">Robust Programming</span></span>  
 <span data-ttu-id="f5337-119">既定では、定義済みの各データフロー ブロックは、メッセージが受信される順序でメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="f5337-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="f5337-120">並列処理の最大範囲に 1 を超える数を指定すると、複数のメッセージが同時に処理されますが、メッセージはそれでも受信した順序で処理されます。</span><span class="sxs-lookup"><span data-stu-id="f5337-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="f5337-121"><xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> プロパティは並列処理の最大範囲を表すため、データ フロー ブロックは、指定より低い並列化の度合いで実行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5337-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="f5337-122">機能要件を満たすため、または使用可能なシステム リソースの不足が原因で、データフロー ブロックは、より小さい並列処理の範囲を使う場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5337-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="f5337-123">データフロー ブロックが、指定より大きな並列処理の範囲を選択することはありません。</span><span class="sxs-lookup"><span data-stu-id="f5337-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5337-124">参照</span><span class="sxs-lookup"><span data-stu-id="f5337-124">See Also</span></span>  
 [<span data-ttu-id="f5337-125">データフロー</span><span class="sxs-lookup"><span data-stu-id="f5337-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
