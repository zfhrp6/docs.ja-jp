---
title: "実稼働環境で構成される microservices ベースのアプリケーションを実行します。"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: e7a2788098aa731699cbb201c7177e7578907673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a><span data-ttu-id="ea079-104">実稼働環境で構成される microservices ベースのアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ea079-104">Run composed and microservices-based applications in production environments</span></span>

<span data-ttu-id="ea079-105">複数 microservices で構成されたアプリケーションは展開の複雑性を容易にし、IT の観点から実行可能なためするために orchestrator クラスターをデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea079-105">Applications composed by multiple microservices do need to be deployed into orchestrator clusters in order to simplify the complexity of deployment and make it viable from an IT point of view.</span></span> <span data-ttu-id="ea079-106">Orchestrator クラスターでは、それができなければを展開およびスケール アウト microservices の複雑なアプリケーションは非常に困難。</span><span class="sxs-lookup"><span data-stu-id="ea079-106">Without an orchestrator cluster, it would be very difficult to deploy and scale-out a complex microservices application.</span></span>

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a><span data-ttu-id="ea079-107">クラスターの orchestrators、スケジューラ、およびコンテナーの概要</span><span class="sxs-lookup"><span data-stu-id="ea079-107">Introduction to orchestrators, schedulers, and container clusters</span></span>

<span data-ttu-id="ea079-108">この電子書籍の前半紹介*クラスター*と*スケジューラ*ソフトウェア アーキテクチャと開発のディスカッションの一部として。</span><span class="sxs-lookup"><span data-stu-id="ea079-108">Earlier in this e-book, we introduced *clusters* and *schedulers* as part of the discussion on software architecture and development.</span></span> <span data-ttu-id="ea079-109">Docker のクラスターには、Docker Swarm と続き Datacenter オペレーティング システム (DC/OS) があります。</span><span class="sxs-lookup"><span data-stu-id="ea079-109">Examples of Docker clusters are Docker Swarm and Mesosphere Datacenter Operating System (DC/OS).</span></span> <span data-ttu-id="ea079-110">Microsoft Azure のコンテナー サービスによって提供されるインフラストラクチャの一部としてこれらの両方を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ea079-110">Both of these can run as a part of the infrastructure provided by Microsoft Azure Container Service.</span></span>

<span data-ttu-id="ea079-111">アプリケーションはスケール アウトされた複数のホスト システムで、ときに各ホスト システムを管理し、基になるプラットフォームの複雑さを抽象化する機能は魅力的なになります。</span><span class="sxs-lookup"><span data-stu-id="ea079-111">When applications are scaled-out across multiple host systems, the ability to manage each host system and abstract away the complexity of the underlying platform becomes attractive.</span></span> <span data-ttu-id="ea079-112">Orchestrators およびスケジューラが提供するものは正確です。</span><span class="sxs-lookup"><span data-stu-id="ea079-112">That is precisely what orchestrators and schedulers provide.</span></span> <span data-ttu-id="ea079-113">ここで見て簡単なを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="ea079-113">Let's take a brief look at them here:</span></span>

-   <span data-ttu-id="ea079-114">**スケジューラ*** *「スケジュール」とは、特定のコンテナーを実行する方法を規定するホスト システムにサービス ファイルの読み込みに管理者の能力です。</span><span class="sxs-lookup"><span data-stu-id="ea079-114">**Schedulers*** *"Scheduling" refers to the ability for an administrator to load a service file onto a host system that establishes how to run a specific container.</span></span> <span data-ttu-id="ea079-115">Docker クラスター内のコンテナーの起動は、スケジュール設定と呼ばれる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="ea079-115">Launching containers in a Docker cluster tends to be known as scheduling.</span></span> <span data-ttu-id="ea079-116">一般的な意味で、サービス定義の読み込みの特定の動作を指しますスケジュールがスケジューラは必要なすべての容量にサービスを管理するホストの init システムにフックをします。</span><span class="sxs-lookup"><span data-stu-id="ea079-116">Although scheduling refers to the specific act of loading the service definition, in a more general sense, schedulers are responsible for hooking into a host's init system to manage services in whatever capacity needed.</span></span>

<span data-ttu-id="ea079-117">クラスター スケジューラは、複数の目標: クラスターのリソースを効率的に使用して、ユーザーが指定した配置制約、スケジューリング「公平性を」エラーに堅牢な中の程度を持つ、すぐに保留状態のままにしないアプリケーションの使用と常に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea079-117">A cluster scheduler has multiple goals: using the cluster's resources efficiently, working with user-supplied placement constraints, scheduling applications rapidly to not leave them in a pending state, having a degree of "fairness," being robust to errors, and always be available.</span></span>

-   <span data-ttu-id="ea079-118">**オーケストレーション*** *プラットフォームが multicontainer、複雑なワークロードをホストのクラスターに展開されているライフ サイクル管理機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="ea079-118">**Orchestration*** *Platforms extend life-cycle management capabilities to complex, multicontainer workloads deployed on a cluster of hosts.</span></span> <span data-ttu-id="ea079-119">ホスト インフラストラクチャを抽象化して、によってオーケストレーション ツールは、1 つの配置ターゲットとしてクラスター全体を処理する方法のユーザーを付けます。</span><span class="sxs-lookup"><span data-stu-id="ea079-119">By abstracting the host infrastructure, orchestration tools give users a way to treat the entire cluster as a single deployment target.</span></span>

<span data-ttu-id="ea079-120">オーケストレーションの処理には、ツールと初期配置またはコンテナー; ごとの配置からのアプリケーション管理のすべての側面を自動化できるプラットフォームが含まれます。コンテナーをそのホストの正常性アドインまたはパフォーマンス; に応じて異なるホストに移動バージョン管理とローリング更新プログラムおよび正常性のスケーリングと; のフェールオーバーをサポートする関数の監視さらに多くします。</span><span class="sxs-lookup"><span data-stu-id="ea079-120">The process of orchestration involves tooling and a platform that can automate all aspects of application management from initial placement or deployment per container; moving containers to different hosts depending on its host's health or performance; versioning and rolling updates and health monitoring functions that support scaling and failover; and many more.</span></span>

<span data-ttu-id="ea079-121">オーケストレーションは、コンテナーのスケジュール設定、クラスター管理、および他のホストのプロビジョニング可能性のあるを参照する広範な用語です。</span><span class="sxs-lookup"><span data-stu-id="ea079-121">Orchestration is a broad term that refers to container scheduling, cluster management, and possibly the provisioning of additional hosts.</span></span>

<span data-ttu-id="ea079-122">Orchestrators およびスケジューラによって提供される機能は、開発し、最初から作成する非常に複雑なしたがって通常はようにするベンダーにより提供されるオーケストレーション ソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea079-122">The capabilities provided by orchestrators and schedulers are very complex to develop and create from scratch, and therefore you usually would want to make use of orchestration solutions offered by vendors.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ea079-123">[前](index.md) [次へ] (管理、運用の docker-environments.md)</span><span class="sxs-lookup"><span data-stu-id="ea079-123">[Previous] (index.md) [Next] (manage-production-docker-environments.md)</span></span>
