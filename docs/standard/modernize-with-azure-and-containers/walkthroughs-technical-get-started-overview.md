---
title: チュートリアルと技術は、開始の概要を取得します。
description: Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |チュートリアルと技術は、開始の概要を取得します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0bad7e3afbdf3e55c447319b3756f2235b9e0a19
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="586b8-103">チュートリアルと技術は、開始の概要を取得します。</span><span class="sxs-lookup"><span data-stu-id="586b8-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="586b8-104">この電子書籍のサイズを制限するには、追加のテクニカル ドキュメントと完全のチュートリアルで行われた使用可能な GitHub リポジトリです。</span><span class="sxs-lookup"><span data-stu-id="586b8-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="586b8-105">オンラインの一連のこの章で説明されているチュートリアルでは、Windows コンテナー、および Azure へのデプロイに基づいて複数の環境の詳細な手順のセットアップについて説明します。</span><span class="sxs-lookup"><span data-stu-id="586b8-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="586b8-106">次のセクションでは、各チュートリアルでは、その目標と高レベルのビジョンを通知し、関連するタスクを次の図は、について説明します。</span><span class="sxs-lookup"><span data-stu-id="586b8-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="586b8-107">チュートリアル自体を取得することができますに、 *eShopModernizing*でアプリの GitHub リポジトリの wiki [ https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="586b8-108">技術的なチュートリアルの一覧</span><span class="sxs-lookup"><span data-stu-id="586b8-108">Technical walkthrough list</span></span>

<span data-ttu-id="586b8-109">はじめに-次のチュートリアルでは、リフトしコンテナーを使用して、シフトし、し、Azure で複数の展開の選択肢を使用して、移動するサンプル アプリの一貫性のあるで包括的なに関するテクニカル ガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="586b8-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="586b8-110">次のチュートリアルの各アプリケーションを使用して、新しいサンプル eShopLegacy と eShopModernizing で GitHub で利用可能である[ https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="586b8-111">**EShop レガシ アプリケーションのツアー**</span><span class="sxs-lookup"><span data-stu-id="586b8-111">**Tour of eShop legacy apps**</span></span>

- <span data-ttu-id="586b8-112">**Windows コンテナーで、既存の .NET アプリケーションを containerize します。**</span><span class="sxs-lookup"><span data-stu-id="586b8-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

- <span data-ttu-id="586b8-113">**Azure Vm を Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="586b8-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="586b8-114">**Azure のコンテナー サービスで Kubernetes に Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="586b8-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="586b8-115">**Azure Service Fabric に Windows コンテナー ベースのアプリを展開します。**</span><span class="sxs-lookup"><span data-stu-id="586b8-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="586b8-116">EShop レガシ アプリケーションのチュートリアル 1: ツアー</span><span class="sxs-lookup"><span data-stu-id="586b8-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="586b8-117">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="586b8-117">Technical walkthrough availability</span></span>

<span data-ttu-id="586b8-118">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="586b8-119">概要</span><span class="sxs-lookup"><span data-stu-id="586b8-119">Overview</span></span>

<span data-ttu-id="586b8-120">このチュートリアルでは、次の 2 つのサンプルのレガシ アプリケーションの最初の実装を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-120">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="586b8-121">両方のサンプル アプリは、モノリシックのアーキテクチャを持ち、従来の ASP.NET を使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="586b8-121">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="586b8-122">1 つのアプリケーションが ASP.NET に基づく 4.x MVC です。2 番目のアプリケーションは、ASP.NET 4.x Web フォームに基づいています。</span><span class="sxs-lookup"><span data-stu-id="586b8-122">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="586b8-123">両方のアプリケーションが、 [GitHub リポジトリの eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-123">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="586b8-124">両方のサンプル アプリを containerize すると同様の方法を containerize するクラシック[Windows Communication Foundation](../../framework/wcf/whats-wcf.md)をデスクトップ アプリケーションとして使用する (WCF) アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="586b8-124">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="586b8-125">例については、次を参照してください。 [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-125">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="586b8-126">目的</span><span class="sxs-lookup"><span data-stu-id="586b8-126">Goals</span></span>

<span data-ttu-id="586b8-127">このチュートリアルの主な目的は、これらのアプリとそのコードおよび構成について理解するだけです。</span><span class="sxs-lookup"><span data-stu-id="586b8-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="586b8-128">テスト目的で SQL データベースを使用せず、モック データを使用して、生成されるように、アプリを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="586b8-129">このオプションの構成は、分離された方法で依存関係の挿入に基づいています。</span><span class="sxs-lookup"><span data-stu-id="586b8-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="586b8-130">シナリオ</span><span class="sxs-lookup"><span data-stu-id="586b8-130">Scenario</span></span>

<span data-ttu-id="586b8-131">図 5-1 は、元のレガシ アプリケーションの簡単なシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="586b8-131">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![元のレガシ アプリケーションのシナリオを単純なアーキテクチャ](./media/image5-1.png)
>
> <span data-ttu-id="586b8-133">**図 5-1**</span><span class="sxs-lookup"><span data-stu-id="586b8-133">**Figure 5-1.**</span></span> <span data-ttu-id="586b8-134">元のレガシ アプリケーションのシナリオを単純なアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="586b8-134">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="586b8-135">ビジネス ドメインの観点から両方のアプリは管理機能に同じカタログを提供します。</span><span class="sxs-lookup"><span data-stu-id="586b8-135">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="586b8-136">EShop エンタープライズ チームのメンバーは表示および製品カタログを編集するアプリを使用します。</span><span class="sxs-lookup"><span data-stu-id="586b8-136">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="586b8-137">図 5-2 は、最初のアプリのスクリーン ショットを示しています。</span><span class="sxs-lookup"><span data-stu-id="586b8-137">Figure 5-2 shows the initial app screenshots.</span></span>

![ASP.NET MVC と ASP.NET Web フォーム アプリケーション (既存の/レガシ テクノロジ)](./media/image5-2.png)

> <span data-ttu-id="586b8-139">**図 5-2**</span><span class="sxs-lookup"><span data-stu-id="586b8-139">**Figure 5-2.**</span></span> <span data-ttu-id="586b8-140">ASP.NET MVC と ASP.NET Web フォーム アプリケーション (既存の/レガシ テクノロジ)</span><span class="sxs-lookup"><span data-stu-id="586b8-140">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="586b8-141">これらは、参照およびカタログのエントリを変更するために使用する web アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="586b8-141">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="586b8-142">両方のアプリが同じビジネス/機能の機能を提供するファクトは単に比較のためです。</span><span class="sxs-lookup"><span data-stu-id="586b8-142">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="586b8-143">ASP.NET MVC と ASP.NET Web フォームのフレームワークを使用して作成されたアプリのような近代化プロセスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-143">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="586b8-144">依存関係 ASP.NET 4.x か (いずれかの MVC または Web フォームの) 以前のバージョンは、コードが ASP.NET Core MVC を使用して、完全に記述し直すされない限り、これらのアプリケーションを .NET Core で実行されないことです。</span><span class="sxs-lookup"><span data-stu-id="586b8-144">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="586b8-145">これは、ポイントを再構築、またはコードを書き換えるにしない場合することができます、既存のアプリケーションを containerize もを使用して同じ .NET テクノロジと、同じコードを示しています。</span><span class="sxs-lookup"><span data-stu-id="586b8-145">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="586b8-146">コンテナーでは、レガシ コードを変更することがなくこのようなアプリケーションを実行する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-146">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="586b8-147">利点</span><span class="sxs-lookup"><span data-stu-id="586b8-147">Benefits</span></span>

<span data-ttu-id="586b8-148">このチュートリアルのメリットは、単純な: だけに慣れれば、コードとアプリケーションの構成、依存関係の挿入に基づいています。</span><span class="sxs-lookup"><span data-stu-id="586b8-148">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="586b8-149">その後、containerize および今後の複数の環境に展開するときに、この方法で試すことができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-149">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="586b8-150">次の手順</span><span class="sxs-lookup"><span data-stu-id="586b8-150">Next steps</span></span>

<span data-ttu-id="586b8-151">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="586b8-151">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="586b8-152">チュートリアル 2: Windows コンテナーで、既存の .NET アプリケーションを Containerize します。</span><span class="sxs-lookup"><span data-stu-id="586b8-152">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="586b8-153">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="586b8-153">Technical walkthrough availability</span></span>

<span data-ttu-id="586b8-154">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-154">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a><span data-ttu-id="586b8-155">概要</span><span class="sxs-lookup"><span data-stu-id="586b8-155">Overview</span></span>

<span data-ttu-id="586b8-156">Windows コンテナーの MVC、Web フォーム、または WCF、運用、開発、およびテスト環境に基づくように、既存の .NET アプリケーションの展開を向上させるために使用します。</span><span class="sxs-lookup"><span data-stu-id="586b8-156">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="586b8-157">目的</span><span class="sxs-lookup"><span data-stu-id="586b8-157">Goals</span></span>

<span data-ttu-id="586b8-158">このチュートリアルの目的は、既存の .NET Framework アプリケーションを containerizing いくつかのオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="586b8-158">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="586b8-159">次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-159">You can:</span></span>

- <span data-ttu-id="586b8-160">使用してアプリを containerize [Docker 用の Visual Studio 2017 Tools](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 年 1 またはそれ以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="586b8-160">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="586b8-161">手動で追加することによってアプリを containerize する[Dockerfile](https://docs.docker.com/engine/reference/builder/)を使用して、 [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-161">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="586b8-162">使用してアプリを containerize、 [Img2Docker](https://github.com/docker/communitytools-image2docker-win)ツール (Docker からオープン ソース ツール)。</span><span class="sxs-lookup"><span data-stu-id="586b8-162">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="586b8-163">このチュートリアルは、Docker 方法は、Visual Studio 2017 ツールに焦点を当てていますが、他の 2 つのアプローチが Dockerfile を使用してに関して類似しています。</span><span class="sxs-lookup"><span data-stu-id="586b8-163">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="586b8-164">シナリオ</span><span class="sxs-lookup"><span data-stu-id="586b8-164">Scenario</span></span>

<span data-ttu-id="586b8-165">図 5-3 は、コンテナー化 eShop レガシ アプリケーションのシナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="586b8-165">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![開発環境でのコンテナー化アプリケーションの簡略化されたアーキテクチャ図](./media/image5-3.png)
>
> <span data-ttu-id="586b8-167">**図 5-3**</span><span class="sxs-lookup"><span data-stu-id="586b8-167">**Figure 5-3.**</span></span> <span data-ttu-id="586b8-168">開発環境でのコンテナー化アプリケーションの簡略化されたアーキテクチャ図</span><span class="sxs-lookup"><span data-stu-id="586b8-168">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="586b8-169">利点</span><span class="sxs-lookup"><span data-stu-id="586b8-169">Benefits</span></span>

<span data-ttu-id="586b8-170">これには、コンテナーでモノリシックなアプリケーションを実行する利点があります。</span><span class="sxs-lookup"><span data-stu-id="586b8-170">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="586b8-171">最初に、アプリケーションのイメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="586b8-171">First, you create an image for the application.</span></span> <span data-ttu-id="586b8-172">その時点から、それぞれの配置を同じ環境で実行します。</span><span class="sxs-lookup"><span data-stu-id="586b8-172">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="586b8-173">すべてのコンテナーは、同じ OS バージョンを使用がインストールされている依存関係の同じバージョン、同じ .NET framework のバージョンを使用して、および同じ処理を使用してビルドされたをします。</span><span class="sxs-lookup"><span data-stu-id="586b8-173">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="586b8-174">基本的には、Docker イメージを使用して、アプリケーションの依存関係を制御します。</span><span class="sxs-lookup"><span data-stu-id="586b8-174">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="586b8-175">依存関係は、コンテナーを展開するときに、アプリケーションに移動します。</span><span class="sxs-lookup"><span data-stu-id="586b8-175">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="586b8-176">その他の利点は、開発者が Windows コンテナーによって提供されている一貫した環境でアプリケーションを実行できることです。</span><span class="sxs-lookup"><span data-stu-id="586b8-176">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="586b8-177">特定のバージョンでのみ表示される問題は、ステージングまたは運用環境での表示ではなく、すぐに発見できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-177">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="586b8-178">開発チームのメンバーで使用される開発環境での違いは重要アプリケーション コンテナーで実行時に小さいです。</span><span class="sxs-lookup"><span data-stu-id="586b8-178">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="586b8-179">コンテナー化アプリケーションは、テクスチャのスケール アウト曲線を含めます。</span><span class="sxs-lookup"><span data-stu-id="586b8-179">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="586b8-180">コンテナー化アプリケーションでは、VM または物理マシンのマシンあたりの通常のアプリケーション展開と比較してで有効にすると、複数のアプリケーションとサービス インスタンス (コンテナーに基づく) があります。</span><span class="sxs-lookup"><span data-stu-id="586b8-180">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="586b8-181">これにより、高密度」および「減らすために必要なリソース、orchestrators Kubernetes など Service Fabric を使用する場合に特にです。</span><span class="sxs-lookup"><span data-stu-id="586b8-181">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="586b8-182">コンテナリゼーション、理想的な状況では、アプリケーション コードに変更を加える必要ありません (C\#)。</span><span class="sxs-lookup"><span data-stu-id="586b8-182">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="586b8-183">ほとんどのシナリオでは、Docker の展開のメタデータ ファイル (Dockerfile と Docker Compose ファイル) だけができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-183">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="586b8-184">次の手順</span><span class="sxs-lookup"><span data-stu-id="586b8-184">Next steps</span></span>

<span data-ttu-id="586b8-185">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="586b8-185">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="586b8-186">チュートリアル 3: Azure Vm を Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-186">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="586b8-187">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="586b8-187">Technical walkthrough availability</span></span>

<span data-ttu-id="586b8-188">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-188">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="586b8-189">概要</span><span class="sxs-lookup"><span data-stu-id="586b8-189">Overview</span></span>

<span data-ttu-id="586b8-190">Azure の Windows Server 2016 仮想マシン (VM) 上の Docker ホストに展開するには、開発/テスト/ステージング環境をすばやくセットアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-190">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="586b8-191">アプリを検証するには、テスト担当者またはビジネス ユーザー用の共通の場所も示します。</span><span class="sxs-lookup"><span data-stu-id="586b8-191">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="586b8-192">Vm は、Service (IaaS) の実稼働環境として有効なインフラストラクチャをすることもできます。</span><span class="sxs-lookup"><span data-stu-id="586b8-192">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="586b8-193">目的</span><span class="sxs-lookup"><span data-stu-id="586b8-193">Goals</span></span>

<span data-ttu-id="586b8-194">このチュートリアルの目的は、Windows Server 2016、またはそれ以降のバージョンに基づいて Azure Vm を Windows コンテナーを展開する場合がある複数の代替を示すためです。</span><span class="sxs-lookup"><span data-stu-id="586b8-194">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="586b8-195">シナリオ</span><span class="sxs-lookup"><span data-stu-id="586b8-195">Scenarios</span></span>

<span data-ttu-id="586b8-196">このチュートリアルでは、いくつかのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="586b8-196">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="586b8-197">シナリオ a: 展開は、Docker エンジン接続から開発用コンピューターから Azure VM に</span><span class="sxs-lookup"><span data-stu-id="586b8-197">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Docker エンジン接続を介して開発用コンピューターから Azure の仮想マシンを展開します。](./media/image5-4.png)

> <span data-ttu-id="586b8-199">**図 5-4**</span><span class="sxs-lookup"><span data-stu-id="586b8-199">**Figure 5-4.**</span></span> <span data-ttu-id="586b8-200">Docker エンジン接続を介して開発用コンピューターから Azure の仮想マシンを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-200">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="586b8-201">シナリオ b: Docker のレジストリを使用する Azure VM を展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-201">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Docker レジストリを使用して Azure の仮想マシンを配置します。](./media/image5-5.png)

> <span data-ttu-id="586b8-203">**図 5-5**</span><span class="sxs-lookup"><span data-stu-id="586b8-203">**Figure 5-5.**</span></span> <span data-ttu-id="586b8-204">Docker レジストリを使用して Azure の仮想マシンを配置します。</span><span class="sxs-lookup"><span data-stu-id="586b8-204">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="586b8-205">シナリオ c: Azure の仮想マシンに Visual Studio Team Services での CI/CD パイプラインから展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-205">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Visual Studio Team Services での CI/CD パイプラインから Azure の仮想マシンを展開します。](./media/image5-6.png)

> <span data-ttu-id="586b8-207">**図 5-6**</span><span class="sxs-lookup"><span data-stu-id="586b8-207">**Figure 5-6.**</span></span> <span data-ttu-id="586b8-208">Visual Studio Team Services での CI/CD パイプラインから Azure の仮想マシンを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-208">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="586b8-209">Windows コンテナーの azure Vm</span><span class="sxs-lookup"><span data-stu-id="586b8-209">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="586b8-210">Windows コンテナーの azure Vm は Vm の Windows Server 2016、Windows 10、またはそれ以降のバージョンに基づく、Docker エンジンがどちらも設定します。</span><span class="sxs-lookup"><span data-stu-id="586b8-210">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="586b8-211">ほとんどの場合は、Windows Server 2016 は Azure Vm で使用されます。</span><span class="sxs-lookup"><span data-stu-id="586b8-211">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="586b8-212">Azure は、という名前の VM を現在提供**コンテナーと Windows Server 2016**です。</span><span class="sxs-lookup"><span data-stu-id="586b8-212">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="586b8-213">この VM を使用して、Windows Server Core または Nano Server の Windows で、新しい Windows Server コンテナー機能を試みることができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-213">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="586b8-214">コンテナー OS イメージがインストールされ、その VM は Docker で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="586b8-214">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="586b8-215">利点</span><span class="sxs-lookup"><span data-stu-id="586b8-215">Benefits</span></span>

<span data-ttu-id="586b8-216">Windows コンテナーは、Azure にデプロイするときに、内部設置型 Windows Server 2016 の Vm を配置できますが、すぐに使用できる Windows Server コンテナーの Vm で、作業を開始する簡単な方法を取得します。</span><span class="sxs-lookup"><span data-stu-id="586b8-216">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="586b8-217">また、テスト担当者、および Azure の仮想マシン スケール セットによる自動スケーラビリティにアクセスできる一般的なオンラインの場所を取得します。</span><span class="sxs-lookup"><span data-stu-id="586b8-217">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="586b8-218">次の手順</span><span class="sxs-lookup"><span data-stu-id="586b8-218">Next steps</span></span>

<span data-ttu-id="586b8-219">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="586b8-219">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="586b8-220">チュートリアル 4: Azure のコンテナー サービスで Kubernetes に Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-220">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="586b8-221">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="586b8-221">Technical walkthrough availability</span></span>

<span data-ttu-id="586b8-222">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-222">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="586b8-223">概要</span><span class="sxs-lookup"><span data-stu-id="586b8-223">Overview</span></span>

<span data-ttu-id="586b8-224">Windows コンテナーに基づいているアプリケーションはすばやく遠ざかる、さらに IaaS Vm からプラットフォームを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="586b8-224">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="586b8-225">これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動化され、では、大幅な向上を配置およびバージョン管理を自動化します。</span><span class="sxs-lookup"><span data-stu-id="586b8-225">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="586b8-226">これらの目標を達成するには、orchestrator を使用して、 [Kubernetes](https://kubernetes.io/)で使用できる、 [Azure コンテナー サービス](https://azure.microsoft.com/services/container-service/)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-226">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="586b8-227">目的</span><span class="sxs-lookup"><span data-stu-id="586b8-227">Goals</span></span>

<span data-ttu-id="586b8-228">Kubernetes に Windows コンテナー ベースのアプリケーションを展開する方法については、このチュートリアルの目的は、(とも呼ばれる*K8s*) Azure コンテナー サービスでします。</span><span class="sxs-lookup"><span data-stu-id="586b8-228">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="586b8-229">2 段階のプロセスは、最初から Kubernetes への展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-229">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="586b8-230">Azure コンテナー サービスに Kubernetes クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-230">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="586b8-231">Kubernetes クラスターに関連するリソースとアプリケーションを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-231">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="586b8-232">シナリオ</span><span class="sxs-lookup"><span data-stu-id="586b8-232">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="586b8-233">開発環境から Kubernetes クラスターに直接シナリオ a: 配置</span><span class="sxs-lookup"><span data-stu-id="586b8-233">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![開発環境から Kubernetes クラスターに直接展開します。](./media/image5-7.png)

> <span data-ttu-id="586b8-235">**図 5-7**</span><span class="sxs-lookup"><span data-stu-id="586b8-235">**Figure 5-7.**</span></span> <span data-ttu-id="586b8-236">開発環境から Kubernetes クラスターに直接展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-236">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="586b8-237">Team Services でパイプライン シナリオ b: Kubernetes クラスターに CI/CD から展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-237">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Team Services での CI/CD パイプラインから Kubernetes クラスターを展開します。](./media/image5-8.png)

> <span data-ttu-id="586b8-239">**図 5-8**</span><span class="sxs-lookup"><span data-stu-id="586b8-239">**Figure 5-8.**</span></span> <span data-ttu-id="586b8-240">Team Services での CI/CD パイプラインから Kubernetes クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-240">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="586b8-241">利点</span><span class="sxs-lookup"><span data-stu-id="586b8-241">Benefits</span></span>

<span data-ttu-id="586b8-242">Kubernetes でクラスターに展開する多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="586b8-242">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="586b8-243">最大のメリットは、運用環境で環境をスケール アウトできます (既存のノードでは内部スケーラビリティ) を使用して、クラスター (ノードまたは Vm の数に基づくコンテナーのインスタンスの数に基づいて、アプリケーションを取得します。グローバルなスケーラビリティはクラスターの)。</span><span class="sxs-lookup"><span data-stu-id="586b8-243">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="586b8-244">Azure のコンテナー サービスは、具体的には Azure の一般的なオープン ソース ツールとテクノロジを最適化します。</span><span class="sxs-lookup"><span data-stu-id="586b8-244">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="586b8-245">移植性をコンテナーと、アプリケーションの構成の両方を提供する、開いているソリューションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="586b8-245">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="586b8-246">ホストの数、サイズを選択し、orchestrator ツール-コンテナーのサービスが他のすべてを処理します。</span><span class="sxs-lookup"><span data-stu-id="586b8-246">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="586b8-247">Kubernetes と開発者は他のユーザー間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画を考えた物理および仮想マシンに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-247">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="586b8-248">複数のコンテナーに基づくアプリケーション</span><span class="sxs-lookup"><span data-stu-id="586b8-248">Applications based on multiple containers</span></span>

- <span data-ttu-id="586b8-249">コンテナーのインスタンスと自動スケールを水平方向にレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="586b8-249">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="586b8-250">名前付けと (たとえば、内部 DNS) を検出します。</span><span class="sxs-lookup"><span data-stu-id="586b8-250">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="586b8-251">負荷を分散</span><span class="sxs-lookup"><span data-stu-id="586b8-251">Balancing loads</span></span>

- <span data-ttu-id="586b8-252">ローリング アップデート</span><span class="sxs-lookup"><span data-stu-id="586b8-252">Rolling updates</span></span>

- <span data-ttu-id="586b8-253">シークレットを配布します。</span><span class="sxs-lookup"><span data-stu-id="586b8-253">Distributing secrets</span></span>

- <span data-ttu-id="586b8-254">アプリケーションの正常性チェック</span><span class="sxs-lookup"><span data-stu-id="586b8-254">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="586b8-255">次の手順</span><span class="sxs-lookup"><span data-stu-id="586b8-255">Next steps</span></span>

<span data-ttu-id="586b8-256">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。 [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="586b8-256">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="586b8-257">チュートリアル 5: Azure Service Fabric を Windows コンテナー ベースのアプリを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-257">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="586b8-258">技術的なチュートリアルの可用性</span><span class="sxs-lookup"><span data-stu-id="586b8-258">Technical walkthrough availability</span></span>

<span data-ttu-id="586b8-259">技術的なチュートリアルは、eShopModernizing GitHub リポジトリの wiki で入手できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-259">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="586b8-260">概要</span><span class="sxs-lookup"><span data-stu-id="586b8-260">Overview</span></span>

<span data-ttu-id="586b8-261">Windows コンテナーをすばやくに基づいてアプリケーションは、プラットフォームでは、遠ざかる、さらに IaaS Vm からを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="586b8-261">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="586b8-262">これを簡単に高いスケーラビリティを実現するために必要なよりスケーラビリティ、自動化され、では、大幅な向上を配置およびバージョン管理を自動化します。</span><span class="sxs-lookup"><span data-stu-id="586b8-262">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="586b8-263">Orchestrator は、Azure クラウドで使用できますが、内部設置型の使用にも使用可能で、Azure Service Fabric を使用するか、別のパブリック クラウドであっても、これらの目標を実現できます。</span><span class="sxs-lookup"><span data-stu-id="586b8-263">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="586b8-264">目的</span><span class="sxs-lookup"><span data-stu-id="586b8-264">Goals</span></span>

<span data-ttu-id="586b8-265">このチュートリアルの目的では、azure Service Fabric クラスターを Windows コンテナー ベースのアプリケーションを展開する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="586b8-265">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="586b8-266">Service Fabric を最初から展開するには、2 段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="586b8-266">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="586b8-267">Azure (または、別の環境) は、Service Fabric クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-267">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="586b8-268">Service Fabric クラスターをアプリケーションと関連するリソースを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-268">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="586b8-269">シナリオ</span><span class="sxs-lookup"><span data-stu-id="586b8-269">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="586b8-270">Service Fabric クラスターに直接開発環境からのシナリオ a: 配置</span><span class="sxs-lookup"><span data-stu-id="586b8-270">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![開発環境から Service Fabric クラスターを直接展開します。](./media/image5-9.png)

> <span data-ttu-id="586b8-272">**図 5-9**</span><span class="sxs-lookup"><span data-stu-id="586b8-272">**Figure 5-9.**</span></span> <span data-ttu-id="586b8-273">開発環境から Service Fabric クラスターを直接展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-273">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="586b8-274">Team Services でパイプライン シナリオ b: Service Fabric クラスターを CI/CD から展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-274">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Visual Studio Team Services での CI/CD パイプラインから Service Fabric クラスターを展開します。](./media/image5-10.png)

> <span data-ttu-id="586b8-276">**図 5-10**</span><span class="sxs-lookup"><span data-stu-id="586b8-276">**Figure 5-10.**</span></span> <span data-ttu-id="586b8-277">Visual Studio Team Services での CI/CD パイプラインから Service Fabric クラスターを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-277">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="586b8-278">利点</span><span class="sxs-lookup"><span data-stu-id="586b8-278">Benefits</span></span>

<span data-ttu-id="586b8-279">Service Fabric クラスターを展開する利点は、Kubernetes を使用する利点と似ています。</span><span class="sxs-lookup"><span data-stu-id="586b8-279">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="586b8-280">1 つの違いは Service Fabric Kubernetes バージョン 1.9 で Windows コンテナーのベータ版のフェーズでは Kubernetes と比較して、Windows アプリケーションの運用環境より完成度の高い (2017 年 12 月)。</span><span class="sxs-lookup"><span data-stu-id="586b8-280">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="586b8-281">Kubernetes は、for Linux より完成度の高い環境です。</span><span class="sxs-lookup"><span data-stu-id="586b8-281">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="586b8-282">Azure Service Fabric を使用する主な利点は、運用環境で環境をスケール アウトできます (既存のノードでは内部スケーラビリティ) を使用するの数に基づいて、コンテナー インスタンスの数に基づいて、アプリケーションを取得します。ノードまたはクラスター (クラスターのグローバルな拡張性) で Vm です。</span><span class="sxs-lookup"><span data-stu-id="586b8-282">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="586b8-283">Azure Service Fabric は、コンテナーと、アプリケーションの構成の両方の移植性を提供します。</span><span class="sxs-lookup"><span data-stu-id="586b8-283">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="586b8-284">Azure では、クラスター、または独自のデータ センターに内部設置型インストールに Service Fabric ことができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-284">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="586b8-285">同様にも別のクラウドにこの Service Fabric クラスターをインストールすることができます[Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/)です。</span><span class="sxs-lookup"><span data-stu-id="586b8-285">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="586b8-286">Service Fabric で開発者は他のユーザー間で、次の機能を容易にするコンテナーを中心としたインフラストラクチャの計画を考えた物理および仮想マシンに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="586b8-286">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="586b8-287">複数のコンテナーに基づくアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="586b8-287">Applications based on multiple containers.</span></span>

- <span data-ttu-id="586b8-288">コンテナーのインスタンスおよび水平方向の自動スケーリングをレプリケートしています。</span><span class="sxs-lookup"><span data-stu-id="586b8-288">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="586b8-289">名前付けと (たとえば、内部 DNS) を検出します。</span><span class="sxs-lookup"><span data-stu-id="586b8-289">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="586b8-290">負荷を分散します。</span><span class="sxs-lookup"><span data-stu-id="586b8-290">Balancing loads.</span></span>

- <span data-ttu-id="586b8-291">更新プログラムの展開です。</span><span class="sxs-lookup"><span data-stu-id="586b8-291">Rolling updates.</span></span>

- <span data-ttu-id="586b8-292">シークレットを配布します。</span><span class="sxs-lookup"><span data-stu-id="586b8-292">Distributing secrets.</span></span>

- <span data-ttu-id="586b8-293">アプリケーションの正常性を確認します。</span><span class="sxs-lookup"><span data-stu-id="586b8-293">Application health checks.</span></span>

<span data-ttu-id="586b8-294">次の機能は、(他の orchestrators と比較して)、Service Fabric で排他が。</span><span class="sxs-lookup"><span data-stu-id="586b8-294">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="586b8-295">ステートフル サービスの機能、信頼性の高いサービス アプリケーションのモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="586b8-295">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="586b8-296">アクター パターン、Reliable Actors アプリケーション モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="586b8-296">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="586b8-297">Windows または Linux のコンテナーに加え、ベア骨のプロセスを展開します。</span><span class="sxs-lookup"><span data-stu-id="586b8-297">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="586b8-298">高度なローリング更新プログラムとの正常性チェックします。</span><span class="sxs-lookup"><span data-stu-id="586b8-298">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="586b8-299">次の手順</span><span class="sxs-lookup"><span data-stu-id="586b8-299">Next steps</span></span>

<span data-ttu-id="586b8-300">GitHub wiki 上には、このコンテンツをさらに詳しい情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="586b8-300">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="586b8-301">[前へ](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[次へ](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="586b8-301">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
