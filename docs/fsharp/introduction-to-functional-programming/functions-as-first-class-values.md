---
title: ファースト クラスの値としての関数 (F#)
description: 関数は、f# のプログラミング言語のファースト クラスのステータスに昇格する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: cccff5fcf9de150da26422f80cae032ddf21014c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566666"
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="2bff3-103">ファースト クラスの値としての関数</span><span class="sxs-lookup"><span data-stu-id="2bff3-103">Functions as First-Class Values</span></span>

<span data-ttu-id="2bff3-104">関数型プログラミング言語の最も大きな特徴は、関数がファースト クラスのステータスに昇格することです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="2bff3-105">他の組み込み型の値で実行できる処理はすべて、同等の手間で、関数を使用して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="2bff3-106">ファースト クラスのステータスの標準的な基準は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="2bff3-107">識別子に関数をバインドすることができますか。</span><span class="sxs-lookup"><span data-stu-id="2bff3-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="2bff3-108">つまり、でく名前を付けますか。</span><span class="sxs-lookup"><span data-stu-id="2bff3-108">That is, can you give them names?</span></span>

- <span data-ttu-id="2bff3-109">格納できるデータ構造内の関数など、リスト内</span><span class="sxs-lookup"><span data-stu-id="2bff3-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="2bff3-110">関数を関数呼び出しの引数として渡すことができますか。</span><span class="sxs-lookup"><span data-stu-id="2bff3-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="2bff3-111">関数呼び出しから関数を返すことができますか。</span><span class="sxs-lookup"><span data-stu-id="2bff3-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="2bff3-112">最後の 2 つのメジャーを定義として知られる仕組み*高階演算*または*高階関数*です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="2bff3-113">高階関数は、引数として関数を受け取り、関数呼び出しの結果値として関数を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="2bff3-114">これらの処理によって、関数型プログラミングの中心となる、関数のマッピングや関数の合成などの機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="2bff3-115">値に名前を付ける</span><span class="sxs-lookup"><span data-stu-id="2bff3-115">Give the Value a Name</span></span>

<span data-ttu-id="2bff3-116">関数がファースト クラスの値である場合は、整数や文字列、その他の組み込みの型に名前を付けることができるのと同様に、関数に名前を付けることができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="2bff3-117">関数型プログラミングの記述では、これを "値に識別子を束縛する" と表現しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="2bff3-118">F# は[`let`バインド](../language-reference/functions/let-bindings.md)値に名前をバインド:`let <identifier> = <value>`です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="2bff3-119">次に、2 つのコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="2bff3-120">関数には簡単に名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-120">You can name a function just as easily.</span></span> <span data-ttu-id="2bff3-121">次の例は、という名前の関数を定義`squareIt`識別子をバインドして`squareIt`を[ラムダ式](../language-reference/functions/lambda-expressions-the-fun-keyword.md)`fun n -> n * n`です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="2bff3-122">関数 `squareIt` は、1 つのパラメーター `n` を受け取り、このパラメーターの 2 乗を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="2bff3-123">F# では、次に示すより簡潔な構文が用意されており、少量の入力で同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="2bff3-124">以降の例では、関数の宣言と他の型の値の宣言の類似性を強調するために、ほとんどの場合に最初の `let <function-name> = <lambda-expression>` というスタイルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="2bff3-125">ただし、名前付き関数はすべて、簡潔な構文で記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="2bff3-126">一部の例では、両方の方法を使用して記述しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-126">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="2bff3-127">値をデータ構造に格納する</span><span class="sxs-lookup"><span data-stu-id="2bff3-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="2bff3-128">ファースト クラスの値はデータ構造に格納できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="2bff3-129">次のコード例では、リストとタプルに値を格納する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="2bff3-130">タプルに格納された関数名が実際に関数として評価されることを確認するために、次の例では、`fst` 演算子と `snd` 演算子を使用して、`funAndArgTuple` タプルから 1 番目の要素と 2 番目の要素を抽出します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="2bff3-131">タプルの 1 番目の要素は `squareIt`、2 番目の要素は `num` です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="2bff3-132">識別子 `num` は、前の例で整数 10 にバインドされています。これは、`squareIt` 関数の有効な引数です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="2bff3-133">2 番目の式は、タプルの 1 番目の要素をタプルの 2 番目の要素に適用します。つまり、`squareIt num` となります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="2bff3-134">識別子 `num` と整数 10 を入れ替えて使用できるのと同様に、識別子 `squareIt` とラムダ式 `fun n -> n * n` も入れ替えて使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="2bff3-135">値を引数として渡す</span><span class="sxs-lookup"><span data-stu-id="2bff3-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="2bff3-136">値が言語内でファースト クラスのステータスを持つ場合、その値は関数に引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="2bff3-137">たとえば、整数や文字列を引数として渡すのは一般的です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="2bff3-138">次のコードは、F# で引数として渡される整数や文字列を示しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="2bff3-139">関数がファースト クラスのステータスを持つ場合は、同様の方法で関数を引数として渡すことができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="2bff3-140">これは高階関数の 1 番目の特性です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="2bff3-141">次の例で、`applyIt` 関数は 2 つのパラメーター `op` と `arg` を持っています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="2bff3-142">1 つのパラメーターを持つ関数を `op` に指定し、その関数の適切な引数を `arg` に渡すと、`op` を `arg` に適用した結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="2bff3-143">次の例では、関数の引数と整数の引数の両方が、同じように名前を使用して渡されています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="2bff3-144">関数を引数として他の関数に送信できる機能は、マップ操作やフィルター操作など、関数型プログラミング言語に共通の抽象化が基礎になっています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="2bff3-145">たとえば、マップ操作は、複数の関数で共有される計算を引き受ける高階関数であり、リストを走査し、各要素に対してなんらかの処理を実行し、結果のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="2bff3-146">整数のリストの各要素をインクリメントしたり、各要素を 2 乗したり、文字列のリストの各要素を大文字に変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="2bff3-147">計算のエラーが発生しやすい部分は、リストを走査し、返す結果のリストを構築する再帰プロセスです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="2bff3-148">この部分はマッピング関数に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="2bff3-149">特定のアプリケーションで記述する必要があるのは、各リスト要素に個別に適用する関数 (加算、2 乗、大文字と小文字の変更) だけです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="2bff3-150">その関数は、前の例で `squareIt` が `applyIt` に渡されたように、マッピング関数への引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="2bff3-151">F# など、ほとんどのコレクション型のマップのメソッドを提供する[一覧](../language-reference/lists.md)、[配列](../language-reference/arrays.md)、および[シーケンス](../language-reference/sequences.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="2bff3-152">次の例では、リストを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-152">The following examples use lists.</span></span> <span data-ttu-id="2bff3-153">構文は `List.map <the function> <the list>` です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="2bff3-154">詳細については、次を参照してください。[一覧](../language-reference/lists.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="2bff3-155">関数呼び出しの結果値を返す</span><span class="sxs-lookup"><span data-stu-id="2bff3-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="2bff3-156">最後に、関数が言語内でファースト クラスのステータスを持つ場合は、整数や文字列などの型を返す場合と同様に、その関数を関数呼び出しの結果値として返すことができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="2bff3-157">次の関数呼び出しでは、整数を返してそれらを表示します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="2bff3-158">次の関数呼び出しでは、文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="2bff3-159">次の関数呼び出しはインラインで宣言されており、ブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="2bff3-160">表示される値は `True` です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="2bff3-161">関数呼び出しの結果値として関数を返すことができるのは、高階関数のもう 1 つの特徴です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="2bff3-162">次の例では、1 つの引数 `checkFor` を受け取り、結果値として新しい関数を返す `item` という関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="2bff3-163">返された関数は、引数 `lst` としてリストを受け取り、その `item` 内で `lst` を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="2bff3-164">`item` が存在する場合、関数は `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="2bff3-165">`item` がない場合、関数は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="2bff3-166">前のセクションと同様に、次のコードで使用する、指定されたリスト関数[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)一覧を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-166">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="2bff3-167">次のコードでは、`checkFor` を使用して新しい関数を作成します。作成された関数は、1 つの引数としてリストを受け取り、そのリストから 7 を検索します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="2bff3-168">次の例では、F# における関数のファースト クラスのステータスを使用して、2 つの関数の引数の合成を返す `compose` 関数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="2bff3-169">さらに短いコードについては、次の「カリー化関数」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bff3-169">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="2bff3-170">次のコードでは、2 つの関数を `compose` の引数として渡します。どちらの関数も、同じ型の 1 つの引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="2bff3-171">戻り値は、この 2 つの関数の引数の合成である新しい関数です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="2bff3-172">F# には、関数を合成する演算子として、`<<` と `>>` の 2 つが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="2bff3-173">たとえば、`let squareAndDouble2 = doubleIt << squareIt` は、前の例の `let squareAndDouble = compose doubleIt squareIt` と同じです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="2bff3-174">次に、関数呼び出しの結果値として関数を返し、単純な推測ゲームを作成する例を示します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="2bff3-175">ゲームを作成するには、他者に推測してもらう値を `makeGame` に渡して `target` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="2bff3-176">`makeGame` 関数からの戻り値は、1 つの引数 (推測) を受け取ってその推測が正しいかどうかを報告する関数です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="2bff3-177">次のコードでは、`makeGame` に値 `7` を渡して `target` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="2bff3-178">識別子 `playGame` には、返されたラムダ式がバインドされます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="2bff3-179">したがって、`playGame` は、`guess` の値を 1 つの引数として受け取る関数になります。</span><span class="sxs-lookup"><span data-stu-id="2bff3-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="2bff3-180">カリー化関数</span><span class="sxs-lookup"><span data-stu-id="2bff3-180">Curried Functions</span></span>

<span data-ttu-id="2bff3-181">前のセクションの例の多くを書き込むより簡潔活用して、暗黙的な*カリー化*f# 関数宣言でします。</span><span class="sxs-lookup"><span data-stu-id="2bff3-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="2bff3-182">カリー化とは、複数のパラメーターを持つ関数を、それぞれが単一のパラメーターを持つ一連の埋め込み関数に変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="2bff3-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="2bff3-183">F# では、複数のパラメーターを持つ関数は本質的にカリー化されます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="2bff3-184">たとえば、前のセクションの `compose` は、次に示すように、3 つのパラメーターを使用する簡潔なスタイルで記述できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="2bff3-185">ただし、`compose4curried` に示すように、この結果は 1 つのパラメーターを持つ関数で、その関数もパラメーターが 1 つの関数を返し、さらにその関数も、パラメーターが 1 つの別の関数を返します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="2bff3-186">この関数は、いくつかの方法で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-186">You can access this function in several ways.</span></span> <span data-ttu-id="2bff3-187">次のそれぞれの例は、18 を返して表示します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="2bff3-188">どの例でも、`compose4` を `compose4curried` に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="2bff3-189">置き換える前と同じように関数が機能することを確認するには、元のテスト ケースをもう一度試します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="2bff3-190">パラメーターをタプルとして囲むことで、カリー化を制限できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="2bff3-191">詳細についてを参照してください「パラメーターのパターン」[パラメーターと引数](../language-reference/parameters-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="2bff3-192">次の例では、暗黙的なカリー化を使用して、より短いバージョンの `makeGame` を作成します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="2bff3-193">この形式では、`makeGame` が `game` 関数を作成して返す方法の詳細はそれほど明確ではありませんが、同じ結果を返す元のテスト ケースを使用することで確認できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="2bff3-194">カリー化の詳細についてを参照してください「部分的なアプリケーションの引数」[関数](../language-reference/functions/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="2bff3-195">識別子と関数定義の交換可能性</span><span class="sxs-lookup"><span data-stu-id="2bff3-195">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="2bff3-196">前に示した例において、変数名 `num` は整数 10 に評価されます。したがって、`num` が有効な場所では、当然ながら 10 も有効です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="2bff3-197">関数識別子とその値にも、同じことが当てはまります。つまり、関数名を使用できる場所では、その名前にバインドされているラムダ式も使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="2bff3-198">次の例では、`Boolean` と呼ばれる `isNegative` 関数を定義し、この関数の名前と関数の定義を同じように使用します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="2bff3-199">次の 3 つの例は、すべて `False` を返して表示します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="2bff3-200">もう 1 歩進めて、`applyIt` にバインドされている値を `applyIt` の代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="2bff3-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="2bff3-201">F# におけるファースト クラスの値としての関数</span><span class="sxs-lookup"><span data-stu-id="2bff3-201">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="2bff3-202">前のセクションの各例は、F# の関数が、ファースト クラスの値であるための基準を満たしていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="2bff3-203">関数定義に識別子をバインドできます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="2bff3-204">関数をデータ構造に格納できます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="2bff3-205">関数を引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="2bff3-206">関数を関数呼び出しの結果値として返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2bff3-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="2bff3-207">F# の詳細については、次を参照してください。、 [f# 言語リファレンス](../language-reference/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bff3-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="2bff3-208">例</span><span class="sxs-lookup"><span data-stu-id="2bff3-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="2bff3-209">説明</span><span class="sxs-lookup"><span data-stu-id="2bff3-209">Description</span></span>

<span data-ttu-id="2bff3-210">次のコードには、このトピックのすべての例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2bff3-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="2bff3-211">コード</span><span class="sxs-lookup"><span data-stu-id="2bff3-211">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="2bff3-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bff3-212">See Also</span></span>

[<span data-ttu-id="2bff3-213">リスト</span><span class="sxs-lookup"><span data-stu-id="2bff3-213">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="2bff3-214">タプル</span><span class="sxs-lookup"><span data-stu-id="2bff3-214">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="2bff3-215">関数</span><span class="sxs-lookup"><span data-stu-id="2bff3-215">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="2bff3-216">`let` バインド</span><span class="sxs-lookup"><span data-stu-id="2bff3-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="2bff3-217">ラムダ式:`fun`キーワード</span><span class="sxs-lookup"><span data-stu-id="2bff3-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
