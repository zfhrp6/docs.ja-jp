---
title: 型推論 (F#)
description: F# コンパイラが値、変数、パラメーター、および戻り値の型を推論する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 93e1568ebe71436ad8f7119ac9d9628cdf58012a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563707"
---
# <a name="type-inference"></a><span data-ttu-id="90e09-103">型推論</span><span class="sxs-lookup"><span data-stu-id="90e09-103">Type Inference</span></span>

<span data-ttu-id="90e09-104">このトピックでは、f# コンパイラが値、変数、パラメーターおよび戻り値の型を推論する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90e09-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="90e09-105">推定の一般的な型します。</span><span class="sxs-lookup"><span data-stu-id="90e09-105">Type Inference in General</span></span>
<span data-ttu-id="90e09-106">型の推論の概念は、f# の構成要素と、コンパイラには、型が推測できません確定以外の種類を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="90e09-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="90e09-107">F# は動的に型指定された言語に、f# で値が厳密に型指定された、明示的な型情報を省略することは限りません。</span><span class="sxs-lookup"><span data-stu-id="90e09-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="90e09-108">F# は、静的に型指定された言語が含まれ、コンパイラがコンパイル時に各構成体の固定の型を推測することを意味します。</span><span class="sxs-lookup"><span data-stu-id="90e09-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="90e09-109">コンパイラが各構成体の型を推測するのに十分な情報がない場合は、コードのどこかに明示的な型の注釈を追加することで、追加の型情報を通常指定してください。</span><span class="sxs-lookup"><span data-stu-id="90e09-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>


## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="90e09-110">パラメーターと戻り値の型の推論</span><span class="sxs-lookup"><span data-stu-id="90e09-110">Inference of Parameter and Return Types</span></span>
<span data-ttu-id="90e09-111">パラメーター リストでは、各パラメーターの型を指定するのにはありません。</span><span class="sxs-lookup"><span data-stu-id="90e09-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="90e09-112">まだ、f# は、静的に型指定された言語とすべての値と式が明確な型コンパイル時。</span><span class="sxs-lookup"><span data-stu-id="90e09-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="90e09-113">明示的に指定されていないその型の場合は、コンパイラは、コンテキストに基づいて型を推測します。</span><span class="sxs-lookup"><span data-stu-id="90e09-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="90e09-114">型がそれ以外の場合を指定でない場合は、ジェネリックにする推論されます。</span><span class="sxs-lookup"><span data-stu-id="90e09-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="90e09-115">コードでは、一貫性がない値を使用する場合このような方法ではなく 1 つ推論された型をコンパイラがエラーを報告する、値のすべての利用を満たします。</span><span class="sxs-lookup"><span data-stu-id="90e09-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="90e09-116">関数の戻り値の型は、関数の最後の式の型によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="90e09-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="90e09-117">たとえば、次のコードでは、パラメーターの型で`a`と`b`、戻り値の型はすべてを推論する`int`ためリテラル`100`の種類は`int`します。</span><span class="sxs-lookup"><span data-stu-id="90e09-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="90e09-118">リテラルは、変更することによって型の推論の影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="90e09-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="90e09-119">加えた場合、 `100` 、 `uint32` 、サフィックスを付加した`u`、種類の`a`、 `b`、および戻り値と推論されます`uint32`です。</span><span class="sxs-lookup"><span data-stu-id="90e09-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="90e09-120">影響を及ぼすことができます関数および特定の種類でのみ利用できるメソッドなどの型に制限を意味するその他の構文を使用して、型の推論します。</span><span class="sxs-lookup"><span data-stu-id="90e09-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="90e09-121">また、適用できます明示的な型の注釈関数またはメソッドのパラメーターまたは変数式では、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="90e09-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="90e09-122">さまざまな制約との間の競合が発生すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="90e09-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="90e09-123">関数の戻り値は、結局のところ、パラメーターの型の注釈を指定して明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="90e09-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="90e09-124">型の注釈はパラメーターで便利です一般的なケースは、パラメーターが、オブジェクト型とメンバーを使用するときに、します。</span><span class="sxs-lookup"><span data-stu-id="90e09-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]
    
## <a name="automatic-generalization"></a><span data-ttu-id="90e09-125">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="90e09-125">Automatic Generalization</span></span>
<span data-ttu-id="90e09-126">関数のコードが、パラメーターの型に依存しない場合は、コンパイラはパラメーターをジェネリックと見なします。</span><span class="sxs-lookup"><span data-stu-id="90e09-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="90e09-127">これと呼ばれる*自動ジェネリック化*複雑さを増やすことがなくジェネリック コードを記述するための強力なを指定できます。</span><span class="sxs-lookup"><span data-stu-id="90e09-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="90e09-128">たとえば、次の関数は、任意の型の組に 2 つのパラメーターを結合します。</span><span class="sxs-lookup"><span data-stu-id="90e09-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="90e09-129">型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="90e09-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="90e09-130">追加情報</span><span class="sxs-lookup"><span data-stu-id="90e09-130">Additional Information</span></span>
<span data-ttu-id="90e09-131">型の推論は f# 言語仕様で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="90e09-131">Type inference is described in more detail in the F# Language Specification.</span></span>


## <a name="see-also"></a><span data-ttu-id="90e09-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="90e09-132">See Also</span></span>
[<span data-ttu-id="90e09-133">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="90e09-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
