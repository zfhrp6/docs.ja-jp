---
title: "型略称 (F#)"
description: "F# 型の省略形型に名前を付けるより意味のあるコードを読みやすくためにについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a><span data-ttu-id="19cb2-104">型略称</span><span class="sxs-lookup"><span data-stu-id="19cb2-104">Type Abbreviations</span></span>

<span data-ttu-id="19cb2-105">A*型略称*エイリアスまたは型の代替名です。</span><span class="sxs-lookup"><span data-stu-id="19cb2-105">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="19cb2-106">構文</span><span class="sxs-lookup"><span data-stu-id="19cb2-106">Syntax</span></span>

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="19cb2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="19cb2-107">Remarks</span></span>
<span data-ttu-id="19cb2-108">型の省略形を使用すると、コードを読みやすくために、型、わかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="19cb2-108">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="19cb2-109">種類が書き込みに面倒なを使いやすい名を作成するのにも使用できます。さらに、型を使用するすべてのコードを変更しなくても、基になる型を変更しやすく型の省略形を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="19cb2-109">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="19cb2-110">単純型の省略形を次に示します。</span><span class="sxs-lookup"><span data-stu-id="19cb2-110">The following is a simple type abbreviation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="19cb2-111">型の省略形は、次のコードのように、ジェネリック パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="19cb2-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="19cb2-112">前のコードで`Transform`を任意の型の 1 つの引数を受け取る関数を表す型の省略形は、同じ型の 1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="19cb2-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="19cb2-113">型の省略形は、.NET Framework の MSIL コードでは保持されません。</span><span class="sxs-lookup"><span data-stu-id="19cb2-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="19cb2-114">したがって、f# アセンブリ別の .NET Framework 言語からを使用する場合は、型の省略形の基になる種類の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19cb2-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="19cb2-115">型の省略形は、測定単位でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="19cb2-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="19cb2-116">詳細については、次を参照してください。[単位](units-of-measure.md)です。</span><span class="sxs-lookup"><span data-stu-id="19cb2-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="19cb2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="19cb2-117">See Also</span></span>
[<span data-ttu-id="19cb2-118">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="19cb2-118">F# Language Reference</span></span>](index.md)

