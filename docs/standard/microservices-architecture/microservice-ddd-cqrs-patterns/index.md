---
title: "マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: be2d8a2fd77d65b82574efde3b9922a1176ad2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="a921b-104">マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む</span><span class="sxs-lookup"><span data-stu-id="a921b-104">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="a921b-105">*ビジネス ドメインの理解を反映するマイクロソフトサービスまたはコンテキスト境界ごとのドメイン モデルを設計する*</span><span class="sxs-lookup"><span data-stu-id="a921b-105">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="a921b-106">このセクションでは、複雑なサブシステムへの取り組みが必要な場合に実装する高度なマイクロサービスについて、またドメイン専門家の知識と絶えず変化するビジネス ルールに由来するマイクロサービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a921b-106">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="a921b-107">このセクションで使用するアーキテクチャ パターンは、図 9-1 に示すように、ドメイン駆動設計 (DDD: Domain-Driven Design) とコマンドクエリ責務分離 (CQRS: Command and Query Responsibility Segregation) の手法に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a921b-107">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="a921b-108">**図 9-1**</span><span class="sxs-lookup"><span data-stu-id="a921b-108">**Figure 9-1**.</span></span> <span data-ttu-id="a921b-109">外部マイクロサービス アーキテクチャとマイクロサービスごとの内部アーキテクチャ パターンとの対比</span><span class="sxs-lookup"><span data-stu-id="a921b-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="a921b-110">ただし、ASP.NET Core Web API サービスの実装方法や Swashbuckle による Swagger メタデータの公開方法など、データ駆動型マイクロサービスのテクニックのほとんどは、DDD パターンで内部的に実装される高度なマイクロサービスにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="a921b-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="a921b-111">前述した実施方法のほとんどはここでも、または任意の種類のマイクロ サービスにも適用されるため、このセクションは前のセクションの内容を増補するものとなっています。</span><span class="sxs-lookup"><span data-stu-id="a921b-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="a921b-112">このセクションでは、まず eShopOnContainers 参照アプリケーションで使用される簡略化された CQRS パターンの詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="a921b-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="a921b-113">後で DDD 手法の概要を説明しますが、そこでは、アプリケーションで再利用できる一般的なパターンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a921b-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="a921b-114">DDD は、学習用に豊富な技術資料が提供されている大きなテーマです。</span><span class="sxs-lookup"><span data-stu-id="a921b-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="a921b-115">入門書としては、Eric Evans 著の『[Domain-Driven Design](https://domainlanguage.com/ddd/)』 (ドメイン駆動設計)、さらに Vaughn Vernon、Jimmy Nilsson、Greg Young、Udi Dahan、Jimmy Bogard の各氏、およびその他多くの DDD/CQRS の専門家による技術資料などを利用できます。</span><span class="sxs-lookup"><span data-stu-id="a921b-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="a921b-116">ただし、DDD 手法の適用方法の習得には何より、具体的なビジネス ドメイン内で専門家との対話、ホワイトボードを使った議論、ドメイン モデリングのセッションを利用する試みが必要です。</span><span class="sxs-lookup"><span data-stu-id="a921b-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="a921b-117">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="a921b-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="a921b-118">DDD (ドメイン駆動設計)</span><span class="sxs-lookup"><span data-stu-id="a921b-118">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="a921b-119">**Eric Evans。Domain Language (ドメイン言語)**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="a921b-119">**Eric Evans. Domain Language**
[*http://domainlanguage.com/*](http://domainlanguage.com/)</span></span>

-   <span data-ttu-id="a921b-120">**Martin Fowler。Domain-Driven Design (ドメイン駆動設計)**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="a921b-120">**Martin Fowler. Domain-Driven Design**
[*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="a921b-121">**Jimmy Bogard。Strengthening your domain: a primer (ドメインの強化: 入門)**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="a921b-121">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="a921b-122">DDD 関連の書籍</span><span class="sxs-lookup"><span data-stu-id="a921b-122">DDD books</span></span>

-   <span data-ttu-id="a921b-123">**Eric Evans。Domain-Driven Design: Tackling Complexity in the Heart of Software (ドメイン駆動設計: ソフトウェアの核心にある複雑さに立ち向かう)**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="a921b-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="a921b-124">**Eric Evans。Domain-Driven Design Reference: Definitions and Pattern Summaries (ドメイン駆動設計リファレンス: 定義とパターンの概要)**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="a921b-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="a921b-125">**Vaughn Vernon。Implementing Domain-Driven Design (実践ドメイン駆動設計)**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="a921b-125">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="a921b-126">**Vaughn Vernon。Domain-Driven Design Distilled (ドメイン駆動設計の本質)**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="a921b-126">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="a921b-127">**Jimmy Nilsson。Applying Domain-Driven Design and Patterns (ドメイン駆動設計とパターンの適用)**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="a921b-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="a921b-128">**Cesar de la Torre。N-Layered Domain-Oriented Architecture Guide with .NET (.NET を使用した N 層のドメイン指向アーキテクチャのガイド)**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="a921b-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="a921b-129">**Abel Avram および Floyd Marinescu。Domain-Driven Design Quickly (ドメイン駆動設計の要点)**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="a921b-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="a921b-130">DDD に関するトレーニング</span><span class="sxs-lookup"><span data-stu-id="a921b-130">DDD training</span></span>

-   <span data-ttu-id="a921b-131">**Julie Lerman および Steve Smith。Domain-Driven Design Fundamentals (ドメイン駆動設計の基礎)**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="a921b-131">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a921b-132">[前へ] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [次へ] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="a921b-132">[Previous] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
