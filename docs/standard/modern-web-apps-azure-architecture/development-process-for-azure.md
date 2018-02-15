---
title: "Azure の開発プロセス"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |Azure の開発プロセス"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 576a717cbdcb8cf465e8cb7b4898df1df7447aa7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="development-process-for-azure"></a><span data-ttu-id="4bf59-103">Azure の開発プロセス</span><span class="sxs-lookup"><span data-stu-id="4bf59-103">Development process for Azure</span></span>

> <span data-ttu-id="4bf59-104">_「、クラウドに個人ユーザーおよび小規模企業、指をスナップできエンタープライズ クラスのサービスをすばやくセットアップできます。」_</span><span class="sxs-lookup"><span data-stu-id="4bf59-104">_"With the cloud, individuals and small businesses can snap their fingers and instantly set up enterprise-class services."_</span></span>  
> <span data-ttu-id="4bf59-105">_-者を務める Roy ので、セントラル_</span><span class="sxs-lookup"><span data-stu-id="4bf59-105">_- Roy Stephan_</span></span>

 ## <a name="vision"></a><span data-ttu-id="4bf59-106">ビジョン</span><span class="sxs-lookup"><span data-stu-id="4bf59-106">Vision</span></span>

> <span data-ttu-id="4bf59-107">*ASP .NET Core アプリケーションが適切に設計された必要な場合、Visual Studio または dotnet CLI と Visual Studio Code または任意のエディターを使用する方法を開発します。*</span><span class="sxs-lookup"><span data-stu-id="4bf59-107">*Develop well-designed ASP .NET Core applications the way you like, using Visual Studio or the dotnet CLI and Visual Studio Code or your editor of choice.*</span></span>

## <a name="development-environment-for-aspnet-core-apps"></a><span data-ttu-id="4bf59-108">ASP.NET Core アプリケーションの開発環境</span><span class="sxs-lookup"><span data-stu-id="4bf59-108">Development environment for ASP.NET Core apps</span></span>

### <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="4bf59-109">開発ツールの選択: IDE やエディター</span><span class="sxs-lookup"><span data-stu-id="4bf59-109">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="4bf59-110">かどうか完全かつ強力な IDE または軽量とアジャイル エディターについて、必要に応じて、Microsoft ASP.NET Core アプリケーションの開発時に対応します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-110">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when developing ASP.NET Core applications.</span></span>

<span data-ttu-id="4bf59-111">**Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="4bf59-111">**Visual Studio 2017.**</span></span> <span data-ttu-id="4bf59-112">使用する場合*Visual Studio 2017* ASP.NET Core アプリケーションを構築できますがある限り、 *.NET Core クロスプラット フォーム開発*ワークロードがインストールされています。</span><span class="sxs-lookup"><span data-stu-id="4bf59-112">If you're using *Visual Studio 2017* you can build ASP.NET Core applications as long as you have the *.NET Core cross-platform development* workload installed.</span></span> <span data-ttu-id="4bf59-113">図 10-1 では、Visual Studio 2017 の [設定] ダイアログ ボックスで、必要なワークロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="4bf59-113">Figure 10-1 shows the required workload in the Visual Studio 2017 setup dialog.</span></span>

![](./media/image10-1.png)

<span data-ttu-id="4bf59-114">**図 10-1。**</span><span class="sxs-lookup"><span data-stu-id="4bf59-114">**Figure 10-1.**</span></span> <span data-ttu-id="4bf59-115">Visual Studio 2017 で .NET Core ワークロードをインストールしています。</span><span class="sxs-lookup"><span data-stu-id="4bf59-115">Installing the .NET Core workload in Visual Studio 2017.</span></span>

[<span data-ttu-id="4bf59-116">Visual Studio 2017 をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="4bf59-116">Download Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)

<span data-ttu-id="4bf59-117">**Visual Studio Code と dotnet CLI** (Mac、Linux および Windows 用のクロスプラット フォーム ツール)。</span><span class="sxs-lookup"><span data-stu-id="4bf59-117">**Visual Studio Code and dotnet CLI** (Cross-Platform Tools for Mac, Linux and Windows).</span></span> <span data-ttu-id="4bf59-118">任意の開発言語をサポートする、軽量でクロスプラット フォーム エディターを使用する場合は、Microsoft Visual Studio Code と dotnet CLI を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-118">If you prefer a lightweight and cross-platform editor supporting any development language, you can use Microsoft Visual Studio Code and the dotnet CLI.</span></span> <span data-ttu-id="4bf59-119">これらの製品では、開発者のワークフローを利用すれば、簡単かつ堅牢なエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-119">These products provide a simple yet robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="4bf59-120">さらに、Visual Studio のコードは C の拡張機能をサポートしている\#および web 開発、intellisense と、エディター内のショートカット タスクを提供します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-120">Additionally, Visual Studio Code supports extensions for C\# and web development, providing intellisense and shortcut-tasks within the editor.</span></span>

[<span data-ttu-id="4bf59-121">.NET Core SDK をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4bf59-121">Download the .NET Core SDK</span></span>](https://www.microsoft.com/net/download/core)

[<span data-ttu-id="4bf59-122">Visual Studio のコードをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4bf59-122">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a><span data-ttu-id="4bf59-123">Azure でホストされる ASP.NET Core アプリケーションの開発のワークフロー</span><span class="sxs-lookup"><span data-stu-id="4bf59-123">Development workflow for Azure-hosted ASP.NET Core apps</span></span>

<span data-ttu-id="4bf59-124">アプリケーションの開発ライフ サイクルは、アプリケーションが希望する言語を使用し、ローカルでテストをコーディング、各開発者のコンピューターから開始します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-124">The application development lifecycle starts from each developer's machine, coding the app using their preferred language and testing it locally.</span></span> <span data-ttu-id="4bf59-125">開発者は、優先されるソース管理システムを選択することがあります継続的な統合 (CI) や継続的な配信/デプロイ (CD) ビルド サーバーを使用して構成できますや、Azure 組み込みの機能に基づいたしてください。</span><span class="sxs-lookup"><span data-stu-id="4bf59-125">Developers may choose their preferred source control system and can configure Continuous Integration (CI) and/or Continuous Delivery/Deployment (CD) using a build server or based on built-in Azure features.</span></span>

<span data-ttu-id="4bf59-126">Visual Studio Team Services や、組織を使用する、CI/CD を使用して ASP.NET Core アプリケーションの開発作業を開始する Team Foundation Server (TFS) を所有します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-126">To get started with developing an ASP.NET Core application using CI/CD, you can use Visual Studio Team Services or your organization's own Team Foundation Server (TFS).</span></span>

### <a name="initial-setup"></a><span data-ttu-id="4bf59-127">初期のセットアップ</span><span class="sxs-lookup"><span data-stu-id="4bf59-127">Initial Setup</span></span>

<span data-ttu-id="4bf59-128">アプリのリリース パイプラインを作成するには、ソース管理に、アプリケーション コードがある必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf59-128">To create a release pipeline for your app, you need to have your application code in source control.</span></span> <span data-ttu-id="4bf59-129">ローカル リポジトリを設定し、チーム プロジェクト内のリモート リポジトリに接続します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-129">Set up a local repository and connect it to a remote repository in a team project.</span></span> <span data-ttu-id="4bf59-130">これらの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4bf59-130">Follow these instructions:</span></span>

-   <span data-ttu-id="4bf59-131">[Git と Visual Studio でコードを共有](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs)または</span><span class="sxs-lookup"><span data-stu-id="4bf59-131">[Share your code with Git and Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) or</span></span>

-   [<span data-ttu-id="4bf59-132">TFVC および Visual Studio とコードを共有します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-132">Share your code with TFVC and Visual Studio</span></span>](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

<span data-ttu-id="4bf59-133">アプリケーションを展開する場合、Azure App Service を作成します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-133">Create an Azure App Service where you'll deploy your application.</span></span> <span data-ttu-id="4bf59-134">Azure ポータルの アプリ サービスのブレードに移動して、Web アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-134">Create a Web App by going to the App Services blade on the Azure portal.</span></span> <span data-ttu-id="4bf59-135">追加 を押しながらクリック、Web アプリケーション テンプレートを選択を作成する、名前とその他の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-135">Click +Add, select the Web App template, click Create, and provide a name and other details.</span></span> <span data-ttu-id="4bf59-136">Web アプリは {name} からアクセス可能になります。 azurewebsites.net です。</span><span class="sxs-lookup"><span data-stu-id="4bf59-136">The web app will be accessible from {name}.azurewebsites.net.</span></span>

![AzureWebApp](./media/image10-2.png)

<span data-ttu-id="4bf59-138">**図 10-2 です。**</span><span class="sxs-lookup"><span data-stu-id="4bf59-138">**Figure 10-2.**</span></span> <span data-ttu-id="4bf59-139">Azure ポータルで新しい Azure App Service Web アプリを作成しています。</span><span class="sxs-lookup"><span data-stu-id="4bf59-139">Creating a new Azure App Service Web App in the Azure Portal.</span></span>

<span data-ttu-id="4bf59-140">CI ビルド プロセスは新しいコードは、プロジェクトのソース管理リポジトリにコミットされるたびに自動ビルドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-140">Your CI build process will perform an automated build whenever new code is committed to the project's source control repository.</span></span> <span data-ttu-id="4bf59-141">これにより、コードはビルドをすぐにフィードバック (および、理想的には、自動のテストに合格した) し、配置可能性があることができます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-141">This gives you immediate feedback that the code builds (and, ideally, passes automated tests) and can potentially be deployed.</span></span> <span data-ttu-id="4bf59-142">この CI ビルド web が生成されますパッケージ成果物を展開し、CD プロセスによって消費を発行します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-142">This CI build will produce a web deploy package artifact and publish it for consumption by your CD process.</span></span>

[<span data-ttu-id="4bf59-143">CI ビルド プロセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-143">Define your CI build process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

<span data-ttu-id="4bf59-144">新しいコードをチームの誰かがコミットされるたびに、システムは、ビルドをキューは、継続的な統合を有効にすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-144">Be sure to enable continuous integration so the system will queue a build whenever someone on your team commits new code.</span></span> <span data-ttu-id="4bf59-145">ビルドをテストし、生成されているなど、web を確認、成果物のいずれかとしてパッケージを展開します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-145">Test the build and verify that it is producing a web deploy package as one of its artifacts.</span></span>

<span data-ttu-id="4bf59-146">ビルドが成功した場合、CD プロセスは、Azure web アプリに対する CI ビルドの結果を展開します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-146">When a build succeeds, your CD process will deploy the results of your CI build to your Azure web app.</span></span> <span data-ttu-id="4bf59-147">これを構成する、作成し、構成、*リリース*、Azure App Service に配置します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-147">To configure this, you create and configure a *Release*, which will deploy to your Azure App Service.</span></span>

[<span data-ttu-id="4bf59-148">CD リリース プロセスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-148">Define your CD release process</span></span>](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

<span data-ttu-id="4bf59-149">CI/CD パイプラインを構成した後は、web アプリの更新を行うし、ソース コントロールに展開されていることにコミットします。</span><span class="sxs-lookup"><span data-stu-id="4bf59-149">Once your CI/CD pipeline is configured, you can simply make updates to your web app and commit them to source control to have them deployed.</span></span>

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a><span data-ttu-id="4bf59-150">Azure でホストされる ASP.NET Core アプリケーションの開発のワークフロー</span><span class="sxs-lookup"><span data-stu-id="4bf59-150">Workflow for developing Azure-hosted ASP.NET Core applications</span></span>

<span data-ttu-id="4bf59-151">Azure アカウントと、CI/CD プロセスを構成した後、Azure でホストされる ASP.NET Core アプリケーションを開発するは簡単です。</span><span class="sxs-lookup"><span data-stu-id="4bf59-151">Once you have configured your Azure account and your CI/CD process, developing Azure-hosted ASP.NET Core applications is simple.</span></span> <span data-ttu-id="4bf59-152">図 10-3 に示すように、Web アプリと Azure App Service でホストされている、ASP.NET Core アプリケーションのビルド時に実行する通常の基本的な手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-152">The following are the basic steps you usually take when building an ASP.NET Core app, hosted in Azure App Service as a Web App, as illustrated in Figure 10-3.</span></span>

![EndToEndDevDeployWorkflow](./media/image10-3.png)

<span data-ttu-id="4bf59-154">**図 10-3。**</span><span class="sxs-lookup"><span data-stu-id="4bf59-154">**Figure 10-3.**</span></span> <span data-ttu-id="4bf59-155">ASP.NET Core アプリケーションの構築し、Azure でホストするそれらのステップ バイ ステップのワークフロー</span><span class="sxs-lookup"><span data-stu-id="4bf59-155">Step-by-step workflow for building ASP.NET Core apps and hosting them in Azure</span></span>

#### <a name="step-1-local-dev-environment-inner-loop"></a><span data-ttu-id="4bf59-156">手順 1.</span><span class="sxs-lookup"><span data-stu-id="4bf59-156">Step 1.</span></span> <span data-ttu-id="4bf59-157">ローカル開発環境の内側のループ</span><span class="sxs-lookup"><span data-stu-id="4bf59-157">Local Dev Environment Inner Loop</span></span>

<span data-ttu-id="4bf59-158">Azure への展開用 ASP.NET Core アプリケーションの開発は、それ以外の場合、アプリケーションの開発と同じです。</span><span class="sxs-lookup"><span data-stu-id="4bf59-158">Developing your ASP.NET Core application for deployment to Azure is no different from developing your application otherwise.</span></span> <span data-ttu-id="4bf59-159">ローカル開発環境に満足する、Visual Studio 2017 または dotnet CLI と Visual Studio Code または好みのエディターであるかどうかを使用します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-159">Use the local development environment you're comfortable with, whether that's Visual Studio 2017 or the dotnet CLI and Visual Studio Code or your preferred editor.</span></span> <span data-ttu-id="4bf59-160">コードを記述、実行し変更内容をデバッグ、自動のテストを実行でき、変更内容を共有されているソース管理リポジトリにプッシュする準備ができたらまで、ローカルのコミットをソース管理に加えることできます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-160">You can write code, run and debug your changes, run automated tests, and make local commits to source control until you're ready to push your changes to your shared source control repository.</span></span>

#### <a name="step-2-application-code-repository"></a><span data-ttu-id="4bf59-161">手順 2.</span><span class="sxs-lookup"><span data-stu-id="4bf59-161">Step 2.</span></span> <span data-ttu-id="4bf59-162">アプリケーション コード リポジトリ</span><span class="sxs-lookup"><span data-stu-id="4bf59-162">Application Code Repository</span></span>

<span data-ttu-id="4bf59-163">チームでコードを共有する準備ができたら、されるたびにする必要があります、変更内容をローカル ソース リポジトリからをリポジトリにプッシュ チームの共有ソース。</span><span class="sxs-lookup"><span data-stu-id="4bf59-163">Whenever you're ready to share your code with your team, you should push your changes from your local source repository to your team's shared source repository.</span></span> <span data-ttu-id="4bf59-164">場合は、カスタムの分岐で作業してきた、この手順通常では、共有の分岐にコードをマージする (おそらくの[プル要求](https://www.visualstudio.com/docs/git/pull-requests))。</span><span class="sxs-lookup"><span data-stu-id="4bf59-164">If you've been working in a custom branch, this step usually involves merging your code into a shared branch (perhaps by means of a [pull request](https://www.visualstudio.com/docs/git/pull-requests)).</span></span>

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a><span data-ttu-id="4bf59-165">手順 3.</span><span class="sxs-lookup"><span data-stu-id="4bf59-165">Step 3.</span></span> <span data-ttu-id="4bf59-166">ビルド サーバー: 継続的な統合。</span><span class="sxs-lookup"><span data-stu-id="4bf59-166">Build Server: Continuous Integration.</span></span> <span data-ttu-id="4bf59-167">ビルド、テストでは、パッケージ</span><span class="sxs-lookup"><span data-stu-id="4bf59-167">Build, Test, Package</span></span>

<span data-ttu-id="4bf59-168">共有アプリケーションのコード リポジトリに新しいコミットが行われたときに、ビルド サーバー上に新しいビルドがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-168">A new build is triggered on the build server whenever a new commit is made to the shared application code repository.</span></span> <span data-ttu-id="4bf59-169">CI のプロセスの一環として、このビルドが完全にアプリケーションをコンパイルし、どおりすべてが動作を確認する自動テストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf59-169">As part of the CI process, this build should fully compile the application and run automated tests to confirm everything is working as expected.</span></span> <span data-ttu-id="4bf59-170">CI のプロセスの最終結果には、パッケージのバージョンの web アプリ、展開用に準備をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf59-170">The end result of the CI process should be a packaged version of the web app, ready for deployment.</span></span>

#### <a name="step-4-build-server-continuous-delivery"></a><span data-ttu-id="4bf59-171">手順 4.</span><span class="sxs-lookup"><span data-stu-id="4bf59-171">Step 4.</span></span> <span data-ttu-id="4bf59-172">継続的配信のビルド サーバー:</span><span class="sxs-lookup"><span data-stu-id="4bf59-172">Build Server: Continuous Delivery</span></span>

<span data-ttu-id="4bf59-173">1 回、ビルドが成功したように、CD 処理を引き継ぎますビルド成果物を生成します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-173">Once a build as succeeded, the CD process will pick up the build artifacts produced.</span></span> <span data-ttu-id="4bf59-174">Web は、このパッケージを展開します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-174">This will include a web deploy package.</span></span> <span data-ttu-id="4bf59-175">Azure App Service、既存のサービスを新しく作成されたものに置き換えるには、ビルド サーバーはこのパッケージを展開します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-175">The build server will deploy this package to Azure App Service, replacing any existing service with the newly created one.</span></span> <span data-ttu-id="4bf59-176">通常この手順は、ステージング環境を対象が、一部のアプリケーションが直接 CD プロセスには、実稼働環境に展開します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-176">Typically this step targets a staging environment, but some applications deploy directly to production through a CD process.</span></span>

#### <a name="step-5-azure-app-service-web-app"></a><span data-ttu-id="4bf59-177">手順 5.</span><span class="sxs-lookup"><span data-stu-id="4bf59-177">Step 5.</span></span> <span data-ttu-id="4bf59-178">Azure App Service。</span><span class="sxs-lookup"><span data-stu-id="4bf59-178">Azure App Service.</span></span> <span data-ttu-id="4bf59-179">Web App.</span><span class="sxs-lookup"><span data-stu-id="4bf59-179">Web App.</span></span>

<span data-ttu-id="4bf59-180">展開した後は、Azure App Service Web アプリのコンテキスト内で ASP.NET Core アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-180">Once deployed, the ASP.NET Core application runs within the context of an Azure App Service Web App.</span></span> <span data-ttu-id="4bf59-181">この Web アプリは、監視することができ、さらに、Azure ポータルを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-181">This Web App can be monitored and further configured using the Azure Portal.</span></span>

#### <a name="step-6-production-monitoring-and-diagnostics"></a><span data-ttu-id="4bf59-182">手順 6.</span><span class="sxs-lookup"><span data-stu-id="4bf59-182">Step 6.</span></span> <span data-ttu-id="4bf59-183">運用環境の監視と診断</span><span class="sxs-lookup"><span data-stu-id="4bf59-183">Production Monitoring and Diagnostics</span></span>

<span data-ttu-id="4bf59-184">Web アプリの実行中には、アプリケーションのヘルスを監視および診断とユーザー動作のデータを収集できます。</span><span class="sxs-lookup"><span data-stu-id="4bf59-184">While the Web App is running, you can monitor the health of the application and collect diagnostics and user behavior data.</span></span> <span data-ttu-id="4bf59-185">Application Insights は、Visual Studio に含まれ、ASP.NET アプリ用の自動実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-185">Application Insights is included in Visual Studio, and offers automatic instrumentation for ASP.NET apps.</span></span> <span data-ttu-id="4bf59-186">使用状況、例外、要求、パフォーマンス、およびログに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4bf59-186">It can provide you with information on usage, exceptions, requests, performance, and logs.</span></span>

## <a name="references"></a><span data-ttu-id="4bf59-187">参照</span><span class="sxs-lookup"><span data-stu-id="4bf59-187">References</span></span>

<span data-ttu-id="4bf59-188">**ビルドし、ASP.NET Core アプリを Azure に配置**</span><span class="sxs-lookup"><span data-stu-id="4bf59-188">**Build and Deploy Your ASP.NET Core App to Azure**</span></span>  
<span data-ttu-id="4bf59-189"><https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure></span><span class="sxs-lookup"><span data-stu-id="4bf59-189"><https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4bf59-190">[前](test-asp-net-core-mvc-apps.md) [次へ] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="4bf59-190">[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)</span></span>
