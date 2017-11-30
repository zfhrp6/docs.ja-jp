---
title: "方法: Parallel クラスを使用してファイル ディレクトリを反復処理する"
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
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a><span data-ttu-id="fe5ea-102">方法: Parallel クラスを使用してファイル ディレクトリを反復処理する</span><span class="sxs-lookup"><span data-stu-id="fe5ea-102">How to: Iterate File Directories with the Parallel Class</span></span>
<span data-ttu-id="fe5ea-103">多くの場合、ファイル反復処理は簡単に並列化できる操作です。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-103">In many cases, file iteration is an operation that can be easily parallelized.</span></span> <span data-ttu-id="fe5ea-104">トピック[する方法: PLINQ を使用してファイル ディレクトリを反復処理する](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md)多くのシナリオに対してこのタスクを実行する最も簡単な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-104">The topic [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) shows the easiest way to perform this task for many scenarios.</span></span> <span data-ttu-id="fe5ea-105">ただし、ファイル システムへのアクセス時に発生する可能性のある多くの種類の例外をコードで処理する必要がある場合は、複雑さが生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-105">However, complications can arise when your code has to deal with the many types of exceptions that can arise when accessing the file system.</span></span> <span data-ttu-id="fe5ea-106">次の例は、この問題への対処方法の 1 つを示しています。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-106">The following example shows one approach to the problem.</span></span> <span data-ttu-id="fe5ea-107">この例では、スタック ベースの反復処理を使用して、指定されたディレクトリにあるすべてのファイルとフォルダーを走査し、コードで各種例外をキャッチして処理できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-107">It uses a stack-based iteration to traverse all files and folders under a specified directory, and it enables your code to catch and handle various exceptions.</span></span> <span data-ttu-id="fe5ea-108">例外を処理する方法は開発者に委ねられています。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-108">Of course, the way that you handle the exceptions is up to you.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe5ea-109">例</span><span class="sxs-lookup"><span data-stu-id="fe5ea-109">Example</span></span>  
 <span data-ttu-id="fe5ea-110">次の例では、ディレクトリの反復処理は順次実行されますが、ファイルの処理は並列で実行されます。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-110">The following example iterates the directories sequentially, but processes the files in parallel.</span></span> <span data-ttu-id="fe5ea-111">これは、ディレクトリのファイル占有率が大きい場合に最適な方法と考えられます。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-111">This is probably the best approach when you have a large file-to-directory ratio.</span></span> <span data-ttu-id="fe5ea-112">また、ディレクトリの反復処理を並列化し、各ファイルに順次アクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-112">It is also possible to parallelize the directory iteration, and access each file sequentially.</span></span> <span data-ttu-id="fe5ea-113">多数のプロセッサを搭載したコンピューターを明確に対象としている場合を除き、両方のループを並列化するのは効率的とは言えません。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-113">It is probably not efficient to parallelize both loops unless you are specifically targeting a machine with a large number of processors.</span></span> <span data-ttu-id="fe5ea-114">ただし、どの場合もアプリケーションを徹底的にテストして、最適な方法を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-114">However, as in all cases, you should test your application thoroughly to determine the best approach.</span></span>  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 <span data-ttu-id="fe5ea-115">この例では、ファイル I/O を同期的に実行します。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-115">In this example, the file I/O is performed synchronously.</span></span> <span data-ttu-id="fe5ea-116">大きなファイルを処理する場合やネットワーク接続が低速の場合は、ファイルに非同期にアクセスするよりも望ましいと考えられます。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-116">When dealing with large files or slow network connections, it might be preferable to access the files asynchronously.</span></span> <span data-ttu-id="fe5ea-117">非同期 I/O の手法を並列反復処理と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-117">You can combine asynchronous I/O techniques with parallel iteration.</span></span> <span data-ttu-id="fe5ea-118">詳細については、「[TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)」(TPL と従来の .NET Framework 非同期プログラミング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-118">For more information, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).</span></span>  
  
 <span data-ttu-id="fe5ea-119">この例では、ローカル変数 `fileCount` を使用して、処理済みファイルの合計数を示すカウントを管理します。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-119">The example uses the local `fileCount` variable to maintain a count of the total number of files processed.</span></span> <span data-ttu-id="fe5ea-120">この変数は複数のタスクから同時にアクセスされる可能性があるため、この変数へのアクセスは <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> メソッドの呼び出しによって同期されています。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-120">Because the variable might be accessed concurrently by multiple tasks, access to it is synchronized by calling the <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fe5ea-121">メイン スレッドで例外がスローされた場合、<xref:System.Threading.Tasks.Parallel.ForEach%2A> メソッドによって開始されたスレッドが引き続き実行されることがあります。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-121">Note that if an exception is thrown on the main thread, the threads that are started by the <xref:System.Threading.Tasks.Parallel.ForEach%2A> method might continue to run.</span></span> <span data-ttu-id="fe5ea-122">これらのスレッドを停止するには、例外ハンドラーで Boolean 変数を設定し、並列ループを反復処理するたびに値をチェックします。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-122">To stop these threads, you can set a Boolean variable in your exception handlers, and check its value on each iteration of the parallel loop.</span></span> <span data-ttu-id="fe5ea-123">例外がスローされたことを値が示している場合は、<xref:System.Threading.Tasks.ParallelLoopState> 変数を使用してループを停止または中断します。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-123">If the value indicates that an exception has been thrown, use the <xref:System.Threading.Tasks.ParallelLoopState> variable to stop or break from the loop.</span></span> <span data-ttu-id="fe5ea-124">詳細については、次を参照してください。[する方法: Parallel.For ループを停止または中断](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)です。</span><span class="sxs-lookup"><span data-stu-id="fe5ea-124">For more information, see [How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5ea-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe5ea-125">See Also</span></span>  
 [<span data-ttu-id="fe5ea-126">データの並列化</span><span class="sxs-lookup"><span data-stu-id="fe5ea-126">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
