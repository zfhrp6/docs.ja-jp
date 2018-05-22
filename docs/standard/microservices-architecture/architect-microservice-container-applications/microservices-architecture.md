---
title: マイクロサービス アーキテクチャ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービス アーキテクチャ
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bcaacce323ed9afa482660f409312f9a1b82cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="microservices-architecture"></a><span data-ttu-id="d678e-103">マイクロサービス アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="d678e-103">Microservices architecture</span></span>

<span data-ttu-id="d678e-104">名前が示すように、マイクロサービス アーキテクチャは、一連の小さなサービスとしてサーバー アプリケーションを構築するアプローチです。</span><span class="sxs-lookup"><span data-stu-id="d678e-104">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="d678e-105">各サービスは独自のプロセスで実行され、HTTP/HTTPS、WebSockets、[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol) などのプロトコルを使用して他のプロセスと通信します。</span><span class="sxs-lookup"><span data-stu-id="d678e-105">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="d678e-106">各マイクロサービスは、特定のコンテキスト境界内で特定のエンドツーエンドのドメインまたはビジネス機能を実装します。個々のマイクロサービスを自律的に開発し、独立して展開可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d678e-106">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="d678e-107">最後に、さまざまなデータ ストレージ テクノロジ (SQL、NoSQL) とさまざまなプログラミング言語に基づいて、各マイクロサービスは関連するドメイン データ モデルとドメイン ロジック (主権と分散データ管理) を所有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d678e-107">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="d678e-108">マイクロサービスはどのくらいのサイズにすべきでしょうか。</span><span class="sxs-lookup"><span data-stu-id="d678e-108">What size should a microservice be?</span></span> <span data-ttu-id="d678e-109">マイクロサービスを開発する場合、サイズは重要なポイントではありません。</span><span class="sxs-lookup"><span data-stu-id="d678e-109">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="d678e-110">その代わり、弱く結合されたサービスを作成して、サービスごとに開発、展開、およびスケールの自律性を持たせることが重要です。</span><span class="sxs-lookup"><span data-stu-id="d678e-110">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="d678e-111">当然ながら、マイクロサービスを特定して設計する場合は、他のマイクロサービスとの直接の依存関係が多くなりすぎない限り、できるだけマイクロサービスを小さくするようにします。</span><span class="sxs-lookup"><span data-stu-id="d678e-111">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="d678e-112">マイクロサービスのサイズよりも重要な点は、必要な内部の凝集度と、他のサービスからの独立性です。</span><span class="sxs-lookup"><span data-stu-id="d678e-112">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="d678e-113">マイクロサービス アーキテクチャを選ぶ理由は何でしょうか。</span><span class="sxs-lookup"><span data-stu-id="d678e-113">Why a microservices architecture?</span></span> <span data-ttu-id="d678e-114">短く説明すると、長期的な機敏性を実現するためです。</span><span class="sxs-lookup"><span data-stu-id="d678e-114">In short, it provides long-term agility.</span></span> <span data-ttu-id="d678e-115">マイクロサービスを使用すると、個々が細かい自律的なライフサイクルを持つ、多数の独立して展開可能なサービスに基づいてアプリケーションを作成できるので、複雑で大規模で高度にスケーラブルなシステムの保守性を向上することができます。</span><span class="sxs-lookup"><span data-stu-id="d678e-115">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="d678e-116">また、個別にスケールアウトできることもマイクロサービスのメリットです。</span><span class="sxs-lookup"><span data-stu-id="d678e-116">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="d678e-117">1 つのモノリシックなアプリケーションを 1 ユニットとしてスケールアウトするのではなく、特定のマイクロサービスをスケールアウトできます。</span><span class="sxs-lookup"><span data-stu-id="d678e-117">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="d678e-118">その結果、需要に応えるために多くの処理能力やネットワーク帯域幅を必要とする機能領域だけをスケールアウトでき、スケールアウトする必要のない機能領域までスケールアウトすることはありません。</span><span class="sxs-lookup"><span data-stu-id="d678e-118">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="d678e-119">つまり、必要なハードウェア数が少ないため、コストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="d678e-119">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="d678e-120">**図 4-6**</span><span class="sxs-lookup"><span data-stu-id="d678e-120">**Figure 4-6**.</span></span> <span data-ttu-id="d678e-121">モノリシック展開とマイクロサービス アプローチ</span><span class="sxs-lookup"><span data-stu-id="d678e-121">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="d678e-122">図 4-6 に示すように、マイクロサービス アプローチを使用すると、複雑で大規模でスケーラブルなアプリケーションの特定の小さな領域を変更できるため、各マイクロサービスの柔軟な変更と迅速な繰り返しが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d678e-122">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="d678e-123">細かいマイクロサービスベースのアプリケーションを設計することで、継続的な統合と継続的デリバリーの方法を実現できます。</span><span class="sxs-lookup"><span data-stu-id="d678e-123">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="d678e-124">また、短期間でアプリケーションに新しい関数を配信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d678e-124">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="d678e-125">細かいアプリケーションの構成にすることで、マイクロサービスを単独で実行してテストし、マイクロサービス間の明確なコントラクトを維持しながら自律的に進化させることもできます。</span><span class="sxs-lookup"><span data-stu-id="d678e-125">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="d678e-126">インターフェイスまたはコントラクトを変更しない限り、任意のマイクロサービスの内部実装を変更することや、他のマイクロサービスを中断することなく新機能を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d678e-126">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="d678e-127">マイクロサービスベースのシステムを含む実稼働環境への移行を成功させるには、次の点が重要です。</span><span class="sxs-lookup"><span data-stu-id="d678e-127">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="d678e-128">サービスとインフラストラクチャの監視と正常性検査。</span><span class="sxs-lookup"><span data-stu-id="d678e-128">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="d678e-129">サービス (つまり、クラウドとオーケストレーター) のスケーラブルなインフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="d678e-129">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="d678e-130">複数レベルのセキュリティ設計と実装: 認証、承認、シークレット管理、セキュリティで保護された通信など。</span><span class="sxs-lookup"><span data-stu-id="d678e-130">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="d678e-131">高速なアプリケーション配信。通常は、チームによって異なるマイクロサービスに集中します。</span><span class="sxs-lookup"><span data-stu-id="d678e-131">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="d678e-132">DevOps および CI/CD のプラクティスとインフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="d678e-132">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="d678e-133">このガイドでは最初の 3 つのみを扱い、紹介しています。</span><span class="sxs-lookup"><span data-stu-id="d678e-133">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="d678e-134">アプリケーションのライフサイクルに関連する残り 2 つの点については、「[Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook)」(Microsoft プラットフォームとツールを使用してコンテナー化された Docker アプリケーションのライフサイクル) の電子書籍を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d678e-134">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d678e-135">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="d678e-135">Additional resources</span></span>

-   <span data-ttu-id="d678e-136">**Mark Russinovich。マイクロサービス: クラウドによって強化されるアプリケーションの革命**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="d678e-136">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="d678e-137">**Martin Fowler。マイクロサービス**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="d678e-137">**Martin Fowler. Microservices**
[*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="d678e-138">**Martin Fowler。マイクロサービスの前提条件**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="d678e-138">**Martin Fowler. Microservice Prerequisites**
[*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="d678e-139">**Jimmy Nilsson。チャンク クラウド コンピューティング**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="d678e-139">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="d678e-140">**Cesar de la Torre。Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル** (ダウンロード可能な e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="d678e-140">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="d678e-141">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="d678e-141">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
