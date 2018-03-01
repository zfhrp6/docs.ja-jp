---
title: "ローカル関数 (C# プログラミング ガイド)"
ms.date: 06/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- local functions [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e95d48e451038f0f7004d0901f329b2c57fe5
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="f932f-102">ローカル関数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f932f-102">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="f932f-103">C# 7 以降、C# では*ローカル関数*がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f932f-103">Starting with C# 7, C# supports *local functions*.</span></span> <span data-ttu-id="f932f-104">ローカル関数は、別のメンバーの入れ子になっているタイプのプライベート メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f932f-104">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="f932f-105">親メンバーからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f932f-105">They can only be called from their containing member.</span></span> <span data-ttu-id="f932f-106">ローカル関数は次の要素で宣言し、呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f932f-106">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="f932f-107">メソッド (特に反復子メソッドと非同期メソッド)</span><span class="sxs-lookup"><span data-stu-id="f932f-107">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="f932f-108">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="f932f-108">Constructors</span></span>
- <span data-ttu-id="f932f-109">プロパティ アクセサー</span><span class="sxs-lookup"><span data-stu-id="f932f-109">Property accessors</span></span>
- <span data-ttu-id="f932f-110">イベント アクセサー</span><span class="sxs-lookup"><span data-stu-id="f932f-110">Event accessors</span></span>
- <span data-ttu-id="f932f-111">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="f932f-111">Anonymous methods</span></span>
- <span data-ttu-id="f932f-112">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="f932f-112">Lambda expressions</span></span>
- <span data-ttu-id="f932f-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="f932f-113">Finalizers</span></span>
- <span data-ttu-id="f932f-114">その他のローカル関数</span><span class="sxs-lookup"><span data-stu-id="f932f-114">Other local functions</span></span>

<span data-ttu-id="f932f-115">ただし、ローカル関数は、式形式のメンバーの内部では宣言できません。</span><span class="sxs-lookup"><span data-stu-id="f932f-115">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="f932f-116">場合によっては、ラムダ式を使用して、ローカル関数でもサポートされている機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="f932f-116">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="f932f-117">比較については、「[ローカル関数とラムダ式の比較](../../local-functions-vs-lambdas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f932f-117">For a comparison, see [Local functions compared to Lambda expressions](../../local-functions-vs-lambdas.md).</span></span>

<span data-ttu-id="f932f-118">ローカル関数を使用すると、コードの意図が明確になります。</span><span class="sxs-lookup"><span data-stu-id="f932f-118">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="f932f-119">コードを見た人は、メソッドが親メソッドによってのみ呼び出し可能であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f932f-119">Anyone reading you code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="f932f-120">また、チーム プロジェクトの場合は、別の開発者がクラスや構造体の別の場所から誤ってメソッドを直接呼び出すことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="f932f-120">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or stuct.</span></span>
 
## <a name="local-function-syntax"></a><span data-ttu-id="f932f-121">ローカル関数の構文</span><span class="sxs-lookup"><span data-stu-id="f932f-121">Local function syntax</span></span>

<span data-ttu-id="f932f-122">ローカル関数は、親メンバーの内側に、入れ子になったメソッドとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="f932f-122">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="f932f-123">その定義の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f932f-123">Its definition has the following syntax:</span></span>

```txt
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="f932f-124">ローカル関数では、[async](../../language-reference/keywords/async.md) および [unsafe](../../language-reference/keywords/unsafe.md) 修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f932f-124">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span> 

<span data-ttu-id="f932f-125">メソッドのパラメーターを含め、親メンバーに定義されたすべてのローカル変数は、ローカル関数からアクセス可能です。</span><span class="sxs-lookup"><span data-stu-id="f932f-125">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span> 

<span data-ttu-id="f932f-126">メソッド定義とは異なり、ローカル関数は次の要素を含むことはできません。</span><span class="sxs-lookup"><span data-stu-id="f932f-126">Unlike a method definition, a local function definition cannot include the following elements:</span></span>

- <span data-ttu-id="f932f-127">メンバー アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="f932f-127">The member access modifier.</span></span> <span data-ttu-id="f932f-128">すべてのローカル関数はプライベートであるため、`private` キーワードなどのアクセス修飾子が含まれていると、コンパイラ エラー CS0106 "修飾子 'private' がこの項目に対して有効ではありません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f932f-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>
 
- <span data-ttu-id="f932f-129">[static](../../language-reference/keywords/static.md) キーワード。</span><span class="sxs-lookup"><span data-stu-id="f932f-129">The [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="f932f-130">`static` キーワードが含まれていると、コンパイラ エラー CS0106 "修飾子 'static' がこの項目に対して有効ではありません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f932f-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="f932f-131">さらに、ローカル関数またはローカル関数のパラメーターと型パラメーターには属性を適用できません。</span><span class="sxs-lookup"><span data-stu-id="f932f-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span> 
 
<span data-ttu-id="f932f-132">次の例は、`GetText` というメソッドに対してプライベートな `AppendPathSeparator` というローカル関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="f932f-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>
   
[!code-csharp[LocalFunctionExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  
   
## <a name="local-functions-and-exceptions"></a><span data-ttu-id="f932f-133">ローカル関数と例外</span><span class="sxs-lookup"><span data-stu-id="f932f-133">Local functions and exceptions</span></span>

<span data-ttu-id="f932f-134">ローカル関数の便利な機能の 1 つは、例外を直ちに検出できることです。</span><span class="sxs-lookup"><span data-stu-id="f932f-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="f932f-135">メソッド反復子の場合、例外は返されたシーケンスを列挙する時点でしか検出されず、反復子を取得した時点では検出されません。</span><span class="sxs-lookup"><span data-stu-id="f932f-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="f932f-136">非同期メソッドの場合、非同期メソッドでスローされた例外は、タスクの戻りを待機中に検出されます。</span><span class="sxs-lookup"><span data-stu-id="f932f-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span> 

<span data-ttu-id="f932f-137">次の例は、指定した範囲にある奇数を列挙する `OddSequence` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="f932f-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="f932f-138">100 より大きい数値を `OddSequence` 列挙子メソッドに渡しているため、メソッドは <xref:System.ArgumentOutOfRangeException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="f932f-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="f932f-139">この例の出力が示すように、例外は列挙子を取得したときではなく、数値を反復処理した時点でのみ検出されます。</span><span class="sxs-lookup"><span data-stu-id="f932f-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)] 

<span data-ttu-id="f932f-140">これに対して、次の例に示すようにローカル関数から列挙子を返すことによって、列挙子を取得する前の検証を実行する時点で例外をスローできます。</span><span class="sxs-lookup"><span data-stu-id="f932f-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="f932f-141">ローカル関数は、非同期操作の外部で例外を処理するために同様の方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="f932f-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="f932f-142">通常、非同期メソッドでスローされた例外では <xref:System.AggregateException> の内部例外を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f932f-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="f932f-143">ローカル関数を使用すると、コードを迅速に失敗させ (Fail Fast)、例外のスローと検出の両方を同時に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f932f-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="f932f-144">次の例は、`GetMultipleAsync` という非同期メソッドを使用して、指定した秒数だけ一時停止した後、その秒数のランダムな倍数である値を返します。</span><span class="sxs-lookup"><span data-stu-id="f932f-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="f932f-145">遅延の最大値は 5 秒です。値が 5 より大きい場合は <xref:System.ArgumentOutOfRangeException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="f932f-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="f932f-146">次の例に示すように、`GetMultipleAsync` メソッドに渡された値が 6 の場合にスローされる例外は、`GetMultipleAsync` メソッドの実行開始後、<xref:System.AggregateException> にラップされます。</span><span class="sxs-lookup"><span data-stu-id="f932f-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)] 

<span data-ttu-id="f932f-147">メソッド反復子と同様、非同期メソッドを呼び出す前に検証を実行するように、この例のコードをリファクターすることができます。</span><span class="sxs-lookup"><span data-stu-id="f932f-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="f932f-148">次の例の出力に示されているように、<xref:System.ArgumentOutOfRangeException> は <x:System.AggregateException> にラップされていません。</span><span class="sxs-lookup"><span data-stu-id="f932f-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <x:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync`](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)] 

## <a name="see-also"></a><span data-ttu-id="f932f-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="f932f-149">See also</span></span>
[<span data-ttu-id="f932f-150">メソッド</span><span class="sxs-lookup"><span data-stu-id="f932f-150">Methods</span></span>](methods.md)
