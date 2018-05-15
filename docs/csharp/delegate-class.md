---
title: System.Delegate と `delegate` キーワード
description: デリゲートをサポートする .NET Framework のクラスと、それが ’delegate’ キーワードにどのように対応付けられるかについて取り上げます。
ms.date: 06/20/2016
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 2265d081b884a19cda6fc9d80a0f621a30c87e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="systemdelegate-and-the-delegate-keyword"></a><span data-ttu-id="6a792-103">System.Delegate と `delegate` キーワード</span><span class="sxs-lookup"><span data-stu-id="6a792-103">System.Delegate and the `delegate` keyword</span></span>

[<span data-ttu-id="6a792-104">前へ</span><span class="sxs-lookup"><span data-stu-id="6a792-104">Previous</span></span>](delegates-overview.md)

<span data-ttu-id="6a792-105">この記事では、デリゲートをサポートする .NET Framework のクラスと、それらが `delegate` キーワードにどのようにして対応付けられるかについて取り上げます。</span><span class="sxs-lookup"><span data-stu-id="6a792-105">This article will cover the classes in the .NET framework that support delegates, and how those map to the `delegate` keyword.</span></span>

## <a name="defining-delegate-types"></a><span data-ttu-id="6a792-106">デリゲート型の定義</span><span class="sxs-lookup"><span data-stu-id="6a792-106">Defining Delegate Types</span></span>

<span data-ttu-id="6a792-107">最初に、'delegate' キーワードから始めましょう。これは、主に、デリゲートを操作する際に使用するためです。</span><span class="sxs-lookup"><span data-stu-id="6a792-107">Let's start with the 'delegate' keyword, because that's primarily what you will use as you work with delegates.</span></span> <span data-ttu-id="6a792-108">`delegate` キーワードを使用したときにコンパイラで生成されるコードは、<xref:System.Delegate> クラスおよび <xref:System.MulticastDelegate> クラスのメンバーを呼び出すメソッド呼び出しにマップされます。</span><span class="sxs-lookup"><span data-stu-id="6a792-108">The code that the compiler generates when you use the `delegate` keyword will map to method calls that invoke members of the <xref:System.Delegate> and <xref:System.MulticastDelegate> classes.</span></span> 

<span data-ttu-id="6a792-109">デリゲート型を定義するには、メソッド シグネチャの定義と同様の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="6a792-109">You define a delegate type using syntax that is similar to defining a method signature.</span></span> <span data-ttu-id="6a792-110">定義に `delegate` キーワードを追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="6a792-110">You just add the `delegate` keyword to the definition.</span></span>

<span data-ttu-id="6a792-111">続けて、例として List.Sort() メソッドを使用してみましょう。</span><span class="sxs-lookup"><span data-stu-id="6a792-111">Let's continue to use the List.Sort() method as our example.</span></span> <span data-ttu-id="6a792-112">最初の手順では、比較デリゲートの型を作成します。</span><span class="sxs-lookup"><span data-stu-id="6a792-112">The first step is to create a type for the comparison delegate:</span></span>

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

<span data-ttu-id="6a792-113">コンパイラは、使用されたシグネチャ (ここでは、整数を返し、2 つの引数を持つメソッド) と一致する `System.Delegate` から派生するクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="6a792-113">The compiler generates a class, derived from `System.Delegate` that matches the signature used (in this case, a method that returns an integer, and has two arguments).</span></span> <span data-ttu-id="6a792-114">そのデリゲートの型は `Comparison` です。</span><span class="sxs-lookup"><span data-stu-id="6a792-114">The type of that delegate is `Comparison`.</span></span> <span data-ttu-id="6a792-115">`Comparison` デリゲート型はジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="6a792-115">The `Comparison` delegate type is a generic type.</span></span> <span data-ttu-id="6a792-116">ジェネリックの詳細については、[こちら](generics.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a792-116">For details on generics see [here](generics.md).</span></span>

<span data-ttu-id="6a792-117">構文は変数を宣言しているように見えるかもしれませんが、実際には "*型*" を宣言していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a792-117">Notice that the syntax may appear as though it is declaring a variable, but it is actually declaring a *type*.</span></span> <span data-ttu-id="6a792-118">デリゲート型は、クラス内で定義したり、名前空間内で直接定義したりできるだけでなく、さらにグローバル名前空間でも定義できます。</span><span class="sxs-lookup"><span data-stu-id="6a792-118">You can define delegate types inside classes, directly inside namespaces, or even in the global namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="6a792-119">グローバル名前空間で直接デリゲート型 (またはその他の型) を宣言することは、お勧めしません。</span><span class="sxs-lookup"><span data-stu-id="6a792-119">Declaring delegate types (or other types) directly in the global namespace is not recommended.</span></span> 

<span data-ttu-id="6a792-120">コンパイラは、この新しい型用の追加ハンドラーと削除ハンドラーも生成するため、このクラスのクライアントは、インスタンスの呼び出しリストでメソッドを追加したり削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="6a792-120">The compiler also generates add and remove handlers for this new type so that clients of this class can add and remove methods from an instance's invocation list.</span></span> <span data-ttu-id="6a792-121">コンパイラでは、追加または削除されるメソッドのシグネチャが、メソッドの宣言時に使用されたシグネチャと一致することが強制されます。</span><span class="sxs-lookup"><span data-stu-id="6a792-121">The compiler will enforce that the signature of the method being added or removed matches the signature used when declaring the method.</span></span> 

## <a name="declaring-instances-of-delegates"></a><span data-ttu-id="6a792-122">デリゲートのインスタンスの宣言</span><span class="sxs-lookup"><span data-stu-id="6a792-122">Declaring instances of delegates</span></span>

<span data-ttu-id="6a792-123">デリゲートを定義した後に、その型のインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6a792-123">After defining the delegate, you can create an instance of that type.</span></span>
<span data-ttu-id="6a792-124">C# のすべての変数と同様に、デリゲート インスタンスを名前空間で直接宣言することも、グローバル名前空間で宣言することもできません。</span><span class="sxs-lookup"><span data-stu-id="6a792-124">Like all variables in C#, you cannot declare delegate instances directly in a namespace, or in the global namespace.</span></span>

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

<span data-ttu-id="6a792-125">変数の型は、前に定義したデリゲート型の `Comparison<T>` です。</span><span class="sxs-lookup"><span data-stu-id="6a792-125">The type of the variable is `Comparison<T>`, the delegate type defined earlier.</span></span> <span data-ttu-id="6a792-126">変数の名前は、`comparator` です。</span><span class="sxs-lookup"><span data-stu-id="6a792-126">The name of the variable is `comparator`.</span></span>
 
 <span data-ttu-id="6a792-127">上記のコード スニペットでは、クラス内でメンバー変数を宣言しました。</span><span class="sxs-lookup"><span data-stu-id="6a792-127">That code snippet above declared a member variable inside a class.</span></span> <span data-ttu-id="6a792-128">ローカル変数であるデリゲート変数、またはメソッドの引数も宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6a792-128">You can also declare delegate variables that are local variables, or arguments to methods.</span></span>

## <a name="invoking-delegates"></a><span data-ttu-id="6a792-129">デリゲートの呼び出し</span><span class="sxs-lookup"><span data-stu-id="6a792-129">Invoking Delegates</span></span>

<span data-ttu-id="6a792-130">デリゲートの呼び出しリストに含まれているメソッドを呼び出すには、そのデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6a792-130">You invoke the methods that are in the invocation list of a delegate by calling that delegate.</span></span> <span data-ttu-id="6a792-131">`Sort()` メソッドの内部で、コードは比較メソッドを呼び出して、オブジェクトを配置する順番を決定します。</span><span class="sxs-lookup"><span data-stu-id="6a792-131">Inside the `Sort()` method, the code will call the comparison method to determine which order to place objects:</span></span>

```csharp
int result = comparator(left, right);
```

<span data-ttu-id="6a792-132">上の行のコードは、デリゲートにアタッチされているメソッドを "*呼び出し*" ます。</span><span class="sxs-lookup"><span data-stu-id="6a792-132">In the line above, the code *invokes* the method attached to the delegate.</span></span>
<span data-ttu-id="6a792-133">変数をメソッド名として扱い、通常のメソッド呼び出しの構文を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6a792-133">You treat the variable as a method name, and invoke it using normal method call syntax.</span></span>

<span data-ttu-id="6a792-134">このコード行は、安全でない想定を行っています。つまり、ターゲットがデリゲートに追加済みであるという保証がありません。</span><span class="sxs-lookup"><span data-stu-id="6a792-134">That line of code makes an unsafe assumption: There's no guarantee that a target has been added to the delegate.</span></span> <span data-ttu-id="6a792-135">ターゲットがアタッチされていない場合、上の行によって `NullReferenceException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6a792-135">If no targets have been attached, the line above would cause a `NullReferenceException` to be thrown.</span></span> <span data-ttu-id="6a792-136">この問題に対処するための用法は、単純な null チェックよりも複雑で、この[シリーズ](delegates-patterns.md)の後の方で説明します。</span><span class="sxs-lookup"><span data-stu-id="6a792-136">The idioms used to address this problem are more complicated than a simple null-check, and are covered later in this [series](delegates-patterns.md).</span></span>

## <a name="assigning-adding-and-removing-invocation-targets"></a><span data-ttu-id="6a792-137">呼び出しターゲットの割り当て、追加、削除</span><span class="sxs-lookup"><span data-stu-id="6a792-137">Assigning, Adding and removing Invocation Targets</span></span>

<span data-ttu-id="6a792-138">デリゲート型の定義方法と、デリゲート インスタンスの宣言および呼び出しの方法は以上です。</span><span class="sxs-lookup"><span data-stu-id="6a792-138">That's how a delegate type is defined, and how delegate instances are declared and invoked.</span></span>

<span data-ttu-id="6a792-139">`List.Sort()` メソッドを使用する開発者は、シグネチャがデリゲート型の定義と一致するメソッドを定義し、sort メソッドによって使用されるデリゲートに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a792-139">Developers that want to use the `List.Sort()` method need to define a method whose signature matches the delegate type definition, and assign it to the delegate used by the sort method.</span></span> <span data-ttu-id="6a792-140">この割り当てによって、そのデリゲート オブジェクトの呼び出しリストにメソッドが追加されます。</span><span class="sxs-lookup"><span data-stu-id="6a792-140">This assignment adds the method to the invocation list of that delegate object.</span></span>

<span data-ttu-id="6a792-141">文字列のリストを、長さを基準にして並べ替えるとします。</span><span class="sxs-lookup"><span data-stu-id="6a792-141">Suppose you wanted to sort a list of strings by their length.</span></span> <span data-ttu-id="6a792-142">比較関数は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6a792-142">Your comparison function might be the following:</span></span>

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

<span data-ttu-id="6a792-143">メソッドは、プライベート メソッドとして宣言されます。</span><span class="sxs-lookup"><span data-stu-id="6a792-143">The method is declared as a private method.</span></span> <span data-ttu-id="6a792-144">それでかまいません。</span><span class="sxs-lookup"><span data-stu-id="6a792-144">That's fine.</span></span> <span data-ttu-id="6a792-145">このメソッドをパブリック インターフェイスに含めることはできないかもしれません。</span><span class="sxs-lookup"><span data-stu-id="6a792-145">You may not want this method to be part of your public interface.</span></span> <span data-ttu-id="6a792-146">それでも、デリゲートにアタッチすれば、比較メソッドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="6a792-146">It can still be used as the comparison method when attached to a delegate.</span></span> <span data-ttu-id="6a792-147">呼び出しコードでは、このメソッドがデリゲート オブジェクトのターゲット リストにアタッチされるため、そのデリゲートを通じてこのメソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6a792-147">The calling code will have this method attached to the target list of the delegate object, and can access it through that delegate.</span></span>

<span data-ttu-id="6a792-148">この関係を作成するには、このメソッドを `List.Sort()` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="6a792-148">You create that relationship by passing that method to the `List.Sort()` method:</span></span>

```csharp
phrases.Sort(CompareLength);
```

<span data-ttu-id="6a792-149">メソッド名が、かっこなしで使用されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a792-149">Notice that the method name is used, without parentheses.</span></span> <span data-ttu-id="6a792-150">メソッドを引数として使用すると、コンパイラは、メソッドの参照を、デリゲート呼び出しターゲットとして使用できる参照に変換し、そのメソッドを呼び出しターゲットとしてアタッチします。</span><span class="sxs-lookup"><span data-stu-id="6a792-150">Using the method as an argument tells the compiler to convert the method reference into a reference that can be used as a delegate invocation target, and attach that method as an invocation target.</span></span>

<span data-ttu-id="6a792-151">'Comparison<string>' 型の変数を宣言し、割り当てを行うことで、明示的にそうすることもできました。</span><span class="sxs-lookup"><span data-stu-id="6a792-151">You could also have been explicit by declaring a variable of type 'Comparison<string>\` and doing an assignment:</span></span>

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

<span data-ttu-id="6a792-152">デリゲート ターゲットとして使用されているメソッドが小さなメソッドである場合は、[ラムダ式](lambda-expressions.md)構文を使用して割り当てを実行することが一般的です。</span><span class="sxs-lookup"><span data-stu-id="6a792-152">In uses where the method being used as a delegate target is a small method, it's common to use [Lambda Expression](lambda-expressions.md) syntax to perform the assignment:</span></span>

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

<span data-ttu-id="6a792-153">デリゲート ターゲットにラムダ式を使用する方法については、[後のセクション](delegates-patterns.md)で詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="6a792-153">Using Lambda Expressions for delegate targets is covered more in a [later section](delegates-patterns.md).</span></span>

<span data-ttu-id="6a792-154">Sort() の例では、通常、デリゲートに 1 つのターゲット メソッドをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="6a792-154">The Sort() example typically attaches a single target method to the delegate.</span></span> <span data-ttu-id="6a792-155">ただし、デリゲート オブジェクトは、複数のターゲット メソッドがデリゲート オブジェクトにアタッチされている呼び出しリストをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6a792-155">However, delegate objects do support invocation lists that have multiple target methods attached to a delegate object.</span></span>

## <a name="delegate-and-multicastdelegate-classes"></a><span data-ttu-id="6a792-156">Delegate クラスと MulticastDelegate クラス</span><span class="sxs-lookup"><span data-stu-id="6a792-156">Delegate and MulticastDelegate classes</span></span>

<span data-ttu-id="6a792-157">前述の言語サポートは、デリゲートの操作で一般的に必要となる機能と支援を提供します。</span><span class="sxs-lookup"><span data-stu-id="6a792-157">The language support described above provides the features and support you'll typically need to work with delegates.</span></span> <span data-ttu-id="6a792-158">これらの機能は、.NET Core Framework の 2 つのクラスである <xref:System.Delegate> と <xref:System.MulticastDelegate> に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6a792-158">These features are built on two classes in the .NET Core framework: <xref:System.Delegate> and <xref:System.MulticastDelegate>.</span></span>

<span data-ttu-id="6a792-159">`System.Delegate` クラスと、その直接的なサブクラス `System.MulticastDelegate` は、デリゲートの作成、デリゲート ターゲットとしてのメソッドの登録、デリゲート ターゲットとして登録されているすべてのメソッドの呼び出しについてフレームワークをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6a792-159">The `System.Delegate` class, and its single direct sub-class, `System.MulticastDelegate`, provide the framework support for creating delegates, registering methods as delegate targets, and invoking all methods that are registered as a delegate target.</span></span> 

<span data-ttu-id="6a792-160">興味深いことに、`System.Delegate` クラスと `System.MulticastDelegate` クラス自体は、デリゲート型ではありません。</span><span class="sxs-lookup"><span data-stu-id="6a792-160">Interestingly, the `System.Delegate` and `System.MulticastDelegate` classes are not themselves delegate types.</span></span> <span data-ttu-id="6a792-161">これらのクラスは、すべてのデリゲート型の基礎となります。</span><span class="sxs-lookup"><span data-stu-id="6a792-161">They do provide the basis for all specific delegate types.</span></span> <span data-ttu-id="6a792-162">この言語設計プロセスにより、`Delegate` または `MulticastDelegate` から派生するクラスを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="6a792-162">That same language design process mandated that you cannot declare a class that derives from `Delegate` or `MulticastDelegate`.</span></span> <span data-ttu-id="6a792-163">C# 言語の規則によって禁止されています。</span><span class="sxs-lookup"><span data-stu-id="6a792-163">The C# language rules prohibit it.</span></span>
 
<span data-ttu-id="6a792-164">代わりに、C# 言語キーワードを使用してデリゲート型を宣言すると、C# コンパイラは、`MulticastDelegate` から派生したクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a792-164">Instead, the C# compiler creates instances of a class derived from `MulticastDelegate` when you use the C# language keyword to declare delegate types.</span></span>

<span data-ttu-id="6a792-165">この設計は、C# と .NET の最初のリリースが起源になっています。</span><span class="sxs-lookup"><span data-stu-id="6a792-165">This design has its roots in the first release of C# and .NET.</span></span> <span data-ttu-id="6a792-166">設計チームの 1 つの目標は、デリゲートを使用するときに言語によってタイプ セーフが強制的に適用されるようにすることでした。</span><span class="sxs-lookup"><span data-stu-id="6a792-166">One goal for the design team was to ensure that the language enforced type safety when using delegates.</span></span> <span data-ttu-id="6a792-167">つまり、デリゲートが確実に適切な型と数の引数で呼び出されるようにすることでした。</span><span class="sxs-lookup"><span data-stu-id="6a792-167">That meant ensuring that delegates were invoked with the right type and number of arguments.</span></span> <span data-ttu-id="6a792-168">また、戻り値の型がコンパイル時に正しく指定されるようにする必要もありました。</span><span class="sxs-lookup"><span data-stu-id="6a792-168">And, that any return type was correctly indicated at compile time.</span></span> <span data-ttu-id="6a792-169">デリゲートは 1.0 .NET リリースに含まれており、ジェネリックより前のことでした。</span><span class="sxs-lookup"><span data-stu-id="6a792-169">Delegates were part of the 1.0 .NET release, which was before generics.</span></span>

<span data-ttu-id="6a792-170">このタイプ セーフを強制的に適用する最良の方法は、使用されるメソッド シグネチャを表す具体的なデリゲート クラスをコンパイラで作成することでした。</span><span class="sxs-lookup"><span data-stu-id="6a792-170">The best way to enforce this type safety was for the compiler to create the concrete delegate classes that represented the method signature being used.</span></span>

<span data-ttu-id="6a792-171">派生クラスを直接作成することはできませんが、これらのクラスで定義されているメソッドを使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="6a792-171">Even though you cannot create derived classes directly, you will use the methods defined on these classes.</span></span> <span data-ttu-id="6a792-172">それでは、デリゲートを操作するときに使用する最も一般的なメソッドを見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="6a792-172">Let's go through the most common methods that you will use when you work with delegates.</span></span>

<span data-ttu-id="6a792-173">まず、覚えておくべき最も重要な事実は、操作するすべてのデリゲートが `MulticastDelegate` から派生しているということです。</span><span class="sxs-lookup"><span data-stu-id="6a792-173">The first, most important fact to remember is that every delegate you work with is derived from `MulticastDelegate`.</span></span> <span data-ttu-id="6a792-174">マルチキャスト デリゲートとは、デリゲートを通じて呼び出す場合に複数のメソッド ターゲットを呼び出すことができることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a792-174">A multicast delegate means that more than one method target can be invoked when invoking through a delegate.</span></span> <span data-ttu-id="6a792-175">元の設計では、アタッチして呼び出すことができるターゲット メソッドが 1 つのみのデリゲートと、複数のターゲット メソッドをアタッチして呼び出すことができるデリゲートを区別することが考慮されていました。</span><span class="sxs-lookup"><span data-stu-id="6a792-175">The original design considered making a distinction between delegates where only one target method could be attached and invoked, and delegates where multiple target methods could be attached and invoked.</span></span> <span data-ttu-id="6a792-176">この区別は、実際には当初考えていたよりも役に立たないことがわかりました。</span><span class="sxs-lookup"><span data-stu-id="6a792-176">That distinction proved to be less useful in practice than originally thought.</span></span> <span data-ttu-id="6a792-177">この異なる 2 つのクラスは既に作成され、初期の公開リリースからフレームワークに含まれていました。</span><span class="sxs-lookup"><span data-stu-id="6a792-177">The two different classes were already created, and have been in the framework since its initial public release.</span></span>

<span data-ttu-id="6a792-178">デリゲートと共に最もよく使用するメソッドは、`Invoke()` と `BeginInvoke()` / `EndInvoke()` です。</span><span class="sxs-lookup"><span data-stu-id="6a792-178">The methods that you will use the most with delegates are `Invoke()` and `BeginInvoke()` / `EndInvoke()`.</span></span> <span data-ttu-id="6a792-179">`Invoke()` は、特定のデリゲート インスタンスにアタッチされているすべてのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6a792-179">`Invoke()` will invoke all the methods that have been attached to a particular delegate instance.</span></span> <span data-ttu-id="6a792-180">前に説明したように、通常はデリゲート変数に対するメソッド呼び出し構文を使用して、デリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6a792-180">As you saw above, you typically invoke delegates using the method call syntax on the delegate variable.</span></span> <span data-ttu-id="6a792-181">[このシリーズの後半](delegates-patterns.md)で説明するように、これらのメソッドを直接操作するパターンは複数あります。</span><span class="sxs-lookup"><span data-stu-id="6a792-181">As you'll see [later in this series](delegates-patterns.md), there are patterns that work directly with these methods.</span></span>

<span data-ttu-id="6a792-182">デリゲートをサポートしている言語構文とクラスの説明は以上です。次に、厳密に型指定されたデリゲートの使用、作成、呼び出しの方法を確認しましょう。</span><span class="sxs-lookup"><span data-stu-id="6a792-182">Now that you've seen the language syntax and the classes that support delegates, let's examine how strongly typed delegates are used, created and invoked.</span></span>

[<span data-ttu-id="6a792-183">次へ</span><span class="sxs-lookup"><span data-stu-id="6a792-183">Next</span></span>](delegates-strongly-typed.md)
