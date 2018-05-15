---
title: 回復力のあるサービス、クラウドの準備ができてをビルドします。 クラウド内の一時的な障害を受け入れる
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |回復力のあるサービス、クラウドの準備ができてをビルドします。 クラウド内の一時的な障害を受け入れる
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 1df21d0f647b96c315686921276be3526f66bbc8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a><span data-ttu-id="84639-105">クラウドの準備が整って回復力のあるサービスを構築しますクラウド内の一時的な障害を受け入れる。</span><span class="sxs-lookup"><span data-stu-id="84639-105">Build resilient services ready for the cloud: Embrace transient failures in the cloud</span></span>

<span data-ttu-id="84639-106">回復性は、障害から回復し、引き続き機能する能力です。</span><span class="sxs-lookup"><span data-stu-id="84639-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="84639-107">回復性エラーを回避するが、エラーが発生するという事実を受信し、ダウンタイムやデータの損失を回避するように後で対応するのではありません。</span><span class="sxs-lookup"><span data-stu-id="84639-107">Resiliency is not about avoiding failures, but accepting the fact that failures will occur, and then responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="84639-108">回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。</span><span class="sxs-lookup"><span data-stu-id="84639-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="84639-109">アプリケーションには、少なくともは、ハードウェア ベースのモデルではなく、回復性のソフトウェア ベースのモデルに実装すると、クラウドの準備ができてです。</span><span class="sxs-lookup"><span data-stu-id="84639-109">Your application is ready for the cloud when, at a minimum, it implements a software-based model of resiliency, rather than a hardware-based model.</span></span> <span data-ttu-id="84639-110">クラウド アプリケーションには、確実に発生する部分的な障害を採用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84639-110">Your cloud application must embrace the partial failures that will certainly occur.</span></span> <span data-ttu-id="84639-111">デザインまたは部分的に予想される部分的な障害回復性を実現するために、アプリケーションをリファクターします。</span><span class="sxs-lookup"><span data-stu-id="84639-111">Design or partially refactor your application to achieve resiliency with expected partial failures.</span></span> <span data-ttu-id="84639-112">これは、一時的なネットワークの停止とノード、または Vm クラウドでクラッシュしたのと同様に、部分的な障害に対処を設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84639-112">It should be designed to cope with partial failures, like transient network outages and nodes, or VMs crashing in the cloud.</span></span> <span data-ttu-id="84639-113">Orchestrator クラスター内の別のノードに移動するものコンテナーには、アプリケーション内での断続的な短いエラー可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84639-113">Even containers being moved to a different node within an orchestrator cluster can cause intermittent short failures within the application.</span></span>

## <a name="handling-partial-failure"></a><span data-ttu-id="84639-114">部分的なエラーの処理</span><span class="sxs-lookup"><span data-stu-id="84639-114">Handling partial failure</span></span>

<span data-ttu-id="84639-115">クラウド ベースのアプリケーションでは、一部の障害のリスクがないです。</span><span class="sxs-lookup"><span data-stu-id="84639-115">In a cloud-based application, there's an ever-present risk of partial failure.</span></span> <span data-ttu-id="84639-116">たとえば、1 つの web サイト インスタンスまたはコンテナーが失敗すると、または使用できなくなったり、短い時間があります。</span><span class="sxs-lookup"><span data-stu-id="84639-116">For instance, a single website instance or a container might fail, or it might be unavailable or unresponsive for a short time.</span></span> <span data-ttu-id="84639-117">または、1 つの VM またはサーバーがクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84639-117">Or, a single VM or server might crash.</span></span>

<span data-ttu-id="84639-118">クライアントとサービスは別のプロセスであるためサービスできないことがあります、クライアントの要求に適切なタイミングで応答します。</span><span class="sxs-lookup"><span data-stu-id="84639-118">Because clients and services are separate processes, a service might not be able to respond in a timely manner to a client's request.</span></span> <span data-ttu-id="84639-119">サービス可能性オーバー ロードがあり、要求に応答が遅くなるまたはにアクセスできない可能性が短時間ネットワークの問題があるためです。</span><span class="sxs-lookup"><span data-stu-id="84639-119">The service might be overloaded and respond slowly to requests, or it might not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="84639-120">たとえば、Azure SQL データベースでデータベースにアクセスするモノリシックな .NET アプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="84639-120">For example, consider a monolithic .NET application that accesses a database in Azure SQL Database.</span></span> <span data-ttu-id="84639-121">Azure SQL データベースやその他のサード パーティのサービスは、簡単な場合に、応答がない場合 (Azure SQL データベースは、別のノードやサーバーに移動される可能性し、数秒応答していない) に、ユーザーは、操作を行う際に、アプリケーションがクラッシュする可能性がありますと表示w 同時例外。</span><span class="sxs-lookup"><span data-stu-id="84639-121">If the Azure SQL database or any other third-party service is unresponsive for a brief time (an Azure SQL database might be moved to a different node or server, and be unresponsive for a few seconds), when the user tries to do any action, the application might crash and show an exception at the same moment.</span></span>

<span data-ttu-id="84639-122">同様のシナリオは、HTTP サービスを使用するアプリで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="84639-122">A similar scenario might occur in an app that consumes HTTP services.</span></span> <span data-ttu-id="84639-123">ネットワークまたはサービス自体できない可能性があります、クラウドで短い、一時的なエラーの際にします。</span><span class="sxs-lookup"><span data-stu-id="84639-123">The network or the service itself might not be available in the cloud during a short, transient failure.</span></span>

<span data-ttu-id="84639-124">図 4-9 に示すような回復力のあるアプリケーションでは、アプリケーション リソースの一時的なエラーを処理する機会を提供する「指数バックオフによる再試行」のような技法を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84639-124">A resilient application like the one shown in Figure 4-9 should implement techniques like "retries with exponential backoff" to give the application an opportunity to handle transient failures in resources.</span></span> <span data-ttu-id="84639-125">また、「ブレーカー」をアプリケーションで使用することも必要があります。</span><span class="sxs-lookup"><span data-stu-id="84639-125">You also should use "circuit breakers" in your applications.</span></span> <span data-ttu-id="84639-126">遮断器は、実際には長期的な障害があるときにリソースにアクセスしようとしてからアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="84639-126">A circuit breaker stops an application from trying to access a resource when it's actually a long-term failure.</span></span> <span data-ttu-id="84639-127">遮断器を使用すると、アプリケーションでは、それ自体にサービス拒否攻撃に富んだで回避できます。</span><span class="sxs-lookup"><span data-stu-id="84639-127">By using a circuit breaker, the application avoids provoking a denial of service to itself.</span></span>

![指数バックオフによる再試行によって処理される部分的な障害](./media/image9.png)

> <span data-ttu-id="84639-129">**図 4-9 です。**</span><span class="sxs-lookup"><span data-stu-id="84639-129">**Figure 4-9.**</span></span> <span data-ttu-id="84639-130">指数バックオフによる再試行によって処理される部分的な障害</span><span class="sxs-lookup"><span data-stu-id="84639-130">Partial failures handled by retries with exponential backoff</span></span>

<span data-ttu-id="84639-131">HTTP リソースとデータベース リソースの両方には、これらの手法を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="84639-131">You can use these techniques both in HTTP resources and in database resources.</span></span> <span data-ttu-id="84639-132">図 4-9 では、アプリケーションに基づきます 3 層アーキテクチャでは、これらの手法は、サービス レベル (HTTP) と、データ層のレベル (TCP) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="84639-132">In Figure 4-9, the application is based on a 3-tier architecture, so you need these techniques at the services level (HTTP) and at the data tier level (TCP).</span></span> <span data-ttu-id="84639-133">(その他のサービスまたは microservices) は、データベース以外の単一のアプリケーション層のみを使用しているモノリシックなアプリケーション、データベース レベルの接続の一時的なエラー処理があるのに十分な。</span><span class="sxs-lookup"><span data-stu-id="84639-133">In a monolithic application that uses only a single app tier in addition to the database (no additional services or microservices), handling transient failures at the database connection level might be enough.</span></span> <span data-ttu-id="84639-134">このシナリオでは、特定のデータベース接続の構成のみが必要です。</span><span class="sxs-lookup"><span data-stu-id="84639-134">In that scenario, just a particular configuration of the database connection is required.</span></span>

<span data-ttu-id="84639-135">を使用している .NET のバージョンによっては、データベースにアクセスする回復力のある通信を実装するときに簡単なできます (たとえば、 [Entity Framework 6 以降](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)、構成するだけで済みますが、データベース接続の場合)。</span><span class="sxs-lookup"><span data-stu-id="84639-135">When implementing resilient communications that access the database, depending on the version of .NET you are using, it can be straightforward (for example, [with Entity Framework 6 or later](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), it's just a matter of configuring the database connection).</span></span> <span data-ttu-id="84639-136">またはのような追加のライブラリを使用する必要があります、 [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (以前のバージョンの .NET)、またはでも独自のライブラリを実装します。</span><span class="sxs-lookup"><span data-stu-id="84639-136">Or, you might need to use additional libraries like the [Transient Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (for earlier versions of .NET), or even implement your own library.</span></span>

<span data-ttu-id="84639-137">使用する、.NET の推奨事項は、HTTP 再試行の回数とブレーカーを実装する場合、[ポリー](https://github.com/App-vNext/Polly)ライブラリで、.NET Framework 4.0、.NET Framework 4.5 と .NET Core のサポートが含まれる .NET 標準 1.1 を対象とします。</span><span class="sxs-lookup"><span data-stu-id="84639-137">When implementing HTTP retries and circuit breakers, the recommendation for .NET is to use the [Polly](https://github.com/App-vNext/Polly) library, which targets .NET Framework 4.0, .NET Framework 4.5, and .NET Standard 1.1, which includes .NET Core support.</span></span>

<span data-ttu-id="84639-138">クラウドでの部分的な障害を処理するための戦略を実装する方法については、次の参照を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84639-138">To learn how to implement strategies for handling partial failures in the cloud, see the following references.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="84639-139">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="84639-139">Additional resources</span></span>

-   <span data-ttu-id="84639-140">**部分的な障害に対処する回復力のある通信を実装します。**</span><span class="sxs-lookup"><span data-stu-id="84639-140">**Implementing resilient communication to handle partial failure**</span></span>

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   <span data-ttu-id="84639-141">**Entity Framework 接続回復性と再試行ロジック (バージョン 6 以降)**</span><span class="sxs-lookup"><span data-stu-id="84639-141">**Entity Framework connection resiliency and retry logic (version 6 and later)**</span></span>

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   <span data-ttu-id="84639-142">**Transient Fault Handling Application Block**</span><span class="sxs-lookup"><span data-stu-id="84639-142">**The Transient Fault Handling Application Block**</span></span>

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   <span data-ttu-id="84639-143">**回復力のある HTTP 通信のポリー ライブラリ**</span><span class="sxs-lookup"><span data-stu-id="84639-143">**Polly library for resilient HTTP communication**</span></span>

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
<span data-ttu-id="84639-144">[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[次へ](modernize-your-apps-with-monitoring-and-telemetry.md)</span><span class="sxs-lookup"><span data-stu-id="84639-144">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](modernize-your-apps-with-monitoring-and-telemetry.md)</span></span>
