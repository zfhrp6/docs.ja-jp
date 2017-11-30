---
title: "破棄 - C# ガイド"
description: "C# の破棄のサポートについて説明します。破棄は、未割り当てで破棄可能な変数です。また、破棄の使用例についても説明します。"
keywords: .NET,.NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 800a27d2d186c738dceb6838aa669377a0c07b01
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="discards---c-guide"></a><span data-ttu-id="3516b-104">破棄 - C# ガイド</span><span class="sxs-lookup"><span data-stu-id="3516b-104">Discards - C# Guide</span></span>

<span data-ttu-id="3516b-105">C# 7 以降、C# は破棄をサポートしています。破棄は、アプリケーション コードで意図的に使用しない一時的なダミー変数です。</span><span class="sxs-lookup"><span data-stu-id="3516b-105">Starting with C# 7, C# supports discards, which are temporary, dummy variables that are intentionally unused in application code.</span></span> <span data-ttu-id="3516b-106">破棄は、未割り当ての変数と同等です。つまり、値がありません。</span><span class="sxs-lookup"><span data-stu-id="3516b-106">Discards are equivalent to unassigned variables; they do not have a value.</span></span> <span data-ttu-id="3516b-107">破棄変数は 1 つのみであり、破棄変数には記憶域も割り当てられないため、破棄を使用するとメモリの割り当てを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="3516b-107">Because there is only a single discard variable, and that variable may not even be allocated storage, discards can reduce memory allocations.</span></span> <span data-ttu-id="3516b-108">また、コードの意図がわかりやすくなるため、読みやすさと保守性が向上します。</span><span class="sxs-lookup"><span data-stu-id="3516b-108">Because they make the intent of your code clear, they enhance its readability and maintainability.</span></span>

<span data-ttu-id="3516b-109">変数を破棄と指定するには、変数名にアンダースコア (`_`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="3516b-109">You indicate that a variable is a discard by assigning it the underscore (`_`) as its name.</span></span> <span data-ttu-id="3516b-110">たとえば、次のメソッド呼び出しが 3 組の最初と 2 番目の値が破棄を返しますと*領域*によって返される対応する 3 番目のコンポーネントに設定する前に宣言された変数は、 *GetCityInformation*:</span><span class="sxs-lookup"><span data-stu-id="3516b-110">For example, the following method call returns a 3-tuple in which the first and second values are discards and *area* is a previously declared variable to be set to the corresponding third component returned by *GetCityInformation*:</span></span>

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

<span data-ttu-id="3516b-111">C# 7 では、破棄は次のコンテキストの割り当てでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3516b-111">In C# 7, discards are supported in assignments in the following contexts:</span></span>

- <span data-ttu-id="3516b-112">タプルとオブジェクトの[分解](deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="3516b-112">Tuple and object [deconstruction](deconstruct.md).</span></span>
- <span data-ttu-id="3516b-113">[is](language-reference/keywords/is.md) と [switch](language-reference/keywords/switch.md) によるパターン マッチング。</span><span class="sxs-lookup"><span data-stu-id="3516b-113">Pattern matching with [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md).</span></span>
- <span data-ttu-id="3516b-114">`out` パラメーターを使用したメソッドの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="3516b-114">Calls to methods with `out` parameters.</span></span>
- <span data-ttu-id="3516b-115">`_` がスコープ内にない場合のスタンドアロンの `_`。</span><span class="sxs-lookup"><span data-stu-id="3516b-115">A standalone `_` when no `_` is in scope.</span></span>

<span data-ttu-id="3516b-116">`_` が有効な破棄の場合、その値を取得しようとすると、または代入演算で使用しようとすると、"名前 '\_' は、現在のコンテキストに存在していません" というコンパイラ エラー CS0301 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3516b-116">When `_` is a valid discard, attempting to retrieve its value or use it in an assignment operation generates compiler error CS0301, "The name '\_' does not exist in the current context".</span></span> <span data-ttu-id="3516b-117">これは、`_` に値が割り当てられておらず、記憶域の場所も割り当てることができないためです。</span><span class="sxs-lookup"><span data-stu-id="3516b-117">This is because `_` is not assigned a value, and may not even be assigned a storage location.</span></span> <span data-ttu-id="3516b-118">実際の変数であれば、前の例のように、複数の値を破棄できません。</span><span class="sxs-lookup"><span data-stu-id="3516b-118">If it were an actual variable, you could not discard more than one value, as the previous example did.</span></span>

## <a name="tuple-and-object-deconstruction"></a><span data-ttu-id="3516b-119">タプルとオブジェクトの分解</span><span class="sxs-lookup"><span data-stu-id="3516b-119">Tuple and object deconstruction</span></span>

<span data-ttu-id="3516b-120">分解は、複数のタプルがあり、アプリケーション コードで一部のタプル要素を使用し、その他の要素を無視する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="3516b-120">Discards are particularly useful in working with tuples when your application code uses some tuple elements but ignores others.</span></span> <span data-ttu-id="3516b-121">たとえば、次の `QueryCityDataForYears` メソッドは、市区町村名、その地域、年、市区町村のその年の人口、2 つ目の年、市区町村のその 2 つ目の年の人口という 6 つのタプルを返します。</span><span class="sxs-lookup"><span data-stu-id="3516b-121">For example, the following `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="3516b-122">この例は、2 つの年の間に変化した人口数を示しています。</span><span class="sxs-lookup"><span data-stu-id="3516b-122">The example shows the change in population between those two years.</span></span> <span data-ttu-id="3516b-123">タプルから使用できるデータのうち、市区町村の地域は使用しません。また、指定時に市区町村名と 2 つの日付はわかっています。</span><span class="sxs-lookup"><span data-stu-id="3516b-123">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="3516b-124">そのため、タプルに格納されている 2 つの人口値のみが必要であり、残りの値は破棄対象として処理できます。</span><span class="sxs-lookup"><span data-stu-id="3516b-124">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="3516b-125">破棄を使用したタプルの分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-tuple-elements-with-discards)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3516b-125">For more information on deconstructing tuples with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-tuple-elements-with-discards).</span></span>

<span data-ttu-id="3516b-126">また、クラス、構造体、またはインターフェイスの `Deconstruct` メソッドを使用すると、オブジェクトから特定セットのデータを取得し、分解することもできます。</span><span class="sxs-lookup"><span data-stu-id="3516b-126">The `Deconstruct` method of a class, structure, or interface also allows you to retrieve and deconstruct a specific set of data from an object.</span></span> <span data-ttu-id="3516b-127">分解された値の一部のみが必要な場合は、破棄を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3516b-127">You can use discards when you are interested in working with only a subset of the deconstructed values.</span></span> <span data-ttu-id="3516b-128">`Person` オブジェクトを 4 つの文字列 (名、姓、市区町村、州) に分解し、姓と州を破棄する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3516b-128">Ihe following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state), but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

<span data-ttu-id="3516b-129">破棄を使用したユーザー定義型の分解の詳細については、「[タプルとその他の型の分解](deconstruct.md#deconstructing-a-user-defined-type-with-discards)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3516b-129">For more information on deconstructing user-defined types with discards, see [Deconstructing tuples and other types](deconstruct.md#deconstructing-a-user-defined-type-with-discards).</span></span>

## <a name="pattern-matching-with-switch-and-is"></a><span data-ttu-id="3516b-130">`switch` と `is` を使用したパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="3516b-130">Pattern matching with `switch` and `is`</span></span>

<span data-ttu-id="3516b-131">*破棄パターン*は、[is](language-reference/keywords/is.md) キーワードと [switch](language-reference/keywords/switch.md) キーワードを使用したパターン マッチングで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3516b-131">The *discard pattern* can be used in pattern matching with the [is](language-reference/keywords/is.md) and [switch](language-reference/keywords/switch.md) keywords.</span></span> <span data-ttu-id="3516b-132">各式は常に破棄パターンと一致します。</span><span class="sxs-lookup"><span data-stu-id="3516b-132">Every expression always matches the discard pattern.</span></span>

<span data-ttu-id="3516b-133">[is](language-reference/keywords/is.md) ステートメントを使用して、オブジェクトが <xref:System.IFormatProvider> 実装を提供しているかどうかを判断し、オブジェクトが `null` かどうかをテストする `ProvidesFormatInfo` メソッドの定義例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3516b-133">The following example defines a `ProvidesFormatInfo` method that uses [is](language-reference/keywords/is.md) statements to determine whether an object provides an <xref:System.IFormatProvider> implementation and tests whether the object is `null`.</span></span> <span data-ttu-id="3516b-134">また、破棄パターンを使用して、その他の任意の型の null 以外のオブジェクトを処理します。</span><span class="sxs-lookup"><span data-stu-id="3516b-134">It also uses the discard pattern to handle non-null objects of any other type.</span></span>

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a><span data-ttu-id="3516b-135">out パラメーターを使用したメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="3516b-135">Calls to methods with out parameters</span></span>

<span data-ttu-id="3516b-136">`Deconstruct` メソッドを呼び出してユーザー定義型 (クラス、構造体、またはインターフェイスのインスタンス) を分解する場合、個々の `out` 引数の値を破棄できます。</span><span class="sxs-lookup"><span data-stu-id="3516b-136">When calling the `Deconstruct` method to deconstruct a user-defined type (an instance of a class, structure, or interface), you can discard the values of individual `out` arguments.</span></span> <span data-ttu-id="3516b-137">また、out パラメーターを指定して任意のメソッドを呼び出すときに、`out` 引数の値を破棄することもできます。</span><span class="sxs-lookup"><span data-stu-id="3516b-137">But you can also discard the value of `out` arguments when calling any method with an out parameter.</span></span> 

<span data-ttu-id="3516b-138">次の例では、[DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) メソッドを呼び出して、現在のカルチャで日付の文字列表現が有効かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3516b-138">The following example calls the [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) method to determine whether the string representation of a date is valid in the current culture.</span></span> <span data-ttu-id="3516b-139">この例では、日付文字列の検証のみが目的で、解析して日付を抽出する処理は行わないため、メソッドの `out` 引数は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="3516b-139">Because the example is concerned only with validating the date string and not with parsing it to extract the date, the `out` argument to the method is a discard.</span></span>

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a><span data-ttu-id="3516b-140">スタンドアロンの破棄</span><span class="sxs-lookup"><span data-stu-id="3516b-140">A standalone discard</span></span>

<span data-ttu-id="3516b-141">スタンドアロンの破棄を使用して、無視対象として任意の変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3516b-141">You can use a standalone discard to indicate any variable that you choose to ignore.</span></span> <span data-ttu-id="3516b-142">次の例では、スタンドアロンの破棄を使用して、非同期操作で返される <xref:System.Threading.Tasks.Task> オブジェクトを無視します。</span><span class="sxs-lookup"><span data-stu-id="3516b-142">The following example uses a standalone discard to ignore the <xref:System.Threading.Tasks.Task> object returned by an asynchronous operation.</span></span> <span data-ttu-id="3516b-143">この結果、この処理が完了するときにスローされる例外が抑制される効果があります。</span><span class="sxs-lookup"><span data-stu-id="3516b-143">This has the effect of suppressing the exception that the operation throws as it is about to complete.</span></span>

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

<span data-ttu-id="3516b-144">`_` は有効な識別子でもある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3516b-144">Note that `_` is also a valid identifier.</span></span> <span data-ttu-id="3516b-145">サポートされるコンテキスト以外で `_` を使用すると、破棄対象ではなく、有効な変数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="3516b-145">When used outside of a supported context, `_` is treated not as a discard but as a valid variable.</span></span> <span data-ttu-id="3516b-146">`_` という識別子が既にスコープ内にある場合、スタンドアロンの破棄として `_` を使用すると、次のような結果になります。</span><span class="sxs-lookup"><span data-stu-id="3516b-146">If an identifier named `_` is already in scope, the use of `_` as a standalone discard can result in:</span></span>

- <span data-ttu-id="3516b-147">意図した破棄の値を割り当てることで、スコープ内の `_` 変数の値が誤って変更される。</span><span class="sxs-lookup"><span data-stu-id="3516b-147">Accidental modification of the value of the in-scope `_` variable by assigning it the value of the intended discard.</span></span> <span data-ttu-id="3516b-148">例:</span><span class="sxs-lookup"><span data-stu-id="3516b-148">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- <span data-ttu-id="3516b-149">タイプ セーフに違反するコンパイラ エラーが発生する。</span><span class="sxs-lookup"><span data-stu-id="3516b-149">A compiler error for violating type safety.</span></span> <span data-ttu-id="3516b-150">例:</span><span class="sxs-lookup"><span data-stu-id="3516b-150">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- <span data-ttu-id="3516b-151">コンパイラ エラー CS0136 "ローカルまたはパラメーター '_' は、その名前が外側のローカルのスコープでローカルやパラメーターの定義に使用されているため、このスコープでは宣言できません" が発生する。</span><span class="sxs-lookup"><span data-stu-id="3516b-151">Compiler error CS0136, "A local or parameter named '_' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter."</span></span> <span data-ttu-id="3516b-152">例:</span><span class="sxs-lookup"><span data-stu-id="3516b-152">For example:</span></span>

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a><span data-ttu-id="3516b-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="3516b-153">See also</span></span>
<span data-ttu-id="3516b-154">[タプルとその他の型の分解](deconstruct.md) </span><span class="sxs-lookup"><span data-stu-id="3516b-154">[Deconstructing tuples and other types](deconstruct.md) </span></span>  
<span data-ttu-id="3516b-155">[`is` キーワード](language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="3516b-155">[`is` keyword](language-reference/keywords/is.md) </span></span>  
[<span data-ttu-id="3516b-156">`switch` キーワード</span><span class="sxs-lookup"><span data-stu-id="3516b-156">`switch` keyword</span></span>](language-reference/keywords/switch.md)   
