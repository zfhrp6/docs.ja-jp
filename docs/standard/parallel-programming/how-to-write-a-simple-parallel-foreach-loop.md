---
title: "方法: 単純な Parallel.ForEach ループを記述する"
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
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="09785-102">方法: 単純な Parallel.ForEach ループを記述する</span><span class="sxs-lookup"><span data-stu-id="09785-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="09785-103">この例を使用する方法を示しています、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>を任意にデータの並列化を有効にするループ<xref:System.Collections.IEnumerable?displayProperty=nameWithType>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>データ ソース。</span><span class="sxs-lookup"><span data-stu-id="09785-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09785-104">ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="09785-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="09785-105">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09785-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09785-106">例</span><span class="sxs-lookup"><span data-stu-id="09785-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="09785-107">A<xref:System.Threading.Tasks.Parallel.ForEach%2A>ループの動作と同様に、<xref:System.Threading.Tasks.Parallel.For%2A>ループします。</span><span class="sxs-lookup"><span data-stu-id="09785-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="09785-108">ソース コレクションがパーティション分割し、システム環境に基づく複数のスレッドで作業をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="09785-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="09785-109">システムのより多くのプロセッサが速ければ速いほど、並列メソッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="09785-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="09785-110">一部のソース コレクションでは、順次ループが、ソース、および実行されている作業の種類のサイズによっては、高速な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="09785-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="09785-111">パフォーマンスの詳細については、次を参照してください[データとタスクの並列化における注意点。](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="09785-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="09785-112">並列ループの詳細については、次を参照してください。[する方法: 単純な Parallel.For ループを記述](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)です。</span><span class="sxs-lookup"><span data-stu-id="09785-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="09785-113">使用する<xref:System.Threading.Tasks.Parallel.ForEach%2A>非ジェネリック コレクションを使用することができますを使用して、<xref:System.Linq.Enumerable.Cast%2A>次の例のように、ジェネリック コレクションにコレクションを変換する拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="09785-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="09785-114">処理を並列化する、Parallel LINQ (PLINQ) を使用することもできます。<xref:System.Collections.Generic.IEnumerable%601>データ ソース。</span><span class="sxs-lookup"><span data-stu-id="09785-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="09785-115">PLINQ では、宣言型のクエリ構文を使用してループを再現することができます。</span><span class="sxs-lookup"><span data-stu-id="09785-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="09785-116">詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09785-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09785-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="09785-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="09785-118">このコードをコピーして、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010年コンソール アプリケーション プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="09785-118">Copy and paste this code into a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="09785-119">System.Drawing.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="09785-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="09785-120">F5 キーを押して</span><span class="sxs-lookup"><span data-stu-id="09785-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09785-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="09785-121">See Also</span></span>  
 [<span data-ttu-id="09785-122">データの並列化</span><span class="sxs-lookup"><span data-stu-id="09785-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="09785-123">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="09785-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="09785-124">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="09785-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
