---
title: F# のツアー
description: F# のプログラミング言語のコード サンプルを使ってこのツアーでの主な機能のいくつかを確認します。
ms.date: 02/28/2018
ms.openlocfilehash: 2ce251b90d5c202996e0b1673e8f7f378a38af5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="tour-of-f"></a><span data-ttu-id="1f616-103">F# のツアー</span><span class="sxs-lookup"><span data-stu-id="1f616-103">Tour of F#</span></span> #

<span data-ttu-id="1f616-104">F# について学習する最善の方法では、f# コードを読み書きします。</span><span class="sxs-lookup"><span data-stu-id="1f616-104">The best way to learn about F# is to read and write F# code.</span></span>  <span data-ttu-id="1f616-105">この記事は、f# 言語の主な機能の一部の機能を確認として機能し、コンピューターに対して実行できます。 一部のコード スニペットでわかります。</span><span class="sxs-lookup"><span data-stu-id="1f616-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span>  <span data-ttu-id="1f616-106">詳細については、開発環境をセットアップして、チェック アウト[作業の開始](tutorials/getting-started/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f616-106">To learn about setting up a development environment, check out [Getting Started](tutorials/getting-started/index.md).</span></span>

<span data-ttu-id="1f616-107">F# である 2 つの主要な概念: 関数と型。</span><span class="sxs-lookup"><span data-stu-id="1f616-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="1f616-108">このツアーはこれら 2 つの概念には、言語の機能を強調します。</span><span class="sxs-lookup"><span data-stu-id="1f616-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="1f616-109">関数とモジュール</span><span class="sxs-lookup"><span data-stu-id="1f616-109">Functions and Modules</span></span>

<span data-ttu-id="1f616-110">任意の f# プログラムの最も基本的な部分が***関数***に編成***モジュール***です。</span><span class="sxs-lookup"><span data-stu-id="1f616-110">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="1f616-111">[関数](language-reference/functions/index.md)の入力、出力を生成するために作業を実行し、下では、編成された[モジュール](language-reference/modules.md)、f# で作業をグループ化する主要な手段であります。</span><span class="sxs-lookup"><span data-stu-id="1f616-111">[Functions](language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="1f616-112">使用して定義されている、 [ `let`バインディング](language-reference/functions/let-bindings.md)関数の名前し、その引数を定義します。</span><span class="sxs-lookup"><span data-stu-id="1f616-112">They are defined using the [`let` binding](language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="1f616-113">`let` バインドも値を他の言語での変数のような名前にバインドする方法です。</span><span class="sxs-lookup"><span data-stu-id="1f616-113">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="1f616-114">`let` バインディングは***不変***既定では、値または関数が名前にバインドされると、それを変更できないことを意味するインプレースでします。</span><span class="sxs-lookup"><span data-stu-id="1f616-114">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="1f616-115">これは、他の言語は、変数とは対照的***変更可能な***時間で任意の時点でその値の意味を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-115">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="1f616-116">変更可能なバインディングを必要とする場合を使用できます`let mutable ...`構文です。</span><span class="sxs-lookup"><span data-stu-id="1f616-116">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="1f616-117">数値、ブール値、および文字列</span><span class="sxs-lookup"><span data-stu-id="1f616-117">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="1f616-118">.NET 言語として f# をサポートしている同じ基になる[プリミティブ型](language-reference/primitive-types.md).NET 内に存在します。</span><span class="sxs-lookup"><span data-stu-id="1f616-118">As a .NET language, F# supports the same underlying [primitive types](language-reference/primitive-types.md) that exist in .NET.</span></span>

<span data-ttu-id="1f616-119">F# でさまざまな数値型の表現を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f616-119">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="1f616-120">ここでは、どのようなブール値と次のように基本的な条件付きロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="1f616-120">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="1f616-121">ここではどのような basic[文字列](language-reference/strings.md)次のように操作します。</span><span class="sxs-lookup"><span data-stu-id="1f616-121">And here's what basic [string](language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="1f616-122">タプル</span><span class="sxs-lookup"><span data-stu-id="1f616-122">Tuples</span></span>

<span data-ttu-id="1f616-123">[組](language-reference/tuples.md)f# では大きな問題は、します。</span><span class="sxs-lookup"><span data-stu-id="1f616-123">[Tuples](language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="1f616-124">これらは、名前のない、順序付きの値は、特定の値として扱うことのグループです。</span><span class="sxs-lookup"><span data-stu-id="1f616-124">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="1f616-125">これらの集計される、その他の値からの値として考えます。</span><span class="sxs-lookup"><span data-stu-id="1f616-125">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="1f616-126">判別しやすいように、関数から複数の値を返すまたはアドホック利便性の値をグループ化など、数多くの用途があります。</span><span class="sxs-lookup"><span data-stu-id="1f616-126">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="1f616-127">F# 4.1、時点で作成することも`struct`組。</span><span class="sxs-lookup"><span data-stu-id="1f616-127">As of F# 4.1, you can also create `struct` tuples.</span></span>  <span data-ttu-id="1f616-128">これらと相互運用も完全にも C# 7 または Visual Basic の 15 の組`struct`組。</span><span class="sxs-lookup"><span data-stu-id="1f616-128">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="1f616-129">ことに注意することが重要`struct`組が値型、タプルを参照する暗黙的に変換することはできませんまたはその逆です。</span><span class="sxs-lookup"><span data-stu-id="1f616-129">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="1f616-130">参照と構造体の組の間で明示的に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f616-130">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="1f616-131">パイプラインおよびコンポジション</span><span class="sxs-lookup"><span data-stu-id="1f616-131">Pipelines and Composition</span></span>

<span data-ttu-id="1f616-132">パイプ演算子 (`|>`、 `<|`、 `||>`、 `<||`、 `|||>`、 `<|||`) と合成演算子 (`>>`と`<<`) の使用頻度が f# でのデータを処理するときにします。</span><span class="sxs-lookup"><span data-stu-id="1f616-132">Pipe operators (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) and composition operators (`>>` and `<<`) are used extensively when processing data in F#.</span></span>  <span data-ttu-id="1f616-133">これらの演算子は、柔軟な方法で「パイプライン」関数を確立するために使用できる関数です。</span><span class="sxs-lookup"><span data-stu-id="1f616-133">These operators are functions which allow you to establish "pipelines" of functions in a flexible manner.</span></span>  <span data-ttu-id="1f616-134">次の例は、どのようにこれらの演算子のパイプラインを構築する単純な機能の利点がかかる場合があります手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f616-134">The following example walks through how you could take advantage of these operators to build a simple functional pipeline.</span></span>

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

<span data-ttu-id="1f616-135">行われた上記のサンプルの f#、リストの処理機能、ファースト クラスの関数を含む多数の機能の使用と[部分適用](language-reference/functions/index.md#partial-application-of-arguments)です。</span><span class="sxs-lookup"><span data-stu-id="1f616-135">The above sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](language-reference/functions/index.md#partial-application-of-arguments).</span></span>  <span data-ttu-id="1f616-136">これらの概念のそれぞれの深い理解がやや高度なことができますになる、ことがありますクリア関数を使用して、パイプラインを構築するときに、データを処理する方法に簡単にします。</span><span class="sxs-lookup"><span data-stu-id="1f616-136">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="1f616-137">リスト、配列、およびシーケンス</span><span class="sxs-lookup"><span data-stu-id="1f616-137">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="1f616-138">リスト、配列、およびシーケンスは、f# コア ライブラリの次の 3 つの主なコレクション型です。</span><span class="sxs-lookup"><span data-stu-id="1f616-138">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="1f616-139">[一覧表示](language-reference/lists.md)は同じ型の要素の順序付けられ、変更できないコレクションです。</span><span class="sxs-lookup"><span data-stu-id="1f616-139">[Lists](language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="1f616-140">シングル リンク リスト、大規模な場合、列挙がランダム アクセスと連結に適さないのために用意されていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1f616-140">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="1f616-141">これは通常のリストを表すシングル リンク リストを使用しないでください、人気のある他の言語のリストとは対照的です。</span><span class="sxs-lookup"><span data-stu-id="1f616-141">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="1f616-142">[配列](language-reference/arrays.md)が固定サイズ、*変更可能な*同じ型の要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="1f616-142">[Arrays](language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="1f616-143">要素の高速なランダム アクセスをサポートし、F# では単に連続するメモリ ブロックのためのリストよりも高速です。</span><span class="sxs-lookup"><span data-stu-id="1f616-143">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="1f616-144">[シーケンス](language-reference/sequences.md)要素は、すべて同じ型の一連の論理がします。</span><span class="sxs-lookup"><span data-stu-id="1f616-144">[Sequences](language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="1f616-145">これらは、リストや配列、任意の論理一連の要素に、"view"することのできるよりもより一般的な型です。</span><span class="sxs-lookup"><span data-stu-id="1f616-145">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="1f616-146">目立つことができるので***レイジー***、つまり、必要な場合にのみ要素を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="1f616-146">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="1f616-147">再帰関数</span><span class="sxs-lookup"><span data-stu-id="1f616-147">Recursive Functions</span></span>

<span data-ttu-id="1f616-148">コレクションまたは要素のシーケンスの処理は、普通で[再帰](language-reference/functions/index.md#recursive-functions)f# でします。</span><span class="sxs-lookup"><span data-stu-id="1f616-148">Processing collections or sequences of elements is typically done with [recursion](language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="1f616-149">F# がループと命令型プログラミングのサポートがありますが、再帰が優先正確性を保証する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="1f616-149">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

>[!NOTE]
<span data-ttu-id="1f616-150">次の例を使用してパターン マッチを利用、`match`式。</span><span class="sxs-lookup"><span data-stu-id="1f616-150">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="1f616-151">この基本的な構造は、この記事で後述について説明します。</span><span class="sxs-lookup"><span data-stu-id="1f616-151">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="1f616-152">F# でも末尾呼び出しの最適化で完全にサポートされるされてがループ構造と同じ速度で単なるように、再帰呼び出しを最適化する方法です。</span><span class="sxs-lookup"><span data-stu-id="1f616-152">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="1f616-153">レコードと判別された共用体型</span><span class="sxs-lookup"><span data-stu-id="1f616-153">Record and Discriminated Union Types</span></span>

<span data-ttu-id="1f616-154">レコードと、共用体の型は f# コードで使用される 2 つの基本的なデータ型、f# のプログラムでデータを表現する最善の方法では、通常</span><span class="sxs-lookup"><span data-stu-id="1f616-154">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="1f616-155">このため、クラスのような他の言語で、構造の等値セマンティクスがあることの主な相違点の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="1f616-155">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="1f616-156">つまり、「ネイティブ」比較が等しいかどうかは簡単です - 1 つが、互いに等しいかどうかはチェックします。</span><span class="sxs-lookup"><span data-stu-id="1f616-156">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="1f616-157">[レコード](language-reference/records.md)は省略可能なメンバー (メソッド) などで、名前付きの値の集計です。</span><span class="sxs-lookup"><span data-stu-id="1f616-157">[Records](language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="1f616-158">C# や Java に慣れている場合、これら必要がありますと思われるした poco からまたは Pojo - と同様に構造の等価と手続きだけです。</span><span class="sxs-lookup"><span data-stu-id="1f616-158">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="1f616-159">F# 4.1、時点では、レコードとしても表すことができる`struct`s。</span><span class="sxs-lookup"><span data-stu-id="1f616-159">As of F# 4.1, you can also represent Records as `struct`s.</span></span>  <span data-ttu-id="1f616-160">これは、`[<Struct>]`属性。</span><span class="sxs-lookup"><span data-stu-id="1f616-160">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="1f616-161">[判別共用体 (Du)](language-reference/discriminated-unions.md)名前付きのフォームまたはケースの数を生じる可能性がある値が格納されています。</span><span class="sxs-lookup"><span data-stu-id="1f616-161">[Discriminated Unions (DUs)](language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="1f616-162">型に格納されたデータには、個別の値をいくつかのいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-162">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="1f616-163">として Du を使用することもできます。*単一ケースの判別共用体*、プリミティブ型をモデリングするドメインを支援します。</span><span class="sxs-lookup"><span data-stu-id="1f616-163">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="1f616-164">多くの場合、文字列およびその他のプリミティブ型、何かを表すために使用し、特定の意味を指定されたためです。</span><span class="sxs-lookup"><span data-stu-id="1f616-164">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="1f616-165">ただし、データのプリミティブ形式のみを使用する可能性が誤って正しくない値を割り当てるときに!</span><span class="sxs-lookup"><span data-stu-id="1f616-165">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="1f616-166">個別の単一ケース共用体の情報の各型を表すと、このシナリオでは、正しいかどうかを適用できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-166">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="1f616-167">単一ケース判別共用体、基になる値を取得する、上記のサンプルに示すように明示的に unwrap する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f616-167">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="1f616-168">さらに、Du もサポートして再帰的な定義ツリーと本質的に再帰型データを簡単に記述することができます。</span><span class="sxs-lookup"><span data-stu-id="1f616-168">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="1f616-169">たとえば、ここでは方法でのバイナリ検索ツリーを表すことができる`exists`と`insert`関数。</span><span class="sxs-lookup"><span data-stu-id="1f616-169">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="1f616-170">Du を使用すると、データ型にツリーを再帰的な構造を表すできますが、この再帰的な構造で動作している単純ではいて正確性を保証します。</span><span class="sxs-lookup"><span data-stu-id="1f616-170">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="1f616-171">次のようにも、パターン マッチでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1f616-171">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="1f616-172">さらに、として Du を表すことができる`struct`で秒、`[<Struct>]`属性。</span><span class="sxs-lookup"><span data-stu-id="1f616-172">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="1f616-173">ただし、これを実施する際に注意する 2 つの主な操作があります。</span><span class="sxs-lookup"><span data-stu-id="1f616-173">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="1f616-174">DU 構造体は、再帰的に定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f616-174">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="1f616-175">DU 構造体には、そのケースのそれぞれに一意の名前が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f616-175">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="1f616-176">上記に従わないと、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1f616-176">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="1f616-177">パターン マッチ</span><span class="sxs-lookup"><span data-stu-id="1f616-177">Pattern Matching</span></span>

<span data-ttu-id="1f616-178">[パターン マッチ](language-reference/pattern-matching.md)f# の型に対する操作のための正確性をできる f# 言語機能します。</span><span class="sxs-lookup"><span data-stu-id="1f616-178">[Pattern Matching](language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="1f616-179">上記のサンプルからもわかるように相当量の`match x with ...`構文です。</span><span class="sxs-lookup"><span data-stu-id="1f616-179">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="1f616-180">このコンストラクトは、コンパイラは、排他的なパターン一致としてを介して、既知のデータ型を使用する場合は、可能なすべてのケースのアカウントを強制するには、データ型の"shape"を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="1f616-180">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="1f616-181">これは正しいかどうか、非常に強力であり、コンパイル時にランタイム問題になる新機能は通常「リフト」に適切に使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-181">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

<span data-ttu-id="1f616-182">短縮形を使用することもできます`function`のまま続行する関数を使用して作成する場合に有用なパターンに一致させるためのコンストラクト[部分適用](language-reference/functions/index.md#partial-application-of-arguments):。</span><span class="sxs-lookup"><span data-stu-id="1f616-182">You can also use the shorthand `function` construct for pattern matching, which is useful when you're writing functions which make use of [Partial Application](language-reference/functions/index.md#partial-application-of-arguments):</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

<span data-ttu-id="1f616-183">使用に問題がありますが、`_`パターン。</span><span class="sxs-lookup"><span data-stu-id="1f616-183">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="1f616-184">これと呼ばれますが、[ワイルドカード パターン](language-reference/pattern-matching.md#wildcard-pattern)、「関係ない何かが」という方法であります。</span><span class="sxs-lookup"><span data-stu-id="1f616-184">This is known as the [Wildcard Pattern](language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="1f616-185">、は便利ですが排他的なパターン マッチを誤ってバイパスおよび不要になったコンパイル時の実施恩恵を使用して注意が必要でない場合`_`です。</span><span class="sxs-lookup"><span data-stu-id="1f616-185">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="1f616-186">分解された型の特定部分を考慮しない場合に最も使用される照合、または最後の句のパターン マッチ式内のすべての意味のあるケースを列挙したときとパターンします。</span><span class="sxs-lookup"><span data-stu-id="1f616-186">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="1f616-187">[アクティブ パターン](language-reference/active-patterns.md)パターン マッチで使用する別の強力な構造は、します。</span><span class="sxs-lookup"><span data-stu-id="1f616-187">[Active Patterns](language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="1f616-188">パターン一致の呼び出しサイトでそれらを分解する、カスタムのフォームに入力データを分割できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-188">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="1f616-189">パラメーター化できる、ため、関数として、パーティションを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="1f616-189">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="1f616-190">アクティブ パターンをサポートするために、前の例を展開する次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1f616-190">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a><span data-ttu-id="1f616-191">省略可能な型</span><span class="sxs-lookup"><span data-stu-id="1f616-191">Optional Types</span></span>

<span data-ttu-id="1f616-192">判別共用体の型の 1 つの特殊なケースは、オプション型、これは、f# コア ライブラリの一部であるために便利です。</span><span class="sxs-lookup"><span data-stu-id="1f616-192">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="1f616-193">[オプションの種類](language-reference/options.md)は 2 つのケースのいずれかを表す型です: 値、またはまったく何も行われません。</span><span class="sxs-lookup"><span data-stu-id="1f616-193">[The Option Type](language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="1f616-194">値が可能性がありますか、特定の操作からされないことがあるシナリオでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f616-194">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="1f616-195">これによって強制すると、アカウントのどちらの場合も、実行時の問題ではなく、コンパイル時の問題になります。</span><span class="sxs-lookup"><span data-stu-id="1f616-195">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="1f616-196">Api でよく使用されます、`null`について心配する必要があるのでを代わりに、"nothing"を表すため`NullReferenceException`多くの場合。</span><span class="sxs-lookup"><span data-stu-id="1f616-196">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a><span data-ttu-id="1f616-197">測定単位</span><span class="sxs-lookup"><span data-stu-id="1f616-197">Units of Measure</span></span>

<span data-ttu-id="1f616-198"># の型システムの固有の機能の 1 つは、メジャーの単位を数値リテラルのコンテキストを提供する機能です。</span><span class="sxs-lookup"><span data-stu-id="1f616-198">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="1f616-199">[測定単位](language-reference/units-of-measure.md)メートルなどの単位に数値型を関連付けること許可し、関数作業を実行数値リテラルではなく、単位にします。</span><span class="sxs-lookup"><span data-stu-id="1f616-199">[Units of Measure](language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="1f616-200">これにより、コンパイラに渡された数値リテラルの種類を特定のコンテキストでなします、その作業の種類に関連付けられている実行時エラーがなくなることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1f616-200">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

<span data-ttu-id="1f616-201">F# コア ライブラリは、多くの SI 単位の種類と単位の変換を定義します。</span><span class="sxs-lookup"><span data-stu-id="1f616-201">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="1f616-202">詳細については、チェック アウト、 [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="1f616-202">To learn more, check out the [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="1f616-203">クラスとインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f616-203">Classes and Interfaces</span></span>

<span data-ttu-id="1f616-204">F# でも、.NET クラスの完全なサポート[インターフェイス](language-reference/interfaces.md)、[抽象クラス](language-reference/abstract-classes.md)、[継承](language-reference/inheritance.md)のようにします。</span><span class="sxs-lookup"><span data-stu-id="1f616-204">F# also has full support for .NET classes, [Interfaces](language-reference/interfaces.md), [Abstract Classes](language-reference/abstract-classes.md), [Inheritance](language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="1f616-205">[クラス](language-reference/classes.md).NET オブジェクトを表す型が持つことができるプロパティ、メソッド、およびイベントとしてその[メンバー](language-reference/members/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f616-205">[Classes](language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

<span data-ttu-id="1f616-206">ジェネリック クラスの定義も非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="1f616-206">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

<span data-ttu-id="1f616-207">インターフェイスを実装する、いずれかを使用できる`interface ... with`構文または[オブジェクト式](language-reference/object-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f616-207">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a><span data-ttu-id="1f616-208">使用する型</span><span class="sxs-lookup"><span data-stu-id="1f616-208">Which Types to Use</span></span>

<span data-ttu-id="1f616-209">クラス、レコード、判別共用体、および組の存在は、重要な質問につながりますこれを使用しますか?。</span><span class="sxs-lookup"><span data-stu-id="1f616-209">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="1f616-210">ほとんどの環境で、すべてのように、応答は、状況に依存します。</span><span class="sxs-lookup"><span data-stu-id="1f616-210">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="1f616-211">組は、関数から複数の値を返すと自体を値として、アドホック集計値の集計を使用するのに適しています。</span><span class="sxs-lookup"><span data-stu-id="1f616-211">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="1f616-212">レコードは、"からのステップ アップ"組、ラベルと省略可能なメンバーのサポートを持つという名前です。</span><span class="sxs-lookup"><span data-stu-id="1f616-212">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="1f616-213">データ転送中のプログラムの実行の低手続き表現に最適です。</span><span class="sxs-lookup"><span data-stu-id="1f616-213">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="1f616-214">構造の等価性があるため、比較が簡単に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f616-214">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="1f616-215">判別共用体多く、用途がありますが、主要な利点は、すべての可能な「図形」データを持つことができるアカウントに一致するパターンと組み合わせて利用することができます。</span><span class="sxs-lookup"><span data-stu-id="1f616-215">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="1f616-216">クラスは、情報を表すしても機能するには、その情報を関連付ける必要がある場合などの理由の数が膨大に最適です。</span><span class="sxs-lookup"><span data-stu-id="1f616-216">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="1f616-217">原則として、としては、概念的には、一部のデータに関連付けられている機能がある場合は大きな利点にはクラスとオブジェクト指向プログラミングの原則を使用してます。</span><span class="sxs-lookup"><span data-stu-id="1f616-217">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="1f616-218">クラスも推奨されるデータ型 c# と Visual Basic の相互運用時にこれらの言語は、ほぼすべてのクラスを使用。</span><span class="sxs-lookup"><span data-stu-id="1f616-218">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f616-219">次の手順</span><span class="sxs-lookup"><span data-stu-id="1f616-219">Next Steps</span></span>

<span data-ttu-id="1f616-220">これで、言語の主な機能の一部を説明しました、する必要があります、最初の f# プログラムを作成する準備完了!</span><span class="sxs-lookup"><span data-stu-id="1f616-220">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="1f616-221">チェック アウト[作業の開始](tutorials/getting-started/index.md)を開発環境を設定して、コードを記述する方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f616-221">Check out [Getting Started](tutorials/getting-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="1f616-222">お好きなよう、さらに詳しく学習の次の手順を指定できますが、ことをお勧め[ファースト クラス値として機能](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)-->コア関数型プログラミングの概念には慣れてを取得します。</span><span class="sxs-lookup"><span data-stu-id="1f616-222">The next steps for learning more can be whatever you like, but we recommend [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="1f616-223">これらは、f# で堅牢なアプリケーションの構築に不可欠なされます。</span><span class="sxs-lookup"><span data-stu-id="1f616-223">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="1f616-224">また、チェック アウト、 [f# 言語リファレンス](language-reference/index.md)を f# の包括的な概念説明のコレクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f616-224">Also, check out the [F# Language Reference](language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
