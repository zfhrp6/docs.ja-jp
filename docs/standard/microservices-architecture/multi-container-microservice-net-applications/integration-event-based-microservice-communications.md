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
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a><span data-ttu-id="64a13-104">Microservices (統合イベント) の間でイベント ベースの通信を実装します。</span><span class="sxs-lookup"><span data-stu-id="64a13-104">Implementing event-based communication between microservices (integration events)</span></span>

<span data-ttu-id="64a13-105">イベント ベースの通信を使用する場合は、前述したとおり、マイクロ サービスは、注目に値する問題が発生すると、ビジネス エンティティを更新したときなど、イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="64a13-105">As described earlier, when you use event-based communication, a microservice publishes an event when something notable happens, such as when it updates a business entity.</span></span> <span data-ttu-id="64a13-106">その他の microservices は、これらのイベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="64a13-106">Other microservices subscribe to those events.</span></span> <span data-ttu-id="64a13-107">マイクロ サービス イベントを受信すると、パブリッシュされている複数のイベントになる可能性があります、独自のビジネス エンティティを更新できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-107">When a microservice receives an event, it can update its own business entities, which might lead to more events being published.</span></span> <span data-ttu-id="64a13-108">このパブリッシュ/サブスクライブ システムは通常、イベント バスの実装を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-108">This publish/subscribe system is usually performed by using an implementation of an event bus.</span></span> <span data-ttu-id="64a13-109">イベント バスは、サブスクライブし、イベントをアンサブスク ライブする、イベントを発行するために必要な api インターフェイスとして設計できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-109">The event bus can be designed as an interface with the API needed to subscribe and unsubscribe to events and to publish events.</span></span> <span data-ttu-id="64a13-110">メッセージ キューや非同期通信と、パブリッシュ/サブスクライブ モデルをサポートする service bus など、プロセス間またはメッセージング通信に基づいて 1 つまたは複数の実装もあります。</span><span class="sxs-lookup"><span data-stu-id="64a13-110">It can also have one or more implementations based on any inter-process or messaging communication, such as a messaging queue or a service bus that supports asynchronous communication and a publish/subscribe model.</span></span>

<span data-ttu-id="64a13-111">できますイベントを使用する複数のサービスにまたがるビジネス トランザクションを実装するのにそれらのサービス間で最終的整合性を提供します。</span><span class="sxs-lookup"><span data-stu-id="64a13-111">You can use events to implement business transactions that span multiple services, which gives you eventual consistency between those services.</span></span> <span data-ttu-id="64a13-112">最終的に一貫性のあるトランザクションは、一連の分散アクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-112">An eventually consistent transaction consists of a series of distributed actions.</span></span> <span data-ttu-id="64a13-113">各アクションには、マイクロ サービスは、ビジネス エンティティを更新し、次のアクションをトリガーするイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="64a13-113">At each action, the microservice updates a business entity and publishes an event that triggers the next action.</span></span>

![](./media/image19.PNG)

<span data-ttu-id="64a13-114">**図 8-18**です。</span><span class="sxs-lookup"><span data-stu-id="64a13-114">**Figure 8-18**.</span></span> <span data-ttu-id="64a13-115">イベント バスに基づき、イベント ドリブン通信</span><span class="sxs-lookup"><span data-stu-id="64a13-115">Event-driven communication based on an event bus</span></span>

<span data-ttu-id="64a13-116">このセクションでは、インターフェイスを使用して、汎用イベント バス、図 8-18 に示すように、この種類の .NET との通信を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="64a13-116">This section describes how you can implement this type of communication with .NET by using a generic event bus interface, as shown in Figure 8-18.</span></span> <span data-ttu-id="64a13-117">さまざまなテクノロジまたは RabbitMQ、Azure サービス バス、またはその他のサード パーティ オープン ソースや商用サービス バスなどのインフラストラクチャを使用して、複数の潜在的な実装されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-117">There are multiple potential implementations, each using a different technology or infrastructure such as RabbitMQ, Azure Service Bus, or any other third-party open source or commercial service bus.</span></span>

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a><span data-ttu-id="64a13-118">実稼働システムのメッセージ ブローカーとサービス バスを使用します。</span><span class="sxs-lookup"><span data-stu-id="64a13-118">Using message brokers and services buses for production systems</span></span>

<span data-ttu-id="64a13-119">前述のアーキテクチャ」は、抽象イベント バスを実装するための複数のメッセージング テクノロジを選択できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-119">As noted in the architecture section, you can choose from multiple messaging technologies for implementing your abstract event bus.</span></span> <span data-ttu-id="64a13-120">ただし、これらのテクノロジは、さまざまなレベルではします。</span><span class="sxs-lookup"><span data-stu-id="64a13-120">But these technologies are at different levels.</span></span> <span data-ttu-id="64a13-121">たとえば、RabbitMQ、broker のメッセージのトランスポートは、Azure Service Bus、NServiceBus、MassTransit、Brighter などの商用の製品よりも低いレベルでです。</span><span class="sxs-lookup"><span data-stu-id="64a13-121">For instance, RabbitMQ, a messaging broker transport, is at a lower level than commercial products like Azure Service Bus, NServiceBus, MassTransit, or Brighter.</span></span> <span data-ttu-id="64a13-122">これらの製品のほとんどは、RabbitMQ や Azure Service Bus のいずれかの上に作業できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-122">Most of these products can work on top of either RabbitMQ or Azure Service Bus.</span></span> <span data-ttu-id="64a13-123">製品の選択は、アプリケーションに必要な機能とどの程度 - の-すぐスケーラビリティの数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="64a13-123">Your choice of product depends on how many features and how much out-of-the-box scalability you need for your application.</span></span>

<span data-ttu-id="64a13-124">だけ、イベント バスの概念実証 eShopOnContainers サンプルと同様に、開発環境を実装するのには十分なコンテナーとして実行されている RabbitMQ 上に簡単な実装可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-124">For implementing just an event bus proof-of-concept for your development environment, as in the eShopOnContainers sample, a simple implementation on top of RabbitMQ running as a container might be enough.</span></span> <span data-ttu-id="64a13-125">ミッション クリティカル運用システム高スケーラビリティが必要では、評価し、Azure Service Fabric を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-125">But for mission-critical and production systems that need high scalability, you might want to evaluate and use Azure Service Fabric.</span></span> <span data-ttu-id="64a13-126">高度な抽象化を必要として、豊富な機能と同様に場合[sagas](https://docs.particular.net/nservicebus/sagas/) NServiceBus、MassTransit と同様に簡単に、その他の商用およびオープン ソースのサービス バスに分散した開発を構成する実行時間の長いプロセスと評価する価値は明るいです。</span><span class="sxs-lookup"><span data-stu-id="64a13-126">If you require high-level abstractions and richer features like [sagas](https://docs.particular.net/nservicebus/sagas/) for long-running processes that make distributed development easier, other commercial and open-source service buses like NServiceBus, MassTransit, and Brighter are worth evaluating.</span></span> <span data-ttu-id="64a13-127">もちろん、RabbitMQ および Docker、ような下位レベルのテクノロジの上に独自のサービス バス機能を常にビルドでしたに労力を必要な作業は、カスタムのエンタープライズ アプリケーションのコストが高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-127">Of course, you could always build your own service bus features on top of lower-level technologies like RabbitMQ and Docker, but the work needed to reinvent the wheel might be too costly for a custom enterprise application.</span></span>

<span data-ttu-id="64a13-128">繰り返しに: 概念実証としてのみ使用するためのサンプル イベント バスの抽象化と展示 eShopOnContainers サンプルで実装します。</span><span class="sxs-lookup"><span data-stu-id="64a13-128">To reiterate: the sample event bus abstractions and implementation showcased in the eShopOnContainers sample are intended to be used only as a proof of concept.</span></span> <span data-ttu-id="64a13-129">こと、およびイベント ドリブンの非同期通信がある現在のセクションで説明したものが決まったら、ニーズに最適なサービス バスの製品を選択してください。</span><span class="sxs-lookup"><span data-stu-id="64a13-129">Once you have decided that you want to have asynchronous and event-driven communication, as explained in the current section, you should choose the service bus product that best fits your needs.</span></span>

## <a name="integration-events"></a><span data-ttu-id="64a13-130">統合イベント</span><span class="sxs-lookup"><span data-stu-id="64a13-130">Integration events</span></span>

<span data-ttu-id="64a13-131">統合イベントは、複数の microservices または外部システムへの同期ドメインの状態を取り込むに使用されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-131">Integration events are used for bringing domain state in sync across multiple microservices or external systems.</span></span> <span data-ttu-id="64a13-132">これは、マイクロ サービス外の統合イベントを発行することによって行います。</span><span class="sxs-lookup"><span data-stu-id="64a13-132">This is done by publishing integration events outside the microservice.</span></span> <span data-ttu-id="64a13-133">(同数 microservices 統合イベントにサブスクライブしているように) に複数の受信者 microservices にイベントが発行されると、各受信者マイクロ サービスで適切なイベント ハンドラーは、イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="64a13-133">When an event is published to multiple receiver microservices (to as many microservices as are subscribed to the integration event), the appropriate event handler in each receiver microservice handles the event.</span></span>

<span data-ttu-id="64a13-134">統合イベントは、次の例のように、データを保持クラスでは基本的には。</span><span class="sxs-lookup"><span data-stu-id="64a13-134">An integration event is basically a data-holding class, as in the following example:</span></span>

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

<span data-ttu-id="64a13-135">使用できる統合イベント クラスは単純です。その ID の GUID を含めることなど、</span><span class="sxs-lookup"><span data-stu-id="64a13-135">The integration event class can be simple; for example, it might contain a GUID for its ID.</span></span>

<span data-ttu-id="64a13-136">サーバーとクライアントで ViewModels を定義する方法を比較できる方法で他の microservices から切り離されているように、各マイクロ サービスのアプリケーション レベルで統合イベントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-136">The integration events can be defined at the application level of each microservice, so they are decoupled from other microservices, in a way comparable to how ViewModels are defined in the server and client.</span></span> <span data-ttu-id="64a13-137">どのような方法はお勧めしませんがライブラリを共有する一般的な統合イベント複数 microservices; の間でこれを行うは、1 つのイベント定義のデータのライブラリとそれら microservices 結合はします。</span><span class="sxs-lookup"><span data-stu-id="64a13-137">What is not recommended is sharing a common integration events library across multiple microservices; doing that would be coupling those microservices with a single event definition data library.</span></span> <span data-ttu-id="64a13-138">そのためには複数 microservices 間で共通のドメイン モデルを共有するたくない上の理由により、同じたくない: microservices を完全に自律的にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-138">You do not want to do that for the same reasons that you do not want to share a common domain model across multiple microservices: microservices must be completely autonomous.</span></span>

<span data-ttu-id="64a13-139">Microservices 間で共有する必要がありますライブラリのいくつかの種類のみがあります。</span><span class="sxs-lookup"><span data-stu-id="64a13-139">There are only a few kinds of libraries you should share across microservices.</span></span> <span data-ttu-id="64a13-140">1 つは、ライブラリと同様に、最終的なアプリケーション ブロックである、[イベント バス クライアント API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus)eShopOnContainers のように、します。</span><span class="sxs-lookup"><span data-stu-id="64a13-140">One is libraries that are final application blocks, like the [Event Bus client API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus), as in eShopOnContainers.</span></span> <span data-ttu-id="64a13-141">他にもさらに JSON シリアライザーなどの NuGet コンポーネントとして共有することがツールを構成するライブラリ。</span><span class="sxs-lookup"><span data-stu-id="64a13-141">Another is libraries that constitute tools that could also be shared as NuGet components, like JSON serializers.</span></span>

## <a name="the-event-bus"></a><span data-ttu-id="64a13-142">イベント バス</span><span class="sxs-lookup"><span data-stu-id="64a13-142">The event bus</span></span>

<span data-ttu-id="64a13-143">イベント バスは、明示的に認識する、他の図 8-19 に示すようにコンポーネントを必要とせず microservices 間パブリッシュ/サブスクライブ スタイルの通信を許可します。</span><span class="sxs-lookup"><span data-stu-id="64a13-143">An event bus allows publish/subscribe-style communication between microservices without requiring the components to explicitly be aware of each other, as shown in Figure 8-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="64a13-144">**図 8-19**です。</span><span class="sxs-lookup"><span data-stu-id="64a13-144">**Figure 8-19**.</span></span> <span data-ttu-id="64a13-145">イベント バスの基礎のパブリッシュ/サブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="64a13-145">Publish/subscribe basics with an event bus</span></span>

<span data-ttu-id="64a13-146">オブザーバー パターンと、発行に関連するイベント バスの定期受信パターン。</span><span class="sxs-lookup"><span data-stu-id="64a13-146">The event bus is related to the Observer pattern and the publish-subscribe pattern.</span></span>

### <a name="observer-pattern"></a><span data-ttu-id="64a13-147">オブザーバー パターン</span><span class="sxs-lookup"><span data-stu-id="64a13-147">Observer pattern</span></span>

<span data-ttu-id="64a13-148">[オブザーバー パターン](https://en.wikipedia.org/wiki/Observer_pattern)、(監視対象と呼ばれます)、プライマリ オブジェクトに関連する情報 (イベント) (オブザーバーと呼ばれる) その他の対象となるオブジェクトに通知します。</span><span class="sxs-lookup"><span data-stu-id="64a13-148">In the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern), your primary object (known as the Observable) notifies other interested objects (known as Observers) with relevant information (events).</span></span>

### <a name="publish-subscribe-pubsub-pattern"></a><span data-ttu-id="64a13-149">(パブリッシュ/サブスクライブ) の発行/定期受信パターン</span><span class="sxs-lookup"><span data-stu-id="64a13-149">Publish-subscribe (Pub/Sub) pattern</span></span> 

<span data-ttu-id="64a13-150">目的は、[パブリッシュ/サブスクライブ パターン](https://msdn.microsoft.com/en-us/library/ff649664.aspx)オブザーバー パターンと同じです。 特定のイベントが発生する場合は、他のサービスを通知します。</span><span class="sxs-lookup"><span data-stu-id="64a13-150">The purpose of the [Pub/Sub pattern](https://msdn.microsoft.com/en-us/library/ff649664.aspx) is the same as the Observer pattern: you want to notify other services when certain events take place.</span></span> <span data-ttu-id="64a13-151">重要な意味上の違い、オブザーバーおよびパブリッシュ/サブスクライブ パターン。</span><span class="sxs-lookup"><span data-stu-id="64a13-151">But there is an important semantic difference between the Observer and Pub/Sub patterns.</span></span> <span data-ttu-id="64a13-152">パブリッシュ/サブスクライブ パターンでは、メッセージをブロードキャストにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="64a13-152">In the Pub/Sub pattern, the focus is on broadcasting messages.</span></span> <span data-ttu-id="64a13-153">これに対し、オブザーバー パターンでは、観測可能なオブジェクトは認識しないイベントが組み込まれて、out になっていること。つまり、観測可能なオブジェクト (パブリッシャー) は認識しないオブザーバー (サブスクライバー) であります。</span><span class="sxs-lookup"><span data-stu-id="64a13-153">In contrast, in the Observer pattern, the Observable does not know who the events are going to, just that they have gone out. In other words, the Observable (the publisher) does not know who the Observers (the subscribers) are.</span></span>

### <a name="the-middleman-or-event-bus"></a><span data-ttu-id="64a13-154">仲介者またはイベント バス</span><span class="sxs-lookup"><span data-stu-id="64a13-154">The middleman or event bus</span></span> 

<span data-ttu-id="64a13-155">パブリッシャーとサブスクライバー間で匿名性を実現するには</span><span class="sxs-lookup"><span data-stu-id="64a13-155">How do you achieve anonymity between publisher and subscriber?</span></span> <span data-ttu-id="64a13-156">簡単な方法は、すべての通信を処理する仲介者を使用できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-156">An easy way is let a middleman take care of all the communication.</span></span> <span data-ttu-id="64a13-157">イベント バスは、このような 1 つの仲介者です。</span><span class="sxs-lookup"><span data-stu-id="64a13-157">An event bus is one such middleman.</span></span>

<span data-ttu-id="64a13-158">イベント バスは通常、2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-158">An event bus is typically composed of two parts:</span></span>

-   <span data-ttu-id="64a13-159">抽象またはインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="64a13-159">The abstraction or interface.</span></span>

-   <span data-ttu-id="64a13-160">1 つまたは複数の実装です。</span><span class="sxs-lookup"><span data-stu-id="64a13-160">One or more implementations.</span></span>

<span data-ttu-id="64a13-161">図 8-19 方法、アプリケーションの観点から、イベント バスがわかります Pub/sub チャネルより詳細に何も行われません。</span><span class="sxs-lookup"><span data-stu-id="64a13-161">In Figure 8-19 you can see how, from an application point of view, the event bus is nothing more than a Pub/Sub channel.</span></span> <span data-ttu-id="64a13-162">この非同期通信を実装する方法が異なることができます。</span><span class="sxs-lookup"><span data-stu-id="64a13-162">The way you implement this asynchronous communication can vary.</span></span> <span data-ttu-id="64a13-163">複数の実装は、環境の要件 (たとえば、開発環境と運用) によってそれらの間で交換できるようにことができます。</span><span class="sxs-lookup"><span data-stu-id="64a13-163">It can have multiple implementations so that you can swap between them, depending on the environment requirements (for example, production versus development environments).</span></span>

<span data-ttu-id="64a13-164">図 8-20 RabbitMQ、Azure サービス バス、または他のサービス バスと NServiceBus、MassTransit などのようなテクノロジをメッセージング インフラストラクチャに基づいて複数の実装では、イベント バスの抽象化を確認できます。</span><span class="sxs-lookup"><span data-stu-id="64a13-164">In Figure 8-20 you can see an abstraction of an event bus with multiple implementations based on infrastructure messaging technologies like RabbitMQ, Azure Service Bus, or other service buses like NServiceBus, MassTransit, etc.</span></span>

![](./media/image21.png)

<span data-ttu-id="64a13-165">**図 8-20 です。**</span><span class="sxs-lookup"><span data-stu-id="64a13-165">**Figure 8- 20.**</span></span> <span data-ttu-id="64a13-166">イベント バスの複数の実装</span><span class="sxs-lookup"><span data-stu-id="64a13-166">Multiple implementations of an event bus</span></span>

<span data-ttu-id="64a13-167">ただし、強調表示されている以前は、抽象化 (イベント バス インターフェイス) を使用するは、抽象化でサポートされている基本イベント バスの機能が必要な場合にのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="64a13-167">However, as highlighted previously, using abstractions (the event bus interface) is possible only if you need basic event bus features supported by your abstractions.</span></span> <span data-ttu-id="64a13-168">豊富なサービス バス機能を必要がある場合は、独自の抽象化ではなく、優先するサービス バスが提供する API を使用する必要があります可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-168">If you need richer service bus features, you should probably use the API provided by your preferred service bus instead of your own abstractions.</span></span>

### <a name="defining-an-event-bus-interface"></a><span data-ttu-id="64a13-169">イベント バス インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="64a13-169">Defining an event bus interface</span></span>

<span data-ttu-id="64a13-170">いくつか実装コードは、イベント バス インターフェイスと探索のための可能な実装から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="64a13-170">Let’s start with some implementation code for the event bus interface and possible implementations for exploration purposes.</span></span> <span data-ttu-id="64a13-171">インターフェイスは、汎用的な単純ですが、次のインターフェイスのようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-171">The interface should be generic and straightforward, as in the following interface.</span></span>

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

<span data-ttu-id="64a13-172">発行方法は簡単です。</span><span class="sxs-lookup"><span data-stu-id="64a13-172">The Publish method is straightforward.</span></span> <span data-ttu-id="64a13-173">イベント バスは、そのイベントにサブスクライブしている任意のマイクロ サービスに渡された統合イベントをブロードキャストします。</span><span class="sxs-lookup"><span data-stu-id="64a13-173">The event bus will broadcast the integration event passed to it to any microservice subscribed to that event.</span></span> <span data-ttu-id="64a13-174">このメソッドは、イベントをパブリッシュしているマイクロ サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="64a13-174">This method is used by the microservice that is publishing the event.</span></span>

<span data-ttu-id="64a13-175">イベントを受信する microservices Subscribe メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="64a13-175">The Subscribe method is used by the microservices that want to receive events.</span></span> <span data-ttu-id="64a13-176">このメソッドには、2 つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="64a13-176">This method has two parts.</span></span> <span data-ttu-id="64a13-177">最初は、(IntegrationEvent) を購読する統合イベントです。</span><span class="sxs-lookup"><span data-stu-id="64a13-177">The first is the integration event to subscribe to (IntegrationEvent).</span></span> <span data-ttu-id="64a13-178">2 番目の部分は、統合イベントのハンドラー (コールバック メソッド) を呼び出せる (IIntegrationEventHandler&lt;T&gt;)、マイクロ サービスがその統合イベント メッセージを受信するとします。</span><span class="sxs-lookup"><span data-stu-id="64a13-178">The second part is the integration event handler (or callback method) to be called (IIntegrationEventHandler&lt;T&gt;) when the microservice receives that integration event message.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="64a13-179">[前](データベースのサーバー-container.md) [次へ] (rabbitmq-event-bus-development-test-environment.md)</span><span class="sxs-lookup"><span data-stu-id="64a13-179">[Previous] (database-server-container.md) [Next] (rabbitmq-event-bus-development-test-environment.md)</span></span>
