---
title: "ドメインのイベントです。 設計と実装"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ドメインのイベント、設計と実装"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 2d98b302be4ee72d8225526944fc3e41cbadcb5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="domain-events-design-and-implementation"></a><span data-ttu-id="f8df0-105">ドメインのイベント: 設計と実装</span><span class="sxs-lookup"><span data-stu-id="f8df0-105">Domain events: design and implementation</span></span>

<span data-ttu-id="f8df0-106">ドメイン内で変更の副作用を明示的に実装するのにには、ドメインのイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-106">Use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="f8df0-107">その他の語と DDD 用語を使用して、複数の集計の間での副作用を明示的に実装するのにドメイン イベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-107">In other words, and using DDD terminology, use domain events to explicitly implement side effects across multiple aggregates.</span></span> <span data-ttu-id="f8df0-108">必要に応じて、スケーラビリティが向上し、データベースのロックの影響を軽減は、同じドメイン内の集計の間で最終的整合性を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-108">Optionally, for better scalability and less impact in database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="what-is-a-domain-event"></a><span data-ttu-id="f8df0-109">ドメインのイベントとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="f8df0-109">What is a domain event?</span></span>

<span data-ttu-id="f8df0-110">イベントは、過去に発生したものです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-110">An event is something that has happened in the past.</span></span> <span data-ttu-id="f8df0-111">ドメインのイベントは、論理的には、特定のドメインで発生した、同じドメイン (インプロセス) を認識し、潜在的に対応するための他の部分を何かたいとします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-111">A domain event is, logically, something that happened in a particular domain, and something you want other parts of the same domain (in-process) to be aware of and potentially react to.</span></span>

<span data-ttu-id="f8df0-112">ドメインのイベントの重要な利点は、暗黙的にではなく副作用後、ドメインに問題が発生しましたを明示的に表現することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-112">An important benefit of domain events is that side effects after something happened in a domain can be expressed explicitly instead of implicitly.</span></span> <span data-ttu-id="f8df0-113">効果必要があります一貫性のある、すべての操作、ビジネス タスクに関連する発生する可能性がそれらの側かのいずれかにします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-113">Those side effects must be consistent so either all the operations related to the business task happen, or none of them.</span></span> <span data-ttu-id="f8df0-114">さらに、ドメインのイベントには、同じドメイン内のクラス間で問題の分離を強化しが有効にします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-114">In addition, domain events enable a better separation of concerns among classes within the same domain.</span></span>

<span data-ttu-id="f8df0-115">たとえば、ユース ケースによって生じる副作用である必要がある場合にだけ、Entity Framework とエンティティまたは偶数の集計だけを使用する場合、ものとして実装されます、結合されたコードでの暗黙的な概念後、問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f8df0-115">For example, if you are just using just Entity Framework and entities or even aggregates, if there have to be side effects provoked by a use case, those will be implemented as an implicit concept in the coupled code after something happened.</span></span> <span data-ttu-id="f8df0-116">ただし、のみが表示コードをわからない場合があります (副作用) そのコードがメインの操作の一部である場合、または副作用ですか。</span><span class="sxs-lookup"><span data-stu-id="f8df0-116">But, if you just see that code, you might not know if that code (the side effect) is part of the main operation or if it really is a side effect.</span></span> <span data-ttu-id="f8df0-117">その一方で、ドメインのイベントを使用して、概念明示的なとユビキタス言語の一部。</span><span class="sxs-lookup"><span data-stu-id="f8df0-117">On the other hand, using domain events makes the concept explicit and part of the ubiquitous language.</span></span> <span data-ttu-id="f8df0-118">たとえば、eShopOnContainers アプリケーションで注文を作成するはほぼ順序です。更新またはユーザーにないため、購入者に注文があるまで、元のユーザーに基づく buyer の集計を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-118">For example, in the eShopOnContainers application, creating an order is not just about the order; it updates or creates a buyer aggregate based on the original user, because the user is not a buyer until there is an order in place.</span></span> <span data-ttu-id="f8df0-119">ドメインのイベントを使用する場合は、ドメインの専門家によって提供されるユビキタス言語に基づく、ドメイン ルールを明示的に表現できます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-119">If you use domain events, you can explicitly express that domain rule based in the ubiquitous language provided by the domain experts.</span></span>

<span data-ttu-id="f8df0-120">ドメイン イベントは、1 つの重要な相違点のメッセージング スタイルのイベントに似ています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-120">Domain events are somewhat similar to messaging-style events, with one important difference.</span></span> <span data-ttu-id="f8df0-121">実際のメッセージング、メッセージ キュー、メッセージ ブローカーまたは AMPQ を使用して、サービス バス、メッセージは常に非同期的に送信し、プロセスとマシンの間で通信します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-121">With real messaging, message queuing, message brokers, or a service bus using AMPQ, a message is always sent asynchronously and communicated across processes and machines.</span></span> <span data-ttu-id="f8df0-122">これは、複数のコンテキストの境界を付けられた、microservices、または別のアプリケーションを統合するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-122">This is useful for integrating multiple Bounded Contexts, microservices, or even different applications.</span></span> <span data-ttu-id="f8df0-123">ただし、ドメインのイベント、現在実行しているドメイン操作からイベントを発生するが、同じドメイン内に発生するすべての副作用をします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-123">However, with domain events, you want to raise an event from the domain operation you are currently running, but you want any side effects to occur within the same domain.</span></span>

<span data-ttu-id="f8df0-124">ドメインのイベントとその副作用 (実行されたアクション後のイベント ハンドラーで管理されている) をほぼ即座に実行する通常のプロセス、および同じドメイン内で。</span><span class="sxs-lookup"><span data-stu-id="f8df0-124">The domain events and their side effects (the actions triggered afterwards that are managed by event handlers) should occur almost immediately, usually in-process, and within the same domain.</span></span> <span data-ttu-id="f8df0-125">したがって、ドメインのイベントは、同期または非同期可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-125">Thus, domain events could be synchronous or asynchronous.</span></span> <span data-ttu-id="f8df0-126">統合イベント、ただしは常に非同期です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-126">Integration events, however, should always be asynchronous.</span></span>

## <a name="domain-events-versus-integration-events"></a><span data-ttu-id="f8df0-127">統合イベントではなくドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="f8df0-127">Domain events versus integration events</span></span>

<span data-ttu-id="f8df0-128">ドメインとの統合のイベントは、同じことを意味します。 だけ発生した問題に関する通知。</span><span class="sxs-lookup"><span data-stu-id="f8df0-128">Semantically, domain and integration events are the same thing: notifications about something that just happened.</span></span> <span data-ttu-id="f8df0-129">ただし、その実装は異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-129">However, their implementation must be different.</span></span> <span data-ttu-id="f8df0-130">ドメインのイベントは、IoC コンテナーまたはその他のメソッドに基づくメモリの媒介として実装される可能性がありますドメインのイベント ディスパッチャーにプッシュされただけのメッセージです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-130">Domain events are just messages pushed to a domain event dispatcher, which could be implemented as an in-memory mediator based on an IoC container or any other method.</span></span>

<span data-ttu-id="f8df0-131">その一方で、統合イベントの目的は、や他の microservices、範囲指定されたコンテキストでも外部アプリケーションでかどうかにコミットされたトランザクションとその他のサブシステムへの更新が反映されるまでです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-131">On the other hand, the purpose of integration events is to propagate committed transactions and updates to additional subsystems, whether they are other microservices, Bounded Contexts or even external applications.</span></span> <span data-ttu-id="f8df0-132">それらを実行するため、エンティティが正常に保存されている場合から多くのシナリオでこれが失敗した場合は、操作全体効果的がなかったかのみです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-132">Hence, they should occur only if the entity is successfully persisted, since in many scenarios if this fails, the entire operation effectively never happened.</span></span>

<span data-ttu-id="f8df0-133">説明したように、統合とさらに、イベントを複数の microservices (他の境界を付けられたコンテキスト) またはも外部システムとアプリケーション間の非同期通信に基づいている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-133">In addition, and as mentioned, integration events must be based on asynchronous communication between multiple microservices (other Bounded Contexts) or even external systems/applications.</span></span> <span data-ttu-id="f8df0-134">したがって、イベント バス インターフェイスには、プロセス間では、可能性のあるリモート サービスの間の通信を分散するインフラストラクチャの一部が必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-134">Thus, the event bus interface needs some infrastructure that allows inter-process and distributed communication between potentially remote services.</span></span> <span data-ttu-id="f8df0-135">商用サービス バス、キュー、メールボックスとして使用される共有データベースまたはその他の分散に基づくことができ、理想的にはベースのメッセージング システムをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-135">It can be based on a commercial service bus, queues, a shared database used as a mailbox, or any other distributed and ideally push based messaging system.</span></span>

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a><span data-ttu-id="f8df0-136">同じドメイン内の複数の集計の間での副作用をトリガーする方法をお勧めとしてドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="f8df0-136">Domain events as a preferred way to trigger side effects across multiple aggregates within the same domain</span></span>

<span data-ttu-id="f8df0-137">集計インスタンスには、1 つまたは複数の他の集計で実行する追加のドメイン ルールが必要です。 いずれかに関連するコマンドを実行している場合は、設計およびドメインのイベントによってトリガーされるこれらの副作用を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-137">If executing a command related to one aggregate instance requires additional domain rules to be run on one or more additional aggregates, you should design and implement those side effects to be triggered by domain events.</span></span> <span data-ttu-id="f8df0-138">図 9-14 に示すように、最も重要なの 1 つとしてユース ケース、ドメイン イベントは、同じドメイン モデル内の複数の集計の状態の変更を伝達するために使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-138">As shown in Figure 9-14, and as one of the most important use cases, a domain event should be used to propagate state changes across multiple aggregates within the same domain model.</span></span>

![](./media/image15.png)

<span data-ttu-id="f8df0-139">**図 9-14**です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-139">**Figure 9-14**.</span></span> <span data-ttu-id="f8df0-140">同じドメイン内の複数の集計の間の整合性のためにドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="f8df0-140">Domain events to enforce consistency between multiple aggregates within the same domain</span></span>

<span data-ttu-id="f8df0-141">図では、ユーザーは、注文を開始したときに、OrderStarted ドメイン イベントは情報と共に、CreateOrder コマンドで identity マイクロ サービスから元のユーザー情報に基づく順序マイクロ サービスの購入者オブジェクトの作成をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-141">In the figure, when the user initiates an order, the OrderStarted domain event triggers creation of a Buyer object in the ordering microservice, based on the original user info from the identity microservice (with information provided in the CreateOrder command).</span></span> <span data-ttu-id="f8df0-142">ドメインのイベントは、最初の場所の作成時に、順序集計によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-142">The domain event is generated by the order aggregate when it is created in the first place.</span></span>

<span data-ttu-id="f8df0-143">代わりに、その集計 (子エンティティ) のメンバーによって発生するイベントを定期受信されている集計ルートを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-143">Alternately, you can have the aggregate root subscribed for events raised by members of its aggregates (child entities).</span></span> <span data-ttu-id="f8df0-144">たとえば、各 OrderItem 子エンティティは、品目の価格は、特定の容量を超えた場合、または製品品目の量が高すぎるとに、イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-144">For instance, each OrderItem child entity can raise an event when the item price is higher than a specific amount, or when the product item amount is too high.</span></span> <span data-ttu-id="f8df0-145">集計のルートは、これらのイベントを受信し、グローバルの計算または集計を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-145">The aggregate root can then receive those events and perform a global calculation or aggregation.</span></span>

<span data-ttu-id="f8df0-146">このイベント ベースの通信が; 集計内で直接実装していないことを理解することが重要ドメインのイベント ハンドラーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-146">It is important to understand that this event-based communication is not implemented directly within the aggregates; you need to implement domain event handlers.</span></span> <span data-ttu-id="f8df0-147">イベントを処理するドメインは、アプリケーション問題です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-147">Handling the domain events is an application concern.</span></span> <span data-ttu-id="f8df0-148">ドメイン モデル レイヤーが、ドメイン ロジックに専念する必要がありますのみ — ドメインの専門家が理解できるようにすること、ハンドラーおよびリポジトリを使用して、副作用が永続性アクションなど、アプリケーション インフラストラクチャされません。</span><span class="sxs-lookup"><span data-stu-id="f8df0-148">The domain model layer should only focus on the domain logic—things that a domain expert would understand, not application infrastructure like handlers and side-effect persistence actions using repositories.</span></span> <span data-ttu-id="f8df0-149">したがって、アプリケーション層のレベルは、ドメインのイベントが発生したときにアクションをトリガーするドメインのイベント ハンドラーを持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-149">Therefore, the application layer level is where you should have domain event handlers triggering actions when a domain event is raised.</span></span>

<span data-ttu-id="f8df0-150">ドメインのイベントは、任意の数のアプリケーションのアクションをトリガーするも使用できより重要な数を増やすにその後で、分離された方法で開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-150">Domain events can also be used to trigger any number of application actions, and what is more important, must be open to increase that number in the future in a decoupled way.</span></span> <span data-ttu-id="f8df0-151">たとえば、順序が開始されると、ことができますをその他の集計には、その情報を伝達する、または通知のようにアプリケーションのアクションを発生させる場合にもドメイン イベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-151">For instance, when the order is started, you might want to publish a domain event to propagate that info to other aggregates or even to raise application actions like notifications.</span></span>

<span data-ttu-id="f8df0-152">重要な点は、ドメインのイベントが発生したときに実行されるアクションの開いている数です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-152">The key point is the open number of actions to be executed when a domain event occurs.</span></span> <span data-ttu-id="f8df0-153">最終的には、アクションと、ドメインおよびアプリケーション内のルールが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-153">Eventually, the actions and rules in the domain and application will grow.</span></span> <span data-ttu-id="f8df0-154">複雑さや問題が起こったときに副作用がアクションの数が増大、コードが「グルー」を伴う場合は (つまり、C では、new キーワードを持つオブジェクトをインスタンス化だけ\#)、たびに、新しいアクションを追加する必要とする必要があります。元のコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-154">The complexity or number of side-effect actions when something happens will grow, but if your code were coupled with “glue” (that is, just instantiating objects with the new keyword in C\#), then every time you needed to add a new action you would need to change the original code.</span></span> <span data-ttu-id="f8df0-155">これは、結果、新しいバグは、各新しい要件が必要になる元のコードのフロー方向を変更します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-155">This could result in new bugs, because with each new requirement you would need to change the original code flow.</span></span> <span data-ttu-id="f8df0-156">これには、に対して、[開く/解決済みの原則](https://en.wikipedia.org/wiki/Open/closed_principle)から[ソリッド](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-156">This goes against the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) from [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)).</span></span> <span data-ttu-id="f8df0-157">それだけでなく、操作を対象に調整された元のクラスは拡張し、拡大、に対してに出向いて、[単一責任原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle)です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-157">Not only that, the original class that was orchestrating the operations would grow and grow, which goes against the [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).</span></span>

<span data-ttu-id="f8df0-158">その一方で、ドメインのイベントを使用する場合は、このアプローチを使用する責任を隔離することによって粒度の細かいと分離の実装を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-158">On the other hand, if you use domain events, you can create a fine-grained and decoupled implementation by segregating responsibilities using this approach:</span></span>

1.  <span data-ttu-id="f8df0-159">コマンド (たとえば、CreateOrder) を送信します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-159">Send a command (for example, CreateOrder).</span></span>
2.  <span data-ttu-id="f8df0-160">コマンド ハンドラーで、コマンドを受信します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-160">Receive the command in a command handler.</span></span>
    -   <span data-ttu-id="f8df0-161">1 つの集計のトランザクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-161">Execute a single aggregate’s transaction.</span></span>
    -   <span data-ttu-id="f8df0-162">(省略可能)副作用 (たとえば、OrderStartedDomainDvent) のドメインのイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-162">(Optional) Raise domain events for side effects (for example, OrderStartedDomainDvent).</span></span>
1.  <span data-ttu-id="f8df0-163">ハンドル ドメイン (現在のプロセス) 内のイベント thast は複数の集計またはアプリケーションのアクションの副作用のオープンの数を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-163">Handle domain events (within the current process) thast will execute an open number of side effects in multiple aggregates or application actions.</span></span> <span data-ttu-id="f8df0-164">例:</span><span class="sxs-lookup"><span data-stu-id="f8df0-164">For example:</span></span>
    -   <span data-ttu-id="f8df0-165">確認するか、購入者および支払方法を作成します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-165">Verify or create buyer and payment method.</span></span>
    -   <span data-ttu-id="f8df0-166">作成し、購入者に電子メールを送信するように microservices またはトリガーの外部アクション間で状態を反映する、イベント バスに関連する統合イベントを送信します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-166">Create and send a related integration event to the event bus to propagate states across microservices or trigger external actions like sending an email to the buyer.</span></span>
    -   <span data-ttu-id="f8df0-167">その他の副作用を処理します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-167">Handle other side effects.</span></span>

<span data-ttu-id="f8df0-168">図 9-15 を示すように、同じドメインのイベントから開始処理すること、ドメインまたは統合イベントおよびイベント バスに接続する microservices 全体を実行する必要があります。 追加のアプリケーション操作には、その他の集計に関連する複数のアクション。</span><span class="sxs-lookup"><span data-stu-id="f8df0-168">As shown in Figure 9-15, starting from the same domain event, you can handle multiple actions related to other aggregates in the domain or additional application actions you need to perform across microservices connecting with integration events and the event bus.</span></span>

![](./media/image16.png)

<span data-ttu-id="f8df0-169">**図 9-15**です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-169">**Figure 9-15**.</span></span> <span data-ttu-id="f8df0-170">ドメインごとの複数のアクションの処理</span><span class="sxs-lookup"><span data-stu-id="f8df0-170">Handling multiple actions per domain</span></span>

<span data-ttu-id="f8df0-171">イベント ハンドラーは通常、アプリケーション レイヤーでマイクロ サービスの動作のリポジトリまたはアプリケーションの API などのインフラストラクチャ オブジェクトを使用するためです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-171">The event handlers are typically in the application layer, because you will use infrastructure objects like repositories or an application API for the microservice’s behavior.</span></span> <span data-ttu-id="f8df0-172">その意味で、イベント ハンドラーは、どちらも、アプリケーション層の一部であるためコマンド ハンドラーに似ています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-172">In that sense, event handlers are similar to command handlers, so both are part of the application layer.</span></span> <span data-ttu-id="f8df0-173">重要な相違点は、コマンドを 1 回だけ処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-173">The important difference is that a command should be processed just once.</span></span> <span data-ttu-id="f8df0-174">ドメイン イベント可能性がありますゼロを処理または *n* ためにがタイムアウトと場合、によって複数の受信器または各ハンドラーに対して別の目的でイベント ハンドラーを受信することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-174">A domain event could be processed zero or *n* times, because if can be received by multiple receivers or event handlers with a different purpose for each handler.</span></span>

<span data-ttu-id="f8df0-175">数が開いている各ドメインのイベント ハンドラーの可能性には、現在コードに影響を与えずに多くのドメイン ルールを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-175">The possibility of an open number of handlers per domain event allows you to add many more domain rules without impacting your current code.</span></span> <span data-ttu-id="f8df0-176">たとえば、右側に発生するイベントの後に次のビジネス ルールを実装するが、いくつかのイベント ハンドラー (または 1 つのみでも) を追加することと同じくらい簡単可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-176">For instance, implementing the following business rule that has to happen right after an event might be as easy as adding a few event handlers (or even just one):</span></span>

<span data-ttu-id="f8df0-177">任意の数、注文の間で、ストアで顧客が購入合計金額が $6,000 を超える場合は、割引は 10% をすべて新しい注文に適用され、そのに割引された料金未来の注文に関する電子メールを顧客に通知します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-177">When the total amount purchased by a customer in the store, across any number of orders, exceeds $6,000, apply a 10% off discount to every new order and notify the customer with an email about that discount for future orders.</span></span>

## <a name="implementing-domain-events"></a><span data-ttu-id="f8df0-178">ドメインのイベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-178">Implementing domain events</span></span>

<span data-ttu-id="f8df0-179">C# の場合は、ドメイン イベントだけで、データを保持構造体またはクラスでは、次の例で示すように、ドメインでの発生に関連するすべての情報を DTO と同様に。</span><span class="sxs-lookup"><span data-stu-id="f8df0-179">In C#, a domain event is simply a data-holding structure or class, like a DTO, with all the information related to what just happened in the domain, as shown in the following example:</span></span>

```csharp
public class OrderStartedDomainEvent : IAsyncNotification
{
    public int CardTypeId { get; private set; }
    public string CardNumber { get; private set; }
    public string CardSecurityNumber { get; private set; }
    public string CardHolderName { get; private set; }
    public DateTime CardExpiration { get; private set; }
    public Order Order { get; private set; }

    public OrderStartedDomainEvent(Order order,
        int cardTypeId, string cardNumber,
        string cardSecurityNumber, string cardHolderName,
        DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

<span data-ttu-id="f8df0-180">これは、本質的に OrderStarted イベントに関連するすべてのデータを保持するクラスです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-180">This is essentially a class that holds all the data related to the OrderStarted event.</span></span>

<span data-ttu-id="f8df0-181">ドメインの場所を問わず、言語の観点から イベントは、以前は、発生したため、イベントのクラス名は、OrderStartedDomainEvent OrderShippedDomainEvent などの過去形動詞として表さ必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-181">In terms of the ubiquitous language of the domain, since an event is something that happened in the past, the class name of the event should be represented as a past-tense verb, like OrderStartedDomainEvent or OrderShippedDomainEvent.</span></span> <span data-ttu-id="f8df0-182">EShopOnContainers で順序付けマイクロ サービスでドメインのイベントを実装する方法です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-182">That is how the domain event is implemented in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="f8df0-183">触れましたが、イベントの重要な特性をイベントとは、変更しないでください、過去に発生したためです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-183">As we have noted, an important characteristic of events is that since an event is something that happened in the past, it should not change.</span></span> <span data-ttu-id="f8df0-184">したがって、変更できないクラスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-184">Therefore it must be an immutable class.</span></span> <span data-ttu-id="f8df0-185">プロパティは読み取り専用からオブジェクトの外部で上記のコードで確認できます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-185">You can see in the preceding code that the properties are read-only from outside of the object.</span></span> <span data-ttu-id="f8df0-186">オブジェクトを更新する唯一の方法は、イベント オブジェクトを作成するときに、コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-186">The only way to update the object is through the constructor when you create the event object.</span></span>

### <a name="raising-domain-events"></a><span data-ttu-id="f8df0-187">ドメインのイベントを発生させる</span><span class="sxs-lookup"><span data-stu-id="f8df0-187">Raising domain events</span></span>

<span data-ttu-id="f8df0-188">次の質問は、その関連するイベント ハンドラーに到達するためにドメイン イベントを発生させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-188">The next question is how to raise a domain event so it reaches its related event handlers.</span></span> <span data-ttu-id="f8df0-189">複数の方法を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-189">You can use multiple approaches.</span></span>

<span data-ttu-id="f8df0-190">Udi Dahan が最初に提案された (など、複数の関連する投稿など[イベントのドメインを 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) を管理して、イベントを発生させるため、静的クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-190">Udi Dahan originally proposed (for example, in several related posts, such as [Domain Events – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) using a static class for managing and raising the events.</span></span> <span data-ttu-id="f8df0-191">静的という名前のクラスがイベントを発生させるドメイン、呼び出された場合にすぐに DomainEvents DomainEvents.Raise (イベント myEvent) のような構文を使用してこのことがあります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-191">This might include a static class named DomainEvents that would raise domain events immediately when it is called, using syntax like DomainEvents.Raise(Event myEvent).</span></span> <span data-ttu-id="f8df0-192">Jimmy Bogard 書いたブログ投稿 ([、ドメインの強化: ドメイン イベント](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/))、同様のアプローチすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-192">Jimmy Bogard wrote a blog post ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) that recommends a similar approach.</span></span>

<span data-ttu-id="f8df0-193">ただし、ドメインのイベント クラスの静的な場合にもディスパッチ ハンドラーにすぐにします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-193">However, when the domain events class is static, it also dispatches to handlers immediately.</span></span> <span data-ttu-id="f8df0-194">これにより、テストおよびデバッグが難しく、副作用のロジックを持つイベント ハンドラーは、イベントが発生した後すぐに実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-194">This makes testing and debugging more difficult, because the event handlers with side-effects logic are executed immediately after the event is raised.</span></span> <span data-ttu-id="f8df0-195">フォーカスとだけ何が起こっているか、現在の集計クラスでするテスト、デバッグしているときに突然にリダイレクトするその他の集計またはアプリケーション ロジックに関連する副作用の他のイベント ハンドラーはしません。</span><span class="sxs-lookup"><span data-stu-id="f8df0-195">When you are testing and debugging, you want to focus on and just what is happening in the current aggregate classes; you do not want to suddenly be redirected to other event handlers for side effects related to other aggregates or application logic.</span></span> <span data-ttu-id="f8df0-196">これによっては他のアプローチが進化に伴い、理由は、次のセクションで説明したようです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-196">This is why other approaches have evolved, as explained in the next section.</span></span>

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a><span data-ttu-id="f8df0-197">遅延を発生させると、イベントのディスパッチのアプローチ</span><span class="sxs-lookup"><span data-stu-id="f8df0-197">The deferred approach for raising and dispatching events</span></span>

<span data-ttu-id="f8df0-198">ドメインのイベント ハンドラーにすぐにディスパッチなどではなくより適切な方法がイベントを追加する、ドメインのコレクションには、そのドメインのこれらのイベントをディスパッチするために*直前*または*右* *後*(EF に SaveChanges) と同様に、トランザクションをコミットします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-198">Instead of dispatching to a domain event handler immediately, a better approach is to add the domain events to a collection and then to dispatch those domain events *right before* or *right* *after* committing the transaction (as with SaveChanges in EF).</span></span> <span data-ttu-id="f8df0-199">(このアプローチは、この投稿の Jimmy Bogard によって説明された[向上ドメインのイベント パターン](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/))。</span><span class="sxs-lookup"><span data-stu-id="f8df0-199">(This approach was described by Jimmy Bogard in this post [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)</span></span>

<span data-ttu-id="f8df0-200">ドメインのイベントを送信するかどうかを決定するトランザクションをコミットした後に右の前に、または右は重要ですが、または別のトランザクションで同じトランザクションの一部として、副作用を含めるかどうかを決定するためです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-200">Deciding if you send the domain events right before or right after committing the transaction is important, since it determines whether you will include the side effects as part of the same transaction or in different transactions.</span></span> <span data-ttu-id="f8df0-201">後者の場合、複数の集計で最終的整合性に対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-201">In the latter case, you need to deal with eventual consistency across multiple aggregates.</span></span> <span data-ttu-id="f8df0-202">このトピックは、次のセクションで説明しています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-202">This topic is discussed in the next section.</span></span>

<span data-ttu-id="f8df0-203">遅延のアプローチは、どのような eShopOnContainers 使用です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-203">The deferred approach is what eShopOnContainers uses.</span></span> <span data-ttu-id="f8df0-204">最初に、コレクションまたはエンティティごとのイベントの一覧に、エンティティで行われているイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-204">First, you add the events happening in your entities into a collection or list of events per entity.</span></span> <span data-ttu-id="f8df0-205">その一覧には、次の例のように、エンティティ オブジェクトの一部またはさらに、基本エンティティ クラスの一部をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-205">That list should be part of the entity object, or even better, part of your base entity class, as shown in the following example:</span></span>

```csharp
public abstract class Entity
{
    private List<IAsyncNotification> _domainEvents;

    public List<IAsyncNotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(IAsyncNotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<IAsyncNotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(IAsyncNotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

<span data-ttu-id="f8df0-206">イベントを発生させる場合は、単に追加するコードを次に示すように、集計 entity メソッド内に配置するイベントの収集。</span><span class="sxs-lookup"><span data-stu-id="f8df0-206">When you want to raise an event, you just add it to the event collection to be placed within an aggregate entity method, as the following code shows:</span></span>

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
    cardTypeId,
    cardNumber,
    cardSecurityNumber,
    cardHolderName,
    cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

<span data-ttu-id="f8df0-207">AddDomainEvent メソッドを行っていることだけが一覧に、イベントを追加することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f8df0-207">Notice that the only thing that the AddDomainEvent method is doing is adding an event to the list.</span></span> <span data-ttu-id="f8df0-208">イベントは生成されませんまだ、およびイベント ハンドラーは呼び出されませんまだです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-208">No event is raised yet, and no event handler is invoked yet.</span></span>

<span data-ttu-id="f8df0-209">実際にするデータベースへのトランザクションをコミットする場合、後で、イベントをディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-209">You actually want to dispatch the events later on, when you commit the transaction to the database.</span></span> <span data-ttu-id="f8df0-210">Entity Framework のコアを使用している場合は、次のコードと同様に、EF DbContext の SaveChanges メソッドでします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-210">If you are using Entity Framework Core, that means in the SaveChanges method of your EF DbContext, as in the following code:</span></span>

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<int> SaveEntitiesAsync()
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);
        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

<span data-ttu-id="f8df0-211">このコードでは、それぞれのそれぞれのイベント ハンドラーにエンティティのイベントをディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-211">With this code, you dispatch the entity events to their respective event handlers.</span></span>

<span data-ttu-id="f8df0-212">全体の結果は、ことが分離 (単純なリストに追加のメモリに) ドメインのイベントの発生からイベント ハンドラーにディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-212">The overall result is that you have decoupled the raising of a domain event (a simple add into a list in memory) from dispatching it to an event handler.</span></span> <span data-ttu-id="f8df0-213">さらに、ディスパッチャーの種類を使用することによって、同期または非同期でイベントをディスパッチでしたします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-213">In addition, depending on what kind of dispatcher you are using, you could dispatch the events synchronously or asynchronously.</span></span>

<span data-ttu-id="f8df0-214">重要になっているトランザクションの境界をここで再生ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f8df0-214">Be aware that transactional boundaries come into significant play here.</span></span> <span data-ttu-id="f8df0-215">作業時間とトランザクションの場合は、単位は、複数の集計をまたがることができる場合 (として EF コアおよびリレーショナル データベースを使用する場合)、うまくいかないことができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-215">If your unit of work and transaction can span more than one aggregate (as when using EF Core and a relational database), this can work well.</span></span> <span data-ttu-id="f8df0-216">一貫性を実現するために追加の手順を実装するためにする場合は、トランザクションは、Azure DocumentDB のような NoSQL データベースを使用する場合などの集計をまたぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="f8df0-216">But if the transaction cannot span aggregates, such as when you are using a NoSQL database like Azure DocumentDB, you have to implement additional steps to achieve consistency.</span></span> <span data-ttu-id="f8df0-217">これは、永続性の無視がユニバーサル; 別の理由使用する記憶域システムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-217">This is another reason why persistence ignorance is not universal; it depends on the storage system you use.</span></span>

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a><span data-ttu-id="f8df0-218">集計の集計で最終的整合性との間で 1 つのトランザクション</span><span class="sxs-lookup"><span data-stu-id="f8df0-218">Single transaction across aggregates versus eventual consistency across aggregates</span></span>

<span data-ttu-id="f8df0-219">意見の分かれる最終的整合性の証明書利用者の間でのそれらの集計と集計の間で 1 つのトランザクションを実行するかどうかの質問はあります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-219">The question of whether to perform a single transaction across aggregates versus relying on eventual consistency across those aggregates is a controversial one.</span></span> <span data-ttu-id="f8df0-220">多くの DDD 作成者 Eric Evans と Vaughn カバー推奨規則を 1 つのトランザクションと同じように = 1 つの集計と集計の間で最終的整合性のためと主張します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-220">Many DDD authors like Eric Evans and Vaughn Vernon advocate the rule that one transaction = one aggregate and therefore argue for eventual consistency across aggregates.</span></span> <span data-ttu-id="f8df0-221">たとえば、著書で*ドメイン デザイン*は、Eric Evans:</span><span class="sxs-lookup"><span data-stu-id="f8df0-221">For example, in his book *Domain-Driven Design*, Eric Evans says this:</span></span>

<span data-ttu-id="f8df0-222">集計にわたるすべてのルールは、常に最新の状態にする必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f8df0-222">Any rule that spans Aggregates will not be expected to be up-to-date at all times.</span></span> <span data-ttu-id="f8df0-223">イベント処理、バッチ処理、またはその他の更新メカニズム、を介して他の依存関係できます内に解決する特定の時刻。</span><span class="sxs-lookup"><span data-stu-id="f8df0-223">Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time.</span></span> <span data-ttu-id="f8df0-224">(pg です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-224">(pg.</span></span> <span data-ttu-id="f8df0-225">128)</span><span class="sxs-lookup"><span data-stu-id="f8df0-225">128)</span></span>

<span data-ttu-id="f8df0-226">Vaughn カバーでは、次の質問[効果的な集計のデザインします。パート II: 行う集計作業まとめて](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span><span class="sxs-lookup"><span data-stu-id="f8df0-226">Vaughn Vernon says the following in [Effective Aggregate Design. Part II: Making Aggregates Work Together](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span></span>

<span data-ttu-id="f8df0-227">したがって、集計インスタンスは、1 つまたは複数の集計に関するその他のビジネス ルールを実行する必要がありますいずれかのコマンドを実行している場合を使用して最終的整合性\[しています.\]DDD モデルで最終的整合性をサポートするために実用的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-227">Thus, if executing a command on one aggregate instance requires that additional business rules execute on one or more aggregates, use eventual consistency \[...\] There is a practical way to support eventual consistency in a DDD model.</span></span> <span data-ttu-id="f8df0-228">集計メソッドは、1 つまたは複数の非同期サブスクライバーに配信された時間内にあるドメインのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-228">An aggregate method publishes a domain event that is in time delivered to one or more asynchronous subscribers.</span></span>

<span data-ttu-id="f8df0-229">この論理的根拠は、多くの集計またはエンティティにまたがるトランザクションではなく詳細なトランザクションの採用に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-229">This rationale is based on embracing fine-grained transactions instead of transactions spanning many aggregates or entities.</span></span> <span data-ttu-id="f8df0-230">考え方としては、2 番目のケースでは、データベース ロックの数がかなり大きくなる場合高い拡張性のニーズを持つ大規模なアプリケーションで。</span><span class="sxs-lookup"><span data-stu-id="f8df0-230">The idea is that in the second case, the number of database locks will be substantial in large-scale applications with high scalability needs.</span></span> <span data-ttu-id="f8df0-231">拡張性の高いアプリケーションでは、複数の集計の間のインスタントのトランザクションの一貫性があるない必要があるという事実を採用で最終的整合性の概念を受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-231">Embracing the fact that high-scalable applications need not have instant transactional consistency between multiple aggregates helps with accepting the concept of eventual consistency.</span></span> <span data-ttu-id="f8df0-232">アトミックの変更がビジネスで必要な多くの場合であり、どのような場合に特定の操作にアトミック トランザクションが必要があるかどうかどうかと、ドメインの専門家の責任です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-232">Atomic changes are often not needed by the business, and it is in any case the responsibility of the domain experts to say whether particular operations need atomic transactions or not.</span></span> <span data-ttu-id="f8df0-233">常に、操作は、複数の集計の間でアトミックのトランザクションを必要とする場合は、集計が大規模なを指定するか、正しく意図していないかどうかを依頼する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-233">If an operation always needs an atomic transaction between multiple aggregates, you might ask whether your aggregate should be larger or was not correctly designed.</span></span>

<span data-ttu-id="f8df0-234">ただし、他の開発者と Jimmy Bogard のように設計者は、単一のトランザクションにまたがる複数の集計の要件を満たして — のみとその他の集計に関連する同じ元のコマンドの副作用がします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-234">However, other developers and architects like Jimmy Bogard are okay with spanning a single transaction across several aggregates—but only when those additional aggregates are related to side effects for the same original command.</span></span> <span data-ttu-id="f8df0-235">たとえば、[向上ドメインのイベント パターン](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard では。</span><span class="sxs-lookup"><span data-stu-id="f8df0-235">For instance, in [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard says this:</span></span>

<span data-ttu-id="f8df0-236">通常、ドメイン、同じ論理トランザクション内では必ずしもドメイン イベントを発生させるの同じスコープ内で発生するイベントの副作用したい\[しています.\]トランザクションをコミットする前にこのハンドラーにイベントをそれぞれをディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-236">Typically, I want the side effects of a domain event to occur within the same logical transaction, but not necessarily in the same scope of raising the domain event \[...\] Just before we commit our transaction, we dispatch our events to their respective handlers.</span></span>

<span data-ttu-id="f8df0-237">右側のドメインのイベントをディスパッチする場合*する前に*元のトランザクションをコミットは、同じトランザクションに含まれるこれらのイベントの副作用をするためです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-237">If you dispatch the domain events right *before* committing the original transaction, it is because you want the side effects of those events to be included in the same transaction.</span></span> <span data-ttu-id="f8df0-238">たとえば、EF DbContext SaveChanges メソッドが失敗した場合、トランザクションがロールバック関連ドメインのイベント ハンドラーによって実装されているすべての副作用操作の結果を含む、すべての変更。</span><span class="sxs-lookup"><span data-stu-id="f8df0-238">For example, if the EF DbContext SaveChanges method fails, the transaction will roll back all changes, including the result of any side effect operations implemented by the related domain event handlers.</span></span> <span data-ttu-id="f8df0-239">これは、DbContext ライフ スコープは、既定でとして定義されているため「スコープ設定されます。」</span><span class="sxs-lookup"><span data-stu-id="f8df0-239">This is because the DbContext life scope is by default defined as "scoped."</span></span> <span data-ttu-id="f8df0-240">したがって、DbContext オブジェクトは、同じスコープまたはオブジェクト グラフ内でインスタンス化されている複数のリポジトリ オブジェクト間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-240">Therefore, the DbContext object is shared across multiple repository objects being instantiated within the same scope or object graph.</span></span> <span data-ttu-id="f8df0-241">これにより、Web API または MVC アプリケーションを開発するときに、HttpRequest スコープと一致します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-241">This coincides with the HttpRequest scope when developing Web API or MVC apps.</span></span>

<span data-ttu-id="f8df0-242">実際には、(1 つのアトミック トランザクションと最終的整合性) の両方の方法を適切に指定できます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-242">In reality, both approaches (single atomic transaction and eventual consistency) can be right.</span></span> <span data-ttu-id="f8df0-243">これは、ドメインまたはビジネス要件と、どのドメインの専門家がわかります本当に依存します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-243">It really depends on your domain or business requirements and what the domain experts tell you.</span></span> <span data-ttu-id="f8df0-244">スケーラブルなどのようにする必要があるにはサービスによっても異なります (より詳細なトランザクションは、データベースのロックに関して以下の影響を与える)。</span><span class="sxs-lookup"><span data-stu-id="f8df0-244">It also depends on how scalable you need the service to be (more granular transactions have less impact with regard to database locks).</span></span> <span data-ttu-id="f8df0-245">どの程度投資をしてもよい最終的整合性は、集計およびな補正アクションを実装する必要性の可能性のある不一致が検出するためにより複雑なコードを必要とするために、コードで行ったによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-245">And it depends on how much investment you are willing to make in your code, since eventual consistency requires more complex code in order to detect possible inconsistencies across aggregates and the need to implement compensatory actions.</span></span> <span data-ttu-id="f8df0-246">元の集計およびその後、イベントがディスパッチされるときに変更をコミットする場合がある問題を考慮し、イベント ハンドラーは、副作用をコミットできません、不一致を集計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-246">Take into account that if you commit changes to the original aggregate and afterwards, when the events are being dispatched, there is an issue and the event handlers cannot commit their side effects, you will have inconsistencies between aggregates.</span></span>

<span data-ttu-id="f8df0-247">な補正アクションを許可する方法は、元のトランザクションの一部ができるように、ドメインのイベントをその他のデータベース テーブルに保存することです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-247">A way to allow compensatory actions would be to store the domain events in additional database tables so they can be part of the original transaction.</span></span> <span data-ttu-id="f8df0-248">その後、バッチ処理の不整合を検出して、集計の現在の状態を持つイベントの一覧を比較することによってな補正アクションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-248">Afterwards, you could have a batch process that detects inconsistencies and runs compensatory actions by comparing the list of events with the current state of the aggregates.</span></span> <span data-ttu-id="f8df0-249">な補正アクションから、側では、ビジネス ユーザー、ドメインの専門家と説明が含まれています。 詳細な分析に必要な複雑なトピックの一部です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-249">The compensatory actions are part of a complex topic that will require deep analysis from your side, which includes discussing it with the business user and domain experts.</span></span>

<span data-ttu-id="f8df0-250">いずれの場合は、必要があるアプローチを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-250">In any case, you can choose the approach you need.</span></span> <span data-ttu-id="f8df0-251">初期遅延アプローチしますが、-1 つのトランザクションを使用するように、コミットする前に、イベントを発生させる — EF コアやリレーショナル データベースを使用する最も簡単な方法は、します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-251">But the initial deferred approach—raising the events before committing, so you use a single transaction—is the simplest approach when using EF Core and a relational database.</span></span> <span data-ttu-id="f8df0-252">簡単に実装して多くのビジネス ケースでは有効であります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-252">It is easier to implement and valid in many business cases.</span></span> <span data-ttu-id="f8df0-253">EShopOnContainers で順序付けマイクロ サービスで使用するアプローチです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-253">It is also the approach used in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="f8df0-254">しかし、方法は実際にディスパッチするそれぞれのそれぞれのイベント ハンドラーにこれらのイベントか。</span><span class="sxs-lookup"><span data-stu-id="f8df0-254">But how do you actually dispatch those events to their respective event handlers?</span></span> <span data-ttu-id="f8df0-255">新機能、\_前の例を参照してください媒介オブジェクトしますか?</span><span class="sxs-lookup"><span data-stu-id="f8df0-255">What is the \_mediator object that you see in the previous example?</span></span> <span data-ttu-id="f8df0-256">持つ手法および成果物のイベントとそのイベント ハンドラーの間でマップを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-256">That has to do with the techniques and artifacts you can use to map between events and their event handlers.</span></span>

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a><span data-ttu-id="f8df0-257">ドメインのイベント ディスパッチャー: イベントからイベント ハンドラーへのマッピング</span><span class="sxs-lookup"><span data-stu-id="f8df0-257">The domain event dispatcher: mapping from events to event handlers</span></span>

<span data-ttu-id="f8df0-258">ディスパッチまたはイベントを発行することが、ある種の成果物ごとの関連するハンドラーを取得でき、プロセスの副作用は、そのイベントに基づくように、イベントを発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-258">Once you are able to dispatch or publish the events, you need some kind of artifact that will publish the event so that every related handler can get it and process side effects based on that event.</span></span>

<span data-ttu-id="f8df0-259">1 つの方法は、実際のメッセージング システムであっても、イベント バス、メモリ内のイベントではなく、サービス バスに基づく可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-259">One approach is a real messaging system or even an event bus, possibly based on a service bus as opposed to in-memory events.</span></span> <span data-ttu-id="f8df0-260">ただし、最初のケースでは、実際のメッセージになりますだけ同一プロセス内のこれらのイベントを処理する必要があるために、ドメインのイベントを処理するための過剰 (つまり、同じドメインおよびアプリケーション レイヤー内)。</span><span class="sxs-lookup"><span data-stu-id="f8df0-260">However, for the first case, real messaging would be overkill for processing domain events, since you just need to process those events within the same process (that is, within the same domain and application layer).</span></span>

<span data-ttu-id="f8df0-261">複数のイベント ハンドラーにイベントをマップする別の方法は、イベントをディスパッチする場所を動的に推論できるように、IoC コンテナー内の型の登録を使用して、です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-261">Another way to map events to multiple event handlers is by using types registration in an IoC container so that you can dynamically infer where to dispatch the events.</span></span> <span data-ttu-id="f8df0-262">つまり、特定のイベントを取得する必要がイベント ハンドラーあるを把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8df0-262">In other words, you need to know what event handlers need to get a specific event.</span></span> <span data-ttu-id="f8df0-263">図 9 ~ 16 を簡略化した方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-263">Figure 9-16 shows a simplified approach for that.</span></span>

![](./media/image17.png)

<span data-ttu-id="f8df0-264">**図 9 ~ 16**です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-264">**Figure 9-16**.</span></span> <span data-ttu-id="f8df0-265">IoC を使用してドメイン イベント ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="f8df0-265">Domain event dispatcher using IoC</span></span>

<span data-ttu-id="f8df0-266">すべての組み込みおよびを自分でアプローチを実装する成果物をビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-266">You can build all the plumbing and artifacts to implement that approach by yourself.</span></span> <span data-ttu-id="f8df0-267">ただし、使用可能なライブラリと同様に使用も[MediatR](https://github.com/jbogard/MediatR)、IoT コンテナー背後を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-267">However, you can also use available libraries like [MediatR](https://github.com/jbogard/MediatR), which underneath the covers uses your IoT container.</span></span> <span data-ttu-id="f8df0-268">したがって直接使用できます、定義済みのインターフェイスと媒介オブジェクトのパブリッシュ/ディスパッチ メソッド。</span><span class="sxs-lookup"><span data-stu-id="f8df0-268">You can therefore directly use the predefined interfaces and the mediator object’s publish/dispatch methods.</span></span>

<span data-ttu-id="f8df0-269">コードでは、まず、IoC コンテナーで、種類のイベント ハンドラーを登録する次の例で示すように。</span><span class="sxs-lookup"><span data-stu-id="f8df0-269">In code, you first need to register the event handler types in your IoC container, as shown in the following example:</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement
        // IAsyncNotificationHandler<>) in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(
            typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
            .GetTypeInfo().Assembly)
            .Where(t => t.IsClosedTypeOf(typeof(IAsyncNotificationHandler<>)))
            .AsImplementedInterfaces();
        // Other registrations ...
    }
}
```

<span data-ttu-id="f8df0-270">コードは、まずアセンブリを指定します、ハンドラーのいずれかを保持するアセンブリを配置することにより、ドメインのイベント ハンドラーが含まれています (typeof(ValidateOrAddBuyerAggregateWhenXxxx)、ですが、使用することが選択したアセンブリを検索するその他のイベント ハンドラー)。</span><span class="sxs-lookup"><span data-stu-id="f8df0-270">The code first identifies the assembly that contains the domain event handlers by locating the assembly that holds any of the handlers (using typeof(ValidateOrAddBuyerAggregateWhenXxxx), but you could have chosen any other event handler to locate the assembly).</span></span> <span data-ttu-id="f8df0-271">すべてのイベント ハンドラーは、IAsyncNotificationHandler インターフェイスを実装しては、型次のものだけを検索し、すべてのイベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-271">Since all the event handlers implement the IAsyncNotificationHandler interface, the code then just searches for those types and registers all the event handlers.</span></span>

### <a name="how-to-subscribe-to-domain-events"></a><span data-ttu-id="f8df0-272">ドメインのイベントをサブスクライブする方法</span><span class="sxs-lookup"><span data-stu-id="f8df0-272">How to subscribe to domain events</span></span>

<span data-ttu-id="f8df0-273">MediatR を使用する場合、各イベント ハンドラーでは、次のコードでわかるように IAsyncNotificationHandler インターフェイスのジェネリック パラメーターで提供されているイベントの種類に使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-273">When you use MediatR, each event handler must use an event type that is provided on the generic parameter of the IAsyncNotificationHandler interface, as you can see in the following code:</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

<span data-ttu-id="f8df0-274">イベントと見なすことができます、サブスクリプション、イベント ハンドラー間のリレーションシップに基づく MediatR 成果物は各イベントのすべてのイベント ハンドラーを検出し、これらのイベント ハンドラーの各をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="f8df0-274">Based on the relationship between event and event handler, which can be considered the subscription, the MediatR artifact can discover all the event handlers for each event and trigger each of those event handlers.</span></span>

### <a name="how-to-handle-domain-events"></a><span data-ttu-id="f8df0-275">ドメインのイベントを処理する方法</span><span class="sxs-lookup"><span data-stu-id="f8df0-275">How to handle domain events</span></span>

<span data-ttu-id="f8df0-276">最後に、イベント ハンドラーでは、通常インフラストラクチャのリポジトリを使用して、必要なその他の集計を取得し、副作用としてドメイン ロジックを実行するアプリケーション層のコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-276">Finally, the event handler usually implements application layer code that uses infrastructure repositories to obtain the required additional aggregates and to execute side-effect domain logic.</span></span> <span data-ttu-id="f8df0-277">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8df0-277">The following code shows an example.</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
    : IAsyncNotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;
    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // Parameter validations
        //...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ?
            orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;
        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }
        buyer.VerifyOrAddPaymentMethod(cardTypeId,
            $"Payment Method on {DateTime.UtcNow}",
            orderStartedEvent.CardNumber,
            orderStartedEvent.CardSecurityNumber,
            orderStartedEvent.CardHolderName,
            orderStartedEvent.CardExpiration,
            orderStartedEvent.Order.Id);
        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) :
        _buyerRepository.Add(buyer);
        await _buyerRepository.UnitOfWork.SaveEntitiesAsync();
        // Logging code using buyerUpdated info, etc.
    }
}
```

<span data-ttu-id="f8df0-278">このイベント ハンドラーのコードがコードと見なされますアプリケーション レイヤー、インフラストラクチャのリポジトリを使用しているためインフラストラクチャ永続性レイヤーで、次のセクションで説明したようです。</span><span class="sxs-lookup"><span data-stu-id="f8df0-278">This event handler code is considered application layer code because it uses infrastructure repositories, as explained in the next section on the infrastructure-persistence layer.</span></span> <span data-ttu-id="f8df0-279">イベント ハンドラーは、他のインフラストラクチャ コンポーネントを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-279">Event handlers could also use other infrastructure components.</span></span>

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a><span data-ttu-id="f8df0-280">ドメインのイベントがマイクロ サービス境界の外部で発行する統合イベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="f8df0-280">Domain events can generate integration events to be published outside of the microservice boundaries</span></span>

<span data-ttu-id="f8df0-281">最後が複数 microservices のイベントに伝達するたい場合がありますは言うまでも重要です。</span><span class="sxs-lookup"><span data-stu-id="f8df0-281">Finally, is important to mention that you might sometimes want to propagate events across multiple microservices.</span></span> <span data-ttu-id="f8df0-282">統合イベントの発生と見なされます、特定のドメインのイベント ハンドラーから、イベント バスを介して発行できました。</span><span class="sxs-lookup"><span data-stu-id="f8df0-282">That is considered an integration event, and it could be published through an event bus from any specific domain event handler.</span></span>

## <a name="conclusions-on-domain-events"></a><span data-ttu-id="f8df0-283">ドメインのイベントのまとめ</span><span class="sxs-lookup"><span data-stu-id="f8df0-283">Conclusions on domain events</span></span> 

<span data-ttu-id="f8df0-284">説明したように、ドメイン内で変更の副作用を明示的に実装するのにドメインのイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-284">As stated, use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="f8df0-285">DDD 用語を使用するのには、1 つまたは複数の集計の間での副作用を明示的に実装するのにドメインのイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-285">To use DDD terminology, use domain events to explicitly implement side effects across one or multiple aggregates.</span></span> <span data-ttu-id="f8df0-286">さらに、およびスケーラビリティの向上とデータベースのロックの影響を軽減は、同じドメイン内の集計の間で最終的整合性を使用します。</span><span class="sxs-lookup"><span data-stu-id="f8df0-286">Additionally, and for better scalability and less impact on database locks, use eventual consistency between aggregates within the same domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f8df0-287">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f8df0-287">Additional resources</span></span>

-   <span data-ttu-id="f8df0-288">**Greg Young です。ドメインのイベントとは何ですか。** 
     [ *http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-288">**Greg Young. What is a Domain Event?**
[*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span></span>

-   <span data-ttu-id="f8df0-289">**年 1 月 Stenberg です。ドメインのイベントと最終的整合性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span><span class="sxs-lookup"><span data-stu-id="f8df0-289">**Jan Stenberg. Domain Events and Eventual Consistency**
[*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span></span>

-   <span data-ttu-id="f8df0-290">**Jimmy Bogard。優れたドメインのイベント パターン**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-290">**Jimmy Bogard. A better domain events pattern**
[*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span></span>

-   <span data-ttu-id="f8df0-291">**Vaughn Vernon。効果的な集計デザイン パート II: 行う作業を一緒に集計**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_記事/カバー\_2011\_2. pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span><span class="sxs-lookup"><span data-stu-id="f8df0-291">**Vaughn Vernon. Effective Aggregate Design Part II: Making Aggregates Work Together**
[*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span></span>

-   <span data-ttu-id="f8df0-292">**Jimmy Bogard。ドメインの強化: ドメイン イベント**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>*</span><span class="sxs-lookup"><span data-stu-id="f8df0-292">**Jimmy Bogard. Strengthening your domain: Domain Events**
*<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span></span>

-   <span data-ttu-id="f8df0-293">**Tony Truong です。ドメインのイベント パターン例**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-293">**Tony Truong. Domain Events Pattern Example**
[*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span></span>

-   <span data-ttu-id="f8df0-294">**Udi Dahan です。ドメイン モデルが完全に作成する方法にカプセル化された**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-294">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>

-   <span data-ttu-id="f8df0-295">**Udi Dahan です。イベントのドメインを 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span><span class="sxs-lookup"><span data-stu-id="f8df0-295">**Udi Dahan. Domain Events – Take 2**
[*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span></span>

-   <span data-ttu-id="f8df0-296">**Udi Dahan です。ドメインのイベントの救済**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-296">**Udi Dahan. Domain Events – Salvation**
[*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span></span>

-   <span data-ttu-id="f8df0-297">**年 1 月 Kronquist です。ドメインのイベントを公開表示しないで、それらが戻ります。** 
     [ *https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-297">**Jan Kronquist. Don't publish Domain Events, return them!**
[*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span></span>

-   <span data-ttu-id="f8df0-298">**Cesar de la Torre。ドメインのイベントとします。DDD および microservices アーキテクチャに統合イベント**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span><span class="sxs-lookup"><span data-stu-id="f8df0-298">**Cesar de la Torre. Domain Events vs. Integration Events in DDD and microservices architectures**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f8df0-299">[前](クライアント-側-validation.md) [次へ] (インフラストラクチャ-永続化のレイヤー-design.md)</span><span class="sxs-lookup"><span data-stu-id="f8df0-299">[Previous] (client-side-validation.md) [Next] (infrastructure-persistence-layer-design.md)</span></span>
