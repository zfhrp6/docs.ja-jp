---
title: 厳密に型指定されたデリゲート
description: デリゲートを必要とする機能を作成するときに、汎用デリゲート型を使用してカスタム型を宣言する方法について説明します。
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="b80c5-103">厳密に型指定されたデリゲート</span><span class="sxs-lookup"><span data-stu-id="b80c5-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="b80c5-104">前へ</span><span class="sxs-lookup"><span data-stu-id="b80c5-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="b80c5-105">前の記事では、`delegate` キーワードを使って実際にデリゲート型を作成する方法を見てきました。</span><span class="sxs-lookup"><span data-stu-id="b80c5-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="b80c5-106">抽象型の Delegate クラスは、疎な結合と呼び出しのための基盤となるものです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="b80c5-107">一方、具体的な Delegate 型は、デリゲート オブジェクトの呼び出しリストに追加されるメソッドのタイプ セーフを促し、また強制的に適用することによって、その利便性を大きく高めています。</span><span class="sxs-lookup"><span data-stu-id="b80c5-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="b80c5-108">`delegate` キーワードを使用し、具体的なデリゲート型を定義すると、それらのメソッドがコンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="b80c5-109">しかし実際にやってみると、異なるメソッド シグネチャが必要になるたびに新しいデリゲート型を作成することになり、</span><span class="sxs-lookup"><span data-stu-id="b80c5-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="b80c5-110">次第にわずらわしくなってくるものです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-110">This work could get tedious after a time.</span></span> <span data-ttu-id="b80c5-111">新しい機能を追加するたびに、新しいデリゲート型が必要になるからです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="b80c5-112">さいわい、その必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b80c5-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="b80c5-113">.NET Core フレームワークには、デリゲート型が必要になったときにいつでも再利用できる型がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="b80c5-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="b80c5-114">それが[ジェネリック](programming-guide/generics/index.md)定義です。新しいメソッドの宣言が必要になったときは、カスタマイズしたものを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="b80c5-115">その筆頭となる型が <xref:System.Action> 型で、いくつかのバリエーションも存在します。</span><span class="sxs-lookup"><span data-stu-id="b80c5-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="b80c5-116">ジェネリック型引数の `in` 修飾子については、共変性についての記事で取り上げます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="b80c5-117">`Action` デリゲートには、最大 16 の引数を含むバリエーションが存在します (例: <xref:System.Action%6016>)。</span><span class="sxs-lookup"><span data-stu-id="b80c5-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="b80c5-118">これらの定義では、デリゲート引数のそれぞれに異なるジェネリック引数が使われているという点が重要です。それによってきわめて高い柔軟性が実現されているからです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="b80c5-119">メソッドの一連の引数は、必ずしも同じ型である必要はありませんが、同じ型である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b80c5-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="b80c5-120">戻り値を持たないデリゲート型には、いずれかの `Action` 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="b80c5-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="b80c5-121">フレームワークには、戻り値を持つデリゲート型に使用できる汎用デリゲート型もいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="b80c5-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="b80c5-122">ジェネリック型引数 result の `out` 修飾子については、共変性についての記事で取り上げます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="b80c5-123">`Func` デリゲートには、最大 16 の入力引数を含むバリエーションが存在します (例: <xref:System.Func%6017>)。</span><span class="sxs-lookup"><span data-stu-id="b80c5-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="b80c5-124">慣例上、`Func` に宣言されているすべての型パラメーターの最後に出現する型が常に実行結果の型になります。</span><span class="sxs-lookup"><span data-stu-id="b80c5-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="b80c5-125">値を返すデリゲート型には、いずれかの `Func` 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="b80c5-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="b80c5-126">また、単一の値に対する判定結果を返すデリゲートに特化された <xref:System.Predicate%601> という型も存在します。</span><span class="sxs-lookup"><span data-stu-id="b80c5-126">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="b80c5-127">どのような `Predicate` 型でも、構造的に同等な `Func` 型が存在することにお気付きでしょうか。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b80c5-127">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="b80c5-128">これら 2 つの型は等価と思うかもしれません。</span><span class="sxs-lookup"><span data-stu-id="b80c5-128">You might think these two types are equivalent.</span></span> <span data-ttu-id="b80c5-129">しかし、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="b80c5-129">They are not.</span></span>
<span data-ttu-id="b80c5-130">これら 2 つの変数を相互に置き換えて使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b80c5-130">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="b80c5-131">一方の型の変数をもう一方の型に代入することはできないのです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-131">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="b80c5-132">C# の型システムで使用されるのは、定義されている型の名前であって、構造ではありません。</span><span class="sxs-lookup"><span data-stu-id="b80c5-132">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="b80c5-133">これらのデリゲート型の定義はすべて .NET Core ライブラリに存在します。つまり、デリゲートを必要とする新しい機能を作成するたびに新たにデリゲート型を定義する必要はないということです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-133">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="b80c5-134">ほとんどの状況で、皆さんが必要になるデリゲート型はすべて、これらのジェネリック定義でまかなうことができるはずです。</span><span class="sxs-lookup"><span data-stu-id="b80c5-134">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="b80c5-135">必要な型パラメーターを指定すれば、それらの型のいずれかをインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-135">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="b80c5-136">汎用化できるアルゴリズムの場合、これらのデリゲートをジェネリック型として使用することが可能です。</span><span class="sxs-lookup"><span data-stu-id="b80c5-136">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="b80c5-137">そうすることで無駄な時間をなくし、デリゲートを使用するうえで新たに作成する必要のある型の数を抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-137">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="b80c5-138">次の記事では、実際にデリゲートを扱うための一般的なパターンをいくつか見ていきます。</span><span class="sxs-lookup"><span data-stu-id="b80c5-138">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="b80c5-139">次へ</span><span class="sxs-lookup"><span data-stu-id="b80c5-139">Next</span></span>](delegates-patterns.md)
