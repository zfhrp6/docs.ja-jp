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
# <a name="nullable-operators"></a>Null 許容の演算子

Null 許容の演算子は、1 つまたは両方の側での null 許容の算術型を使用する算術演算または比較の二項演算子です。 Null 許容型は、実際の値の代わりに null を許可するデータベースなどのソースからデータを操作するときに頻繁に発生します。 Null 許容の演算子は、クエリ式でよく使用されます。 算術演算子および比較の null 許容の演算子に加えて、変換演算子を null 許容型の間で変換を使用できます。 特定のクエリ演算子の null 許容バージョンもあります。


## <a name="table-of-nullable-operators"></a>Null 許容の演算子のテーブル
次の表には、f# 言語でサポートされる null 許容の演算子が一覧表示します。

|左側に null 値を許容|右側に null 値を許容|両辺が null 許容型|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>コメント
Null 許容の演算子に含まれる、 [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007)名前空間内のモジュール[Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)です。 Null 許容型のデータの型は`System.Nullable<'T>`します。

クエリ式では、null 許容型は、値の代わりに null 値を許容するデータ ソースからデータを選択するときに発生します。 テーブル内の各データ列では、SQL Server データベースで null 値が許可されるかどうかを示す属性があります。 Null 値が許可されている場合、データベースから返されるデータが null などのプリミティブ データ型で表すことはできませんを含めることができます`int`、`float`のようにします。 データとして返されますそのため、`System.Nullable<int>`の代わりに`int`、および`System.Nullable<float>`の代わりに`float`です。 実際の値を取得できます、`System.Nullable<'T>`オブジェクトを使用して、`Value`プロパティ、およびするかを判別できます、`System.Nullable<'T>`オブジェクトに値を呼び出すことによって、`HasValue`メソッドです。 他の便利な方法は、`System.Nullable<'T>.GetValueOrDefault`メソッドで、値、または適切な型の既定値を取得することができます。 既定値はなんらかの形式の 0 の場合など、「ゼロ」値 0.0、または`false`です。

Null 許容型はなどの通常の変換演算子を使用して、null 非許容のプリミティブ型に変換することがあります`int`または`float`です。 Null 許容型の変換演算子を使用して、1 つの null 許容型から別の null 許容型に変換することもできます。 適切な変換演算子は、標準と同じ名前になりますが、個別のモジュールでは、 [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e)内のモジュール、 [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)名前空間。 通常、クエリ式を使用する場合は、この名前空間を開きます。 プレフィックスを追加することで、null 許容型の変換演算子を使用する場合は、`Nullable.`適切な変換演算子と、次のコードに示すようにします。

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

出力は `10.000000`になります。

など、null 許容型のデータ フィールドの演算子のクエリ`sumByNullable`クエリ式で使用する場合もあります。 非 null 許容型のクエリ演算子はありません、null 許容型で型と互換性のある null 値を許容データ値を使用しているときに、適切なクエリ演算子の null 許容バージョンを使用する必要があります。 詳細については、次を参照してください。[クエリ式](../query-expressions.md)です。

次の例では、f# クエリ式で null 許容の演算子の使用を示します。 最初のクエリは、null 許容の演算子; を使用せず、クエリを記述する方法を示しています。2 番目のクエリは、null 許容の演算子を使用する同等のクエリを示しています。 このサンプル コードを使用するデータベースを設定する方法を含む、完全コンテキストを参照してください。[チュートリアル: 型プロバイダーを使用して SQL データベースへのアクセス](../../tutorials/type-providers/accessing-a-sql-database.md)です。

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

## <a name="see-also"></a>関連項目

[型プロバイダー](../../tutorials/type-providers/index.md)

[クエリ式](../query-expressions.md)
