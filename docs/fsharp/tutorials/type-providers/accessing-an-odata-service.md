---
title: "チュートリアル : 型プロバイダーを使用した OData サービスへのアクセス (F#)"
description: "F# 3.0 で f# ODataService 型プロバイダーを使用して、OData サービスのクライアント型を生成する方法を学習し、クエリできるデータ フィードをサービスを提供します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 750407c36a989cece30c0c0654ff905c8eee3b33
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>チュートリアル : 型プロバイダーを使用した OData サービスへのアクセス

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](https://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

OData (Open Data Protocol) は、インターネットでデータを転送するためのプロトコルです。 多くのデータ プロバイダーが、OData Web サービスを公開してデータへのアクセスを提供しています。 F# 3.0 では、`ODataService` 型プロバイダーによって自動生成されるデータ型を使用して、どの OData ソースからでもデータにアクセスできます。 OData の詳細については、https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62 を参照してください。

このチュートリアルでは、F# ODataService 型プロバイダーを使用して、OData サービスのクライアント型を生成し、サービスが提供するデータ フィードを照会する方法を示します。

このチュートリアルでは以下のタスクについて説明します。このチュートリアルを正しく行うには、これらのタスクを順に行ってください。


- OData サービスのクライアント プロジェクトの構成
<br />

- OData 型へのアクセス
<br />

- OData サービスの照会
<br />

- OData 要求の確認
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>OData サービスのクライアント プロジェクトの構成
この手順では、OData 型プロバイダーを使用するようにプロジェクトを設定します。


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>OData サービスのクライアント プロジェクトを構成するには

- F# コンソール アプリケーション プロジェクトを開き、`System.Data.Services.Client` Framework アセンブリへの参照を追加します。
<br />

- `Extensions`への参照を追加、`FSharp.Data.TypeProviders`アセンブリ。
<br />

## <a name="accessing-odata-types"></a>OData 型へのアクセス
この手順では、OData サービスの型とデータへのアクセスを提供する型プロバイダーを作成します。


#### <a name="to-access-odata-types"></a>OData 型にアクセスするには

- コード エディターで、F# ソース ファイルを開いて次のコードを入力します。
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"https://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

この例では、F# 型プロバイダーを呼び出し、指定した OData URI に基づく一連の型を生成するように指示しました。 データに関する情報を含む 2 つのオブジェクトを使用できます。この例では、1 つは簡易データ コンテキストの `db` です。 このオブジェクトには、テーブルやフィードの型を含む、データベースに関連付けられているデータ型だけが含まれています。 この例の、もう 1 つのオブジェクト `fullContext` は `System.Data.Linq.DataContext` のインスタンスで、追加のプロパティ、メソッド、イベントなどが多数含まれています。
<br />


## <a name="querying-an-odata-service"></a>OData サービスの照会
この手順では、F# クエリ式を使用して OData サービスを照会します。


#### <a name="to-query-an-odata-service"></a>OData サービスに照会するには

1. 型プロバイダーを設定したので、OData サービスを照会できます。
<br />  OData は、使用可能なクエリ操作の一部のみをサポートしています。 次の操作と対応するキーワードがサポートされています。
<br />
  - プロジェクション (`select`)
<br />

  - フィルター処理 (`where`、文字列演算と日付演算を使用)
<br />

  - ページング (`skip`、`take`)
<br />

  - 順序付け (`orderBy`、`thenBy`)
<br />

  - `AddQueryOption` および `Expand` (OData 固有の演算)
<br />

  詳細については、次を参照してください。 [LINQ に関する留意点 &#40;です。WCF Data Services &#41;](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  フィードまたはテーブルのすべてのエントリが必要な場合は、次のコードのように、クエリ式の最も単純な形式を使用してください。
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. select キーワードの後にタプルを使用して、必要なフィールドまたは列を指定します。
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. `where` 句を使用して、条件を指定します。
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. `System.String.Contains(System.String)` メソッドを使用して、クエリに部分文字列の条件を指定します。 次のクエリは、名前に "Chef" を含むすべての製品を返します。 また、`System.Nullable<'T>.GetValueOrDefault()` の使い方にも注目してください。 `UnitPrice` は null 許容値であるため、`Value` プロパティを使用して値を取得するか、`System.Nullable<'T>.GetValueOrDefault()` を呼び出す必要があります。
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. 文字列が特定の部分文字列で終わるように指定するには、`System.String.EndsWith(System.String)` メソッドを使用します。
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. `&&` 演算子を使用して、where 句で条件を組み合わせます。
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

演算子 `?>` と `?<` は null 許容の演算子です。 null 許容の等価演算子と比較演算子をすべて使用できます。 詳細については、次を参照してください。 [Linq.NullableOperators モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)です。
<br />

7. 順序付けを指定するには `sortBy` クエリ演算子を使用し、さらにもう 1 レベル順序付けを指定するには `thenBy` を使用します。 クエリの select 部分にタプルが使用されている点にも注目してください。 したがって、クエリには要素型としてタプルが含まれています。
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. skip 演算子を使用して、指定した数のレコードを無視し、take 演算子を使用して、返すレコードの数を指定します。 この方法で、データ フィードにページングを実装できます。
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>OData 要求の確認
OData のすべてのクエリは、特定の OData 要求 URI に変換されます。 完全なデータ コンテキスト オブジェクトの `SendingRequest` イベントにイベント ハンドラーを追加することによって、デバッグなどを行うためにその URI を確認できます。


#### <a name="to-verify-the-odata-request"></a>OData 要求を確認するには

- OData 要求 URI を確認するには、次のコードを使用します。
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

前のコードの出力は次のようになります。
<br />`requesting https://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>参照
[クエリ式](../../language-reference/query-expressions.md)

[LINQ に関する留意点 (WCF Data Services)](https://msdn.microsoft.com/library/ee622463.aspx)

[ODataService 型プロバイダー (f#)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
