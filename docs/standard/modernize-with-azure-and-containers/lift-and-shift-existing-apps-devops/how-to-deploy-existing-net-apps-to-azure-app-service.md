---
title: "既存の .NET アプリケーションを Azure App Service をデプロイする方法"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |既存の .NET アプリケーションを Azure App Service をデプロイする方法"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aefcd79574cbbf6b3759bfa6cc0f9e46a58244ce
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="cc254-103">既存の .NET アプリケーションを Azure App Service をデプロイする方法</span><span class="sxs-lookup"><span data-stu-id="cc254-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="cc254-104">Azure App Service の Web アプリの機能は、web サイトと web アプリをホストするために最適化された完全に管理されたコンピューティング プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="cc254-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="cc254-105">Microsoft Azure でのこの paas 型サービスに専念するビジネス ロジック、Azure は、インフラストラクチャを実行し、アプリをスケールの処理中にします。</span><span class="sxs-lookup"><span data-stu-id="cc254-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="cc254-106">サイトを検証し、Azure App Service Migration Assistant の App Service に移行</span><span class="sxs-lookup"><span data-stu-id="cc254-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="cc254-107">Visual Studio で、通常、アプリを App Service に移動する新しいアプリケーションを作成することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="cc254-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="cc254-108">ただし、App Service に既存のアプリケーションの移行を計画している場合は、まずすべてのアプリケーションの依存関係は App Service と互換性があるかどうかを評価するします。</span><span class="sxs-lookup"><span data-stu-id="cc254-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="cc254-109">これには、サーバーの OS など、サーバーにインストールされているサード パーティのソフトウェアの依存関係が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc254-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="cc254-110">使用することができます[Azure App Service Migration Assistant](https://www.migratetoazure.net/)をサイトを分析し、App Service に Windows および Linux の web サーバーから移行します。</span><span class="sxs-lookup"><span data-stu-id="cc254-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="cc254-111">移行の一環として、ツールは web アプリを作成および Azure 上のデータベースに応じて、コンテンツを発行し、データベースを発行します。</span><span class="sxs-lookup"><span data-stu-id="cc254-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="cc254-112">Azure アプリのサービスの移行のアシスタントをクラウドに Windows Server で実行されている IIS からの移行をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc254-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="cc254-113">App Service では、Windows Server 2003 およびそれ以降のバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc254-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> <span data-ttu-id="cc254-115">**図 4-5 です。**</span><span class="sxs-lookup"><span data-stu-id="cc254-115">**Figure 4-5.**</span></span> <span data-ttu-id="cc254-116">Azure App Service Migration Assistant を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc254-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="cc254-117">アプリ サービス Migration Assistant は、web サイトを web サーバーから Azure クラウドに移動するツールです。</span><span class="sxs-lookup"><span data-stu-id="cc254-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="cc254-118">Web サイトは、App Service に移行は、後にサイトがありますを安全かつ効率的に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc254-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="cc254-119">サイトがセットアップし、Azure クラウド PaaS サービス (アプリ サービス) で自動的に実行します。</span><span class="sxs-lookup"><span data-stu-id="cc254-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="cc254-120">App Service の移行ツールでは、web サイトを分析でき、App Service に移動するための互換性についてレポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="cc254-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="cc254-121">場合は、分析に満足したら、アプリ サービス Migration Assistant の内容、データ、および設定を移行することができます。</span><span class="sxs-lookup"><span data-stu-id="cc254-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="cc254-122">サイトに非常に互換性がない場合、移行ツールがわかります機能させるを調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc254-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cc254-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="cc254-123">Additional resources</span></span>

- <span data-ttu-id="cc254-124">**Azure App Service Migration Assistant**</span><span class="sxs-lookup"><span data-stu-id="cc254-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="cc254-125">https://www.migratetoazure.net/</span><span class="sxs-lookup"><span data-stu-id="cc254-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="cc254-126">[前へ](what-about-cloud-optimized-applications.md)
[次へ](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="cc254-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
