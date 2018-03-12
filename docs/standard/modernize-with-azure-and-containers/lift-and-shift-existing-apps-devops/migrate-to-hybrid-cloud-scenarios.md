---
title: "ハイブリッド クラウド シナリオへの移行します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |ハイブリッド クラウド シナリオへの移行します。"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6216068786745ac4ebc00263a14b4afe247193f5
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="d47f2-103">ハイブリッド クラウド シナリオへの移行します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="d47f2-104">組織や企業によっては、Microsoft Azure などのパブリック クラウドに、アプリケーションの一部または規制や独自のポリシーのための他の任意のパブリック クラウドに移行できません。</span><span class="sxs-lookup"><span data-stu-id="d47f2-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="d47f2-105">ただし、どのような組織は、パブリック クラウドおよびその他のアプリケーション、オンプレミスでのアプリケーションの一部がなくなりますメリットがある可能性がありますです。</span><span class="sxs-lookup"><span data-stu-id="d47f2-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="d47f2-106">混在する環境がさまざまなプラットフォームと内部設置型環境とパブリック クラウドで使用されているテクノロジのための環境での複雑度が高くを招くことができます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="d47f2-107">Microsoft では、最適なハイブリッド クラウド ソリューションを提供する、既存の資産を最適化できますいずれか、オンプレミスと Azure のハイブリッド クラウド内の一貫性を確保するときに、パブリック クラウドでします。</span><span class="sxs-lookup"><span data-stu-id="d47f2-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="d47f2-108">既存のスキルを最大化し、クラウドまたはオンプレミスで Azure スタック (オンプレミス) と Azure (パブリック クラウド) のおかげで実行できるアプリを構築するための柔軟で、統一されたアプローチを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="d47f2-109">セキュリティに関しては、ときに、ハイブリッド クラウドの間で管理およびセキュリティを一元化できます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="d47f2-110">内部設置型へのシングル サインオンを指定して、クラウド データ センターからすべての資産の制御を取得し、クラウド アプリできます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="d47f2-111">ためには、Active Directory のハイブリッド クラウドに拡張および id 管理を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d47f2-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="d47f2-112">最後に、配布しシームレスにデータを分析、クラウドとオンプレミスの資産に同じクエリ言語を使用し、適用できます分析と深いをその元に関係なく、データを強化する Azure で学習します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="d47f2-113">Azure のスタック</span><span class="sxs-lookup"><span data-stu-id="d47f2-113">Azure Stack</span></span>

<span data-ttu-id="d47f2-114">Azure のスタックは、ハイブリッド クラウド プラットフォームできるように、組織のデータ センターから Azure サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="d47f2-115">Azure のスタックは、エッジと接続されていない環境では、または特定のセキュリティとコンプライアンス要件を満たすように、主要なシナリオで、最新のアプリケーション用の新しいオプションをサポートするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="d47f2-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="d47f2-116">図 4-13 では、Microsoft が提供する場合は true。 ハイブリッド クラウド プラットフォームの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Azure のスタックは、Azure で Microsoft ハイブリッド クラウド プラットフォーム](./media/image13.jpg)

> <span data-ttu-id="d47f2-118">**図 4-13。**</span><span class="sxs-lookup"><span data-stu-id="d47f2-118">**Figure 4-13.**</span></span> <span data-ttu-id="d47f2-119">Azure のスタックは、Azure で Microsoft ハイブリッド クラウド プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="d47f2-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="d47f2-120">Azure のスタックは、ニーズに合わせて、展開の 2 つのオプションで提供されています。</span><span class="sxs-lookup"><span data-stu-id="d47f2-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="d47f2-121">Azure のスタックは、システムを統合</span><span class="sxs-lookup"><span data-stu-id="d47f2-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="d47f2-122">Azure のスタック開発キット</span><span class="sxs-lookup"><span data-stu-id="d47f2-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="d47f2-123">Azure のスタックは、システムを統合</span><span class="sxs-lookup"><span data-stu-id="d47f2-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="d47f2-124">Microsoft とハードウェア パートナーのパートナーシップでは、azure スタック統合システムが提供します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="d47f2-125">パートナーシップでは、わかりやすくするための管理の分散クラウド ペース革新性を実現するソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="d47f2-126">ハードウェアとソフトウェアの統合システムとして、Azure のスタックが提供されるため、まだクラウドから革新を採用しているときに柔軟性と制御、適切な量を取得します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="d47f2-127">Azure 統合スタック システムでは、12 のノードに 4 からサイズの範囲し、ハードウェア パートナーと Microsoft によって共同でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="d47f2-128">Azure スタック統合システムを使用すると、実稼働ワークロードの新しいシナリオを実装します。</span><span class="sxs-lookup"><span data-stu-id="d47f2-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="d47f2-129">Azure のスタック開発キット</span><span class="sxs-lookup"><span data-stu-id="d47f2-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="d47f2-130">Microsoft Azure スタック Development Kit では、評価し、Azure の履歴に関する学習を行うこともできる Azure スタックの単一ノード展開です。</span><span class="sxs-lookup"><span data-stu-id="d47f2-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="d47f2-131">またするツールと一貫性がある Azure して Api を使用して開発できます。 ここで、開発環境として Azure スタック開発キットを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d47f2-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="d47f2-132">Azure スタック Development Kit は、実稼働環境として使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="d47f2-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d47f2-133">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="d47f2-133">Additional resources</span></span>

-   <span data-ttu-id="d47f2-134">**Azure のハイブリッド クラウド**</span><span class="sxs-lookup"><span data-stu-id="d47f2-134">**Azure hybrid cloud**</span></span>

    [<span data-ttu-id="d47f2-135">https://www.microsoft.com/cloud-platform/hybrid-cloud</span><span class="sxs-lookup"><span data-stu-id="d47f2-135">https://www.microsoft.com/cloud-platform/hybrid-cloud</span></span>](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="d47f2-136">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="d47f2-136">**Azure Stack**</span></span>

    [<span data-ttu-id="d47f2-137">https://azure.microsoft.com/overview/azure-stack/</span><span class="sxs-lookup"><span data-stu-id="d47f2-137">https://azure.microsoft.com/overview/azure-stack/</span></span>](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="d47f2-138">**Windows コンテナーの active Directory のサービス アカウントします。**</span><span class="sxs-lookup"><span data-stu-id="d47f2-138">**Active Directory Service Accounts for Windows Containers**</span></span>

    [<span data-ttu-id="d47f2-139">https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts</span><span class="sxs-lookup"><span data-stu-id="d47f2-139">https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="d47f2-140">**サポートが Active Directory コンテナーを作成します。**</span><span class="sxs-lookup"><span data-stu-id="d47f2-140">**Create a container with Active Directory support**</span></span>

    [<span data-ttu-id="d47f2-141">https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/</span><span class="sxs-lookup"><span data-stu-id="d47f2-141">https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/</span></span>](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="d47f2-142">**Azure のハイブリッド特典ライセンス**</span><span class="sxs-lookup"><span data-stu-id="d47f2-142">**Azure Hybrid Benefit licensing**</span></span>

    [<span data-ttu-id="d47f2-143">https://azure.microsoft.com/pricing/hybrid-use-benefit/</span><span class="sxs-lookup"><span data-stu-id="d47f2-143">https://azure.microsoft.com/pricing/hybrid-use-benefit/</span></span>](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="d47f2-144">[前へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[次へ](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="d47f2-144">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
