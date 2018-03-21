---
title: "匿名メソッド (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96e78257c5aab84562cd8cdb336bb5a91ba59534
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="b33e2-102">匿名メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b33e2-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="b33e2-103">C# 2.0 より前のバージョンでは、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)を宣言するには[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)を使用するしかありませんでした。</span><span class="sxs-lookup"><span data-stu-id="b33e2-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="b33e2-104">C# 2.0 では匿名メソッドが導入され、C# 3.0 以降では、インライン コードを記述するための本来の方法として、匿名メソッドに代わってラムダ式が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b33e2-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="b33e2-105">ただし、このトピックに記載した匿名メソッドに関する情報は、ラムダ式にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="b33e2-106">ラムダ式にはない機能を匿名メソッドが備えているケースが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="b33e2-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="b33e2-107">匿名メソッドではパラメーター リストを省略できます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="b33e2-108">つまり、匿名メソッドを、さまざまなシグネチャを持つデリゲートに変換できます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="b33e2-109">これはラムダ式では不可能です。</span><span class="sxs-lookup"><span data-stu-id="b33e2-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="b33e2-110">ラムダ式の詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b33e2-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="b33e2-111">匿名メソッドは、基本的にコード ブロックをデリゲート パラメーターとして渡すときに作成します。</span><span class="sxs-lookup"><span data-stu-id="b33e2-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="b33e2-112">2 つの例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="b33e2-113">匿名メソッドを使用すると、別のメソッドを作成する必要がないため、デリゲートをインスタンス化する際のコーディングのオーバーヘッドを削減できます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="b33e2-114">たとえば、デリゲートの代わりにコード ブロックを指定すると、メソッドを作成するのが余分なオーバーヘッドと思われる場合に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="b33e2-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="b33e2-115">新しいスレッドを開始する場合などがそのよい例です。</span><span class="sxs-lookup"><span data-stu-id="b33e2-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="b33e2-116">このクラスではスレッドを作成し、スレッドが実行するコードも含みますが、デリゲート用の追加のメソッドは作成していません。</span><span class="sxs-lookup"><span data-stu-id="b33e2-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="b33e2-117">コメント</span><span class="sxs-lookup"><span data-stu-id="b33e2-117">Remarks</span></span>  
 <span data-ttu-id="b33e2-118">匿名メソッドのパラメーターのスコープは、"*匿名メソッド ブロック*" です。</span><span class="sxs-lookup"><span data-stu-id="b33e2-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="b33e2-119">匿名メソッド ブロックの内部で使用しているジャンプ ステートメント ([goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md) など) のジャンプ先がブロックの外部にある場合はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="b33e2-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="b33e2-120">また、匿名メソッド ブロックの外部で使用しているジャンプ ステートメント (`goto`、`break`、`continue` など) のジャンプ先がブロックの内部にある場合もエラーになります。</span><span class="sxs-lookup"><span data-stu-id="b33e2-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="b33e2-121">匿名メソッドの宣言をスコープに含むローカル変数とパラメーターは、匿名メソッドの "*外部*" 変数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="b33e2-122">たとえば、次のコード セグメントに示されている `n` は外部変数です。</span><span class="sxs-lookup"><span data-stu-id="b33e2-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="b33e2-123">外部変数 `n` への参照は、デリゲートの作成時に "*キャプチャ*" されるといわれます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="b33e2-124">ローカル変数とは異なり、匿名メソッドを参照するデリゲートがガベージ コレクションの対象になるまで、キャプチャされた変数の有効期間を拡張します。</span><span class="sxs-lookup"><span data-stu-id="b33e2-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="b33e2-125">匿名メソッドは、外部スコープの [in](../../../csharp/language-reference/keywords/in.md)、[ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b33e2-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="b33e2-126">"*匿名メソッド ブロック*" 内のアンセーフ コードにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="b33e2-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="b33e2-127">匿名メソッドは、[is](../../../csharp/language-reference/keywords/is.md) 演算子の左辺では使用できません。</span><span class="sxs-lookup"><span data-stu-id="b33e2-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b33e2-128">例</span><span class="sxs-lookup"><span data-stu-id="b33e2-128">Example</span></span>  
 <span data-ttu-id="b33e2-129">次の例は、デリゲートをインスタンス化する 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b33e2-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="b33e2-130">デリゲートと匿名メソッドを関連付ける。</span><span class="sxs-lookup"><span data-stu-id="b33e2-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="b33e2-131">デリゲートと名前付きメソッド (`DoWork`) を関連付ける。</span><span class="sxs-lookup"><span data-stu-id="b33e2-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="b33e2-132">どちらの場合も、デリゲートを呼び出すと、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b33e2-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b33e2-133">参照</span><span class="sxs-lookup"><span data-stu-id="b33e2-133">See Also</span></span>  
 [<span data-ttu-id="b33e2-134">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b33e2-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b33e2-135">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b33e2-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b33e2-136">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b33e2-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="b33e2-137">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="b33e2-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="b33e2-138">アンセーフ コードとポインター</span><span class="sxs-lookup"><span data-stu-id="b33e2-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="b33e2-139">メソッド</span><span class="sxs-lookup"><span data-stu-id="b33e2-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="b33e2-140">名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート</span><span class="sxs-lookup"><span data-stu-id="b33e2-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
