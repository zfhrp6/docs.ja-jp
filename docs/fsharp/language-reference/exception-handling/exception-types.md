---
title: "例外の種類 (F#)"
description: "定義して、f# の例外の種類を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="f66a5-104">例外の種類</span><span class="sxs-lookup"><span data-stu-id="f66a5-104">Exception Types</span></span>

<span data-ttu-id="f66a5-105">F# の例外の 2 つのカテゴリがあります。 .NET の例外の種類と f# の例外の種類。</span><span class="sxs-lookup"><span data-stu-id="f66a5-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="f66a5-106">このトピックでは、定義して、f# の例外の種類を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f66a5-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="f66a5-107">構文</span><span class="sxs-lookup"><span data-stu-id="f66a5-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="f66a5-108">コメント</span><span class="sxs-lookup"><span data-stu-id="f66a5-108">Remarks</span></span>
<span data-ttu-id="f66a5-109">前の構文で*例外型*新しい f# の例外の種類の名前を指定および*引数の型*この型の例外が発生するときに指定できる引数の型を表します。</span><span class="sxs-lookup"><span data-stu-id="f66a5-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="f66a5-110">タプル型を使用して複数の引数を指定することができます*引数の型*です。</span><span class="sxs-lookup"><span data-stu-id="f66a5-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="f66a5-111">F# の例外の一般的な定義には、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f66a5-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="f66a5-112">使用してこの型の例外を生成することができます、`raise`関数は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f66a5-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="f66a5-113">F# の例外の種類を使用するには、フィルター内で直接、`try...with`式では、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="f66a5-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="f66a5-114">例外の種類で定義された、 `exception` f# のキーワードはから継承する新しい型`System.Exception`です。</span><span class="sxs-lookup"><span data-stu-id="f66a5-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="f66a5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f66a5-115">See Also</span></span>
[<span data-ttu-id="f66a5-116">例外処理</span><span class="sxs-lookup"><span data-stu-id="f66a5-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="f66a5-117">例外: `raise` 関数</span><span class="sxs-lookup"><span data-stu-id="f66a5-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="f66a5-118">例外階層</span><span class="sxs-lookup"><span data-stu-id="f66a5-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
