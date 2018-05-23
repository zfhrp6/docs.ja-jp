---
title: in パラメーター修飾子 (C# リファレンス)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 58500cf2caa1446af6b663f1b765c0be92309f1d
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="in-parameter-modifier-c-reference"></a><span data-ttu-id="076ea-102">in パラメーター修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="076ea-102">in parameter modifier (C# Reference)</span></span>

<span data-ttu-id="076ea-103">`in` キーワードによって、参照により引数が渡されます。</span><span class="sxs-lookup"><span data-stu-id="076ea-103">The `in` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="076ea-104">これは、[ref](ref.md) または [out](out-parameter-modifier.md) キーワードと似ています。ただし、、呼び出されたメソッドで `in` 引数を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="076ea-104">It is like the [ref](ref.md) or [out](out-parameter-modifier.md) keywords, except that `in` arguments cannot be modified by the called method.</span></span> <span data-ttu-id="076ea-105">`ref` 引数は変更できます。また、`out` 引数は呼び出し元が変更する必要があり、これらの変更は呼び出し元コンテキストで監視可能です。</span><span class="sxs-lookup"><span data-stu-id="076ea-105">Whereas `ref` arguments may be modified,  `out` arguments must be modified by the caller, and those modifications are observable in the calling context.</span></span>

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

<span data-ttu-id="076ea-106">前の例は、通常、`in` 修飾子が呼び出しサイトでは不要であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="076ea-106">The preceding example demonstrates that the `in` modifier is usually unnecessary at the call site.</span></span> <span data-ttu-id="076ea-107">これはメソッド宣言でのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="076ea-107">It is only required in the method declaration.</span></span>

> [!NOTE] 
> <span data-ttu-id="076ea-108">`foreach` ステートメントの一部、または LINQ クエリの `join` 句の一部として、型パラメーターが反変であることを示すために `in` キーワードをジェネリック型パラメーターで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="076ea-108">The `in` keyword can also be used with a generic type parameter to specify that the type parameter is contravariant, as part of a `foreach` statement, or as part of a `join` clause in a LINQ query.</span></span> <span data-ttu-id="076ea-109">これらのコンテキストでの `in` キーワードの使用の詳細については、これらすべての使用に関するリンクを提供する「[in](in.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="076ea-109">For more information on the use of the `in` keyword in these contexts, see [in](in.md), which provides links to all those uses.</span></span>
  
 <span data-ttu-id="076ea-110">`in` 引数として渡される変数は、メソッド呼び出しで渡される前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="076ea-110">Variables passed as `in` arguments must be initialized before being passed in a method call.</span></span> <span data-ttu-id="076ea-111">ただし、呼び出されたメソッドでは値の割り当てや、引数の変更を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="076ea-111">However, the called method may not assign a value or modify the argument.</span></span>  
  
 <span data-ttu-id="076ea-112">`in`、`ref`、`out`キーワードは実行時の動作が異なりますが、コンパイル時にメソッド シグネチャの一部とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="076ea-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="076ea-113">したがって、唯一の違いが、1 つのメソッドは `ref` または `in` 引数を受け取り、もう一方のメソッドは `out` 引数を受け取ることである場合、メソッドはオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="076ea-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="076ea-114">たとえば、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="076ea-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="076ea-115">`in` の有無に基づくオーバーロードが可能です。</span><span class="sxs-lookup"><span data-stu-id="076ea-115">Overloading based on the presence of `in` is allowed:</span></span>  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a><span data-ttu-id="076ea-116">オーバーロードの解決ルール</span><span class="sxs-lookup"><span data-stu-id="076ea-116">Overload resolution rules</span></span>

<span data-ttu-id="076ea-117">`in` 引数の意図を理解して、値と `in` 引数の比較によって、メソッドに対するオーバーロードの解決ルールを理解できます。</span><span class="sxs-lookup"><span data-stu-id="076ea-117">You can understand the overload resolution rules for methods with by value vs. `in` arguments by understanding the motivation for `in` arguments.</span></span> <span data-ttu-id="076ea-118">`in` パラメーターを使用してメソッドを定義すると、パフォーマンスを最適化できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="076ea-118">Defining methods using `in` parameters is a potential performance optimization.</span></span> <span data-ttu-id="076ea-119">一部の `struct` 型引数は、サイズが大きくなる可能性があり、メソッドが短いループまたは重要なコード パスで呼び出される場合、その構造のコピーのコストが重要になります。</span><span class="sxs-lookup"><span data-stu-id="076ea-119">Some `struct` type arguments may be large in size, and when methods are called in tight loops or critical code paths, the cost of copying those structures is critical.</span></span> <span data-ttu-id="076ea-120">呼び出されたメソッドは引数の状態を変更しないため、メソッドで `in` パラメーターを宣言して、参照で安全に渡すことができる引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="076ea-120">Methods declare `in` parameters to specify that arguments may be passed by reference safely because the called method does not modify the state of that argument.</span></span> <span data-ttu-id="076ea-121">参照によりこれらの引数を渡して、(可能性がある) 高額なコピーを回避します。</span><span class="sxs-lookup"><span data-stu-id="076ea-121">Passing those arguments by reference avoids the (potentially) expensive copy.</span></span> 

<span data-ttu-id="076ea-122">呼び出しサイトで引数に `in` を指定することは、通常は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="076ea-122">Specifying `in` for arguments at the call site is typically optional.</span></span> <span data-ttu-id="076ea-123">値で引数を渡す場合と `in` 修飾子を使用して参照で渡す場合の間に、セマンティックの相違点はありません。</span><span class="sxs-lookup"><span data-stu-id="076ea-123">There is no semantic difference between passing arguments by value and passing them by reference using the `in` modifier.</span></span> <span data-ttu-id="076ea-124">引数の値が変更される可能性があることを示す必要はないため、呼び出しサイトの `in` 修飾子は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="076ea-124">The `in` modifier at the call site is optional because you don't need to indicate that the argument's value might be changed.</span></span> <span data-ttu-id="076ea-125">呼び出しサイトで `in` 修飾子を明示的に追加して、引数が値ではなく、参照で渡されるようにします。</span><span class="sxs-lookup"><span data-stu-id="076ea-125">You explicitly add the `in` modifier at the call site to ensure the argument is passed by reference, not by value.</span></span> <span data-ttu-id="076ea-126">明示的に `in` を使用すると、次の 2 つの効果があります。</span><span class="sxs-lookup"><span data-stu-id="076ea-126">Explicitly using `in` has the following two effects:</span></span>

<span data-ttu-id="076ea-127">1 つ目は、呼び出しサイトで `in` を指定すると、一致する `in` パラメーターで定義されたメソッドがコンパイラで強制的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="076ea-127">First, specifying `in` at the call site forces the compiler to select a method defined with a matching `in` parameter.</span></span> <span data-ttu-id="076ea-128">それ以外の場合は、2 つのメソッドで `in` の有無のみが異なるときは、値によるオーバーロードの方が適しています。</span><span class="sxs-lookup"><span data-stu-id="076ea-128">Otherwise, when two methods differ only in the presence of `in`, the by value overload is a better match.</span></span>

<span data-ttu-id="076ea-129">2 つ目は、`in` を指定して、参照で引数を渡す意図を宣言します。</span><span class="sxs-lookup"><span data-stu-id="076ea-129">Second, specifying `in` declares your intent to pass an argument by reference.</span></span> <span data-ttu-id="076ea-130">`in` で使用される引数では、直接参照できる場所を表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="076ea-130">The argument used with `in` must represent a location that can be directly referred to.</span></span> <span data-ttu-id="076ea-131">`out` および `ref` 引数と同じ一般ルールが適用されます。定数、通常のプロパティ、または値を生成するその他の式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="076ea-131">The same general rules for `out` and `ref` arguments apply: You cannot use constants, ordinary properties, or other expressions that produce values.</span></span> <span data-ttu-id="076ea-132">それ以外の場合は、呼び出しサイトで `in` を省略すると、メソッドに読み取り専用の参照で渡すために、一時変数の作成を許可することが、コンパイラに通知されます。</span><span class="sxs-lookup"><span data-stu-id="076ea-132">Otherwise, omitting `in` at the call site informs the compiler that you will allow it to create a temporary variable to pass by read-only reference to the method.</span></span> <span data-ttu-id="076ea-133">コンパイラでは、一時変数を作成して、`in` 引数でのいくつかの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="076ea-133">The compiler creates a temporary variable to overcome several restrictions with `in` arguments:</span></span>

- <span data-ttu-id="076ea-134">一時変数では、`in` パラメーターとしてコンパイル時の定数を許可します。</span><span class="sxs-lookup"><span data-stu-id="076ea-134">A temporary variable allows compile-time constants as `in` parameters.</span></span>
- <span data-ttu-id="076ea-135">一時変数では、プロパティ、または `in` パラメーターのその他の式を許可します。</span><span class="sxs-lookup"><span data-stu-id="076ea-135">A temporary variable allows properties, or other expressions for `in` parameters.</span></span>
- <span data-ttu-id="076ea-136">一時変数では、引数型からパラメーターの型への暗黙の変換がある引数を許可します。</span><span class="sxs-lookup"><span data-stu-id="076ea-136">A temporary variable allows arguments where there is an implicit conversion from the argument type to the parameter type.</span></span>

<span data-ttu-id="076ea-137">先のすべてのインスタンスで、コンパイラは定数、プロパティ、またはその他の式の値を格納する一時変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="076ea-137">In all the preceding instances, the compiler creates a temporary variable that stores the value of the constant, property, or other expression.</span></span>

<span data-ttu-id="076ea-138">これらのルールが発生するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="076ea-138">The following code illustrates these rules:</span></span>

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="076ea-139">ここでは、値の引数で使用する別のメソッドが使用できたと想定します。</span><span class="sxs-lookup"><span data-stu-id="076ea-139">Now, suppose another method using by value arguments was available.</span></span> <span data-ttu-id="076ea-140">次のコードに示すように、結果が変更されます。</span><span class="sxs-lookup"><span data-stu-id="076ea-140">The results change as shown in the following code:</span></span>

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

<span data-ttu-id="076ea-141">引数が参照で渡されるメソッドの呼び出しは、最後のメソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="076ea-141">The only method call where the argument is passed by reference is the final one.</span></span>

> [!NOTE]
> <span data-ttu-id="076ea-142">先のコードでは、わかりやすくするために `int` を引数型として使用します。</span><span class="sxs-lookup"><span data-stu-id="076ea-142">The preceding code uses `int` as the argument type for simplicity.</span></span> <span data-ttu-id="076ea-143">`int` は最新のマシンの参照より大きくなることはないため、読み取り専用の参照として単一の `int` を渡すメリットはありません。</span><span class="sxs-lookup"><span data-stu-id="076ea-143">Because `int` is no larger than a reference in most modern machines, there is no benefit to passing a single `int` as a readonly reference.</span></span> 

## <a name="limitations-on-in-parameters"></a><span data-ttu-id="076ea-144">`in` パラメーターの制限</span><span class="sxs-lookup"><span data-stu-id="076ea-144">Limitations on `in` parameters</span></span>

<span data-ttu-id="076ea-145">次の種類のメソッドには、`in`、`ref`、`out` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="076ea-145">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="076ea-146">[async](async.md) 修飾子を使用して定義した Async メソッド。</span><span class="sxs-lookup"><span data-stu-id="076ea-146">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="076ea-147">[yield return](yield.md) または `yield break` ステートメントを含む Iterator メソッド。</span><span class="sxs-lookup"><span data-stu-id="076ea-147">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="076ea-148">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="076ea-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="076ea-149">参照</span><span class="sxs-lookup"><span data-stu-id="076ea-149">See Also</span></span>  
 [<span data-ttu-id="076ea-150">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="076ea-150">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="076ea-151">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="076ea-151">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="076ea-152">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="076ea-152">C# Keywords</span></span>](index.md)  
 <span data-ttu-id="076ea-153">[メソッドのパラメーター](method-parameters.md) [値の型による参照セマンティクス](../../reference-semantics-with-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="076ea-153">[Method Parameters](method-parameters.md) [Reference Semantics with Value Types](../../reference-semantics-with-value-types.md)</span></span>
