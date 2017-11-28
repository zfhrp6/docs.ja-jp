---
title: "オブジェクト式 (F#)"
description: "名前付きの種類を追加のコードと、新規作成に必要なオーバーヘッドを回避するときに、f# オブジェクト式を使用する方法を学習します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c6dcf4c9-e7fd-4eee-9e4e-1176f4c27f57
ms.openlocfilehash: 28660d430473de02a8a55e37a26609827b364012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="object-expressions"></a><span data-ttu-id="20460-104">オブジェクト式</span><span class="sxs-lookup"><span data-stu-id="20460-104">Object Expressions</span></span>

<span data-ttu-id="20460-105">*式をオブジェクト*は動的に作成された、匿名のオブジェクトの種類の新しいインスタンスを作成する式が既存の基本型、インターフェイス、またはインターフェイスのセットに基づいて。</span><span class="sxs-lookup"><span data-stu-id="20460-105">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>


## <a name="syntax"></a><span data-ttu-id="20460-106">構文</span><span class="sxs-lookup"><span data-stu-id="20460-106">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="20460-107">コメント</span><span class="sxs-lookup"><span data-stu-id="20460-107">Remarks</span></span>
<span data-ttu-id="20460-108">前の構文では、 *typename*既存のクラス型またはインターフェイス型を表します。</span><span class="sxs-lookup"><span data-stu-id="20460-108">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="20460-109">*型 params*省略可能なジェネリック型パラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="20460-109">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="20460-110">*引数*コンス トラクターのパラメーターを必要とするクラス型に対してのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="20460-110">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="20460-111">*メンバー定義*は基本クラスのメソッドをオーバーライドまたは基底クラスまたはインターフェイスのいずれかの抽象メソッドの実装です。</span><span class="sxs-lookup"><span data-stu-id="20460-111">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="20460-112">次の例は、さまざまな種類のオブジェクトの式を示しています。</span><span class="sxs-lookup"><span data-stu-id="20460-112">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="20460-113">オブジェクト式を使用します。</span><span class="sxs-lookup"><span data-stu-id="20460-113">Using Object Expressions</span></span>
<span data-ttu-id="20460-114">余分なコードと名前付きの種類を新規作成に必要なオーバーヘッドを回避する場合は、オブジェクト表現を使用します。</span><span class="sxs-lookup"><span data-stu-id="20460-114">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="20460-115">プログラムで作成された型の数を最小限に抑えるには、オブジェクト表現を使用する場合のコード行の数を削減し、型の不要な急増を回避できます。</span><span class="sxs-lookup"><span data-stu-id="20460-115">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="20460-116">特定の状況に対処するためだけの多くの種類を作成するには、代わりに、既存の種類をカスタマイズまたは特定の状況にインターフェイスの適切な実装を提供するオブジェクト式を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="20460-116">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>


## <a name="see-also"></a><span data-ttu-id="20460-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="20460-117">See Also</span></span>
[<span data-ttu-id="20460-118">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="20460-118">F# Language Reference</span></span>](index.md)
