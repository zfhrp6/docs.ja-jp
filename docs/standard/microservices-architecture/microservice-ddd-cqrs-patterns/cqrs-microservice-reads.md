---
title: CQRS マイクロサービスに読み取り/クエリを実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | CQRS マイクロサービスに読み取り/クエリを実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.openlocfilehash: 8eca01acc2308097d1684be8bdb0f07edd86832f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579107"
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="f55fe-103">CQRS マイクロサービスに読み取り/クエリを実装する</span><span class="sxs-lookup"><span data-stu-id="f55fe-103">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="f55fe-104">読み取り/クエリの場合、eShopOnContainers 参照アプリケーションのオーダリング マイクロサービスでは、DDD モデルおよびトランザクション領域とは別にクエリを実装します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="f55fe-105">この主な理由は、クエリとトランザクションの要求が大幅に異なるためです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="f55fe-106">書き込みでは、ドメイン ロジックに準拠する必要があるトランザクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="f55fe-107">一方、クエリはべき等であり、ドメイン ルールから分離することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="f55fe-108">図 9-3 に示すように、方法は単純です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-108">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="f55fe-109">API インターフェイスは、Dapper のようなマイクロ オブジェクト リレーショナル マッパー (ORM) などの任意のインフラストラクチャを使用して、UI アプリケーションのニーズに応じて動的な ViewModel を返すことで Web API コントローラーによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="f55fe-110">**図 9-3**</span><span class="sxs-lookup"><span data-stu-id="f55fe-110">**Figure 9-3**.</span></span> <span data-ttu-id="f55fe-111">CQRS マイクロサービスでのクエリの最も単純な方法</span><span class="sxs-lookup"><span data-stu-id="f55fe-111">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="f55fe-112">これがクエリの最も単純な方法と考えられます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-112">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="f55fe-113">クエリ定義ではデータベースをクエリし、各クエリに対してオンザフライでビルドされた動的な ViewModel を返します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-113">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="f55fe-114">クエリはべき等であるため、クエリの実行回数に関係なく、データが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="f55fe-114">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="f55fe-115">したがって、トランザクション側で使用される DDD パターン (集計などのパターン) によって制限される必要はありません。これが、クエリがトランザクション領域から分離される理由です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-115">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="f55fe-116">UI に必要なデータについてデータベースをクエリし、SQL ステートメント自体を除く、任意の場所 (ViewModel のクラスがない) で静的に定義する必要のない動的な ViewModel を返すだけです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-116">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="f55fe-117">これは単純な方法であるため、クエリ側で必要なコード ([Dapper](https://github.com/StackExchange/Dapper) のようなマイクロ ORM を使用するコードなど) を[同じ Web API プロジェクト内で](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)実装することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-117">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="f55fe-118">これは図 9-4 に示されています。</span><span class="sxs-lookup"><span data-stu-id="f55fe-118">Figure 9-4 shows this.</span></span> <span data-ttu-id="f55fe-119">クエリは eShopOnContainers 内の **Ordering.API** マイクロサービス プロジェクトで定義されています。</span><span class="sxs-lookup"><span data-stu-id="f55fe-119">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="f55fe-120">**図 9-4**</span><span class="sxs-lookup"><span data-stu-id="f55fe-120">**Figure 9-4**.</span></span> <span data-ttu-id="f55fe-121">eShopOnContainers でのオーダリング マイクロサービスのクエリ</span><span class="sxs-lookup"><span data-stu-id="f55fe-121">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="f55fe-122">ドメイン モデル制約とは別の、クライアント アプリ専用の ViewModel の使用</span><span class="sxs-lookup"><span data-stu-id="f55fe-122">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="f55fe-123">クエリはクライアント アプリケーションで必要なデータを取得するために実行されるため、戻り値の型は、クエリによって返されるデータに基づいて、クライアント専用に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-123">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="f55fe-124">これらのモデル、またはデータ転送オブジェクト (DTO)、は ViewModel と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-124">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="f55fe-125">返されるデータ (ViewModel) は、データベースの複数のエンティティまたはテーブルからの、あるいはトランザクション領域のドメイン モデルで定義されている複数の集計全体のデータの結合結果である場合があります。</span><span class="sxs-lookup"><span data-stu-id="f55fe-125">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="f55fe-126">ここでは、ドメイン モデルには依存しないクエリを作成するため、集計の境界と制約は完全に無視され、必要になる可能性のあるテーブルと列をクエリするのは自由です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-126">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="f55fe-127">この方法では、開発者がクエリの作成または更新を行う場合に優れた柔軟性と生産性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-127">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="f55fe-128">ViewModel として、クラスで定義されている静的な型を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-128">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="f55fe-129">または、実行 (オーダリング マイクロサービスで実装) されたクエリに基づいて動的に作成することもできます。これは、開発者にとって非常にアジャイルな方法です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-129">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="f55fe-130">クエリを実行するためのマイクロ ORM としての Dapper の使用</span><span class="sxs-lookup"><span data-stu-id="f55fe-130">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="f55fe-131">クエリでは、任意のマイクロ ORM、Entity Framework Core、またはプレーン ADO.NET を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-131">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="f55fe-132">サンプル アプリケーションでは、一般的なマイクロ ORM の良い例として、eShopOnContainers でのオーダリング マイクロサービスに対して Dapper が選択されました。</span><span class="sxs-lookup"><span data-stu-id="f55fe-132">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="f55fe-133">これは非常に軽量なフレームワークであるため、パフォーマンスの優れたプレーン SQL クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-133">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="f55fe-134">Dapper を使用することで、複数のテーブルのアクセスと結合が可能な SQL クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-134">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="f55fe-135">Dapper はオープンソースのプロジェクト (Sam Saffron によって最初に作成された) であり、[スタック オーバーフロー](https://stackoverflow.com/)で使用される構成要素の一部です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-135">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="f55fe-136">Dapper を使用するために必要になるのは、次の図に示すように、[Dapper NuGet パッケージ](https://www.nuget.org/packages/Dapper)を使用してインストールすることだけです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-136">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="f55fe-137">コードで Dapper 拡張メソッドにアクセスできるようにするために、ステートメントを追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f55fe-137">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="f55fe-138">コードで Dapper を使用する場合は、<xref:System.Data.SqlClient> 名前空間で使用可能な <xref:System.Data.SqlClient.SqlConnection> クラスを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-138">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="f55fe-139">QueryAsync メソッドと、<xref:System.Data.SqlClient.SqlConnection> クラスを拡張するその他の拡張メソッドを使用して、簡単でパフォーマンスの高い方法でクエリを実行するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-139">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="f55fe-140">動的な ViewModel と静的な ViewModel</span><span class="sxs-lookup"><span data-stu-id="f55fe-140">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="f55fe-141">ViewModel をサーバー側からクライアント アプリに返す場合、エンティティ モデルの内部ドメイン エンティティとは異なる可能性のある DTO として ViewModel について考えることができます。これは、ViewModel がクライアント アプリで必要な方法でデータを保持するためです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-141">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="f55fe-142">したがって、多くの場合、複数のドメイン エンティティからのデータを集計し、クライアント アプリでそのデータがいかに必要であるかに従って ViewModel を正確に構成できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-142">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="f55fe-143">これらの ViewModel または DTO は、後述のコード スニペットで示す [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) クラスと同様に (データ ホルダー クラスとして) 明示的に定義できます。あるいは、`dynamic` 型として、クエリによって返される属性に基づいて、単に動的な ViewModel または動的な DTO を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-143">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="f55fe-144">動的な型としての ViewModel</span><span class="sxs-lookup"><span data-stu-id="f55fe-144">ViewModel as dynamic type</span></span>

<span data-ttu-id="f55fe-145">次のコードに示すように、ViewModel は、内部的にクエリによって返される属性に基づく動的な型を返すことで、クエリで直接返すことができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-145">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="f55fe-146">これは、返される属性のサブセットがクエリ自体に基づいていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-146">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="f55fe-147">そのため、クエリまたは結合に新しい列を追加する場合、そのデータは返される ViewModel に動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-147">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="f55fe-148">重要な点は、動的な型を使用することで、返されるデータ コレクションが ViewModel として動的にアセンブルされることです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-148">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="f55fe-149">*長所:* この方法では、クエリの SQL 文を更新するたびに静的な ViewModel クラスを変更する必要性が低くなります。したがって、この設計方法は非常にアジャイルなコーディング方法であり、簡単で、将来の変更に合わせてすばやく進化します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-149">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="f55fe-150">*短所:* 長期的に見ると、動的な型は明確性に悪影響を与える可能性があり、また、クライアント アプリとのサービスの互換性に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f55fe-150">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="f55fe-151">さらに、Swagger のようなミドルウェア ソフトウェアでは、動的な型を使用する場合に戻り値の型で同じレベルのドキュメントを提供できません。</span><span class="sxs-lookup"><span data-stu-id="f55fe-151">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="f55fe-152">定義済み DTO クラスとしての ViewModel</span><span class="sxs-lookup"><span data-stu-id="f55fe-152">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="f55fe-153">*長所:* 明示的な DTO クラスに基づく "コントラクト" のように、静的な定義済み ViewModel クラスを使用することは、パブリック API だけでなく、長期的なマイクロサービスでも確実に適しています。同じアプリケーションでのみ使用される場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-153">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="f55fe-154">Swagger の応答型を指定する場合は、戻り値の型として明示的な DTO クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f55fe-154">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="f55fe-155">したがって、定義済み DTO クラスを使用すれば、Swagger からより豊富な情報を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-155">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="f55fe-156">これにより、API 利用時の API のドキュメントと互換性が改善されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-156">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="f55fe-157">*短所:* 前述のとおり、コードを更新する場合、DTO クラスを更新するためにさらにいくつかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-157">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="f55fe-158">*経験に基づくヒント:* eShopOnContainers のオーダリング マイクロサービスで実装されたクエリでは、初期の開発段階において非常に簡単でアジャイルであるため、動的な ViewModel を使用して開発を開始しました。</span><span class="sxs-lookup"><span data-stu-id="f55fe-158">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="f55fe-159">しかし、開発が安定した後で、API をリファクタリングし、ViewModel に静的な、または定義済みの DTO を使用することにしました。これは、マイクロサービスのコンシューマーが、"コントラクト" として使用される、明示的な DTO 型を認識しやすいためです。</span><span class="sxs-lookup"><span data-stu-id="f55fe-159">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="f55fe-160">次の例では、明示的な ViewModel DTO クラスである OrderSummary クラスを使用して、クエリでどのようにデータが返されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-160">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<dynamic>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="f55fe-161">Web API の応答型の説明</span><span class="sxs-lookup"><span data-stu-id="f55fe-161">Describing response types of Web APIs</span></span>

<span data-ttu-id="f55fe-162">Web API とマイクロサービスを利用する開発者は、何が返されるか (具体的には、応答型とエラー コード (標準以外の場合)) を最も考慮します。</span><span class="sxs-lookup"><span data-stu-id="f55fe-162">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="f55fe-163">これらは、XML のコメントおよびデータ注釈で処理されます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-163">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="f55fe-164">Swagger UI に適切なドキュメントがないと、コンシューマーは返される型や返される可能性のある HTTP コードを認識できません。</span><span class="sxs-lookup"><span data-stu-id="f55fe-164">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="f55fe-165">この問題は <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> を追加することで解決されるため、次のコードに示すように、Swagger は API の戻りモデルと値に関するより豊富な情報を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-165">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
       //Additional code...
       [Route("")]
       [HttpGet]
       [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
                             (int)HttpStatusCode.OK)]
       public async Task<IActionResult> GetOrders()
       {
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

<span data-ttu-id="f55fe-166">ただし、`ProducesResponseType` 属性では型として動的な型を使用できず、次の例に示すように、`OrderSummary` ViewModel DTO などの明示的な型を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f55fe-166">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="f55fe-167">これが、長期的に見ると、明示的な戻り値の型が動的な型より適しているもう 1 つの理由です。</span><span class="sxs-lookup"><span data-stu-id="f55fe-167">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="f55fe-168">`ProducesResponseType` 属性を使用する場合、考えられる HTTP エラー/コード (200、400 など) について予期される結果を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-168">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="f55fe-169">次のイメージで、Swagger UI にどのように ResponseType 情報が表示されるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-169">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="f55fe-170">**図 9-5**</span><span class="sxs-lookup"><span data-stu-id="f55fe-170">**Figure 9-5**.</span></span> <span data-ttu-id="f55fe-171">Web API からの応答型と考えられる HTTP ステータス コードを示す Swagger UI</span><span class="sxs-lookup"><span data-stu-id="f55fe-171">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="f55fe-172">上のイメージでは、ViewModel 型に基づくいくつかの値の例と、返される可能性のある HTTP ステータス コードを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f55fe-172">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f55fe-173">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f55fe-173">Additional resources</span></span>

-   <span data-ttu-id="f55fe-174">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="f55fe-174">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="f55fe-175">**Julie Lerman。データ ポイント - Dapper、Entity Framework、およびハイブリッド アプリ (MSDN マガジンの記事)**</span><span class="sxs-lookup"><span data-stu-id="f55fe-175">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    *https://msdn.microsoft.com/magazine/mt703432.aspx*

-   <span data-ttu-id="f55fe-176">**Swagger を使用する ASP.NET Core Web API のヘルプ ページ**</span><span class="sxs-lookup"><span data-stu-id="f55fe-176">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    *https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*

>[!div class="step-by-step"]
<span data-ttu-id="f55fe-177">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="f55fe-177">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
