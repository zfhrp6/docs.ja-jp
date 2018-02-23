---
title: "部分的なエラーの処理"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 部分的なエラーの処理"
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
ms.openlocfilehash: 0b03a5d341dbaadde302692ed0ed236ff3423e63
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="handling-partial-failure"></a><span data-ttu-id="8e606-104">部分的なエラーの処理</span><span class="sxs-lookup"><span data-stu-id="8e606-104">Handling partial failure</span></span>

<span data-ttu-id="8e606-105">マイクロサービスベースのアプリケーションのような分散システムでは、部分的なエラーが発生するリスクが常にあります。</span><span class="sxs-lookup"><span data-stu-id="8e606-105">In distributed systems like microservices-based applications, there is an ever-present risk of partial failure.</span></span> <span data-ttu-id="8e606-106">たとえば、単一のマイクロサービス/コンテナーでエラーが発生する場合、短時間応答できない場合、単一の VM またはサーバーがクラッシュする場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-106">For instance, a single microservice/container can fail or might not be available to respond for a short time, or a single VM or server can crash.</span></span> <span data-ttu-id="8e606-107">クライアントとサービスは別のプロセスなので、サービスがクライアントの要求に迅速に応答できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="8e606-107">Since clients and services are separate processes, a service might not be able to respond in a timely way to a client’s request.</span></span> <span data-ttu-id="8e606-108">サービスが過負荷になり、要求への応答が過度に遅くなる場合や、ネットワークの問題のために短時間アクセスできなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-108">The service might be overloaded and responding extremely slowly to requests, or might simply not be accessible for a short time because of network issues.</span></span>

<span data-ttu-id="8e606-109">eShopOnContainers サンプル アプリケーションの [Order details]\(注文の詳細\) ページを例にして考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="8e606-109">For example, consider the Order details page from the eShopOnContainers sample application.</span></span> <span data-ttu-id="8e606-110">ユーザーが発注しようとしたときに発注マイクロサービスが応答しない場合、クライアント プロセスの不適切な実装 (MVC Web アプリケーション) では、たとえばクライアント コードがタイムアウトのない同期 RPC を使用する場合などに、応答を無期限に待機するスレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="8e606-110">If the ordering microservice is unresponsive when the user tries to submit an order, a bad implementation of the client process (the MVC web application)—for example, if the client code were to use synchronous RPCs with no timeout—would block threads indefinitely waiting for a response.</span></span> <span data-ttu-id="8e606-111">不適切なユーザー エクスペリエンスが作り出されるだけでなく、応答しない待機が発生するたびにスレッドが消費またはブロックされます。また、スケーラブルなアプリケーションでは、スレッドは非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="8e606-111">In addition to creating a bad user experience, every unresponsive wait consumes or blocks a thread, and threads are extremely valuable in highly scalable applications.</span></span> <span data-ttu-id="8e606-112">ブロックされたスレッドが多数発生すると、最終的にはアプリケーションの実行時にスレッドが不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-112">If there are many blocked threads, eventually the application’s runtime can run out of threads.</span></span> <span data-ttu-id="8e606-113">その場合、図 10-1 に示すように、アプリケーションは部分的に応答しなくなるのではなく、全体的に応答しなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-113">In that case, the application can become globally unresponsive instead of just partially unresponsive, as show in Figure 10-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="8e606-114">**図 10-1**</span><span class="sxs-lookup"><span data-stu-id="8e606-114">**Figure 10-1**.</span></span> <span data-ttu-id="8e606-115">サービス スレッドの可用性に影響する依存関係が原因の部分的なエラー</span><span class="sxs-lookup"><span data-stu-id="8e606-115">Partial failures because of dependencies that impact service thread availability</span></span>

<span data-ttu-id="8e606-116">大規模なマイクロサービスベースのアプリケーションでは、部分的なエラーが拡大する可能性があります。特に、内部マイクロサービスの相互作用のほとんどが同期 HTTP 呼び出し (アンチパターンと見なされます) に基づいている場合は拡大する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-116">In a large microservices-based application, any partial failure can be amplified, especially if most of the internal microservices interaction is based on synchronous HTTP calls (which is considered an anti-pattern).</span></span> <span data-ttu-id="8e606-117">1 日あたり何百万もの着信を受け取るシステムについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="8e606-117">Think about a system that receives millions of incoming calls per day.</span></span> <span data-ttu-id="8e606-118">同期 HTTP 呼び出しの長いチェーンに基づいているような不適切な設計のシステムの場合、このような着信の結果、同期の依存関係として数百万の発信が数十の内部マイクロサービスに対して行われる可能性があります (たとえば、1:4 の比率としましょう)。</span><span class="sxs-lookup"><span data-stu-id="8e606-118">If your system has a bad design that is based on long chains of synchronous HTTP calls, these incoming calls might result in many more millions of outgoing calls (let’s suppose a ratio of 1:4) to dozens of internal microservices as synchronous dependencies.</span></span> <span data-ttu-id="8e606-119">この状況を図 10-2 (特に依存関係 \#3) に示します。</span><span class="sxs-lookup"><span data-stu-id="8e606-119">This situation is shown in Figure 10-2, especially dependency \#3.</span></span>

![](./media/image2.png)

<span data-ttu-id="8e606-120">**図 10-2**</span><span class="sxs-lookup"><span data-stu-id="8e606-120">**Figure 10-2**.</span></span> <span data-ttu-id="8e606-121">HTTP 要求の長いチェーンが特徴の不適切な設計の影響</span><span class="sxs-lookup"><span data-stu-id="8e606-121">The impact of having an incorrect design featuring long chains of HTTP requests</span></span>

<span data-ttu-id="8e606-122">分散型のクラウド ベースのシステムでは、すべての依存関係自体に優れた可用性がある場合でも、事実上、断続的なエラーは必ず発生します。</span><span class="sxs-lookup"><span data-stu-id="8e606-122">Intermittent failure is virtually guaranteed in a distributed and cloud based system, even if every dependency itself has excellent availability.</span></span> <span data-ttu-id="8e606-123">この点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-123">This should be a fact you need to consider.</span></span>

<span data-ttu-id="8e606-124">フォールト トレランスを確保するための手法を設計および実装していない場合は、たとえ短時間のダウンタイムであっても増幅する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-124">If you do not design and implement techniques to ensure fault tolerance, even small downtimes can be amplified.</span></span> <span data-ttu-id="8e606-125">たとえば、可用性がそれぞれ 99.99% の依存関係が 50 個ある場合、この波及効果のために毎月数時間のダウンタイムが発生します。</span><span class="sxs-lookup"><span data-stu-id="8e606-125">As an example, 50 dependencies each with 99.99% of availability would result in several hours of downtime each month because of this ripple effect.</span></span> <span data-ttu-id="8e606-126">マイクロサービスの依存関係が大量の要求を処理しているときにエラーが発生すると、そのエラーによって各サービスのすべての使用可能な要求スレッドが短時間で飽和状態になり、アプリケーション全体がクラッシュする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8e606-126">When a microservice dependency fails while handling a high volume of requests, that failure can quickly saturate all available request threads in each service and crash the whole application.</span></span>

![](./media/image3.png)

<span data-ttu-id="8e606-127">**図 10-3**</span><span class="sxs-lookup"><span data-stu-id="8e606-127">**Figure 10-3**.</span></span> <span data-ttu-id="8e606-128">同期 HTTP 呼び出しの長いチェーンがあるマイクロサービスによって増幅される部分的なエラー</span><span class="sxs-lookup"><span data-stu-id="8e606-128">Partial failure amplified by microservices with long chains of synchronous HTTP calls</span></span>

<span data-ttu-id="8e606-129">この問題を最小限に抑えるために、「*マイクロ サービスの自律性を強制する非同期マイクロ サービスの統合*」(アーキテクチャの章) セクションでは、内部のマイクロサービス全体で非同期通信を使用することをお勧めしました。</span><span class="sxs-lookup"><span data-stu-id="8e606-129">To minimize this problem, in the section "*Asynchronous microservice integration enforce microservice’s autonomy*” (in the architecture chapter), we encouraged you to use asynchronous communication across the internal microservices.</span></span> <span data-ttu-id="8e606-130">次のセクションで簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="8e606-130">We briefly explain more in the next section.</span></span>

<span data-ttu-id="8e606-131">さらに、部分的なエラーを処理する (つまり、回復力のあるマイクロサービスとクライアント アプリケーションを構築する) ようにマイクロサービスとクライアント アプリケーションを設計することが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="8e606-131">In addition, it is essential that you design your microservices and client applications to handle partial failures—that is, to build resilient microservices and client applications.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8e606-132">[Previous] (index.md) [Next] (partial-failure-strategies.md)</span><span class="sxs-lookup"><span data-stu-id="8e606-132">[Previous] (index.md) [Next] (partial-failure-strategies.md)</span></span>
