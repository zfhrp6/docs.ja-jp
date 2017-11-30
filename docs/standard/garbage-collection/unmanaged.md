---
title: "アンマネージ リソースのクリーンアップ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c94a449edbbe38c4028e27fd946b66a054badf51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="5127f-102">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="5127f-102">Cleaning Up Unmanaged Resources</span></span>
<span data-ttu-id="5127f-103">アプリで作成されるオブジェクトのほとんどに依存することができます。ガベージ コレクターが NET のメモリ管理を処理します。</span><span class="sxs-lookup"><span data-stu-id="5127f-103">For the majority of the objects that your app creates, you can rely on .NET's garbage collector to handle memory management.</span></span> <span data-ttu-id="5127f-104">しかし、アンマネージ リソースを含むオブジェクトを作成する場合は、アプリケーションでそのオブジェクトの使用が終了した時点で、そのリソースを明示的に解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5127f-104">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them in your app.</span></span> <span data-ttu-id="5127f-105">アンマネージ リソースの種類で最も一般的なのは、ファイル、ウィンドウ、ネットワーク接続、データベース接続などのオペレーティング システム リソースをラップしたオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="5127f-105">The most common types of unmanaged resource are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="5127f-106">ガベージ コレクターは、アンマネージ リソースをカプセル化したオブジェクトを有効期間全体にわたって監視できますが、アンマネージ リソースを解放しクリーンアップする方法については情報を持っていません。</span><span class="sxs-lookup"><span data-stu-id="5127f-106">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>  
  
 <span data-ttu-id="5127f-107">型でアンマネージ リソースを使用している場合は、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5127f-107">If your types use unmanaged resources, you should do the following:</span></span>  
  
-   <span data-ttu-id="5127f-108">実装、 [dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="5127f-108">Implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md).</span></span> <span data-ttu-id="5127f-109">これは、アンマネージ リソースの確定的解放を有効にするために <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5127f-109">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of  unmanaged resources.</span></span> <span data-ttu-id="5127f-110">型のコンシューマーはオブジェクト (および使用するリソース) が不要になると <xref:System.IDisposable.Dispose%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5127f-110">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) is no longer needed.</span></span> <span data-ttu-id="5127f-111"><xref:System.IDisposable.Dispose%2A> メソッドはアンマネージ リソースを直ちに解放します。</span><span class="sxs-lookup"><span data-stu-id="5127f-111">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>  
  
-   <span data-ttu-id="5127f-112">型のコンシューマーが <xref:System.IDisposable.Dispose%2A> の呼び出しを忘れた場合にアンマネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="5127f-112">Provide for your unmanaged resources to be released in the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>.</span></span> <span data-ttu-id="5127f-113">これには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="5127f-113">There are two ways to do this:</span></span>  
  
    -   <span data-ttu-id="5127f-114">アンマネージ リソースをラップするセーフ ハンドルを使用します。</span><span class="sxs-lookup"><span data-stu-id="5127f-114">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="5127f-115">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5127f-115">This is the recommended technique.</span></span> <span data-ttu-id="5127f-116">セーフ ハンドルは <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> クラスから派生し、堅牢な <xref:System.Object.Finalize%2A> メソッドを含みます。</span><span class="sxs-lookup"><span data-stu-id="5127f-116">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="5127f-117">セーフ ハンドルを使用するときは、単純に <xref:System.IDisposable> インターフェイスを実装し、<xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> の実装でセーフ ハンドルの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5127f-117">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="5127f-118">セーフ ハンドルのファイナライザーは、<xref:System.IDisposable.Dispose%2A> メソッドが呼び出されなかった場合、ガベージ コレクターによって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5127f-118">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>  
  
         <span data-ttu-id="5127f-119">または</span><span class="sxs-lookup"><span data-stu-id="5127f-119">—or—</span></span>  
  
    -   <span data-ttu-id="5127f-120"><xref:System.Object.Finalize%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="5127f-120">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5127f-121">終了処理では、型のコンシューマーが <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> を呼び出してアンマネージ リソースを確定的に破棄しなかった場合に、リソースを非確定的に解放できます。</span><span class="sxs-lookup"><span data-stu-id="5127f-121">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="5127f-122">ただし、オブジェクトの終了処理は複雑でエラーが発生しやすい操作であるため、独自のファイナライザーを用意する代わりに、セーフ ハンドルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5127f-122">However, because object finalization can be a complex and error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>  
  
 <span data-ttu-id="5127f-123">これで型のコンシューマーは、<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を直接呼び出して、アンマネージ リソースで使用されるメモリを解放することができます。</span><span class="sxs-lookup"><span data-stu-id="5127f-123">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="5127f-124"><xref:System.IDisposable.Dispose%2A> メソッドを適切に実装すると、セーフ ハンドルの <xref:System.Object.Finalize%2A> メソッドまたは <xref:System.Object.Finalize%2A?displayProperty=nameWithType> メソッドの独自のオーバーライドは、<xref:System.IDisposable.Dispose%2A> メソッドが呼び出されなかった場合にリソースをクリーンアップするための安全装置になります。</span><span class="sxs-lookup"><span data-stu-id="5127f-124">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5127f-125">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5127f-125">In This Section</span></span>  
 [<span data-ttu-id="5127f-126">Dispose メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="5127f-126">Implementing a Dispose Method</span></span>](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="5127f-127">実装する方法について説明します、 [dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)アンマネージ リソースを解放するためです。</span><span class="sxs-lookup"><span data-stu-id="5127f-127">Describes how to implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) for releasing unmanaged resources.</span></span>  
  
 [<span data-ttu-id="5127f-128">IDisposable を実装するオブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="5127f-128">Using Objects That Implement IDisposable</span></span>](../../../docs/standard/garbage-collection/using-objects.md)  
 <span data-ttu-id="5127f-129">型のコンシューマーが <xref:System.IDisposable.Dispose%2A> の実装を確実に呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5127f-129">Describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="5127f-130">このためには、C# の `using` ステートメントまたは Visual Basic の `Using` ステートメントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5127f-130">We recommend using the C# `using` statement or the Visual Basic `Using` statement to do this.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5127f-131">参照</span><span class="sxs-lookup"><span data-stu-id="5127f-131">Reference</span></span>  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 <span data-ttu-id="5127f-132">アンマネージ リソースの解放のための <xref:System.IDisposable.Dispose%2A> メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="5127f-132">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 <span data-ttu-id="5127f-133">アンマネージ リソースが <xref:System.IDisposable.Dispose%2A> メソッドによって解放されない場合に、オブジェクトの終了処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="5127f-133">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span>  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 <span data-ttu-id="5127f-134">終了処理を抑制します。</span><span class="sxs-lookup"><span data-stu-id="5127f-134">Suppresses finalization.</span></span> <span data-ttu-id="5127f-135">このメソッドは、慣例的に `Dispose` メソッドから呼び出され、ファイナライザーが実行されないようにします。</span><span class="sxs-lookup"><span data-stu-id="5127f-135">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span>
