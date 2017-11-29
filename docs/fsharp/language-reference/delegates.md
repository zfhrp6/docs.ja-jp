---
title: "デリゲート (F#)"
description: "F# でデリゲートを使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 719948a3-83ba-4618-82d6-a22945c3f4b0
ms.openlocfilehash: c929a342ab4c5098062417691a99cee3b007d2d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="472f8-104">デリゲート</span><span class="sxs-lookup"><span data-stu-id="472f8-104">Delegates</span></span>

<span data-ttu-id="472f8-105">デリゲートは、オブジェクトとして関数呼び出しを表します。</span><span class="sxs-lookup"><span data-stu-id="472f8-105">A delegate represents a function call as an object.</span></span> <span data-ttu-id="472f8-106">F# では、通常使用することは関数の値をファーストクラスの値として関数を表すただし、デリゲートには .NET Framework で使用し、相互運用することが期待する Api を使用したときに、必要なため。</span><span class="sxs-lookup"><span data-stu-id="472f8-106">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="472f8-107">用に設計されたオーサリング ライブラリが他の .NET Framework 言語から使用も使用できます。</span><span class="sxs-lookup"><span data-stu-id="472f8-107">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="472f8-108">構文</span><span class="sxs-lookup"><span data-stu-id="472f8-108">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="472f8-109">コメント</span><span class="sxs-lookup"><span data-stu-id="472f8-109">Remarks</span></span>
<span data-ttu-id="472f8-110">前の構文で`type1`引数の型または型を表すと`type2`戻り値の型を表します。</span><span class="sxs-lookup"><span data-stu-id="472f8-110">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="472f8-111">引数の型によって表される`type1`自動的にカリー化します。</span><span class="sxs-lookup"><span data-stu-id="472f8-111">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="472f8-112">これは対象の関数の引数はカリー化された場合は、タプルの形式を使用するこの型、タプルの形式に既に含まれている引数をかっこで囲まれた組のことを示します。</span><span class="sxs-lookup"><span data-stu-id="472f8-112">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="472f8-113">自動カリー化には、対象のメソッドに一致する組の引数を残して、かっこのセットを削除します。</span><span class="sxs-lookup"><span data-stu-id="472f8-113">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="472f8-114">各ケースで使用する構文のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472f8-114">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="472f8-115">デリゲートは、f# 関数値、および静的に関連付けることができます。 またはインスタンス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="472f8-115">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="472f8-116">F# の関数の値は、デリゲート コンス トラクターに引数として直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="472f8-116">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="472f8-117">静的メソッドは、クラスとメソッドの名前を使用して、デリゲートを構築します。</span><span class="sxs-lookup"><span data-stu-id="472f8-117">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="472f8-118">インスタンス メソッドでは、オブジェクトのインスタンスと 1 つの引数でメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="472f8-118">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="472f8-119">どちらの場合、メンバー アクセス演算子 (`.`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="472f8-119">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="472f8-120">`Invoke`デリゲート型のメソッドは、カプセル化された関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="472f8-120">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="472f8-121">また、デリゲートは、かっこがない場合は、Invoke メソッドの名前を参照することによって関数の値として渡されますことができます。</span><span class="sxs-lookup"><span data-stu-id="472f8-121">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="472f8-122">次のコードは、クラスのさまざまなメソッドを表すデリゲートを作成するための構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="472f8-122">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="472f8-123">メソッドは静的メソッドまたはインスタンス メソッドで、かどうかと、引数はタプル形式またはカリー化された形式であるかどうか、に応じてを宣言して、デリゲートを割り当てるのための構文は若干異なりますです。</span><span class="sxs-lookup"><span data-stu-id="472f8-123">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="472f8-124">次のコードでは、デリゲートを使用するさまざまな方法の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="472f8-124">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="472f8-125">上記のコード例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="472f8-125">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="472f8-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="472f8-126">See Also</span></span>
[<span data-ttu-id="472f8-127">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="472f8-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="472f8-128">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="472f8-128">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="472f8-129">イベント</span><span class="sxs-lookup"><span data-stu-id="472f8-129">Events</span></span>](members/events.md)
