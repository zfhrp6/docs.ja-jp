---
title: "自動ジェネリック化 (F#)"
description: "どの F# で自動的に一般化引数および関数の型が可能であれば、複数の型を操作できるように説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 14a3554c-3fad-4eba-a93d-8ba07d1245b4
ms.openlocfilehash: d60831084cef76ce29f64322362b4920520f71d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-generalization"></a><span data-ttu-id="b5973-104">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="b5973-104">Automatic Generalization</span></span>

<span data-ttu-id="b5973-105">F# の関数よぶ式の種類を評価するのに型の推定を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5973-105">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="b5973-106">このトピックでは、どの F# で自動的に一般化引数と型の関数の可能な限り、複数の型を動作させることについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b5973-106">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="b5973-107">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="b5973-107">Automatic Generalization</span></span>
<span data-ttu-id="b5973-108">F# コンパイラ、関数の型の推論を実行するときに、指定されたパラメーターがジェネリックできるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b5973-108">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="b5973-109">コンパイラは、各パラメーターを調べし、関数は、そのパラメーターの特定の種類に依存しているかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b5973-109">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="b5973-110">そうでない場合は、ジェネリックにする型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="b5973-110">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="b5973-111">次のコード例は、ジェネリックにするに基づいてコンパイラが推定する関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5973-111">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="b5973-112">ある型を推論`'a -> 'a -> 'a`です。</span><span class="sxs-lookup"><span data-stu-id="b5973-112">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="b5973-113">種類は、同じの不明な型の 2 つの引数を受け取りを同じ型の値を返します関数であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b5973-113">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="b5973-114">前の関数である理由のいずれかのジェネリックは、大きい-演算子よりも (`>`) 自体はジェネリックではします。</span><span class="sxs-lookup"><span data-stu-id="b5973-114">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="b5973-115">大きい-シグネチャを持つ演算子よりも`'a -> 'a -> bool`します。</span><span class="sxs-lookup"><span data-stu-id="b5973-115">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="b5973-116">ジェネリックではできない演算子もし、そのパラメーターの型を一般化することはできません、関数のコードでは、非ジェネリック関数または演算子と共にパラメーターの型を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="b5973-116">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="b5973-117">`max`はジェネリックを使用できますの種類など`int`、`float`というように、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b5973-117">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="b5973-118">ただし、2 つの引数は、同じ種類のする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5973-118">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="b5973-119">署名が`'a -> 'a -> 'a`ではなく、`'a -> 'b -> 'a`です。</span><span class="sxs-lookup"><span data-stu-id="b5973-119">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="b5973-120">したがって、次のコードは、型が一致しないために、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b5973-120">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="b5973-121">`max`使用することも、大きい値をサポートする任意の型の演算子よりもします。</span><span class="sxs-lookup"><span data-stu-id="b5973-121">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="b5973-122">そのため、使用することもに、文字列で、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b5973-122">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="b5973-123">値制限</span><span class="sxs-lookup"><span data-stu-id="b5973-123">Value Restriction</span></span>
<span data-ttu-id="b5973-124">コンパイラは、明示的な引数を持ち、完全な関数定義でのみ、単純な変更できない値に自動ジェネリック化を実行します。</span><span class="sxs-lookup"><span data-stu-id="b5973-124">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="b5973-125">つまり、コンパイラ エラーが発生すると、特定の型であることを十分に制約を受けないがもない汎化可能なコードをコンパイルしようとする場合。</span><span class="sxs-lookup"><span data-stu-id="b5973-125">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="b5973-126">この問題は、エラー メッセージが値としての自動ジェネリック化では、この制限を指す、*値制限*です。</span><span class="sxs-lookup"><span data-stu-id="b5973-126">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="b5973-127">通常、ジェネリックにする構成要素、その場合、コンパイラが不十分な情報を一般化し、か、または意図せずに、非ジェネリック コンストラクトのための十分な種類の情報を省略した場合に、値制限エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b5973-127">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="b5973-128">値制限エラーの解決策は、複数の完全で、次の方法のいずれかの型の推論の問題を制限する詳細な情報についてを提供することです。</span><span class="sxs-lookup"><span data-stu-id="b5973-128">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="b5973-129">値またはパラメーターに、明示的な型の注釈を追加することで非ジェネリックである型を制限します。</span><span class="sxs-lookup"><span data-stu-id="b5973-129">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="b5973-130">問題が使用されている場合、関数の合成など、または不完全なジェネリック関数を定義する、汎化できない構成コンストラクトに適用されるカリー化関数の引数を通常の関数定義として関数を書き直してください。</span><span class="sxs-lookup"><span data-stu-id="b5973-130">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="b5973-131">問題が複雑すぎるため、汎用化では式の場合は、なります関数に、未使用のパラメーターを追加することによってです。</span><span class="sxs-lookup"><span data-stu-id="b5973-131">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="b5973-132">明示的なジェネリック型パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5973-132">Add explicit generic type parameters.</span></span> <span data-ttu-id="b5973-133">このオプションはほとんど使用されません。</span><span class="sxs-lookup"><span data-stu-id="b5973-133">This option is rarely used.</span></span>

- <span data-ttu-id="b5973-134">次のコード例では、これらの各シナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="b5973-134">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="b5973-135">ケース 1: 式が複雑すぎます。</span><span class="sxs-lookup"><span data-stu-id="b5973-135">Case 1: Too complex an expression.</span></span> <span data-ttu-id="b5973-136">この例では、一覧で`counter`するものでは`int option ref`、単純な変更できない値が定義されていませんが、します。</span><span class="sxs-lookup"><span data-stu-id="b5973-136">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="b5973-137">ケース 2: では、汎化できない構成要素を使用して、ジェネリック関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="b5973-137">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="b5973-138">この例では、構造は、関数の引数の部分的な適用が伴うので汎化できない構成がします。</span><span class="sxs-lookup"><span data-stu-id="b5973-138">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="b5973-139">ケース 3: は、未使用のパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5973-139">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="b5973-140">この式が汎化のほど単純でないため、コンパイラは、値の制限のエラーを発行します。</span><span class="sxs-lookup"><span data-stu-id="b5973-140">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="b5973-141">ケース 4: 型パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5973-141">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="b5973-142">最後の場合、値には型関数の場合、次のようになど多くのさまざまな種類の値を作成するために使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b5973-142">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="b5973-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5973-143">See Also</span></span>
[<span data-ttu-id="b5973-144">型推論</span><span class="sxs-lookup"><span data-stu-id="b5973-144">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="b5973-145">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="b5973-145">Generics</span></span>](index.md)

[<span data-ttu-id="b5973-146">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5973-146">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="b5973-147">制約</span><span class="sxs-lookup"><span data-stu-id="b5973-147">Constraints</span></span>](constraints.md)

