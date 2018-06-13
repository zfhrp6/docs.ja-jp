---
title: チュートリアルと技術は、開始の概要を取得します。
description: Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |チュートリアルと技術は、開始の概要を取得します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027390"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="ad224-103">チュートリアルと技術は、開始の概要を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad224-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="ad224-104">この電子書籍のサイズを制限するには、追加のテクニカル ドキュメントと完全のチュートリアルで行われた使用可能な GitHub リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="ad224-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="ad224-105">オンラインの一連のこの章で説明されているチュートリアルでは、Windows コンテナー、および Azure へのデプロイに基づいて複数の環境の詳細な手順のセットアップについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad224-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="ad224-106">次のセクションでは、各チュートリアルでは、その目標と高レベルのビジョンを通知し、関連するタスクを次の図は、について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad224-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="ad224-107">チュートリアル自体を取得することができますに、 *eShopModernizing*でアプリの GitHub リポジトリの wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="ad224-108">技術的なチュートリアルの一覧</span><span class="sxs-lookup"><span data-stu-id="ad224-108">Technical walkthrough list</span></span>

<span data-ttu-id="ad224-109">はじめに-次のチュートリアルでは、リフトしコンテナーを使用して、シフトし、し、Azure で複数の展開の選択肢を使用して、移動するサンプル アプリの一貫性のあるで包括的なに関するテクニカル ガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad224-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="ad224-110">次のチュートリアルの各アプリケーションを使用して、新しいサンプル eShopLegacy と eShopModernizing で GitHub で利用可能である[ https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="ad224-111">**EShop レガシ アプリ (基準の最新化) のツアー**</span><span class="sxs-lookup"><span data-stu-id="ad224-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="ad224-112">**Windows コンテナーで (WebForms & MVC) 既存の ASP.NET web アプリを containerize します。**</span><span class="sxs-lookup"><span data-stu-id="ad224-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="ad224-113">**Windows コンテナーで既存の WCF サービス (N 層アプリケーション) を containerize します。**</span><span class="sxs-lookup"><span data-stu-id="ad224-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="ad224-114">**Azure Vm を Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="ad224-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="ad224-115">**Azure のコンテナー サービスで Kubernetes に Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="ad224-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="ad224-116">**Azure Service Fabric に Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="ad224-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="ad224-117">EShop レガシ アプリケーションのチュートリアル 1: ツアー</span><span class="sxs-lookup"><span data-stu-id="ad224-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ad224-118">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="ad224-118">Technical walkthrough availability</span></span>

<span data-ttu-id="ad224-119">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="ad224-120">eShopModernizing wiki チュートリアル</span><span class="sxs-lookup"><span data-stu-id="ad224-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="ad224-121">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-121">Overview</span></span>

<span data-ttu-id="ad224-122">このチュートリアルでは、次の 3 つのサンプルのレガシ アプリケーションの最初の実装を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="ad224-123">最初の 2 つのサンプル web アプリケーションは、単体のアーキテクチャを持ち、従来の ASP.NET を使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="ad224-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="ad224-124">1 つのアプリケーションが ASP.NET に基づく 4.x MVC です。2 番目のアプリケーションは、ASP.NET 4.x Web フォームに基づいています。</span><span class="sxs-lookup"><span data-stu-id="ad224-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="ad224-125">3 番目のアプリはクライアント WinForms アプリケーションとサーバー側で構成される 3 層アプリ[Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md)サービス。</span><span class="sxs-lookup"><span data-stu-id="ad224-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="ad224-126">これらすべてのアプリケーションは、 [GitHub リポジトリの eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-127">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-127">Goals</span></span>

<span data-ttu-id="ad224-128">このチュートリアルの主な目的は、これらのアプリとそのコードおよび構成について理解するだけです。</span><span class="sxs-lookup"><span data-stu-id="ad224-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="ad224-129">テスト目的で SQL データベースを使用せず、モック データを使用して、生成されるように、アプリを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="ad224-130">このオプションの構成は、分離された方法で依存関係の挿入に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ad224-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="ad224-131">シナリオ 1: ASP.NET Web アプリ</span><span class="sxs-lookup"><span data-stu-id="ad224-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="ad224-132">次の図は、元のレガシ ASP.NET web アプリケーションの簡単なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![元のレガシ ASP.NET web アプリケーションのシナリオを単純なアーキテクチャ](./media/image5-1.png)
>

<span data-ttu-id="ad224-134">ビジネス ドメインの観点から両方のアプリは管理機能に同じカタログを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad224-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="ad224-135">EShop エンタープライズ チームのメンバーは表示および製品カタログを編集するアプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad224-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="ad224-136">次の図は、最初のアプリのスクリーン ショットを示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-136">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC と ASP.NET Web フォーム アプリケーション (既存の/レガシ テクノロジ)](./media/image5-2.png)

<span data-ttu-id="ad224-138">依存関係 ASP.NET 4.x か (いずれかの MVC または Web フォームの) 以前のバージョンは、コードが ASP.NET Core MVC を使用して、完全に記述し直すされない限り、これらのアプリケーションを .NET Core で実行されないことです。</span><span class="sxs-lookup"><span data-stu-id="ad224-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="ad224-139">シナリオ 2: WCF サービスと WinForms クライアント アプリ (アプリが 3 層)</span><span class="sxs-lookup"><span data-stu-id="ad224-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="ad224-140">次の図は、元の 3 層のレガシ アプリケーションの簡単なシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![WCF サービスと元レガシ 3 層アプリケーションおよび WinForms クライアント アプリのシナリオを単純なアーキテクチャ](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ad224-142">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-142">Benefits</span></span>

<span data-ttu-id="ad224-143">このチュートリアルのメリットは、単純な: コードと最初のアプリに精通して表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ad224-144">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-144">Next steps</span></span>

<span data-ttu-id="ad224-145">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ad224-146">ASP.NET MVC のベースラインをツアーと Web フォーム「レガシ」アプリ</span><span class="sxs-lookup"><span data-stu-id="ad224-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="ad224-147">WCF サービスの基準と WinForms (3 層)「レガシ」アプリのツアー</span><span class="sxs-lookup"><span data-stu-id="ad224-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="ad224-148">チュートリアル 2: Windows コンテナーで、既存の .NET アプリケーションを Containerize します。</span><span class="sxs-lookup"><span data-stu-id="ad224-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="ad224-149">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-149">Overview</span></span>

<span data-ttu-id="ad224-150">Windows コンテナーの MVC、Web フォーム、または WCF、運用、開発、およびテスト環境に基づくように、既存の .NET アプリケーションの展開を向上させるために使用します。</span><span class="sxs-lookup"><span data-stu-id="ad224-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-151">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-151">Goals</span></span>

<span data-ttu-id="ad224-152">このチュートリアルの目的は、既存の .NET Framework アプリケーションを containerizing いくつかのオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="ad224-153">次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-153">You can:</span></span>

- <span data-ttu-id="ad224-154">使用してアプリを containerize [Docker 用の Visual Studio 2017 Tools](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 年 1 またはそれ以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="ad224-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="ad224-155">手動で追加することによってアプリを containerize する[Dockerfile](https://docs.docker.com/engine/reference/builder/)を使用して、 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="ad224-156">使用してアプリを containerize、 [Img2Docker](https://github.com/docker/communitytools-image2docker-win)ツール (Docker からオープン ソース ツール)。</span><span class="sxs-lookup"><span data-stu-id="ad224-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="ad224-157">このチュートリアルは、Docker 方法は、Visual Studio 2017 ツールに焦点を当てていますが、他の 2 つのアプローチが Dockerfile を使用してに関して類似しています。</span><span class="sxs-lookup"><span data-stu-id="ad224-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="ad224-158">シナリオ 1: コンテナーの ASP.NET web アプリ</span><span class="sxs-lookup"><span data-stu-id="ad224-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="ad224-159">次の図は、コンテナー化 eShop レガシ web アプリのアプリケーションのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![開発環境での ASP.NET アプリケーションのコンテナーの簡略化されたアーキテクチャ図](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="ad224-161">シナリオ 2: コンテナーの WCF サービス</span><span class="sxs-lookup"><span data-stu-id="ad224-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="ad224-162">次の図は、コンテナー化の WCF サービスと 3 層アプリケーションのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![開発環境でのコンテナー化の WCF サービスのアーキテクチャ図を簡素化されます。](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="ad224-164">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-164">Benefits</span></span>

<span data-ttu-id="ad224-165">これには、コンテナーでモノリシックなアプリケーションを実行する利点があります。</span><span class="sxs-lookup"><span data-stu-id="ad224-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="ad224-166">最初に、アプリケーションのイメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad224-166">First, you create an image for the application.</span></span> <span data-ttu-id="ad224-167">その時点から、それぞれの配置を同じ環境で実行します。</span><span class="sxs-lookup"><span data-stu-id="ad224-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="ad224-168">すべてのコンテナーは、同じ OS バージョンを使用がインストールされている依存関係の同じバージョン、同じ .NET framework のバージョンを使用して、および同じ処理を使用してビルドされたをします。</span><span class="sxs-lookup"><span data-stu-id="ad224-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="ad224-169">基本的には、Docker イメージを使用して、アプリケーションの依存関係を制御します。</span><span class="sxs-lookup"><span data-stu-id="ad224-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="ad224-170">依存関係は、コンテナーを展開するときに、アプリケーションに移動します。</span><span class="sxs-lookup"><span data-stu-id="ad224-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="ad224-171">その他の利点は、開発者が Windows コンテナーによって提供されている一貫した環境でアプリケーションを実行できることです。</span><span class="sxs-lookup"><span data-stu-id="ad224-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="ad224-172">特定のバージョンでのみ表示される問題は、ステージングまたは運用環境での表示ではなく、すぐに発見できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="ad224-173">開発チームのメンバーで使用される開発環境での違いは重要アプリケーション コンテナーで実行時に小さいです。</span><span class="sxs-lookup"><span data-stu-id="ad224-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="ad224-174">コンテナー化アプリケーションは、テクスチャのスケール アウト曲線を含めます。</span><span class="sxs-lookup"><span data-stu-id="ad224-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="ad224-175">コンテナー化アプリケーションでは、VM または物理マシンのマシンあたりの通常のアプリケーション展開と比較してで有効にすると、複数のアプリケーションとサービス インスタンス (コンテナーに基づく) があります。</span><span class="sxs-lookup"><span data-stu-id="ad224-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="ad224-176">これにより、高密度」および「減らすために必要なリソース、orchestrators Kubernetes など Service Fabric を使用する場合に特にです。</span><span class="sxs-lookup"><span data-stu-id="ad224-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="ad224-177">コンテナリゼーション、理想的な状況では、アプリケーション コードに変更を加える必要ありません (C\#)。</span><span class="sxs-lookup"><span data-stu-id="ad224-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="ad224-178">ほとんどのシナリオでは、Docker の展開のメタデータ ファイル (Dockerfile と Docker Compose ファイル) だけができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="ad224-179">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-179">Next steps</span></span>

<span data-ttu-id="ad224-180">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="ad224-181">Windows コンテナーと Docker で .NET Framework の web アプリを containerize する方法</span><span class="sxs-lookup"><span data-stu-id="ad224-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="ad224-182">WCF サービスに Docker のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="ad224-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="ad224-183">チュートリアル 3: Azure Vm を Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ad224-184">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="ad224-184">Technical walkthrough availability</span></span>

<span data-ttu-id="ad224-185">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="ad224-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="ad224-186">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-186">Overview</span></span>

<span data-ttu-id="ad224-187">Azure の Windows Server 2016 仮想マシン (VM) 上の Docker ホストに展開するには、開発/テスト/ステージング環境をすばやくセットアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="ad224-188">アプリを検証するには、テスト担当者またはビジネス ユーザー用の共通の場所も示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="ad224-189">Vm は、Service (IaaS) の実稼働環境として有効なインフラストラクチャをすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad224-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-190">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-190">Goals</span></span>

<span data-ttu-id="ad224-191">このチュートリアルの目的は、Windows Server 2016、またはそれ以降のバージョンに基づいて Azure Vm を Windows コンテナーを展開する場合がある複数の代替を示すためです。</span><span class="sxs-lookup"><span data-stu-id="ad224-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ad224-192">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ad224-192">Scenarios</span></span>

<span data-ttu-id="ad224-193">このチュートリアルでは、いくつかのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad224-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="ad224-194">シナリオ a: 展開は、Docker エンジン接続から開発用コンピューターから Azure VM に</span><span class="sxs-lookup"><span data-stu-id="ad224-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker エンジン接続を介して開発用コンピューターから Azure の仮想マシンを展開します。](./media/image5-4.png)

> <span data-ttu-id="ad224-196">**図 5-4**</span><span class="sxs-lookup"><span data-stu-id="ad224-196">**Figure 5-4.**</span></span> <span data-ttu-id="ad224-197">Docker エンジン接続を介して開発用コンピューターから Azure の仮想マシンを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="ad224-198">シナリオ b: Docker のレジストリを使用する Azure VM を展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Docker レジストリを使用して Azure の仮想マシンを配置します。](./media/image5-5.png)

> <span data-ttu-id="ad224-200">**図 5-5**</span><span class="sxs-lookup"><span data-stu-id="ad224-200">**Figure 5-5.**</span></span> <span data-ttu-id="ad224-201">Docker レジストリを使用して Azure の仮想マシンを配置します。</span><span class="sxs-lookup"><span data-stu-id="ad224-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="ad224-202">シナリオ c: Azure の仮想マシンに Visual Studio Team Services での CI/CD パイプラインから展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Visual Studio Team Services での CI/CD パイプラインから Azure の仮想マシンを展開します。](./media/image5-6.png)

> <span data-ttu-id="ad224-204">**図 5-6**</span><span class="sxs-lookup"><span data-stu-id="ad224-204">**Figure 5-6.**</span></span> <span data-ttu-id="ad224-205">Visual Studio Team Services での CI/CD パイプラインから Azure の仮想マシンを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-205">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="ad224-206">Windows コンテナーの azure Vm</span><span class="sxs-lookup"><span data-stu-id="ad224-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="ad224-207">Windows コンテナーの azure Vm は Vm の Windows Server 2016、Windows 10、またはそれ以降のバージョンに基づく、Docker エンジンがどちらも設定します。</span><span class="sxs-lookup"><span data-stu-id="ad224-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="ad224-208">ほとんどの場合は、Windows Server 2016 は Azure Vm で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ad224-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="ad224-209">Azure は、という名前の VM を現在提供**コンテナーと Windows Server 2016**です。</span><span class="sxs-lookup"><span data-stu-id="ad224-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="ad224-210">この VM を使用して、Windows Server Core または Nano Server の Windows で、新しい Windows Server コンテナー機能を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="ad224-211">コンテナー OS イメージがインストールされ、その VM は Docker で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ad224-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="ad224-212">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-212">Benefits</span></span>

<span data-ttu-id="ad224-213">Windows コンテナーは、Azure にデプロイするときに、内部設置型 Windows Server 2016 の Vm を配置できますが、すぐに使用できる Windows Server コンテナーの Vm で、作業を開始する簡単な方法を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad224-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="ad224-214">また、テスト担当者、および Azure の仮想マシン スケール セットによる自動スケーラビリティにアクセスできる一般的なオンラインの場所を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad224-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ad224-215">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-215">Next steps</span></span>

<span data-ttu-id="ad224-216">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="ad224-217">チュートリアル 4: Azure のコンテナー インスタンス (ACI) に Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ad224-218">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="ad224-218">Technical walkthrough availability</span></span>

<span data-ttu-id="ad224-219">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="ad224-220">[ACI (Azure のコンテナー インスタンス) に、アプリを展開します。](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="ad224-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="ad224-221">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-221">Overview</span></span>

<span data-ttu-id="ad224-222">[Azure コンテナー インスタンス (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/)コンテナーの単一のインスタンスを展開するコンテナー開発/テスト/ステージング環境がある最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="ad224-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-223">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-223">Goals</span></span>

<span data-ttu-id="ad224-224">このチュートリアルは、主なシナリオ Azure コンテナー インスタンス (ACI) と ACI に eShopModernizing アプリを展開する方法に Windows コンテナーを展開するときにします。</span><span class="sxs-lookup"><span data-stu-id="ad224-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ad224-225">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ad224-225">Scenarios</span></span>

<span data-ttu-id="ad224-226">1 つまたはすべて (MVC アプリ、web フォーム アプリケーションまたは WCF サービス) のアプリの展開など ACI に eShopModernizing アプリの展開のバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="ad224-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="ad224-227">次に示す次のシナリオでことができます、コンテナーとして ACI (Azure のコンテナー インスタンス) に ASP.NET MVC アプリケーションと、これらの両方に展開されている SQL Server のコンテナーを参照します。</span><span class="sxs-lookup"><span data-stu-id="ad224-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![開発環境から ACI を展開します。](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="ad224-229">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-229">Benefits</span></span>

<span data-ttu-id="ad224-230">Azure のコンテナー インスタンスでは、簡単に作成し、仮想マシンをプロビジョニングまたは高レベルのサービスを採用することがなく、Azure では、Docker コンテナーを管理します。</span><span class="sxs-lookup"><span data-stu-id="ad224-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="ad224-231">ACI で直接 Azure での Windows コンテナーを展開してへの公開インターネット完全修飾ドメイン名 (FQDN) を数秒で (Docker Hub または Azure コンテナーのように Docker レジストリで準備ができて、Windows コンテナー イメージがある場合にレジストリ)。</span><span class="sxs-lookup"><span data-stu-id="ad224-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="ad224-232">注意事項</span><span class="sxs-lookup"><span data-stu-id="ad224-232">Considerations</span></span>

<span data-ttu-id="ad224-233">いずれか完全な .NET Framework による Windows コンテナーを展開する/ASP.NET または SQL Server には、Azure コンテナー インスタンス (ACI) が Docker イメージに存在するために (Windows コンテナーでの Windows Server 2016) のような通常の Docker ホストに展開すると非常に高速ではありませんたびに (プル Docker レジストリから) ダウンロードし、SQL コンテナー イメージ (15.1 GB) と ASP.NET のコンテナーのイメージ (13.9 GB) のサイズは大幅に大きなただし、これは、独自の docker ホスト (永続的にオンラインを維持することよりはるかに低コストAzure で Windows コンテナーの VM で Windows Server 2016) であり、その一方で、運用環境の配置の優れた選択肢 (AKS/ACS) を Azure または Azure Service Fabric で Kubernetes と同様に全体の orchestrator を言うまでもありません。</span><span class="sxs-lookup"><span data-stu-id="ad224-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="ad224-234">メイン最後に、としては、Azure コンテナー インスタンスを使用して開発およびテスト シナリオの場合とパイプラインの CI/CD に非常に説得力のあるオプション。</span><span class="sxs-lookup"><span data-stu-id="ad224-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad224-235">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-235">Next steps</span></span>

<span data-ttu-id="ad224-236">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="ad224-237">チュートリアル 5: Azure のコンテナー サービスで Kubernetes に Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ad224-238">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="ad224-238">Technical walkthrough availability</span></span>

<span data-ttu-id="ad224-239">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="ad224-240">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-240">Overview</span></span>

<span data-ttu-id="ad224-241">Windows コンテナーに基づいているアプリケーションはすばやく遠ざかる、さらに IaaS Vm からプラットフォームを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad224-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ad224-242">これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動化され、では、大幅な向上を配置およびバージョン管理を自動化します。</span><span class="sxs-lookup"><span data-stu-id="ad224-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ad224-243">これらの目標を達成するには、orchestrator を使用して、 [Kubernetes](https://kubernetes.io/)で使用できる、 [Azure コンテナー サービス](https://azure.microsoft.com/services/container-service/)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-244">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-244">Goals</span></span>

<span data-ttu-id="ad224-245">Kubernetes に Windows コンテナー ベースのアプリケーションを展開する方法については、このチュートリアルの目的は、(とも呼ばれる*K8s*) Azure コンテナー サービスでします。</span><span class="sxs-lookup"><span data-stu-id="ad224-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="ad224-246">2 段階のプロセスは、最初から Kubernetes への展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ad224-247">Azure コンテナー サービスに Kubernetes クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="ad224-248">Kubernetes クラスターに関連するリソースとアプリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ad224-249">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ad224-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="ad224-250">開発環境から Kubernetes クラスターに直接シナリオ a: 配置</span><span class="sxs-lookup"><span data-stu-id="ad224-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![開発環境から Kubernetes クラスターに直接展開します。](./media/image5-7.png)

> <span data-ttu-id="ad224-252">**図 5-7**</span><span class="sxs-lookup"><span data-stu-id="ad224-252">**Figure 5-7.**</span></span> <span data-ttu-id="ad224-253">開発環境から Kubernetes クラスターに直接展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="ad224-254">Team Services でパイプライン シナリオ b: Kubernetes クラスターに CI/CD から展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Team Services での CI/CD パイプラインから Kubernetes クラスターを展開します。](./media/image5-8.png)

> <span data-ttu-id="ad224-256">**図 5-8**</span><span class="sxs-lookup"><span data-stu-id="ad224-256">**Figure 5-8.**</span></span> <span data-ttu-id="ad224-257">Team Services での CI/CD パイプラインから Kubernetes クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="ad224-258">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-258">Benefits</span></span>

<span data-ttu-id="ad224-259">Kubernetes でクラスターに展開する多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="ad224-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="ad224-260">最大のメリットは、運用環境で環境をスケール アウトできます (既存のノードでは内部スケーラビリティ) を使用して、クラスター (ノードまたは Vm の数に基づくコンテナーのインスタンスの数に基づいて、アプリケーションを取得します。グローバルなスケーラビリティはクラスターの)。</span><span class="sxs-lookup"><span data-stu-id="ad224-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ad224-261">Azure のコンテナー サービスは、具体的には Azure の一般的なオープン ソース ツールとテクノロジを最適化します。</span><span class="sxs-lookup"><span data-stu-id="ad224-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="ad224-262">移植性をコンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad224-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="ad224-263">ホストの数、サイズを選択し、orchestrator ツール-コンテナーのサービスが他のすべてを処理します。</span><span class="sxs-lookup"><span data-stu-id="ad224-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="ad224-264">Kubernetes と開発者は他のユーザー間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画を考えた物理および仮想マシンに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ad224-265">複数のコンテナーに基づくアプリケーション</span><span class="sxs-lookup"><span data-stu-id="ad224-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="ad224-266">コンテナーのインスタンスと自動スケールを水平方向にレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="ad224-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="ad224-267">名前付けと (たとえば、内部 DNS) を検出します。</span><span class="sxs-lookup"><span data-stu-id="ad224-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="ad224-268">負荷を分散</span><span class="sxs-lookup"><span data-stu-id="ad224-268">Balancing loads</span></span>

- <span data-ttu-id="ad224-269">ローリング アップデート</span><span class="sxs-lookup"><span data-stu-id="ad224-269">Rolling updates</span></span>

- <span data-ttu-id="ad224-270">シークレットを配布します。</span><span class="sxs-lookup"><span data-stu-id="ad224-270">Distributing secrets</span></span>

- <span data-ttu-id="ad224-271">アプリケーションの正常性チェック</span><span class="sxs-lookup"><span data-stu-id="ad224-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad224-272">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-272">Next steps</span></span>

<span data-ttu-id="ad224-273">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="ad224-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="ad224-274">チュートリアル 6: Azure Service Fabric を Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="ad224-275">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="ad224-275">Technical walkthrough availability</span></span>

<span data-ttu-id="ad224-276">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="ad224-277">概要</span><span class="sxs-lookup"><span data-stu-id="ad224-277">Overview</span></span>

<span data-ttu-id="ad224-278">Windows コンテナーをすばやくに基づいてアプリケーションは、プラットフォームでは、遠ざかる、さらに IaaS Vm からを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad224-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="ad224-279">これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動化され、では、大幅な向上を配置およびバージョン管理を自動化します。</span><span class="sxs-lookup"><span data-stu-id="ad224-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="ad224-280">Orchestrator は、Azure クラウドで使用できますが、内部設置型の使用にも使用可能で、Azure Service Fabric を使用するか、別のパブリック クラウドであっても、これらの目標を実現できます。</span><span class="sxs-lookup"><span data-stu-id="ad224-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="ad224-281">目的</span><span class="sxs-lookup"><span data-stu-id="ad224-281">Goals</span></span>

<span data-ttu-id="ad224-282">このチュートリアルの目的では、azure Service Fabric クラスターを Windows コンテナー ベースのアプリケーションを展開する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="ad224-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="ad224-283">Service Fabric を最初から展開するには、2 段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="ad224-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="ad224-284">Azure (または、別の環境) は、Service Fabric クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="ad224-285">Service Fabric クラスターをアプリケーションと関連するリソースを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="ad224-286">シナリオ</span><span class="sxs-lookup"><span data-stu-id="ad224-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="ad224-287">Service Fabric クラスターに直接開発環境からのシナリオ a: 配置</span><span class="sxs-lookup"><span data-stu-id="ad224-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![開発環境から Service Fabric クラスターを直接展開します。](./media/image5-9.png)

> <span data-ttu-id="ad224-289">**図 5-9**</span><span class="sxs-lookup"><span data-stu-id="ad224-289">**Figure 5-9.**</span></span> <span data-ttu-id="ad224-290">開発環境から Service Fabric クラスターを直接展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="ad224-291">Team Services でパイプライン シナリオ b: Service Fabric クラスターを CI/CD から展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Visual Studio Team Services での CI/CD パイプラインから Service Fabric クラスターを展開します。](./media/image5-10.png)

> <span data-ttu-id="ad224-293">**図 5-10**</span><span class="sxs-lookup"><span data-stu-id="ad224-293">**Figure 5-10.**</span></span> <span data-ttu-id="ad224-294">Visual Studio Team Services での CI/CD パイプラインから Service Fabric クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="ad224-295">利点</span><span class="sxs-lookup"><span data-stu-id="ad224-295">Benefits</span></span>

<span data-ttu-id="ad224-296">Service Fabric クラスターを展開する利点は、Kubernetes を使用する利点と似ています。</span><span class="sxs-lookup"><span data-stu-id="ad224-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="ad224-297">1 つの違いは Service Fabric Kubernetes バージョン 1.9 で Windows コンテナーのベータ版のフェーズでは Kubernetes と比較して、Windows アプリケーションの運用環境より完成度の高い (2017 年 12 月)。</span><span class="sxs-lookup"><span data-stu-id="ad224-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="ad224-298">Kubernetes は、for Linux より完成度の高い環境です。</span><span class="sxs-lookup"><span data-stu-id="ad224-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="ad224-299">Azure Service Fabric を使用する主な利点は、運用環境で環境をスケール アウトできます (既存のノードでは内部スケーラビリティ) を使用するの数に基づいて、コンテナー インスタンスの数に基づいて、アプリケーションを取得します。ノードまたはクラスター (クラスターのグローバルな拡張性) で Vm です。</span><span class="sxs-lookup"><span data-stu-id="ad224-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="ad224-300">Azure Service Fabric は、コンテナーと、アプリケーションの構成の両方の移植性を提供します。</span><span class="sxs-lookup"><span data-stu-id="ad224-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="ad224-301">Azure では、クラスター、または独自のデータ センターに内部設置型インストールに Service Fabric ことができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="ad224-302">同様にも別のクラウドにこの Service Fabric クラスターをインストールすることができます[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)です。</span><span class="sxs-lookup"><span data-stu-id="ad224-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="ad224-303">Service Fabric で開発者は他のユーザー間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画を考えた物理および仮想マシンに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="ad224-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="ad224-304">複数のコンテナーに基づくアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="ad224-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="ad224-305">コンテナーのインスタンスおよび水平方向の自動スケーリングをレプリケートしています。</span><span class="sxs-lookup"><span data-stu-id="ad224-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="ad224-306">名前付けと (たとえば、内部 DNS) を検出します。</span><span class="sxs-lookup"><span data-stu-id="ad224-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="ad224-307">負荷を分散します。</span><span class="sxs-lookup"><span data-stu-id="ad224-307">Balancing loads.</span></span>

- <span data-ttu-id="ad224-308">更新プログラムの展開です。</span><span class="sxs-lookup"><span data-stu-id="ad224-308">Rolling updates.</span></span>

- <span data-ttu-id="ad224-309">シークレットを配布します。</span><span class="sxs-lookup"><span data-stu-id="ad224-309">Distributing secrets.</span></span>

- <span data-ttu-id="ad224-310">アプリケーションの正常性を確認します。</span><span class="sxs-lookup"><span data-stu-id="ad224-310">Application health checks.</span></span>

<span data-ttu-id="ad224-311">次の機能は、(他の orchestrators と比較して)、Service Fabric で排他が。</span><span class="sxs-lookup"><span data-stu-id="ad224-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="ad224-312">ステートフル サービスの機能、信頼性の高いサービス アプリケーションのモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad224-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="ad224-313">アクター パターン、Reliable Actors アプリケーション モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad224-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="ad224-314">Windows または Linux のコンテナーに加え、ベア骨のプロセスを展開します。</span><span class="sxs-lookup"><span data-stu-id="ad224-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="ad224-315">高度なローリング更新プログラムとの正常性チェックします。</span><span class="sxs-lookup"><span data-stu-id="ad224-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ad224-316">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad224-316">Next steps</span></span>

<span data-ttu-id="ad224-317">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ad224-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="ad224-318">[前へ](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[次へ](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="ad224-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
