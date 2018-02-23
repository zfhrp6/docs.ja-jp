---
title: "開発環境またはテスト環境の RabbitMQ でイベント バスを実装する"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 開発環境またはテスト環境の RabbitMQ でイベント バスを実装する"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3505cb993c736165d4aff4ce8fad38cfa14ed417
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="b30d0-104">開発環境またはテスト環境の RabbitMQ でイベント バスを実装する</span><span class="sxs-lookup"><span data-stu-id="b30d0-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="b30d0-105">eShopOnContainers アプリケーションの場合のようにコンテナーで実行される RabbitMQ に基づいてカスタム イベント バスを作成した場合、その使用は開発環境およびテスト環境に限定する必要があるということを述べることから始めます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="b30d0-106">カスタム イベント バスについては、実働可能なサービス バスの一部として作成していない限り、運用環境で使用すべきではありません。</span><span class="sxs-lookup"><span data-stu-id="b30d0-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="b30d0-107">単純なカスタム イベント バスには、商用サービス バスが備えている重要な実働可能機能の多くが不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b30d0-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="b30d0-108">eShopOnContainers でのイベント バスのカスタム実装の 1 つは基本的には RabbitMQ API を使用するライブラリです (Azure Service Bus に基づく別の実装もあります)。</span><span class="sxs-lookup"><span data-stu-id="b30d0-108">One of the event bus custom implementation in eShopOnContainers is basically a library using the RabbitMQ API (There’s another implementation based on Azure Service Bus).</span></span> 

<span data-ttu-id="b30d0-109">図 8-21 に示すように、RabbitMQ でのイベント バスの実装により、マイクロサービスはイベントのサブスクライブ、イベントの発行、およびイベントの受け取りを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-109">The event bus implementation with RabbitMQ lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="b30d0-110">**図 8-21**</span><span class="sxs-lookup"><span data-stu-id="b30d0-110">**Figure 8-21.**</span></span> <span data-ttu-id="b30d0-111">イベント バスの RabbitMQ 実装</span><span class="sxs-lookup"><span data-stu-id="b30d0-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="b30d0-112">コードの中で、EventBusRabbitMQ クラスは汎用的な IEventBus インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b30d0-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="b30d0-113">これは、この開発/テスト バージョンから運用環境バージョンに切り替えられるように、依存関係挿入に基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="b30d0-114">サンプルの開発/テスト イベント バスの RabbitMQ 実装は定型的なコードです。</span><span class="sxs-lookup"><span data-stu-id="b30d0-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="b30d0-115">これは、RabbitMQ サーバーへの接続を処理し、メッセージ イベントをキューに発行するためのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="b30d0-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="b30d0-116">また、イベントの種類ごとに統合イベント ハンドラーのコレクションから成る辞書を実装する必要があります。このようなイベントの種類では、図 8-21 に示すように、受信側のマイクロサービスごとに、インスタンス化したものが異なり、さまざまなサブスクリプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b30d0-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="b30d0-117">RabbitMQ で単純な発行方法を実装する</span><span class="sxs-lookup"><span data-stu-id="b30d0-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="b30d0-118">次のコードは RabbitMQ 用の簡略化されたイベント バスの実装です。eShopOnContainers の[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)では機能が強化されます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-118">The following code is part is a simplified event bus implementation for RabbitMQ, improved in the [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of eShopOnContainers.</span></span> <span data-ttu-id="b30d0-119">通常、機能強化を行うのでなければ、このコードを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b30d0-119">You usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="b30d0-120">このコードでは、RabbitMQ への接続とチャネルを取得し、メッセージを作成し、キューにメッセージを発行します。</span><span class="sxs-lookup"><span data-stu-id="b30d0-120">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="b30d0-121">eShopOnContainers アプリケーションの Publish メソッドの[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)は、[Polly](https://github.com/App-vNext/Polly) 再試行ポリシーで機能強化されています。このポリシーでは、RabbitMQ コンテナーが準備完了状態にない場合にタスクが特定の回数試行されます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-121">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="b30d0-122">これは docker-compose がコンテナーを開始する場合に発生する可能性があります。たとえば、RabbitMQ コンテナーは他のコンテナーより緩やかに開始します。</span><span class="sxs-lookup"><span data-stu-id="b30d0-122">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="b30d0-123">前述したように、RabbitMQ には可能な構成が多数存在するため、このコードは開発環境およびテスト環境でのみの使用に限定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b30d0-123">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="b30d0-124">RabbitMQ API でサブスクリプション コードを実装する</span><span class="sxs-lookup"><span data-stu-id="b30d0-124">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="b30d0-125">発行コードの場合と同様に、次のコードも RabbitMQ 用のイベント バス実装の一部を簡略化したものです。</span><span class="sxs-lookup"><span data-stu-id="b30d0-125">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="b30d0-126">繰り返しますが、機能強化を行うのでなければ、これを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b30d0-126">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="b30d0-127">各種のイベントには、RabbitMQ からイベントを取得ための関連チャネルがあります。</span><span class="sxs-lookup"><span data-stu-id="b30d0-127">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="b30d0-128">チャネルとイベントの種類ごとにイベント ハンドラーを必要な数だけ使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-128">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="b30d0-129">Subscribe メソッドは IIntegrationEventHandler オブジェクト (現在のマイクロサービスでのコールバック メソッドに似ている) に加えて、それに関連する IntegrationEvent オブジェクトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-129">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="b30d0-130">コードは次にそのイベント ハンドラーを、各種の統合イベントがクライアント マイクロサービスごとに保持できるイベント ハンドラーの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="b30d0-130">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="b30d0-131">クライアント コードがまだサブスクライブしていないイベントがある場合、コードは該当するイベントの種類に対してチャネルを作成します。これにより、そのイベントが他のサービスから発行されたときに RabbitMQ からプッシュ スタイルでイベントを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b30d0-131">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="b30d0-132">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span><span class="sxs-lookup"><span data-stu-id="b30d0-132">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
