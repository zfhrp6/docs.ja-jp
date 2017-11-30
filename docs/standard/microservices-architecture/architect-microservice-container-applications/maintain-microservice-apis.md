---
title: "作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="56847-104">作成、進化、およびバージョン管理マイクロ サービス Api とコントラクト</span><span class="sxs-lookup"><span data-stu-id="56847-104">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="56847-105">マイクロ サービス API は、サービスとクライアント間のコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="56847-105">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="56847-106">単独で拡張、マイクロ サービス コントラクトが非常に重要な理由は、その API コントラクトが損なわれていない場合にのみことができます。</span><span class="sxs-lookup"><span data-stu-id="56847-106">You will be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="56847-107">コントラクトを変更する場合、クライアント アプリケーションまたは API ゲートウェイに影響します。</span><span class="sxs-lookup"><span data-stu-id="56847-107">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="56847-108">API 定義の性質は、どのプロトコルを使用しているによって異なります。</span><span class="sxs-lookup"><span data-stu-id="56847-108">The nature of the API definition depends on which protocol you are using.</span></span> <span data-ttu-id="56847-109">たとえば、メッセージングを使用している場合 (など[AMQP](https://www.amqp.org/))、API は、メッセージの種類。</span><span class="sxs-lookup"><span data-stu-id="56847-109">For instance, if you are using messaging (like [AMQP](https://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="56847-110">HTTP と RESTful サービスを使用している場合、Url と、要求と応答の JSON 形式の API で構成されます。</span><span class="sxs-lookup"><span data-stu-id="56847-110">If you are using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="56847-111">ただし、場合でもよく考えられた、初期のコントラクトは、サービス API が時間の経過と共に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56847-111">However, even if you are thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="56847-112">このような場合 —、API が複数のクライアント アプリケーションによって使用されるパブリック API である場合に特にと -通常、新しい API コントラクトにアップグレードするすべてのクライアントを強制できません。</span><span class="sxs-lookup"><span data-stu-id="56847-112">When that happens—and especially if your API is a public API consumed by multiple client applications—you typically cannot force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="56847-113">通常、サービス コントラクトの新旧両方のバージョンを同時に実行している方法でサービスの新しいバージョンを増分配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56847-113">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="56847-114">そのため、サービスのバージョン管理するための戦略を理解しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="56847-114">Therefore, it is important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="56847-115">API が変更されたが、API に属性またはパラメーターを追加する場合と同様に、小さいとき、古い API を使用するクライアントを切り替えるし、サービスの新しいバージョンで機能します。</span><span class="sxs-lookup"><span data-stu-id="56847-115">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="56847-116">既定値は、必要なすべての不足している属性を提供することができ、クライアントは、すべての余分な応答属性を無視できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="56847-116">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="56847-117">ただし、場合によって、サービス API にメジャーと互換性のない変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="56847-117">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="56847-118">すぐに新しいバージョンにアップグレードするには、クライアント アプリケーションまたはサービスを強制的にできない可能性があります、ために、サービスは、一定期間の古いバージョンの API をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56847-118">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="56847-119">REST などの HTTP ベースのメカニズムを使用している場合、1 つは、URL または HTTP ヘッダーには、API のバージョン番号を埋め込むにです。</span><span class="sxs-lookup"><span data-stu-id="56847-119">If you are using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into a HTTP header.</span></span> <span data-ttu-id="56847-120">同じサービス インスタンス内で同時に、サービスの両方のバージョンを実装するか、または API のバージョンを処理するそれぞれの異なるインスタンスを展開するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="56847-120">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="56847-121">これをお勧め、[媒介パターン](https://en.wikipedia.org/wiki/Mediator_pattern)(たとえば、 [MediatR ライブラリ](https://github.com/jbogard/MediatR)) を独立したハンドラーを別の実装のバージョンを分離します。</span><span class="sxs-lookup"><span data-stu-id="56847-121">A good approach for this is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="56847-122">最後に、REST アーキテクチャを使用している場合、 [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia)バージョン管理に最適なソリューションは、サービス、および evolvable Api を許可します。</span><span class="sxs-lookup"><span data-stu-id="56847-122">Finally, if you are using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="56847-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="56847-123">Additional resources</span></span>

-   <span data-ttu-id="56847-124">**Scott Hanselman です。ASP.NET Core RESTful Web API のバージョン管理が簡単に作成**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span><span class="sxs-lookup"><span data-stu-id="56847-124">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
<http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx></span></span>

-   <span data-ttu-id="56847-125">**RESTful web API のバージョン管理**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span><span class="sxs-lookup"><span data-stu-id="56847-125">**Versioning a RESTful web API**
[*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)</span></span>

-   <span data-ttu-id="56847-126">**者を務める Roy Fielding です。バージョン管理、Hypermedia、および REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning></span><span class="sxs-lookup"><span data-stu-id="56847-126">**Roy Fielding. Versioning, Hypermedia, and REST**
<https://www.infoq.com/articles/roy-fielding-on-versioning></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="56847-127">[前](非同期のメッセージに基づく-communication.md) [次へ] (microservices-addressability-サービス-registry.md)</span><span class="sxs-lookup"><span data-stu-id="56847-127">[Previous] (asynchronous-message-based-communication.md) [Next] (microservices-addressability-service-registry.md)</span></span>
