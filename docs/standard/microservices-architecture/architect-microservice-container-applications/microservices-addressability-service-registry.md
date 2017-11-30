---
title: "Microservices addressability およびサービス レジストリ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices addressability およびサービス レジストリ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a><span data-ttu-id="d1eb9-104">Microservices addressability およびサービス レジストリ</span><span class="sxs-lookup"><span data-stu-id="d1eb9-104">Microservices addressability and the service registry</span></span>

<span data-ttu-id="d1eb9-105">各マイクロ サービスには、その場所を解決するために使用する一意の名前 (URL) があります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-105">Each microservice has a unique name (URL) that is used to resolve its location.</span></span> <span data-ttu-id="d1eb9-106">マイクロ サービスが実行されている場所でアドレス指定可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-106">Your microservice needs to be addressable wherever it is running.</span></span> <span data-ttu-id="d1eb9-107">、元のコンピューターを実行している特定のマイクロ サービスを検討する必要ことできます不適切なすばやく移動します。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-107">If you have to think about which computer is running a particular microservice, things can go bad quickly.</span></span> <span data-ttu-id="d1eb9-108">DNS が URL を特定のコンピューターに解決される、同じ方法で、マイクロ サービスを現在の場所が探索可能になるよう名前が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-108">In the same way that DNS resolves a URL to a particular computer, your microservice needs to have a unique name so that its current location is discoverable.</span></span> <span data-ttu-id="d1eb9-109">Microservices には、アドレス指定可能な名前で実行されているインフラストラクチャから独立して構成することが必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-109">Microservices need addressable names that make them independent from the infrastructure that they are running on.</span></span> <span data-ttu-id="d1eb9-110">つまりする必要があります、サービスを展開する方法と、検出方法の間の相互作用があること、[サービス レジストリ](http://microservices.io/patterns/service-registry.html)です。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-110">This implies that there is an interaction between how your service is deployed and how it is discovered, because there needs to be a [service registry](http://microservices.io/patterns/service-registry.html).</span></span> <span data-ttu-id="d1eb9-111">同様に、コンピューターが失敗したときに、レジストリ サービスできる必要がありますを示す、サービスが実行されているようになりました。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-111">In the same vein, when a computer fails, the registry service must be able to indicate where the service is now running.</span></span>

<span data-ttu-id="d1eb9-112">[サービス レジストリ パターン](http://microservices.io/patterns/service-registry.html)サービス検出の重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-112">The [service registry pattern](http://microservices.io/patterns/service-registry.html) is a key part of service discovery.</span></span> <span data-ttu-id="d1eb9-113">レジストリは、サービス インスタンスのネットワークの場所を含むデータベースです。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-113">The registry is a database containing the network locations of service instances.</span></span> <span data-ttu-id="d1eb9-114">サービス レジストリでは、可用性が高く、最新の状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-114">A service registry needs to be highly available and up to date.</span></span> <span data-ttu-id="d1eb9-115">クライアントは、サービスのレジストリから取得したネットワークの場所でキャッシュでした。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-115">Clients could cache network locations obtained from the service registry.</span></span> <span data-ttu-id="d1eb9-116">ただし、その情報を最終的に期限切れになりクライアントはサービス インスタンスを検出できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-116">However, that information eventually goes out of date and clients can no longer discover service instances.</span></span> <span data-ttu-id="d1eb9-117">その結果、サービス レジストリは、整合性を維持するためにレプリケーションのプロトコルを使用するサーバーのクラスターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-117">Consequently, a service registry consists of a cluster of servers that use a replication protocol to maintain consistency.</span></span>

<span data-ttu-id="d1eb9-118">マイクロ サービスの展開環境が (以降のセクションで説明する、クラスターと呼ばれます) によって、サービスの検出が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-118">In some microservice deployment environments (called clusters, to be covered in a later section), service discovery is built-in.</span></span> <span data-ttu-id="d1eb9-119">など、Azure コンテナー サービス環境内 Kubernetes とマラソンと DC/OS がサービスのインスタンスの登録を処理し、登録解除します。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-119">For example, within an Azure Container Service environment, Kubernetes and DC/OS with Marathon can handle service instance registration and deregistration.</span></span> <span data-ttu-id="d1eb9-120">サーバー側の検出のルーターの役割を果たす各クラスター ホストでプロキシでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-120">They also run a proxy on each cluster host that plays the role of server-side discovery router.</span></span> <span data-ttu-id="d1eb9-121">別の例は、Azure Service Fabric は、そのボックスの名前付けサービスをサービス レジストリにも提供します。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-121">Another example is Azure Service Fabric, which also provides a service registry through its out-of-the-box Naming Service.</span></span>

<span data-ttu-id="d1eb9-122">サービス レジストリともこの問題を解決するのに役立つ、API ゲートウェイ パターンの間で特定のオーバー ラップがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-122">Note that there is certain overlap between the service registry and the API gateway pattern, which helps solve this problem as well.</span></span> <span data-ttu-id="d1eb9-123">たとえば、[サービス ファブリック リバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)API ゲートウェイ サービス Fabrice 名前付けサービスのベースとし、内部のサービスにアドレス解決を解決するのに役立ちますの実装の型です。</span><span class="sxs-lookup"><span data-stu-id="d1eb9-123">For example, the [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) is a type of implementation of an API Gateway that is based on the Service Fabrice Naming Service and that helps resolve address resolution to the internal services.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d1eb9-124">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="d1eb9-124">Additional resources</span></span>

-   <span data-ttu-id="d1eb9-125">**Chris Richardson です。パターン: サービス レジストリ**
    *http://microservices.io/patterns/service-registry.html*</span><span class="sxs-lookup"><span data-stu-id="d1eb9-125">**Chris Richardson. Pattern: Service registry**
*http://microservices.io/patterns/service-registry.html*</span></span>

-   <span data-ttu-id="d1eb9-126">**Auth0 です。サービス レジストリ**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span><span class="sxs-lookup"><span data-stu-id="d1eb9-126">**Auth0. The Service Registry**
[*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span></span>

-   <span data-ttu-id="d1eb9-127">**サンガブリエル Schenker です。サービスの検出**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span><span class="sxs-lookup"><span data-stu-id="d1eb9-127">**Gabriel Schenker. Service discovery**
[*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d1eb9-128">[前](管理-マイクロ サービス-apis.md) [次へ] (microservice-based-composite-ui-shape-layout.md)</span><span class="sxs-lookup"><span data-stu-id="d1eb9-128">[Previous] (maintain-microservice-apis.md) [Next] (microservice-based-composite-ui-shape-layout.md)</span></span>
