---
title: 回復性の高いアプリケーションの実装
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 回復性の高いアプリケーションの実装'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 211814eff0f2aaf0cf71a19cfcaaeb44924fb6f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-resilient-applications"></a><span data-ttu-id="915ea-103">回復性の高いアプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="915ea-103">Implementing Resilient Applications</span></span>

<span data-ttu-id="915ea-104">*マイクロサービスおよびクラウド ベースのアプリケーションは、最終的に確実に発生する部分的な障害を受け入れる必要があります。そのような部分的な障害に対する回復性があるようにアプリケーションを設計する必要があります。*</span><span class="sxs-lookup"><span data-stu-id="915ea-104">*Your microservice and cloud based applications must embrace the partial failures that will certainly occur eventually. You need to design your application so it will be resilient to those partial failures.*</span></span>

<span data-ttu-id="915ea-105">回復性は、障害から回復し、引き続き機能する能力です。</span><span class="sxs-lookup"><span data-stu-id="915ea-105">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="915ea-106">障害を回避することではなく、障害が発生するという事実を受け入れ、ダウンタイムまたはデータの損失を回避するようにそれらに対応することです。</span><span class="sxs-lookup"><span data-stu-id="915ea-106">It is not about avoiding failures, but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="915ea-107">回復性の目的は、障害発生後にアプリケーションを完全に機能する状態に戻すことです。</span><span class="sxs-lookup"><span data-stu-id="915ea-107">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="915ea-108">マイクロサービスベースのアプリケーションの設計および導入は難しい作業です。</span><span class="sxs-lookup"><span data-stu-id="915ea-108">It is challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="915ea-109">しかし、何らかの障害が確実に発生する環境で、アプリケーションの稼働を維持する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="915ea-109">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="915ea-110">そのため、アプリケーションは、回復性を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="915ea-110">Therefore, your application should be resilient.</span></span> <span data-ttu-id="915ea-111">ネットワークの停止、クラウド内のノードまたは VM のクラッシュなどの部分的な障害に対処するように設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="915ea-111">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="915ea-112">クラスタ内でマイクロサービス (コンテナー) を別のノードに移動するだけでも、アプリケーション内での断続的な短いエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="915ea-112">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="915ea-113">アプリケーションの多くの個々のコンポーネントにも、正常性監視機能を組み込むも必要があります。</span><span class="sxs-lookup"><span data-stu-id="915ea-113">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="915ea-114">この章のガイドラインに従うと、複雑で、クラウド ベースの展開で発生する一時的なダウンタイムや定期的な障害があってもスムーズに動作するアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="915ea-114">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="915ea-115">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="915ea-115">[Previous] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [Next] (handle-partial-failure.md)</span></span>
