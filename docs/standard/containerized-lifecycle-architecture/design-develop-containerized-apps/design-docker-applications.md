---
title: "Docker のアプリケーションを設計します。"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aeddd3a4b7ebd3c917fba46e048fbab5a77dda19
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="design-docker-applications"></a><span data-ttu-id="17ca8-104">Docker のアプリケーションを設計します。</span><span class="sxs-lookup"><span data-stu-id="17ca8-104">Design Docker applications</span></span>

<span data-ttu-id="17ca8-105">第 1 章には、コンテナーと Docker に関する基本的な概念が導入されました。</span><span class="sxs-lookup"><span data-stu-id="17ca8-105">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="17ca8-106">その情報は、基本的なレベルの作業を開始するに必要な情報です。</span><span class="sxs-lookup"><span data-stu-id="17ca8-106">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="17ca8-107">しかし、エンタープライズ アプリケーションには、1 つのサービスまたはコンテナーではなく複数のサービスで構成され、複雑なを指定できます。</span><span class="sxs-lookup"><span data-stu-id="17ca8-107">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="17ca8-108">これらのオプションで使用する場合、オーケストレーションの概念デザイン、サービス指向アーキテクチャ (SOA) より高度な microservices および概念コンテナーへの追加方法を把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17ca8-108">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="17ca8-109">このドキュメントの範囲は microservices に限定されませんが、Docker アプリケーションのライフ サイクルをそのため、これは情報を表示しません microservices アーキテクチャの深さでも正規サン、バック グラウンド タスクまたはジョブでコンテナーと Docker を使用したりもあるためモノリシックなアプリケーション展開アプローチです。</span><span class="sxs-lookup"><span data-stu-id="17ca8-109">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="17ca8-110">ただし、DevOps とアプリケーションのライフ サイクルに進む前をデザインに移動する方法を理解し、アプリケーションと設計の選択は、新機能を構築する重要な。</span><span class="sxs-lookup"><span data-stu-id="17ca8-110">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="17ca8-111">[前](index.md) [次へ] (共通のコンテナーのデザインの principles.md)</span><span class="sxs-lookup"><span data-stu-id="17ca8-111">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
