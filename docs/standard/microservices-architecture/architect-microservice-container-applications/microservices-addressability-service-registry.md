---
title: "マイクロサービスのアドレス指定能力およびサービス レジストリ"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスのアドレス指定能力およびサービス レジストリ"
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
ms.openlocfilehash: cc26b22d18d460fe6870da7360d73368e20f71d2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a><span data-ttu-id="ed999-104">マイクロサービスのアドレス指定能力およびサービス レジストリ</span><span class="sxs-lookup"><span data-stu-id="ed999-104">Microservices addressability and the service registry</span></span>

<span data-ttu-id="ed999-105">各マイクロサービスには、その場所を解決するために使用する一意の名前 (URL) が付けられています。</span><span class="sxs-lookup"><span data-stu-id="ed999-105">Each microservice has a unique name (URL) that is used to resolve its location.</span></span> <span data-ttu-id="ed999-106">マイクロサービスは、その実行場所にかかわらず、アドレス指定可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed999-106">Your microservice needs to be addressable wherever it is running.</span></span> <span data-ttu-id="ed999-107">特定のマイクロサービスをどのコンピューターで実行するかについて考える必要がある場合、事態はすぐに悪化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed999-107">If you have to think about which computer is running a particular microservice, things can go bad quickly.</span></span> <span data-ttu-id="ed999-108">DNS が URL を特定のコンピューターに解決するのと同様に、マイクロサービスの現在の場所が探索できるようにマイクロサービスには一意の名前が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed999-108">In the same way that DNS resolves a URL to a particular computer, your microservice needs to have a unique name so that its current location is discoverable.</span></span> <span data-ttu-id="ed999-109">マイクロサービスには、実行されているインフラストラクチャからマイクロサービスを独立させるためのアドレス指定可能な名前が必要です。</span><span class="sxs-lookup"><span data-stu-id="ed999-109">Microservices need addressable names that make them independent from the infrastructure that they are running on.</span></span> <span data-ttu-id="ed999-110">このことは、[サービス レジストリ](http://microservices.io/patterns/service-registry.html)が必要であるために、サービスの展開方法とサービスの検出方法との間には相互作用があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="ed999-110">This implies that there is an interaction between how your service is deployed and how it is discovered, because there needs to be a [service registry](http://microservices.io/patterns/service-registry.html).</span></span> <span data-ttu-id="ed999-111">同様に、コンピューターで障害が発生した場合、レジストリ サービスは、サービスが現在実行されている場所を示すことができなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ed999-111">In the same vein, when a computer fails, the registry service must be able to indicate where the service is now running.</span></span>

<span data-ttu-id="ed999-112">[サービス レジストリ パターン](http://microservices.io/patterns/service-registry.html)は、サービス検出の重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="ed999-112">The [service registry pattern](http://microservices.io/patterns/service-registry.html) is a key part of service discovery.</span></span> <span data-ttu-id="ed999-113">レジストリは、サービス インスタンスのネットワークの場所を含むデータベースです。</span><span class="sxs-lookup"><span data-stu-id="ed999-113">The registry is a database containing the network locations of service instances.</span></span> <span data-ttu-id="ed999-114">サービス レジストリは、可用性が高く、最新の状態である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed999-114">A service registry needs to be highly available and up to date.</span></span> <span data-ttu-id="ed999-115">クライアントは、サービス レジストリから取得したネットワークの場所をキャッシュすることが可能です。</span><span class="sxs-lookup"><span data-stu-id="ed999-115">Clients could cache network locations obtained from the service registry.</span></span> <span data-ttu-id="ed999-116">ただし、その情報は最終的には期限切れになり、クライアントはサービス インスタンスを検出できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ed999-116">However, that information eventually goes out of date and clients can no longer discover service instances.</span></span> <span data-ttu-id="ed999-117">したがって、サービス レジストリは、レプリケーション プロトコルを使用して整合性を維持するサーバーのクラスターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="ed999-117">Consequently, a service registry consists of a cluster of servers that use a replication protocol to maintain consistency.</span></span>

<span data-ttu-id="ed999-118">一部のマイクロサービスの展開環境 (クラスターと呼ばれ、後のセクションで説明します) には、サービス検出が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="ed999-118">In some microservice deployment environments (called clusters, to be covered in a later section), service discovery is built-in.</span></span> <span data-ttu-id="ed999-119">たとえば、Azure Container Service 環境において、Kubernetes や、Marathon を使用した DC/OS では、サービスのインスタンスの登録と登録解除を処理できます。</span><span class="sxs-lookup"><span data-stu-id="ed999-119">For example, within an Azure Container Service environment, Kubernetes and DC/OS with Marathon can handle service instance registration and deregistration.</span></span> <span data-ttu-id="ed999-120">これらはまた、サーバー側の検出ルーターの役割を果たす各クラスター ホスト上でプロキシを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed999-120">They also run a proxy on each cluster host that plays the role of server-side discovery router.</span></span> <span data-ttu-id="ed999-121">別の例として Azure Service Fabric が挙げられます。これもまた、すぐに使用できる Naming Service を介してサービス レジストリを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed999-121">Another example is Azure Service Fabric, which also provides a service registry through its out-of-the-box Naming Service.</span></span>

<span data-ttu-id="ed999-122">サービス レジストリと API ゲートウェイ パターンとの間には特定のオーバーラップがあり、この問題の解決にも役立っています。</span><span class="sxs-lookup"><span data-stu-id="ed999-122">Note that there is certain overlap between the service registry and the API gateway pattern, which helps solve this problem as well.</span></span> <span data-ttu-id="ed999-123">たとえば、[Service Fabric のリバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)は、Service Fabric の Naming Service に基づく API ゲートウェイの実装の種類であり、内部サービスへのアドレスの解決を解決するのに役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="ed999-123">For example, the [Service Fabric Reverse Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) is a type of implementation of an API Gateway that is based on the Service Fabrice Naming Service and that helps resolve address resolution to the internal services.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ed999-124">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="ed999-124">Additional resources</span></span>

-   <span data-ttu-id="ed999-125">**Chris Richardson。パターン: サービス レジストリ**
    *http://microservices.io/patterns/service-registry.html*</span><span class="sxs-lookup"><span data-stu-id="ed999-125">**Chris Richardson. Pattern: Service registry**
*http://microservices.io/patterns/service-registry.html*</span></span>

-   <span data-ttu-id="ed999-126">**Auth0。サービス レジストリ**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span><span class="sxs-lookup"><span data-stu-id="ed999-126">**Auth0. The Service Registry**
[*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)</span></span>

-   <span data-ttu-id="ed999-127">**Gabriel Schenker。サービスの検出**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span><span class="sxs-lookup"><span data-stu-id="ed999-127">**Gabriel Schenker. Service discovery**
[*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ed999-128">[Previous] (maintain-microservice-apis.md) [Next] (microservice-based-composite-ui-shape-layout.md)</span><span class="sxs-lookup"><span data-stu-id="ed999-128">[Previous] (maintain-microservice-apis.md) [Next] (microservice-based-composite-ui-shape-layout.md)</span></span>
