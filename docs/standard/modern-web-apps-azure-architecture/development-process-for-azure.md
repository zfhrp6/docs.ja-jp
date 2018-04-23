---
title: Azure の開発プロセス
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | Azure の開発プロセス
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea5e699046d603ebb765265be403fd4561aa742e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="development-process-for-azure"></a><span data-ttu-id="961bf-103">Azure の開発プロセス</span><span class="sxs-lookup"><span data-stu-id="961bf-103">Development process for Azure</span></span>

> <span data-ttu-id="961bf-104">_"クラウドを使用すれば、個人や小企業は指をパチンと鳴らすだけでエンタープライズ クラスのサービスをすぐにセットアップできます。"_</span><span class="sxs-lookup"><span data-stu-id="961bf-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="961bf-105">_- Roy Stephan_</span><span class="sxs-lookup"><span data-stu-id="961bf-105">_- Roy Stephan_</span></span>

 ## <a name="vision"></a><span data-ttu-id="961bf-106">ビジョン</span><span class="sxs-lookup"><span data-stu-id="961bf-106">Vision</span></span>

> <span data-ttu-id="961bf-107">*Visual Studio または dotnet CLI および Visual Studio Code または任意のエディターを使用して、好きな方法で適切に設計された ASP .NET Core アプリケーションを開発します。*</span><span class="sxs-lookup"><span data-stu-id="961bf-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="961bf-108">ASP.NET Core アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="961bf-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="961bf-109">開発ツールの選択: IDE またはエディター</span><span class="sxs-lookup"><span data-stu-id="961bf-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="961bf-110">完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft は ASP.NET Core アプリケーションの開発に対応できます。</span><span class="sxs-lookup"><span data-stu-id="961bf-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="961bf-111">**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="961bf-111">**Visual Studio 2017.**</span></span> <span data-ttu-id="961bf-112">*Visual Studio 2017* を使用する場合、*.NET Core クロスプラットフォームの開発* ワークロードがインストールされている限り、ASP.NET Core アプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="961bf-112">If you're using *Visual Studio 2017* you can build ASP.NET Core applications as long as you have the *.NET Core cross-platform development* workload installed.</span></span> <span data-ttu-id="961bf-113">図 10-1 には、Visual Studio 2017 の必要なワークロードのセットアップ ダイアログが示されています。</span><span class="sxs-lookup"><span data-stu-id="961bf-113">Figure 10-1 shows the required workload in the Visual Studio 2017 setup dialog.</span></span>

![](./media/image10-1.png)

<span data-ttu-id="961bf-114">**図 10-1**</span><span class="sxs-lookup"><span data-stu-id="961bf-114">**Figure 10-1.**</span></span> <span data-ttu-id="961bf-115">Visual Studio 2017 での .NET Core ワークロードのインストール。</span><span class="sxs-lookup"><span data-stu-id="961bf-115">Installing the .NET Core workload in Visual Studio 2017.</span></span>

[<span data-ttu-id="961bf-116">Visual Studio 2017 をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="961bf-116">Download Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

<span data-ttu-id="961bf-117">**Visual Studio Code と dotnet CLI** (Mac、Linux および Windows 用のクロスプラット フォーム ツール)。</span><span class="sxs-lookup"><span data-stu-id="961bf-117">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="961bf-118">任意の開発言語をサポートする軽量なクロスプラットフォーム エディターを選択すると、Microsoft Visual Studio Code と dotnet CLI を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="961bf-118">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="961bf-119">これらの製品は、開発者のワークフローを効率化する、簡単かつ堅牢性の高いエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="961bf-119">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="961bf-120">さらに、Visual Studio Code は C\# および Web 開発の拡張機能をサポートし、エディター内での IntelliSense およびショートカット タスクを提供します。</span><span class="sxs-lookup"><span data-stu-id="961bf-120">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="961bf-121">.NET Core SDK をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="961bf-121">Download the .NET Core SDK</span></span>](https://www.microsoft.com/net/download/core)

[<span data-ttu-id="961bf-122">Visual Studio Code をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="961bf-122">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="961bf-123">Azure でホストされる ASP.NET Core アプリの開発ワークフロー</span><span class="sxs-lookup"><span data-stu-id="961bf-123">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="961bf-124">アプリケーション開発のライフサイクルは、各開発者のコンピューターで開始されます。その場合、アプリは開発者の好みの言語でコーディングされ、ローカルでテストされます。</span><span class="sxs-lookup"><span data-stu-id="961bf-124">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="961bf-125">開発者は好みのソース管理システムを選択できます。また、ビルド サーバーを使用するか、組み込みの Azure 機能に基づいて、継続的インテグレーション (CI) および/または継続的デリバリー/デプロイ (CD) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="961bf-125">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="961bf-126">CI/CD を使用して ASP.NET Core アプリケーションの開発を開始する場合は、Visual Studio Team Services または組織独自の Team Foundation Server (TFS) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="961bf-126">To get started with developing an ASP.NET Core application using CI/CD, you can use Visual Studio Team Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="961bf-127">初期セットアップ</span><span class="sxs-lookup"><span data-stu-id="961bf-127">Initial Setup</span></span>

<span data-ttu-id="961bf-128">アプリのリリース パイプラインを作成するには、ソース管理でアプリケーション コードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="961bf-128">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="961bf-129">ローカル リポジトリをセットアップし、それをチーム プロジェクトのリモート リポジトリに接続します。</span><span class="sxs-lookup"><span data-stu-id="961bf-129">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="961bf-130">次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="961bf-130">Follow these instructions:</span></span>

-   <span data-ttu-id="961bf-131">[Git と Visual Studio でコードを共有する](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs)、または</span><span class="sxs-lookup"><span data-stu-id="961bf-131">[Share your code with Git and Visual Studio](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs) or</span></span>

-   [<span data-ttu-id="961bf-132">TFVC と Visual Studio でコードを共有する</span><span class="sxs-lookup"><span data-stu-id="961bf-132">Share your code with TFVC and Visual Studio</span></span>](https://docs.microsoft.com/vsts/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="961bf-133">アプリケーションをデプロイする Azure App Service を作成します。</span><span class="sxs-lookup"><span data-stu-id="961bf-133">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="961bf-134">Azure Portal の App Services ブレードに移動して、Web アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="961bf-134">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="961bf-135">[+追加] をクリックして Web アプリ テンプレートを選択し、[作成] をクリックして名前とその他の詳細を入力します。</span><span class="sxs-lookup"><span data-stu-id="961bf-135">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="961bf-136">Web アプリは {name}.azurewebsites.net からアクセス可能になります。</span><span class="sxs-lookup"><span data-stu-id="961bf-136">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="961bf-138">**図 10-2**</span><span class="sxs-lookup"><span data-stu-id="961bf-138">**Figure 10-2.**</span></span> <span data-ttu-id="961bf-139">Azure Portal での新しい Azure App Service Web アプリの作成。</span><span class="sxs-lookup"><span data-stu-id="961bf-139">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="961bf-140">CI ビルド プロセスでは、新しいコードがプロジェクトのソース管理リポジトリにコミットされるたびに自動ビルドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="961bf-140">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="961bf-141">これにより、コードがビルドし (理想的には、自動テストに合格し)、デプロイされる可能性のあるフィードバックがすぐに返されます。</span><span class="sxs-lookup"><span data-stu-id="961bf-141">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="961bf-142">この CI ビルドでは Web デプロイ パッケージ成果物が生成され、CD プロセスで使用するために公開されます。</span><span class="sxs-lookup"><span data-stu-id="961bf-142">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="961bf-143">CI ビルド プロセスを定義する</span><span class="sxs-lookup"><span data-stu-id="961bf-143">Define your CI build process</span></span>](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#ci)

<span data-ttu-id="961bf-144">自分のチームのメンバーが新しいコードをコミットするたびにシステムによってビルドがキューに入れられるように、必ず、継続的インテグレーションを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="961bf-144">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="961bf-145">ビルドをテストし、成果物の 1 つとして Web デプロイ パッケージが生成されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="961bf-145">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="961bf-146">ビルドに成功すると、CD プロセスでは CI ビルドの結果が Azure Web アプリにデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="961bf-146">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="961bf-147">これを構成するには、*リリース*を作成して構成します。これは、Azure App Service にデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="961bf-147">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="961bf-148">CD リリース プロセスを定義する</span><span class="sxs-lookup"><span data-stu-id="961bf-148">Define your CD release process</span></span>](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#cd)

<span data-ttu-id="961bf-149">CI/CD パイプラインが構成されたら、Web アプリを更新して、それをソース管理にコミットしてデプロイするだけです。</span><span class="sxs-lookup"><span data-stu-id="961bf-149">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="961bf-150">Azure でホストされる ASP.NET Core アプリケーションの開発ワークフロー</span><span class="sxs-lookup"><span data-stu-id="961bf-150">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="961bf-151">Azure アカウントと CI/CD プロセスを構成したら、Azure でホストされる ASP.NET Core アプリケーションの開発は簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="961bf-151">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="961bf-152">以下の図 10-3 に示されているように、Web アプリとして Azure App Service でホストされる、ASP.NET Core アプリを構築する場合に通常行う基本的な手順があります。</span><span class="sxs-lookup"><span data-stu-id="961bf-152">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-3.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="961bf-154">**図 10-3**</span><span class="sxs-lookup"><span data-stu-id="961bf-154">**Figure 10-3.**</span></span> <span data-ttu-id="961bf-155">ASP.NET Core アプリを構築して Azure でホストするステップ バイ ステップのワークフロー</span><span class="sxs-lookup"><span data-stu-id="961bf-155">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="961bf-156">手順 1.</span><span class="sxs-lookup"><span data-stu-id="961bf-156">Step 1.</span></span> <span data-ttu-id="961bf-157">ローカル開発環境の内側のループ</span><span class="sxs-lookup"><span data-stu-id="961bf-157">Local Dev Environment Inner Loop</span></span>

<span data-ttu-id="961bf-158">Azure にデプロイする場合の ASP.NET Core アプリケーションの開発と、それ以外の場合のアプリケーションの開発は同じです。</span><span class="sxs-lookup"><span data-stu-id="961bf-158">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="961bf-159">使い慣れたローカル開発環境を使用します。つまり、Visual Studio 2017 または dotnet CLI および Visual Studio Code または好みのエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="961bf-159">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="961bf-160">コードを記述し、変更を実行してデバッグし、自動テストを実行し、変更を共有ソース管理リポジトリにプッシュできるようになるまで、ソース管理へのローカル コミットを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="961bf-160">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="961bf-161">手順 2.</span><span class="sxs-lookup"><span data-stu-id="961bf-161">Step 2.</span></span> <span data-ttu-id="961bf-162">アプリケーション コード リポジトリ</span><span class="sxs-lookup"><span data-stu-id="961bf-162">Application Code Repository</span></span>

<span data-ttu-id="961bf-163">チームでコードを共有できるようになった場合は、常にローカル ソース リポジトリからチームの共有ソース リポジトリに変更をプッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="961bf-163">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="961bf-164">カスタム ブランチで作業をしていた場合、この手順では通常、(たとえば、[プル要求](https://docs.microsoft.com/vsts/git/pull-requests)を使用して) コードを共有ブランチにマージします。</span><span class="sxs-lookup"><span data-stu-id="961bf-164">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](https://docs.microsoft.com/vsts/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="961bf-165">手順 3.</span><span class="sxs-lookup"><span data-stu-id="961bf-165">Step 3.</span></span> <span data-ttu-id="961bf-166">ビルド サーバー: 継続的インテグレーション。</span><span class="sxs-lookup"><span data-stu-id="961bf-166">Build Server: Continuous Integration.</span></span> <span data-ttu-id="961bf-167">ビルド、テスト、パッケージ</span><span class="sxs-lookup"><span data-stu-id="961bf-167">Build, Test, Package</span></span>

<span data-ttu-id="961bf-168">共有アプリケーション コード リポジトリに新しいコミットが行われるたびに、ビルド サーバーで新しいビルドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="961bf-168">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="961bf-169">CI プロセスの一部として、このビルドで完全にアプリケーションをコンパイルし、自動テストを実行して、すべて予期したとおりに動作していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="961bf-169">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="961bf-170">CI プロセスの最終結果は、デプロイの準備ができている、パッケージ化されたバージョンの Web アプリである必要があります。</span><span class="sxs-lookup"><span data-stu-id="961bf-170">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="961bf-171">手順 4.</span><span class="sxs-lookup"><span data-stu-id="961bf-171">Step 4.</span></span> <span data-ttu-id="961bf-172">ビルド サーバー: 継続的デリバリー</span><span class="sxs-lookup"><span data-stu-id="961bf-172">Build Server: Continuous Delivery</span></span>

<span data-ttu-id="961bf-173">ビルドが成功すると、CD プロセスは生成されたビルド成果物を選択します。</span><span class="sxs-lookup"><span data-stu-id="961bf-173">Once a build as succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="961bf-174">これには、Web デプロイ パッケージが含まれます。</span><span class="sxs-lookup"><span data-stu-id="961bf-174">This will include a web deploy package.</span></span> <span data-ttu-id="961bf-175">ビルド サーバーは Azure App Service にこのパッケージをデプロイして、既存のサービスを新しく作成されたものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="961bf-175">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="961bf-176">通常、この手順の対象はステージング環境ですが、一部のアプリケーションは CD プロセスを通じて運用環境に直接デプロイします。</span><span class="sxs-lookup"><span data-stu-id="961bf-176">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="961bf-177">手順 5.</span><span class="sxs-lookup"><span data-stu-id="961bf-177">Step 5.</span></span> <span data-ttu-id="961bf-178">Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="961bf-178">Azure App Service.</span></span> <span data-ttu-id="961bf-179">Web アプリ。</span><span class="sxs-lookup"><span data-stu-id="961bf-179">Web App.</span></span>

<span data-ttu-id="961bf-180">デプロイ後、ASP.NET Core アプリケーションは Azure App Service Web アプリのコンテキスト内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="961bf-180">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="961bf-181">この Web アプリは、Azure Portal を使用して監視でき、さらに構成することができます。</span><span class="sxs-lookup"><span data-stu-id="961bf-181">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="961bf-182">手順 6.</span><span class="sxs-lookup"><span data-stu-id="961bf-182">Step 6.</span></span> <span data-ttu-id="961bf-183">運用の監視と診断</span><span class="sxs-lookup"><span data-stu-id="961bf-183">Production Monitoring and Diagnostics</span></span>

<span data-ttu-id="961bf-184">Web アプリの実行中に、アプリケーションの正常性を監視し、診断およびユーザー動作のデータを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="961bf-184">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="961bf-185">Application Insights は Visual Studio に含まれており、ASP.NET アプリの自動実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="961bf-185">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="961bf-186">使用状況、例外、要求、パフォーマンス、およびログに関する情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="961bf-186">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="961bf-187">参照</span><span class="sxs-lookup"><span data-stu-id="961bf-187">References</span></span>

<span data-ttu-id="961bf-188">**ASP.NET Core アプリを構築して Azure にデプロイする**</span><span class="sxs-lookup"><span data-stu-id="961bf-188">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core>


>[!div class="step-by-step"]
<span data-ttu-id="961bf-189">[前へ] (test-asp-net-core-mvc-apps.md) [次へ] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="961bf-189">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>
