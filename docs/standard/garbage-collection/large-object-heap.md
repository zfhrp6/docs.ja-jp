---
title: Windows システムの大きなオブジェクト ヒープ
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68513d2535ea9e19a42f9e58b9d423e17008f9de
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="18765-102">Windows システムの大きなオブジェクト ヒープ</span><span class="sxs-lookup"><span data-stu-id="18765-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="18765-103">.NET のガベージ コレクター (GC) は、オブジェクトを小さなオブジェクトと大きなオブジェクトに分けます。</span><span class="sxs-lookup"><span data-stu-id="18765-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="18765-104">オブジェクトが大きい場合、その属性のいくつかは、オブジェクトが小さい場合に比べて、より重要な意味を持つようになります。</span><span class="sxs-lookup"><span data-stu-id="18765-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="18765-105">たとえば、最適化 (つまり、メモリをヒープ上の他の場所にコピーする処理) のコストが高くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="18765-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="18765-106">そのため、.NET ガベージ コレクターは、大きなオブジェクトを大きなオブジェクト ヒープ (LOH) に配置します。</span><span class="sxs-lookup"><span data-stu-id="18765-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="18765-107">このトピックでは、大きなオブジェクト ヒープについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="18765-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="18765-108">大きなオブジェクトの定義、その収集方法、大きなオブジェクトがパフォーマンスに与える影響などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="18765-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18765-109">このトピックでは、Windows システムのみで実行されている .NET Framework と .NET Core の大きなオブジェクト ヒープについて説明します。</span><span class="sxs-lookup"><span data-stu-id="18765-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="18765-110">その他のプラットフォームの .NET 実装で実行されている LOH については取り上げません。</span><span class="sxs-lookup"><span data-stu-id="18765-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="18765-111">大きなオブジェクト ヒープのオブジェクトが最終的にどのようになり、GC でどのように処理されるかについて</span><span class="sxs-lookup"><span data-stu-id="18765-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="18765-112">オブジェクトのサイズが 85,000 バイト以上の場合、大きなオブジェクトと見なされます。</span><span class="sxs-lookup"><span data-stu-id="18765-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="18765-113">この数値は、パフォーマンス チューニングによって決定されたものです。</span><span class="sxs-lookup"><span data-stu-id="18765-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="18765-114">85,000 バイト以上のオブジェクトの割り当て要求の場合、ランタイムはそれを大きなオブジェクト ヒープに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="18765-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="18765-115">.NET GC に関する基本事項をいくつか確認することで、これが何を意味するのかを理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="18765-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="18765-116">.NET ガベージ コレクターは世代別コレクターです。</span><span class="sxs-lookup"><span data-stu-id="18765-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="18765-117">世代 0、世代 1、世代 2 という 3 つの世代があります。</span><span class="sxs-lookup"><span data-stu-id="18765-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="18765-118">世代が 3 つあるのは、適切にチューニングされたアプリでは、ほとんどのオブジェクトが世代 0 で終了するためです。</span><span class="sxs-lookup"><span data-stu-id="18765-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="18765-119">たとえば、サーバー アプリでは、各要求に関連付けられた割り当ては、その要求の完了後に終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18765-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="18765-120">処理中の割り当て要求は、世代 1 に進み、その世代で終了します。</span><span class="sxs-lookup"><span data-stu-id="18765-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="18765-121">本質的に、世代 1 は、短期間存在するオブジェクトの領域と長期間存在するオブジェクトの領域との間でバッファーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="18765-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="18765-122">小さなオブジェクトは常に世代 0 に割り当てられ、その有効期間に応じて、世代 1 または世代 2 に昇格される場合があります。</span><span class="sxs-lookup"><span data-stu-id="18765-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="18765-123">大きなオブジェクトは常に世代 2 に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="18765-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="18765-124">大きなオブジェクトは世代 2 に属します。これは、大きなオブジェクトが世代 2 の収集中にのみ収集されるためです。</span><span class="sxs-lookup"><span data-stu-id="18765-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="18765-125">ある世代の収集時には、それより存在期間の短い世代もすべて収集されます。</span><span class="sxs-lookup"><span data-stu-id="18765-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="18765-126">たとえば、世代 1 の GC が行われるときには、世代 1 と世代 0 の両方が収集されます。</span><span class="sxs-lookup"><span data-stu-id="18765-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="18765-127">また、世代 2 の GC が行われるときには、ヒープ全体が収集されます。</span><span class="sxs-lookup"><span data-stu-id="18765-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="18765-128">そのため、世代 2 の GC は*フル GC* とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="18765-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="18765-129">この記事では、フル GC ではなく、世代 2 の GC と呼びますが、どちらの用語も使用できます。</span><span class="sxs-lookup"><span data-stu-id="18765-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="18765-130">世代では、GC ヒープの論理ビューが提供されます。</span><span class="sxs-lookup"><span data-stu-id="18765-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="18765-131">物理的には、オブジェクトはマネージド ヒープ セグメントに存在します。</span><span class="sxs-lookup"><span data-stu-id="18765-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="18765-132">*マネージド ヒープ セグメント* は、GC がマネージド コードに代わって [VirtualAlloc 関数](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx)を呼び出して OS から予約するメモリのチャンクです。</span><span class="sxs-lookup"><span data-stu-id="18765-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) on behalf of managed code.</span></span> <span data-ttu-id="18765-133">CLR が読み込まれると、GC は 2 つの初期ヒープ セグメントを割り当てます。その 1 つは小さなオブジェクト用 (小さなオブジェクト ヒープ、つまり SOH) で、もう 1 つは大きなオブジェクト用 (大きなオブジェクト ヒープ) です。</span><span class="sxs-lookup"><span data-stu-id="18765-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="18765-134">割り当て要求は、これらのマネージド ヒープ セグメントにマネージド オブジェクトを配置すると満たされます。</span><span class="sxs-lookup"><span data-stu-id="18765-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="18765-135">オブジェクトが 85,000 バイト未満の場合、SOH のセグメントに配置されます。それ以外の場合は、LOH セグメントに配置されます。</span><span class="sxs-lookup"><span data-stu-id="18765-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="18765-136">セグメントに割り当てるオブジェクトが増加していくと、セグメントは (小さいチャンクへと) コミットされます。</span><span class="sxs-lookup"><span data-stu-id="18765-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="18765-137">SOH の場合、GC で残ったオブジェクトは次の世代に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="18765-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="18765-138">世代 0 のコレクションで残ったオブジェクトは、世代 1 のオブジェクトと見なされるようになり、以後同様です。</span><span class="sxs-lookup"><span data-stu-id="18765-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="18765-139">ただし、最も古い世代で終了しなかったオブジェクトは、引き続き最も古い世代と見なされます。</span><span class="sxs-lookup"><span data-stu-id="18765-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="18765-140">つまり、世代 2 で残ったオブジェクトは世代 2 のオブジェクトであり、LOH で残ったオブジェクトは LOH オブジェクト (世代 2 で収集) となります。</span><span class="sxs-lookup"><span data-stu-id="18765-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span> 

<span data-ttu-id="18765-141">ユーザー コードは、世代 0 (小さなオブジェクト) または LOH (大きなオブジェクト) にのみ割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="18765-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="18765-142">GC だけが、世代 1 (世代 0 で残ったオブジェクトを昇格) と世代 2 (世代 1 と世代 2 で残ったオブジェクトを昇格) のオブジェクトを "割り当てる" ことができます。</span><span class="sxs-lookup"><span data-stu-id="18765-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="18765-143">ガベージ コレクションがトリガーされると、GC は、ライブ オブジェクトをトレースし、それらを最適化します。</span><span class="sxs-lookup"><span data-stu-id="18765-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="18765-144">ただし、最適化のコストが高いため、GC は LOH を*一掃* し、終了したオブジェクトから空きリストを作成します。これらのオブジェクトは、大きなオブジェクトの割り当て要求を満たすために、後で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="18765-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="18765-145">隣接する複数の終了したオブジェクトは、1 つの空きオブジェクトに結合されます。</span><span class="sxs-lookup"><span data-stu-id="18765-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="18765-146">.NET Core と .NET Framework (.NET Framework 4.5.1 以降) には <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> プロパティが含まれています。これを使用して、ユーザーは LOH を次のフル ブロッキング GC 中に最適化するよう指定できます。</span><span class="sxs-lookup"><span data-stu-id="18765-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="18765-147">将来的には、.NET で LOH を自動的に最適化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="18765-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="18765-148">つまり、大きなオブジェクトを割り当てたときに、そのオブジェクトが移動されないようにするには、オブジェクトを固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18765-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="18765-149">図 1 に示したシナリオでは、GC は世代 0 の GC で `Obj1` と `Obj3` が終了した後に世代 1 を形成し、世代 1 の GC で `Obj2` と `Obj5` が終了した後に世代 2 を形成しています。</span><span class="sxs-lookup"><span data-stu-id="18765-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="18765-150">この図と次の図は単に例を示すためのものであることに注意してください。ヒープで何が起こっているかをわかりやすくするために、図にはごくわずかなオブジェクトしか含まれていません。</span><span class="sxs-lookup"><span data-stu-id="18765-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="18765-151">実際には、通常、GC にはより多くのオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="18765-151">In reality, many more objects are typically involved in a GC.</span></span>

![図 1: 世代 0 の GC と世代 1 の GC](media/loh/loh-figure-1.jpg)   
<span data-ttu-id="18765-153">図 1: 世代 0 および世代 1 の GC。</span><span class="sxs-lookup"><span data-stu-id="18765-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="18765-154">図 2 では、`Obj1` と `Obj2` を終了させた世代 2 の GC の後、GC は、`Obj1` と `Obj2` が占有していたメモリから隣接する空き領域を形成し、`Obj4` に対する割り当て要求を満たすためにその空き領域を使用しています。</span><span class="sxs-lookup"><span data-stu-id="18765-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="18765-155">最後のオブジェクト `Obj3` からセグメントの末尾までの領域は、割り当て要求を満たすために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="18765-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>
 
![図 2: 世代 2 の GC の後](media/loh/loh-figure-2.jpg)  
<span data-ttu-id="18765-157">図 2: 世代 2 の GC の後</span><span class="sxs-lookup"><span data-stu-id="18765-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="18765-158">大きなオブジェクトの割り当て要求に応じるだけの十分な空き領域がない場合、GC はまず、OS からさらにセグメントを取得することを試みます。</span><span class="sxs-lookup"><span data-stu-id="18765-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="18765-159">それが失敗した場合、多少の領域を解放できることを期待して、世代 2 の GC をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="18765-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="18765-160">世代 1 または世代 2 の GC 中に、ガベージ コレクターは、ライブ オブジェクトが存在しないセグメントを、[VirtualFree 関数](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx)を呼び出して解放し、OS に戻します。</span><span class="sxs-lookup"><span data-stu-id="18765-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span></span> <span data-ttu-id="18765-161">最後の有効なオブジェクトからセグメントの末尾までの領域はデコミットされます (ただし、世代 0/世代 1 が有効な短期セグメントの場合を除きます。この場合、アプリケーションですぐに割り当てられるため、ガベージ コレクターは一部をコミットしたままにします)。</span><span class="sxs-lookup"><span data-stu-id="18765-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="18765-162">また、空き領域は引き続きコミットされていますが、リセットされます。つまり、OS はその領域のデータをディスクに書き戻す必要がありません。</span><span class="sxs-lookup"><span data-stu-id="18765-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="18765-163">LOH は世代 2 の GC 中にのみ収集されるため、LOH セグメントを解放できるのはその GC 中のみとなります。</span><span class="sxs-lookup"><span data-stu-id="18765-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="18765-164">図 3 に示したシナリオでは、ガベージ コレクターは 1 つのセグメント (セグメント 2) を解放して OS に戻し、残りのセグメントでより多くの領域をデコミットしています。</span><span class="sxs-lookup"><span data-stu-id="18765-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="18765-165">大きなオブジェクトの割り当て要求を満たすために、セグメント末尾のデコミットされた領域を使用する必要がある場合は、メモリを再度コミットします </span><span class="sxs-lookup"><span data-stu-id="18765-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="18765-166">(コミット/デコミットの詳細については、[VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) に関するドキュメントを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="18765-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span></span>
 
![図 3: 世代 2 の GC 後の LOH](media/loh/loh-figure-3.jpg)  
<span data-ttu-id="18765-168">図 3: 世代 2 の GC 後の LOH</span><span class="sxs-lookup"><span data-stu-id="18765-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="18765-169">大きなオブジェクトが収集されるタイミング</span><span class="sxs-lookup"><span data-stu-id="18765-169">When is a large object collected?</span></span>

<span data-ttu-id="18765-170">一般に、GC は次の 3 つの状態のいずれかになった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="18765-170">In general, a GC occurs when one of the following following 3 conditions happens:</span></span>

- <span data-ttu-id="18765-171">割り当てが世代 0 または大きなオブジェクトのしきい値を超えている場合。</span><span class="sxs-lookup"><span data-stu-id="18765-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

   <span data-ttu-id="18765-172">しきい値は世代のプロパティの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="18765-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="18765-173">世代のしきい値は、ガベージ コレクターがオブジェクトをそれに割り当てるときに設定されます。</span><span class="sxs-lookup"><span data-stu-id="18765-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="18765-174">しきい値を超えたときに、その世代に対して GC がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="18765-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="18765-175">小さなオブジェクトまたは大きなオブジェクトを割り当てると、世代 0 と LOH のしきい値がそれぞれ消費されます。</span><span class="sxs-lookup"><span data-stu-id="18765-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="18765-176">ガベージ コレクターがオブジェクトを世代 1 と世代 2 に割り当てると、それらのしきい値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="18765-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="18765-177">これらのしきい値は、プログラムの実行時に動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="18765-177">These thresholds are dynamically tuned as the program runs.</span></span>

   <span data-ttu-id="18765-178">これは一般的なケースです。マネージド ヒープでの割り当てにより、ほとんどの GC が発生します。</span><span class="sxs-lookup"><span data-stu-id="18765-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="18765-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType> メソッドが呼び出された場合。</span><span class="sxs-lookup"><span data-stu-id="18765-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

   <span data-ttu-id="18765-180">パラメーターなしの <xref:System.GC.Collect?displayProperty=nameWithType> メソッドが呼び出されたか、別のオーバーロードに引数として <xref:System.GC.MaxGeneration?displayProperty=nameWithType> が渡された場合、マネージド ヒープの残りの部分と共に LOH が収集されます。</span><span class="sxs-lookup"><span data-stu-id="18765-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="18765-181">システムのメモリが不足している場合。</span><span class="sxs-lookup"><span data-stu-id="18765-181">The system is in low memory situation.</span></span>

   <span data-ttu-id="18765-182">これは、ガベージ コレクターが、OS からメモリ使用率が高いという通知を受け取ったときに起こります。</span><span class="sxs-lookup"><span data-stu-id="18765-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="18765-183">ガベージ コレクターは、世代 2 の GC を行うことが有効であると判断した場合は、それをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="18765-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="18765-184">LOH のパフォーマンスへの影響</span><span class="sxs-lookup"><span data-stu-id="18765-184">LOH Performance Implications</span></span>

<span data-ttu-id="18765-185">大きなオブジェクト ヒープへの割り当ては、次のようにパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="18765-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="18765-186">割り当てコスト。</span><span class="sxs-lookup"><span data-stu-id="18765-186">Allocation cost.</span></span>

   <span data-ttu-id="18765-187">CLR では、すべての新しいオブジェクトに対して解放時にメモリがクリアされることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="18765-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="18765-188">これは、大きなオブジェクトの割り当てコストが完全に、メモリのクリアによって占められることを意味します (GC をトリガーしない限り)。</span><span class="sxs-lookup"><span data-stu-id="18765-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="18765-189">1 バイトをクリアするのに 2 サイクルかかるとすると、大きなオブジェクトの中で最小のものであっても、クリアするのに 170,000 サイクルかかります。</span><span class="sxs-lookup"><span data-stu-id="18765-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="18765-190">2 GHz のマシンで 16 MB のメモリをクリアする場合、約 16 ミリ秒かかります。</span><span class="sxs-lookup"><span data-stu-id="18765-190">Clearing the memmory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="18765-191">これはかなり大きなコストです。</span><span class="sxs-lookup"><span data-stu-id="18765-191">That's a rather large cost.</span></span>

- <span data-ttu-id="18765-192">コレクション コスト。</span><span class="sxs-lookup"><span data-stu-id="18765-192">Collection cost.</span></span>

   <span data-ttu-id="18765-193">LOH と世代 2 は一緒に収集されるため、いずれかのしきい値を超えると、世代 2 のコレクションがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="18765-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="18765-194">LOH のしきい値によって世代 2 の収集がトリガーされた場合、世代 2 が GC 後に非常に小さくなるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="18765-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="18765-195">世代 2 にあまり多くのデータがない場合、影響は最小限になります。</span><span class="sxs-lookup"><span data-stu-id="18765-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="18765-196">ただし、世代 2 が大きい場合は、世代 2 の多くの GC がトリガーされると、パフォーマンス上の問題が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="18765-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="18765-197">多くの大きなオブジェクトがごく一時的に割り当てられており、大きな SOH がある場合は、GC の実行に過度な時間を費やす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="18765-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="18765-198">さらに、非常に大きなオブジェクトの割り当てと解放を引き続き繰り返すと、割り当てコストが相当に増加します。</span><span class="sxs-lookup"><span data-stu-id="18765-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="18765-199">参照型の配列要素。</span><span class="sxs-lookup"><span data-stu-id="18765-199">Array elements with reference types.</span></span>

   <span data-ttu-id="18765-200">LOH 上の非常に大きなオブジェクトは、通常は配列です (非常に大きなインスタンス オブジェクトを持つということは、ごくまれです)。</span><span class="sxs-lookup"><span data-stu-id="18765-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="18765-201">配列の要素に参照が多く含まれる場合、要素に参照が多く含まれない場合には存在しないコストが発生します。</span><span class="sxs-lookup"><span data-stu-id="18765-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="18765-202">要素に参照が含まれない場合、ガベージ コレクターは配列をまったく確認する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="18765-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="18765-203">たとえば、配列を使用してバイナリ ツリーのノードを格納する場合、これを実装する方法の 1 つは、ノードの右および左のノードを実際のノードで参照することです。</span><span class="sxs-lookup"><span data-stu-id="18765-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   <span data-ttu-id="18765-204">`num_nodes` が大きい場合、ガベージ コレクターは、要素ごとに少なくとも 2 回の参照を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="18765-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="18765-205">他に、左右のノードのインデックスを格納するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="18765-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   <span data-ttu-id="18765-206">左のノードのデータを `left.d` として参照する代わりに、それを `binary_tr[left_index].d` として参照します。</span><span class="sxs-lookup"><span data-stu-id="18765-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="18765-207">ガベージ コレクターは、左右のノードに対して参照を確認する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="18765-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="18765-208">3 つの要因のうち、通常は最初の 2 つが 3 番目より重要です。</span><span class="sxs-lookup"><span data-stu-id="18765-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="18765-209">そのため、一時オブジェクトを割り当てる代わりに再利用する大きなオブジェクトのプールを割り当てることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18765-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span> 

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="18765-210">LOH のパフォーマンス データの収集</span><span class="sxs-lookup"><span data-stu-id="18765-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="18765-211">特定の領域のパフォーマンス データを収集するには、次のような状況である必要があります。</span><span class="sxs-lookup"><span data-stu-id="18765-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="18765-212">この領域に着目する理由がわかっている。</span><span class="sxs-lookup"><span data-stu-id="18765-212">Found evidence that you should be looking at this area.</span></span>

1. <span data-ttu-id="18765-213">既知の他の領域を調べつくしたが、確認されたパフォーマンス上の問題を説明できる原因が見つからなかった。</span><span class="sxs-lookup"><span data-stu-id="18765-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="18765-214">メモリと CPU の基礎の詳細については、ブログの「[Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/)」 (解決策を見つける前に問題を理解する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18765-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="18765-215">次のツールを使用して、LOH のパフォーマンスに関するデータを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="18765-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="18765-216">.NET CLR メモリ パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="18765-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="18765-217">ETW イベント</span><span class="sxs-lookup"><span data-stu-id="18765-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="18765-218">デバッガー</span><span class="sxs-lookup"><span data-stu-id="18765-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="18765-219">.NET CLR メモリ パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="18765-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="18765-220">これらのパフォーマンス カウンターは、通常、パフォーマンスの問題について調べる最初の手順として有効です (ただし、[ETW イベント](#etw)を使用することをお勧めします)。</span><span class="sxs-lookup"><span data-stu-id="18765-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw)).</span></span> <span data-ttu-id="18765-221">パフォーマンス モニターを構成するには、図 4 に示すように、必要なカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="18765-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="18765-222">LOH に関連するものは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="18765-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="18765-223">**\# Gen 2 Collections**</span><span class="sxs-lookup"><span data-stu-id="18765-223">**\# Gen 2 Collections**</span></span>

   <span data-ttu-id="18765-224">プロセスが開始されてから世代 2 の GC が発生した回数を示します。</span><span class="sxs-lookup"><span data-stu-id="18765-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="18765-225">このカウンターは、世代 2 のコレクション (フル ガベージ コレクションとも呼ばれる) の最後にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="18765-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="18765-226">このカウンターは、最後に計測された値を表示します。</span><span class="sxs-lookup"><span data-stu-id="18765-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="18765-227">**Large Object Heap size**</span><span class="sxs-lookup"><span data-stu-id="18765-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="18765-228">LOH の現在のサイズ (空き領域を含む) をバイト単位で表示します。</span><span class="sxs-lookup"><span data-stu-id="18765-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="18765-229">このカウンターは、割り当てがなされるたびに更新されるのではなく、ガベージ コレクションが 1 回終了するごとに更新されます。</span><span class="sxs-lookup"><span data-stu-id="18765-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="18765-230">パフォーマンス カウンターを見る一般的な方法は、パフォーマンス モニター (perfmon.exe) で表示することです。</span><span class="sxs-lookup"><span data-stu-id="18765-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="18765-231">対象のプロセスに対して表示するカウンターを追加するには、[カウンターの追加] を使用します。</span><span class="sxs-lookup"><span data-stu-id="18765-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="18765-232">図 4 に示すように、パフォーマンス カウンターのデータは、ログ ファイルに保存できます。</span><span class="sxs-lookup"><span data-stu-id="18765-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![図 4: パフォーマンス カウンターの追加。](media/loh/perfcounter.png)    
<span data-ttu-id="18765-234">図 4: 世代 2 の GC 後の LOH</span><span class="sxs-lookup"><span data-stu-id="18765-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="18765-235">また、パフォーマンス カウンターに対してプログラムでクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="18765-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="18765-236">多くのユーザーは、日常的なテスト プロセスの一部として、そのような方法でカウンターのデータを収集しています。</span><span class="sxs-lookup"><span data-stu-id="18765-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="18765-237">カウンターに通常範囲外の値を見つけたときは、他の手段を使用して、調査に役立つ詳細なデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="18765-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="18765-238">ETW ではより豊富な情報が提供されるため、パフォーマンス カウンターではなく、ETW イベントを使用することをお勧めます。</span><span class="sxs-lookup"><span data-stu-id="18765-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw"></a><span data-ttu-id="18765-239">ETW</span><span class="sxs-lookup"><span data-stu-id="18765-239">ETW</span></span>

<span data-ttu-id="18765-240">ガベージ コレクターは、ヒープで行われる内容とその理由を理解するのに役立つ、豊富な ETW イベントのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="18765-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="18765-241">次のブログ記事には、ETW を使用して GC イベントを収集および理解する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="18765-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="18765-242">GC ETW イベント - 1 </span><span class="sxs-lookup"><span data-stu-id="18765-242">GC ETW Events - 1 </span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [<span data-ttu-id="18765-243">GC ETW イベント - 2</span><span class="sxs-lookup"><span data-stu-id="18765-243">GC ETW Events - 2</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [<span data-ttu-id="18765-244">GC ETW イベント - 3</span><span class="sxs-lookup"><span data-stu-id="18765-244">GC ETW Events - 3</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [<span data-ttu-id="18765-245">GC ETW イベント - 4</span><span class="sxs-lookup"><span data-stu-id="18765-245">GC ETW Events - 4</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

<span data-ttu-id="18765-246">一時 LOH の割り当てによる過度の世代 2 の GC を特定するには、GC のトリガー理由の列を確認します。</span><span class="sxs-lookup"><span data-stu-id="18765-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="18765-247">大きな一時オブジェクトのみを割り当てる簡単なテストの場合は、次の [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) コマンド ラインを使用して、ETW イベントに関する情報を収集できます。</span><span class="sxs-lookup"><span data-stu-id="18765-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="18765-248">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="18765-248">The result is something like this:</span></span>
 
![図 5: PerfView を使用する ETW イベントの確認](media/loh/perfview.png)  
<span data-ttu-id="18765-250">図 5: PerfView を使用した場合に表示される ETW イベント</span><span class="sxs-lookup"><span data-stu-id="18765-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="18765-251">ご覧のとおり、すべての GC は世代 2 の GC であり、AllocLarge によってすべてトリガーされます。これは、大きなオブジェクトの割り当てにより、この GC がトリガーされたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="18765-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="18765-252">**LOH Survival Rate %** 列に 1% と示されているため、これらの割り当ては一時的なものであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="18765-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="18765-253">これらの大きなオブジェクトを割り当てたユーザーを示す追加の ETW イベントを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="18765-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="18765-254">たとえば、以下のコマンド ラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="18765-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="18765-255">この場合、AllocationTick イベントが収集されます。このイベントは、約 100 K 相当の割り当てごとに発生します。</span><span class="sxs-lookup"><span data-stu-id="18765-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="18765-256">つまり、イベントは、大きなオブジェクトが割り当てられるたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="18765-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="18765-257">次に、大きなオブジェクトを割り当てた呼び出し履歴を示す、GC ヒープ割り当てビューのいずれかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="18765-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>
 
![図 6: GC ヒープ割り当てビュー](media/loh/perfview2.png)  
<span data-ttu-id="18765-259">図 6: GC ヒープ割り当てビュー</span><span class="sxs-lookup"><span data-stu-id="18765-259">Figure 6: A GC Heap Alloc view</span></span>
 
<span data-ttu-id="18765-260">ご覧のとおり、これは、`Main` メソッドから大きなオブジェクトを割り当てるだけの非常に簡単なテストです。</span><span class="sxs-lookup"><span data-stu-id="18765-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="18765-261">デバッガー</span><span class="sxs-lookup"><span data-stu-id="18765-261">A debugger</span></span>

<span data-ttu-id="18765-262">メモリ ダンプしかない状態で、LOH に実際にどのオブジェクトが存在するかを確認する必要がある場合は、.NET で提供される [SoS デバッガー拡張](http://msdn2.microsoft.com/ms404370.aspx)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="18765-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](http://msdn2.microsoft.com/ms404370.aspx) provided by .NET.</span></span> 

> [!NOTE]
> <span data-ttu-id="18765-263">このセクションに示されているデバッグ コマンドは、[Windows デバッガー](http://www.microsoft.com/whdc/devtools/debugging/default.mspx)に適用できます。</span><span class="sxs-lookup"><span data-stu-id="18765-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="18765-264">LOH の分析からのサンプル出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="18765-264">The following shows sample output from analyzing the LOH:</span></span>

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="18765-265">LOH のヒープ サイズは (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 バイトです。</span><span class="sxs-lookup"><span data-stu-id="18765-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="18765-266">アドレス 023e1000 と 033db630 の間で、8,008,736 バイトが <xref:System.Object?displayProperty=fullName> オブジェクトの配列によって占有され、6,663,696 バイトが <xref:System.Byte?displayProperty=nameWithType> オブジェクトの配列によって占有され、2,081,792 バイトが空き領域によって占有されています。</span><span class="sxs-lookup"><span data-stu-id="18765-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=fullName> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="18765-267">デバッガーによって、LOH の合計サイズが 85,000 バイトより少ないことが示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="18765-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="18765-268">その理由は、ランタイム自体が LOH を使用して、大きなオブジェクトよりも小さいいくつかのオブジェクトを割り当てるためです。</span><span class="sxs-lookup"><span data-stu-id="18765-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="18765-269">LOH は最適化されないため、LOH が断片化の元であると考えられる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="18765-269">Because the LOH is not compacted, sometimes the LOH is thoought to be the source of fragmentation.</span></span> <span data-ttu-id="18765-270">断片化の意味を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="18765-270">Fragmentation means:</span></span>

- <span data-ttu-id="18765-271">マネージド ヒープの断片化: マネージド オブジェクト間の空き領域の量で示されます。</span><span class="sxs-lookup"><span data-stu-id="18765-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="18765-272">SoS では、`!dumpheap –type Free` コマンドはマネージド オブジェクト間の空き領域の量を示します。</span><span class="sxs-lookup"><span data-stu-id="18765-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="18765-273">仮想メモリ (VM) アドレス空間の断片化: `MEM_FREE` としてマークされるメモリです。</span><span class="sxs-lookup"><span data-stu-id="18765-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="18765-274">windbg でさまざまなデバッガー コマンドを使用して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="18765-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="18765-275">次の例は、VM 領域内の断片化を示しています。</span><span class="sxs-lookup"><span data-stu-id="18765-275">The following example shows fragmentation in the VM space:</span></span>

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="18765-276">より一般的に VM の断片化が見られるケースは、大きな一時オブジェクトが、OS から新しいマネージド ヒープ セグメントを頻繁に取得して空のセグメントを開放して OS に戻すためにガベージ コレクターを必要とするような場合です。</span><span class="sxs-lookup"><span data-stu-id="18765-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="18765-277">LOH が VM の断片化を生じさせているかどうかを確認するには、[VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) と [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) にブレークポイントを設定して、その呼び出し元を確認します。</span><span class="sxs-lookup"><span data-stu-id="18765-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) and [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) to see who call them.</span></span> <span data-ttu-id="18765-278">たとえば、OS から 8 MB を超える仮想メモリ チャンクを割り当てようとしているオブジェクトを調べる場合、次のようにブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="18765-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="18765-279">このコマンドはデバッガーを中断し、[VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) が 8 MB (0x800000) より大きい割り当てサイズで呼び出された場合にのみ、呼び出し履歴を表示します。</span><span class="sxs-lookup"><span data-stu-id="18765-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="18765-280">CLR 2.0 では *VM Hoarding* という機能が追加されました。これは、セグメント (大きなオブジェクト ヒープと小さなオブジェクト ヒープを含む) が頻繁に取得され、解放されるシナリオで役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="18765-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="18765-281">VM Hoarding を指定するには、ホスティング API で、`STARTUP_HOARD_GC_VM` というスタートアップ フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="18765-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="18765-282">空のセグメントを解放して OS に戻す代わりに、CLR はこれらのセグメント上のメモリをデコミットして、スタンバイ リストに含めます </span><span class="sxs-lookup"><span data-stu-id="18765-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="18765-283">(大きすぎるセグメントの場合、CLR はこれを行わないことに注意してください)。CLR は、新しいセグメント要求を満たすために、後でこれらのセグメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="18765-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="18765-284">次にアプリで新しいセグメントが必要になったときに、CLR は、このスタンバイ リストに十分に大きなセグメントがあれば、それを使用します。</span><span class="sxs-lookup"><span data-stu-id="18765-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="18765-285">VM Hoarding は、メモリ不足の例外を回避するために、システム上で実行されている優先度の高いアプリである一部のサーバー アプリなど、既に取得されているセグメントに保持する必要があるアプリケーションでも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="18765-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="18765-286">この機能を使用する際には、アプリケーションを慎重にテストして、アプリケーションのメモリ使用量が十分に安定しているのを確認することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18765-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
<span data-ttu-id="18765-287">bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"</span><span class="sxs-lookup"><span data-stu-id="18765-287">bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"</span></span>
```

This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).

CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released. To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API. Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list. (Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests. The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.

VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.

We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.
