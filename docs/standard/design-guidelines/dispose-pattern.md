---
title: "Dispose パターン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 86fef5b18ac2c1c1b1dfee385b726484191fe714
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dispose-pattern"></a><span data-ttu-id="40168-102">Dispose パターン</span><span class="sxs-lookup"><span data-stu-id="40168-102">Dispose Pattern</span></span>
<span data-ttu-id="40168-103">すべてのプログラムは、それらの実行の進行中にメモリ、システムのハンドル、またはデータベース接続など、1 つまたは複数のシステム リソースを取得します。</span><span class="sxs-lookup"><span data-stu-id="40168-103">All programs acquire one or more system resources, such as memory, system handles, or database connections, during the course of their execution.</span></span> <span data-ttu-id="40168-104">開発者は、取得し、使用後に解放する必要があるためには、このようなシステム リソースを使用する場合は注意が必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-104">Developers have to be careful when using such system resources, because they must be released after they have been acquired and used.</span></span>  
  
 <span data-ttu-id="40168-105">CLR は、自動メモリ管理のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="40168-105">The CLR provides support for automatic memory management.</span></span> <span data-ttu-id="40168-106">マネージ メモリ (c# 演算子を使用して割り当てられたメモリ`new`) 明示的に解放する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="40168-106">Managed memory (memory allocated using the C# operator `new`) does not need to be explicitly released.</span></span> <span data-ttu-id="40168-107">ガベージ コレクター (GC) によって自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="40168-107">It is released automatically by the garbage collector (GC).</span></span> <span data-ttu-id="40168-108">これにより、開発者は、メモリを解放する難しい面倒な作業を解放し、.NET Framework によって提供される画期的な生産性向上のための主な理由の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="40168-108">This frees developers from the tedious and difficult task of releasing memory and has been one of the main reasons for the unprecedented productivity afforded by the .NET Framework.</span></span>  
  
 <span data-ttu-id="40168-109">残念ながら、マネージ メモリは、さまざまな種類のシステム リソースの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="40168-109">Unfortunately, managed memory is just one of many types of system resources.</span></span> <span data-ttu-id="40168-110">ただし、マネージ メモリ以外のリソースは明示的に解放する必要あるし、アンマネージ リソースと呼びます。</span><span class="sxs-lookup"><span data-stu-id="40168-110">Resources other than managed memory still need to be released explicitly and are referred to as unmanaged resources.</span></span> <span data-ttu-id="40168-111">GC が具体的には想定していません、このようなアンマネージ リソースを管理するには、開発者の手にアンマネージ リソースを管理する責任があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="40168-111">The GC was specifically not designed to manage such unmanaged resources, which means that the responsibility for managing unmanaged resources lies in the hands of the developers.</span></span>  
  
 <span data-ttu-id="40168-112">CLR では、アンマネージ リソースを解放するときにいくつかのヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="40168-112">The CLR provides some help in releasing unmanaged resources.</span></span> <span data-ttu-id="40168-113"><xref:System.Object?displayProperty=nameWithType>仮想メソッドを宣言<xref:System.Object.Finalize%2A>(ファイナライザーとも呼ばれます) 前に、オブジェクトのメモリ GC によって解放され、アンマネージ リソースを解放するをオーバーライドすることができます、GC によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40168-113"><xref:System.Object?displayProperty=nameWithType> declares a virtual method <xref:System.Object.Finalize%2A> (also called the finalizer) that is called by the GC before the object’s memory is reclaimed by the GC and can be overridden to release unmanaged resources.</span></span> <span data-ttu-id="40168-114">ファイナライザーをオーバーライドする型は、ファイナライズ可能な型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="40168-114">Types that override the finalizer are referred to as finalizable types.</span></span>  
  
 <span data-ttu-id="40168-115">ファイナライザーは、一部のクリーンアップのシナリオで効果的なは、2 つの重要な欠点があります。</span><span class="sxs-lookup"><span data-stu-id="40168-115">Although finalizers are effective in some cleanup scenarios, they have two significant drawbacks:</span></span>  
  
-   <span data-ttu-id="40168-116">ファイナライザーは、GC では、オブジェクトがコレクションの対象となることが検出された場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40168-116">The finalizer is called when the GC detects that an object is eligible for collection.</span></span> <span data-ttu-id="40168-117">これは、不定一定時間、リソースが今後不要後に行われます。</span><span class="sxs-lookup"><span data-stu-id="40168-117">This happens at some undetermined period of time after the resource is not needed anymore.</span></span> <span data-ttu-id="40168-118">開発者がでしたまたはリソースとリソースが実際には、ファイナライザーで解放ときの時刻をリリースする場合の間の遅延が多く不足しているリソース (が簡単に不足したりリソース) を取得するプログラムでもは許容できない可能性があります。リソースの使用 (大規模なアンマネージ メモリ バッファーなど) に保持するコストのかかるがである場合。</span><span class="sxs-lookup"><span data-stu-id="40168-118">The delay between when the developer could or would like to release the resource and the time when the resource is actually released by the finalizer might be unacceptable in programs that acquire many scarce resources (resources that can be easily exhausted) or in cases in which resources are costly to keep in use (e.g., large unmanaged memory buffers).</span></span>  
  
-   <span data-ttu-id="40168-119">CLR は、ファイナライザーを呼び出す必要がある、ときに、次は、ガベージ コレクション (コレクション間で実行するファイナライザー) のラウンドするまで、オブジェクトのメモリのコレクションを延期にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-119">When the CLR needs to call a finalizer, it must postpone collection of the object’s memory until the next round of garbage collection (the finalizers run between collections).</span></span> <span data-ttu-id="40168-120">これは、オブジェクトのメモリ (およびを参照してすべてのオブジェクト) は時間の長い期間に解放されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="40168-120">This means that the object’s memory (and all objects it refers to) will not be released for a longer period of time.</span></span>  
  
 <span data-ttu-id="40168-121">そのため、ファイナライザーでのみ証明書利用者できない可能性があります、不足しているリソースを処理する場合、可能な限り早くアンマネージ リソースを解放する必要がある場合、多くのシナリオで、または高パフォーマンスの高いシナリオで適切な GC の追加のオーバーヘッドファイナライズは許容されません。</span><span class="sxs-lookup"><span data-stu-id="40168-121">Therefore, relying exclusively on finalizers might not be appropriate in many scenarios when it is important to reclaim unmanaged resources as quickly as possible, when dealing with scarce resources, or in highly performant scenarios in which the added GC overhead of finalization is unacceptable.</span></span>  
  
 <span data-ttu-id="40168-122">フレームワークは、提供、<xref:System.IDisposable?displayProperty=nameWithType>インターフェイスを手動で必要でないとすぐに、アンマネージ リソースを解放することを開発者に提供するために実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-122">The Framework provides the <xref:System.IDisposable?displayProperty=nameWithType> interface that should be implemented to provide the developer a manual way to release unmanaged resources as soon as they are not needed.</span></span> <span data-ttu-id="40168-123">用意されています、<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>するように、GC が知ることができるメソッド オブジェクトの破棄が手動で必要としない、完了するをその場合、オブジェクトのメモリを再要求できる前です。</span><span class="sxs-lookup"><span data-stu-id="40168-123">It also provides the <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> method that can tell the GC that an object was manually disposed of and does not need to be finalized anymore, in which case the object’s memory can be reclaimed earlier.</span></span> <span data-ttu-id="40168-124">実装する型、`IDisposable`インターフェイスが破棄可能な型と呼びます。</span><span class="sxs-lookup"><span data-stu-id="40168-124">Types that implement the `IDisposable` interface are referred to as disposable types.</span></span>  
  
 <span data-ttu-id="40168-125">Dispose パターンは、使用状況およびファイナライザーの実装を標準化するためのものと`IDisposable`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="40168-125">The Dispose Pattern is intended to standardize the usage and implementation of finalizers and the `IDisposable` interface.</span></span>  
  
 <span data-ttu-id="40168-126">パターンの主要な動機がの実装の複雑さを軽減するには、<xref:System.Object.Finalize%2A>と<xref:System.IDisposable.Dispose%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="40168-126">The main motivation for the pattern is to reduce the complexity of the implementation of the <xref:System.Object.Finalize%2A> and the <xref:System.IDisposable.Dispose%2A> methods.</span></span> <span data-ttu-id="40168-127">複雑さのメソッドがいくつかのコード パスが (相違点は後で説明) を共有することに由来します。</span><span class="sxs-lookup"><span data-stu-id="40168-127">The complexity stems from the fact that the methods share some but not all code paths (the differences are described later in the chapter).</span></span> <span data-ttu-id="40168-128">さらに、履歴上の理由から決定論的リソース管理のための言語サポートの進化に関連するパターンの一部の要素があります。</span><span class="sxs-lookup"><span data-stu-id="40168-128">In addition, there are historical reasons for some elements of the pattern related to the evolution of language support for deterministic resource management.</span></span>  
  
 <span data-ttu-id="40168-129">**✓ しないで**破棄可能な型のインスタンスを含む型で、基本的な Dispose パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="40168-129">**✓ DO** implement the Basic Dispose Pattern on types containing instances of disposable types.</span></span> <span data-ttu-id="40168-130">参照してください、 [Dispose の基本的なパターン](#basic_pattern)基本的なパターンの詳細セクションです。</span><span class="sxs-lookup"><span data-stu-id="40168-130">See the [Basic Dispose Pattern](#basic_pattern) section for details on the basic pattern.</span></span>  
  
 <span data-ttu-id="40168-131">型が破棄可能なその他のオブジェクトの有効期間を担当する場合は、開発者はすぎる、それらを破棄する方法を必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-131">If a type is responsible for the lifetime of other disposable objects, developers need a way to dispose of them, too.</span></span> <span data-ttu-id="40168-132">使用して、コンテナーの`Dispose`実現する便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="40168-132">Using the container’s `Dispose` method is a convenient way to make this possible.</span></span>  
  
 <span data-ttu-id="40168-133">**✓ しないで**基本の Dispose パターンを実装し、保持しているリソースを明示的に解放できる必要があると、ファイナライザーがない型でファイナライザーを用意します。</span><span class="sxs-lookup"><span data-stu-id="40168-133">**✓ DO** implement the Basic Dispose Pattern and provide a finalizer on types holding resources that need to be freed explicitly and that do not have finalizers.</span></span>  
  
 <span data-ttu-id="40168-134">たとえば、アンマネージ メモリ バッファーを格納する型で、パターンを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-134">For example, the pattern should be implemented on types storing unmanaged memory buffers.</span></span> <span data-ttu-id="40168-135">[ファイナライズ可能な型](#finalizable_types)ファイナライザーを実装する関連のガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="40168-135">The [Finalizable Types](#finalizable_types) section discusses guidelines related to implementing finalizers.</span></span>  
  
 <span data-ttu-id="40168-136">**✓ を検討してください**基本の Dispose パターンを実装するクラスでのリソースとアンマネージ自体を保持しないことや、破棄可能なオブジェクトは、実行のサブタイプをされている可能性がします。</span><span class="sxs-lookup"><span data-stu-id="40168-136">**✓ CONSIDER** implementing the Basic Dispose Pattern on classes that themselves don’t hold unmanaged resources or disposable objects but are likely to have subtypes that do.</span></span>  
  
 <span data-ttu-id="40168-137">これの好例が、<xref:System.IO.Stream?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="40168-137">A great example of this is the <xref:System.IO.Stream?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="40168-138">抽象基本クラスのすべてのリソースを保持しませんが、そのサブクラスのほとんどは、このため、このパターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="40168-138">Although it is an abstract base class that doesn’t hold any resources, most of its subclasses do and because of this, it implements this pattern.</span></span>  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a><span data-ttu-id="40168-139">基本の Dispose パターン</span><span class="sxs-lookup"><span data-stu-id="40168-139">Basic Dispose Pattern</span></span>  
 <span data-ttu-id="40168-140">基本的なパターンの実装では、実装では、`System.IDisposable`インターフェイスを宣言する、`Dispose(bool)`間で共有するすべてのリソースのクリーンアップ ロジックを実装するメソッド、`Dispose`メソッドと省略可能な終了します。</span><span class="sxs-lookup"><span data-stu-id="40168-140">The basic implementation of the pattern involves implementing the `System.IDisposable` interface and declaring the `Dispose(bool)` method that implements all resource cleanup logic to be shared between the `Dispose` method and the optional finalizer.</span></span>  
  
 <span data-ttu-id="40168-141">次の例は、基本的なパターンの簡単な実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="40168-141">The following example shows a simple implementation of the basic pattern:</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="40168-142">ブール型パラメーター`disposing`から呼び出されたメソッドであるかどうかを示す、`IDisposable.Dispose`実装またはファイナライザーからです。</span><span class="sxs-lookup"><span data-stu-id="40168-142">The Boolean parameter `disposing` indicates whether the method was invoked from the `IDisposable.Dispose` implementation or from the finalizer.</span></span> <span data-ttu-id="40168-143">`Dispose(bool)`実装は、その他の参照オブジェクト (上記のサンプルのリソース フィールドなど) にアクセスする前に、パラメーターを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-143">The `Dispose(bool)` implementation should check the parameter before accessing other reference objects (e.g., the resource field in the preceding sample).</span></span> <span data-ttu-id="40168-144">このようなオブジェクトからこのメソッドが呼び出された場合にのみアクセスする必要があります、`IDisposable.Dispose`実装 (ときに、`disposing`パラメーターが true に等しい)。</span><span class="sxs-lookup"><span data-stu-id="40168-144">Such objects should only be accessed when the method is called from the `IDisposable.Dispose` implementation (when the `disposing` parameter is equal to true).</span></span> <span data-ttu-id="40168-145">メソッドがファイナライザーから呼び出された場合 (`disposing`は false)、その他のオブジェクトにアクセスしないようにします。</span><span class="sxs-lookup"><span data-stu-id="40168-145">If the method is invoked from the finalizer (`disposing` is false), other objects should not be accessed.</span></span> <span data-ttu-id="40168-146">オブジェクトが予期しない順序で完了し、ため、またはその依存関係のいずれかが既にが完了することです。</span><span class="sxs-lookup"><span data-stu-id="40168-146">The reason is that objects are finalized in an unpredictable order and so they, or any of their dependencies, might already have been finalized.</span></span>  
  
 <span data-ttu-id="40168-147">また、このセクションでは、Dispose パターンが実装していません基数を持つクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="40168-147">Also, this section applies to classes with a base that does not already implement the Dispose Pattern.</span></span> <span data-ttu-id="40168-148">オーバーライドするだけで既にパターンを実装するクラスから継承している場合、`Dispose(bool)`追加のリソースのクリーンアップ ロジックを提供します。</span><span class="sxs-lookup"><span data-stu-id="40168-148">If you are inheriting from a class that already implements the pattern, simply override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="40168-149">**✓ しないで**保護された仮想 void を宣言`Dispose(bool disposing)`アンマネージ リソースの解放に関連するすべてのロジックを集中管理するメソッド。</span><span class="sxs-lookup"><span data-stu-id="40168-149">**✓ DO** declare a protected virtual void `Dispose(bool disposing)` method to centralize all logic related to releasing unmanaged resources.</span></span>  
  
 <span data-ttu-id="40168-150">すべてのリソースのクリーンアップは、このメソッドで発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-150">All resource cleanup should occur in this method.</span></span> <span data-ttu-id="40168-151">両方のファイナライザーからメソッドを呼び出したと`IDisposable.Dispose`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="40168-151">The method is called from both the finalizer and the `IDisposable.Dispose` method.</span></span> <span data-ttu-id="40168-152">パラメーターは、ファイナライザーの内部から呼び出されている場合は false になります。</span><span class="sxs-lookup"><span data-stu-id="40168-152">The parameter will be false if being invoked from inside a finalizer.</span></span> <span data-ttu-id="40168-153">終了処理中に実行されるコードがファイナライズ可能なその他のオブジェクトにアクセスしていないことを確認することを使用してください。</span><span class="sxs-lookup"><span data-stu-id="40168-153">It should be used to ensure any code running during finalization is not accessing other finalizable objects.</span></span> <span data-ttu-id="40168-154">ファイナライザーの実装の詳細については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="40168-154">Details of implementing finalizers are described in the next section.</span></span>  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 <span data-ttu-id="40168-155">**✓ しないで**実装、`IDisposable`だけ呼び出すことによってインターフェイス`Dispose(true)`続く`GC.SuppressFinalize(this)`です。</span><span class="sxs-lookup"><span data-stu-id="40168-155">**✓ DO** implement the `IDisposable` interface by simply calling `Dispose(true)` followed by `GC.SuppressFinalize(this)`.</span></span>  
  
 <span data-ttu-id="40168-156">呼び出し`SuppressFinalize`場合にのみ発生`Dispose(true)`が正常に実行します。</span><span class="sxs-lookup"><span data-stu-id="40168-156">The call to `SuppressFinalize` should only occur if `Dispose(true)` executes successfully.</span></span>  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 <span data-ttu-id="40168-157">**X しないで**パラメーターなしで行う`Dispose`仮想メソッドです。</span><span class="sxs-lookup"><span data-stu-id="40168-157">**X DO NOT** make the parameterless `Dispose` method virtual.</span></span>  
  
 <span data-ttu-id="40168-158">`Dispose(bool)`メソッドであるサブクラスによってオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-158">The `Dispose(bool)` method is the one that should be overridden by subclasses.</span></span>  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 <span data-ttu-id="40168-159">**X しないで**のすべてのオーバー ロードを宣言、`Dispose`以外のメソッド`Dispose()`と`Dispose(bool)`です。</span><span class="sxs-lookup"><span data-stu-id="40168-159">**X DO NOT** declare any overloads of the `Dispose` method other than `Dispose()` and `Dispose(bool)`.</span></span>  
  
 <span data-ttu-id="40168-160">`Dispose`このパターンを体系化し、実装、ユーザー、およびコンパイラの間での混乱を回避するために予約語を考慮ください。</span><span class="sxs-lookup"><span data-stu-id="40168-160">`Dispose` should be considered a reserved word to help codify this pattern and prevent confusion among implementers, users, and compilers.</span></span> <span data-ttu-id="40168-161">一部の言語は、特定の種類に自動的にこのパターンを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="40168-161">Some languages might choose to automatically implement this pattern on certain types.</span></span>  
  
 <span data-ttu-id="40168-162">**✓ しないで**を許可する、`Dispose(bool)`に複数回呼び出されるメソッド。</span><span class="sxs-lookup"><span data-stu-id="40168-162">**✓ DO** allow the `Dispose(bool)` method to be called more than once.</span></span> <span data-ttu-id="40168-163">メソッドは、最初の呼び出し後に何もすることもできます。</span><span class="sxs-lookup"><span data-stu-id="40168-163">The method might choose to do nothing after the first call.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="40168-164">**避け x**内から例外をスローして`Dispose(bool)`されている重要な状況で格納しているプロセスが破損している場合を除き (リークを一貫性のない共有状態などです。)。</span><span class="sxs-lookup"><span data-stu-id="40168-164">**X AVOID** throwing an exception from within `Dispose(bool)` except under critical situations where the containing process has been corrupted (leaks, inconsistent shared state, etc.).</span></span>  
  
 <span data-ttu-id="40168-165">ユーザーが期待するへの呼び出し`Dispose`例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="40168-165">Users expect that a call to `Dispose` will not raise an exception.</span></span>  
  
 <span data-ttu-id="40168-166">場合`Dispose`例外を発生させる可能性があります、これ以上の finally ブロックのクリーンアップ ロジックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="40168-166">If `Dispose` could raise an exception, further finally-block cleanup logic will not execute.</span></span> <span data-ttu-id="40168-167">この問題を回避する、ユーザーが すべての呼び出しをラップする必要があります`Dispose`(内で、finally ブロック!)、try ブロックで非常に複雑なクリーンアップ ハンドラーにつながります。</span><span class="sxs-lookup"><span data-stu-id="40168-167">To work around this, the user would need to wrap every call to `Dispose` (within the finally block!) in a try block, which leads to very complex cleanup handlers.</span></span> <span data-ttu-id="40168-168">実行している場合、`Dispose(bool disposing)`メソッド、破棄が false の場合に例外がスローされません。</span><span class="sxs-lookup"><span data-stu-id="40168-168">If executing a `Dispose(bool disposing)` method, never throw an exception if disposing is false.</span></span> <span data-ttu-id="40168-169">これによりファイナライザー コンテキスト内で実行されている場合、プロセスが終了されます。</span><span class="sxs-lookup"><span data-stu-id="40168-169">Doing so will terminate the process if executing inside a finalizer context.</span></span>  
  
 <span data-ttu-id="40168-170">**✓ しないで**スロー、<xref:System.ObjectDisposedException>オブジェクトが破棄された後は使用できませんのすべてのメンバーからです。</span><span class="sxs-lookup"><span data-stu-id="40168-170">**✓ DO** throw an <xref:System.ObjectDisposedException> from any member that cannot be used after the object has been disposed of.</span></span>  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 <span data-ttu-id="40168-171">**✓ を検討してください**メソッドを提供する`Close()`に加え、`Dispose()`領域での一般的な用語が閉じるかどうかは。</span><span class="sxs-lookup"><span data-stu-id="40168-171">**✓ CONSIDER** providing method `Close()`, in addition to the `Dispose()`, if close is standard terminology in the area.</span></span>  
  
 <span data-ttu-id="40168-172">これを行うことが重要を作成すること、`Close`実装と同じ`Dispose`を実装することを検討してください、`IDisposable.Dispose`メソッドに明示的にします。</span><span class="sxs-lookup"><span data-stu-id="40168-172">When doing so, it is important that you make the `Close` implementation identical to `Dispose` and consider implementing the `IDisposable.Dispose` method explicitly.</span></span>  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a><span data-ttu-id="40168-173">ファイナライズ可能な型</span><span class="sxs-lookup"><span data-stu-id="40168-173">Finalizable Types</span></span>  
 <span data-ttu-id="40168-174">ファイナライズ可能な型はファイナライザーをオーバーライドして、終了コードのパスを提供することによって、基本的な Dispose パターンを拡張する型は、`Dispose(bool)`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="40168-174">Finalizable types are types that extend the Basic Dispose Pattern by overriding the finalizer and providing finalization code path in the `Dispose(bool)` method.</span></span>  
  
 <span data-ttu-id="40168-175">ファイナライザーは、実行中に、システムの状態に関する (通常は有効な) 仮定をすることはできませんので、主に正しく実装する非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="40168-175">Finalizers are notoriously difficult to implement correctly, primarily because you cannot make certain (normally valid) assumptions about the state of the system during their execution.</span></span> <span data-ttu-id="40168-176">慎重に検討には、次のガイドラインを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40168-176">The following guidelines should be taken into careful consideration.</span></span>  
  
 <span data-ttu-id="40168-177">ガイドラインの一部がしないようにだけに適用されるに注意してください、`Finalize`メソッド、ファイナライザーからすべてのコードが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40168-177">Note that some of the guidelines apply not just to the `Finalize` method, but to any code called from a finalizer.</span></span> <span data-ttu-id="40168-178">つまり、ロジック内で実行される場合は、基本的な Dispose パターン以前に定義した、`Dispose(bool disposing)`ときに、`disposing`パラメーターを false にします。</span><span class="sxs-lookup"><span data-stu-id="40168-178">In the case of the Basic Dispose Pattern previously defined, this means logic that executes inside `Dispose(bool disposing)` when the `disposing` parameter is false.</span></span>  
  
 <span data-ttu-id="40168-179">基本クラス既にファイナライズ可能な基本的な Dispose パターンを実装場合、する必要がありますはオーバーライド`Finalize`もう一度です。</span><span class="sxs-lookup"><span data-stu-id="40168-179">If the base class already is finalizable and implements the Basic Dispose Pattern, you should not override `Finalize` again.</span></span> <span data-ttu-id="40168-180">代わりにだけをオーバーライドする、`Dispose(bool)`追加のリソースのクリーンアップ ロジックを提供します。</span><span class="sxs-lookup"><span data-stu-id="40168-180">You should instead just override the `Dispose(bool)` method to provide additional resource cleanup logic.</span></span>  
  
 <span data-ttu-id="40168-181">次のコードでは、ファイナライズ可能な型の例を示します。</span><span class="sxs-lookup"><span data-stu-id="40168-181">The following code shows an example of a finalizable type:</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 <span data-ttu-id="40168-182">**避け x**ファイナライズ可能な型を作成します。</span><span class="sxs-lookup"><span data-stu-id="40168-182">**X AVOID** making types finalizable.</span></span>  
  
 <span data-ttu-id="40168-183">いかなる場合においてもいると思われるファイナライザーが必要な慎重に検討します。</span><span class="sxs-lookup"><span data-stu-id="40168-183">Carefully consider any case in which you think a finalizer is needed.</span></span> <span data-ttu-id="40168-184">実際のパフォーマンスとコードの両方の複雑さの観点からのファイナライザーを持つインスタンスに関連付けられているコスト。</span><span class="sxs-lookup"><span data-stu-id="40168-184">There is a real cost associated with instances with finalizers, from both a performance and code complexity standpoint.</span></span> <span data-ttu-id="40168-185">などのリソースのラッパーを使用して必要に応じて<xref:System.Runtime.InteropServices.SafeHandle>を可能な場合は、アンマネージ リソースをカプセル化する、その場合、ファイナライザーが不要になるラッパーが独自のリソースのクリーンアップを行うためです。</span><span class="sxs-lookup"><span data-stu-id="40168-185">Prefer using resource wrappers such as <xref:System.Runtime.InteropServices.SafeHandle> to encapsulate unmanaged resources where possible, in which case a finalizer becomes unnecessary because the wrapper is responsible for its own resource cleanup.</span></span>  
  
 <span data-ttu-id="40168-186">**X しないで**ファイナライズ可能な値の型を作成します。</span><span class="sxs-lookup"><span data-stu-id="40168-186">**X DO NOT** make value types finalizable.</span></span>  
  
 <span data-ttu-id="40168-187">実際には参照型のみが、CLR によって終了取得され、値の型でファイナライザーを配置するあらゆる試みは無視されるためです。</span><span class="sxs-lookup"><span data-stu-id="40168-187">Only reference types actually get finalized by the CLR, and thus any attempt to place a finalizer on a value type will be ignored.</span></span> <span data-ttu-id="40168-188">C# および C++ コンパイラは、この規則を強制します。</span><span class="sxs-lookup"><span data-stu-id="40168-188">The C# and C++ compilers enforce this rule.</span></span>  
  
 <span data-ttu-id="40168-189">**✓ しないで**型は独自のファイナライザーがない、アンマネージ リソースを解放する必要がある場合の種類をファイナライズようにします。</span><span class="sxs-lookup"><span data-stu-id="40168-189">**✓ DO** make a type finalizable if the type is responsible for releasing an unmanaged resource that does not have its own finalizer.</span></span>  
  
 <span data-ttu-id="40168-190">ファイナライザーを実装する場合を呼び出すだけ`Dispose(false)`内のすべてのリソースのクリーンアップ ロジックを配置し、`Dispose(bool disposing)`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="40168-190">When implementing the finalizer, simply call `Dispose(false)` and place all resource cleanup logic inside the `Dispose(bool disposing)` method.</span></span>  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="40168-191">**✓ しないで**ファイナライズ可能な型で、基本的な Dispose パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="40168-191">**✓ DO** implement the Basic Dispose Pattern on every finalizable type.</span></span>  
  
 <span data-ttu-id="40168-192">これにより、型のユーザーは明示的にファイナライザーが担当する同じリソースの確定的なクリーンアップを実行することを意味します。</span><span class="sxs-lookup"><span data-stu-id="40168-192">This gives users of the type a means to explicitly perform deterministic cleanup of those same resources for which the finalizer is responsible.</span></span>  
  
 <span data-ttu-id="40168-193">**X しないで**こと、が既に終了されている重大なリスクがあるため、ファイナライザーのコード パスに、ファイナライズ可能なオブジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="40168-193">**X DO NOT** access any finalizable objects in the finalizer code path, because there is significant risk that they will have already been finalized.</span></span>  
  
 <span data-ttu-id="40168-194">たとえば、別のファイナライズ可能なオブジェクト B を参照しているファイナライズ可能なオブジェクト A 確実にでは使用できません B A のファイナライザー、またはその逆です。</span><span class="sxs-lookup"><span data-stu-id="40168-194">For example, a finalizable object A that has a reference to another finalizable object B cannot reliably use B in A’s finalizer, or vice versa.</span></span> <span data-ttu-id="40168-195">ファイナライザーは、(重要な終了処理の弱い順序保証) する場合を除きランダムな順序で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="40168-195">Finalizers are called in a random order (short of a weak ordering guarantee for critical finalization).</span></span>  
  
 <span data-ttu-id="40168-196">また、アプリケーション ドメインのアンロード中またはプロセスの終了中に、静的変数に格納されているオブジェクトは特定の時点で収集取得こともあります。</span><span class="sxs-lookup"><span data-stu-id="40168-196">Also, be aware that objects stored in static variables will get collected at certain points during an application domain unload or while exiting the process.</span></span> <span data-ttu-id="40168-197">ファイナライズ可能なオブジェクト (または静的変数に格納された値を使用する静的メソッドを呼び出す) を参照する静的変数ができない可能性がありますにアクセスする場合は安全な<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>は true を返します。</span><span class="sxs-lookup"><span data-stu-id="40168-197">Accessing a static variable that refers to a finalizable object (or calling a static method that might use values stored in static variables) might not be safe if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> returns true.</span></span>  
  
 <span data-ttu-id="40168-198">**✓ しないで**ように、`Finalize`保護されているメソッド。</span><span class="sxs-lookup"><span data-stu-id="40168-198">**✓ DO** make your `Finalize` method protected.</span></span>  
  
 <span data-ttu-id="40168-199">C#、C++、および VB.NET の開発者は、このガイドラインを適用すると、コンパイラに役立つため、これについて心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="40168-199">C#, C++, and VB.NET developers do not need to worry about this, because the compilers help to enforce this guideline.</span></span>  
  
 <span data-ttu-id="40168-200">**X しないで**システムに重大な障害を除く、ファイナライザーのロジックから使用すると、例外のエスケープします。</span><span class="sxs-lookup"><span data-stu-id="40168-200">**X DO NOT** let exceptions escape from the finalizer logic, except for system-critical failures.</span></span>  
  
 <span data-ttu-id="40168-201">ファイナライザーから例外をスローすると場合、CLR はシャット ダウンの時点で .NET Framework version 2.0)、プロセス全体を実行して適切な方法で解放されてからのリソースから他のファイナライザーを防止します。</span><span class="sxs-lookup"><span data-stu-id="40168-201">If an exception is thrown from a finalizer, the CLR will shut down the entire process (as of .NET Framework version 2.0), preventing other finalizers from executing and resources from being released in a controlled manner.</span></span>  
  
 <span data-ttu-id="40168-202">**✓ を検討してください**を作成して、重要なファイナライズ可能なオブジェクトを使用して (を含む型階層を持つ型<xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) の状況でファイナライザーどうしても必要があります実行発生した場合でも強制アプリケーション ドメインのアンロード スレッド中止します。</span><span class="sxs-lookup"><span data-stu-id="40168-202">**✓ CONSIDER** creating and using a critical finalizable object (a type with a type hierarchy that contains <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) for situations in which a finalizer absolutely must execute even in the face of forced application domain unloads and thread aborts.</span></span>  
  
 <span data-ttu-id="40168-203">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="40168-203">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="40168-204">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="40168-204">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40168-205">参照</span><span class="sxs-lookup"><span data-stu-id="40168-205">See Also</span></span>  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="40168-206">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="40168-206">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="40168-207">共通デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="40168-207">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [<span data-ttu-id="40168-208">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="40168-208">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
