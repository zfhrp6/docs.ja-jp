---
title: '方法: 単純な Parallel.ForEach ループを記述する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e3fb5fd807971aed014ba98cbb207c4483b93f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581681"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="1d4d0-102">方法: 単純な Parallel.ForEach ループを記述する</span><span class="sxs-lookup"><span data-stu-id="1d4d0-102">How to: Write a Simple Parallel.ForEach Loop</span></span>
<span data-ttu-id="1d4d0-103">この例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループを使用して、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> データ ソースでのデータの並列処理を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d4d0-104">ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="1d4d0-105">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d4d0-106">例</span><span class="sxs-lookup"><span data-stu-id="1d4d0-106">Example</span></span>  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <span data-ttu-id="1d4d0-107"><xref:System.Threading.Tasks.Parallel.ForEach%2A> ループは <xref:System.Threading.Tasks.Parallel.For%2A> ループのように動作します。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-107">A <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A> loop.</span></span> <span data-ttu-id="1d4d0-108">ソース コレクションはパーティション分割され、作業はシステム環境に基づいて複数のスレッドでスケジューリングされます。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-108">The source collection is partitioned and the work is scheduled on multiple threads based on the system environment.</span></span> <span data-ttu-id="1d4d0-109">システムのプロセッサの数が多いほど、並列メソッドの実行が速くなります。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-109">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="1d4d0-110">一部のソース コレクションでは、ソースのサイズや実行される作業の種類に応じて、順次ループがより高速になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-110">For some source collections, a sequential loop may be faster, depending on the size of the source, and the kind of work being performed.</span></span> <span data-ttu-id="1d4d0-111">パフォーマンスの詳細については、「[データとタスクの並列化における注意点](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-111">For more information about performance, see [Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>  
  
 <span data-ttu-id="1d4d0-112">並列ループの詳細については、「[方法: 単純な Parallel.For ループを記述する](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-112">For more information about parallel loops, see [How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>  
  
 <span data-ttu-id="1d4d0-113">非ジェネリック コレクションで <xref:System.Threading.Tasks.Parallel.ForEach%2A> を使用する場合は、次の例に示すように、<xref:System.Linq.Enumerable.Cast%2A> 拡張メソッドを使用して、コレクションをジェネリック コレクションに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-113">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 <span data-ttu-id="1d4d0-114">また、Parallel LINQ (PLINQ) を使用して、<xref:System.Collections.Generic.IEnumerable%601> データ ソースの処理を並列化することもできます。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-114">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="1d4d0-115">PLINQ では、宣言型のクエリ構文を使用して、ループの動作を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-115">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="1d4d0-116">詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-116">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d4d0-117">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1d4d0-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1d4d0-118">このコードをコピーして、Visual Studio 2010 コンソール アプリケーション プロジェクトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-118">Copy and paste this code into a Visual Studio 2010 Console Application project.</span></span>  
  
-   <span data-ttu-id="1d4d0-119">System.Drawing.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-119">Add a reference to System.Drawing.dll</span></span>  
  
-   <span data-ttu-id="1d4d0-120">F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1d4d0-120">Press F5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4d0-121">参照</span><span class="sxs-lookup"><span data-stu-id="1d4d0-121">See Also</span></span>  
 [<span data-ttu-id="1d4d0-122">データの並列化</span><span class="sxs-lookup"><span data-stu-id="1d4d0-122">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="1d4d0-123">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="1d4d0-123">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="1d4d0-124">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1d4d0-124">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
