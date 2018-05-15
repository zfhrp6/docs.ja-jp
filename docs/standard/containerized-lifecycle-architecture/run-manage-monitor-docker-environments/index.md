---
title: Docker 実稼働環境の実行、管理、および監視
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 1bd1abccb55fe9f837b024cc0f61eea71d3b64c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="run-manage-and-monitor-docker-production-environments"></a><span data-ttu-id="66e19-103">Docker 実稼働環境の実行、管理、および監視</span><span class="sxs-lookup"><span data-stu-id="66e19-103">Run, manage, and monitor Docker production environments</span></span>

<span data-ttu-id="66e19-104">ビジョン: エンタープライズ アプリケーションは可用性と拡張性が高い状態で実行する必要があります。IT 運用チームは、環境とアプリケーション自体を管理および監視できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="66e19-104">Vision: Enterprise applications need to run with high availability and high scalability; IT operations need to be able to manage and monitor the environments and the applications themselves.</span></span>

<span data-ttu-id="66e19-105">コンテナー化された Docker アプリケーションのライフ サイクルのこの最後の柱の焦点は、拡張性と可用性の高い (HA) 実稼働環境で、アプリケーションをどのように実行、管理、および監視するかです。</span><span class="sxs-lookup"><span data-stu-id="66e19-105">This last pillar in the containerized Docker applications life cycle is centered on how you can run, manage, and monitor your applications in scalable, high availability (HA) production environments.</span></span>

<span data-ttu-id="66e19-106">実稼働環境 (インフラストラクチャ アーキテクチャとプラットフォーム テクノロジ) で、コンテナー化アプリケーションをどのように実行するかは、この電子書籍の第 1 章で確認した、選択したアーキテクチャと開発プラットフォームにも、非常に関連しており、完全に基づいています。</span><span class="sxs-lookup"><span data-stu-id="66e19-106">How you run your containerized applications in production (infrastructure architecture and platform technologies) is also very much related and completely founded on the chosen architecture and development platforms that we looked at in the Chapter 1 of this e-book.</span></span> <span data-ttu-id="66e19-107">この章では、非常に拡張性の高い、HA 分散アプリケーションを効率的に実行するために使用できる、Microsoft および他のベンダーの特定の製品および技術を確認します。それに加え、IT の観点からどのようにそれを管理および監視するか検証します。</span><span class="sxs-lookup"><span data-stu-id="66e19-107">This chapter examines specific products and technologies from Microsoft and other vendors that you can use to effectively run highly scalable, HA distributed applications plus how you can manage and monitor them from the IT perspective.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="66e19-108">[前へ] (../docker-devops-workflow/docker-application-outer-loop-devops-workflow.md) [次へ] (run-microservices-based-applications-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="66e19-108">[Previous] (../docker-devops-workflow/docker-application-outer-loop-devops-workflow.md) [Next] (run-microservices-based-applications-in-production.md)</span></span>
