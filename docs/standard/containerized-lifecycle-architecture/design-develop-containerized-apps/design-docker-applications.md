---
title: Docker のアプリケーションを設計します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 951169a6b7c458872f5c90a8845826b675671101
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="design-docker-applications"></a><span data-ttu-id="762db-103">Docker のアプリケーションを設計します。</span><span class="sxs-lookup"><span data-stu-id="762db-103">Design Docker applications</span></span>

<span data-ttu-id="762db-104">第 1 章には、コンテナーと Docker に関する基本的な概念が導入されました。</span><span class="sxs-lookup"><span data-stu-id="762db-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="762db-105">その情報は、基本的なレベルの作業を開始するに必要な情報です。</span><span class="sxs-lookup"><span data-stu-id="762db-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="762db-106">しかし、エンタープライズ アプリケーションには、1 つのサービスまたはコンテナーではなく複数のサービスで構成され、複雑なを指定できます。</span><span class="sxs-lookup"><span data-stu-id="762db-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="762db-107">これらのオプションで使用する場合、オーケストレーションの概念デザイン、サービス指向アーキテクチャ (SOA) より高度な microservices および概念コンテナーへの追加方法を把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="762db-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="762db-108">このドキュメントの範囲は microservices に限定されませんが、Docker アプリケーションのライフ サイクルをそのため、これは情報を表示しません microservices アーキテクチャの深さでも正規サン、バック グラウンド タスクまたはジョブでコンテナーと Docker を使用したりもあるためモノリシックなアプリケーション展開アプローチです。</span><span class="sxs-lookup"><span data-stu-id="762db-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SAO, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="762db-109">ただし、DevOps とアプリケーションのライフ サイクルに進む前をデザインに移動する方法を理解し、アプリケーションと設計の選択は、新機能を構築する重要な。</span><span class="sxs-lookup"><span data-stu-id="762db-109">However, before we get into the application life cycle and DevOps, it is important to know how you are going to design and construct your application and what are your design choices.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="762db-110">[前] (index.md) [次へ] (共通のコンテナーのデザインの principles.md)</span><span class="sxs-lookup"><span data-stu-id="762db-110">[Previous] (index.md) [Next] (common-container-design-principles.md)</span></span>
