---
title: "開発またはテスト環境の RabbitMQ と、イベント バスを実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |開発またはテスト環境の RabbitMQ と、イベント バスを実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f58d355b6f5fd31a21791d3b072c77f70f90c387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a>開発またはテスト環境の RabbitMQ と、イベント バスを実装します。

EShopOnContainers アプリケーションなど、コンテナーで実行されている RabbitMQ に基づいて、カスタム イベント バスを作成する場合を使用することのみの開発およびテスト環境を言うことにより開始する必要があります。 必要がありますを使用しないこと、実稼働環境では、運用環境で service bus の一部として作成する場合を除き、します。 単純なカスタム イベント バスには、商用サービス バスには多くの運用環境で重要な機能が不足している可能性があります。

イベント バスの eShopOnContainers のカスタム実装は、基本的に RabbitMQ API を使用してライブラリです。 実装では図 8-21 を示すように microservices イベントにサブスクライブする、イベントを発行、および、イベントを受け取ることができます。

![](./media/image22.png)

**図 8-21 です。** イベント バスの RabbitMQ 実装

コードでは、EventBusRabbitMQ クラスは、ジェネリック IEventBus インターフェイスを実装します。 これは、この開発/テスト バージョンから実稼働バージョンに切り替えられるように、依存関係の挿入に基づいています。

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

サンプル開発/テスト イベント バスの RabbitMQ 実装は、定型的なコードです。 RabbitMQ サーバーへの接続を処理し、キューにメッセージ イベントを公開するためのコードを提供する必要があるとします。 各イベントの種類です。 統合イベントのハンドラーのコレクションの辞書を実装する必要があるもこれらのイベント タイプには、図 8-21 を示すように別のインスタンス化し、各受信者のマイクロ サービスの各サブスクリプションを持つことができます。

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a>RabbitMQ を持つメソッドを公開する単純なを実装します。

次のコードは通常必要はありませんの機能強化を行っている場合を除き、そのコードを記述するための RabbitMQ の eShopOnContainers イベント バス実装の一部です。 コード接続と RabbitMQ へのチャネルを取得するには、メッセージが作成およびキューにメッセージを公開します。

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Publish(IntegrationEvent @event)
    {
        var eventName = @event.GetType().Name;
        var factory = new ConnectionFactory() { HostName = _connectionString };
        using (var connection = factory.CreateConnection())
        using (var channel = connection.CreateModel())
        {
            channel.ExchangeDeclare(exchange: _brokerName,
                type: "direct");
            string message = JsonConvert.SerializeObject(@event);
            var body = Encoding.UTF8.GetBytes(message);
            channel.BasicPublish(exchange: _brokerName,
                routingKey: eventName,
                basicProperties: null,
                body: body);
       }
    }
}
```

[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)eShopOnContainers アプリケーション内のメソッドの向上を使用して、publish、[ポリー](https://github.com/App-vNext/Polly)再試行ポリシーで、RabbitMQ コンテナーがある場合は、数時間にタスクを再試行準備ができていません。 これは、発生時の docker 構成を開始して、コンテナーたとえば、RabbitMQ コンテナーはまず他のコンテナーより緩やかに変化します。

前述のようがある RabbitMQ で利用可能な多くの構成のためこのコードを開発およびテスト環境にのみ使用する必要があります。

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a>サブスクリプションを RabbitMQ API を使用してコードを実装します。

発行コードと同様、次のコードは、RabbitMQ のイベントのバス実装の一部の簡素化。 もう一度、する通常必要はありませんを向上させている場合を除き、これを変更します。

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...
    public void Subscribe<T>(IIntegrationEventHandler<T> handler)
        where T : IntegrationEvent
    {
        var eventName = typeof(T).Name;
        if (_handlers.ContainsKey(eventName))
        {
            _handlers[eventName].Add(handler);
        }
        else
        {
            var channel = GetChannel();
            channel.QueueBind(queue: _queueName,
                exchange: _brokerName,
                routingKey: eventName);
            _handlers.Add(eventName, new List<IIntegrationEventHandler>());
            _handlers[eventName].Add(handler);
            _eventTypes.Add(typeof(T));
        }
    }
}
```

各イベントの種類が、関連チャネル RabbitMQ からイベントを取得します。 必要に応じて、チャネルとイベントの種類ごとに多数のイベント ハンドラー、ことができます。

Subscribe メソッドは、現在マイクロ サービスのコールバック メソッドのようには、IIntegrationEventHandler オブジェクト、およびその関連 IntegrationEvent オブジェクトを受け入れます。 コードは、クライアント マイクロ サービスごとに各統合イベントの種類が持つことができるイベント ハンドラーの一覧にし、そのイベント ハンドラーを追加します。 クライアント コードがイベントに既にサブスクライブされていない場合、コードは、そのイベントがその他のサービスから発行されたときに RabbitMQ プッシュ スタイルでイベントを受信できるように、イベントの種類のチャネルを作成します。


>[!div class="step-by-step"]
[前](統合-イベント-ベースのマイクロ サービス-communications.md) [次へ] (サブスクライブ events.md)
