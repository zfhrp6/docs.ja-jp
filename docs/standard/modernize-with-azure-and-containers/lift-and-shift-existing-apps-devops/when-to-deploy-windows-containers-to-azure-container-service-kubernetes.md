---
title: "Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="03094-103">Azure コンテナー サービス (つまり、Kubernetes) に Windows コンテナーを展開するタイミング</span><span class="sxs-lookup"><span data-stu-id="03094-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="03094-104">Azure のコンテナー サービスは、Azure の特に人気のオープン ソース ツールとテクノロジの構成を最適化します。</span><span class="sxs-lookup"><span data-stu-id="03094-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="03094-105">移植性、コンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="03094-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="03094-106">サイズ、ホストの数と、orchestrator ツールを選択します。</span><span class="sxs-lookup"><span data-stu-id="03094-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="03094-107">Azure のコンテナー サービスは、のインフラストラクチャを処理します。</span><span class="sxs-lookup"><span data-stu-id="03094-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="03094-108">既にしているオープン ソース orchestrators Kubernetes、Docker Swarm、DC/OS など場合、は、コンテナー ワークロードをクラウドに移動する、既存の管理方法を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="03094-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="03094-109">既にに精通して任意の orchestrator の標準 API エンドポイントを介して接続する、アプリケーションの管理ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="03094-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="03094-110">これらすべての orchestrators は、使用する場合があっての Linux Docker コンテナーもサポート Windows コンテナー 2017 (前、最近では、orchestrator によって異なります) のように完成度の高い環境が。</span><span class="sxs-lookup"><span data-stu-id="03094-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="03094-111">たとえば、Kubernetes でのサポートのコンテナーは Kubernetes で Windows コンテナーを使用してネイティブ (ファーストクラス市民) では非常に効率的かつ信頼性の高いも (までプレビュー早期分類 2017)。</span><span class="sxs-lookup"><span data-stu-id="03094-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="03094-112">[前へ](when-to-deploy-windows-containers-to-service-fabric.md)
[次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="03094-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
