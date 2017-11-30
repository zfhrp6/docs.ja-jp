---
title: "論理アーキテクチャと物理アーキテクチャ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |論理アーキテクチャと物理アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="89180-104">論理アーキテクチャと物理アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="89180-104">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="89180-105">この時点でを停止し、上の論理アーキテクチャと物理アーキテクチャ、およびマイクロ サービス ベースのアプリケーションのデザインに適用するこの方法での違いを説明すると便利です。</span><span class="sxs-lookup"><span data-stu-id="89180-105">It is useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="89180-106">まず、microservices を構築しても、特定のテクノロジの使用は不要です。</span><span class="sxs-lookup"><span data-stu-id="89180-106">To begin, building microservices does not require the use of any specific technology.</span></span> <span data-ttu-id="89180-107">たとえば、Docker コンテナーは、マイクロ サービス ベースのアーキテクチャを作成するために必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="89180-107">For instance, Docker containers are not mandatory in order to create a microservice-based architecture.</span></span> <span data-ttu-id="89180-108">それら microservices がプレーンなプロセスとして実行することも可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89180-108">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="89180-109">Microservices は、論理アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="89180-109">Microservices is a logical architecture.</span></span>

<span data-ttu-id="89180-110">さらに、場合でも、マイクロ サービスを 1 つのサービス、プロセス、またはコンテナーとして物理的に実装できます (の初期のバージョンで採用されているアプローチをわかりやすくするために、 [eShopOnContainers](http://aka.ms/MicroservicesArchitecture))、間でこのパリティビジネス マイクロ サービスと物理サービスまたはコンテナーは必ずしも不要常に多く数十または数百ものサービスから成る大規模で複雑なアプリケーションをビルドするときです。</span><span class="sxs-lookup"><span data-stu-id="89180-110">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity’s sake, that is the approach taken in the initial version of [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container is not necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="89180-111">これは、ような場合は、アプリケーションの論理アーキテクチャと物理アーキテクチャの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="89180-111">This is where there is a difference between an application’s logical architecture and physical architecture.</span></span> <span data-ttu-id="89180-112">論理アーキテクチャおよびシステムの論理的な境界マップされていない必ずしも物理マシンまたは展開のアーキテクチャと一対一です。</span><span class="sxs-lookup"><span data-stu-id="89180-112">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="89180-113">発生する可能性が、ですが、多くの場合、開きません。</span><span class="sxs-lookup"><span data-stu-id="89180-113">It can happen, but it often does not.</span></span>

<span data-ttu-id="89180-114">特定のビジネス microservices または範囲指定されたコンテキストを識別が (ASP.NET Web API の場合) などの 1 つのサービスまたは各ビジネス マイクロ サービスの 1 つの Docker コンテナーを作成してそれらを実装する最善の方法が常にあることは限りません。</span><span class="sxs-lookup"><span data-stu-id="89180-114">Although you might have identified certain business microservices or Bounded Contexts, it does not mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="89180-115">各ビジネス マイクロ サービスをというルールが 1 つのサービスを使用して実装するのにまたはコンテナーが固定すぎます。</span><span class="sxs-lookup"><span data-stu-id="89180-115">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="89180-116">したがって、ビジネスのマイクロ サービスまたは範囲指定されたコンテキストは (またはない) が同時に発生する論理アーキテクチャと物理アーキテクチャ。</span><span class="sxs-lookup"><span data-stu-id="89180-116">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="89180-117">重要な点ビジネス マイクロ サービスまたは範囲指定されたコンテキストはあることです自律的なコードと状態になるとは独立してバージョン管理された、展開、およびスケールを許可します。</span><span class="sxs-lookup"><span data-stu-id="89180-117">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="89180-118">図 4-8 に示すいくつかのサービスやプロセスのカタログ ビジネス マイクロ サービスを構成することでした。</span><span class="sxs-lookup"><span data-stu-id="89180-118">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="89180-119">これらは、複数の ASP.NET Web API サービスまたはその他の種類の HTTP またはその他のプロトコルを使用してサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="89180-119">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="89180-120">さらに、これらのサービスは、同じビジネス ドメインに関してまとまりとして、サービスは、同じデータを共有でした。</span><span class="sxs-lookup"><span data-stu-id="89180-120">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![](./media/image8.png)

<span data-ttu-id="89180-121">**図 4-8**です。</span><span class="sxs-lookup"><span data-stu-id="89180-121">**Figure 4-8**.</span></span> <span data-ttu-id="89180-122">複数の物理サービスとビジネス マイクロ サービス</span><span class="sxs-lookup"><span data-stu-id="89180-122">Business microservice with several physical services</span></span>

<span data-ttu-id="89180-123">サービスの例では、Web API サービス、Search サービスと同じデータを対象とするために同じデータ モデルを共有します。</span><span class="sxs-lookup"><span data-stu-id="89180-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="89180-124">そのため、ビジネス マイクロ サービスの物理的な実装に分割する機能を拡張するための内部サービスのそれぞれを上下必要に応じて。</span><span class="sxs-lookup"><span data-stu-id="89180-124">So, in the physical implementation of the business microservice, you are splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="89180-125">おそらく、Web API サービス通常必要よりインスタンス Search サービスよりも、またはその逆です。)</span><span class="sxs-lookup"><span data-stu-id="89180-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.)</span></span>

<span data-ttu-id="89180-126">つまり、microservices の論理アーキテクチャ常にする必要はありません、物理的な展開アーキテクチャと一致します。</span><span class="sxs-lookup"><span data-stu-id="89180-126">In short, the logical architecture of microservices does not always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="89180-127">このガイドのマイクロ サービスをお伝えされるたびに意味ビジネスまたは 1 つまたは複数のサービスにマップできなかった論理のマイクロ サービスします。</span><span class="sxs-lookup"><span data-stu-id="89180-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more services.</span></span> <span data-ttu-id="89180-128">ほとんどの場合、これは、1 つのサービスですが詳細である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89180-128">In most cases, this will be a single service, but it might be more.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="89180-129">[前](データ-に対して-あたり-microservice.md) [次へ] (分散-データ-management.md)</span><span class="sxs-lookup"><span data-stu-id="89180-129">[Previous] (data-sovereignty-per-microservice.md) [Next] (distributed-data-management.md)</span></span>
