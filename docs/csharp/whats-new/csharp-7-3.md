---
title: C# 7.3 の新機能
description: C# 7.3 の新機能の概要
ms.date: 05/16/2018
ms.openlocfilehash: 135351fa06a498e4aa90cb4d9372880b8119de0f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106776"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="ea6dc-103">C# 7.3 の新機能</span><span class="sxs-lookup"><span data-stu-id="ea6dc-103">What's new in C# 7.3</span></span>

<span data-ttu-id="ea6dc-104">C# 7.3 リリースには 2 つの主要なテーマがあります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="ea6dc-105">1 つ目のテーマは、アンセーフ コードと同様のパフォーマンスをセーフ コードで確保するための機能の提供です。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="ea6dc-106">2 つ目のテーマは、既存の機能のインクリメンタルな改善の提供です。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="ea6dc-107">また、新しいコンパイラ オプションがこのリリースで追加されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="ea6dc-108">次の新機能は、セーフ コードのパフォーマンス向上のテーマをサポートします。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="ea6dc-109">ピン留めを使用せずに fixed フィールドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="ea6dc-110">`ref` ローカル変数を再割り当てできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="ea6dc-111">`stackalloc` 配列で初期化子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="ea6dc-112">パターンをサポートする型と共に `fixed` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="ea6dc-113">追加のジェネリック制約を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="ea6dc-114">既存の機能が次のように強化されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="ea6dc-115">タプル型を使用して `==` と `!=` をテストできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="ea6dc-116">式の変数をより多くの場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="ea6dc-117">自動実装プロパティのバッキング フィールドに属性をアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="ea6dc-118">引数が `in` によって異なる場合のメソッド解決が改善されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="ea6dc-119">オーバーロードの解決のあいまいなケースが削減されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="ea6dc-120">新しいコンパイラ オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-120">The new compiler options are:</span></span>

- <span data-ttu-id="ea6dc-121">`-publicsign`: オープン ソース ソフトウェア (OSS) のアセンブリの署名を可能にします。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="ea6dc-122">`-pathmap`: ソース ディレクトリのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="ea6dc-123">この記事の残りの部分では、それぞれの機能強化の詳細とリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-performant-safe-code"></a><span data-ttu-id="ea6dc-124">パフォーマンスに優れたセーフ コードの実現</span><span class="sxs-lookup"><span data-stu-id="ea6dc-124">Enabling more performant safe code</span></span>

<span data-ttu-id="ea6dc-125">アンセーフ コードと同様のパフォーマンスを確保した C# コードを安全に記述できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="ea6dc-126">セーフ コードは、バッファー オーバーラン、ストレイ ポインター、その他のメモリ アクセス エラーなどのエラーを回避します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="ea6dc-127">ここで説明する新機能は、検証可能なセーフ コードの機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="ea6dc-128">安全なコンストラクトを使用してより多くのコードを記述するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="ea6dc-129">以下に示す機能によって、コードの記述が容易になります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="ea6dc-130">ピン留めが不要な `fixed` フィールドのインデックス付け</span><span class="sxs-lookup"><span data-stu-id="ea6dc-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="ea6dc-131">たとえば、次の構造体があるとします。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="ea6dc-132">以前のバージョンの C# では、`myFixedField` の一部であるいずれかの整数にアクセスするために変数のピン留めが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="ea6dc-133">現在では、次のコードが安全なコンテキストでコンパイルされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-133">Now, the following code compiles in a safe context:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="ea6dc-134">変数 `p` は `myFixedField` の 1 個の要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="ea6dc-135">個別の `int*` 変数を宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="ea6dc-136">`unsafe` コンテキストは引き続き必要です。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="ea6dc-137">以前のバージョンの C# では、2 番目の固定ポインターを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="ea6dc-138">詳しくは、[`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-138">Fore more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="ea6dc-139">再割り当て可能な `ref` ローカル変数</span><span class="sxs-lookup"><span data-stu-id="ea6dc-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="ea6dc-140">初期化後に別のインスタンスを参照するために、`ref` ローカル変数を再割り当てできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="ea6dc-141">次のコードがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="ea6dc-142">詳しくは、[`ref` 戻り値と `ref` ローカル変数](../programming-guide/classes-and-structs/ref-returns.md)に関する記事と [`foreach`](../language-reference/keywords/foreach-in.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="ea6dc-143">`stackalloc` 配列による初期化子のサポート</span><span class="sxs-lookup"><span data-stu-id="ea6dc-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="ea6dc-144">配列を初期化する際に、配列内の要素の値を指定することが可能でした。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="ea6dc-145">現在では、`stackalloc` で宣言された配列に同じ構文を適用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="ea6dc-146">詳しくは、言語リファレンスの [`stackalloc` ステートメント](../language-reference/keywords/stackalloc.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="ea6dc-147">多くの型による `fixed` ステートメントのサポート</span><span class="sxs-lookup"><span data-stu-id="ea6dc-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="ea6dc-148">`fixed` ステートメントは、限られた一連の型をサポートしていました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="ea6dc-149">C# 7.3 以降では、`ref T` または `ref readonly T` を返す `GetPinnableReference()` メソッドを格納する型として `fixed` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="ea6dc-150">この機能の追加により、`fixed` を <xref:System.Span%601?displayProperty=nameWithType> および関連する型と共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="ea6dc-151">詳しくは、言語リファレンスの [`fixed` ステートメント](../language-reference/keywords/fixed-statement.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="ea6dc-152">ジェネリック制約の拡張</span><span class="sxs-lookup"><span data-stu-id="ea6dc-152">Enhanced generic constraints</span></span>

<span data-ttu-id="ea6dc-153">型パラメーターの基底クラスの制約として、<xref:System.Enum?displayProperty=nameWithType> 型または <xref:System.Delegate?displayProperty=nameWithType> 型を指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="ea6dc-154">また、新しい `unmanaged` 制約を使用して、型パラメーターが**アンマネージ型**である必要があることを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="ea6dc-155">**アンマネージ型**は参照型ではない型であり、任意の入れ子のレベルに参照型を含みません。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="ea6dc-156">詳しくは、[`where` ジェネリック制約](../language-reference/keywords/where-generic-type-constraint.md)および[型パラメーターの制約](../programming-guide/generics/constraints-on-type-parameters.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="ea6dc-157">既存の機能の改善</span><span class="sxs-lookup"><span data-stu-id="ea6dc-157">Make existing features better</span></span>

<span data-ttu-id="ea6dc-158">2 つ目のテーマは、言語の機能の改善の提供です。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-158">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="ea6dc-159">以下に示す機能によって、C# を記述する際の生産性が向上します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-159">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="ea6dc-160">タプルによる `==` と `!=` のサポート</span><span class="sxs-lookup"><span data-stu-id="ea6dc-160">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="ea6dc-161">C# のタプル型で `==` と `!=` がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-161">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="ea6dc-162">詳しくは、[タプル](../tuples.md)に関する記事の[等値](../tuples.md#equality-and-tuples)について説明したセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-162">Fore more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="ea6dc-163">自動実装プロパティのバッキング フィールドへの属性のアタッチ</span><span class="sxs-lookup"><span data-stu-id="ea6dc-163">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="ea6dc-164">次の構文がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-164">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="ea6dc-165">属性 `SomeThingAboutFieldAttribute` は、`SomeProperty` のコンパイラによって生成されるバッキング フィールドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-165">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="ea6dc-166">詳しくは、C# プログラミング ガイドの「[属性](../programming-guide/concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-166">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="ea6dc-167">`in` メソッドのオーバーロードの解決のタイブレーカー</span><span class="sxs-lookup"><span data-stu-id="ea6dc-167">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="ea6dc-168">`in` 引数修飾子が追加されると、次の 2 つのメソッドがあいまいさの原因となっていました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-168">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="ea6dc-169">現在では、値による (前述の例の最初の方法) オーバーロードが readonly 参照によるオーバーロードよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-169">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="ea6dc-170">readonly 参照引数を使用してバージョンを呼び出すには、メソッドの呼び出し時に `in` 修飾子を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-170">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="ea6dc-171">これはバグの修正として実装されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-171">This was implemented as a bug fix.</span></span> <span data-ttu-id="ea6dc-172">これにより、言語バージョンが "7.2" に設定されている場合でもあいまいさが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-172">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="ea6dc-173">詳しくは、[`in` パラメーター修飾子](../language-reference/keywords/in-parameter-modifier.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-173">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="ea6dc-174">初期化子における式の変数の拡張</span><span class="sxs-lookup"><span data-stu-id="ea6dc-174">Extend expression variables in initializers</span></span>

<span data-ttu-id="ea6dc-175">`out` 変数の宣言を許可するために C# 7.0 に追加された構文が、フィールド初期化子、プロパティ初期化子、コンストラクター初期化子、およびクエリ句を含めるように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-175">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="ea6dc-176">これにより、次の例に示すようなコードを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-176">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a><span data-ttu-id="ea6dc-177">オーバーロード候補の改善</span><span class="sxs-lookup"><span data-stu-id="ea6dc-177">Improved overload candidates</span></span>

<span data-ttu-id="ea6dc-178">すべてのリリースにおいて、あいまいなメソッド呼び出しに対する "明らかな" 選択肢が存在する状況に対応するようにオーバーロードの解決ルールが更新されました。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-178">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="ea6dc-179">このリリースでは、コンパイラが明らかな選択肢を選択できるようにする 3 つの新しいルールが追加されています。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-179">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="ea6dc-180">インスタンス メンバーと静的メンバーの両方がメソッド グループに含まれている場合は、インスタンス レシーバーまたはコンテキストを指定せずにメソッドが呼び出されると、コンパイラがインスタンス メンバーを破棄します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-180">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="ea6dc-181">インスタンス レシーバーを使用してメソッドが呼び出された場合、コンパイラは静的メンバーを破棄します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-181">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="ea6dc-182">レシーバーがない場合、コンパイラは静的メンバーだけを静的コンテキストに含めます。それ以外の場合は、静的メンバーとインスタンス メンバーの両方を含めます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-182">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="ea6dc-183">レシーバーがあいまいなインスタンスまたは型である場合、コンパイラは両方のメンバーを含めます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-183">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="ea6dc-184">暗黙的な `this` インスタンス レシーバーを使用できない静的コンテキストには、`this` が定義されないメンバー (静的メンバーなど) の本体および `this` を使用できない場所 (フィールド初期化子やコンストラクター初期化子など) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-184">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="ea6dc-185">型引数が制約を満たしていない複数のジェネリック メソッドがメソッド グループに含まれている場合、そのグループのメンバーは候補セットから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-185">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="ea6dc-186">メソッド グループの変換では、戻り値の型がデリゲートの戻り値の型と一致しない候補メソッドが候補セットから削除されます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-186">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="ea6dc-187">適切なメソッドがわかっている場合には、あいまいなメソッドのオーバーロードに対するコンパイラ エラーが少なくなることを認識できるため、この変更点にのみ注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-187">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="ea6dc-188">新しいコンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ea6dc-188">New compiler options</span></span>

<span data-ttu-id="ea6dc-189">新しいコンパイラ オプションでは、C# プログラムの新しいビルドと DevOps のシナリオがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-189">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="ea6dc-190">公開署名またはオープン ソース署名</span><span class="sxs-lookup"><span data-stu-id="ea6dc-190">Public or Open Source signing</span></span>

<span data-ttu-id="ea6dc-191">`-publicsign` コンパイラ オプションは、公開キーを使用してアセンブリに署名するようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-191">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="ea6dc-192">アセンブリは署名済みとしてマークされますが、署名は公開キーから取得されます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-192">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="ea6dc-193">このオプションでは、公開キーを使用するオープン ソース プロジェクトから署名済みのアセンブリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-193">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="ea6dc-194">詳しくは、[-publicsign コンパイラ オプション](../language-reference/compiler-options/publicsign-compiler-option.md)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-194">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="ea6dc-195">pathmap</span><span class="sxs-lookup"><span data-stu-id="ea6dc-195">pathmap</span></span>

<span data-ttu-id="ea6dc-196">`-pathmap` コンパイラ オプションは、ビルド環境からのソース パスをマップ済みのソース パスに置き換えるようにコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-196">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="ea6dc-197">`-pathmap` オプションは、コンパイラが記述した PDB ファイルまたは <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> のソース パスを制御します。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-197">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="ea6dc-198">詳しくは、[-pathmap コンパイラ オプション](../language-reference/compiler-options/pathmap-compiler-option.md)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea6dc-198">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
