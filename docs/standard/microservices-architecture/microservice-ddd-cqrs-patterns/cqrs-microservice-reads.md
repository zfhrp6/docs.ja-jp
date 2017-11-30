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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>CQRS マイクロ サービスでの読み取り]、[クエリの実装

読み取り/クエリでは、eShopOnContainers の参照をアプリケーションから順序マイクロ サービスは DDD モデルと領域をトランザクションから独立してクエリを実装します。 これは、クエリおよびトランザクションの要求が大幅に異なるため、主にします。 書き込みは、ドメイン ロジックに準拠する必要があるトランザクションを実行します。 クエリ、その一方で、べき等なので、ドメイン ルールから分離できます。

アプローチは、図 9-3 に示すように単純です。 Web API コント ローラー (micro Dapper などの ORM) などの任意のインフラストラクチャを使用し、UI アプリケーションのニーズに応じて動的 ViewModels を返すことによって、API インターフェイスが実装されます。

![](./media/image3.png)

**図 9-3**です。 CQRS マイクロ サービスでのクエリの最も簡単な方法

これは、クエリの最も簡単な方法をも考えられます。 クエリの定義は、データベースを照会し、各クエリに対してその場で構築された動的 ViewModel を返します。 クエリでは、べき等であるため、クエリを実行する回数に関係なく、データは変更されません。 したがって、集計およびその他のパターンと同様に、トランザクションの側で使用される任意の DDD パターンにより制限を適用する必要はありません、ため、クエリは、トランザクション領域から区切られます。 単に、UI が必要なデータをデータベースに照会し、静的にする必要のない動的 ViewModel で定義されている任意の場所 (、ViewModels のクラスを持たない) を除く SQL ステートメント自体を返します。

クエリ側のコードに必要なので、これは、単純な方法で (などの ORM マイクロを使用してコードをなど[Dapper](https://github.com/StackExchange/Dapper)) を実装する[同じ Web API プロジェクト内で](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs)です。 図 9-4 では、これを示します。 クエリが定義されている、 **Ordering.API** eShopOnContainers ソリューション内のマイクロ サービスのプロジェクトです。

![](./media/image4.png)

**図 9-4**です。 EShopOnContainers で順序付けマイクロ サービス内のクエリ

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>具体的には、ドメイン モデルの制約から独立してクライアント アプリに対して行われた ViewModels を使用します。

クライアント アプリケーションで必要なデータを取得するためには、クエリが実行、ので、クエリによって返されるデータに基づいて、クライアントの戻り値の型を具体的には作成できます。 これらのモデル、またはデータ転送オブジェクト (Dto) は、ViewModels と呼ばれます。

返されるデータ (ViewModel) は、データベース、またはトランザクションの領域のドメイン モデルで定義されている複数の集計が異なる場合でも、複数のエンティティまたはテーブルからデータを結合する結果を指定できます。 ここでは、クエリを作成するドメイン モデルに依存して、ため、集計の境界と制約はすべて無視され、自由にクエリをテーブルと列にする必要があります。 この方法は、作成またはクエリを更新する開発者向けの優れた柔軟性と生産性を提供します。

ViewModels には、クラスで定義された静的な型を指定できます。 または、作成できます (に実装されている順序マイクロ サービス) を実行して、クエリに基づいて動的に開発者にとって非常にアジャイルであります。

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>マイクロ ORM として Dapper を使用してクエリを実行するには 

任意のマイクロ ORM、エンティティ フレームワークのコアまたはでもプレーンな ADO.NET を使用するを照会するためです。 サンプル アプリケーションで一般的なマイクロ ORM の好例として eShopOnContainers で順序付けマイクロ サービス用 Dapper に選択しました。 非常に小さいフレームワークになっているために、優れたパフォーマンスは、プレーンな SQL クエリで実行できます。 Dapper を使用すると、複数のテーブルを結合およびアクセスできる SQL クエリを記述できます。

Dapper オープン ソース プロジェクト (Sam Saffron によって作成された)、元で使用される構成要素の一部[スタック オーバーフロー](https://stackoverflow.com/)です。 使用するには Dapper だけインストールする必要がを通じて、[口ひげ NuGet パッケージ](https://www.nuget.org/packages/Dapper)次の図に示すように、します。

![](./media/image5.png)

使用して、追加する必要がありますもステートメント、コードがある口ひげ拡張メソッドにアクセスできるようにします。

コードで Dapper を使用するときに直接クラスを使用する SqlClient System.Data.SqlClient 名前空間で使用できます。 QueryAsync メソッドと、SqlClient クラスを拡張する他の拡張メソッドでは、単に簡単でパフォーマンスの高い方法でクエリを実行することができます。

## <a name="dynamic-and-static-viewmodels"></a>動的および静的 ViewModels

クエリによって返される ViewModels のほとんどとして実装される順序マイクロ サービスから次のコードに示すように、*動的*です。 返される属性のサブセットをクエリ自体に基づいているためです。 クエリまたは結合する新しい列を追加する場合、そのデータは返された ViewModel に動的に追加します。 この方法は、基になるデータ モデルがこの設計手法より柔軟で将来の変更に対応する更新プログラムへの応答でクエリを変更する必要性を軽減します。

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

重要な点を動的な型を使用すると、返されるデータのコレクションは動的としてアセンブル、ViewModel です。

ほとんどのクエリは簡単で生産性の高いコーディングすることにより、DTO または ViewModel クラスを事前に定義する必要はありません。 ただし、事前に定義できます (定義済み DTOs) のような ViewModels ViewModels にコントラクトとしてより制限された定義を使用する場合。

#### <a name="additional-resources"></a>その他の技術情報

-   **口ひげ**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman です。データ ポイント - 口ひげ、Entity Framework とのハイブリッド アプリ (MSDN Mag. 記事)**

    *https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*


>[!div class="step-by-step"]
[前](eshoponcontainers-cqrs-ddd-microservice.md) [次へ] (ddd-指向-microservice.md)
