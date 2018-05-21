---
title: 連続するキーで結果をグループ化する
description: 連続するキーで結果をグループ化する方法。
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="2590f-103">連続するキーで結果をグループ化する</span><span class="sxs-lookup"><span data-stu-id="2590f-103">Group results by contiguous keys</span></span>

<span data-ttu-id="2590f-104">要素をグループ化し、連続するキーのサブシーケンスを表すチャンクにする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2590f-104">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="2590f-105">たとえば、次の一連のキーと値のペアがあるとします。</span><span class="sxs-lookup"><span data-stu-id="2590f-105">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="2590f-106">キー</span><span class="sxs-lookup"><span data-stu-id="2590f-106">Key</span></span>|<span data-ttu-id="2590f-107">[値]</span><span class="sxs-lookup"><span data-stu-id="2590f-107">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="2590f-108">A</span><span class="sxs-lookup"><span data-stu-id="2590f-108">A</span></span>|<span data-ttu-id="2590f-109">水</span><span class="sxs-lookup"><span data-stu-id="2590f-109">We</span></span>|  
|<span data-ttu-id="2590f-110">A</span><span class="sxs-lookup"><span data-stu-id="2590f-110">A</span></span>|<span data-ttu-id="2590f-111">think</span><span class="sxs-lookup"><span data-stu-id="2590f-111">think</span></span>|  
|<span data-ttu-id="2590f-112">A</span><span class="sxs-lookup"><span data-stu-id="2590f-112">A</span></span>|<span data-ttu-id="2590f-113">that</span><span class="sxs-lookup"><span data-stu-id="2590f-113">that</span></span>|  
|<span data-ttu-id="2590f-114">B</span><span class="sxs-lookup"><span data-stu-id="2590f-114">B</span></span>|<span data-ttu-id="2590f-115">Linq</span><span class="sxs-lookup"><span data-stu-id="2590f-115">Linq</span></span>|  
|<span data-ttu-id="2590f-116">C</span><span class="sxs-lookup"><span data-stu-id="2590f-116">C</span></span>|<span data-ttu-id="2590f-117">is</span><span class="sxs-lookup"><span data-stu-id="2590f-117">is</span></span>|  
|<span data-ttu-id="2590f-118">A</span><span class="sxs-lookup"><span data-stu-id="2590f-118">A</span></span>|<span data-ttu-id="2590f-119">really</span><span class="sxs-lookup"><span data-stu-id="2590f-119">really</span></span>|  
|<span data-ttu-id="2590f-120">B</span><span class="sxs-lookup"><span data-stu-id="2590f-120">B</span></span>|<span data-ttu-id="2590f-121">cool</span><span class="sxs-lookup"><span data-stu-id="2590f-121">cool</span></span>|  
|<span data-ttu-id="2590f-122">B</span><span class="sxs-lookup"><span data-stu-id="2590f-122">B</span></span>|<span data-ttu-id="2590f-123">!</span><span class="sxs-lookup"><span data-stu-id="2590f-123">!</span></span>|  
  
 <span data-ttu-id="2590f-124">次のグループがこの順序で作成されます。</span><span class="sxs-lookup"><span data-stu-id="2590f-124">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="2590f-125">We, think, that</span><span class="sxs-lookup"><span data-stu-id="2590f-125">We, think, that</span></span>  
  
2.  <span data-ttu-id="2590f-126">Linq</span><span class="sxs-lookup"><span data-stu-id="2590f-126">Linq</span></span>  
  
3.  <span data-ttu-id="2590f-127">is</span><span class="sxs-lookup"><span data-stu-id="2590f-127">is</span></span>  
  
4.  <span data-ttu-id="2590f-128">really</span><span class="sxs-lookup"><span data-stu-id="2590f-128">really</span></span>  
  
5.  <span data-ttu-id="2590f-129">cool, !</span><span class="sxs-lookup"><span data-stu-id="2590f-129">cool, !</span></span>  
  
 <span data-ttu-id="2590f-130">ソリューションは、結果をストリーミングで返すスレッド セーフな拡張メソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="2590f-130">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="2590f-131">つまり、ソース シーケンス内を移動するときにグループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2590f-131">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="2590f-132">`group` 演算子や `orderby` 演算子とは異なり、すべてのシーケンスの読み取りが終わる前に、呼び出し元にグループを返し始めることができます。</span><span class="sxs-lookup"><span data-stu-id="2590f-132">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="2590f-133">ソース コードのコメントで説明されているように、ソース シーケンスが反復処理されるときに各グループまたはチャンクのコピーを作成することで、スレッド セーフが実現されます。</span><span class="sxs-lookup"><span data-stu-id="2590f-133">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="2590f-134">ソース シーケンスに連続するアイテムの大きなシーケンスがある場合、共通言語ランタイムにより <xref:System.OutOfMemoryException> がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2590f-134">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2590f-135">例</span><span class="sxs-lookup"><span data-stu-id="2590f-135">Example</span></span>  
 <span data-ttu-id="2590f-136">拡張メソッドと、それを使用するクライアント コードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2590f-136">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="2590f-137">プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="2590f-137">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2590f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="2590f-138">See also</span></span>  
 [<span data-ttu-id="2590f-139">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="2590f-139">LINQ Query Expressions</span></span>](index.md)  
 
