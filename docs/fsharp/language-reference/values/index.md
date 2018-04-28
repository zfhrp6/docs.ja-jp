---
title: 値 (F#)
description: F# の値の特定の種類の数量の方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b40e4a0409a9161a4ef48c8d4ad82b4da346538e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="values"></a><span data-ttu-id="77fe7-103">値</span><span class="sxs-lookup"><span data-stu-id="77fe7-103">Values</span></span>

<span data-ttu-id="77fe7-104">F# の値は、特定の型を持つ数量です。値は、整数または浮動小数点数、文字またはテキスト、リスト、シーケンス、配列、タプル、判別共用体、レコード、クラス型、関数値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="77fe7-104">Values in F# are quantities that have a specific type; values can be integral or floating point numbers, characters or text, lists, sequences, arrays, tuples, discriminated unions, records, class types, or function values.</span></span>


## <a name="binding-a-value"></a><span data-ttu-id="77fe7-105">値のバインド</span><span class="sxs-lookup"><span data-stu-id="77fe7-105">Binding a Value</span></span>
<span data-ttu-id="77fe7-106">*バインド*とは、名前と定義を関連付けることを意味します。</span><span class="sxs-lookup"><span data-stu-id="77fe7-106">The term *binding* means associating a name with a definition.</span></span> <span data-ttu-id="77fe7-107">`let` キーワードは、次の例のように、値のバインディングを行います。</span><span class="sxs-lookup"><span data-stu-id="77fe7-107">The `let` keyword binds a value, as in the following examples:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet601.fs)]

<span data-ttu-id="77fe7-108">値の型は、定義から推論されます。</span><span class="sxs-lookup"><span data-stu-id="77fe7-108">The type of a value is inferred from the definition.</span></span> <span data-ttu-id="77fe7-109">整数や浮動小数点数などのプリミティブ型では、型がリテラルの型から判断されます。</span><span class="sxs-lookup"><span data-stu-id="77fe7-109">For a primitive type, such as an integral or floating point number, the type is determined from the type of the literal.</span></span> <span data-ttu-id="77fe7-110">したがって、前の例では、コンパイラによって `b` の型が `unsigned int` と推論されるのに対し、`a` の型は `int` と推論されます。</span><span class="sxs-lookup"><span data-stu-id="77fe7-110">Therefore, in the previous example, the compiler infers the type of `b` to be `unsigned int`, whereas the compiler infers the type of `a` to be `int`.</span></span> <span data-ttu-id="77fe7-111">関数値の型は、関数本体の戻り値から判断されます。</span><span class="sxs-lookup"><span data-stu-id="77fe7-111">The type of a function value is determined from the return value in the function body.</span></span> <span data-ttu-id="77fe7-112">関数値の型の詳細については、「[関数](../functions/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77fe7-112">For more information about function value types, see [Functions](../functions/index.md).</span></span> <span data-ttu-id="77fe7-113">リテラルの型の詳細については、「[Literals](../literals.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77fe7-113">For more information about literal types, see [Literals](../literals.md).</span></span>


## <a name="why-immutable"></a><span data-ttu-id="77fe7-114">変更不可である理由</span><span class="sxs-lookup"><span data-stu-id="77fe7-114">Why Immutable?</span></span>
<span data-ttu-id="77fe7-115">変更不可の値とは、プログラムの実行過程全体を通じて変更できない値です。</span><span class="sxs-lookup"><span data-stu-id="77fe7-115">Immutable values are values that cannot be changed throughout the course of a program's execution.</span></span> <span data-ttu-id="77fe7-116">C++、Visual Basic、C# などの言語に慣れている場合は、F# のプログラムの実行中に、新しい値の割り当てが可能な変数よりも、変更不可な値が優先されることが意外に思われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-116">If you are used to languages such as C++, Visual Basic, or C#, you might find it surprising that F# puts primacy over immutable values rather than variables that can be assigned new values during the execution of a program.</span></span> <span data-ttu-id="77fe7-117">変更不可のデータは、関数型プログラミングの重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="77fe7-117">Immutable data is an important element of functional programming.</span></span> <span data-ttu-id="77fe7-118">マルチスレッド環境では、多数の異なるスレッドによる変更が可能な共有の変数を管理することは困難です。</span><span class="sxs-lookup"><span data-stu-id="77fe7-118">In a multithreaded environment, shared mutable variables that can be changed by many different threads are difficult to manage.</span></span> <span data-ttu-id="77fe7-119">また、変更可能な変数では、変数が別の関数に渡されたときに変更される可能性があるかどうかを見分けるのが難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-119">Also, with mutable variables, it can sometimes be hard to tell if a variable might be changed when it is passed to another function.</span></span>

<span data-ttu-id="77fe7-120">純粋な関数型言語では、変数は存在せず、関数は数学関数として厳密に機能します。</span><span class="sxs-lookup"><span data-stu-id="77fe7-120">In pure functional languages, there are no variables, and functions behave strictly as mathematical functions.</span></span> <span data-ttu-id="77fe7-121">手続き型言語のコードでは変数割り当てを使用して値を変更しますが、関数型言語の同等のコードには、入力である変更不可の値、変更不可の関数、および出力としての別の変更不可の値があります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-121">Where code in a procedural language uses a variable assignment to alter a value, the equivalent code in a functional language has an immutable value that is the input, an immutable function, and different immutable values as the output.</span></span> <span data-ttu-id="77fe7-122">この数学的な厳密性により、プログラムの動作についての強力な推論が実現します。</span><span class="sxs-lookup"><span data-stu-id="77fe7-122">This mathematical strictness allows for tighter reasoning about the behavior of the program.</span></span> <span data-ttu-id="77fe7-123">この強力な推論により、コンパイラでコードをより厳密にチェックし、より効率的に最適化を行い、開発者が正しいコードを容易に理解および記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-123">This tighter reasoning is what enables compilers to check code more stringently and to optimize more effectively, and helps make it easier for developers to understand and write correct code.</span></span> <span data-ttu-id="77fe7-124">したがって、関数型コードは、通常の手続き型コードよりもデバッグが容易になるのが普通です。</span><span class="sxs-lookup"><span data-stu-id="77fe7-124">Functional code is therefore likely to be easier to debug than ordinary procedural code.</span></span>

<span data-ttu-id="77fe7-125">F# は、純粋な関数型言語ではありませんが、関数型プログラミングを完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="77fe7-125">F# is not a pure functional language, yet it fully supports functional programming.</span></span> <span data-ttu-id="77fe7-126">変更不可の値の使用は、コードで関数型プログラミングの重要な特長を利用できる、優れたプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="77fe7-126">Using immutable values is a good practice because doing this allows your code to benefit from an important aspect of functional programming.</span></span>


## <a name="mutable-variables"></a><span data-ttu-id="77fe7-127">変更可能な変数</span><span class="sxs-lookup"><span data-stu-id="77fe7-127">Mutable Variables</span></span>
<span data-ttu-id="77fe7-128">キーワード `mutable` を使用して、変更可能な変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="77fe7-128">You can use the keyword `mutable` to specify a variable that can be changed.</span></span> <span data-ttu-id="77fe7-129">F# での変更可能な変数の範囲は、通常、型のフィールドまたはローカル値として限定されています。</span><span class="sxs-lookup"><span data-stu-id="77fe7-129">Mutable variables in F# should generally have a limited scope, either as a field of a type or as a local value.</span></span> <span data-ttu-id="77fe7-130">範囲が限定された変更可能な変数は、制御が容易であり、誤った方法で変更される可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-130">Mutable variables with a limited scope are easier to control and are less likely to be modified in incorrect ways.</span></span>

<span data-ttu-id="77fe7-131">変更可能な変数に初期値を割り当てるには、値を定義するときと同じ方法で、`let` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="77fe7-131">You can assign an initial value to a mutable variable by using the `let` keyword in the same way as you would define a value.</span></span> <span data-ttu-id="77fe7-132">ただし、次の例に示すように、`<-` 演算子を使用して、変更可能な変数に後で新しい値を割り当てることができる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="77fe7-132">However, the difference is that you can subsequently assign new values to mutable variables by using the `<-` operator, as in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet602.fs)]
    
## <a name="related-topics"></a><span data-ttu-id="77fe7-133">関連トピック</span><span class="sxs-lookup"><span data-stu-id="77fe7-133">Related Topics</span></span>


|<span data-ttu-id="77fe7-134">タイトル</span><span class="sxs-lookup"><span data-stu-id="77fe7-134">Title</span></span>|<span data-ttu-id="77fe7-135">説明</span><span class="sxs-lookup"><span data-stu-id="77fe7-135">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="77fe7-136">let バインド</span><span class="sxs-lookup"><span data-stu-id="77fe7-136">let Bindings</span></span>](../functions/let-bindings.md)|<span data-ttu-id="77fe7-137">使用に関する情報、`let`キーワード値や関数に名前をバインドします。</span><span class="sxs-lookup"><span data-stu-id="77fe7-137">Provides information about using the `let` keyword to bind names to values and functions.</span></span>|
|[<span data-ttu-id="77fe7-138">関数</span><span class="sxs-lookup"><span data-stu-id="77fe7-138">Functions</span></span>](../functions/index.md)|<span data-ttu-id="77fe7-139">F# の関数の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="77fe7-139">Provides an overview of functions in F#.</span></span>|

## <a name="see-also"></a><span data-ttu-id="77fe7-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="77fe7-140">See Also</span></span>
[<span data-ttu-id="77fe7-141">null 値</span><span class="sxs-lookup"><span data-stu-id="77fe7-141">Null Values</span></span>](null-Values.md)

[<span data-ttu-id="77fe7-142">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="77fe7-142">F# Language Reference</span></span>](../index.md)
