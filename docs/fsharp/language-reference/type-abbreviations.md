---
title: 型略称 (F#)
description: F# 型の省略形型に名前を付けるより意味のあるコードを読みやすくためにについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058958"
---
# <a name="type-abbreviations"></a><span data-ttu-id="13d8a-103">型略称</span><span class="sxs-lookup"><span data-stu-id="13d8a-103">Type Abbreviations</span></span>

<span data-ttu-id="13d8a-104">A*型略称*エイリアスまたは型の代替名です。</span><span class="sxs-lookup"><span data-stu-id="13d8a-104">A *type abbreviation* is an alias or alternate name for a type.</span></span>

## <a name="syntax"></a><span data-ttu-id="13d8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="13d8a-105">Syntax</span></span>

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a><span data-ttu-id="13d8a-106">コメント</span><span class="sxs-lookup"><span data-stu-id="13d8a-106">Remarks</span></span>
<span data-ttu-id="13d8a-107">型の省略形を使用すると、コードを読みやすくために、型、わかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="13d8a-107">You can use type abbreviations to give a type a more meaningful name, in order to make code easier to read.</span></span> <span data-ttu-id="13d8a-108">種類が書き込みに面倒なを使いやすい名を作成するのにも使用できます。さらに、型を使用するすべてのコードを変更しなくても、基になる型を変更しやすく型の省略形を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="13d8a-108">You can also use them to create an easy to use name for a type that is otherwise cumbersome to write out. Additionally, you can use type abbreviations to make it easier to change an underlying type without changing all the code that uses the type.</span></span> <span data-ttu-id="13d8a-109">単純型の省略形を次に示します。</span><span class="sxs-lookup"><span data-stu-id="13d8a-109">The following is a simple type abbreviation.</span></span>

<span data-ttu-id="13d8a-110">型の省略形のユーザー補助機能が既定で`public`です。</span><span class="sxs-lookup"><span data-stu-id="13d8a-110">Accessibility of type abbreviations defaults to `public`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

<span data-ttu-id="13d8a-111">型の省略形は、次のコードのように、ジェネリック パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="13d8a-111">Type abbreviations can include generic parameters, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

<span data-ttu-id="13d8a-112">前のコードで`Transform`を任意の型の 1 つの引数を受け取る関数を表す型の省略形は、同じ型の 1 つの値を返します。</span><span class="sxs-lookup"><span data-stu-id="13d8a-112">In the previous code, `Transform` is a type abbreviation that represents a function that takes a single argument of any type and that returns a single value of that same type.</span></span>

<span data-ttu-id="13d8a-113">型の省略形は、.NET Framework の MSIL コードでは保持されません。</span><span class="sxs-lookup"><span data-stu-id="13d8a-113">Type abbreviations are not preserved in the .NET Framework MSIL code.</span></span> <span data-ttu-id="13d8a-114">したがって、f# アセンブリ別の .NET Framework 言語からを使用する場合は、型の省略形の基になる種類の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13d8a-114">Therefore, when you use an F# assembly from another .NET Framework language, you must use the underlying type name for a type abbreviation.</span></span>

<span data-ttu-id="13d8a-115">型の省略形は、測定単位でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="13d8a-115">Type abbreviations can also be used on units of measure.</span></span> <span data-ttu-id="13d8a-116">詳細については、次を参照してください。[単位](units-of-measure.md)です。</span><span class="sxs-lookup"><span data-stu-id="13d8a-116">For more information, see [Units of Measure](units-of-measure.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="13d8a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="13d8a-117">See Also</span></span>
[<span data-ttu-id="13d8a-118">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="13d8a-118">F# Language Reference</span></span>](index.md)

