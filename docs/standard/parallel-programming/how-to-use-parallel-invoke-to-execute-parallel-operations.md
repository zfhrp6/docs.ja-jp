---
title: '方法: Parallel.Invoke を使用して並列操作を実行する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4b5e005ddd7bbd598a9da3032574eb2ba7dd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="ea491-102">方法: Parallel.Invoke を使用して並列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="ea491-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="ea491-103">この例では、タスク並列ライブラリの <xref:System.Threading.Tasks.Parallel.Invoke%2A> を使用して操作を並列化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea491-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="ea491-104">共有データ ソースで 3 つの操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ea491-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="ea491-105">操作によってソースが変更されるわけではないため、簡単に並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="ea491-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea491-106">ここでは、ラムダ式を使用して TPL でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="ea491-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="ea491-107">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[PLINQ および TPL のラムダ式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea491-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea491-108">例</span><span class="sxs-lookup"><span data-stu-id="ea491-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="ea491-109">なお、<xref:System.Threading.Tasks.Parallel.Invoke%2A> を使用すると、どの操作を同時に実行するかを示すだけで、ランタイムによりすべてのスレッドのスケジュール詳細が処理され、ホスト コンピューター上のコア数も自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="ea491-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="ea491-110">この例では、データではなく操作を並列化します。</span><span class="sxs-lookup"><span data-stu-id="ea491-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="ea491-111">別の方法としては、PLINQ を使用して LINQ クエリを並列化し、クエリを順番に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ea491-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="ea491-112">また、PLINQ を使用してデータを並列化することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea491-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="ea491-113">もう 1 つのオプションとしては、クエリとタスクの両方を並列化する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="ea491-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="ea491-114">プロセッサの数が比較的少ないホスト コンピューターでは、オーバーヘッドの発生によってパフォーマンスが低下しますが、プロセッサ数の多いコンピューターではパフォーマンスは適切に調整されます。</span><span class="sxs-lookup"><span data-stu-id="ea491-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea491-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="ea491-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ea491-116">この例の全体をコピーして、Microsoft Visual Studio 2010 プロジェクトに貼り付けて F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ea491-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea491-117">参照</span><span class="sxs-lookup"><span data-stu-id="ea491-117">See Also</span></span>  
 [<span data-ttu-id="ea491-118">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="ea491-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="ea491-119">方法: タスクとその子を取り消す</span><span class="sxs-lookup"><span data-stu-id="ea491-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [<span data-ttu-id="ea491-120">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ea491-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
