---
title: デリゲート (F#)
description: F# でデリゲートを使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 664b4f80302871d05ea9604ca90219e19bc14ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563442"
---
# <a name="delegates"></a><span data-ttu-id="62b77-103">デリゲート</span><span class="sxs-lookup"><span data-stu-id="62b77-103">Delegates</span></span>

<span data-ttu-id="62b77-104">デリゲートは、オブジェクトとして関数呼び出しを表します。</span><span class="sxs-lookup"><span data-stu-id="62b77-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="62b77-105">F# では、通常使用することは関数の値をファーストクラスの値として関数を表すただし、デリゲートには .NET Framework で使用し、相互運用することが期待する Api を使用したときに、必要なため。</span><span class="sxs-lookup"><span data-stu-id="62b77-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="62b77-106">用に設計されたオーサリング ライブラリが他の .NET Framework 言語から使用も使用できます。</span><span class="sxs-lookup"><span data-stu-id="62b77-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>


## <a name="syntax"></a><span data-ttu-id="62b77-107">構文</span><span class="sxs-lookup"><span data-stu-id="62b77-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="62b77-108">コメント</span><span class="sxs-lookup"><span data-stu-id="62b77-108">Remarks</span></span>
<span data-ttu-id="62b77-109">前の構文で`type1`引数の型または型を表すと`type2`戻り値の型を表します。</span><span class="sxs-lookup"><span data-stu-id="62b77-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="62b77-110">引数の型によって表される`type1`自動的にカリー化します。</span><span class="sxs-lookup"><span data-stu-id="62b77-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="62b77-111">これは対象の関数の引数はカリー化された場合は、タプルの形式を使用するこの型、タプルの形式に既に含まれている引数をかっこで囲まれた組のことを示します。</span><span class="sxs-lookup"><span data-stu-id="62b77-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="62b77-112">自動カリー化には、対象のメソッドに一致する組の引数を残して、かっこのセットを削除します。</span><span class="sxs-lookup"><span data-stu-id="62b77-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="62b77-113">各ケースで使用する構文のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62b77-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="62b77-114">デリゲートは、f# 関数値、および静的に関連付けることができます。 またはインスタンス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="62b77-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="62b77-115">F# の関数の値は、デリゲート コンス トラクターに引数として直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="62b77-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="62b77-116">静的メソッドは、クラスとメソッドの名前を使用して、デリゲートを構築します。</span><span class="sxs-lookup"><span data-stu-id="62b77-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="62b77-117">インスタンス メソッドでは、オブジェクトのインスタンスと 1 つの引数でメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="62b77-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="62b77-118">どちらの場合、メンバー アクセス演算子 (`.`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="62b77-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="62b77-119">`Invoke`デリゲート型のメソッドは、カプセル化された関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="62b77-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="62b77-120">また、デリゲートは、かっこがない場合は、Invoke メソッドの名前を参照することによって関数の値として渡されますことができます。</span><span class="sxs-lookup"><span data-stu-id="62b77-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="62b77-121">次のコードは、クラスのさまざまなメソッドを表すデリゲートを作成するための構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="62b77-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="62b77-122">メソッドは静的メソッドまたはインスタンス メソッドで、かどうかと、引数はタプル形式またはカリー化された形式であるかどうか、に応じてを宣言して、デリゲートを割り当てるのための構文は若干異なりますです。</span><span class="sxs-lookup"><span data-stu-id="62b77-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="62b77-123">次のコードでは、デリゲートを使用するさまざまな方法の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="62b77-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="62b77-124">上記のコード例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="62b77-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="62b77-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="62b77-125">See Also</span></span>
[<span data-ttu-id="62b77-126">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="62b77-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="62b77-127">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="62b77-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="62b77-128">イベント</span><span class="sxs-lookup"><span data-stu-id="62b77-128">Events</span></span>](members/events.md)
