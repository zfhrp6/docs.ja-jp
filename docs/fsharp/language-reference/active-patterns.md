---
title: アクティブ パターン (F#)
description: アクティブ パターンを使用して、f# のプログラミング言語で入力データを分割する名前付きのパーティションを定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="active-patterns"></a><span data-ttu-id="37d30-103">アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="37d30-103">Active Patterns</span></span>

<span data-ttu-id="37d30-104">*アクティブ パターン*パターン一致式の判別共用体の場合と同様に、これらの名前を使用できるように、入力のデータを分割する名前付きパーティションを定義できるようにします。</span><span class="sxs-lookup"><span data-stu-id="37d30-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="37d30-105">アクティブ パターンを使用すると、パーティションごとにカスタマイズした方法でデータを分解できます。</span><span class="sxs-lookup"><span data-stu-id="37d30-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>


## <a name="syntax"></a><span data-ttu-id="37d30-106">構文</span><span class="sxs-lookup"><span data-stu-id="37d30-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="37d30-107">コメント</span><span class="sxs-lookup"><span data-stu-id="37d30-107">Remarks</span></span>
<span data-ttu-id="37d30-108">前の構文では、識別子で表される入力データのパーティションの名*引数*、または、つまり、他の名前、引数のすべての値のセットのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="37d30-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="37d30-109">アクティブ パターン定義では最大 7 つのパーティションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="37d30-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="37d30-110">*式*データを分解するには、フォームをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="37d30-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="37d30-111">アクティブ パターン定義を使用すると、判断するための名前付きのパーティションに属している引数として提供された値の規則を定義します。</span><span class="sxs-lookup"><span data-stu-id="37d30-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="37d30-112">(| と |) のシンボルをいいます*バナナ クリップ*この型の使用すると、バインディングによって作成された関数が呼び出されると、*アクティブ レコグナイザー*です。</span><span class="sxs-lookup"><span data-stu-id="37d30-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="37d30-113">たとえば、引数を指定して、次のアクティブなパターンを検討してください。</span><span class="sxs-lookup"><span data-stu-id="37d30-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="37d30-114">次の例のように、式と一致するパターンでは、アクティブ パターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="37d30-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="37d30-115">このプログラムの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="37d30-116">アクティブ パターンの別の使用は、同じ基になるデータがさまざまな可能な表現が場合など、いくつかの方法でデータ型を分解するためです。</span><span class="sxs-lookup"><span data-stu-id="37d30-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="37d30-117">たとえば、 `Color` RGB 表現または HSB 表現にオブジェクトを分解する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="37d30-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="37d30-118">上のプログラムの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-118">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="37d30-119">組み合わせで、アクティブなパターンを使用してこれら 2 つの方法を有効にするパーティションにデータを適切なフォームだけに分解し、計算のため最も便利な形式で、適切なデータに対して適切な計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="37d30-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="37d30-120">結果として得られるパターン一致式では、非常に判読できる、大幅に簡素化する可能性のある複雑な分岐構造やデータ分析のコードは、便利な方法で書き込むデータを有効にします。</span><span class="sxs-lookup"><span data-stu-id="37d30-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>


## <a name="partial-active-patterns"></a><span data-ttu-id="37d30-121">パーシャル アクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="37d30-121">Partial Active Patterns</span></span>
<span data-ttu-id="37d30-122">場合によっては、入力領域の一部だけを分割する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37d30-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="37d30-123">その場合は、いくつかの入力に一致は他の入力が一致しなくなるの部分のパターンのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="37d30-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="37d30-124">常に、値を生成しないアクティブ パターンと呼びます*パーシャル アクティブ パターン*; オプションの種類である戻り値があります。</span><span class="sxs-lookup"><span data-stu-id="37d30-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="37d30-125">部分的なアクティブ パターンを定義するのには、バナナ クリップ内のパターンの一覧の最後にワイルドカード文字 (_) を使用します。</span><span class="sxs-lookup"><span data-stu-id="37d30-125">To define a partial active pattern, you use a wildcard character (_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="37d30-126">次のコードでは、部分的なアクティブ パターンの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="37d30-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="37d30-127">前の例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="37d30-128">パーシャル アクティブ パターンを使用して、個々 の選択肢もあります不整合または相互に排他的なが必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37d30-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="37d30-129">次の例では、パターン四角形パターン キューブのでとは、不整合のあるいくつかの番号は、四角形、64 などのキューブの両方です。</span><span class="sxs-lookup"><span data-stu-id="37d30-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="37d30-130">次のプログラムは、すべての整数が 1000000 までは、四角形およびキューブの両方を印刷します。</span><span class="sxs-lookup"><span data-stu-id="37d30-130">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="37d30-131">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-131">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="37d30-132">パラメーター化されたアクティブ パターン</span><span class="sxs-lookup"><span data-stu-id="37d30-132">Parameterized Active Patterns</span></span>
<span data-ttu-id="37d30-133">アクティブ パターンが常に一致する項目の少なくとも 1 つの引数を受け取りますが、名前で同様に、追加の引数がかかる*パラメーター化されたアクティブ パターン*適用されます。</span><span class="sxs-lookup"><span data-stu-id="37d30-133">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="37d30-134">追加の引数には、一般的なパターンを特化することができるようにします。</span><span class="sxs-lookup"><span data-stu-id="37d30-134">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="37d30-135">たとえば、文字列を解析する多くの場合、正規表現を使用してアクティブ パターンが部分的なアクティブ パターンを使用する次のコードのように、余分なパラメーターとして、正規表現を含める`Integer`上記のコード例で定義されています。</span><span class="sxs-lookup"><span data-stu-id="37d30-135">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="37d30-136">この例では、[全般] である ParseRegex アクティブ パターンをカスタマイズするさまざまな日付形式の正規表現を使用する文字列が与えられます。</span><span class="sxs-lookup"><span data-stu-id="37d30-136">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="37d30-137">整数アクティブ パターンが一致した文字列を DateTime コンス トラクターに渡すことができる整数に変換するために使用します。</span><span class="sxs-lookup"><span data-stu-id="37d30-137">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="37d30-138">前のコードの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-138">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="37d30-139">アクティブなパターンは、パターン一致式のみに限定することはありません、let バインディングで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="37d30-139">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="37d30-140">前のコードの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37d30-140">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="37d30-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="37d30-141">See Also</span></span>
[<span data-ttu-id="37d30-142">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="37d30-142">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="37d30-143">match 式</span><span class="sxs-lookup"><span data-stu-id="37d30-143">Match Expressions</span></span>](match-expressions.md)

