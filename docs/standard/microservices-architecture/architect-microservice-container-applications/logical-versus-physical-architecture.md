---
title: "論理アーキテクチャと物理アーキテクチャ"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 論理アーキテクチャと物理アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b08a5b8fb8f9df8a9a0a821fa85f1f6a94fce2d3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="757f1-104">論理アーキテクチャと物理アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="757f1-104">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="757f1-105">ここで一度立ち止まって、論理アーキテクチャと物理アーキテクチャの違いと、マイクロサービスベースのアプリケーションの設計に適用する方法について考察することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="757f1-105">It is useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="757f1-106">まず、マイクロサービスを構築するために、特定のテクノロジを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="757f1-106">To begin, building microservices does not require the use of any specific technology.</span></span> <span data-ttu-id="757f1-107">たとえば、マイクロサービスベースのアーキテクチャを作成するために Docker コンテナーは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="757f1-107">For instance, Docker containers are not mandatory in order to create a microservice-based architecture.</span></span> <span data-ttu-id="757f1-108">このようなマイクロサービスは、プレーン プロセスとして実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="757f1-108">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="757f1-109">マイクロサービスは論理アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="757f1-109">Microservices is a logical architecture.</span></span>

<span data-ttu-id="757f1-110">さらに、マイクロサービスが物理的に単一のサービス、プロセス、またはコンテナー (簡単に言うと、[eShopOnContainers](http://aka.ms/MicroservicesArchitecture) の最初のバージョンで採用されるアプローチ) として実装できる場合でも、ビジネス マイクロサービスと物理サービスまたはコンテナーとの間のこのパリティは、数十から数百のサービスで構成される大規模で複雑なアプリケーションを構築する場合は必ずしも必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="757f1-110">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity’s sake, that is the approach taken in the initial version of [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container is not necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="757f1-111">ここに、アプリケーションの論理アーキテクチャと物理アーキテクチャの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="757f1-111">This is where there is a difference between an application’s logical architecture and physical architecture.</span></span> <span data-ttu-id="757f1-112">システムの論理アーキテクチャと論理的境界は、物理または展開アーキテクチャと 1 対 1 でマップされるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="757f1-112">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="757f1-113">マップされない可能性はありますが、多くの場合はマップされます。</span><span class="sxs-lookup"><span data-stu-id="757f1-113">It can happen, but it often does not.</span></span>

<span data-ttu-id="757f1-114">特定のビジネス マイクロサービスまたは境界コンテキストを指定している場合でも、ビジネス マイクロサービスごとに単一のサービス (ASP.NET Web API など) または単一の Docker コンテナーを作成して実装する方法が最善というわけではありません。</span><span class="sxs-lookup"><span data-stu-id="757f1-114">Although you might have identified certain business microservices or Bounded Contexts, it does not mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="757f1-115">単一のサービスまたはコンテナーを使用して各ビジネス マイクロサービスを実装する必要がある、というルールを持つことは厳格すぎます。</span><span class="sxs-lookup"><span data-stu-id="757f1-115">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="757f1-116">そのため、ビジネス マイクロサービスまたは境界コンテキストは、物理アーキテクチャと一致する (または一致しない) 可能性がある論理アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="757f1-116">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="757f1-117">重要な点は、コードと状態を独立してバージョン管理、展開、およびスケーリングできるようにすることで、ビジネス マイクロサービスまたは境界コンテキストを自律的にする必要があることです。</span><span class="sxs-lookup"><span data-stu-id="757f1-117">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="757f1-118">図 4-8 に示すように、カタログ ビジネス マイクロサービスは、いくつかのサービスまたはプロセスで構成されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="757f1-118">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="757f1-119">また、複数の ASP.NET Web API サービス、または HTTP やその他のプロトコルを使用するその他の種類のサービスである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="757f1-119">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="757f1-120">さらに重要な点は、これらのサービスが同じビジネス ドメインに対して一貫性がある限り、サービスは同じデータを共有できることです。</span><span class="sxs-lookup"><span data-stu-id="757f1-120">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![](./media/image8.png)

<span data-ttu-id="757f1-121">**図 4-8**</span><span class="sxs-lookup"><span data-stu-id="757f1-121">**Figure 4-8**.</span></span> <span data-ttu-id="757f1-122">複数の物理サービスを持つビジネス マイクロサービス</span><span class="sxs-lookup"><span data-stu-id="757f1-122">Business microservice with several physical services</span></span>

<span data-ttu-id="757f1-123">Web API サービスは Search サービスと同じデータをターゲットにしているため、この例のサービスは同じデータ モデルを共有します。</span><span class="sxs-lookup"><span data-stu-id="757f1-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="757f1-124">そのため、ビジネス マイクロサービスの物理的な実装では、機能を分割して、必要に応じてこうした各内部サービスを拡大縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="757f1-124">So, in the physical implementation of the business microservice, you are splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="757f1-125">通常は Web API サービスに Search サービスよりも多くのインスタンスが必要な場合や、その逆の場合があります。</span><span class="sxs-lookup"><span data-stu-id="757f1-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.)</span></span>

<span data-ttu-id="757f1-126">つまり、マイクロサービスの論理アーキテクチャは、物理的な展開アーキテクチャと必ずしも一致するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="757f1-126">In short, the logical architecture of microservices does not always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="757f1-127">このガイドで "マイクロサービス" と言う場合は、1 つ以上のサービスにマッピングできるビジネスまたは論理マイクロサービスを意味します。</span><span class="sxs-lookup"><span data-stu-id="757f1-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more services.</span></span> <span data-ttu-id="757f1-128">ほとんどの場合は単一のサービスですが、複数のサービスの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="757f1-128">In most cases, this will be a single service, but it might be more.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="757f1-129">[Previous] (data-sovereignty-per-microservice.md) [Next] (distributed-data-management.md)</span><span class="sxs-lookup"><span data-stu-id="757f1-129">[Previous] (data-sovereignty-per-microservice.md) [Next] (distributed-data-management.md)</span></span>
