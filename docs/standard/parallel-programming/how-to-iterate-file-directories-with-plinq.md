---
title: "方法: PLINQ を使用してファイル ディレクトリを反復処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a><span data-ttu-id="564b9-102">方法: PLINQ を使用してファイル ディレクトリを反復処理する</span><span class="sxs-lookup"><span data-stu-id="564b9-102">How to: Iterate File Directories with PLINQ</span></span>
<span data-ttu-id="564b9-103">この例では、ファイルのディレクトリでの操作を並列化する 2 つの簡単な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="564b9-103">This example shows two simple ways to parallelize operations on file directories.</span></span> <span data-ttu-id="564b9-104">最初のクエリを使用して、<xref:System.IO.Directory.GetFiles%2A>ディレクトリとすべてのサブディレクトリ内のファイル名の配列に挿入する方法です。</span><span class="sxs-lookup"><span data-stu-id="564b9-104">The first query uses the <xref:System.IO.Directory.GetFiles%2A> method to populate an array of file names in a directory and all subdirectories.</span></span> <span data-ttu-id="564b9-105">このメソッドは、配列全体を設定すると、され、そのため、操作の開始時の待機時間が生じることになるまでには返されません。</span><span class="sxs-lookup"><span data-stu-id="564b9-105">This method does not return until the entire array is populated, and therefore it can introduce latency at the beginning of the operation.</span></span> <span data-ttu-id="564b9-106">ただし、配列を作成すると、後に PLINQ ことができます、並列処理非常に短時間です。</span><span class="sxs-lookup"><span data-stu-id="564b9-106">However, after the array is populated, PLINQ can process it in parallel very quickly.</span></span>  
  
 <span data-ttu-id="564b9-107">2 番目のクエリは、静的な<xref:System.IO.Directory.EnumerateDirectories%2A>と<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>すぐに結果を返すを開始するメソッド。</span><span class="sxs-lookup"><span data-stu-id="564b9-107">The second query uses the static <xref:System.IO.Directory.EnumerateDirectories%2A> and <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> methods which begin returning results immediately.</span></span> <span data-ttu-id="564b9-108">このアプローチは短縮されます大規模なディレクトリ ツリーを繰り返し処理するときと比較する最初の例と処理時間が、さまざまな要因に依存できます。</span><span class="sxs-lookup"><span data-stu-id="564b9-108">This approach can be faster when you are iterating over large directory trees, although the processing time compared to the first example can depend on many factors.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="564b9-109">これらの例は、使用法を説明するものでし、可能性がありますいないほど高速で、同等の連続した LINQ to Objects クエリ。</span><span class="sxs-lookup"><span data-stu-id="564b9-109">These examples are intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="564b9-110">高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。</span><span class="sxs-lookup"><span data-stu-id="564b9-110">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="564b9-111">例</span><span class="sxs-lookup"><span data-stu-id="564b9-111">Example</span></span>  
 <span data-ttu-id="564b9-112">次の例と、ツリー内のすべてのディレクトリへのアクセスがある、ファイルのサイズが非常に大きなアクセス時間が重要ではありませんは、単純なシナリオでのファイル ディレクトリを反復処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="564b9-112">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="564b9-113">この方法には、ファイル名の配列が構築されるときに、先頭の待機時間の期間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="564b9-113">This approach involves a period of latency at the beginning while the array of file names is being constructed.</span></span>  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a><span data-ttu-id="564b9-114">例</span><span class="sxs-lookup"><span data-stu-id="564b9-114">Example</span></span>  
 <span data-ttu-id="564b9-115">次の例と、ツリー内のすべてのディレクトリへのアクセスがある、ファイルのサイズが非常に大きなアクセス時間が重要ではありませんは、単純なシナリオでのファイル ディレクトリを反復処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="564b9-115">The following example shows how to iterate over file directories in simple scenarios when you have access to all directories in the tree, the file sizes are not very large, and the access times are not significant.</span></span> <span data-ttu-id="564b9-116">この方法は、前の例よりも高速に結果を生成を開始します。</span><span class="sxs-lookup"><span data-stu-id="564b9-116">This approach begins producing results faster than the previous example.</span></span>  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 <span data-ttu-id="564b9-117">使用する場合<xref:System.IO.Directory.GetFiles%2A>ツリー内のすべてのディレクトリに十分なアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="564b9-117">When using <xref:System.IO.Directory.GetFiles%2A>, be sure that you have sufficient permissions on all directories in the tree.</span></span> <span data-ttu-id="564b9-118">それ以外の場合、例外がスローし、結果は返されません。</span><span class="sxs-lookup"><span data-stu-id="564b9-118">Otherwise an exception will be thrown and no results will be returned.</span></span> <span data-ttu-id="564b9-119">使用する場合、 <xref:System.IO.Directory.EnumerateDirectories%2A> PLINQ クエリでは例外を処理する I/O の反復処理を続行することができます、正常な方法で問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="564b9-119">When using the <xref:System.IO.Directory.EnumerateDirectories%2A> in a PLINQ query, it is problematic to handle I/O exceptions in a graceful way that enables you to continue iterating.</span></span> <span data-ttu-id="564b9-120">かどうかは、コードは、I/O または不正アクセス例外を処理する必要がありますで説明されているアプローチを検討する必要があります[する方法: Parallel クラスの使用してファイル ディレクトリを反復処理する](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="564b9-120">If your code must handle I/O or unauthorized access exceptions, then you should consider the approach described in [How to: Iterate File Directories with the Parallel Class](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).</span></span>  
  
 <span data-ttu-id="564b9-121">I/O 待機時間が問題の場合は、たとえば、ネットワーク経由でのファイル I/O の使用を検討してで説明されている非同期 I/O の手法のいずれかの[TPL と従来の .NET Framework 非同期プログラミング](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)とこの[ブログの投稿](http://go.microsoft.com/fwlink/?LinkID=186458).</span><span class="sxs-lookup"><span data-stu-id="564b9-121">If I/O latency is an issue, for example with file I/O over a network, consider using one of the asynchronous I/O techniques described in [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) and in this [blog post](http://go.microsoft.com/fwlink/?LinkID=186458).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="564b9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="564b9-122">See Also</span></span>  
 [<span data-ttu-id="564b9-123">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="564b9-123">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
