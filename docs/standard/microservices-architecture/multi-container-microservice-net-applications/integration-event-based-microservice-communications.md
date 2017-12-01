---
title: "Microservices (統合イベント) の間でイベント ベースの通信を実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices (統合イベント) の間でイベント ベースの通信を実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e438607ab3549d63b89bef6af64c6723a4cac950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Microservices (統合イベント) の間でイベント ベースの通信を実装します。

イベント ベースの通信を使用する場合は、前述したとおり、マイクロ サービスは、注目に値する問題が発生すると、ビジネス エンティティを更新したときなど、イベントを公開します。 その他の microservices は、これらのイベントにサブスクライブします。 マイクロ サービス イベントを受信すると、パブリッシュされている複数のイベントになる可能性があります、独自のビジネス エンティティを更新できます。 このパブリッシュ/サブスクライブ システムは通常、イベント バスの実装を使用して実行されます。 イベント バスは、サブスクライブし、イベントをアンサブスク ライブする、イベントを発行するために必要な api インターフェイスとして設計できます。 メッセージ キューや非同期通信と、パブリッシュ/サブスクライブ モデルをサポートする service bus など、プロセス間またはメッセージング通信に基づいて 1 つまたは複数の実装もあります。

できますイベントを使用する複数のサービスにまたがるビジネス トランザクションを実装するのにそれらのサービス間で最終的整合性を提供します。 最終的に一貫性のあるトランザクションは、一連の分散アクションで構成されます。 各アクションには、マイクロ サービスは、ビジネス エンティティを更新し、次のアクションをトリガーするイベントを公開します。

![](./media/image19.PNG)

**図 8-18**です。 イベント バスに基づき、イベント ドリブン通信

このセクションでは、インターフェイスを使用して、汎用イベント バス、図 8-18 に示すように、この種類の .NET との通信を実装する方法について説明します。 さまざまなテクノロジまたは RabbitMQ、Azure サービス バス、またはその他のサード パーティ オープン ソースや商用サービス バスなどのインフラストラクチャを使用して、複数の潜在的な実装されます。

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>実稼働システムのメッセージ ブローカーとサービス バスを使用します。

前述のアーキテクチャ」は、抽象イベント バスを実装するための複数のメッセージング テクノロジを選択できます。 ただし、これらのテクノロジは、さまざまなレベルではします。 たとえば、RabbitMQ、broker のメッセージのトランスポートは、Azure Service Bus、NServiceBus、MassTransit、Brighter などの商用の製品よりも低いレベルでです。 これらの製品のほとんどは、RabbitMQ や Azure Service Bus のいずれかの上に作業できます。 製品の選択は、アプリケーションに必要な機能とどの程度 - の-すぐスケーラビリティの数によって異なります。

だけ、イベント バスの概念実証 eShopOnContainers サンプルと同様に、開発環境を実装するのには十分なコンテナーとして実行されている RabbitMQ 上に簡単な実装可能性があります。 ミッション クリティカル運用システム高スケーラビリティが必要では、評価し、Azure Service Fabric を使用する必要があります。 高度な抽象化を必要として、豊富な機能と同様に場合[sagas](https://docs.particular.net/nservicebus/sagas/) NServiceBus、MassTransit と同様に簡単に、その他の商用およびオープン ソースのサービス バスに分散した開発を構成する実行時間の長いプロセスと評価する価値は明るいです。 もちろん、RabbitMQ および Docker、ような下位レベルのテクノロジの上に独自のサービス バス機能を常にビルドでしたに労力を必要な作業は、カスタムのエンタープライズ アプリケーションのコストが高くなる可能性があります。

繰り返しに: 概念実証としてのみ使用するためのサンプル イベント バスの抽象化と展示 eShopOnContainers サンプルで実装します。 こと、およびイベント ドリブンの非同期通信がある現在のセクションで説明したものが決まったら、ニーズに最適なサービス バスの製品を選択してください。

## <a name="integration-events"></a>統合イベント

統合イベントは、複数の microservices または外部システムへの同期ドメインの状態を取り込むに使用されます。 これは、マイクロ サービス外の統合イベントを発行することによって行います。 (同数 microservices 統合イベントにサブスクライブしているように) に複数の受信者 microservices にイベントが発行されると、各受信者マイクロ サービスで適切なイベント ハンドラーは、イベントを処理します。

統合イベントは、次の例のように、データを保持クラスでは基本的には。

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

使用できる統合イベント クラスは単純です。その ID の GUID を含めることなど、

サーバーとクライアントで ViewModels を定義する方法を比較できる方法で他の microservices から切り離されているように、各マイクロ サービスのアプリケーション レベルで統合イベントを定義できます。 どのような方法はお勧めしませんがライブラリを共有する一般的な統合イベント複数 microservices; の間でこれを行うは、1 つのイベント定義のデータのライブラリとそれら microservices 結合はします。 そのためには複数 microservices 間で共通のドメイン モデルを共有するたくない上の理由により、同じたくない: microservices を完全に自律的にする必要があります。

Microservices 間で共有する必要がありますライブラリのいくつかの種類のみがあります。 1 つは、ライブラリと同様に、最終的なアプリケーション ブロックである、[イベント バス クライアント API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)eShopOnContainers のように、します。 他にもさらに JSON シリアライザーなどの NuGet コンポーネントとして共有することがツールを構成するライブラリ。

## <a name="the-event-bus"></a>イベント バス

イベント バスは、明示的に認識する、他の図 8-19 に示すようにコンポーネントを必要とせず microservices 間パブリッシュ/サブスクライブ スタイルの通信を許可します。

![](./media/image20.png)

**図 8-19**です。 イベント バスの基礎のパブリッシュ/サブスクライブします。

オブザーバー パターンと、発行に関連するイベント バスの定期受信パターン。

### <a name="observer-pattern"></a>オブザーバー パターン

[オブザーバー パターン](https://en.wikipedia.org/wiki/Observer_pattern)、(監視対象と呼ばれます)、プライマリ オブジェクトに関連する情報 (イベント) (オブザーバーと呼ばれる) その他の対象となるオブジェクトに通知します。

### <a name="publish-subscribe-pubsub-pattern"></a>(パブリッシュ/サブスクライブ) の発行/定期受信パターン 

目的は、[パブリッシュ/サブスクライブ パターン](https://msdn.microsoft.com/en-us/library/ff649664.aspx)オブザーバー パターンと同じです。 特定のイベントが発生する場合は、他のサービスを通知します。 重要な意味上の違い、オブザーバーおよびパブリッシュ/サブスクライブ パターン。 パブリッシュ/サブスクライブ パターンでは、メッセージをブロードキャストにフォーカスがあります。 これに対し、オブザーバー パターンでは、観測可能なオブジェクトは認識しないイベントが組み込まれて、out になっていること。つまり、観測可能なオブジェクト (パブリッシャー) は認識しないオブザーバー (サブスクライバー) であります。

### <a name="the-middleman-or-event-bus"></a>仲介者またはイベント バス 

パブリッシャーとサブスクライバー間で匿名性を実現するには 簡単な方法は、すべての通信を処理する仲介者を使用できます。 イベント バスは、このような 1 つの仲介者です。

イベント バスは通常、2 つの部分で構成されます。

-   抽象またはインターフェイス。

-   1 つまたは複数の実装です。

図 8-19 方法、アプリケーションの観点から、イベント バスがわかります Pub/sub チャネルより詳細に何も行われません。 この非同期通信を実装する方法が異なることができます。 複数の実装は、環境の要件 (たとえば、開発環境と運用) によってそれらの間で交換できるようにことができます。

図 8-20 RabbitMQ、Azure サービス バス、または他のサービス バスと NServiceBus、MassTransit などのようなテクノロジをメッセージング インフラストラクチャに基づいて複数の実装では、イベント バスの抽象化を確認できます。

![](./media/image21.png)

**図 8-20 です。** イベント バスの複数の実装

ただし、強調表示されている以前は、抽象化 (イベント バス インターフェイス) を使用するは、抽象化でサポートされている基本イベント バスの機能が必要な場合にのみ可能です。 豊富なサービス バス機能を必要がある場合は、独自の抽象化ではなく、優先するサービス バスが提供する API を使用する必要があります可能性があります。

### <a name="defining-an-event-bus-interface"></a>イベント バス インターフェイスを定義します。

いくつか実装コードは、イベント バス インターフェイスと探索のための可能な実装から始めましょう。 インターフェイスは、汎用的な単純ですが、次のインターフェイスのようにする必要があります。

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);
    void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T: IntegrationEvent;

    void Unsubscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent;
}
```

発行方法は簡単です。 イベント バスは、そのイベントにサブスクライブしている任意のマイクロ サービスに渡された統合イベントをブロードキャストします。 このメソッドは、イベントをパブリッシュしているマイクロ サービスによって使用されます。

イベントを受信する microservices Subscribe メソッドを使用します。 このメソッドには、2 つの部分があります。 最初は、(IntegrationEvent) を購読する統合イベントです。 2 番目の部分は、統合イベントのハンドラー (コールバック メソッド) を呼び出せる (IIntegrationEventHandler&lt;T&gt;)、マイクロ サービスがその統合イベント メッセージを受信するとします。


>[!div class="step-by-step"]
[前](データベースのサーバー-container.md) [次へ] (rabbitmq-event-bus-development-test-environment.md)
