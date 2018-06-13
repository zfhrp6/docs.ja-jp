---
title: パラメーターと引数 (F#)
description: パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための f# 言語サポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 319cf0e7346d498ce34e41a9993fe0160038461a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566221"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="f0963-103">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="f0963-103">Parameters and Arguments</span></span>

<span data-ttu-id="f0963-104">このトピックでは、パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための言語サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f0963-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="f0963-105">定義して、可変個の引数を受け取るメソッドを使用する方法と、参照渡しする方法に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f0963-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>


## <a name="parameters-and-arguments"></a><span data-ttu-id="f0963-106">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="f0963-106">Parameters and Arguments</span></span>
<span data-ttu-id="f0963-107">用語*パラメーター*を指定する必要な値の名前を表すために使用します。</span><span class="sxs-lookup"><span data-stu-id="f0963-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="f0963-108">用語*引数*は各パラメーターに指定された値を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0963-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="f0963-109">パラメーターは、組、カリー化形式、または 2 つの組み合わせで指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="f0963-110">明示的なパラメーター名を使用して引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f0963-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="f0963-111">メソッドのパラメーターを省略可能として指定し、既定値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-111">Parameters of methods can be specified as optional and given a default value.</span></span>


## <a name="parameter-patterns"></a><span data-ttu-id="f0963-112">パラメーターのパターン</span><span class="sxs-lookup"><span data-stu-id="f0963-112">Parameter Patterns</span></span>
<span data-ttu-id="f0963-113">関数やメソッドに渡されるパラメーターは一般に、スペースで区切られたパターンです。</span><span class="sxs-lookup"><span data-stu-id="f0963-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="f0963-114">つまり、基本的に、パターンのいずれかの記載[Match 式](match-expressions.md)関数またはメンバーのパラメーター リストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="f0963-115">メソッドは、通常渡す引数のタプルの形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f0963-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="f0963-116">これの処理タプルの形式に一致する .NET メソッドに引数が渡される方法は他の .NET 言語の観点から明確結果。</span><span class="sxs-lookup"><span data-stu-id="f0963-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="f0963-117">カリー化されたフォームを使用して作成した関数で最もよく使用される`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="f0963-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="f0963-118">次の疑似コードは、組、カリー化された引数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="f0963-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="f0963-119">組にいくつかの引数があり、いくつかの場合は、形式を組み合わせています。</span><span class="sxs-lookup"><span data-stu-id="f0963-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="f0963-120">他のパターンは、パラメーター リストにも使用できますが、パラメーターのパターンが可能なすべての入力が一致しない場合があります不完全な一致実行時にします。</span><span class="sxs-lookup"><span data-stu-id="f0963-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="f0963-121">例外`MatchFailureException`引数の値がパラメーター リストで指定されたパターンと一致しない場合に生成します。</span><span class="sxs-lookup"><span data-stu-id="f0963-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="f0963-122">不完全な一致では、パラメーターのパターンと、コンパイラは警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="f0963-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="f0963-123">他には、少なくとも 1 つのパターンが一般的に、パラメーター リストに便利ですし、ワイルドカード パターンがします。</span><span class="sxs-lookup"><span data-stu-id="f0963-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="f0963-124">提供されている引数を無視したいときに、パラメーター リストでワイルドカード パターンを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="f0963-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="f0963-125">次のコードでは、引数リスト内のワイルドカード パターンの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="f0963-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="f0963-126">ワイルドカード パターンでは、不要なコマンドラインの引数は通常、次のコードと同様に、文字列の配列として提供されているときに、使用するプログラムへのメイン エントリ ポイントなど、渡された引数を必要としないときに便利です。 を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="f0963-127">引数でときどき使われるその他のパターンは、`as`パターン、および判別共用体、およびアクティブ パターンに関連付けられている識別子パターン。</span><span class="sxs-lookup"><span data-stu-id="f0963-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="f0963-128">単一ケースの判別共用体パターンは次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="f0963-129">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f0963-129">The output is as follows.</span></span>

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="f0963-130">アクティブ パターンは、引数を次の例のように、目的の形式に変換するときに、たとえば、パラメーターとして役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f0963-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="f0963-131">使用することができます、`as`次のコード行に示すように、ローカルの値として照合する値を格納するパターン。</span><span class="sxs-lookup"><span data-stu-id="f0963-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="f0963-132">使用されることがある別のパターンは、関数の本文として提供して、名前のない最後の引数のままにする関数、暗黙の型引数をすぐにパターン マッチを実行する、ラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="f0963-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="f0963-133">この例では、次のコード行がします。</span><span class="sxs-lookup"><span data-stu-id="f0963-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="f0963-134">このコードをジェネリック リストを受け取りを返す関数定義`true`リストが空の場合と`false`それ以外の場合。</span><span class="sxs-lookup"><span data-stu-id="f0963-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="f0963-135">このような手法を使用すると、コードが読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="f0963-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="f0963-136">場合によっては、不完全な一致を伴うパターンは、役立ちます。 など、プログラムの一覧が 3 つだけの要素を持つことがわかっている場合がありますパターンを使用する、次のようにパラメーター リスト内です。</span><span class="sxs-lookup"><span data-stu-id="f0963-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="f0963-137">不完全な一致パターンの使用は、クイック プロトタイプの作成とその他の一時的な使用に最適な予約されています。</span><span class="sxs-lookup"><span data-stu-id="f0963-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="f0963-138">コンパイラでは、このようなコードの警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="f0963-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="f0963-139">このようなパターンでは、すべての可能な入力の一般的なケースを対応することはできませんし、したがってはコンポーネント Api には向いていません。</span><span class="sxs-lookup"><span data-stu-id="f0963-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="f0963-140">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="f0963-140">Named Arguments</span></span>
<span data-ttu-id="f0963-141">メソッドの引数は、引数のコンマ区切りリストを内の位置で指定できます。 または渡すことができるメソッドを明示的に等号 (=) とで渡される値の後に、名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0963-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="f0963-142">名前を提供することで指定した場合は、宣言で使用されているとは異なる順序で表示ことができます。</span><span class="sxs-lookup"><span data-stu-id="f0963-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="f0963-143">名前付き引数、コード読みやすくし、適応性がより API では、メソッドのパラメーターの順序変更などの変更の特定の種類になります。</span><span class="sxs-lookup"><span data-stu-id="f0963-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="f0963-144">名前付き引数がなく、メソッドに対してのみ許可されます`let`-関数、関数の値、またはラムダ式を連結します。</span><span class="sxs-lookup"><span data-stu-id="f0963-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="f0963-145">次のコード例では、名前付き引数の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="f0963-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="f0963-146">クラスのコンス トラクターの呼び出しでは、名前付き引数に似た構文を使用して、クラスのプロパティの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="f0963-147">次の例は、この構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="f0963-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="f0963-148">詳細については、次を参照してください。[コンス トラクター (f#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)です。</span><span class="sxs-lookup"><span data-stu-id="f0963-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="f0963-149">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="f0963-149">Optional Parameters</span></span>
<span data-ttu-id="f0963-150">パラメーター名の前に疑問符 () を使用して、メソッドのオプション パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="f0963-151">省略可能なパラメーターが、f# オプションの種類として解釈されるを使用して、オプションの種類がクエリを通常の方法で照会できますので、`match`を持つ式`Some`と`None`です。</span><span class="sxs-lookup"><span data-stu-id="f0963-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="f0963-152">省略可能なパラメーターを使用して作成した関数ではなく、メンバーでのみ許可`let`バインドします。</span><span class="sxs-lookup"><span data-stu-id="f0963-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="f0963-153">関数を使用することもできます。 `defaultArg`、省略可能な引数の既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f0963-153">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="f0963-154">`defaultArg`関数は、最初の引数と省略可能なパラメーターと、既定値、2 つ目として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f0963-154">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="f0963-155">次の例では、省略可能なパラメーターの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="f0963-155">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="f0963-156">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f0963-156">The output is as follows.</span></span>

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a><span data-ttu-id="f0963-157">参照を渡し</span><span class="sxs-lookup"><span data-stu-id="f0963-157">Passing by Reference</span></span>
<span data-ttu-id="f0963-158">F# でサポートする、`byref`キーワードで、参照渡しでパラメーターを渡すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0963-158">F# supports the `byref` keyword, which specifies that a parameter is passed by reference.</span></span> <span data-ttu-id="f0963-159">つまり、関数の実行後の値に変更が保持されます。</span><span class="sxs-lookup"><span data-stu-id="f0963-159">This means that any changes to the value are retained after the execution of the function.</span></span> <span data-ttu-id="f0963-160">に対して指定した値、`byref`パラメーターを変更可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0963-160">Values provided to a `byref` parameter must be mutable.</span></span> <span data-ttu-id="f0963-161">また、適切な種類の参照セルを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f0963-161">Alternatively, you can pass reference cells of the appropriate type.</span></span>

<span data-ttu-id="f0963-162">関数から 1 つ以上の値を返す方法として発展 .NET 言語での参照渡しです。</span><span class="sxs-lookup"><span data-stu-id="f0963-162">Passing by reference in .NET languages evolved as a way to return more than one value from a function.</span></span> <span data-ttu-id="f0963-163">F# では、この目的で組を返すまたは、変更可能な参照セルをパラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-163">In F#, you can return a tuple for this purpose, or use a mutable reference cell as a parameter.</span></span> <span data-ttu-id="f0963-164">`byref` .NET ライブラリとの相互運用のパラメーターが提供される主にします。</span><span class="sxs-lookup"><span data-stu-id="f0963-164">The `byref` parameter is mainly provided for interoperability with .NET libraries.</span></span>

<span data-ttu-id="f0963-165">次の例では、使用、`byref`キーワード。</span><span class="sxs-lookup"><span data-stu-id="f0963-165">The following examples illustrate the use of the `byref` keyword.</span></span> <span data-ttu-id="f0963-166">参照セルをパラメーターとして使用するときにする必要があります名前付きの値として参照セルを作成して、パラメーターとして使用するは、追加だけでなく、`ref`演算子の最初の呼び出しに示すよう`Increment`次のコードにします。</span><span class="sxs-lookup"><span data-stu-id="f0963-166">Note that when you use a reference cell as a parameter, you must create a reference cell as a named value and use that as the parameter, not just add the `ref` operator as shown in the first call to `Increment` in the following code.</span></span> <span data-ttu-id="f0963-167">参照セルを作成する基になる値のコピーを作成するための最初の呼び出しは一時的な値だけインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="f0963-167">Because creating a reference cell creates a copy of the underlying value, the first call just increments a temporary value.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

<span data-ttu-id="f0963-168">戻り値として組を使用して格納できる`out`.NET ライブラリのメソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="f0963-168">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="f0963-169">または、扱うことのできる、`out`パラメーターとして、`byref`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f0963-169">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="f0963-170">次のコード例では、両方の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f0963-170">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="f0963-171">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="f0963-171">Parameter Arrays</span></span>
<span data-ttu-id="f0963-172">場合によっては異機種混在型のパラメーターの任意の数を取得する関数を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0963-172">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="f0963-173">これは実用的ではないために使用できるすべての型のために可能なすべてのオーバー ロードされたメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0963-173">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="f0963-174">.NET の実装では、パラメーター配列の機能によってこのようなメソッドのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f0963-174">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="f0963-175">任意の数のパラメーターでは、そのシグニチャに、パラメーター配列を受け取るメソッドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-175">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="f0963-176">パラメーターは、配列に配置されています。</span><span class="sxs-lookup"><span data-stu-id="f0963-176">The parameters are put into an array.</span></span> <span data-ttu-id="f0963-177">配列の要素の型では、関数に渡すことができるパラメーターの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="f0963-177">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="f0963-178">場合は、パラメーター配列を定義する`System.Object`要素型として、クライアント コード値渡すことが任意の型。</span><span class="sxs-lookup"><span data-stu-id="f0963-178">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="f0963-179">F# で、パラメーター配列は、メソッドでのみ定義します。</span><span class="sxs-lookup"><span data-stu-id="f0963-179">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="f0963-180">スタンドアロン関数またはモジュールで定義されている関数では、それらを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f0963-180">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="f0963-181">使用して、パラメーター配列を定義する、`ParamArray`属性。</span><span class="sxs-lookup"><span data-stu-id="f0963-181">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="f0963-182">`ParamArray`属性は、最後のパラメーターにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="f0963-182">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="f0963-183">次のコードは、両方とを受け取り、パラメーター配列の種類の定義をパラメーター配列を受け取るメソッドが f# の .NET メソッドの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="f0963-183">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="f0963-184">プロジェクト内で実行するときに、前のコードの出力のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f0963-184">When run in a project, the output of the previous code is as follows:</span></span>

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="f0963-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0963-185">See Also</span></span>
[<span data-ttu-id="f0963-186">メンバー</span><span class="sxs-lookup"><span data-stu-id="f0963-186">Members</span></span>](members/index.md)
