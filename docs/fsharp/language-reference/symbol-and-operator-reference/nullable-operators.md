---
title: Null 許容の演算子 (F#)
description: F# のプログラミング言語で使用できる null 許容の演算子について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 37025e16768b949b51f6b9f0cff32e88da110ca8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="nullable-operators"></a><span data-ttu-id="088e8-103">Null 許容の演算子</span><span class="sxs-lookup"><span data-stu-id="088e8-103">Nullable Operators</span></span>

<span data-ttu-id="088e8-104">Null 許容の演算子は、1 つまたは両方の側での null 許容の算術型を使用する算術演算または比較の二項演算子です。</span><span class="sxs-lookup"><span data-stu-id="088e8-104">Nullable operators are binary arithmetic or comparison operators that work with nullable arithmetic types on one or both sides.</span></span> <span data-ttu-id="088e8-105">Null 許容型は、実際の値の代わりに null を許可するデータベースなどのソースからデータを操作するときに頻繁に発生します。</span><span class="sxs-lookup"><span data-stu-id="088e8-105">Nullable types arise frequently when you work with data from sources such as databases that allow nulls in place of actual values.</span></span> <span data-ttu-id="088e8-106">Null 許容の演算子は、クエリ式でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="088e8-106">Nullable operators are used frequently in query expressions.</span></span> <span data-ttu-id="088e8-107">算術演算子および比較の null 許容の演算子に加えて、変換演算子を null 許容型の間で変換を使用できます。</span><span class="sxs-lookup"><span data-stu-id="088e8-107">In addition to nullable operators for arithmetic and comparison, conversion operators can be used to convert between nullable types.</span></span> <span data-ttu-id="088e8-108">特定のクエリ演算子の null 許容バージョンもあります。</span><span class="sxs-lookup"><span data-stu-id="088e8-108">There are also nullable versions of certain query operators.</span></span>


## <a name="table-of-nullable-operators"></a><span data-ttu-id="088e8-109">Null 許容の演算子のテーブル</span><span class="sxs-lookup"><span data-stu-id="088e8-109">Table of Nullable Operators</span></span>
<span data-ttu-id="088e8-110">次の表には、f# 言語でサポートされる null 許容の演算子が一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="088e8-110">The following table lists nullable operators supported in the F# language.</span></span>

|<span data-ttu-id="088e8-111">左側に null 値を許容</span><span class="sxs-lookup"><span data-stu-id="088e8-111">Nullable on left</span></span>|<span data-ttu-id="088e8-112">右側に null 値を許容</span><span class="sxs-lookup"><span data-stu-id="088e8-112">Nullable on right</span></span>|<span data-ttu-id="088e8-113">両辺が null 許容型</span><span class="sxs-lookup"><span data-stu-id="088e8-113">Both sides nullable</span></span>|
|---|---|---|
|[<span data-ttu-id="088e8-114">?>=</span><span class="sxs-lookup"><span data-stu-id="088e8-114">?>=</span></span>](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[<span data-ttu-id="088e8-115">>=?</span><span class="sxs-lookup"><span data-stu-id="088e8-115">>=?</span></span>](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[<span data-ttu-id="088e8-116">?>=?</span><span class="sxs-lookup"><span data-stu-id="088e8-116">?>=?</span></span>](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[<span data-ttu-id="088e8-117">?></span><span class="sxs-lookup"><span data-stu-id="088e8-117">?></span></span>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[<span data-ttu-id="088e8-118">>?</span><span class="sxs-lookup"><span data-stu-id="088e8-118">>?</span></span>](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[<span data-ttu-id="088e8-119">?>?</span><span class="sxs-lookup"><span data-stu-id="088e8-119">?>?</span></span>](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[<span data-ttu-id="088e8-120">?<=</span><span class="sxs-lookup"><span data-stu-id="088e8-120">?<=</span></span>](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<span data-ttu-id="088e8-121"><=?</span><span class="sxs-lookup"><span data-stu-id="088e8-121"><=?</span></span>](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[<span data-ttu-id="088e8-122">?<=?</span><span class="sxs-lookup"><span data-stu-id="088e8-122">?<=?</span></span>](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[<span data-ttu-id="088e8-123">?<</span><span class="sxs-lookup"><span data-stu-id="088e8-123">?<</span></span>](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<span data-ttu-id="088e8-124"><?</span><span class="sxs-lookup"><span data-stu-id="088e8-124"><?</span></span>](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[<span data-ttu-id="088e8-125">?<?</span><span class="sxs-lookup"><span data-stu-id="088e8-125">?<?</span></span>](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[<span data-ttu-id="088e8-126">?=</span><span class="sxs-lookup"><span data-stu-id="088e8-126">?=</span></span>](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[<span data-ttu-id="088e8-127">=?</span><span class="sxs-lookup"><span data-stu-id="088e8-127">=?</span></span>](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[<span data-ttu-id="088e8-128">?=?</span><span class="sxs-lookup"><span data-stu-id="088e8-128">?=?</span></span>](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[<span data-ttu-id="088e8-129">?<></span><span class="sxs-lookup"><span data-stu-id="088e8-129">?<></span></span>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<span data-ttu-id="088e8-130"><>?</span><span class="sxs-lookup"><span data-stu-id="088e8-130"><>?</span></span>](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[<span data-ttu-id="088e8-131">?<>?</span><span class="sxs-lookup"><span data-stu-id="088e8-131">?<>?</span></span>](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[<span data-ttu-id="088e8-132">?+</span><span class="sxs-lookup"><span data-stu-id="088e8-132">?+</span></span>](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[<span data-ttu-id="088e8-133">+?</span><span class="sxs-lookup"><span data-stu-id="088e8-133">+?</span></span>](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[<span data-ttu-id="088e8-134">?+?</span><span class="sxs-lookup"><span data-stu-id="088e8-134">?+?</span></span>](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[<span data-ttu-id="088e8-135">?-</span><span class="sxs-lookup"><span data-stu-id="088e8-135">?-</span></span>](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[<span data-ttu-id="088e8-136">-?</span><span class="sxs-lookup"><span data-stu-id="088e8-136">-?</span></span>](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[<span data-ttu-id="088e8-137">?-?</span><span class="sxs-lookup"><span data-stu-id="088e8-137">?-?</span></span>](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[<span data-ttu-id="088e8-138">?\*</span><span class="sxs-lookup"><span data-stu-id="088e8-138">?\*</span></span>](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[<span data-ttu-id="088e8-139">\*?</span><span class="sxs-lookup"><span data-stu-id="088e8-139">\*?</span></span>](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[<span data-ttu-id="088e8-140">?\*?</span><span class="sxs-lookup"><span data-stu-id="088e8-140">?\*?</span></span>](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[<span data-ttu-id="088e8-141">?/</span><span class="sxs-lookup"><span data-stu-id="088e8-141">?/</span></span>](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[<span data-ttu-id="088e8-142">/?</span><span class="sxs-lookup"><span data-stu-id="088e8-142">/?</span></span>](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[<span data-ttu-id="088e8-143">?/?</span><span class="sxs-lookup"><span data-stu-id="088e8-143">?/?</span></span>](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[<span data-ttu-id="088e8-144">?%</span><span class="sxs-lookup"><span data-stu-id="088e8-144">?%</span></span>](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[<span data-ttu-id="088e8-145">%?</span><span class="sxs-lookup"><span data-stu-id="088e8-145">%?</span></span>](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[<span data-ttu-id="088e8-146">?%?</span><span class="sxs-lookup"><span data-stu-id="088e8-146">?%?</span></span>](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a><span data-ttu-id="088e8-147">コメント</span><span class="sxs-lookup"><span data-stu-id="088e8-147">Remarks</span></span>
<span data-ttu-id="088e8-148">Null 許容の演算子に含まれる、 [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007)名前空間内のモジュール[Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)です。</span><span class="sxs-lookup"><span data-stu-id="088e8-148">The nullable operators are included in the [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) module in the namespace [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d).</span></span> <span data-ttu-id="088e8-149">Null 許容型のデータの型は`System.Nullable<'T>`します。</span><span class="sxs-lookup"><span data-stu-id="088e8-149">The type for nullable data is `System.Nullable<'T>`.</span></span>

<span data-ttu-id="088e8-150">クエリ式では、null 許容型は、値の代わりに null 値を許容するデータ ソースからデータを選択するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="088e8-150">In query expressions, nullable types arise when selecting data from a data source that allows nulls instead of values.</span></span> <span data-ttu-id="088e8-151">テーブル内の各データ列では、SQL Server データベースで null 値が許可されるかどうかを示す属性があります。</span><span class="sxs-lookup"><span data-stu-id="088e8-151">In a SQL Server database, each data column in a table has an attribute that indicates whether nulls are allowed.</span></span> <span data-ttu-id="088e8-152">Null 値が許可されている場合、データベースから返されるデータが null などのプリミティブ データ型で表すことはできませんを含めることができます`int`、`float`のようにします。</span><span class="sxs-lookup"><span data-stu-id="088e8-152">If nulls are allowed, the data returned from the database can contain nulls that cannot be represented by a primitive data type such as `int`, `float`, and so on.</span></span> <span data-ttu-id="088e8-153">データとして返されますそのため、`System.Nullable<int>`の代わりに`int`、および`System.Nullable<float>`の代わりに`float`です。</span><span class="sxs-lookup"><span data-stu-id="088e8-153">Therefore, the data is returned as a `System.Nullable<int>` instead of `int`, and `System.Nullable<float>` instead of `float`.</span></span> <span data-ttu-id="088e8-154">実際の値を取得できます、`System.Nullable<'T>`オブジェクトを使用して、`Value`プロパティ、およびするかを判別できます、`System.Nullable<'T>`オブジェクトに値を呼び出すことによって、`HasValue`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="088e8-154">The actual value can be obtained from a `System.Nullable<'T>` object by using the `Value` property, and you can determine if a `System.Nullable<'T>` object has a value by calling the `HasValue` method.</span></span> <span data-ttu-id="088e8-155">他の便利な方法は、`System.Nullable<'T>.GetValueOrDefault`メソッドで、値、または適切な型の既定値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="088e8-155">Another useful method is the `System.Nullable<'T>.GetValueOrDefault` method, which allows you to get the value or a default value of the appropriate type.</span></span> <span data-ttu-id="088e8-156">既定値はなんらかの形式の 0 の場合など、「ゼロ」値 0.0、または`false`です。</span><span class="sxs-lookup"><span data-stu-id="088e8-156">The default value is some form of "zero" value, such as 0, 0.0, or `false`.</span></span>

<span data-ttu-id="088e8-157">Null 許容型はなどの通常の変換演算子を使用して、null 非許容のプリミティブ型に変換することがあります`int`または`float`です。</span><span class="sxs-lookup"><span data-stu-id="088e8-157">Nullable types may be converted to non-nullable primitive types using the usual conversion operators such as `int` or `float`.</span></span> <span data-ttu-id="088e8-158">Null 許容型の変換演算子を使用して、1 つの null 許容型から別の null 許容型に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="088e8-158">It is also possible to convert from one nullable type to another nullable type by using the conversion operators for nullable types.</span></span> <span data-ttu-id="088e8-159">適切な変換演算子は、標準と同じ名前になりますが、個別のモジュールでは、 [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e)内のモジュール、 [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)名前空間。</span><span class="sxs-lookup"><span data-stu-id="088e8-159">The appropriate conversion operators have the same name as the standard ones, but they are in a separate module, the [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) module in the [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) namespace.</span></span> <span data-ttu-id="088e8-160">通常、クエリ式を使用する場合は、この名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="088e8-160">Typically, you open this namespace when working with query expressions.</span></span> <span data-ttu-id="088e8-161">プレフィックスを追加することで、null 許容型の変換演算子を使用する場合は、`Nullable.`適切な変換演算子と、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="088e8-161">In that case, you can use the nullable conversion operators by adding the prefix `Nullable.` to the appropriate conversion operator, as shown in the following code.</span></span>

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

<span data-ttu-id="088e8-162">出力は `10.000000`になります。</span><span class="sxs-lookup"><span data-stu-id="088e8-162">The output is `10.000000`.</span></span>

<span data-ttu-id="088e8-163">など、null 許容型のデータ フィールドの演算子のクエリ`sumByNullable`クエリ式で使用する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="088e8-163">Query operators on nullable data fields, such as `sumByNullable`, also exist for use in query expressions.</span></span> <span data-ttu-id="088e8-164">非 null 許容型のクエリ演算子はありません、null 許容型で型と互換性のある null 値を許容データ値を使用しているときに、適切なクエリ演算子の null 許容バージョンを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="088e8-164">The query operators for non-nullable types are not type-compatible with nullable types, so you must use the nullable version of the appropriate query operator when you are working with nullable data values.</span></span> <span data-ttu-id="088e8-165">詳細については、次を参照してください。[クエリ式](../query-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="088e8-165">For more information, see [Query Expressions](../query-expressions.md).</span></span>

<span data-ttu-id="088e8-166">次の例では、f# クエリ式で null 許容の演算子の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="088e8-166">The following example shows the use of nullable operators in an F# query expression.</span></span> <span data-ttu-id="088e8-167">最初のクエリは、null 許容の演算子; を使用せず、クエリを記述する方法を示しています。2 番目のクエリは、null 許容の演算子を使用する同等のクエリを示しています。</span><span class="sxs-lookup"><span data-stu-id="088e8-167">The first query shows how you would write a query without a nullable operator; the second query shows an equivalent query that uses a nullable operator.</span></span> <span data-ttu-id="088e8-168">このサンプル コードを使用するデータベースを設定する方法を含む、完全コンテキストを参照してください。[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](../../tutorials/type-providers/accessing-a-sql-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="088e8-168">For the full context, including how to set up the database to use this sample code, see [Walkthrough: Accessing a SQL Database by Using Type Providers](../../tutorials/type-providers/accessing-a-sql-database.md).</span></span>

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a><span data-ttu-id="088e8-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="088e8-169">See Also</span></span>

[<span data-ttu-id="088e8-170">型プロバイダー</span><span class="sxs-lookup"><span data-stu-id="088e8-170">Type Providers</span></span>](../../tutorials/type-providers/index.md)

[<span data-ttu-id="088e8-171">クエリ式</span><span class="sxs-lookup"><span data-stu-id="088e8-171">Query Expressions</span></span>](../query-expressions.md)
