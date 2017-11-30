---
title: "永続化インフラストラクチャとして NoSQL データベースを使用します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |永続化インフラストラクチャとして NoSQL データベースを使用します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="6442d-104">永続化インフラストラクチャとして NoSQL データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="6442d-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="6442d-105">インフラストラクチャと、データ層の NoSQL データベースを使用するときに通常使用しない、ORM Entity Framework Core と同様にします。</span><span class="sxs-lookup"><span data-stu-id="6442d-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="6442d-106">代わりに、Azure Cosmos DB、MongoDB、Cassandra、RavenDB、CouchDB、または Azure ストレージ テーブルなどの NoSQL エンジンによって提供される API を使用します。</span><span class="sxs-lookup"><span data-stu-id="6442d-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="6442d-107">ただし、NoSQL データベース、特に、ドキュメント指向データベース Azure Cosmos DB、CouchDB、RavenDB などを使用するときに DDD 集計でモデルを設計する方法に似ていますが部分的にどのようにできますで行うこと EF コアの id に関連集計ルート、子エンティティ クラス、および値オブジェクトのクラスです。</span><span class="sxs-lookup"><span data-stu-id="6442d-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="6442d-108">ただし、最終的には、データベースの選択が影響を与える、設計にあります。</span><span class="sxs-lookup"><span data-stu-id="6442d-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="6442d-109">ドキュメント指向データベースを使用する場合は、JSON または別の形式でシリアル化された 1 つのドキュメントとして集計を実装します。</span><span class="sxs-lookup"><span data-stu-id="6442d-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="6442d-110">ただし、データベースの使用は、ドメイン モデルのコードの観点からは透過的です。</span><span class="sxs-lookup"><span data-stu-id="6442d-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="6442d-111">NoSQL データベースを使用する場合も使用しているエンティティ クラスと、集計のルート クラスが、ために EF コアを使用する、ときよりも高い柔軟性を永続化はリレーショナルありません。</span><span class="sxs-lookup"><span data-stu-id="6442d-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="6442d-112">そのモデルを永続化する方法が違います。</span><span class="sxs-lookup"><span data-stu-id="6442d-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="6442d-113">POCO エンティティ クラスに基づく、ドメイン モデルを実装する場合、インフラストラクチャの永続性に依存しない、可能性がありますように見えます。 NoSQL にリレーショナルからでも、別の永続化インフラストラクチャに移動する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6442d-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="6442d-114">ただし、目的のできませんをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6442d-114">However, that should not be your goal.</span></span> <span data-ttu-id="6442d-115">常に、異なるデータベース内の制約をプッシュする元に戻すのモデルが同じにできないリレーショナルまたは NoSQL データベース。</span><span class="sxs-lookup"><span data-stu-id="6442d-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="6442d-116">永続化モデルの変更はできません、単純なトランザクションと永続化操作が非常に異なるため。</span><span class="sxs-lookup"><span data-stu-id="6442d-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="6442d-117">たとえば、ドキュメント指向のデータベースが、集計のルートを持つ複数の子コレクション プロパティの。</span><span class="sxs-lookup"><span data-stu-id="6442d-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="6442d-118">リレーショナル データベースの複数の子コレクション プロパティのクエリは、共用体のすべての SQL ステートメントを戻す EF から取得するためです。</span><span class="sxs-lookup"><span data-stu-id="6442d-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="6442d-119">リレーショナル データベースまたは NoSQL データベースを同じドメイン モデルを持つことは簡単ではありませんしようとしてする必要がありますいないこと。</span><span class="sxs-lookup"><span data-stu-id="6442d-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="6442d-120">実際をそれぞれ特定のデータベースで使用するデータを移動する方法の概要と、モデルを設計する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="6442d-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="6442d-121">NoSQL データベースを使用する場合の利点は、エンティティより非正規化テーブルのマッピングを設定しないためです。</span><span class="sxs-lookup"><span data-stu-id="6442d-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="6442d-122">ドメイン モデルをリレーショナル データベースを使用する場合よりも柔軟に指定できます。</span><span class="sxs-lookup"><span data-stu-id="6442d-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="6442d-123">集計に基づいてドメイン モデルをデザインすると、NoSQL への移動とドキュメント指向データベースがあります、リレーショナル データベースを使用するよりも簡単にデザインする集計と似ています、ドキュメント指向データベース内のドキュメントをシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="6442d-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="6442d-124">その集計に必要なすべての情報を「バッグ」に含めるとことができます。</span><span class="sxs-lookup"><span data-stu-id="6442d-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="6442d-125">たとえば、次の JSON コードは、ドキュメント指向データベースを使用するときに、順序集計のサンプル実装です。</span><span class="sxs-lookup"><span data-stu-id="6442d-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="6442d-126">下にある EF コアを使用せずに eShopOnContainers サンプルを実装しましたの集計の順序に似ています。</span><span class="sxs-lookup"><span data-stu-id="6442d-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

<span data-ttu-id="6442d-127">C を使用すると\#Cosmos DB、Azure SDK、集計のようなものによって使用される集計を実装するモデルは、C のような\#POCO クラス EF コアと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="6442d-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="6442d-128">次のコードのように、アプリケーションとインフラストラクチャのレイヤーからそれらを使用するための方法が違います。</span><span class="sxs-lookup"><span data-stu-id="6442d-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);
OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="6442d-129">ドメイン モデルを操作する方法をインフラストラクチャは、EF ときに、ドメイン モデル レイヤーで使用するのと同様にできることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6442d-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="6442d-130">でも、集計ルートと同じメソッドを使用するには、インバリアント、し、集計内での検証では、整合性を確認します。</span><span class="sxs-lookup"><span data-stu-id="6442d-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="6442d-131">ただし、ときに永続化する、モデル、NoSQL データベース、コードと EF コア コードと比較して大幅に API の変更またはリレーショナル データベースに関連するその他のコードにします。</span><span class="sxs-lookup"><span data-stu-id="6442d-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6442d-132">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="6442d-132">Additional resources</span></span>

-   <span data-ttu-id="6442d-133">**DocumentDB 内のデータをモデリング**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="6442d-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="6442d-134">**Vaughn Vernon。理想的なドメインに基づくデザイン集計ストアしますか。** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="6442d-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="6442d-135">**永続化とらわれない for .NET イベント ストアです。**</span><span class="sxs-lookup"><span data-stu-id="6442d-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="6442d-136">GitHub のリポジトリ。</span><span class="sxs-lookup"><span data-stu-id="6442d-136">GitHub repo.</span></span>
    [<span data-ttu-id="6442d-137">*https://github.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="6442d-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="6442d-138">[前](infrastructure-persistence-layer-implemenation-entity-framework-core.md) [次へ] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="6442d-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>
