---
title: デリゲートとラムダ
description: 特定のメソッド シグネチャを指定する型をデリゲートで定義する方法について説明します。このようなメソッドは、直接呼び出すか、別のメソッドに渡して呼び出すことができます。
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: f8184b87fc62f378fe72138733f87de924da60f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574563"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="46801-103">デリゲートとラムダ</span><span class="sxs-lookup"><span data-stu-id="46801-103">Delegates and lambdas</span></span>

<span data-ttu-id="46801-104">デリゲートは、特定のメソッド シグネチャを指定する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="46801-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="46801-105">このシグネチャを満たすメソッド (静的またはインスタンス) は、その型の変数に代入し、(適切な引数を使用して) 直接呼び出したり、別のメソッドに引数そのものとして渡してから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="46801-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="46801-106">次の例は、デリゲートの使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="46801-106">The following example demonstrates delegate use.</span></span>

```csharp
public class Program
{

  public delegate string Reverse(string s);

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Reverse rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

*   <span data-ttu-id="46801-107">4 行目で特定のシグネチャのデリゲート型を作成しています。この場合、文字列パラメーターを取ってから文字列パラメーターを返すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="46801-107">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="46801-108">6 行目で、まったく同じシグネチャを持つメソッドを提供することによって、デリゲートの実装を定義しています。</span><span class="sxs-lookup"><span data-stu-id="46801-108">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="46801-109">13 行目では、メソッドが `Reverse` デリゲートに準拠する型に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="46801-109">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="46801-110">最後に、15 行目で元に戻す文字列を渡してデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="46801-110">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="46801-111">開発プロセスを効率化するため、.NET にはプログラマが再利用できるデリゲート型のセットが含まれているため、新しい型を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="46801-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="46801-112">これらは `Func<>`、`Action<>`、および `Predicate<>` で、新しいデリゲート型を定義することなく、.NET API を通じてさまざまな場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="46801-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="46801-113">もちろん、これらの 3 つの間にはそのシグネチャで見られるように、いくつかの違いがあり、ほとんどがその用途に関係しています。</span><span class="sxs-lookup"><span data-stu-id="46801-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="46801-114">`Action<>` は、デリゲートの引数を使用してアクションを実行する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="46801-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="46801-115">`Func<>` は、通常、変換が手元にあるときに使用されます。つまり、デリゲートの引数を異なる結果に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46801-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="46801-116">これの典型的な例が予測です。</span><span class="sxs-lookup"><span data-stu-id="46801-116">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="46801-117">`Predicate<>` は、引数がデリゲートの条件を満たすかどうかを判断する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="46801-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="46801-118">`Func<T, bool>` として書き込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="46801-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="46801-119">ここで、上記の例を使用して、カスタム型の代わりに `Func<>` デリゲートを使用して書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="46801-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="46801-120">プログラムは引き続きまったく同じに実行されます。</span><span class="sxs-lookup"><span data-stu-id="46801-120">The program will continue running exactly the same.</span></span>

```csharp
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

<span data-ttu-id="46801-121">この簡単な例では、Main() メソッドの外部で定義されているメソッドは、少し余分なようです。</span><span class="sxs-lookup"><span data-stu-id="46801-121">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="46801-122">これは、.NET Framework 2.0 で**匿名デリゲート**の概念が導入されたためです。</span><span class="sxs-lookup"><span data-stu-id="46801-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="46801-123">そのサポートにより、追加の型やメソッドを指定せずに、"インライン" デリゲートを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="46801-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="46801-124">必要に応じて、デリゲートの定義を単純にインライン化します。</span><span class="sxs-lookup"><span data-stu-id="46801-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="46801-125">たとえば、デリゲートを切り替え、この匿名デリゲートを使用して、偶数だけをリストから除外し、コンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="46801-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="46801-126">強調表示された行に注目してください。</span><span class="sxs-lookup"><span data-stu-id="46801-126">Notice the highlighted lines.</span></span> <span data-ttu-id="46801-127">ご覧のように、デリゲートの本体は、他のデリゲートと同じく、単なる式のセットです。</span><span class="sxs-lookup"><span data-stu-id="46801-127">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="46801-128">しかし、それを別の定義にする代わりに、`List<T>` 型の `FindAll()` メソッドへの呼び出しでそれを_アド ホック_で導入しました。</span><span class="sxs-lookup"><span data-stu-id="46801-128">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="46801-129">ただし、この方法でも、破棄できる多くのコードがまだ残ります。</span><span class="sxs-lookup"><span data-stu-id="46801-129">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="46801-130">このような場合に**ラムダ式**が機能します。</span><span class="sxs-lookup"><span data-stu-id="46801-130">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="46801-131">ラムダ式 (または略して単に "ラムダ") は、最初に C# 3.0 で統合言語クエリ (LINQ) のコア ビルディング ブロックの 1 つとして導入されました。</span><span class="sxs-lookup"><span data-stu-id="46801-131">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="46801-132">これらは、デリゲートの使用の利便性を高める構文です。</span><span class="sxs-lookup"><span data-stu-id="46801-132">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="46801-133">これらは、シグネチャとメソッド本体を宣言しますが、デリゲートに割り当てられない限り、独自の正式な ID を持ちません。</span><span class="sxs-lookup"><span data-stu-id="46801-133">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="46801-134">デリゲートの場合とは異なり、これらはイベント登録の左側として、またはさまざまな Linq 句およびメソッドで、直接割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="46801-134">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="46801-135">ラムダ式はデリゲートを指定するもう 1 つの方法であるため、上記のサンプルを匿名デリゲートの代わりにラムダ式を使用するように書き換えることができるようになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="46801-135">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(i => i % 2 == 0);

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="46801-136">強調表示された行を見ると、ラムダ式がどのようなものかがわかります。</span><span class="sxs-lookup"><span data-stu-id="46801-136">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="46801-137">繰り返しますが、これは、匿名デリゲートの使用に**非常に**便利な構文であるため、内部での動作は匿名デリゲートの動作と似ています。</span><span class="sxs-lookup"><span data-stu-id="46801-137">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="46801-138">ここでも、ラムダは単なるデリゲートです。つまり、次のコード スニペットに示すように、ラムダは問題なくイベント ハンドラーとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="46801-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

## <a name="further-reading-and-resources"></a><span data-ttu-id="46801-139">参考資料とリソース</span><span class="sxs-lookup"><span data-stu-id="46801-139">Further reading and resources</span></span>

*   [<span data-ttu-id="46801-140">デリゲート</span><span class="sxs-lookup"><span data-stu-id="46801-140">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="46801-141">匿名関数</span><span class="sxs-lookup"><span data-stu-id="46801-141">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="46801-142">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="46801-142">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
