---
title: コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958012"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="d62ef-103">コンテナー ベース アプリケーション用の Azure のコンピューティング プラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="d62ef-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="d62ef-104">お気付きに前のセクションを読んだ後、Azure は複数の選択肢を提供する、開いているクラウドです。</span><span class="sxs-lookup"><span data-stu-id="d62ef-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="d62ef-105">ニーズに最適値を使用するもには、コンテナー化アプリケーションを使用する製品/テクノロジに関する質問を明らかにただし、します。</span><span class="sxs-lookup"><span data-stu-id="d62ef-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="d62ef-106">として、*既定*このガイドで推奨されている主な条件、推奨事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d62ef-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="d62ef-107">**1 つのモノリシック アプリ:** Azure App Service の選択</span><span class="sxs-lookup"><span data-stu-id="d62ef-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="d62ef-108">**N 層アプリケーション:** orchestrators Azure Kubernetes サービス (AKS)、Service Fabric (SF) またはアプリ サービスなどを選択して、1 つまたはいくつかのバックエンド サービスがある場合</span><span class="sxs-lookup"><span data-stu-id="d62ef-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="d62ef-109">**Linux microservices:** AKS/Kubernetes の選択</span><span class="sxs-lookup"><span data-stu-id="d62ef-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="d62ef-110">**Windows microservices:** Service Fabric の選択</span><span class="sxs-lookup"><span data-stu-id="d62ef-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="d62ef-111">**サーバーなしの関数とイベント ハンドラー:** Azure 関数の選択</span><span class="sxs-lookup"><span data-stu-id="d62ef-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="d62ef-112">**大規模なバッチ:** Azure Batch の選択</span><span class="sxs-lookup"><span data-stu-id="d62ef-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="d62ef-113">ただし、製品の選択は、特定のアプリケーションのニーズと特性に依存するの salt、ピンチ操作でこの推奨事項を実行してください。</span><span class="sxs-lookup"><span data-stu-id="d62ef-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="d62ef-114">すべてのアプリケーションは、最初に類似した種類を検索する場合があるときでも同じです。</span><span class="sxs-lookup"><span data-stu-id="d62ef-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="d62ef-115">アプリケーションのニーズの詳細な分析の後は、選択されている製品が異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d62ef-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="d62ef-116">開始点としてお勧めして、初期のガイダンスの評価を開始することができ、特定の優先順位に基づくテストします。</span><span class="sxs-lookup"><span data-stu-id="d62ef-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="d62ef-117">次の図に、詳細な意思決定テーブル中にグローバルよりを分析できます。</span><span class="sxs-lookup"><span data-stu-id="d62ef-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="d62ef-118">通知方法 (Windows と OS の基になります。Linux) では、いくつか orchestrators が成熟 Linux コンテナーと Windows コンテナーの その他、決定要因こともできます。</span><span class="sxs-lookup"><span data-stu-id="d62ef-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="d62ef-119">たとえば、Linux コンテナーは、小さい Service Fabric で完成度の高い、非常に成熟 Kubernetes (Azure で AKS) です。</span><span class="sxs-lookup"><span data-stu-id="d62ef-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="d62ef-120">その一方で、Windows コンテナーは、(2017 年 1 月リリース) Service Fabric で完成度の高い小さい AKS で完成度の高い。</span><span class="sxs-lookup"><span data-stu-id="d62ef-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="d62ef-121">ただし、成熟度の OS でそれらの相違点は自動的に後で複数のプラットフォームは比較可能な OS 成熟度および意思決定が、アプリケーションが必要になるまたは各プラットフォームのエコシステムに基づく特定の機能に基づいた環境設定でさらにレイアウト理由があります。</span><span class="sxs-lookup"><span data-stu-id="d62ef-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d62ef-122">[前へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[次へ](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="d62ef-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
