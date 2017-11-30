---
title: "部分的な障害を処理"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |部分的な障害を処理"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7d16acf3de2d395da70e8f46e59c129dec24f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="handling-partial-failure"></a><span data-ttu-id="5c64a-104">部分的な障害を処理</span><span class="sxs-lookup"><span data-stu-id="5c64a-104">Handling partial failure</span></span>

<span data-ttu-id="5c64a-105">Microservices ベースのアプリケーションのような分散システムでは、一部の障害のリスクがないです。</span><span class="sxs-lookup"><span data-stu-id="5c64a-105">In distributed systems like microservices-based applications, there is an ever-present risk of partial failure.</span></span> <span data-ttu-id="5c64a-106">たとえば、単一のマイクロ サービス/コンテナーが失敗する可能性、短い時間で応答できない可能性があります。 または 1 つの VM またはサーバーがクラッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c64a-106">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="5c64a-107">クライアントとサービスは別のプロセスであるため、サービスできないことがあります、クライアントの要求に迅速に応答します。</span><span class="sxs-lookup"><span data-stu-id="5c64a-107">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client’s request.</span></span> <span data-ttu-id="5c64a-108">サービスは、オーバー ロードされた、非常に遅いに応答しての要求があるか、単にアクセスできない可能性が短時間ネットワークの問題によりください。</span><span class="sxs-lookup"><span data-stu-id="5c64a-108">The service might be overloaded and responding extremely slowly to requests, or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="5c64a-109">たとえば、注文の詳細ページ、eShopOnContainers からをサンプル アプリケーションについて考えます。</span><span class="sxs-lookup"><span data-stu-id="5c64a-109">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="5c64a-110">順序マイクロ サービスが応答しない場合、ユーザーしようとすると、クライアント プロセス (MVC web アプリケーション) の実装が不適切な注文を送信 — たとえば、クライアント コードがタイムアウトなしで同期 Rpc を使用する場合: スレッドが無期限にブロック応答を待機しています。</span><span class="sxs-lookup"><span data-stu-id="5c64a-110">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="5c64a-111">不正なユーザー エクスペリエンスを作成するだけでなくすべての応答待機消費スレッドをブロックやスレッドは、拡張性の高いアプリケーションで非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-111">In addition to creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="5c64a-112">ブロックされたスレッドの数がある場合は最終的に、アプリケーションのランタイムがスレッドが枯渇実行できます。</span><span class="sxs-lookup"><span data-stu-id="5c64a-112">If there are many blocked threads, eventually the application’s runtime can run out of threads.</span></span> <span data-ttu-id="5c64a-113">アプリケーションの代わりにグローバルに応答しなくなることができる場合、のみ部分的に応答しない場合、図 10-1 に示されているようにします。</span><span class="sxs-lookup"><span data-stu-id="5c64a-113">In that case, the application can become globally unresponsive instead of just partially unresponsive, as show in Figure 10-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="5c64a-114">**図 10-1**です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-114">**Figure 10-1**.</span></span> <span data-ttu-id="5c64a-115">依存サービスのスレッドの可用性に影響を与えることがあるため、部分的な障害</span><span class="sxs-lookup"><span data-stu-id="5c64a-115">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="5c64a-116">大きな microservices ベースのアプリケーションで任意の部分的な失敗できます増幅される、内部 microservices 相互作用のほとんどは、同期の HTTP 呼び出し (これは、アンチ パターンと見なされます) に基づいている場合に特にです。</span><span class="sxs-lookup"><span data-stu-id="5c64a-116">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="5c64a-117">数百万の 1 日あたりの受信呼び出しを受信するシステムについて検討します。</span><span class="sxs-lookup"><span data-stu-id="5c64a-117">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="5c64a-118">システムに不適切なデザイン同期の HTTP 呼び出しの長いチェーンに基づいている場合、これらの着信呼び出し可能性があります (たとえば 1:4 の比率) の送信呼び出しの多くの詳細数百万に多数の内部 microservices へ同期の依存関係として。</span><span class="sxs-lookup"><span data-stu-id="5c64a-118">If your system has a bad design that is based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let’s suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="5c64a-119">このような状況は、図 10-2 に示す、特に依存関係\#3 です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-119">This situation is shown in Figure 10-2, especially dependency \#3.</span></span>

![](./media/image2.png)

<span data-ttu-id="5c64a-120">**図 10-2**です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-120">**Figure 10-2**.</span></span> <span data-ttu-id="5c64a-121">HTTP 要求の長いチェーンを特徴と、正しくないデザインを持つの影響</span><span class="sxs-lookup"><span data-stu-id="5c64a-121">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="5c64a-122">断続的なエラーが実質的には、分散の保証し、クラウド ベースのシステムのすべての依存関係自体に優れた可用性がある場合でもです。</span><span class="sxs-lookup"><span data-stu-id="5c64a-122">Intermittent failure is virtually guaranteed in a distributed and cloud based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="5c64a-123">ファクトについて考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c64a-123">This should be a fact you need to consider.</span></span>

<span data-ttu-id="5c64a-124">設計しないでフォールト トレランスを確保する手法を実装して場合に、小さなダウンタイムが増幅されることができます。</span><span class="sxs-lookup"><span data-stu-id="5c64a-124">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="5c64a-125">例として、50 依存関係の各可用性 99.99% になります、数時間のダウンタイムは毎月のためこの波及効果。</span><span class="sxs-lookup"><span data-stu-id="5c64a-125">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="5c64a-126">マイクロ サービスの依存関係は、大量の要求の処理中に失敗した場合、そのエラーことができます迅速に各サービス内のすべての使用可能な要求スレッドが飽和状態し、全体のアプリケーションがクラッシュします。</span><span class="sxs-lookup"><span data-stu-id="5c64a-126">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![](./media/image3.png)

<span data-ttu-id="5c64a-127">**図 10-3**です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-127">**Figure 10-3**.</span></span> <span data-ttu-id="5c64a-128">同期の HTTP 呼び出しの長いチェーンを microservices 増幅の部分的な失敗</span><span class="sxs-lookup"><span data-stu-id="5c64a-128">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="5c64a-129">セクションで、この問題を最小限に抑える"*非同期マイクロ サービスの統合がマイクロ サービスの自律性を強制*"(アーキテクチャの章で)、おことをお勧めする内部の間での非同期通信を使用するにはmicroservices です。</span><span class="sxs-lookup"><span data-stu-id="5c64a-129">To minimize this problem, in the section "*Asynchronous microservice integration enforce microservice’s autonomy*” (in the architecture chapter), we encouraged you to use asynchronous communication across the internal microservices.</span></span> <span data-ttu-id="5c64a-130">簡単に説明より次のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="5c64a-130">We briefly explain more in the next section.</span></span>

<span data-ttu-id="5c64a-131">さらは、部分的な障害を処理するアプリケーションの microservices とクライアント アプリケーションを設計することが不可欠-は、回復力のある microservices とクライアント アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="5c64a-131">In addition, it is essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5c64a-132">[前](index.md) [次へ] (部分的な障害 strategies.md)</span><span class="sxs-lookup"><span data-stu-id="5c64a-132">[Previous] (index.md) [Next] (partial-failure-strategies.md)</span></span>
