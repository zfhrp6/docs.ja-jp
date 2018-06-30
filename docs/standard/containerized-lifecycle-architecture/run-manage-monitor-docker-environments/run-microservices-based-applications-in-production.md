---
title: 実稼働環境で構成される microservices ベースのアプリケーションを実行します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4192ff1d67a3f70bb5eeb9a36245cfd35bafb53
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105632"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="f8bbf-103">実稼働環境で構成される microservices ベースのアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-103">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="f8bbf-104">複数 microservices で構成されたアプリケーションは展開の複雑性を容易にし、IT の観点から実行可能なためするために orchestrator クラスターをデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-104">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="f8bbf-105">Orchestrator クラスターでは、それができなければを展開およびスケール アウト microservices の複雑なアプリケーションは非常に困難。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-105">Without an orchestrator cluster, it would be very difficult to deploy and scale-out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="f8bbf-106">クラスターの orchestrators、スケジューラ、およびコンテナーの概要</span><span class="sxs-lookup"><span data-stu-id="f8bbf-106">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="f8bbf-107">この電子書籍の前半紹介*クラスター*と*スケジューラ*ソフトウェア アーキテクチャと開発のディスカッションの一部として。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-107">Earlier in this e-book, we introduced *clusters* and *schedulers* as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="f8bbf-108">Docker のクラスターには、Docker Swarm と続き Datacenter オペレーティング システム (DC/OS) があります。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-108">Examples of Docker clusters are Docker Swarm and Mesosphere Datacenter Operating System (DC/OS).</span></span> <span data-ttu-id="f8bbf-109">Microsoft Azure のコンテナー サービスによって提供されるインフラストラクチャの一部としてこれらの両方を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-109">Both of these can run as a part of the infrastructure provided by Microsoft Azure Container Service.</span></span>

<span data-ttu-id="f8bbf-110">アプリケーションはスケール アウトされた複数のホスト システムで、ときに各ホスト システムを管理し、基になるプラットフォームの複雑さを抽象化する機能は魅力的なになります。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-110">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="f8bbf-111">Orchestrators およびスケジューラが提供するものは正確です。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-111">That is precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="f8bbf-112">ここで見て簡単なを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-112">Let's take a brief look at them here:</span></span>

-   <span data-ttu-id="f8bbf-113">**スケジューラ * * * *「スケジュール」とは、特定のコンテナーを実行する方法を規定するホスト システムにサービス ファイルの読み込みに管理者の能力です。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-113">**Schedulers*** *"Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="f8bbf-114">Docker クラスター内のコンテナーの起動は、スケジュール設定と呼ばれる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-114">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="f8bbf-115">一般的な意味で、サービス定義の読み込みの特定の動作を指しますスケジュールがスケジューラは必要なすべての容量にサービスを管理するホストの init システムにフックをします。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-115">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

<span data-ttu-id="f8bbf-116">クラスター スケジューラは、複数の目標: クラスターのリソースを効率的に使用して、ユーザーが指定した配置制約、スケジューリング「公平性を」エラーに堅牢な中の程度を持つ、すぐに保留状態のままにしないアプリケーションの使用と常に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-116">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

-   <span data-ttu-id="f8bbf-117">**オーケストレーション * * * *プラットフォームが multicontainer、複雑なワークロードをホストのクラスターに展開されているライフ サイクル管理機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-117">**Orchestration*** *Platforms extend life-cycle management capabilities to complex, multicontainer workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="f8bbf-118">ホスト インフラストラクチャを抽象化して、によってオーケストレーション ツールは、1 つの配置ターゲットとしてクラスター全体を処理する方法のユーザーを付けます。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-118">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

<span data-ttu-id="f8bbf-119">オーケストレーションの処理には、ツールと初期配置またはコンテナー; ごとの配置からのアプリケーション管理のすべての側面を自動化できるプラットフォームが含まれます。コンテナーをそのホストの正常性アドインまたはパフォーマンス; に応じて異なるホストに移動バージョン管理とローリング更新プログラムおよび正常性のスケーリングと; のフェールオーバーをサポートする関数の監視さらに多くします。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-119">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

<span data-ttu-id="f8bbf-120">オーケストレーションは、コンテナーのスケジュール設定、クラスター管理、および他のホストのプロビジョニング可能性のあるを参照する広範な用語です。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-120">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="f8bbf-121">Orchestrators およびスケジューラによって提供される機能は、開発し、最初から作成する非常に複雑なしたがって通常はようにするベンダーにより提供されるオーケストレーション ソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8bbf-121">The capabilities provided by orchestrators and schedulers are very complex to develop and create from scratch, and therefore you usually would want to make use of orchestration solutions offered by vendors.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f8bbf-122">[前へ](index.md)
[次へ](manage-production-docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="f8bbf-122">[Previous](index.md)
[Next](manage-production-docker-environments.md)</span></span>
