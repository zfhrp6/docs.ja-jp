---
title: インデックス付きプロパティ (F#)
description: F# でインデックス付きのプロパティは順序付けされたデータを配列に似たアクセスを提供するプロパティについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235942"
---
# <a name="indexed-properties"></a><span data-ttu-id="b938d-103">インデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="b938d-103">Indexed Properties</span></span>

<span data-ttu-id="b938d-104">*インデックス付きプロパティ*を配列に似たアクセスを提供するプロパティ値に基づいて並べ替えられるデータ。</span><span class="sxs-lookup"><span data-stu-id="b938d-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="b938d-105">これらは 3 つの形式があります。</span><span class="sxs-lookup"><span data-stu-id="b938d-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="b938d-106">F# のメンバーは、これら 3 つの配列に似たアクセスを提供する名前のいずれかの名前をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b938d-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="b938d-107">`IndexerName` 次の 3 つのオプションのいずれかを表すために使用します。</span><span class="sxs-lookup"><span data-stu-id="b938d-107">`IndexerName` is used to represent any of the three options below:</span></span>


## <a name="syntax"></a><span data-ttu-id="b938d-108">構文</span><span class="sxs-lookup"><span data-stu-id="b938d-108">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="b938d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b938d-109">Remarks</span></span>
<span data-ttu-id="b938d-110">前の構文のフォームは、両方があるインデックス付きプロパティを定義する方法を示して、`get`と`set`メソッドが、`get`メソッドのみかが、`set`メソッドのみです。</span><span class="sxs-lookup"><span data-stu-id="b938d-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="b938d-111">両方のみ get および set のみに示される構文に示される構文を結合し、get および set の両方を持つプロパティを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b938d-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="b938d-112">この後者の形式を使用すると、get で異なるアクセシビリティ修飾子と属性を配置して、メソッドを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b938d-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="b938d-113">ときに、 *IndexerName*は`Item`コンパイラは、既定のインデックス付きプロパティとしてプロパティを扱います。</span><span class="sxs-lookup"><span data-stu-id="b938d-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="b938d-114">A*インデックス付きプロパティの既定*オブジェクト インスタンスの配列に似た構文を使用してアクセスできるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="b938d-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="b938d-115">たとえば場合、`obj`構文は、このプロパティを定義する型のオブジェクトである`obj.[index]`プロパティにアクセスするために使用します。</span><span class="sxs-lookup"><span data-stu-id="b938d-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="b938d-116">既定以外のインデックス付きプロパティへのアクセスの構文では、プロパティ、かっこ内のインデックスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b938d-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="b938d-117">たとえば、次のプロパティが`Ordinal`、記述する`obj.Ordinal(index)`へのアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b938d-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="b938d-118">使用する形式に関係なくのカリー化された形式を使用する必要があります常に、`set`インデックス付きプロパティのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b938d-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="b938d-119">カリー化関数については、次を参照してください。[関数](../functions/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="b938d-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="b938d-120">例</span><span class="sxs-lookup"><span data-stu-id="b938d-120">Example</span></span>

<span data-ttu-id="b938d-121">次のコード例は、定義と使用の既定値と既定以外のインデックス付きプロパティ get し、set メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="b938d-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="b938d-122">出力</span><span class="sxs-lookup"><span data-stu-id="b938d-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="b938d-123">複数のインデックス変数でインデックス付きプロパティ</span><span class="sxs-lookup"><span data-stu-id="b938d-123">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="b938d-124">インデックス付きプロパティには、1 つ以上のインデックス変数を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="b938d-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="b938d-125">その場合は、プロパティを使用する場合に、変数はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="b938d-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="b938d-126">このようなプロパティの set メソッド、最初は、キーを含むタプル、2 番目の値が設定されている 2 つのカリー化された引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="b938d-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="b938d-127">次のコードでは、複数のインデックス変数でインデックス付きプロパティの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="b938d-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="b938d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b938d-128">See Also</span></span>
[<span data-ttu-id="b938d-129">メンバー</span><span class="sxs-lookup"><span data-stu-id="b938d-129">Members</span></span>](index.md)
