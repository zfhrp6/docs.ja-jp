---
title: ファイナライザー (C# プログラミング ガイド)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="1dbac-102">ファイナライザー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1dbac-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="1dbac-103">ファイナライザーは、クラスのインスタンスを破棄するために使います。</span><span class="sxs-lookup"><span data-stu-id="1dbac-103">Finalizers are used to destruct instances of classes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dbac-104">コメント</span><span class="sxs-lookup"><span data-stu-id="1dbac-104">Remarks</span></span>  
  
-   <span data-ttu-id="1dbac-105">ファイナライザーは、構造体には定義できません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="1dbac-106">クラスでだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="1dbac-107">クラスで使用できるファイナライザーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="1dbac-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="1dbac-108">ファイナライザーを継承またはオーバーロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="1dbac-109">ファイナライザーを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-109">Finalizers cannot be called.</span></span> <span data-ttu-id="1dbac-110">デストラクターは自動的に起動されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="1dbac-111">ファイナライザーは修飾子を取らず、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="1dbac-112">たとえば、次はクラス `Car` に対するファイナライザーの宣言です。</span><span class="sxs-lookup"><span data-stu-id="1dbac-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

<span data-ttu-id="1dbac-113">ファイナライザーは、式本体の定義として実行することもできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="1dbac-114">ファイナライザーは、オブジェクトの基底クラスで <xref:System.Object.Finalize%2A> を暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="1dbac-115">そのため、ファイナライザーの呼び出しは、暗黙的に次のコードに解釈されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="1dbac-116">つまり、派生が最も多いクラスから派生が最も少ないクラスまで、継承チェーンのすべてのインスタンスに対して、`Finalize` メソッドが再帰的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dbac-117">空のファイナライザーは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1dbac-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="1dbac-118">ファイナライザーがクラスに存在するときは、エントリが `Finalize` キューで作成されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="1dbac-119">ファイナライザーを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="1dbac-120">ファイナライザーが空の場合、パフォーマンスを不必要に低下させるだけです。</span><span class="sxs-lookup"><span data-stu-id="1dbac-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="1dbac-121">ファイナライザーがいつ呼び出されるかはガベージ コレクターによって決定されるため、プログラマは制御できません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="1dbac-122">ガベージ コレクターは、アプリケーションが使用していないオブジェクトをチェックします。</span><span class="sxs-lookup"><span data-stu-id="1dbac-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="1dbac-123">終了処理が可能なオブジェクトと考えられる場合、ファイナライザー (存在する場合) を呼び出し、オブジェクトの格納に使用されているメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> <span data-ttu-id="1dbac-124">ファイナライザーは、プログラムの終了時にも呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-124">Finalizers are also called when the program exits.</span></span>  
  
 <span data-ttu-id="1dbac-125"><xref:System.GC.Collect%2A> を呼び出すことによって、ガベージ コレクションを強制的に行うことができます。ただし、パフォーマンスに問題が発生する可能性があるため、通常はこの処理を避けます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="1dbac-126">ファイナライザーを使ったリソースの解放</span><span class="sxs-lookup"><span data-stu-id="1dbac-126">Using Finalizers to Release Resources</span></span>  
 <span data-ttu-id="1dbac-127">一般に C# では、ガベージ コレクションでランタイムにターゲットを設定しない言語で開発する場合ほど、メモリ管理を必要としません。</span><span class="sxs-lookup"><span data-stu-id="1dbac-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="1dbac-128">.NET Framework のガベージ コレクターが、オブジェクトに対するメモリの割り当てと解放を暗黙的に管理するからです。</span><span class="sxs-lookup"><span data-stu-id="1dbac-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="1dbac-129">ただし、ウィンドウ、ファイル、ネットワーク接続などのアンマネージ リソースをアプリケーションでカプセル化するとき、ファイナライザーを使ってこれらのリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dbac-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="1dbac-130">終了処理が可能なオブジェクトの場合、ガベージ コレクターはそのオブジェクトの `Finalize` メソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="1dbac-131">リソースの明示的な解放</span><span class="sxs-lookup"><span data-stu-id="1dbac-131">Explicit Release of Resources</span></span>  
 <span data-ttu-id="1dbac-132">アプリケーションで高額な外部リソースを使用している場合、ガベージ コレクターがオブジェクトを解放する前にリソースを明示的に解放する手段を用意することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="1dbac-133">この処理を行うには、オブジェクトに対して必要なクリーンアップを実行する `Dispose` メソッドを <xref:System.IDisposable> インターフェイスから実装します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="1dbac-134">これによって、アプリケーションのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="1dbac-135">このようにリソースを明示的に制御する場合でも、ファイナライザーは、`Dispose` メソッドの呼び出しが失敗したときにリソースをクリーンアップするための安全装置になります。</span><span class="sxs-lookup"><span data-stu-id="1dbac-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="1dbac-136">リソースのクリーンアップの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbac-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1dbac-137">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="1dbac-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="1dbac-138">Dispose メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="1dbac-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="1dbac-139">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="1dbac-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1dbac-140">例</span><span class="sxs-lookup"><span data-stu-id="1dbac-140">Example</span></span>  
 <span data-ttu-id="1dbac-141">次の例では、継承チェーンを形成する 3 つのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="1dbac-142">`First` が基底クラスであり、`Second` は `First` から派生し、`Third` は `Second` から派生します。</span><span class="sxs-lookup"><span data-stu-id="1dbac-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="1dbac-143">3 つのクラスのいずれにもファイナライザーがあります。</span><span class="sxs-lookup"><span data-stu-id="1dbac-143">All three have finalizers.</span></span> <span data-ttu-id="1dbac-144">`Main` では、派生が最も多いクラスのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="1dbac-145">プログラムを実行すると、3 つのクラスのファイナライザーが派生が最も多いクラスから派生が最も少ないクラスの順に自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1dbac-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1dbac-146">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1dbac-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1dbac-147">参照</span><span class="sxs-lookup"><span data-stu-id="1dbac-147">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="1dbac-148">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1dbac-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1dbac-149">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1dbac-149">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="1dbac-150">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="1dbac-150">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
