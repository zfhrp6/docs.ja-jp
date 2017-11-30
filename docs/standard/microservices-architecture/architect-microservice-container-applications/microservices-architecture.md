---
title: "マイクロサービス アーキテクチャ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a><span data-ttu-id="0cc3a-104">マイクロサービス アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="0cc3a-104">Microservices architecture</span></span>

<span data-ttu-id="0cc3a-105">名前からわかるように、microservices アーキテクチャは、一連の小さなサービスとしてのサーバー アプリケーションを構築する方法です。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-105">As the name implies, a microservices architecture is an approach to building a server application as a set of small services.</span></span> <span data-ttu-id="0cc3a-106">各サービスが、独自のプロセスで実行され、HTTP、HTTPS、Websocket などのプロトコルを使用して他のプロセスと通信するか、 [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)です。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-106">Each service runs in its own process and communicates with other processes using protocols such as HTTP/HTTPS, WebSockets, or [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol).</span></span> <span data-ttu-id="0cc3a-107">各マイクロ サービスは、特定のエンド ツー エンドのドメインまたは特定のコンテキストの境界内でのビジネス機能を実装および各自律的に開発する必要があります個別に配置されます。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-107">Each microservice implements a specific end-to-end domain or business capability within a certain context boundary, and each must be developed autonomously and be deployable independently.</span></span> <span data-ttu-id="0cc3a-108">最後に、各マイクロ サービスでは、その関連するドメインのデータ モデルと別のデータ記憶域テクノロジ (SQL、NoSQL) と異なるプログラミング言語に基づくドメイン ロジック (に対しておよび分散データ管理) を所有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-108">Finally, each microservice should own its related domain data model and domain logic (sovereignty and decentralized data management) based on different data storage technologies (SQL, NoSQL) and different programming languages.</span></span>

<span data-ttu-id="0cc3a-109">どのようなサイズ、マイクロ サービスべきでしょうか。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-109">What size should a microservice be?</span></span> <span data-ttu-id="0cc3a-110">マイクロ サービスを開発するときに、サイズは、重要なポイントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-110">When developing a microservice, size should not be the important point.</span></span> <span data-ttu-id="0cc3a-111">代わりに、重要な点は、疎を作成するにはサービスを開発、配置、および各サービスのスケールの自律性があるように結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-111">Instead, the important point should be to create loosely coupled services so you have autonomy of development, deployment, and scale, for each service.</span></span> <span data-ttu-id="0cc3a-112">もちろんとを識別する microservices を設計、、ようにできるだけ小さくとその他の microservices が多すぎます直接的な依存関係があるない限り、しようとする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-112">Of course, when identifying and designing microservices, you should try to make them as small as possible as long as you do not have too many direct dependencies with other microservices.</span></span> <span data-ttu-id="0cc3a-113">ほど重要、マイクロ サービスのサイズは必要があります内部凝集度とその他のサービスから独立します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-113">More important than the size of the microservice is the internal cohesion it must have and its independence from other services.</span></span>

<span data-ttu-id="0cc3a-114">なぜ microservices アーキテクチャしますか?</span><span class="sxs-lookup"><span data-stu-id="0cc3a-114">Why a microservices architecture?</span></span> <span data-ttu-id="0cc3a-115">つまり、長期的な機敏性を提供します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-115">In short, it provides long-term agility.</span></span> <span data-ttu-id="0cc3a-116">Microservices は、細かいおよび自律的なライフ サイクルがあるとは別に配置可能なサービスの多くに基づくアプリケーションを作成することで複雑な大規模な拡張性の高いシステムで保守性の向上を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-116">Microservices enable better maintainability in complex, large, and highly-scalable systems by letting you create applications based on many independently deployable services that each have granular and autonomous lifecycles.</span></span>

<span data-ttu-id="0cc3a-117">追加のメリットとして microservices ことができますを個別に拡張します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-117">As an additional benefit, microservices can scale out independently.</span></span> <span data-ttu-id="0cc3a-118">単位としてスケール アウトする必要がありますを単一のモノリシックなアプリケーションはなく、代わりにスケール アウトできます microservices を特定します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-118">Instead of having a single monolithic application that you must scale out as a unit, you can instead scale out specific microservices.</span></span> <span data-ttu-id="0cc3a-119">このようにより多くの処理電源やネットワーク帯域幅のスケール アウトを拡張する必要がないアプリケーションの他の領域ではなく、要求をサポートするために必要な機能領域だけを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-119">That way, you can scale just the functional area that needs more processing power or network bandwidth to support demand, rather than scaling out other areas of the application that do not need to be scaled.</span></span> <span data-ttu-id="0cc3a-120">コストの節約は、ハードウェアが必要なのでを意味します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-120">That means cost savings because you need less hardware.</span></span>

![](./media/image6.png)

<span data-ttu-id="0cc3a-121">**図 4. ~ 6.**です。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-121">**Figure 4-6**.</span></span> <span data-ttu-id="0cc3a-122">モノリシックな展開と microservices アプローチ</span><span class="sxs-lookup"><span data-stu-id="0cc3a-122">Monolithic deployment versus the microservices approach</span></span>

<span data-ttu-id="0cc3a-123">図 4 ~ 6 に示す microservices アプローチで複雑な大規模なおよびスケーラブルなアプリケーションの特定、小さな領域を変更できるためアジャイル変更し、各マイクロ サービスの迅速な反復処理ができます。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-123">As Figure 4-6 shows, the microservices approach allows agile changes and rapid iteration of each microservice, because you can change specific, small areas of complex, large, and scalable applications.</span></span>

<span data-ttu-id="0cc3a-124">粒度の細かい microservices ベースのアプリケーションで有効に継続的インテグレーションと継続的配信のプラクティスを構築します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-124">Architecting fine-grained microservices-based applications enables continuous integration and continuous delivery practices.</span></span> <span data-ttu-id="0cc3a-125">また、アプリケーションに新しい関数の配信も向上します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-125">It also accelerates delivery of new functions into the application.</span></span> <span data-ttu-id="0cc3a-126">アプリケーションの粒度の細かいコンポジションを実行し、分離で microservices をテストして、それらの間のクリアのコントラクトを維持しながら自律的に進化させることができます。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-126">Fine-grained composition of applications also allows you to run and test microservices in isolation, and to evolve them autonomously while maintaining clear contracts between them.</span></span> <span data-ttu-id="0cc3a-127">インターフェイスまたはコントラクトを変更しない限り、任意のマイクロ サービスの内部実装を変更したりその他の microservices を分断することがなく新しい機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-127">As long as you do not change the interfaces or contracts, you can change the internal implementation of any microservice or add new functionality without breaking other microservices.</span></span>

<span data-ttu-id="0cc3a-128">Microservices ベースのシステムで実稼働に移行の成功を有効にする重要な側面を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-128">The following are important aspects to enable success in going into production with a microservices-based system:</span></span>

-   <span data-ttu-id="0cc3a-129">サービスとインフラストラクチャの監視および正常性チェックします。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-129">Monitoring and health checks of the services and infrastructure.</span></span>

-   <span data-ttu-id="0cc3a-130">(つまり、クラウド、orchestrators) サービスのスケーラブルなインフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-130">Scalable infrastructure for the services (that is, cloud and orchestrators).</span></span>

-   <span data-ttu-id="0cc3a-131">セキュリティの設計と実装を複数のレベルで: 認証、承認、機密情報の管理、セキュリティで保護された通信などです。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-131">Security design and implementation at multiple levels: authentication, authorization, secrets management, secure communication, etc.</span></span>

-   <span data-ttu-id="0cc3a-132">通常はチームごとに異なる microservices に焦点を当てたと共にアプリケーションの迅速な配信します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-132">Rapid application delivery, usually with different teams focusing on different microservices.</span></span>

-   <span data-ttu-id="0cc3a-133">DevOps と CI/CD のプラクティスおよびインフラストラクチャです。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-133">DevOps and CI/CD practices and infrastructure.</span></span>

<span data-ttu-id="0cc3a-134">、これらの最初の 3 つのみが対象か、このガイドで導入されました。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-134">Of these, only the first three are covered or introduced in this guide.</span></span> <span data-ttu-id="0cc3a-135">最後の 2 つのポイントは、アプリケーションのライフ サイクルに関連する、については、「その他[Microsoft プラットフォームとツールと Docker アプリケーションのライフ サイクルのコンテナー](https://aka.ms/dockerlifecycleebook)電子書籍します。</span><span class="sxs-lookup"><span data-stu-id="0cc3a-135">The last two points, which are related to application lifecycle, are covered in the additional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) e-book.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0cc3a-136">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="0cc3a-136">Additional resources</span></span>

-   <span data-ttu-id="0cc3a-137">**Mark Russinovich です。Microservices: アプリケーション revolution クラウドから電力を得て**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-137">**Mark Russinovich. Microservices: An application revolution powered by the cloud**
[*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)</span></span>

-   <span data-ttu-id="0cc3a-138">**Martin Fowler。Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-138">**Martin Fowler. Microservices**
[*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)</span></span>

-   <span data-ttu-id="0cc3a-139">**Martin Fowler。マイクロ サービスの前提条件**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-139">**Martin Fowler. Microservice Prerequisites**
[*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)</span></span>

-   <span data-ttu-id="0cc3a-140">**Jimmy Nilsson。チャンクのクラウド コンピューティング**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-140">**Jimmy Nilsson. Chunk Cloud Computing**
[*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)</span></span>

-   <span data-ttu-id="0cc3a-141">**Cesar de la Torre。Microsoft プラットフォームとツールのアプリケーションのライフ サイクルの Docker のコンテナー** (ダウンロード可能な電子書籍) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-141">**Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="0cc3a-142">[前](サービス-指向-architecture.md) [次へ] (データ-に対して-あたり-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="0cc3a-142">[Previous] (service-oriented-architecture.md) [Next] (data-sovereignty-per-microservice.md)</span></span>
