---
title: "匿名メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 92842becf26a15ab1a6f5e9621002abf71dc67bc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="34738-102">匿名メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="34738-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="34738-103">C# 2.0 より前のバージョンでは、[デリゲート](../../../csharp/language-reference/keywords/delegate.md)を宣言するには[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)を使用するしかありませんでした。</span><span class="sxs-lookup"><span data-stu-id="34738-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="34738-104">C# 2.0 では匿名メソッドが導入され、C# 3.0 以降では、インライン コードを記述するための本来の方法として、匿名メソッドに代わってラムダ式が使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="34738-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="34738-105">ただし、このトピックに記載した匿名メソッドに関する情報は、ラムダ式にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="34738-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="34738-106">ラムダ式にはない機能を匿名メソッドが備えているケースが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="34738-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="34738-107">匿名メソッドではパラメーター リストを省略できます。</span><span class="sxs-lookup"><span data-stu-id="34738-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="34738-108">つまり、匿名メソッドを、さまざまなシグネチャを持つデリゲートに変換できます。</span><span class="sxs-lookup"><span data-stu-id="34738-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="34738-109">これはラムダ式では不可能です。</span><span class="sxs-lookup"><span data-stu-id="34738-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="34738-110">ラムダ式の詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34738-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="34738-111">匿名メソッドは、基本的にコード ブロックをデリゲート パラメーターとして渡すときに作成します。</span><span class="sxs-lookup"><span data-stu-id="34738-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="34738-112">2 つの例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="34738-112">Here are two examples:</span></span>  
  
 <span data-ttu-id="34738-113">[!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="34738-113">[!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="34738-114">[!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="34738-114">[!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="34738-115">匿名メソッドを使用すると、別のメソッドを作成する必要がないため、デリゲートをインスタンス化する際のコーディングのオーバーヘッドを削減できます。</span><span class="sxs-lookup"><span data-stu-id="34738-115">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="34738-116">たとえば、デリゲートの代わりにコード ブロックを指定すると、メソッドを作成するのが余分なオーバーヘッドと思われる場合に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="34738-116">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="34738-117">新しいスレッドを開始する場合などがそのよい例です。</span><span class="sxs-lookup"><span data-stu-id="34738-117">A good example would be when you start a new thread.</span></span> <span data-ttu-id="34738-118">このクラスではスレッドを作成し、スレッドが実行するコードも含みますが、デリゲート用の追加のメソッドは作成していません。</span><span class="sxs-lookup"><span data-stu-id="34738-118">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 <span data-ttu-id="34738-119">[!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="34738-119">[!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34738-120">コメント</span><span class="sxs-lookup"><span data-stu-id="34738-120">Remarks</span></span>  
 <span data-ttu-id="34738-121">匿名メソッドのパラメーターのスコープは、"*匿名メソッド ブロック*" です。</span><span class="sxs-lookup"><span data-stu-id="34738-121">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="34738-122">匿名メソッド ブロックの内部で使用しているジャンプ ステートメント ([goto](../../../csharp/language-reference/keywords/goto.md)、[break](../../../csharp/language-reference/keywords/break.md)、[continue](../../../csharp/language-reference/keywords/continue.md) など) のジャンプ先がブロックの外部にある場合はエラーになります。</span><span class="sxs-lookup"><span data-stu-id="34738-122">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="34738-123">また、匿名メソッド ブロックの外部で使用しているジャンプ ステートメント (`goto`、`break`、`continue` など) のジャンプ先がブロックの内部にある場合もエラーになります。</span><span class="sxs-lookup"><span data-stu-id="34738-123">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="34738-124">匿名メソッドの宣言をスコープに含むローカル変数とパラメーターは、匿名メソッドの "*外部*" 変数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="34738-124">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="34738-125">たとえば、次のコード セグメントに示されている `n` は外部変数です。</span><span class="sxs-lookup"><span data-stu-id="34738-125">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 <span data-ttu-id="34738-126">[!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="34738-126">[!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="34738-127">外部変数 `n` への参照は、デリゲートの作成時に "*キャプチャ*" されるといわれます。</span><span class="sxs-lookup"><span data-stu-id="34738-127">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="34738-128">ローカル変数とは異なり、匿名メソッドを参照するデリゲートがガベージ コレクションの対象になるまで、キャプチャされた変数の有効期間を拡張します。</span><span class="sxs-lookup"><span data-stu-id="34738-128">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="34738-129">匿名メソッドは、外部スコープの [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターや [out](../../../csharp/language-reference/keywords/out.md) パラメーターにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="34738-129">An anonymous method cannot access the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="34738-130">"*匿名メソッド ブロック*" 内のアンセーフ コードにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="34738-130">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="34738-131">匿名メソッドは、[is](../../../csharp/language-reference/keywords/is.md) 演算子の左辺では使用できません。</span><span class="sxs-lookup"><span data-stu-id="34738-131">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34738-132">例</span><span class="sxs-lookup"><span data-stu-id="34738-132">Example</span></span>  
 <span data-ttu-id="34738-133">次の例は、デリゲートをインスタンス化する 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="34738-133">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="34738-134">デリゲートと匿名メソッドを関連付ける。</span><span class="sxs-lookup"><span data-stu-id="34738-134">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="34738-135">デリゲートと名前付きメソッド (`DoWork`) を関連付ける。</span><span class="sxs-lookup"><span data-stu-id="34738-135">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="34738-136">どちらの場合も、デリゲートを呼び出すと、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34738-136">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 <span data-ttu-id="34738-137">[!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="34738-137">[!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34738-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="34738-138">See Also</span></span>  
 <span data-ttu-id="34738-139">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="34738-139">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="34738-140">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="34738-140">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="34738-141">[デリゲート](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="34738-141">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="34738-142">[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="34738-142">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
 <span data-ttu-id="34738-143">[アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="34738-143">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="34738-144">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="34738-144">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 [<span data-ttu-id="34738-145">名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート</span><span class="sxs-lookup"><span data-stu-id="34738-145">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)

