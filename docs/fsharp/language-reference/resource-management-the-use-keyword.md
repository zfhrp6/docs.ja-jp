---
title: "リソースの管理: use キーワード (F#)"
description: "F# キーワード 'use' と 'を使用して' の関数は、初期化とリソースの解放を制御できますについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="47620-104">リソースの管理: use キーワード</span><span class="sxs-lookup"><span data-stu-id="47620-104">Resource Management: The use Keyword</span></span>

<span data-ttu-id="47620-105">このトピックは、キーワードをについて説明`use`と`using`関数で、初期化とリソースの解放を制御できます。</span><span class="sxs-lookup"><span data-stu-id="47620-105">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="47620-106">リソース</span><span class="sxs-lookup"><span data-stu-id="47620-106">Resources</span></span>
<span data-ttu-id="47620-107">用語*リソース*は複数の方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="47620-107">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="47620-108">[はい]、リソースがこのコンテキストでは文字列、画像、および、like など、アプリケーションで使用されるデータを指定できます*リソース*グラフィックス デバイス コンテキスト、ファイル ハンドル、ネットワークなど、ソフトウェアやオペレーティング システムのリソースへの参照データベースの接続、待機ハンドルなどの同時実行オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="47620-108">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="47620-109">アプリケーションでこれらのリソースを使用するには、オペレーティング システムまたはその他のアプリケーションに提供できるようにプールに、リソースの以降のリリースを続けて、その他のリソース プロバイダーからリソースの取得が含まれます。</span><span class="sxs-lookup"><span data-stu-id="47620-109">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="47620-110">問題は、アプリケーションが共通のプールに戻してリソースを解放しない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="47620-110">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="47620-111">リソースの管理</span><span class="sxs-lookup"><span data-stu-id="47620-111">Managing Resources</span></span>
<span data-ttu-id="47620-112">確実かつ効率的にリソースを管理するアプリケーションで、迅速にし、予測可能な方法でリソースを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47620-112">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="47620-113">.NET Framework では、このことで実行できます。、`System.IDisposable`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="47620-113">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="47620-114">実装する型`System.IDisposable`が、`System.IDisposable.Dispose`メソッドで、正しくリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="47620-114">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="47620-115">適切に記述されたアプリケーションを確実に`System.IDisposable.Dispose`迅速に制限されているリソースを保持する任意のオブジェクトが不要になったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="47620-115">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="47620-116">しかし、ほとんどの .NET 言語が、簡単に作成するサポートを提供し、f# 例外ではありません。</span><span class="sxs-lookup"><span data-stu-id="47620-116">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="47620-117">Dispose パターンをサポートする 2 つの有用な言語構成要素がある:`use`バインディング、および`using`関数。</span><span class="sxs-lookup"><span data-stu-id="47620-117">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="47620-118">バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="47620-118">use Binding</span></span>
<span data-ttu-id="47620-119">`use`キーワードがフォームに似ている`let`バインド。</span><span class="sxs-lookup"><span data-stu-id="47620-119">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="47620-120">使用して*値* = *式*</span><span class="sxs-lookup"><span data-stu-id="47620-120">use *value* = *expression*</span></span>

<span data-ttu-id="47620-121">同じ機能を提供、`let`バインドしますが、への呼び出しを追加`Dispose`値がスコープ外に出るときの値にします。</span><span class="sxs-lookup"><span data-stu-id="47620-121">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="47620-122">コンパイラによって挿入される値では、null チェックする場合、値はメモ`null`への呼び出し`Dispose`は行われません。</span><span class="sxs-lookup"><span data-stu-id="47620-122">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="47620-123">次の例を使用してファイルを自動的に終了する方法を示しています、`use`キーワード。</span><span class="sxs-lookup"><span data-stu-id="47620-123">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="47620-124">使用することができます`use`コンピュテーション式で、カスタマイズされたバージョンの場合、`use`式を使用します。</span><span class="sxs-lookup"><span data-stu-id="47620-124">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="47620-125">詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="47620-125">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="using-function"></a><span data-ttu-id="47620-126">関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="47620-126">using Function</span></span>
<span data-ttu-id="47620-127">`using`関数は、次の形式。</span><span class="sxs-lookup"><span data-stu-id="47620-127">The `using` function has the following form:</span></span>

<span data-ttu-id="47620-128">`using`(*expression1*)*関数またはラムダ*</span><span class="sxs-lookup"><span data-stu-id="47620-128">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="47620-129">`using`式、 *expression1*破棄する必要があるオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="47620-129">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="47620-130">結果*expression1* (にあるオブジェクトを破棄する必要があります) では、引数になります*値*を*関数またはラムダ*、これは、1 つを期待している関数残りの値に一致する型の引数によって生成される*expression1*、またはその型の引数を受け取るラムダ式。</span><span class="sxs-lookup"><span data-stu-id="47620-130">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="47620-131">ランタイムが呼び出す関数の実行の最後に、`Dispose`リソースを解放し、(値がない限り、 `null`、後者 Dispose の呼び出しは行われません)。</span><span class="sxs-lookup"><span data-stu-id="47620-131">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="47620-132">次の例で、`using`ラムダ式を持つ式。</span><span class="sxs-lookup"><span data-stu-id="47620-132">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="47620-133">[次へ]、例に示す、`using`式、関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="47620-133">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="47620-134">関数が既に適用されるいくつかの引数を持つ関数がある場合に注意してください。</span><span class="sxs-lookup"><span data-stu-id="47620-134">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="47620-135">次のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="47620-135">The following code example demonstrates this.</span></span> <span data-ttu-id="47620-136">文字列を含むファイルが作成されます`XYZ`です。</span><span class="sxs-lookup"><span data-stu-id="47620-136">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="47620-137">`using`関数および`use`バインディングは、同じことを実現するほぼ同等の方法です。</span><span class="sxs-lookup"><span data-stu-id="47620-137">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="47620-138">`using`キーワードにより、タイミングをより細かく制御`Dispose`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="47620-138">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="47620-139">使用すると`using`、`Dispose`を使用するときに、関数、またはラムダ式の最後に呼び出される、`use`キーワード、`Dispose`要素を含むコード ブロックの最後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="47620-139">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="47620-140">一般に、使用する優先する必要があります`use`の代わりに、`using`関数。</span><span class="sxs-lookup"><span data-stu-id="47620-140">In general, you should prefer to use `use` instead of the `using` function.</span></span>


## <a name="see-also"></a><span data-ttu-id="47620-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="47620-141">See Also</span></span>
[<span data-ttu-id="47620-142">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="47620-142">F# Language Reference</span></span>](index.md)