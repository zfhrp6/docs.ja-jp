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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>永続化インフラストラクチャとして NoSQL データベースを使用します。

インフラストラクチャと、データ層の NoSQL データベースを使用するときに通常使用しない、ORM Entity Framework Core と同様にします。 代わりに、Azure Cosmos DB、MongoDB、Cassandra、RavenDB、CouchDB、または Azure ストレージ テーブルなどの NoSQL エンジンによって提供される API を使用します。

ただし、NoSQL データベース、特に、ドキュメント指向データベース Azure Cosmos DB、CouchDB、RavenDB などを使用するときに DDD 集計でモデルを設計する方法に似ていますが部分的にどのようにできますで行うこと EF コアの id に関連集計ルート、子エンティティ クラス、および値オブジェクトのクラスです。 ただし、最終的には、データベースの選択が影響を与える、設計にあります。

ドキュメント指向データベースを使用する場合は、JSON または別の形式でシリアル化された 1 つのドキュメントとして集計を実装します。 ただし、データベースの使用は、ドメイン モデルのコードの観点からは透過的です。 NoSQL データベースを使用する場合も使用しているエンティティ クラスと、集計のルート クラスが、ために EF コアを使用する、ときよりも高い柔軟性を永続化はリレーショナルありません。

そのモデルを永続化する方法が違います。 POCO エンティティ クラスに基づく、ドメイン モデルを実装する場合、インフラストラクチャの永続性に依存しない、可能性がありますように見えます。 NoSQL にリレーショナルからでも、別の永続化インフラストラクチャに移動する可能性があります。 ただし、目的のできませんをする必要があります。 常に、異なるデータベース内の制約をプッシュする元に戻すのモデルが同じにできないリレーショナルまたは NoSQL データベース。 永続化モデルの変更はできません、単純なトランザクションと永続化操作が非常に異なるため。

たとえば、ドキュメント指向のデータベースが、集計のルートを持つ複数の子コレクション プロパティの。 リレーショナル データベースの複数の子コレクション プロパティのクエリは、共用体のすべての SQL ステートメントを戻す EF から取得するためです。 リレーショナル データベースまたは NoSQL データベースを同じドメイン モデルを持つことは簡単ではありませんしようとしてする必要がありますいないこと。 実際をそれぞれ特定のデータベースで使用するデータを移動する方法の概要と、モデルを設計する必要があるとします。

NoSQL データベースを使用する場合の利点は、エンティティより非正規化テーブルのマッピングを設定しないためです。 ドメイン モデルをリレーショナル データベースを使用する場合よりも柔軟に指定できます。

集計に基づいてドメイン モデルをデザインすると、NoSQL への移動とドキュメント指向データベースがあります、リレーショナル データベースを使用するよりも簡単にデザインする集計と似ています、ドキュメント指向データベース内のドキュメントをシリアル化されます。 その集計に必要なすべての情報を「バッグ」に含めるとことができます。

たとえば、次の JSON コードは、ドキュメント指向データベースを使用するときに、順序集計のサンプル実装です。 下にある EF コアを使用せずに eShopOnContainers サンプルを実装しましたの集計の順序に似ています。

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

C を使用すると\#Cosmos DB、Azure SDK、集計のようなものによって使用される集計を実装するモデルは、C のような\#POCO クラス EF コアと共に使用します。 次のコードのように、アプリケーションとインフラストラクチャのレイヤーからそれらを使用するための方法が違います。

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

ドメイン モデルを操作する方法をインフラストラクチャは、EF ときに、ドメイン モデル レイヤーで使用するのと同様にできることを確認できます。 でも、集計ルートと同じメソッドを使用するには、インバリアント、し、集計内での検証では、整合性を確認します。

ただし、ときに永続化する、モデル、NoSQL データベース、コードと EF コア コードと比較して大幅に API の変更またはリレーショナル データベースに関連するその他のコードにします。

#### <a name="additional-resources"></a>その他の技術情報

-   **DocumentDB 内のデータをモデリング**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon。理想的なドメインに基づくデザイン集計ストアしますか。** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **永続化とらわれない for .NET イベント ストアです。** GitHub のリポジトリ。
    [*https://github.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[前](infrastructure-persistence-layer-implemenation-entity-framework-core.md) [次へ] (microservice-application-layer-web-api-design.md)
