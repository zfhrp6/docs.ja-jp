---
title: "C# の配列 - C# 言語のツアー"
description: "配列は、C# 言語において最も基本的なコレクション型です。"
keywords: ".NET、C#、配列、コレクション"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 82362a3675c431423a99d3d728fb8dd1da58c9c7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="arrays"></a><span data-ttu-id="7c990-104">配列</span><span class="sxs-lookup"><span data-stu-id="7c990-104">Arrays</span></span>

<span data-ttu-id="7c990-105">***配列***はデータ構造で、算出されたインデックスを介してアクセスされる多くの変数を含みます。</span><span class="sxs-lookup"><span data-stu-id="7c990-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="7c990-106">配列に含まれる変数は配列の***要素***とも呼ばれ、すべて同じ型であり、この型は配列の***要素型***と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7c990-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="7c990-107">配列型は参照型で、配列変数の宣言は、配列インスタンスへの参照の領域を確保します。</span><span class="sxs-lookup"><span data-stu-id="7c990-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="7c990-108">実際の配列インスタンスは、new 演算子を使用して実行時に動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="7c990-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="7c990-109">この操作で新しい配列インスタンスの***長さ***が指定され、それはインスタンスの有効期間中は固定です。</span><span class="sxs-lookup"><span data-stu-id="7c990-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="7c990-110">配列の要素のインデックスは、`0` から `Length - 1` までです。</span><span class="sxs-lookup"><span data-stu-id="7c990-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="7c990-111">`new` 演算子は配列の要素を自動的に既定値に初期化します。たとえば、すべての数値型はゼロ、すべての参照型は `null` です。</span><span class="sxs-lookup"><span data-stu-id="7c990-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="7c990-112">次の例では、`int` 要素の配列を作成し、その配列を初期化し、配列の内容を出力します。</span><span class="sxs-lookup"><span data-stu-id="7c990-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

<span data-ttu-id="7c990-113">[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]</span><span class="sxs-lookup"><span data-stu-id="7c990-113">[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]</span></span>

<span data-ttu-id="7c990-114">この例は ***1 次元配列***を作成し、操作対象とします。</span><span class="sxs-lookup"><span data-stu-id="7c990-114">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="7c990-115">C# はさらに***多次元配列***をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7c990-115">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="7c990-116">配列型の次元数は、配列型の***ランク***とも呼ばれ、配列型の角かっこ内に記述されたコンマの数に 1 を追加したものです。</span><span class="sxs-lookup"><span data-stu-id="7c990-116">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="7c990-117">次の例では、1 次元、2 次元、および 3 次元の配列をそれぞれ割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7c990-117">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

<span data-ttu-id="7c990-118">[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]</span><span class="sxs-lookup"><span data-stu-id="7c990-118">[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]</span></span>

<span data-ttu-id="7c990-119">`a1` 配列は 10 の要素、`a2` 配列は 50 (10 × 5) の要素、`a3` 配列は 100 (10 × 5 × 2) の要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="7c990-119">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="7c990-120">配列の要素型には、配列型を含む任意の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="7c990-120">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="7c990-121">配列型の要素を持つ配列は、***ジャグ配列***と呼ばれることがあります。要素の配列の長さがすべて同じである必要がないからです。</span><span class="sxs-lookup"><span data-stu-id="7c990-121">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="7c990-122">次の例では、`int` の配列の配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7c990-122">The following example allocates an array of arrays of `int`:</span></span>

<span data-ttu-id="7c990-123">[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]</span><span class="sxs-lookup"><span data-stu-id="7c990-123">[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]</span></span>

<span data-ttu-id="7c990-124">最初の行で 3 つの要素を持つ配列を作成しますが、各々は `int[]` 型で `null` 初期値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="7c990-124">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="7c990-125">それ以降の行では、3 つの要素を、それぞれ異なる長さの配列インスタンスへの参照で初期化します。</span><span class="sxs-lookup"><span data-stu-id="7c990-125">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="7c990-126">new 演算子では、配列要素の初期値を、区切り記号 `{` および `}` のあいだに記述された式の一覧である***配列初期化子***を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7c990-126">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="7c990-127">次の例は、`int[]` を割り当て 3 つの要素で初期化します。</span><span class="sxs-lookup"><span data-stu-id="7c990-127">The following example allocates and initializes an `int[]` with three elements.</span></span>

<span data-ttu-id="7c990-128">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]</span><span class="sxs-lookup"><span data-stu-id="7c990-128">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]</span></span>

<span data-ttu-id="7c990-129">配列の長さが { and } の間にある式の数から推論されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c990-129">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="7c990-130">ローカル変数およびフィールド宣言をさらに短縮して、配列型を再起動する必要がないようにできます。</span><span class="sxs-lookup"><span data-stu-id="7c990-130">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

<span data-ttu-id="7c990-131">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]</span><span class="sxs-lookup"><span data-stu-id="7c990-131">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]</span></span>

<span data-ttu-id="7c990-132">前述の例はどちらも、次の例と同等です。</span><span class="sxs-lookup"><span data-stu-id="7c990-132">Both of the previous examples are equivalent to the following:</span></span>

<span data-ttu-id="7c990-133">[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]</span><span class="sxs-lookup"><span data-stu-id="7c990-133">[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7c990-134">[前へ](structs.md)
[次へ](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="7c990-134">[Previous](structs.md)
[Next](interfaces.md)</span></span>

