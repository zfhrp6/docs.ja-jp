---
title: "CQRS マイクロ サービスでの読み取り]、[クエリの実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |CQRS マイクロ サービスでの読み取り]、[クエリの実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="1b9b2-104">CQRS マイクロ サービスでの読み取り]、[クエリの実装</span><span class="sxs-lookup"><span data-stu-id="1b9b2-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="1b9b2-105">読み取り/クエリでは、eShopOnContainers の参照をアプリケーションから順序マイクロ サービスは DDD モデルと領域をトランザクションから独立してクエリを実装します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="1b9b2-106">これは、クエリおよびトランザクションの要求が大幅に異なるため、主にします。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="1b9b2-107">書き込みは、ドメイン ロジックに準拠する必要があるトランザクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="1b9b2-108">クエリ、その一方で、べき等なので、ドメイン ルールから分離できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="1b9b2-109">アプローチは、図 9-3 に示すように単純です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="1b9b2-110">Web API コント ローラー (micro Dapper などの ORM) などの任意のインフラストラクチャを使用し、UI アプリケーションのニーズに応じて動的 ViewModels を返すことによって、API インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="1b9b2-111">**図 9-3**です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-111">**Figure 9-3**.</span></span> <span data-ttu-id="1b9b2-112">CQRS マイクロ サービスでのクエリの最も簡単な方法</span><span class="sxs-lookup"><span data-stu-id="1b9b2-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="1b9b2-113">これは、クエリの最も簡単な方法をも考えられます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="1b9b2-114">クエリの定義は、データベースを照会し、各クエリに対してその場で構築された動的 ViewModel を返します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="1b9b2-115">クエリでは、べき等であるため、クエリを実行する回数に関係なく、データは変更されません。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="1b9b2-116">したがって、集計およびその他のパターンと同様に、トランザクションの側で使用される任意の DDD パターンにより制限を適用する必要はありません、ため、クエリは、トランザクション領域から区切られます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="1b9b2-117">単に、UI が必要なデータをデータベースに照会し、静的にする必要のない動的 ViewModel で定義されている任意の場所 (、ViewModels のクラスを持たない) を除く SQL ステートメント自体を返します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="1b9b2-118">クエリ側のコードに必要なので、これは、単純な方法で (などの ORM マイクロを使用してコードをなど[Dapper](https://github.com/StackExchange/Dapper)) を実装する[同じ Web API プロジェクト内で](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="1b9b2-119">図 9-4 では、これを示します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="1b9b2-120">クエリが定義されている、 **Ordering.API** eShopOnContainers ソリューション内のマイクロ サービスのプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="1b9b2-121">**図 9-4**です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-121">**Figure 9-4**.</span></span> <span data-ttu-id="1b9b2-122">EShopOnContainers で順序付けマイクロ サービス内のクエリ</span><span class="sxs-lookup"><span data-stu-id="1b9b2-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="1b9b2-123">具体的には、ドメイン モデルの制約から独立してクライアント アプリに対して行われた ViewModels を使用します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="1b9b2-124">クライアント アプリケーションで必要なデータを取得するためには、クエリが実行、ので、クエリによって返されるデータに基づいて、クライアントの戻り値の型を具体的には作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="1b9b2-125">これらのモデル、またはデータ転送オブジェクト (Dto) は、ViewModels と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="1b9b2-126">返されるデータ (ViewModel) は、データベース、またはトランザクションの領域のドメイン モデルで定義されている複数の集計が異なる場合でも、複数のエンティティまたはテーブルからデータを結合する結果を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="1b9b2-127">ここでは、クエリを作成するドメイン モデルに依存して、ため、集計の境界と制約はすべて無視され、自由にクエリをテーブルと列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="1b9b2-128">この方法は、作成またはクエリを更新する開発者向けの優れた柔軟性と生産性を提供します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="1b9b2-129">ViewModels には、クラスで定義された静的な型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="1b9b2-130">または、作成できます (に実装されている順序マイクロ サービス) を実行して、クエリに基づいて動的に開発者にとって非常にアジャイルであります。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="1b9b2-131">マイクロ ORM として Dapper を使用してクエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="1b9b2-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="1b9b2-132">任意のマイクロ ORM、エンティティ フレームワークのコアまたはでもプレーンな ADO.NET を使用するを照会するためです。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="1b9b2-133">サンプル アプリケーションで一般的なマイクロ ORM の好例として eShopOnContainers で順序付けマイクロ サービス用 Dapper に選択しました。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="1b9b2-134">非常に小さいフレームワークになっているために、優れたパフォーマンスは、プレーンな SQL クエリで実行できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="1b9b2-135">Dapper を使用すると、複数のテーブルを結合およびアクセスできる SQL クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="1b9b2-136">Dapper オープン ソース プロジェクト (Sam Saffron によって作成された)、元で使用される構成要素の一部[スタック オーバーフロー](https://stackoverflow.com/)です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="1b9b2-137">使用するには Dapper だけインストールする必要がを通じて、[口ひげ NuGet パッケージ](https://www.nuget.org/packages/Dapper)次の図に示すように、します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="1b9b2-138">使用して、追加する必要がありますもステートメント、コードがある口ひげ拡張メソッドにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="1b9b2-139">コードで Dapper を使用するときに直接クラスを使用する SqlClient System.Data.SqlClient 名前空間で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="1b9b2-140">QueryAsync メソッドと、SqlClient クラスを拡張する他の拡張メソッドでは、単に簡単でパフォーマンスの高い方法でクエリを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="1b9b2-141">動的および静的 ViewModels</span><span class="sxs-lookup"><span data-stu-id="1b9b2-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="1b9b2-142">クエリによって返される ViewModels のほとんどとして実装される順序マイクロ サービスから次のコードに示すように、*動的*です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="1b9b2-143">返される属性のサブセットをクエリ自体に基づいているためです。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="1b9b2-144">クエリまたは結合する新しい列を追加する場合、そのデータは返された ViewModel に動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="1b9b2-145">この方法は、基になるデータ モデルがこの設計手法より柔軟で将来の変更に対応する更新プログラムへの応答でクエリを変更する必要性を軽減します。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

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

<span data-ttu-id="1b9b2-146">重要な点を動的な型を使用すると、返されるデータのコレクションは動的としてアセンブル、ViewModel です。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="1b9b2-147">ほとんどのクエリは簡単で生産性の高いコーディングすることにより、DTO または ViewModel クラスを事前に定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="1b9b2-148">ただし、事前に定義できます (定義済み DTOs) のような ViewModels ViewModels にコントラクトとしてより制限された定義を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="1b9b2-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1b9b2-149">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="1b9b2-149">Additional resources</span></span>

-   <span data-ttu-id="1b9b2-150">**口ひげ**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="1b9b2-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="1b9b2-151">**Julie Lerman です。データ ポイント - 口ひげ、Entity Framework とのハイブリッド アプリ (MSDN Mag. 記事)**</span><span class="sxs-lookup"><span data-stu-id="1b9b2-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="1b9b2-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="1b9b2-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1b9b2-153">[前](eshoponcontainers-cqrs-ddd-microservice.md) [次へ] (ddd-指向-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="1b9b2-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
