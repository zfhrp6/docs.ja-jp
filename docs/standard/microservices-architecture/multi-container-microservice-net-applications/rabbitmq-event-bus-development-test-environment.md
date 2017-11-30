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
# <a name="implementing-an-event-bus-with-rabbitmq-for-the-development-or-test-environment"></a><span data-ttu-id="a8d7c-104">開発またはテスト環境の RabbitMQ と、イベント バスを実装します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-104">Implementing an event bus with RabbitMQ for the development or test environment</span></span>

<span data-ttu-id="a8d7c-105">EShopOnContainers アプリケーションなど、コンテナーで実行されている RabbitMQ に基づいて、カスタム イベント バスを作成する場合を使用することのみの開発およびテスト環境を言うことにより開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-105">We should start by saying that if you create your custom event bus based on RabbitMQ running in a container, as the eShopOnContainers application does, it should be used only for your development and test environments.</span></span> <span data-ttu-id="a8d7c-106">必要がありますを使用しないこと、実稼働環境では、運用環境で service bus の一部として作成する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-106">You should not use it for your production environment, unless you are building it as a part of a production-ready service bus.</span></span> <span data-ttu-id="a8d7c-107">単純なカスタム イベント バスには、商用サービス バスには多くの運用環境で重要な機能が不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-107">A simple custom event bus might be missing many production-ready critical features that a commercial service bus has.</span></span>

<span data-ttu-id="a8d7c-108">イベント バスの eShopOnContainers のカスタム実装は、基本的に RabbitMQ API を使用してライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-108">The eShopOnContainers custom implementation of an event bus is basically a library using the RabbitMQ API.</span></span> <span data-ttu-id="a8d7c-109">実装では図 8-21 を示すように microservices イベントにサブスクライブする、イベントを発行、および、イベントを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-109">The implementation lets microservices subscribe to events, publish events, and receive events, as shown in Figure 8-21.</span></span>

![](./media/image22.png)

<span data-ttu-id="a8d7c-110">**図 8-21 です。**</span><span class="sxs-lookup"><span data-stu-id="a8d7c-110">**Figure 8-21.**</span></span> <span data-ttu-id="a8d7c-111">イベント バスの RabbitMQ 実装</span><span class="sxs-lookup"><span data-stu-id="a8d7c-111">RabbitMQ implementation of an event bus</span></span>

<span data-ttu-id="a8d7c-112">コードでは、EventBusRabbitMQ クラスは、ジェネリック IEventBus インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-112">In the code, the EventBusRabbitMQ class implements the generic IEventBus interface.</span></span> <span data-ttu-id="a8d7c-113">これは、この開発/テスト バージョンから実稼働バージョンに切り替えられるように、依存関係の挿入に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-113">This is based on Dependency Injection so that you can swap from this dev/test version to a production version.</span></span>

```csharp
public class EventBusRabbitMQ : IEventBus, IDisposable
{
    // Implementation using RabbitMQ API
    //...
```

<span data-ttu-id="a8d7c-114">サンプル開発/テスト イベント バスの RabbitMQ 実装は、定型的なコードです。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-114">The RabbitMQ implementation of a sample dev/test event bus is boilerplate code.</span></span> <span data-ttu-id="a8d7c-115">RabbitMQ サーバーへの接続を処理し、キューにメッセージ イベントを公開するためのコードを提供する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-115">It has to handle the connection to the RabbitMQ server and provide code for publishing a message event to the queues.</span></span> <span data-ttu-id="a8d7c-116">各イベントの種類です。 統合イベントのハンドラーのコレクションの辞書を実装する必要があるもこれらのイベント タイプには、図 8-21 を示すように別のインスタンス化し、各受信者のマイクロ サービスの各サブスクリプションを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-116">It also has to implement a dictionary of collections of integration event handlers for each event type; these event types can have a different instantiation and different subscriptions for each receiver microservice, as shown in Figure 8-21.</span></span>

## <a name="implementing-a-simple-publish-method-with-rabbitmq"></a><span data-ttu-id="a8d7c-117">RabbitMQ を持つメソッドを公開する単純なを実装します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-117">Implementing a simple publish method with RabbitMQ</span></span>

<span data-ttu-id="a8d7c-118">次のコードは通常必要はありませんの機能強化を行っている場合を除き、そのコードを記述するための RabbitMQ の eShopOnContainers イベント バス実装の一部です。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-118">The following code is part of the eShopOnContainers event bus implementation for RabbitMQ, so you usually do not need to code it unless you are making improvements.</span></span> <span data-ttu-id="a8d7c-119">コード接続と RabbitMQ へのチャネルを取得するには、メッセージが作成およびキューにメッセージを公開します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-119">The code gets a connection and channel to RabbitMQ, creates a message, and then publishes the message into the queue.</span></span>

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

<span data-ttu-id="a8d7c-120">[実際のコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs)eShopOnContainers アプリケーション内のメソッドの向上を使用して、publish、[ポリー](https://github.com/App-vNext/Polly)再試行ポリシーで、RabbitMQ コンテナーがある場合は、数時間にタスクを再試行準備ができていません。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-120">The [actual code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.cs) of the Publish method in the eShopOnContainers application is improved by using a [Polly](https://github.com/App-vNext/Polly) retry policy, which retries the task a certain number of times in case the RabbitMQ container is not ready.</span></span> <span data-ttu-id="a8d7c-121">これは、発生時の docker 構成を開始して、コンテナーたとえば、RabbitMQ コンテナーはまず他のコンテナーより緩やかに変化します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-121">This can occur when docker-compose is starting the containers; for example, the RabbitMQ container might start more slowly than the other containers.</span></span>

<span data-ttu-id="a8d7c-122">前述のようがある RabbitMQ で利用可能な多くの構成のためこのコードを開発およびテスト環境にのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-122">As mentioned earlier, there are many possible configurations in RabbitMQ, so this code should be used only for dev/test environments.</span></span>

## <a name="implementing-the-subscription-code-with-the-rabbitmq-api"></a><span data-ttu-id="a8d7c-123">サブスクリプションを RabbitMQ API を使用してコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-123">Implementing the subscription code with the RabbitMQ API</span></span>

<span data-ttu-id="a8d7c-124">発行コードと同様、次のコードは、RabbitMQ のイベントのバス実装の一部の簡素化。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-124">As with the publish code, the following code is a simplification of part of the event bus implementation for RabbitMQ.</span></span> <span data-ttu-id="a8d7c-125">もう一度、する通常必要はありませんを向上させている場合を除き、これを変更します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-125">Again, you usually do not need to change it unless you are improving it.</span></span>

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

<span data-ttu-id="a8d7c-126">各イベントの種類が、関連チャネル RabbitMQ からイベントを取得します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-126">Each event type has a related channel to get events from RabbitMQ.</span></span> <span data-ttu-id="a8d7c-127">必要に応じて、チャネルとイベントの種類ごとに多数のイベント ハンドラー、ことができます。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-127">You can then have as many event handlers per channel and event type as needed.</span></span>

<span data-ttu-id="a8d7c-128">Subscribe メソッドは、現在マイクロ サービスのコールバック メソッドのようには、IIntegrationEventHandler オブジェクト、およびその関連 IntegrationEvent オブジェクトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-128">The Subscribe method accepts an IIntegrationEventHandler object, which is like a callback method in the current microservice, plus its related IntegrationEvent object.</span></span> <span data-ttu-id="a8d7c-129">コードは、クライアント マイクロ サービスごとに各統合イベントの種類が持つことができるイベント ハンドラーの一覧にし、そのイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-129">The code then adds that event handler to the list of event handlers that each integration event type can have per client microservice.</span></span> <span data-ttu-id="a8d7c-130">クライアント コードがイベントに既にサブスクライブされていない場合、コードは、そのイベントがその他のサービスから発行されたときに RabbitMQ プッシュ スタイルでイベントを受信できるように、イベントの種類のチャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-130">If the client code has not already been subscribed to the event, the code creates a channel for the event type so it can receive events in a push style from RabbitMQ when that event is published from any other service.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a8d7c-131">[前](統合-イベント-ベースのマイクロ サービス-communications.md) [次へ] (サブスクライブ events.md)</span><span class="sxs-lookup"><span data-stu-id="a8d7c-131">[Previous] (integration-event-based-microservice-communications.md) [Next] (subscribe-events.md)</span></span>
