---
title: "Linux または Windows Nano Server ホスト上で 1 つのコンテナー ベースの NET Core Web アプリケーションを展開する"
description: "コンテナー化 .NET アプリケーションの .NET マイクロサービス アーキテクチャ |Linux または Windows Nano Server ホスト上で 1 つのコンテナー ベースの .NET Core Web アプリケーションを展開する"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f85b3db6b4ca6d22c4b855c8b96051c1c31350a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a><span data-ttu-id="e826b-104">Linux または Windows Nano Server ホスト上で 1 つのコンテナー ベースの NET Core Web アプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="e826b-104">Deploying Single-Container-Based .NET Core Web Applications on Linux or Windows Nano Server Hosts</span></span>

<span data-ttu-id="e826b-105">*Docker コンテナーは、単純な Web アプリケーションのモノリシックな展開に使用できます。これにより継続的な統合と継続的な展開のパイプラインが向上し、展開から実稼働を成功に導くのために役立ちます。"自分のコンピューターでは動作するのに実稼働環境では動作しないのはなぜ" と悩むことがなくなります。*</span><span class="sxs-lookup"><span data-stu-id="e826b-105">*You can use Docker containers for monolithic deployment of simpler web applications. This improves continuous integration and continuous deployment pipelines and helps achieve deployment-to-production success. No more “It works in my machine, why does not work in production?”*</span></span>

<span data-ttu-id="e826b-106">マイクロサービスベースのアーキテクチャには、多くの利点がありますが、それらの利点のために複雑さが増加します。</span><span class="sxs-lookup"><span data-stu-id="e826b-106">A microservices-based architecture has many benefits, but those benefits come at a cost of increased complexity.</span></span> <span data-ttu-id="e826b-107">場合によっては、コストが利点を上回り、1 つのコンテナーまたは少数のコンテナーで実行されているモノリシック展開アプリケーションの方が有効なことがあります。</span><span class="sxs-lookup"><span data-stu-id="e826b-107">In some cases, the costs outweigh the benefits, and you will be better served with a monolithic deployment application running in a single container or in just a few containers.</span></span> 

<span data-ttu-id="e826b-108">モノリシック アプリケーションを適切に区切られたマイクロサービスに簡単に分解できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-108">A monolithic application might not be easily decomposable into well-separated microservices.</span></span> <span data-ttu-id="e826b-109">これらは機能別にパーティション化する必要があることは学習しました。マイクロサービスは相互に独立して起動することで、より回復力のあるアプリケーションを提供します。</span><span class="sxs-lookup"><span data-stu-id="e826b-109">You have learned that these should be partitioned by function: microservices should work independently of each other to provide a more resilient application.</span></span> <span data-ttu-id="e826b-110">アプリケーションの機能のスライスを提供できない場合、分割しても複雑さが増加するだけです。</span><span class="sxs-lookup"><span data-stu-id="e826b-110">If you cannot deliver feature slices of the application, separating it only adds complexity.</span></span>

<span data-ttu-id="e826b-111">場合によっては、アプリケーションを機能に依存せずに拡張できる必要があります</span><span class="sxs-lookup"><span data-stu-id="e826b-111">An application might not yet need to scale features independently.</span></span> <span data-ttu-id="e826b-112">たとえば、eShopOnContainers 参照アプリケーションの有効期間の早い段階で、トラフィックには、機能を複数の異なるマイクロサービスに分割する理由がないとします。</span><span class="sxs-lookup"><span data-stu-id="e826b-112">Let’s suppose that early in the life of our eShopOnContainers reference application, the traffic did not justify separating features into different microservices.</span></span> <span data-ttu-id="e826b-113">トラフィックは、十分に小さく、1 つのサービスにリソースを追加することは、一般的にすべてのサービスにリソースを追加することを意味しました。</span><span class="sxs-lookup"><span data-stu-id="e826b-113">Traffic was small enough that adding resources to one service typically meant adding resources to all services.</span></span> <span data-ttu-id="e826b-114">アプリケーションを個別のサービスに分割する追加の作業からは最小限のメリットしか得られませんでした。</span><span class="sxs-lookup"><span data-stu-id="e826b-114">The additional work to separate the application into discrete services provided minimal benefit.</span></span>

<span data-ttu-id="e826b-115">さらにアプリケーション開発の早い段階では、自然の機能的な境界を明確に把握できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e826b-115">Also, early in the development of an application you might not have a clear idea where the natural functional boundaries are.</span></span> <span data-ttu-id="e826b-116">最小の実行可能な製品を開発したときには、自然な境界がまだ明らかにならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="e826b-116">As you develop a minimum viable product, the natural separation might not yet have emerged.</span></span>

<span data-ttu-id="e826b-117">これらの条件の一部は、一時的な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-117">Some of these conditions might be temporary.</span></span> <span data-ttu-id="e826b-118">最初にモノリシック アプリケーションを作成し、後で一部の個別の機能を開発して、マイクロサービスとして展開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-118">You might start by creating a monolithic application, and later separate some features to be developed and deployed as microservices.</span></span> <span data-ttu-id="e826b-119">その他の条件はアプリケーションの問題の領域に不可欠な場合があります。つまり、アプリケーションを複数マイクロサービスに分割しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-119">Other conditions might be essential to the application’s problem space, meaning that the application might never be broken into multiple microservices.</span></span>

<span data-ttu-id="e826b-120">多くの個別のプロセスにアプリケーションを分割すると、オーバーヘッドも発生します。</span><span class="sxs-lookup"><span data-stu-id="e826b-120">Separating an application into many discrete processes also introduces overhead.</span></span> <span data-ttu-id="e826b-121">別のプロセスに機能を分離することで、複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="e826b-121">There is more complexity in separating features into different processes.</span></span> <span data-ttu-id="e826b-122">通信プロトコルはより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="e826b-122">The communication protocols become more complex.</span></span> <span data-ttu-id="e826b-123">メソッドの呼び出しではなく、サービス間の非同期通信を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-123">Instead of method calls, you must use asynchronous communications between services.</span></span> <span data-ttu-id="e826b-124">マイクロサービス アーキテクチャに移動するきには、eShopOnContainers アプリケーションのマイクロサービス バージョンに実装される多くの構築ブロックを追加する必要があります。つまり、イベント バスの処理、メッセージの回復性と再試行、最終的な整合性などです。</span><span class="sxs-lookup"><span data-stu-id="e826b-124">As you move to a microservices architecture, you need to add many of the building blocks implemented in the microservices version of the eShopOnContainers application: event bus handling, message resiliency and retries, eventual consistency, and more.</span></span>

<span data-ttu-id="e826b-125">EShopOnContainers の大幅に簡略化したバージョン (名前付き[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) で同じ GitHub リポジトリに含まれる) は、モノリシックな MVC アプリケーションとして実行され、説明したように、この設計を選択するといくつか利点が提供されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-125">A much-simplified version of eShopOnContainers (named [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) and included in the same GitHub repo) runs as a monolithic MVC application, and as just described, there are advantages offered by that design choice.</span></span> <span data-ttu-id="e826b-126">GitHub からこのアプリケーションのソースをダウンロードして、ローカルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-126">You can download the source for this application from GitHub and run it locally.</span></span> <span data-ttu-id="e826b-127">このモノリシック アプリケーションは、コンテナー環境で展開すると有益です。</span><span class="sxs-lookup"><span data-stu-id="e826b-127">Even this monolithic application benefits from being deployed in a container environment.</span></span>

<span data-ttu-id="e826b-128">1 つは、コンテナー化した展開は、アプリケーションのすべてのインスタンスが同じ環境で実行されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e826b-128">For one, the containerized deployment means that every instance of the application runs in the same environment.</span></span> <span data-ttu-id="e826b-129">これには、初期のテストと開発を行う開発者環境が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e826b-129">This includes the developer environment where early testing and development take place.</span></span> <span data-ttu-id="e826b-130">開発チームは、実稼働環境に一致するコンテナー化した環境でアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-130">The development team can run the application in a containerized environment that matches the production environment.</span></span>

<span data-ttu-id="e826b-131">さらに、コンテナー化アプリケーションは低コストでスケールアウトされます。</span><span class="sxs-lookup"><span data-stu-id="e826b-131">In addition, containerized applications scale out at lower cost.</span></span> <span data-ttu-id="e826b-132">先ほど見たように、コンテナー環境では、従来の VM 環境よりも多くのリソースを共有できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-132">As you saw earlier, the container environment enables greater resource sharing than traditional VM environments.</span></span>

<span data-ttu-id="e826b-133">最後に、アプリケーションのコンテナー化は、強制的にビジネス ロジックと記憶域サーバーの間を分離します。</span><span class="sxs-lookup"><span data-stu-id="e826b-133">Finally, containerizing the application forces a separation between the business logic and the storage server.</span></span> <span data-ttu-id="e826b-134">アプリケーションのスケール アウト時には、複数のコンテナーはすべて単一の物理記憶域メディアに移動します。</span><span class="sxs-lookup"><span data-stu-id="e826b-134">As the application scales out, the multiple containers will all rely on a single physical storage medium.</span></span> <span data-ttu-id="e826b-135">通常、SQL Server データベースを実行している高可用性サーバーになります。</span><span class="sxs-lookup"><span data-stu-id="e826b-135">This would typically be a high-availability server running a SQL Server database.</span></span>

## <a name="application-tour"></a><span data-ttu-id="e826b-136">アプリケーション ツアー</span><span class="sxs-lookup"><span data-stu-id="e826b-136">Application tour</span></span>

<span data-ttu-id="e826b-137">[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) アプリケーションでは、モノリシック アプリケーション (.NET Core で実行されている ASP.NET Core MVC ベースのアプリケーション) として実行されているいくつかの eShopOnContainers アプリケーションを表します。</span><span class="sxs-lookup"><span data-stu-id="e826b-137">The [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) application represents some of the eShopOnContainers application running as a monolithic application—an ASP.NET Core MVC based application running on .NET Core.</span></span> <span data-ttu-id="e826b-138">主に、前のセクションで説明したカタログ参照機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e826b-138">It mainly provides the catalog browsing capabilities that we described in earlier sections.</span></span>

<span data-ttu-id="e826b-139">アプリケーションは、カタログ ストレージのために SQL Server データベースを使用します。</span><span class="sxs-lookup"><span data-stu-id="e826b-139">The application uses a SQL Server database for the catalog storage.</span></span> <span data-ttu-id="e826b-140">コンテナー ベースの展開では、このモノリシックなアプリケーションはマイクロサービス ベースのアプリケーションと同じデータ ストアにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e826b-140">In container-based deployments, this monolithic application can access the same data store as the microservices-based application.</span></span> <span data-ttu-id="e826b-141">アプリケーションはモノリシック アプリケーションと共にコンテナー内で SQL Server を実行するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-141">The application is configured to run SQL Server in a container alongside the monolithic application.</span></span> <span data-ttu-id="e826b-142">実稼働環境では、SQL Server は、Docker ホストの外部の高可用性コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-142">In a production environment, SQL Server would run on a high-availability machine, outside of the Docker host.</span></span> <span data-ttu-id="e826b-143">開発またはテスト環境の利便性のために、独自のコンテナーで SQL Server を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e826b-143">For convenience in a dev or test environment, we recommend running SQL Server in its own container.</span></span>

<span data-ttu-id="e826b-144">初期機能セットは、カタログの参照のみを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e826b-144">The initial feature set only enables browsing the catalog.</span></span> <span data-ttu-id="e826b-145">更新プログラムは、コンテナー化アプリケーションの完全な機能セットを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e826b-145">Updates would enable the full feature set of the containerized application.</span></span> <span data-ttu-id="e826b-146">モノリシックな Web アプリケーションのアーキテクチャの詳細については、「[ASP.NET Web Application architecture practices](https://aka.ms/webappebook)」(ASP.NET Web アプリケーションのアーキテクチャのプラクティス) 電子ブックおよび関連する [eShopOnWeb サンプル アプリケーション](http://aka.ms/WebAppArchitecture) を参照してください。ただし、その場合は、シナリオは ASP.NET Core を使用した一般的な Web 開発に焦点を当てているため Docker コンテナー上では実行されていません。</span><span class="sxs-lookup"><span data-stu-id="e826b-146">A more advanced monolithic web application architecture is described in the [ASP.NET Web Application architecture practices](https://aka.ms/webappebook) e-book and related [eShopOnWeb sample application](http://aka.ms/WebAppArchitecture), although in that case it is not running on Docker containers because that scenario focuses on plain web development with ASP.NET Core.</span></span>

<span data-ttu-id="e826b-147">ただし、Docker コンテナーで実行される eShopOnContainers (eShopWeb) で簡略化されたバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-147">However, the simplified version available in eShopOnContainers (eShopWeb) runs in a Docker container.</span></span>

## <a name="docker-support"></a><span data-ttu-id="e826b-148">Docker のサポート</span><span class="sxs-lookup"><span data-stu-id="e826b-148">Docker support</span></span>

<span data-ttu-id="e826b-149">eShopOnWeb プロジェクトは、.NET Core で実行されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-149">The eShopOnWeb project runs on .NET Core.</span></span> <span data-ttu-id="e826b-150">そのため、Windows ベースまたは Linux ベースのコンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-150">Therefore, it can run in either Linux-based or Windows-based containers.</span></span> <span data-ttu-id="e826b-151">Docker の展開の場合、SQL Server に同じホストの種類を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-151">Note that for Docker deployment, you want to use the same host type for SQL Server.</span></span> <span data-ttu-id="e826b-152">Linux ベースのコンテナーは、小さなフット プリントが可能なので優先されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-152">Linux-based containers allow a smaller footprint and are preferred.</span></span>

<span data-ttu-id="e826b-153">Visual Studio には、ソリューションに Docker のサポートを追加するプロジェクト テンプレートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e826b-153">Visual Studio provides a project template that adds support for Docker to a solution.</span></span> <span data-ttu-id="e826b-154">プロジェクトを右クリックし、**[追加]** をクリックして、その後に **[Docker サポート]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e826b-154">You right-click the project, click **Add** followed by **Docker Support**.</span></span> <span data-ttu-id="e826b-155">テンプレートでは、Dockerfile をプロジェクトに追加し、最初に使用する docker compose.yml ファイルを提供する新しい **docker-compose** プロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="e826b-155">The template adds a Dockerfile to your project, and a new **docker-compose** project that provides a starter docker-compose.yml file.</span></span> <span data-ttu-id="e826b-156">GitHub からダウンロードする eShopOnWeb プロジェクトでは、この手順は既に実行されています。</span><span class="sxs-lookup"><span data-stu-id="e826b-156">This step has already been done in the eShopOnWeb project downloaded from GitHub.</span></span> <span data-ttu-id="e826b-157">図 6-1 に示すように、ソリューションに **eShopOnWeb** プロジェクトおよび **docker-compose** プロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e826b-157">You will see that the solution contains the **eShopOnWeb** project and the **docker-compose** project as shown in Figure 6-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="e826b-158">**図 6-1**。</span><span class="sxs-lookup"><span data-stu-id="e826b-158">**Figure 6-1**.</span></span> <span data-ttu-id="e826b-159">単一コンテナーの Web アプリケーションの **docker-compose** プロジェクト</span><span class="sxs-lookup"><span data-stu-id="e826b-159">The **docker-compose** project in a single-container web application</span></span>

<span data-ttu-id="e826b-160">これらのファイルは、すべての Docker プロジェクトと一貫性のある標準の docker-compose ファイルです。</span><span class="sxs-lookup"><span data-stu-id="e826b-160">These files are standard docker-compose files, consistent with any Docker project.</span></span> <span data-ttu-id="e826b-161">これらは、Visual Studio で、またはコマンドラインから使用できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-161">You can use them with Visual Studio or from the command line.</span></span> <span data-ttu-id="e826b-162">このアプリケーションは、.NET Core で実行され、Linux コンテナーを使用するため、Mac または Linux マシンでコーディング、ビルド、および実行できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-162">This application runs on .NET Core and uses Linux containers, so you can also code, build, and run on a Mac or on a Linux machine.</span></span>

<span data-ttu-id="e826b-163">docker-compose.yml ファイルには、どのようなイメージをビルドしてどのようなコンテナーを起動するかに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e826b-163">The docker-compose.yml file contains information about what images to build and what containers to launch.</span></span> <span data-ttu-id="e826b-164">テンプレートでは、eshopweb イメージを構築して、アプリケーションのコンテナーを起動する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e826b-164">The templates specify how to build the eshopweb image and launch the application’s containers.</span></span> <span data-ttu-id="e826b-165">依存関係のイメージ (たとえば mssql-server-linux) を含めることによって、SQL Server 上の依存関係を追加する必要があり、コンテナーをビルドして起動するために Docker 用の sql.data イメージのサービスを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-165">You need to add the dependency on SQL Server by including an image for it (for example, mssql-server-linux), and a service for the sql.data image for Docker to build and launch that container.</span></span> <span data-ttu-id="e826b-166">これらの設定を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e826b-166">These settings are shown in the following example:</span></span>

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

<span data-ttu-id="e826b-167">depends\_on ディレクティブは、eShopWeb イメージが sql.data イメージに依存することを Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="e826b-167">The depends\_on directive tells Docker that the eShopWeb image depends on the sql.data image.</span></span> <span data-ttu-id="e826b-168">その下の行は、microsoft/mssql-server-linux イメージ使用して、sql.data をターゲットとするイメージを構築する手順です。</span><span class="sxs-lookup"><span data-stu-id="e826b-168">Lines below that are the instructions to build an image tagged sql.data using the microsoft/mssql-server-linux image.</span></span>

<span data-ttu-id="e826b-169">**docker-compose** プロジェクトは、メインの docker-compose.yml ノードの下に他の docker-compose ファイルを表示し、これらのファイルが関連付けられていることを視覚的に示します。</span><span class="sxs-lookup"><span data-stu-id="e826b-169">The **docker-compose** project displays the other docker-compose files under the main docker-compose.yml node to provide a visual indication that these files are related.</span></span> <span data-ttu-id="e826b-170">docker-compose-override.yml ファイルには、接続文字列、他のアプリケーション設定などの両方のサービスの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e826b-170">The docker-compose-override.yml file contains settings for both services, such as connection strings and other application settings.</span></span>

<span data-ttu-id="e826b-171">次の例では、Visual Studio でのデバッグに使用される設定を含む docker compose.vs.debug.yml ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="e826b-171">The following example shows the docker-compose.vs.debug.yml file, which contains settings used for debugging in Visual Studio.</span></span> <span data-ttu-id="e826b-172">このファイルでは、eshopweb イメージに dev タグが追加されています。</span><span class="sxs-lookup"><span data-stu-id="e826b-172">In that file, the eshopweb image has the dev tag appended to it.</span></span> <span data-ttu-id="e826b-173">これは、リリース イメージからデバッグを分離するために役立ち、運用環境にデバッグ情報を誤って展開しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e826b-173">That helps separate debug from release images so that you do not accidentally deploy the debug information to a production environment:</span></span>

```yml
version: '2'
  
services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

<span data-ttu-id="e826b-174">追加された最後のファイルは、docker compose.ci.build.yml です。</span><span class="sxs-lookup"><span data-stu-id="e826b-174">The last file added is docker-compose.ci.build.yml.</span></span> <span data-ttu-id="e826b-175">これを、コマンドラインから使用し、CI サーバーからプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="e826b-175">This would be used from the command line to build the project from a CI server.</span></span> <span data-ttu-id="e826b-176">この構成ファイルでは、アプリケーションに必要なイメージを構築する Docker コンテナーを開始します。</span><span class="sxs-lookup"><span data-stu-id="e826b-176">This compose file starts a Docker container that builds the images needed for your application.</span></span> <span data-ttu-id="e826b-177">docker-compose.ci.build.yml ファイルの内容の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e826b-177">The following example shows the contents of the docker-compose.ci.build.yml file.</span></span>

```yml
version: '2'
  
services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

<span data-ttu-id="e826b-178">**注**: .NET Core 2.0 以降、dotnet 復元コマンドは、dotnet の発行が実行されるときに自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-178">**Note**: Starting with .NET Core 2.0, the dotnet restore command executes automatically when dotnet publish is executed.</span></span>

<span data-ttu-id="e826b-179">イメージは、ASP.NET Core ビルド イメージであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e826b-179">Notice that the image is an ASP.NET Core build image.</span></span> <span data-ttu-id="e826b-180">そのイメージには、アプリケーションをビルドし、必要なイメージを作成するための SDK とビルド ツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e826b-180">That image includes the SDK and build tools to build your application and create the required images.</span></span> <span data-ttu-id="e826b-181">このファイルを使用して、**docker-compose** プロジェクトを実行すると、イメージからビルド コンテナーが開始され、そのコンテナー内でアプリケーションのイメージが構築されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-181">Running the **docker-compose** project using this file starts the build container from the image, then builds your application’s image in that container.</span></span> <span data-ttu-id="e826b-182">その docker-compose ファイルをコマンドラインの一部として指定し、Docker コンテナーでアプリケーションをビルドしてからこれを起動します。</span><span class="sxs-lookup"><span data-stu-id="e826b-182">You specify that docker-compose file as part of the command line to build your application in a Docker container, then launch it.</span></span>

<span data-ttu-id="e826b-183">Visual Studio で、**docker-compose** プロジェクトをスタートアップ プロジェクトとして選択して、Docker コンテナーでアプリケーションを実行し、その後で他のアプリケーションと同じように、Ctrl キーを押しながら F5 キー (デバッグのための F5) を押すことができます。</span><span class="sxs-lookup"><span data-stu-id="e826b-183">In Visual Studio, you can run your application in Docker containers by selecting the **docker-compose** project as the startup project, and then pressing Ctrl+F5 (F5 to debug), as you can with any other application.</span></span> <span data-ttu-id="e826b-184">**docker-compose** プロジェクトを開始すると、Visual Studio が docker-compose.yml ファイル、docker-compose.override.yml ファイル、およびいずれかの docker-compose.vs.\* ファイルを使用して **docker-compose** を実行します。</span><span class="sxs-lookup"><span data-stu-id="e826b-184">When you start the **docker-compose** project, Visual Studio runs **docker-compose** using the docker-compose.yml file, the docker-compose.override.yml file, and one of the docker-compose.vs.\* files.</span></span> <span data-ttu-id="e826b-185">アプリケーションが開始されると、Visual Studio がブラウザーを起動します。</span><span class="sxs-lookup"><span data-stu-id="e826b-185">Once the application has started, Visual Studio launches the browser for you.</span></span>

<span data-ttu-id="e826b-186">デバッガーでアプリケーションを起動した場合、Visual Studio は、Docker で実行中のアプリケーションに接続します。</span><span class="sxs-lookup"><span data-stu-id="e826b-186">If you launch the application in the debugger, Visual Studio will attach to the running application in Docker.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e826b-187">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e826b-187">Troubleshooting</span></span>

<span data-ttu-id="e826b-188">このセクションでは、コンテナーをローカルで実行した場合に発生する可能性があるいくつかの問題と、推奨される解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e826b-188">This section describes a few issues that might arise when your run containers locally and suggests some fixes.</span></span>

### <a name="stopping-docker-containers"></a><span data-ttu-id="e826b-189">Docker コンテナーを停止する</span><span class="sxs-lookup"><span data-stu-id="e826b-189">Stopping Docker containers</span></span> 

<span data-ttu-id="e826b-190">コンテナー化アプリケーションを起動した後、デバッグを停止した後もコンテナーは引き続き実行されます。</span><span class="sxs-lookup"><span data-stu-id="e826b-190">After you launch the containerized application, the containers continue to run, even after you have stopped debugging.</span></span> <span data-ttu-id="e826b-191">コマンドラインから docker ps コマンドを実行し、どのコンテナーが実行されているを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e826b-191">You can run the docker ps command from the command line to see which containers are running.</span></span> <span data-ttu-id="e826b-192">docker stop コマンドは、図 6-2 に示すように、実行中のコンテナーを停止します。</span><span class="sxs-lookup"><span data-stu-id="e826b-192">The docker stop command stops a running container, as shown in Figure 6-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="e826b-193">**図 6-2**。</span><span class="sxs-lookup"><span data-stu-id="e826b-193">**Figure 6-2**.</span></span> <span data-ttu-id="e826b-194">docker ps および docker stop CLI コマンドを使用したコンテナーの一覧表示と停止</span><span class="sxs-lookup"><span data-stu-id="e826b-194">Listing and stopping containers with the docker ps and docker stop CLI commands</span></span>

<span data-ttu-id="e826b-195">場合によっては、さまざまな構成を切り替えるときにプロセスの実行を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-195">You might need to stop running processes when you switch between different configurations.</span></span> <span data-ttu-id="e826b-196">それ以外の場合、Web アプリケーションを実行しているコンテナーは、アプリケーション用のポート (この例では 5106) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e826b-196">Otherwise, the container that is running the web application is using the port for your application (5106 in this example).</span></span>

### <a name="adding-docker-to-your-projects"></a><span data-ttu-id="e826b-197">Docker をプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="e826b-197">Adding Docker to your projects</span></span>

<span data-ttu-id="e826b-198">Docker のサポートを追加するウィザードは、実行中の Docker プロセスと通信します。</span><span class="sxs-lookup"><span data-stu-id="e826b-198">The wizard that adds Docker support communicates with the running Docker process.</span></span> <span data-ttu-id="e826b-199">ウィザードを起動するときに、Docker が実行されていない場合、ウィザードは正しく実行されません。</span><span class="sxs-lookup"><span data-stu-id="e826b-199">The wizard will not run correctly if Docker is not running when you start the wizard.</span></span> <span data-ttu-id="e826b-200">さらに、ウィザードでは、正しい Docker のサポートを追加するためにコンテナーの現在の選択について説明します。</span><span class="sxs-lookup"><span data-stu-id="e826b-200">In addition, the wizard examines your current container choice to add the correct Docker support.</span></span> <span data-ttu-id="e826b-201">Windows コンテナーのサポートを追加する場合は、Windows コンテナーが構成された状態で Docker が実行されているときに、ウィザードを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-201">If you want to add support for Windows Containers, you need to run the wizard while you have Docker running with Windows Containers configured.</span></span> <span data-ttu-id="e826b-202">Linux コンテナーのサポートを追加する場合は、Linux コンテナーが構成された状態で Docker が実行されているときに、ウィザードを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e826b-202">If you want to add support for Linux containers, run the wizard while you have Docker running with Linux containers configured.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e826b-203">[Previous] (../docker-application-development-process/docker-app-development-workflow.md) [Next] (../containerize-net-framework-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e826b-203">[Previous] (../docker-application-development-process/docker-app-development-workflow.md) [Next] (../containerize-net-framework-applications/index.md)</span></span>
