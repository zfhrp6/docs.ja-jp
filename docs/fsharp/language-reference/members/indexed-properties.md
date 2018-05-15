---
title: インデックス付きプロパティ (F#)
description: F# でインデックス付きのプロパティは順序付けされたデータを配列に似たアクセスを提供するプロパティについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b3945c7fc22977373b601856036178e890abc13e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="indexed-properties"></a><span data-ttu-id="e6b7d-103">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="e6b7d-103">Indexed Properties</span></span>

<span data-ttu-id="e6b7d-104">*インデックス付きプロパティ*を配列に似たアクセスを提供するプロパティ値に基づいて並べ替えられるデータ。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="e6b7d-105">構文</span><span class="sxs-lookup"><span data-stu-id="e6b7d-105">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="e6b7d-106">コメント</span><span class="sxs-lookup"><span data-stu-id="e6b7d-106">Remarks</span></span>
<span data-ttu-id="e6b7d-107">前の構文の 3 つの形式は、両方があるインデックス付きプロパティを定義する方法を示して、`get`と`set`メソッドが、`get`メソッドのみかが、`set`メソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-107">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="e6b7d-108">両方のみ get および set のみに示される構文に示される構文を結合し、get および set の両方を持つプロパティを生成できます。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-108">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="e6b7d-109">この後者の形式を使用すると、get で異なるアクセシビリティ修飾子と属性を配置して、メソッドを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-109">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="e6b7d-110">ときに、 *PropertyName*は`Item`コンパイラは、既定のインデックス付きプロパティとしてプロパティを扱います。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-110">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="e6b7d-111">A*インデックス付きプロパティの既定*オブジェクト インスタンスの配列に似た構文を使用してアクセスできるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-111">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="e6b7d-112">たとえば場合、`obj`構文は、このプロパティを定義する型のオブジェクトである`obj.[index]`プロパティにアクセスするために使用します。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-112">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="e6b7d-113">既定以外のインデックス付きプロパティへのアクセスの構文では、プロパティ、かっこ内のインデックスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-113">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="e6b7d-114">たとえば、次のプロパティが`Ordinal`、記述する`obj.Ordinal(index)`へのアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-114">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="e6b7d-115">使用する形式に関係なくのカリー化された形式を使用する必要があります常に、`set`インデックス付きプロパティのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-115">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="e6b7d-116">カリー化関数については、次を参照してください。[関数](../functions/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-116">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6b7d-117">例</span><span class="sxs-lookup"><span data-stu-id="e6b7d-117">Example</span></span>

<span data-ttu-id="e6b7d-118">次のコード例は、定義と使用の既定値と既定以外のインデックス付きプロパティ get し、set メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-118">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="e6b7d-119">出力</span><span class="sxs-lookup"><span data-stu-id="e6b7d-119">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="e6b7d-120">複数のインデックス変数でインデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="e6b7d-120">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="e6b7d-121">インデックス付きプロパティには、1 つ以上のインデックス変数を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-121">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="e6b7d-122">その場合は、プロパティを使用する場合に、変数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-122">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="e6b7d-123">このようなプロパティの set メソッド、最初は、キーを含むタプル、2 番目の値が設定されている 2 つのカリー化された引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-123">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="e6b7d-124">次のコードでは、複数のインデックス変数でインデックス付きプロパティの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="e6b7d-124">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="e6b7d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6b7d-125">See Also</span></span>
[<span data-ttu-id="e6b7d-126">メンバー</span><span class="sxs-lookup"><span data-stu-id="e6b7d-126">Members</span></span>](index.md)
