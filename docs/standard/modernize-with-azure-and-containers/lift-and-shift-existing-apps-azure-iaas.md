---
title: "リフト アンド シフト Azure IaaS の既存のアプリ"
description: "既存の .NET アプリケーションと Azure のクラウドと Windows コンテナーを開放します。"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eed17ad06c138c3a4eb85f5e023427b681488784
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a><span data-ttu-id="f1271-103">リフト アンド シフト Azure IaaS の既存のアプリ</span><span class="sxs-lookup"><span data-stu-id="f1271-103">Lift and shift existing apps Azure IaaS</span></span>

> <span data-ttu-id="f1271-104">ビジョン: 最初の手順としてをハードウェアの内部設置型への投資と総コストを削減し、クラウド内の既存のアプリケーションを再ホスト ネットワークのメンテナンス、単純にします。</span><span class="sxs-lookup"><span data-stu-id="f1271-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="f1271-105">入る前に*方法*Azure infrastructure as a service (IaaS) プラットフォームを既存のアプリケーションを移行することが理由を分析する重要*理由*IaaS に直接移行します。azure です。</span><span class="sxs-lookup"><span data-stu-id="f1271-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="f1271-106">この近代化成熟度レベルのシナリオでは引き続き、現在、内部設置型インフラストラクチャを使用してではなく、クラウド内の Vm の使用を開始を本質的にします。</span><span class="sxs-lookup"><span data-stu-id="f1271-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="f1271-107">分析に別のポイントが*理由*詳細設定で、Azure 管理サービスを追加するだけではなく純粋な IaaS クラウドへ移行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1271-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="f1271-108">場合がありますかを調べる必要 IaaS を最初の場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="f1271-108">You need to determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="f1271-109">図 2-1 では、クラウド インフラストラクチャの準備完了のアプリケーションを配置近代化成熟度レベルで。</span><span class="sxs-lookup"><span data-stu-id="f1271-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-1.png)

> <span data-ttu-id="f1271-111">**図 2-1。**</span><span class="sxs-lookup"><span data-stu-id="f1271-111">**Figure 2-1.**</span></span> <span data-ttu-id="f1271-112">クラウド インフラストラクチャの準備完了のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="f1271-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="f1271-113">Azure IaaS に既存の .NET web アプリケーションを移行する理由</span><span class="sxs-lookup"><span data-stu-id="f1271-113">Why migrate existing .NET web applications to Azure IaaS</span></span> 

<span data-ttu-id="f1271-114">初期の IaaS レベルでも、クラウドに移行する主な理由は、コストの削減を実現するためにです。</span><span class="sxs-lookup"><span data-stu-id="f1271-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="f1271-115">多くの管理されたインフラストラクチャ サービスを使用すると、組織はハードウェアのメンテナンス、サーバーまたは VM のプロビジョニングし配置、およびインフラストラクチャの管理で、投資収益率を下げることができます。</span><span class="sxs-lookup"><span data-stu-id="f1271-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="f1271-116">アプリをクラウドに移動する意思決定を行うと、選択する理由が IaaS PaaS は単純にするようより高度なオプションではなく、IaaS 環境主な理由は、他の一般的なになります。</span><span class="sxs-lookup"><span data-stu-id="f1271-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="f1271-117">現在次のような環境への移動、オンプレミス環境には、低い習得、これにより、クラウドが最速のパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f1271-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="f1271-118">ただし、クラウドに移行する最も簡単な方法を選ぶわけでは、アプリケーション、クラウドで実行する必要がなくなりますほとんどの利益を得ることがあります。</span><span class="sxs-lookup"><span data-stu-id="f1271-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="f1271-119">任意の組織には、既に導入クラウド DevOps 対応および PaaS (クラウドに最適化された) の成熟度レベルでのクラウド移行から最も重要な利点が獲得できません。</span><span class="sxs-lookup"><span data-stu-id="f1271-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud DevOps-Ready and PaaS (Cloud-Optimized) maturity levels.</span></span>

<span data-ttu-id="f1271-120">これもが明らかになりますアプリケーションが簡単に最新化および再 IaaS 上であっても、クラウドで既に実行されている場合、今後設計います。</span><span class="sxs-lookup"><span data-stu-id="f1271-120">It also has become evident that applications are easier to modernize and re-architect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="f1271-121">部分的にアプリケーション データの移行が実現されて既にため true です。</span><span class="sxs-lookup"><span data-stu-id="f1271-121">This is true in part because application data migration has already been achieved.</span></span> <span data-ttu-id="f1271-122">また、組織が、クラウドでの作業に必要なスキルを獲得しようし、shift キーを押し"クラウド culture"で動作しています。</span><span class="sxs-lookup"><span data-stu-id="f1271-122">Also, your organization will have gained skills required for working in the cloud, and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="f1271-123">代わりに PaaS に IaaS に移行するときに</span><span class="sxs-lookup"><span data-stu-id="f1271-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="f1271-124">次のセクションでは、クラウド DevOps 対応は、ほとんどの場合に基づくアプリケーションの PaaS プラットフォームおよびサービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f1271-124">In the next sections, we discuss Cloud DevOps-Ready applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="f1271-125">これらのアプリによって、クラウドへの移行からほとんどの利点がわかります。</span><span class="sxs-lookup"><span data-stu-id="f1271-125">These apps give you the most benefits from migrating to the cloud.</span></span>

<span data-ttu-id="f1271-126">目標は、既存のアプリケーションをクラウドに移動することだけが場合、は、最初に、Azure App Service で実行するに大幅な変更が必要になる既存のアプリケーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="f1271-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that will require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="f1271-127">これらのアプリは、最初の候補にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1271-127">These apps should be the first candidates.</span></span>

<span data-ttu-id="f1271-128">次に、したくないまたは Azure Service Fabric など Kubernetes orchestrators やと Windows コンテナーに移動できません、まだ、しではプレーンな Vm (IaaS) を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="f1271-128">Then, if you don't want or still cannot move to Windows Containers and or orchestrators like Azure Service Fabric or Kubernetes, yet, then is when you would use plain VMs (IaaS).</span></span>

<span data-ttu-id="f1271-129">しかし、正しく構成、セキュリティ保護、および Vm の維持が必要である多くの時間と azure PaaS サービスを使用する場合に比べて IT 専門知識に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f1271-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="f1271-130">Azure の仮想マシンを検討している場合は、更新プログラム、更新、および VM 環境の管理に必要な継続的な保守作業を考慮するを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1271-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="f1271-131">Azure の仮想マシンは、IaaS です。</span><span class="sxs-lookup"><span data-stu-id="f1271-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="f1271-132">Azure の移行を使用して分析し、既存のアプリケーションを Azure に移行</span><span class="sxs-lookup"><span data-stu-id="f1271-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="f1271-133">クラウドへの移行は、困難であるがありません。</span><span class="sxs-lookup"><span data-stu-id="f1271-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="f1271-134">多くの組織が、環境とアプリケーション、ワークロード、およびデータの間で緊密な依存関係の詳細表示の開始に苦労します。</span><span class="sxs-lookup"><span data-stu-id="f1271-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="f1271-135">その可視性なしは、移行パスを計画するが困難ができます。</span><span class="sxs-lookup"><span data-stu-id="f1271-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="f1271-136">移行の成功のために必要な新機能の詳細な情報がない場合、組織内で右のメッセージ交換ことはできません。</span><span class="sxs-lookup"><span data-stu-id="f1271-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="f1271-137">潜在的なメリットをコストについて十分かわからないまたはかどうかワークロードまたはことがだけリフトと-シフト大幅な修正を正常に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1271-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="f1271-138">当然と多くの組織になる躊躇します。</span><span class="sxs-lookup"><span data-stu-id="f1271-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="f1271-139">[Azure 移行](https://aka.ms/azuremigrate)ガイダンス、insights、および Azure への移行を支援するために必要なメカニズムを提供する新しいサービスは、します。</span><span class="sxs-lookup"><span data-stu-id="f1271-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="f1271-140">Azure の移行を提供します。</span><span class="sxs-lookup"><span data-stu-id="f1271-140">Azure Migrate provides:</span></span>

-   <span data-ttu-id="f1271-141">探索と内部設置型の仮想マシンの評価</span><span class="sxs-lookup"><span data-stu-id="f1271-141">Discovery and assessment for on-premises virtual machines</span></span>

-   <span data-ttu-id="f1271-142">多階層アプリケーションの信頼性の高い検出用の組み込みの依存関係のマッピング</span><span class="sxs-lookup"><span data-stu-id="f1271-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

-   <span data-ttu-id="f1271-143">Azure の仮想マシンをインテリジェント適正</span><span class="sxs-lookup"><span data-stu-id="f1271-143">Intelligent rightsizing to Azure virtual machines</span></span>

-   <span data-ttu-id="f1271-144">潜在的な問題を修復するためのガイドラインとレポートの互換性</span><span class="sxs-lookup"><span data-stu-id="f1271-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

-   <span data-ttu-id="f1271-145">データベースの検出と移行のための Azure Database Management Service との統合</span><span class="sxs-lookup"><span data-stu-id="f1271-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="f1271-146">Azure の移行では、信頼度のワークロードが業務に影響を最小限に移行し、Azure で期待どおりに実行できます。</span><span class="sxs-lookup"><span data-stu-id="f1271-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="f1271-147">適切なツールとガイダンスでは、最大の重要なパフォーマンスを確保しながら投資回収を実現でき、信頼性のニーズを満たしています。</span><span class="sxs-lookup"><span data-stu-id="f1271-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="f1271-148">図 2-2 では、Azure の移行によって実行されるすべてのサーバーとアプリケーションの接続の組み込みの依存関係のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="f1271-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-2.png)

> <span data-ttu-id="f1271-150">**図 2-2 です。**</span><span class="sxs-lookup"><span data-stu-id="f1271-150">**Figure 2-2.**</span></span> <span data-ttu-id="f1271-151">クラウド インフラストラクチャの準備完了のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="f1271-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="f1271-152">Azure Site Recovery を使用して、既存の Vm を Azure Vm に移行するには</span><span class="sxs-lookup"><span data-stu-id="f1271-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="f1271-153">エンド ツー エンドの一部として[Azure 移行](https://aka.ms/azuremigrate)、 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) Azure での Vm に web アプリを簡単に移行に使用できるツールです。</span><span class="sxs-lookup"><span data-stu-id="f1271-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="f1271-154">内部設置型 Vm と物理サーバーを Azure にレプリケートする、またはセカンダリ オンプレミスの場所にこれらをレプリケートするには、Site Recovery を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f1271-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="f1271-155">サポートされている Azure 仮想マシンの場合、内部設置型上で実行されているワークロードをレプリケートすることもできます*HYPER-V* VM の*VMware* VM、または Windows または Linux の物理サーバーにします。</span><span class="sxs-lookup"><span data-stu-id="f1271-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="f1271-156">Azure へのレプリケーションでは、コストとセカンダリ データ センターを維持するための複雑さを排除します。</span><span class="sxs-lookup"><span data-stu-id="f1271-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="f1271-157">サイトの回復が部分的であるハイブリッド環境の具体的には行われたも、内部設置型と一部の Azure です。</span><span class="sxs-lookup"><span data-stu-id="f1271-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="f1271-158">Site Recovery の Vm で実行されているアプリを保持することでビジネス継続性によりと内部設置型で利用できる物理サーバー、サイトがダウンした場合。</span><span class="sxs-lookup"><span data-stu-id="f1271-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="f1271-159">実行されている仮想マシンおよび物理サーバー上で常に利用可能なセカンダリの場所に、プライマリ サイトが利用できない場合のワークロードをレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="f1271-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="f1271-160">これが上向きのとき、プライマリ サイトを再実行してワークロードを回復します。</span><span class="sxs-lookup"><span data-stu-id="f1271-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="f1271-161">図 2-3 では、Azure Site Recovery を使用して、複数の VM の移行の実行を示します。</span><span class="sxs-lookup"><span data-stu-id="f1271-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-3.png)

> <span data-ttu-id="f1271-163">**図 2-3。**</span><span class="sxs-lookup"><span data-stu-id="f1271-163">**Figure 2-3.**</span></span> <span data-ttu-id="f1271-164">クラウド インフラストラクチャの準備完了のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="f1271-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f1271-165">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="f1271-165">Additional resources</span></span>

-   <span data-ttu-id="f1271-166">**Azure 移行データシート**</span><span class="sxs-lookup"><span data-stu-id="f1271-166">**Azure Migrate Datasheet**</span></span>

    [<span data-ttu-id="f1271-167">https://aka.ms/azuremigration\_datasheet</span><span class="sxs-lookup"><span data-stu-id="f1271-167">https://aka.ms/azuremigration\_datasheet</span></span>](https://aka.ms/azuremigration\_datasheet)

-   <span data-ttu-id="f1271-168">Azure を移行します。</span><span class="sxs-lookup"><span data-stu-id="f1271-168">**Azure Migrate**</span></span>

    [<span data-ttu-id="f1271-169">http://azuremigrationcenter.com/</span><span class="sxs-lookup"><span data-stu-id="f1271-169">http://azuremigrationcenter.com/</span></span>](http://azuremigrationcenter.com/)

-   <span data-ttu-id="f1271-170">**Site Recovery と Azure への移行します。**</span><span class="sxs-lookup"><span data-stu-id="f1271-170">**Migrate to Azure with Site Recovery**</span></span>

    [<span data-ttu-id="f1271-171">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure</span><span class="sxs-lookup"><span data-stu-id="f1271-171">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

-   <span data-ttu-id="f1271-172">**Azure Site Recovery サービスの概要**</span><span class="sxs-lookup"><span data-stu-id="f1271-172">**Azure Site Recovery service overview**</span></span>

    [<span data-ttu-id="f1271-173">https://docs.microsoft.com/azure/site-recovery/site-recovery-overview</span><span class="sxs-lookup"><span data-stu-id="f1271-173">https://docs.microsoft.com/azure/site-recovery/site-recovery-overview</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

-   <span data-ttu-id="f1271-174">**AWS を Azure Vm で Vm を移行します。**</span><span class="sxs-lookup"><span data-stu-id="f1271-174">**Migrating VMs in AWS to Azure VMs**</span></span>

    [<span data-ttu-id="f1271-175">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure</span><span class="sxs-lookup"><span data-stu-id="f1271-175">https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure</span></span>](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
<span data-ttu-id="f1271-176">[前へ](index.md)
[次へ](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="f1271-176">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
