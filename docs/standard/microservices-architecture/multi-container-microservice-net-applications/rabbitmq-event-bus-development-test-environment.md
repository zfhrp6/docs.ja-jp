---
title: 開発環境またはテスト環境の RabbitMQ でイベント バスを実装する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 開発環境またはテスト環境の RabbitMQ でイベント バスを実装する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: e2b0f1a6152df5d323164fb2eca102fcb973667e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="7a4d6-103">開発環境またはテスト環境の RabbitMQ でイベント バスを実装する</span><span class="sxs-lookup"><span data-stu-id="7a4d6-103">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="7a4d6-104">eShopOnContainers アプリケーションの場合のようにコンテナーで実行される RabbitMQ に基づいてカスタム イベント バスを作成した場合、その使用は開発環境およびテスト環境に限定する必要があるということを述べることから始めます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-104">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="7a4d6-105">カスタム イベント バスについては、実働可能なサービス バスの一部として作成していない限り、運用環境で使用すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-105">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="7a4d6-106">単純なカスタム イベント バスには、商用サービス バスが備えている重要な実働可能機能の多くが不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-106">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="7a4d6-107">eShopOnContainers でのイベント バスのカスタム実装の 1 つは基本的には RabbitMQ API を使用するライブラリです (Azure Service Bus に基づく別の実装もあります)。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-107">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="7a4d6-108">図 8-21 に示すように、RabbitMQ でのイベント バスの実装により、マイクロサービスはイベントのサブスクライブ、イベントの発行、およびイベントの受け取りを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-108">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="7a4d6-109">**図 8-21**</span><span class="sxs-lookup"><span data-stu-id="7a4d6-109">**Figure 8-21.**</span></span> <span data-ttu-id="7a4d6-110">イベント バスの RabbitMQ 実装</span><span class="sxs-lookup"><span data-stu-id="7a4d6-110">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="7a4d6-111">コードの中で、EventBusRabbitMQ クラスは汎用的な IEventBus インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-111">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="7a4d6-112">これは、この開発/テスト バージョンから運用環境バージョンに切り替えられるように、依存関係挿入に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-112">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="7a4d6-113">サンプルの開発/テスト イベント バスの RabbitMQ 実装は定型的なコードです。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-113">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="7a4d6-114">これは、RabbitMQ サーバーへの接続を処理し、メッセージ イベントをキューに発行するためのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-114">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="7a4d6-115">また、イベントの種類ごとに統合イベント ハンドラーのコレクションから成る辞書を実装する必要があります。このようなイベントの種類では、図 8-21 に示すように、受信側のマイクロサービスごとに、インスタンス化したものが異なり、さまざまなサブスクリプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-115">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="7a4d6-116">RabbitMQ で単純な発行方法を実装する</span><span class="sxs-lookup"><span data-stu-id="7a4d6-116">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="7a4d6-117">次のコードは RabbitMQ 用の簡略化されたイベント バスの実装です。eShopOnContainers の[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)では機能が強化されます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-117">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="7a4d6-118">通常、機能強化を行うのでなければ、このコードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-118">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="7a4d6-119">このコードでは、RabbitMQ への接続とチャネルを取得し、メッセージを作成し、キューにメッセージを発行します。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="7a4d6-120">eShopOnContainers アプリケーションの Publish メソッドの[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)は、[Polly](https://github.com/App-vNext/Polly) 再試行ポリシーで機能強化されています。このポリシーでは、RabbitMQ コンテナーが準備完了状態にない場合にタスクが特定の回数試行されます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="7a4d6-121">これは docker-compose がコンテナーを開始する場合に発生する可能性があります。たとえば、RabbitMQ コンテナーは他のコンテナーより緩やかに開始します。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="7a4d6-122">前述したように、RabbitMQ には可能な構成が多数存在するため、このコードは開発環境およびテスト環境でのみの使用に限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="7a4d6-123">RabbitMQ API でサブスクリプション コードを実装する</span><span class="sxs-lookup"><span data-stu-id="7a4d6-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="7a4d6-124">発行コードの場合と同様に、次のコードも RabbitMQ 用のイベント バス実装の一部を簡略化したものです。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="7a4d6-125">繰り返しますが、機能強化を行うのでなければ、これを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-125">Again, you usually do not need to change it unless you are improving it.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Member objects and other methods ...
    // ...

    public void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>
    {
        var eventName = _subsManager.GetEventKey<T>();
        
        var containsKey = _subsManager.HasSubscriptionsForEvent(eventName);
        if (!containsKey)
        {
            if (!_persistentConnection.IsConnected)
            {
                _persistentConnection.TryConnect();
            }

            using (var channel = _persistentConnection.CreateModel())
            {
                channel.QueueBind(queue: _queueName,
                                    exchange: BROKER_NAME,
                                    routingKey: eventName);
            }
        }

        _subsManager.AddSubscription<T, TH>();
    }
}
```

<span data-ttu-id="7a4d6-126">各種のイベントには、RabbitMQ からイベントを取得ための関連チャネルがあります。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="7a4d6-127">チャネルとイベントの種類ごとにイベント ハンドラーを必要な数だけ使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="7a4d6-128">Subscribe メソッドは IIntegrationEventHandler オブジェクト (現在のマイクロサービスでのコールバック メソッドに似ている) に加えて、それに関連する IntegrationEvent オブジェクトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="7a4d6-129">コードは次にそのイベント ハンドラーを、各種の統合イベントがクライアント マイクロサービスごとに保持できるイベント ハンドラーの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="7a4d6-130">クライアント コードがまだサブスクライブしていないイベントがある場合、コードは該当するイベントの種類に対してチャネルを作成します。これにより、そのイベントが他のサービスから発行されたときに RabbitMQ からプッシュ スタイルでイベントを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="7a4d6-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7a4d6-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="7a4d6-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
