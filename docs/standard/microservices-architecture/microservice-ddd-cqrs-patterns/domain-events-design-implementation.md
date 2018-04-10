---
title: 'ドメイン イベント:  設計と実装'
description: コンテナー化された .NET アプリケーション向けの .NET マイクロサービス アーキテクチャ | ドメイン イベントの設計と実装
keywords: Docker, マイクロサービス, ASP.NET, コンテナー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: af6a6b73c790577cebf301075f2ff7e90960ea62
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="domain-events-design-and-implementation"></a><span data-ttu-id="92edb-105">ドメイン イベント: 設計と実装</span><span class="sxs-lookup"><span data-stu-id="92edb-105">Domain events: design and implementation</span></span>

<span data-ttu-id="92edb-106">ドメイン内での変更の副作用を明示的に実装するには、ドメイン イベントを使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-106">Use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="92edb-107">DDD の用語を使って言い換えるなら、複数の集計に副作用を明示的に実装するには、ドメイン イベントを使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-107">In other words, and using DDD terminology, use domain events to explicitly implement side effects across multiple aggregates.</span></span> <span data-ttu-id="92edb-108">また、スケーラビリティを向上させ、データベース ロックの影響を小さくする必要がある場合は、同じドメイン内の集計の間の最終的な整合性を使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-108">Optionally, for better scalability and less impact in database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="what-is-a-domain-event"></a><span data-ttu-id="92edb-109">ドメイン イベントとは</span><span class="sxs-lookup"><span data-stu-id="92edb-109">What is a domain event?</span></span>

<span data-ttu-id="92edb-110">イベントとは、過去に発生した出来事です。</span><span class="sxs-lookup"><span data-stu-id="92edb-110">An event is something that has happened in the past.</span></span> <span data-ttu-id="92edb-111">ドメイン イベントは、論理的には、特定のドメインにおいて発生した出来事であり、同じドメイン (インプロセス) の他の部分がそれを認識し、必要に応じて対応する必要のあることです。</span><span class="sxs-lookup"><span data-stu-id="92edb-111">A domain event is, logically, something that happened in a particular domain, and something you want other parts of the same domain (in-process) to be aware of and potentially react to.</span></span>

<span data-ttu-id="92edb-112">ドメイン イベントの重要な利点は、ドメイン内で何かが発生した後の副作用を、暗黙的にではなく明示的に表現できることです。</span><span class="sxs-lookup"><span data-stu-id="92edb-112">An important benefit of domain events is that side effects after something happened in a domain can be expressed explicitly instead of implicitly.</span></span> <span data-ttu-id="92edb-113">ビジネス タスクに関連するすべての操作が行われるか、またはまったく行われないように、これらの副作用は一貫している必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-113">Those side effects must be consistent so either all the operations related to the business task happen, or none of them.</span></span> <span data-ttu-id="92edb-114">さらに、ドメイン イベントを使うことにより、同じドメイン内のクラス間で問題をよりはっきりと分離することができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-114">In addition, domain events enable a better separation of concerns among classes within the same domain.</span></span>

<span data-ttu-id="92edb-115">たとえば、Entity Framework とエンティティまたは集計だけを使っているとすると、ユース ケースによってある副作用を発生させる必要がある場合、そのような副作用は、何かが発生した後の結合されたコードでの暗黙的な概念として実装されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-115">For example, if you're just using Entity Framework and entities or even aggregates, if there have to be side effects provoked by a use case, those will be implemented as an implicit concept in the coupled code after something happened.</span></span> <span data-ttu-id="92edb-116">しかし、そのコードを見ただけでは、そのコード (副作用) がメインの操作の一部なのか、それとも副作用なのかが、わからない場合があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-116">But, if you just see that code, you might not know if that code (the side effect) is part of the main operation or if it really is a side effect.</span></span> <span data-ttu-id="92edb-117">一方、ドメイン イベントを使うと、概念が明確になり、ユビキタス言語の一部になります。</span><span class="sxs-lookup"><span data-stu-id="92edb-117">On the other hand, using domain events makes the concept explicit and part of the ubiquitous language.</span></span> <span data-ttu-id="92edb-118">たとえば、eShopOnContainers アプリケーションでは、注文の作成は注文だけに関係しているわけではありません。注文が行われるまでユーザーは購入者ではないので、注文の作成により、元のユーザーに基づいて購入者の集計が更新または作成されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-118">For example, in the eShopOnContainers application, creating an order is not just about the order; it updates or creates a buyer aggregate based on the original user, because the user is not a buyer until there is an order in place.</span></span> <span data-ttu-id="92edb-119">ドメイン イベントを使う場合、ドメインの専門家によって提供されるユビキタス言語に基づいて、ドメイン ルールを明示的に表現できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-119">If you use domain events, you can explicitly express that domain rule based in the ubiquitous language provided by the domain experts.</span></span>

<span data-ttu-id="92edb-120">ドメイン イベントはメッセージング スタイルのイベントに似ていますが、重要な相違点が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="92edb-120">Domain events are somewhat similar to messaging-style events, with one important difference.</span></span> <span data-ttu-id="92edb-121">実際のメッセージング、メッセージ キュー、メッセージ ブローカー、または AMPQ を使うサービス バスでは、メッセージは常に非同期に送信され、プロセスとマシンの間で通信されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-121">With real messaging, message queuing, message brokers, or a service bus using AMPQ, a message is always sent asynchronously and communicated across processes and machines.</span></span> <span data-ttu-id="92edb-122">これは、複数の境界コンテキスト、マイクロサービス、または異なるアプリケーションを統合する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="92edb-122">This is useful for integrating multiple Bounded Contexts, microservices, or even different applications.</span></span> <span data-ttu-id="92edb-123">一方、ドメイン イベントでは、現在実行しているドメイン操作からイベントが生成されて、同じドメイン内で副作用が発生することが望まれます。</span><span class="sxs-lookup"><span data-stu-id="92edb-123">However, with domain events, you want to raise an event from the domain operation you are currently running, but you want any side effects to occur within the same domain.</span></span>

<span data-ttu-id="92edb-124">ドメイン イベントとその副作用 (その後にトリガーされる、イベント ハンドラーによって管理されるアクション) は、ほぼ瞬時に (通常はインプロセス) 同じドメイン内で発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-124">The domain events and their side effects (the actions triggered afterwards that are managed by event handlers) should occur almost immediately, usually in-process, and within the same domain.</span></span> <span data-ttu-id="92edb-125">したがって、ドメイン イベントは同期でも非同期でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="92edb-125">Thus, domain events could be synchronous or asynchronous.</span></span> <span data-ttu-id="92edb-126">ただし、統合イベントは常に非同期でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="92edb-126">Integration events, however, should always be asynchronous.</span></span>

## <a name="domain-events-versus-integration-events"></a><span data-ttu-id="92edb-127">統合イベントとドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="92edb-127">Domain events versus integration events</span></span>

<span data-ttu-id="92edb-128">意味としては、ドメイン イベントと統合イベントは同じものであり、発生したばかりのことに関する通知です。</span><span class="sxs-lookup"><span data-stu-id="92edb-128">Semantically, domain and integration events are the same thing: notifications about something that just happened.</span></span> <span data-ttu-id="92edb-129">しかし、それらの実装は異なっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-129">However, their implementation must be different.</span></span> <span data-ttu-id="92edb-130">ドメイン イベントはドメイン イベント ディスパッチャーにプッシュされるメッセージでしかなく、IoC コンテナーまたは他の何らかの方法に基づくインメモリ メディエーターとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-130">Domain events are just messages pushed to a domain event dispatcher, which could be implemented as an in-memory mediator based on an IoC container or any other method.</span></span>

<span data-ttu-id="92edb-131">一方、統合イベントの目的は、コミットされたトランザクションや更新を他のサブシステムに伝達することです。サブシステムは、他のマイクロサービス、境界コンテキスト、さらには外部アプリケーションのいずれでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="92edb-131">On the other hand, the purpose of integration events is to propagate committed transactions and updates to additional subsystems, whether they are other microservices, Bounded Contexts or even external applications.</span></span> <span data-ttu-id="92edb-132">したがって、多くのシナリオではこれが失敗した場合は操作全体が実質的に発生しなかったことになるので、統合イベントはエンティティが正常に保存された場合にのみ発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-132">Hence, they should occur only if the entity is successfully persisted, since in many scenarios if this fails, the entire operation effectively never happened.</span></span>

<span data-ttu-id="92edb-133">さらに、説明したように、統合イベントは、複数のマイクロサービス (他の境界コンテキスト) 間または外部システム/アプリケーション間の非同期通信に基づいている必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-133">In addition, and as mentioned, integration events must be based on asynchronous communication between multiple microservices (other Bounded Contexts) or even external systems/applications.</span></span> <span data-ttu-id="92edb-134">したがって、イベント バス インターフェイスには、場合によってはリモート サービス間でのプロセス間分散通信を可能にする何らかのインフラストラクチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="92edb-134">Thus, the event bus interface needs some infrastructure that allows inter-process and distributed communication between potentially remote services.</span></span> <span data-ttu-id="92edb-135">商用のサービス バス、キュー、メールボックスとして使われる共有データベース、またはその他の分散で、できればプッシュ ベースのメッセージング システムのいずれが基になっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="92edb-135">It can be based on a commercial service bus, queues, a shared database used as a mailbox, or any other distributed and ideally push based messaging system.</span></span>

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a><span data-ttu-id="92edb-136">同じドメイン内の複数の集計間で副作用をトリガーする望ましい方法としてのドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="92edb-136">Domain events as a preferred way to trigger side effects across multiple aggregates within the same domain</span></span>

<span data-ttu-id="92edb-137">ある集計インスタンスに関係のあるコマンドを実行するために、1 つ以上の他の集計で他のドメイン ルールを実行する必要がある場合は、このような副作用がドメイン イベントによってトリガーされるように設計および実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-137">If executing a command related to one aggregate instance requires additional domain rules to be run on one or more additional aggregates, you should design and implement those side effects to be triggered by domain events.</span></span> <span data-ttu-id="92edb-138">図 9-14 で示すように、最も重要なユース ケースの 1 つとして、ドメイン イベントを使って、同じドメイン モデル内の複数の集計の間で状態の変化を伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-138">As shown in Figure 9-14, and as one of the most important use cases, a domain event should be used to propagate state changes across multiple aggregates within the same domain model.</span></span>

![](./media/image15.png)

<span data-ttu-id="92edb-139">**図 9-14**: </span><span class="sxs-lookup"><span data-stu-id="92edb-139">**Figure 9-14**.</span></span> <span data-ttu-id="92edb-140">同じドメイン内の複数の集計の間に整合性を適用するためのドメイン イベント</span><span class="sxs-lookup"><span data-stu-id="92edb-140">Domain events to enforce consistency between multiple aggregates within the same domain</span></span>

<span data-ttu-id="92edb-141">図では、ユーザーが注文を開始すると、OrderStarted ドメイン イベントによって、ID マイクロサービスからの元のユーザー情報 (および、CreateOrder コマンドで提供された情報) を基にした、注文マイクロサービスでの Buyer オブジェクトの作成がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="92edb-141">In the figure, when the user initiates an order, the OrderStarted domain event triggers creation of a Buyer object in the ordering microservice, based on the original user info from the identity microservice (with information provided in the CreateOrder command).</span></span> <span data-ttu-id="92edb-142">ドメイン イベントは、注文集計が最初の場所で作成されたときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-142">The domain event is generated by the order aggregate when it is created in the first place.</span></span>

<span data-ttu-id="92edb-143">または、集計ルートを作成し、その集計 (子エンティティ) のメンバーによって生成されるイベントをサブスクライブすることもできます。</span><span class="sxs-lookup"><span data-stu-id="92edb-143">Alternately, you can have the aggregate root subscribed for events raised by members of its aggregates (child entities).</span></span> <span data-ttu-id="92edb-144">たとえば、OrderItem の各子エンティティは、品目の価格が指定された金額より高いとき、または製品品目の量が高すぎるとに、イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-144">For instance, each OrderItem child entity can raise an event when the item price is higher than a specific amount, or when the product item amount is too high.</span></span> <span data-ttu-id="92edb-145">集計ルートは、これらのイベントを受け取って、グローバルな計算または集計を実行できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-145">The aggregate root can then receive those events and perform a global calculation or aggregation.</span></span>

<span data-ttu-id="92edb-146">このイベント ベースの通信は集計内に直接実装されないことを理解しておくことが重要です。ドメイン イベント ハンドラーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-146">It is important to understand that this event-based communication is not implemented directly within the aggregates; you need to implement domain event handlers.</span></span> <span data-ttu-id="92edb-147">ドメイン イベントの処理は、アプリケーションの問題です。</span><span class="sxs-lookup"><span data-stu-id="92edb-147">Handling the domain events is an application concern.</span></span> <span data-ttu-id="92edb-148">ドメイン モデル レイヤーでは、ハンドラーやリポジトリを使った副作用の永続化アクションといったアプリケーション インフラストラクチャに関することではなく、ドメインの専門家が理解しているドメインのロジックだけに注目する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-148">The domain model layer should only focus on the domain logic—things that a domain expert would understand, not application infrastructure like handlers and side-effect persistence actions using repositories.</span></span> <span data-ttu-id="92edb-149">したがって、ドメイン イベントが発生したときのドメイン イベント ハンドラー トリガー アクションは、アプリケーション レイヤー レベルで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-149">Therefore, the application layer level is where you should have domain event handlers triggering actions when a domain event is raised.</span></span>

<span data-ttu-id="92edb-150">また、ドメイン イベントを使って、任意の数のアプリケーション アクションをトリガーすることができます。さらに重要なことは、後でその数を他に影響を与えない方法で増やすことができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-150">Domain events can also be used to trigger any number of application actions, and what is more important, must be open to increase that number in the future in a decoupled way.</span></span> <span data-ttu-id="92edb-151">たとえば、注文が開始されたら、ドメイン イベントを発行してその情報を他の集計に伝達したり、通知などのアプリケーション アクションを発生させたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-151">For instance, when the order is started, you might want to publish a domain event to propagate that info to other aggregates or even to raise application actions like notifications.</span></span>

<span data-ttu-id="92edb-152">重要な点は、ドメイン イベントが発生したときに実行されるアクションの数が開放されていることです。</span><span class="sxs-lookup"><span data-stu-id="92edb-152">The key point is the open number of actions to be executed when a domain event occurs.</span></span> <span data-ttu-id="92edb-153">いずれ、ドメインおよびアプリケーション内のアクションとルールは増えていきます。</span><span class="sxs-lookup"><span data-stu-id="92edb-153">Eventually, the actions and rules in the domain and application will grow.</span></span> <span data-ttu-id="92edb-154">何かが発生したときの副作用の複雑さや数は上昇しますが、コードが "接着剤" で結合されていると (つまり、C\# で new キーワードを使ってオブジェクトをインスタンス化するだけ)、新しいアクションを追加する必要があるたびに、元のコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-154">The complexity or number of side-effect actions when something happens will grow, but if your code were coupled with “glue” (that is, just instantiating objects with the new keyword in C\#), then every time you needed to add a new action you would need to change the original code.</span></span> <span data-ttu-id="92edb-155">これでは、新しい要件が出てくるたびに元のコード フローを変更する必要があるので、新しいバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-155">This could result in new bugs, because with each new requirement you would need to change the original code flow.</span></span> <span data-ttu-id="92edb-156">これは、[SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) の[開放/閉鎖原則](https://en.wikipedia.org/wiki/Open/closed_principle)に反しています。</span><span class="sxs-lookup"><span data-stu-id="92edb-156">This goes against the [Open/Closed principle](https://en.wikipedia.org/wiki/Open/closed_principle) from [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)).</span></span> <span data-ttu-id="92edb-157">それだけでなく、操作を調整していた元のクラスが拡大を重ね、[単一責任原則 (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle) に反するようになります。</span><span class="sxs-lookup"><span data-stu-id="92edb-157">Not only that, the original class that was orchestrating the operations would grow and grow, which goes against the [Single Responsibility Principle (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).</span></span>

<span data-ttu-id="92edb-158">これに対し、ドメイン イベントでは、以下のアプローチを使って責任を隔離することにより、粒度が細かく分離された実装を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-158">On the other hand, if you use domain events, you can create a fine-grained and decoupled implementation by segregating responsibilities using this approach:</span></span>

1.  <span data-ttu-id="92edb-159">コマンドを送信します (例: CreateOrder)。</span><span class="sxs-lookup"><span data-stu-id="92edb-159">Send a command (for example, CreateOrder).</span></span>
2.  <span data-ttu-id="92edb-160">コマンド ハンドラーでコマンドを受信します。</span><span class="sxs-lookup"><span data-stu-id="92edb-160">Receive the command in a command handler.</span></span>
    -   <span data-ttu-id="92edb-161">1 つの集計のトランザクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="92edb-161">Execute a single aggregate’s transaction.</span></span>
    -   <span data-ttu-id="92edb-162">(省略可能) 副作用のドメイン イベントを発生させます (例: OrderStartedDomainEvent)。</span><span class="sxs-lookup"><span data-stu-id="92edb-162">(Optional) Raise domain events for side effects (for example, OrderStartedDomainEvent).</span></span>
1.  <span data-ttu-id="92edb-163">複数の集計またはアプリケーション アクションにおいて開放された数の副作用を実行する (現在のプロセス内の) ドメイン ベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="92edb-163">Handle domain events (within the current process) that will execute an open number of side effects in multiple aggregates or application actions.</span></span> <span data-ttu-id="92edb-164">例:</span><span class="sxs-lookup"><span data-stu-id="92edb-164">For example:</span></span>
    -   <span data-ttu-id="92edb-165">購入者および支払方法を確認または作成します。</span><span class="sxs-lookup"><span data-stu-id="92edb-165">Verify or create buyer and payment method.</span></span>
    -   <span data-ttu-id="92edb-166">関連する統合イベントを作成してイベント バスに送信し、複数のマイクロサービスに状態を伝達するか、購入者へのメール送信のような外部アクションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="92edb-166">Create and send a related integration event to the event bus to propagate states across microservices or trigger external actions like sending an email to the buyer.</span></span>
    -   <span data-ttu-id="92edb-167">他の副作用を処理します。</span><span class="sxs-lookup"><span data-stu-id="92edb-167">Handle other side effects.</span></span>

<span data-ttu-id="92edb-168">図 9-15 で示すように、同じドメイン イベントから開始して、統合イベントおよびイベント バスによって接続されている複数のマイクロサービスを実行するために必要な、ドメイン内の他の集計に関連する複数のアクションまたは他のアプリケーション アクションを処理できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-168">As shown in Figure 9-15, starting from the same domain event, you can handle multiple actions related to other aggregates in the domain or additional application actions you need to perform across microservices connecting with integration events and the event bus.</span></span>

![](./media/image16.png)

<span data-ttu-id="92edb-169">**図 9-15**: </span><span class="sxs-lookup"><span data-stu-id="92edb-169">**Figure 9-15**.</span></span> <span data-ttu-id="92edb-170">ドメインごとに複数のアクションの処理</span><span class="sxs-lookup"><span data-stu-id="92edb-170">Handling multiple actions per domain</span></span>

<span data-ttu-id="92edb-171">マイクロサービスの動作にはリポジトリやアプリケーション API などのインフラストラクチャ オブジェクトを使うため、通常、イベント ハンドラーはアプリケーション レイヤーにあります。</span><span class="sxs-lookup"><span data-stu-id="92edb-171">The event handlers are typically in the application layer, because you will use infrastructure objects like repositories or an application API for the microservice’s behavior.</span></span> <span data-ttu-id="92edb-172">どちらもアプリケーション レイヤーの一部であるという意味で、イベント ハンドラーはコマンド ハンドラーに似ています。</span><span class="sxs-lookup"><span data-stu-id="92edb-172">In that sense, event handlers are similar to command handlers, so both are part of the application layer.</span></span> <span data-ttu-id="92edb-173">重要な相違点は、コマンドは 1 回だけ処理する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="92edb-173">The important difference is that a command should be processed just once.</span></span> <span data-ttu-id="92edb-174">ドメイン イベントは、それぞれが異なる用途を持つ複数のレシーバーまたはイベント ハンドラーで受信できるため、ドメイン イベントはゼロ回または *n* 回処理される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-174">A domain event could be processed zero or *n* times, because if can be received by multiple receivers or event handlers with a different purpose for each handler.</span></span>

<span data-ttu-id="92edb-175">ドメイン イベントあたりのハンドラーの数を開放できるため、現在のコードに影響を与えずにさらに多くのドメイン ルールを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-175">The possibility of an open number of handlers per domain event allows you to add many more domain rules without impacting your current code.</span></span> <span data-ttu-id="92edb-176">たとえば、イベントの直後に発生する必要のある次のビジネス ルールは、いくつかのイベント ハンドラー (またはたった 1 つ) を追加するだけで簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-176">For instance, implementing the following business rule that has to happen right after an event might be as easy as adding a few event handlers (or even just one):</span></span>

<span data-ttu-id="92edb-177">顧客がストアで行った任意の数の注文の合計購入金額が $6,000 を超える場合、すべての新規注文に 10% の割引を適用し、将来の注文に対するその割引のことをメールで顧客に通知します。</span><span class="sxs-lookup"><span data-stu-id="92edb-177">When the total amount purchased by a customer in the store, across any number of orders, exceeds $6,000, apply a 10% off discount to every new order and notify the customer with an email about that discount for future orders.</span></span>

## <a name="implementing-domain-events"></a><span data-ttu-id="92edb-178">ドメイン イベントの実装</span><span class="sxs-lookup"><span data-stu-id="92edb-178">Implementing domain events</span></span>

<span data-ttu-id="92edb-179">C# のドメイン イベントは、ドメインで発生したことに関連するすべての情報を含む、DTO のようなデータ保持構造体またはクラスです。次にその例を示します。</span><span class="sxs-lookup"><span data-stu-id="92edb-179">In C#, a domain event is simply a data-holding structure or class, like a DTO, with all the information related to what just happened in the domain, as shown in the following example:</span></span>

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

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

<span data-ttu-id="92edb-180">これは、本質的に OrderStarted イベントに関連するすべてのデータを保持するクラスです。</span><span class="sxs-lookup"><span data-stu-id="92edb-180">This is essentially a class that holds all the data related to the OrderStarted event.</span></span>

<span data-ttu-id="92edb-181">ユビキタス言語の観点からは、イベントは過去に発生した事柄なので、イベントのクラス名は OrderStartedDomainEvent や OrderShippedDomainEvent のような過去形動詞として表される必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-181">In terms of the ubiquitous language of the domain, since an event is something that happened in the past, the class name of the event should be represented as a past-tense verb, like OrderStartedDomainEvent or OrderShippedDomainEvent.</span></span> <span data-ttu-id="92edb-182">これは、eShopOnContainers の注文マイクロサービスでのドメイン イベントの実装方法です。</span><span class="sxs-lookup"><span data-stu-id="92edb-182">That is how the domain event is implemented in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="92edb-183">前に説明したように、イベントの重要な特性は、イベントは過去に発生したことなので変更できない、ということです。</span><span class="sxs-lookup"><span data-stu-id="92edb-183">As noted earlier, an important characteristic of events is that since an event is something that happened in the past, it should not change.</span></span> <span data-ttu-id="92edb-184">したがって、不変クラスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-184">Therefore it must be an immutable class.</span></span> <span data-ttu-id="92edb-185">上のコードでは、プロパティがオブジェクトの外部からは読み取り専用であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="92edb-185">You can see in the previous code that the properties are read-only from outside of the object.</span></span> <span data-ttu-id="92edb-186">オブジェクトを更新する唯一の方法は、イベント オブジェクトを作成するときにコンストラクターを使うことです。</span><span class="sxs-lookup"><span data-stu-id="92edb-186">The only way to update the object is through the constructor when you create the event object.</span></span>

### <a name="raising-domain-events"></a><span data-ttu-id="92edb-187">ドメイン イベントの生成</span><span class="sxs-lookup"><span data-stu-id="92edb-187">Raising domain events</span></span>

<span data-ttu-id="92edb-188">次に知りたいことは、関連するイベント ハンドラーに届くようにドメイン イベントを生成する方法です。</span><span class="sxs-lookup"><span data-stu-id="92edb-188">The next question is how to raise a domain event so it reaches its related event handlers.</span></span> <span data-ttu-id="92edb-189">複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-189">You can use multiple approaches.</span></span>

<span data-ttu-id="92edb-190">Udi Dahan がもともと提案しているのは (たとえば、「[Domain Events – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)」(ドメイン イベント – テイク 2 などの複数の関連する投稿を参照))、イベントの管理と生成に静的クラスを使う方法です。</span><span class="sxs-lookup"><span data-stu-id="92edb-190">Udi Dahan originally proposed (for example, in several related posts, such as [Domain Events – Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) using a static class for managing and raising the events.</span></span> <span data-ttu-id="92edb-191">これには、呼び出されるとすぐにドメイン イベントを生成する DomainEvents という名前の静的クラスが含まれる場合があります (DomainEvents.Raise(Event myEvent) のような構文を使用)。</span><span class="sxs-lookup"><span data-stu-id="92edb-191">This might include a static class named DomainEvents that would raise domain events immediately when it is called, using syntax like DomainEvents.Raise(Event myEvent).</span></span> <span data-ttu-id="92edb-192">Jimmy Bogard も、ブログ投稿「[Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)」(ドメインの強化: ドメイン イベント) で同様のアプローチを推奨しています。</span><span class="sxs-lookup"><span data-stu-id="92edb-192">Jimmy Bogard wrote a blog post ([Strengthening your domain: Domain Events](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)) that recommends a similar approach.</span></span>

<span data-ttu-id="92edb-193">ただし、ドメイン イベント クラスが静的である場合は、ハンドラーにもすぐにディスパッチにします。</span><span class="sxs-lookup"><span data-stu-id="92edb-193">However, when the domain events class is static, it also dispatches to handlers immediately.</span></span> <span data-ttu-id="92edb-194">これにより、副作用のロジックを含むイベント ハンドラーがイベント生成直後に実行されるため、テストとデバッグが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="92edb-194">This makes testing and debugging more difficult, because the event handlers with side-effects logic are executed immediately after the event is raised.</span></span> <span data-ttu-id="92edb-195">テストとデバッグを行うときは、現在の集計クラスで発生していることだけに注目する必要があります。他の集計やアプリケーション ロジックに関連する副作用に対する他のイベント ハンドラーに突然リダイレクトされるのは困ります。</span><span class="sxs-lookup"><span data-stu-id="92edb-195">When you are testing and debugging, you want to focus on and just what is happening in the current aggregate classes; you do not want to suddenly be redirected to other event handlers for side effects related to other aggregates or application logic.</span></span> <span data-ttu-id="92edb-196">このような理由から、次のセクションで説明する他のアプローチが考案されています。</span><span class="sxs-lookup"><span data-stu-id="92edb-196">This is why other approaches have evolved, as explained in the next section.</span></span>

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a><span data-ttu-id="92edb-197">イベントの生成とディスパッチに対する遅延アプローチ</span><span class="sxs-lookup"><span data-stu-id="92edb-197">The deferred approach for raising and dispatching events</span></span>

<span data-ttu-id="92edb-198">ドメイン イベント ハンドラーにすぐにディスパッチするよりよい方法は、ドメイン イベントをコレクションに追加した後、トランザクションを (EF の SaveChanges で) コミットする "*直前*" または "*直**後*" に、それらのドメイン イベントをディスパッチすることです</span><span class="sxs-lookup"><span data-stu-id="92edb-198">Instead of dispatching to a domain event handler immediately, a better approach is to add the domain events to a collection and then to dispatch those domain events *right before* or *right* *after* committing the transaction (as with SaveChanges in EF).</span></span> <span data-ttu-id="92edb-199">(このアプローチについては、Jimmy Bogard の「[A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)」(よりよいドメイン イベント パターン) を参照)。</span><span class="sxs-lookup"><span data-stu-id="92edb-199">(This approach was described by Jimmy Bogard in this post [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)</span></span>

<span data-ttu-id="92edb-200">ドメイン イベントの送信をトランザクションのコミットの直前または直後のどちらにするかは、副作用を同じトランザクションまたは別のトランザクションのどちらに含めればよいかに影響するので、重要な決定です。</span><span class="sxs-lookup"><span data-stu-id="92edb-200">Deciding if you send the domain events right before or right after committing the transaction is important, since it determines whether you will include the side effects as part of the same transaction or in different transactions.</span></span> <span data-ttu-id="92edb-201">後者の場合は、複数の集計の間の最終的な整合性に対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-201">In the latter case, you need to deal with eventual consistency across multiple aggregates.</span></span> <span data-ttu-id="92edb-202">これについては、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="92edb-202">This topic is discussed in the next section.</span></span>

<span data-ttu-id="92edb-203">eShopOnContainers では遅延アプローチを使っています。</span><span class="sxs-lookup"><span data-stu-id="92edb-203">The deferred approach is what eShopOnContainers uses.</span></span> <span data-ttu-id="92edb-204">最初に、エンティティで発生したイベントを、エンティティごとのコレクションまたはイベント リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="92edb-204">First, you add the events happening in your entities into a collection or list of events per entity.</span></span> <span data-ttu-id="92edb-205">このリストは、エンティティ オブジェクトの一部にする必要があり、さらによい方法は、次の Entity 基底クラスの例で示すように、基本エンティティ クラスの一部にすることです。</span><span class="sxs-lookup"><span data-stu-id="92edb-205">That list should be part of the entity object, or even better, part of your base entity class, as shown in the following example of the Entity base class:</span></span>

```csharp
public abstract class Entity
{
     //... 
    private List<INotification> _domainEvents;
    public List<INotification> DomainEvents => _domainEvents;

    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }

    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

<span data-ttu-id="92edb-206">イベントを生成するときは、集計ルート エンティティの任意のメソッドのコードから、イベント コレクションにイベントを追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="92edb-206">When you want to raise an event, you just add it to the event collection from code at any method of the aggregate-root entity.</span></span>

<span data-ttu-id="92edb-207">次に示すコードの例は、[eShopOnContainers の Order 集計ルート](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs)の一部です。</span><span class="sxs-lookup"><span data-stu-id="92edb-207">The following code, part of the [Order agregate-root at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), shows an example:</span></span>

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

<span data-ttu-id="92edb-208">AddDomainEvent メソッドで行われているのが、リストへのイベントの追加だけであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92edb-208">Notice that the only thing that the AddDomainEvent method is doing is adding an event to the list.</span></span> <span data-ttu-id="92edb-209">イベントはまだディスパッチされておらず、イベント ハンドラーはまだ呼び出されていません。</span><span class="sxs-lookup"><span data-stu-id="92edb-209">No event is dispatched yet, and no event handler is invoked yet.</span></span>

<span data-ttu-id="92edb-210">実際にイベントをディスパッチするのは、後でデータベースにトランザクションをコミットするときです。</span><span class="sxs-lookup"><span data-stu-id="92edb-210">You actually want to dispatch the events later on, when you commit the transaction to the database.</span></span> <span data-ttu-id="92edb-211">Entity Framework Core を使っている場合は、次のコードのように、EF DbContext の SaveChanges メソッド内であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="92edb-211">If you are using Entity Framework Core, that means in the SaveChanges method of your EF DbContext, as in the following code:</span></span>

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
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

<span data-ttu-id="92edb-212">このコードでは、エンティティ イベントを対応するイベント ハンドラーにディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="92edb-212">With this code, you dispatch the entity events to their respective event handlers.</span></span>

<span data-ttu-id="92edb-213">全体な結果として、ドメイン イベントの生成 (単にメモリ内のリストへの追加) がイベント ハンドラーへのディスパッチから切り離されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-213">The overall result is that you have decoupled the raising of a domain event (a simple add into a list in memory) from dispatching it to an event handler.</span></span> <span data-ttu-id="92edb-214">さらに、使っているディスパッチャーの種類によっては、同期または非同期にイベントをディスパッチできます。</span><span class="sxs-lookup"><span data-stu-id="92edb-214">In addition, depending on what kind of dispatcher you are using, you could dispatch the events synchronously or asynchronously.</span></span>

<span data-ttu-id="92edb-215">ここでは、トランザクション境界が重要な意味を持つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="92edb-215">Be aware that transactional boundaries come into significant play here.</span></span> <span data-ttu-id="92edb-216">作業単位とトランザクションが複数の集計にまたがることができる場合 (EF Core とリレーショナル データベースを使っている場合など)、これはうまくいきます。</span><span class="sxs-lookup"><span data-stu-id="92edb-216">If your unit of work and transaction can span more than one aggregate (as when using EF Core and a relational database), this can work well.</span></span> <span data-ttu-id="92edb-217">しかし、トランザクションが複数の集計にまたがることができない場合は (Azure DocumentDB のような NoSQL を使っている場合)、整合性を実現するための追加手順を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-217">But if the transaction cannot span aggregates, such as when you are using a NoSQL database like Azure DocumentDB, you have to implement additional steps to achieve consistency.</span></span> <span data-ttu-id="92edb-218">これは、永続性の無視がユニバーサルではないもう 1 つの理由であり、使っているストレージ システムに依存します。</span><span class="sxs-lookup"><span data-stu-id="92edb-218">This is another reason why persistence ignorance is not universal; it depends on the storage system you use.</span></span>

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a><span data-ttu-id="92edb-219">複数の集計にまたがる 1 つのトランザクションと集計の間の最終的な整合性</span><span class="sxs-lookup"><span data-stu-id="92edb-219">Single transaction across aggregates versus eventual consistency across aggregates</span></span>

<span data-ttu-id="92edb-220">複数の集計にまたがる 1 つのトランザクションを実行する方がよいか、それともそれらの集計の間の最終的な整合性に依存する方がよいかは、難しい問題です。</span><span class="sxs-lookup"><span data-stu-id="92edb-220">The question of whether to perform a single transaction across aggregates versus relying on eventual consistency across those aggregates is a controversial one.</span></span> <span data-ttu-id="92edb-221">Eric Evans や Vaughn Vernon などの多くの DDD 作成者は、1 トランザクション = 1 集計のルールを推奨しており、したがって集計間の最終的な整合性を主張しています。</span><span class="sxs-lookup"><span data-stu-id="92edb-221">Many DDD authors like Eric Evans and Vaughn Vernon advocate the rule that one transaction = one aggregate and therefore argue for eventual consistency across aggregates.</span></span> <span data-ttu-id="92edb-222">たとえば、Eric Evans は『*Domain-Driven Design*』(ドメイン ドリブンの設計) で次のように書いています。</span><span class="sxs-lookup"><span data-stu-id="92edb-222">For example, in his book *Domain-Driven Design*, Eric Evans says this:</span></span>

<span data-ttu-id="92edb-223">複数の集計に関係するルールは、常に最新の状態であることを期待できません。</span><span class="sxs-lookup"><span data-stu-id="92edb-223">Any rule that spans Aggregates will not be expected to be up-to-date at all times.</span></span> <span data-ttu-id="92edb-224">イベント処理、バッチ処理、または他の更新メカニズムにより、他の依存関係はある特定の時間内に解決できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-224">Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time.</span></span> <span data-ttu-id="92edb-225">(128 ページ)</span><span class="sxs-lookup"><span data-stu-id="92edb-225">(page 128)</span></span>

<span data-ttu-id="92edb-226">Vaughn Vernon は、『[Effective Aggregate Design.Part II: Making Aggregates Work Together](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)』(効果的な集計設計パート II: 集計処理の連携) で次のように書いています。</span><span class="sxs-lookup"><span data-stu-id="92edb-226">Vaughn Vernon says the following in [Effective Aggregate Design. Part II: Making Aggregates Work Together](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):</span></span>

<span data-ttu-id="92edb-227">したがって、1 つの集計インスタンスでコマンドを実行するために、他のビジネス ルールを 1 つ以上の集計で実行する必要がある場合は、最終的な整合性を使います \[...\]。DDD モデルには最終的な整合性をサポートするための実用的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-227">Thus, if executing a command on one aggregate instance requires that additional business rules execute on one or more aggregates, use eventual consistency \[...\] There is a practical way to support eventual consistency in a DDD model.</span></span> <span data-ttu-id="92edb-228">集計メソッドが発行したドメイン イベントは、1 つ以上の非同期サブスクライバーに時間内に配信されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-228">An aggregate method publishes a domain event that is in time delivered to one or more asynchronous subscribers.</span></span>

<span data-ttu-id="92edb-229">この原理は、多数の集計またはエンティティにまたがるトランザクションではなく、粒度が細かいトランザクションの採用に基づいています。</span><span class="sxs-lookup"><span data-stu-id="92edb-229">This rationale is based on embracing fine-grained transactions instead of transactions spanning many aggregates or entities.</span></span> <span data-ttu-id="92edb-230">考え方として、2 番目のケースでは、高いスケーラビリティが必要な大規模なアプリケーションではデータベース ロックの数がかなり多くなるということです。</span><span class="sxs-lookup"><span data-stu-id="92edb-230">The idea is that in the second case, the number of database locks will be substantial in large-scale applications with high scalability needs.</span></span> <span data-ttu-id="92edb-231">拡張性の高いアプリケーションでは複数の集計間に即時のトランザクション整合性は必要ないという事実を考えると、最終的な整合性の概念を受け入れるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="92edb-231">Embracing the fact that high-scalable applications need not have instant transactional consistency between multiple aggregates helps with accepting the concept of eventual consistency.</span></span> <span data-ttu-id="92edb-232">アトミックな変更はビジネスで必要ないことが多く、特定の操作にアトミックなトランザクションが必要かどうかを示すのは、常にドメイン専門家の責任です。</span><span class="sxs-lookup"><span data-stu-id="92edb-232">Atomic changes are often not needed by the business, and it is in any case the responsibility of the domain experts to say whether particular operations need atomic transactions or not.</span></span> <span data-ttu-id="92edb-233">常に操作で複数の集計の間にアトミックなトランザクションが必要な場合は、集計をもっと大きくする必要があるかどうか、または集計が正しく設計されているか疑問に感じることがあります。</span><span class="sxs-lookup"><span data-stu-id="92edb-233">If an operation always needs an atomic transaction between multiple aggregates, you might ask whether your aggregate should be larger or was not correctly designed.</span></span>

<span data-ttu-id="92edb-234">一方、Jimmy Bogard のような他の開発者や設計者は、単一のトランザクションが複数の集計にまたがってもかまわないと考えています。ただし、このような追加の集計が同じ元のコマンドの副作用に関係している場合だけです。</span><span class="sxs-lookup"><span data-stu-id="92edb-234">However, other developers and architects like Jimmy Bogard are okay with spanning a single transaction across several aggregates—but only when those additional aggregates are related to side effects for the same original command.</span></span> <span data-ttu-id="92edb-235">たとえば、Bogard は「[A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)」(よりよいドメイン イベント パターン) で次のように書いています。</span><span class="sxs-lookup"><span data-stu-id="92edb-235">For instance, in [A better domain events pattern](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard says this:</span></span>

<span data-ttu-id="92edb-236">通常はドメイン イベントの副作用は同じ論理トランザクション内で発生する必要がありますが、必ずしも同じドメイン イベント発生スコープ内である必要はありません \[...\]。トランザクションをコミットする直前に、対応するハンドラーにイベントをディスパッチします。</span><span class="sxs-lookup"><span data-stu-id="92edb-236">Typically, I want the side effects of a domain event to occur within the same logical transaction, but not necessarily in the same scope of raising the domain event \[...\] Just before we commit our transaction, we dispatch our events to their respective handlers.</span></span>

<span data-ttu-id="92edb-237">元のトランザクションをコミットする "*直前*" にドメイン イベントをディスパッチする場合は、これらのイベントの副作用を同じトランザクションに含まれるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="92edb-237">If you dispatch the domain events right *before* committing the original transaction, it is because you want the side effects of those events to be included in the same transaction.</span></span> <span data-ttu-id="92edb-238">たとえば、EF DbContext SaveChanges メソッドが失敗した場合、トランザクションは、関連するドメイン イベント ハンドラーによって実装されているすべての副作用操作の結果を含む、すべての変更をロールバックします。</span><span class="sxs-lookup"><span data-stu-id="92edb-238">For example, if the EF DbContext SaveChanges method fails, the transaction will roll back all changes, including the result of any side effect operations implemented by the related domain event handlers.</span></span> <span data-ttu-id="92edb-239">これは、DbContext の有効期間の範囲が、既定で "スコープ" と定義されているためです。</span><span class="sxs-lookup"><span data-stu-id="92edb-239">This is because the DbContext life scope is by default defined as "scoped."</span></span> <span data-ttu-id="92edb-240">したがって、DbContext オブジェクトは、同じスコープ内またはオブジェクト グラフ内でインスタンス化されている複数のリポジトリ オブジェクト間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-240">Therefore, the DbContext object is shared across multiple repository objects being instantiated within the same scope or object graph.</span></span> <span data-ttu-id="92edb-241">これは、Web API または MVC アプリを開発するときの HttpRequest スコープと一致します。</span><span class="sxs-lookup"><span data-stu-id="92edb-241">This coincides with the HttpRequest scope when developing Web API or MVC apps.</span></span>

<span data-ttu-id="92edb-242">実際には、どちらの方法 (単一のアトミック トランザクションと最終的な整合性) も適切な場合があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-242">In reality, both approaches (single atomic transaction and eventual consistency) can be right.</span></span> <span data-ttu-id="92edb-243">どちらがよいかは、ドメインまたはビジネスの要件と、ドメイン専門家の意見に依存します。</span><span class="sxs-lookup"><span data-stu-id="92edb-243">It really depends on your domain or business requirements and what the domain experts tell you.</span></span> <span data-ttu-id="92edb-244">また、サービスに必要なスケーラビリティのレベルにも依存します (トランザクションの粒度が細かいほど、データベース ロックに関する影響は小さくなります)。</span><span class="sxs-lookup"><span data-stu-id="92edb-244">It also depends on how scalable you need the service to be (more granular transactions have less impact with regard to database locks).</span></span> <span data-ttu-id="92edb-245">また、最終的な整合性では、集計間で可能性のある不整合を検出するためにより複雑なコードが必要であり、補正アクションを実装する必要があるため、コードにかけられる費用によっても左右されます。</span><span class="sxs-lookup"><span data-stu-id="92edb-245">And it depends on how much investment you are willing to make in your code, since eventual consistency requires more complex code in order to detect possible inconsistencies across aggregates and the need to implement compensatory actions.</span></span> <span data-ttu-id="92edb-246">元の集計に変更をコミットした後、イベントがディスパッチされるとき、問題があってイベント ハンドラーが副作用をコミットできない場合は、集計の間に不整合が発生することを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-246">Take into account that if you commit changes to the original aggregate and afterwards, when the events are being dispatched, there is an issue and the event handlers cannot commit their side effects, you will have inconsistencies between aggregates.</span></span>

<span data-ttu-id="92edb-247">補正アクションを実装するには、ドメイン イベントを追加データベース テーブルに格納して、ドメイン インベントが元のトランザクションの一部になるようにします。</span><span class="sxs-lookup"><span data-stu-id="92edb-247">A way to allow compensatory actions would be to store the domain events in additional database tables so they can be part of the original transaction.</span></span> <span data-ttu-id="92edb-248">その後は、バッチ処理で、イベントのリストと集計の現在の状態を比較することによって不整合を検出し、補正アクションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-248">Afterwards, you could have a batch process that detects inconsistencies and runs compensatory actions by comparing the list of events with the current state of the aggregates.</span></span> <span data-ttu-id="92edb-249">補正アクションは開発側からの詳細な分析が必要な複雑なトピックの一部であり、ビジネス ユーザーやドメイン専門家との検討が含まれます。</span><span class="sxs-lookup"><span data-stu-id="92edb-249">The compensatory actions are part of a complex topic that will require deep analysis from your side, which includes discussing it with the business user and domain experts.</span></span>

<span data-ttu-id="92edb-250">どのような場合でも、必要なアプローチを選ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-250">In any case, you can choose the approach you need.</span></span> <span data-ttu-id="92edb-251">ただし、EF Core とリレーショナル データベースを使うときは、初期遅延アプローチ (コミットの前にイベントを生成し、単一のトランザクションを使う) が最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="92edb-251">But the initial deferred approach—raising the events before committing, so you use a single transaction—is the simplest approach when using EF Core and a relational database.</span></span> <span data-ttu-id="92edb-252">実装が簡単であり、多くのビジネス ケースで有効です。</span><span class="sxs-lookup"><span data-stu-id="92edb-252">It is easier to implement and valid in many business cases.</span></span> <span data-ttu-id="92edb-253">eShopOnContainers の注文マイクロサービスでも、この方法が使われています。</span><span class="sxs-lookup"><span data-stu-id="92edb-253">It is also the approach used in the ordering microservice in eShopOnContainers.</span></span>

<span data-ttu-id="92edb-254">しかし、これらのイベントを対応するイベント ハンドラーに実際にディスパッチするにはどうすればよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="92edb-254">But how do you actually dispatch those events to their respective event handlers?</span></span> <span data-ttu-id="92edb-255">前の例で使われている \_mediator オブジェクトとはいったい何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="92edb-255">What is the \_mediator object that you see in the previous example?</span></span> <span data-ttu-id="92edb-256">これは、イベントとそのイベント ハンドラーの間をマップするために使うことができる手法および成果物に関係します。</span><span class="sxs-lookup"><span data-stu-id="92edb-256">That has to do with the techniques and artifacts you can use to map between events and their event handlers.</span></span>

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a><span data-ttu-id="92edb-257">ドメイン イベント ディスパッチャー: イベントからイベント ハンドラーへのマッピング</span><span class="sxs-lookup"><span data-stu-id="92edb-257">The domain event dispatcher: mapping from events to event handlers</span></span>

<span data-ttu-id="92edb-258">イベントをディスパッチまたは発行できるようになったら、関連するすべてのハンドラーがイベントを入手し、イベントに基づいて副作用を処理できるように、イベントを発行する何らかの種類の成果物が必要です。</span><span class="sxs-lookup"><span data-stu-id="92edb-258">Once you're able to dispatch or publish the events, you need some kind of artifact that will publish the event, so that every related handler can get it and process side effects based on that event.</span></span>

<span data-ttu-id="92edb-259">1 つの方法は、おそらくインメモリ イベントではなくサービス バスに基づく、実際のメッセージング システムまたはイベント バスです。</span><span class="sxs-lookup"><span data-stu-id="92edb-259">One approach is a real messaging system or even an event bus, possibly based on a service bus as opposed to in-memory events.</span></span> <span data-ttu-id="92edb-260">ただし、最初のケースでは、必要なのは同じプロセス内でこれらのイベントを処理することだけなので (つまり、同じドメイン内および同じアプリケーション レイヤー内)、実際のメッセージングを使うのは過剰です。</span><span class="sxs-lookup"><span data-stu-id="92edb-260">However, for the first case, real messaging would be overkill for processing domain events, since you just need to process those events within the same process (that is, within the same domain and application layer).</span></span>

<span data-ttu-id="92edb-261">イベントを複数のイベント ハンドラーにマップするもう 1 つの方法は、イベントをディスパッチする場所を動的に推論できるように、IoC コンテナーへの型の登録を使うことです。</span><span class="sxs-lookup"><span data-stu-id="92edb-261">Another way to map events to multiple event handlers is by using types registration in an IoC container so that you can dynamically infer where to dispatch the events.</span></span> <span data-ttu-id="92edb-262">つまり、特定のイベント ハンドラーで必要な特定のイベントを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-262">In other words, you need to know what event handlers need to get a specific event.</span></span> <span data-ttu-id="92edb-263">図 9-16 はこのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="92edb-263">Figure 9-16 shows a simplified approach for that.</span></span>

![](./media/image17.png)

<span data-ttu-id="92edb-264">**図 9-16**: </span><span class="sxs-lookup"><span data-stu-id="92edb-264">**Figure 9-16**.</span></span> <span data-ttu-id="92edb-265">IoC を使ったドメイン イベント ディスパッチャー</span><span class="sxs-lookup"><span data-stu-id="92edb-265">Domain event dispatcher using IoC</span></span>

<span data-ttu-id="92edb-266">このアプローチを実装するためのすべての仕組みと成果物を自分で作成することができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-266">You can build all the plumbing and artifacts to implement that approach by yourself.</span></span> <span data-ttu-id="92edb-267">ただし、[MediatR](https://github.com/jbogard/MediatR) のようなライブラリを使うこともできます。このライブラリは内部で IoC コンテナーを使っています。</span><span class="sxs-lookup"><span data-stu-id="92edb-267">However, you can also use available libraries like [MediatR](https://github.com/jbogard/MediatR), which underneath the covers uses your IoC container.</span></span> <span data-ttu-id="92edb-268">したがって、定義済みのインターフェイスとメディエーター オブジェクトのパブリッシュ/ディスパッチ メソッドを直接使うことができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-268">You can therefore directly use the predefined interfaces and the mediator object’s publish/dispatch methods.</span></span>

<span data-ttu-id="92edb-269">コードでは最初に、イベント ハンドラーの型を IoC コンテナーに登録する必要があります。次に示す [eShopOnContainers の Ordering マイクロサービス](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs)での例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="92edb-269">In code, you first need to register the event handler types in your IoC container, as shown in the following example at [eShopOnContainers Ordering microservice](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

<span data-ttu-id="92edb-270">このコードは最初に、いずれかのハンドラーを保持するアセンブリを探すことによってドメイン イベント ハンドラーが含まれているアセンブリを特定します (typeof(ValidateOrAddBuyerAggregateWhenXxxx) を使いますが、他のイベント ハンドラーを選んでアセンブリを探してもかまいません)。</span><span class="sxs-lookup"><span data-stu-id="92edb-270">The code first identifies the assembly that contains the domain event handlers by locating the assembly that holds any of the handlers (using typeof(ValidateOrAddBuyerAggregateWhenXxxx), but you could have chosen any other event handler to locate the assembly).</span></span> <span data-ttu-id="92edb-271">すべてのイベント ハンドラーは IAsyncNotificationHandler インターフェイスを実装しているので、次に、それらの型だけを検索してすべてのイベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="92edb-271">Since all the event handlers implement the IAsyncNotificationHandler interface, the code then just searches for those types and registers all the event handlers.</span></span>

### <a name="how-to-subscribe-to-domain-events"></a><span data-ttu-id="92edb-272">ドメイン イベントをサブスクライブする方法</span><span class="sxs-lookup"><span data-stu-id="92edb-272">How to subscribe to domain events</span></span>

<span data-ttu-id="92edb-273">MediatR を使うときは、次のコードでわかるように、INotificationHandler インターフェイスのジェネリック パラメーターで提供されるイベントの型を、各イベント ハンドラーで使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-273">When you use MediatR, each event handler must use an event type that is provided on the generic parameter of the INotificationHandler interface, as you can see in the following code:</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

<span data-ttu-id="92edb-274">イベントとイベント ハンドラーの間の関係 (これはサブスクリプションと考えることができます) に基づいて、MediatR の成果物は各イベントのすべてのイベント ハンドラーを検出し、それらの各イベント ハンドラーをトリガーすることができます。</span><span class="sxs-lookup"><span data-stu-id="92edb-274">Based on the relationship between event and event handler, which can be considered the subscription, the MediatR artifact can discover all the event handlers for each event and trigger each of those event handlers.</span></span>

### <a name="how-to-handle-domain-events"></a><span data-ttu-id="92edb-275">ドメイン イベントを処理する方法</span><span class="sxs-lookup"><span data-stu-id="92edb-275">How to handle domain events</span></span>

<span data-ttu-id="92edb-276">最後になりますが、通常、イベント ハンドラーでは、インフラストラクチャのリポジトリを使って必要な他の集計を取得して副作用のドメイン ロジックを実行する、アプリケーション レイヤーのコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="92edb-276">Finally, the event handler usually implements application layer code that uses infrastructure repositories to obtain the required additional aggregates and to execute side-effect domain logic.</span></span> <span data-ttu-id="92edb-277">次に示すのは、[eShopOnContainers のドメイン イベント ハンドラーのコード](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)での実装の例です。</span><span class="sxs-lookup"><span data-stu-id="92edb-277">The following [domain event handler code at eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), shows an implementation example.</span></span>

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;        
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

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer) 
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

<span data-ttu-id="92edb-278">このドメイン イベント ハンドラーのコードは、インフラストラクチャ永続レイヤーについて次のセクションで説明するように、インフラストラクチャのリポジトリを使っているので、アプリケーション レイヤーのコードと考えられます。</span><span class="sxs-lookup"><span data-stu-id="92edb-278">The previous domain event handler code is considered application layer code because it uses infrastructure repositories, as explained in the next section on the infrastructure-persistence layer.</span></span> <span data-ttu-id="92edb-279">イベント ハンドラーは、他のインフラストラクチャ コンポーネントを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="92edb-279">Event handlers could also use other infrastructure components.</span></span>

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a><span data-ttu-id="92edb-280">ドメイン イベントは、マイクロサービス境界の外部で発行される統合イベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-280">Domain events can generate integration events to be published outside of the microservice boundaries</span></span>

<span data-ttu-id="92edb-281">最後に、重要なこととして、複数のマイクロサービスにイベントを伝達することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="92edb-281">Finally, is important to mention that you might sometimes want to propagate events across multiple microservices.</span></span> <span data-ttu-id="92edb-282">これは統合イベントと見なされ、任意の特定のドメイン イベント ハンドラーからイベント バスを介して発行できます。</span><span class="sxs-lookup"><span data-stu-id="92edb-282">That is considered an integration event, and it could be published through an event bus from any specific domain event handler.</span></span>

## <a name="conclusions-on-domain-events"></a><span data-ttu-id="92edb-283">ドメイン イベントのまとめ</span><span class="sxs-lookup"><span data-stu-id="92edb-283">Conclusions on domain events</span></span>

<span data-ttu-id="92edb-284">説明したように、ドメイン内での変更の副作用を明示的に実装するには、ドメイン イベントを使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-284">As stated, use domain events to explicitly implement side effects of changes within your domain.</span></span> <span data-ttu-id="92edb-285">DDD の用語では、1 つ以上の集計に副作用を明示的に実装するには、ドメイン イベントを使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-285">To use DDD terminology, use domain events to explicitly implement side effects across one or multiple aggregates.</span></span> <span data-ttu-id="92edb-286">さらに、スケーラビリティを向上させ、データベース ロックの影響を小さくする必要がある場合は、同じドメイン内の集計の間の最終的な整合性を使います。</span><span class="sxs-lookup"><span data-stu-id="92edb-286">Additionally, and for better scalability and less impact on database locks, use eventual consistency between aggregates within the same domain.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="92edb-287">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="92edb-287">Additional resources</span></span>

-   <span data-ttu-id="92edb-288">**Greg Young。ドメイン イベントとは**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span><span class="sxs-lookup"><span data-stu-id="92edb-288">**Greg Young. What is a Domain Event?**
[*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)</span></span>

-   <span data-ttu-id="92edb-289">**Jan Stenberg。ドメイン イベントと最終的な整合性**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span><span class="sxs-lookup"><span data-stu-id="92edb-289">**Jan Stenberg. Domain Events and Eventual Consistency**
[*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)</span></span>

-   <span data-ttu-id="92edb-290">**Jimmy Bogard。よりよいドメイン イベント パターン**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span><span class="sxs-lookup"><span data-stu-id="92edb-290">**Jimmy Bogard. A better domain events pattern**
[*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)</span></span>

-   <span data-ttu-id="92edb-291">**Vaughn Vernon。効果的な集計設計パート II: 集計処理の連携**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span><span class="sxs-lookup"><span data-stu-id="92edb-291">**Vaughn Vernon. Effective Aggregate Design Part II: Making Aggregates Work Together**
[*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)</span></span>

-   <span data-ttu-id="92edb-292">**Jimmy Bogard。ドメインの強化: ドメイン イベント**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span><span class="sxs-lookup"><span data-stu-id="92edb-292">**Jimmy Bogard. Strengthening your domain: Domain Events**
*<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *</span></span>

-   <span data-ttu-id="92edb-293">**Tony Truong。ドメイン イベント パターンの例**
    [*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span><span class="sxs-lookup"><span data-stu-id="92edb-293">**Tony Truong. Domain Events Pattern Example**
[*http://www.tonytruong.net/domain-events-pattern-example/*](http://www.tonytruong.net/domain-events-pattern-example/)</span></span>

-   <span data-ttu-id="92edb-294">**Udi Dahan。完全にカプセル化されたドメイン モデルを作成する方法**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="92edb-294">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>

-   <span data-ttu-id="92edb-295">**Udi Dahan。ドメイン イベント – テイク 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span><span class="sxs-lookup"><span data-stu-id="92edb-295">**Udi Dahan. Domain Events – Take 2**
[*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)</span></span>

-   <span data-ttu-id="92edb-296">**Udi Dahan。ドメイン イベント – 救済**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span><span class="sxs-lookup"><span data-stu-id="92edb-296">**Udi Dahan. Domain Events – Salvation**
[*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)</span></span>

-   <span data-ttu-id="92edb-297">**Jan Kronquist。ドメイン イベントを発行しないで返す**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span><span class="sxs-lookup"><span data-stu-id="92edb-297">**Jan Kronquist. Don't publish Domain Events, return them!**
[*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)</span></span>

-   <span data-ttu-id="92edb-298">**Cesar de la Torre。DDD およびマイクロサービス アーキテクチャでのドメイン イベントと統合イベント**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span><span class="sxs-lookup"><span data-stu-id="92edb-298">**Cesar de la Torre. Domain Events vs. Integration Events in DDD and microservices architectures**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="92edb-299">[前へ](client-side-validation.md) [次へ](infrastructure-persistence-layer-design.md)</span><span class="sxs-lookup"><span data-stu-id="92edb-299">[Previous] (client-side-validation.md) [Next] (infrastructure-persistence-layer-design.md)</span></span>
