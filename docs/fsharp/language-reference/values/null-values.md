---
title: "null 値 (F#)"
description: "F# のプログラミング言語で null 値を使用する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 68ebd261-51cf-4582-b2dc-44c84d1c2500
ms.openlocfilehash: 01c14de00eb5efd0952145ffc8aabe69d65a3a48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="null-values"></a><span data-ttu-id="c446d-104">null 値</span><span class="sxs-lookup"><span data-stu-id="c446d-104">Null Values</span></span>

<span data-ttu-id="c446d-105">このトピックでは、f# では、null 値を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c446d-105">This topic describes how the null value is used in F#.</span></span>


## <a name="null-value"></a><span data-ttu-id="c446d-106">Null 値</span><span class="sxs-lookup"><span data-stu-id="c446d-106">Null Value</span></span>
<span data-ttu-id="c446d-107">Null 値は通常使用されません f# での値または変数。</span><span class="sxs-lookup"><span data-stu-id="c446d-107">The null value is not normally used in F# for values or variables.</span></span> <span data-ttu-id="c446d-108">ただし、特定の状況で異常値として null が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c446d-108">However, null appears as an abnormal value in certain situations.</span></span> <span data-ttu-id="c446d-109">しない限り、null がいない正規の値として許可型が f# で定義されている場合、 [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f)型に属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="c446d-109">If a type is defined in F#, null is not permitted as a regular value unless the [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) attribute is applied to the type.</span></span> <span data-ttu-id="c446d-110">Null は使用可能な値型が他のいくつかの .NET 言語で定義されている場合と f# コードが null 値に生じるそのような型の相互運用するときにします。</span><span class="sxs-lookup"><span data-stu-id="c446d-110">If a type is defined in some other .NET language, null is a possible value, and when you are interoperating with such types, your F# code might encounter null values.</span></span>

<span data-ttu-id="c446d-111">F# で定義されているし、F# からにのみ使用の種類を直接 f# ライブラリを使用して null 値を作成する唯一の方法は使用する[Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977)または[Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)です。</span><span class="sxs-lookup"><span data-stu-id="c446d-111">For a type defined in F# and used strictly from F#, the only way to create a null value using the F# library directly is to use [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) or [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2).</span></span> <span data-ttu-id="c446d-112">ただし、f# の型の他の .NET 言語から使用されるまたは null 値が発生する可能性が f# など、.NET Framework で記述されたない API を使用してその型を使用している場合。</span><span class="sxs-lookup"><span data-stu-id="c446d-112">However, for an F# type that is used from other .NET languages, or if you are using that type with an API that is not written in F#, such as the .NET Framework, null values can occur.</span></span>

<span data-ttu-id="c446d-113">使用することができます、 `option` f# 可能な値が null の他の .NET 言語で参照変数を使用する状況での型。</span><span class="sxs-lookup"><span data-stu-id="c446d-113">You can use the `option` type in F# when you might use a reference variable with a possible null value in another .NET language.</span></span> <span data-ttu-id="c446d-114">Null の場合、f# ではなく`option`型、オプションの値を使用する`None`オブジェクトが存在しない場合。</span><span class="sxs-lookup"><span data-stu-id="c446d-114">Instead of null, with an F# `option` type, you use the option value `None` if there is no object.</span></span> <span data-ttu-id="c446d-115">オプションの値を使用する`Some(obj)`オブジェクト`obj`オブジェクトがある場合。</span><span class="sxs-lookup"><span data-stu-id="c446d-115">You use the option value `Some(obj)` with an object `obj` when there is an object.</span></span> <span data-ttu-id="c446d-116">詳細については、次を参照してください。[オプション](../options.md)です。</span><span class="sxs-lookup"><span data-stu-id="c446d-116">For more information, see [Options](../options.md).</span></span>

<span data-ttu-id="c446d-117">`null`キーワードは f# 言語で有効なキーワードと .NET Framework Api または他の .NET 言語で記述されているその他の Api を使用するときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c446d-117">The `null` keyword is a valid keyword in the F# language, and you have to use it when you are working with .NET Framework APIs or other APIs that are written in another .NET language.</span></span> <span data-ttu-id="c446d-118">Null 値が必要がある 2 つの状況は、.NET API を呼び出すし、null 値を引数として渡すときに、戻り値または .NET メソッドの呼び出しから出力パラメーターを解釈するときにします。</span><span class="sxs-lookup"><span data-stu-id="c446d-118">The two situations in which you might need a null value are when you call a .NET API and pass a null value as an argument, and when you interpret the return value or an output parameter from a .NET method call.</span></span>

<span data-ttu-id="c446d-119">.NET メソッドに null 値を渡すを使用した、`null`呼び出し元のコードのキーワードです。</span><span class="sxs-lookup"><span data-stu-id="c446d-119">To pass a null value to a .NET method, just use the `null` keyword in the calling code.</span></span> <span data-ttu-id="c446d-120">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="c446d-120">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

<span data-ttu-id="c446d-121">.NET メソッドから取得される null 値を解釈するには、するには、可能な場合に一致するパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c446d-121">To interpret a null value that is obtained from a .NET method, use pattern matching if you can.</span></span> <span data-ttu-id="c446d-122">次のコード例は、パターン マッチを使用して、返される null 値を解釈する方法を示しています。`ReadLine`入力ストリームの末尾を越えて読み取ろうとしたときにします。</span><span class="sxs-lookup"><span data-stu-id="c446d-122">The following code example shows how to use pattern matching to interpret the null value that is returned from `ReadLine` when it tries to read past the end of an input stream.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

<span data-ttu-id="c446d-123">F# の型の null 値を使用する場合など、他の方法で生成することも`Array.zeroCreate`、どの呼び出し`Unchecked.defaultof`です。</span><span class="sxs-lookup"><span data-stu-id="c446d-123">Null values for F# types can also be generated in other ways, such as when you use `Array.zeroCreate`, which calls `Unchecked.defaultof`.</span></span> <span data-ttu-id="c446d-124">そのようなコードのカプセル化された null 値を保持するように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c446d-124">You must be careful with such code to keep the null values encapsulated.</span></span> <span data-ttu-id="c446d-125">専用の f# ライブラリですべての関数で null 値を確認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c446d-125">In a library intended only for F#, you do not have to check for null values in every function.</span></span> <span data-ttu-id="c446d-126">他の .NET 言語と相互運用ライブラリを作成している場合は null のチェックは、入力パラメーターと、スローを追加する必要が可能性があります、 `ArgumentNullException`c# または Visual Basic コードで行うのと同様、します。</span><span class="sxs-lookup"><span data-stu-id="c446d-126">If you are writing a library for interoperation with other .NET languages, you might have to add checks for null input parameters and throw an `ArgumentNullException`, just as you do in C# or Visual Basic code.</span></span>

<span data-ttu-id="c446d-127">次のコードを使用すると、任意の値が null を確認します。</span><span class="sxs-lookup"><span data-stu-id="c446d-127">You can use the following code to check if an arbitrary value is null.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a><span data-ttu-id="c446d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c446d-128">See Also</span></span>
[<span data-ttu-id="c446d-129">値</span><span class="sxs-lookup"><span data-stu-id="c446d-129">Values</span></span>](index.md)

[<span data-ttu-id="c446d-130">match 式</span><span class="sxs-lookup"><span data-stu-id="c446d-130">Match Expressions</span></span>](../match-expressions.md)
