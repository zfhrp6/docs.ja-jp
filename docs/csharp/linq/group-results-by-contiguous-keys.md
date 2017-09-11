---
title: "連続するキーで結果をグループ化する"
description: "連続するキーで結果をグループ化する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ddd028a3aad5186ef6773b32e9f9e8e1cbff95fc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="ccf93-104">連続するキーで結果をグループ化する</span><span class="sxs-lookup"><span data-stu-id="ccf93-104">Group results by contiguous keys</span></span>

<span data-ttu-id="ccf93-105">要素をグループ化し、連続するキーのサブシーケンスを表すチャンクにする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ccf93-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="ccf93-106">たとえば、次の一連のキーと値のペアがあるとします。</span><span class="sxs-lookup"><span data-stu-id="ccf93-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="ccf93-107">キー</span><span class="sxs-lookup"><span data-stu-id="ccf93-107">Key</span></span>|<span data-ttu-id="ccf93-108">値</span><span class="sxs-lookup"><span data-stu-id="ccf93-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="ccf93-109">A</span><span class="sxs-lookup"><span data-stu-id="ccf93-109">A</span></span>|<span data-ttu-id="ccf93-110">水</span><span class="sxs-lookup"><span data-stu-id="ccf93-110">We</span></span>|  
|<span data-ttu-id="ccf93-111">A</span><span class="sxs-lookup"><span data-stu-id="ccf93-111">A</span></span>|<span data-ttu-id="ccf93-112">think</span><span class="sxs-lookup"><span data-stu-id="ccf93-112">think</span></span>|  
|<span data-ttu-id="ccf93-113">A</span><span class="sxs-lookup"><span data-stu-id="ccf93-113">A</span></span>|<span data-ttu-id="ccf93-114">that</span><span class="sxs-lookup"><span data-stu-id="ccf93-114">that</span></span>|  
|<span data-ttu-id="ccf93-115">B</span><span class="sxs-lookup"><span data-stu-id="ccf93-115">B</span></span>|<span data-ttu-id="ccf93-116">Linq</span><span class="sxs-lookup"><span data-stu-id="ccf93-116">Linq</span></span>|  
|<span data-ttu-id="ccf93-117">C</span><span class="sxs-lookup"><span data-stu-id="ccf93-117">C</span></span>|<span data-ttu-id="ccf93-118">is</span><span class="sxs-lookup"><span data-stu-id="ccf93-118">is</span></span>|  
|<span data-ttu-id="ccf93-119">A</span><span class="sxs-lookup"><span data-stu-id="ccf93-119">A</span></span>|<span data-ttu-id="ccf93-120">really</span><span class="sxs-lookup"><span data-stu-id="ccf93-120">really</span></span>|  
|<span data-ttu-id="ccf93-121">B</span><span class="sxs-lookup"><span data-stu-id="ccf93-121">B</span></span>|<span data-ttu-id="ccf93-122">cool</span><span class="sxs-lookup"><span data-stu-id="ccf93-122">cool</span></span>|  
|<span data-ttu-id="ccf93-123">B</span><span class="sxs-lookup"><span data-stu-id="ccf93-123">B</span></span>|<span data-ttu-id="ccf93-124">!</span><span class="sxs-lookup"><span data-stu-id="ccf93-124">!</span></span>|  
  
 <span data-ttu-id="ccf93-125">次のグループがこの順序で作成されます。</span><span class="sxs-lookup"><span data-stu-id="ccf93-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="ccf93-126">We, think, that</span><span class="sxs-lookup"><span data-stu-id="ccf93-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="ccf93-127">Linq</span><span class="sxs-lookup"><span data-stu-id="ccf93-127">Linq</span></span>  
  
3.  <span data-ttu-id="ccf93-128">is</span><span class="sxs-lookup"><span data-stu-id="ccf93-128">is</span></span>  
  
4.  <span data-ttu-id="ccf93-129">really</span><span class="sxs-lookup"><span data-stu-id="ccf93-129">really</span></span>  
  
5.  <span data-ttu-id="ccf93-130">cool, !</span><span class="sxs-lookup"><span data-stu-id="ccf93-130">cool, !</span></span>  
  
 <span data-ttu-id="ccf93-131">ソリューションは、結果をストリーミングで返すスレッド セーフな拡張メソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="ccf93-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="ccf93-132">つまり、ソース シーケンス内を移動するときにグループが作成されます。</span><span class="sxs-lookup"><span data-stu-id="ccf93-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="ccf93-133">`group` 演算子や `orderby` 演算子とは異なり、すべてのシーケンスの読み取りが終わる前に、呼び出し元にグループを返し始めることができます。</span><span class="sxs-lookup"><span data-stu-id="ccf93-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="ccf93-134">ソース コードのコメントで説明されているように、ソース シーケンスが反復処理されるときに各グループまたはチャンクのコピーを作成することで、スレッド セーフが実現されます。</span><span class="sxs-lookup"><span data-stu-id="ccf93-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="ccf93-135">ソース シーケンスに連続するアイテムの大きなシーケンスがある場合、共通言語ランタイムにより <xref:System.OutOfMemoryException> がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ccf93-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccf93-136">例</span><span class="sxs-lookup"><span data-stu-id="ccf93-136">Example</span></span>  
 <span data-ttu-id="ccf93-137">拡張メソッドと、それを使用するクライアント コードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ccf93-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 <span data-ttu-id="ccf93-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ccf93-138">[!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]</span></span>  
  
 <span data-ttu-id="ccf93-139">プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="ccf93-139">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf93-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccf93-140">See also</span></span>  
 [<span data-ttu-id="ccf93-141">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="ccf93-141">LINQ Query Expressions</span></span>](index.md)   
 

