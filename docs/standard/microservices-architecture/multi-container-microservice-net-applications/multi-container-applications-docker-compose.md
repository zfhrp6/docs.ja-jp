---
title: "Docker compose.yml でアプリケーションを複数のコンテナーを定義します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker compose.yml でアプリケーションを複数のコンテナーを定義します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c5d4d2c9fb9fbb595f6f6ea195247474f353a32f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="9676c-104">Docker compose.yml でアプリケーションを複数のコンテナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="9676c-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="9676c-105">このガイドで、 [docker compose.yml](https://docs.docker.com/compose/compose-file/)ファイルは、セクションで導入された[手順 4 です。複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスの定義](#step4_define_svcs_in_docker_compose_yml)です。</span><span class="sxs-lookup"><span data-stu-id="9676c-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="9676c-106">ただし、さらに詳しく検討する価値がある docker-compose ファイルを使用するその他の方法があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="9676c-107">たとえば、明示的に記述できます docker compose.yml ファイルで、複数のコンテナー アプリケーションを配置する方法。</span><span class="sxs-lookup"><span data-stu-id="9676c-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="9676c-108">必要に応じて、移動する、カスタムの Docker イメージを構築する方法を記述できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="9676c-109">(カスタム Docker images も構築できます Docker CLI を使用しています。)</span><span class="sxs-lookup"><span data-stu-id="9676c-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="9676c-110">基本的には、各コンテナーを展開すると各コンテナー展開の特定の特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="9676c-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="9676c-111">によってコーディネートされます。 1 つのアクションで全体のソリューションを配置することができます、複数のコンテナーの展開の記述ファイルを作成したら、[を docker 構成](https://docs.docker.com/compose/overview/)CLI コマンド、またはすることができます、透過的に Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9676c-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="9676c-112">それ以外の場合は Docker CLI を使用して、コマンドラインからコマンドを実行する、docker を使用して、複数の手順でコンテナーはコンテナーでを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="9676c-113">したがって、docker compose.yml で定義された各サービスはただ 1 つのイメージを指定またはビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="9676c-114">その他のキーはオプションであり、docker コマンド ライン古くての実行に似ています。</span><span class="sxs-lookup"><span data-stu-id="9676c-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="9676c-115">次の YAML コードは、eShopOnContainers サンプルの可能なグローバルが単一 docker-compose.yml ファイルの定義です。</span><span class="sxs-lookup"><span data-stu-id="9676c-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="9676c-116">EShopOnContainers から実際 docker-compose ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="9676c-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="9676c-117">最適なは、1 つのファイルに簡単で統合のバージョンでは代わりに、方法を使用する docker-構成ファイル、後で説明したようです。</span><span class="sxs-lookup"><span data-stu-id="9676c-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '2'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="9676c-118">このファイルのルート キーはサービスです。</span><span class="sxs-lookup"><span data-stu-id="9676c-118">The root key in this file is services.</span></span> <span data-ttu-id="9676c-119">配置および実行するときに実行するサービスを定義するキーの下で、コマンドまたはこの docker compose.yml ファイルを使用して Visual Studio からのデプロイを docker 構成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="9676c-120">この例では、docker compose.yml ファイルでは、次の一覧に示すように定義されている場合、複数のサービスがいます。</span><span class="sxs-lookup"><span data-stu-id="9676c-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="9676c-121">webmvc サーバー側 C から microservices を消費する ASP.NET Core MVC アプリケーションを含むコンテナー\#</span><span class="sxs-lookup"><span data-stu-id="9676c-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="9676c-122">catalog.api カタログ ASP.NET Core Web API マイクロ サービスを含むコンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="9676c-123">ordering.api ASP.NET Core Web API の順序付けマイクロ サービスを含むコンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="9676c-124">sql.data microservices データベースを保持して、Linux 用 SQL Server を実行中のコンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="9676c-125">バスケット ASP.NET Core Web API マイクロ サービスを basket.api コンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="9676c-126">basket.data REDIS キャッシュとしてバスケット データベースに REDIS cache サービスを実行中のコンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="9676c-127">単純な Web サービス API コンテナー</span><span class="sxs-lookup"><span data-stu-id="9676c-127">A simple Web Service API container</span></span>

<span data-ttu-id="9676c-128">1 つのコンテナーに焦点を当てた、catalog.api コンテナー マイクロ サービスを使うと、簡単な定義があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="9676c-129">このコンテナー サービスには、次の基本的な構成があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="9676c-130">カスタム eshop/catalog.api イメージに基づいています。</span><span class="sxs-lookup"><span data-stu-id="9676c-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="9676c-131">わかりやすくするために、ビルドはありません。 キー ファイルの設定。</span><span class="sxs-lookup"><span data-stu-id="9676c-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="9676c-132">つまり、イメージ必要がありますが既にビルドされて (docker ビルド) には任意の Docker レジストリから (コマンドを使用して、docker プル) ダウンロードされました。</span><span class="sxs-lookup"><span data-stu-id="9676c-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="9676c-133">カタログ データ モデルを含む SQL Server インスタンスにアクセスする Entity Framework で使用する接続文字列の ConnectionString をという名前の環境変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="9676c-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="9676c-134">この場合、同じ SQL Server のコンテナーには、複数のデータベースが保持しています。</span><span class="sxs-lookup"><span data-stu-id="9676c-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="9676c-135">したがってより少ないメモリは、Docker 用に開発用コンピューターで必要。</span><span class="sxs-lookup"><span data-stu-id="9676c-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="9676c-136">ただし、マイクロ サービス データベースごとに 1 つの SQL Server のコンテナーを展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="9676c-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="9676c-137">SQL Server 名は sql.data、Linux 用 SQL Server インスタンスが実行されているコンテナーで使用される同じ名前です。</span><span class="sxs-lookup"><span data-stu-id="9676c-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="9676c-138">これは、方法は便利です。この名前解決 (内部、Docker ホストへ) を使用できることを他のコンテナーにアクセスするコンテナーの内部 ip アドレスを知る必要はありません、ネットワーク アドレスが解決されます。</span><span class="sxs-lookup"><span data-stu-id="9676c-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="9676c-139">接続文字列が環境変数で定義されているため、別のメカニズムを使用し、別の時点でその変数を設定する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="9676c-140">たとえば、最終的なホスト、または VSTS または優先 DevOps システムで、構成項目/CD パイプラインから手順を実行して、実稼働環境に展開するときに、別の接続文字列を設定できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="9676c-141">内部サービスへのアクセス、catalog.api Docker ホスト内でポート 80 を公開します。</span><span class="sxs-lookup"><span data-stu-id="9676c-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="9676c-142">ホストは、Linux VM では現在 for Linux Docker イメージ上に基づきますが、代わりに、Windows イメージ上で実行するコンテナーを構成することもあるためです。</span><span class="sxs-lookup"><span data-stu-id="9676c-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="9676c-143">公開されているポート 80、Docker ホスト コンピューター (Linux VM) にポート 5101 コンテナー上を転送します。</span><span class="sxs-lookup"><span data-stu-id="9676c-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="9676c-144">Web サービスを sql.data サービス (コンテナーで実行されている Linux データベースの SQL Server のインスタンス) にリンクします。</span><span class="sxs-lookup"><span data-stu-id="9676c-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="9676c-145">この依存関係を指定すると、catalog.api コンテナーまでは起動しません sql.data コンテナーが既に開始します。これは重要なは、SQL Server データベースでセットアップを catalog.api 必要があるためされ実行されている最初です。</span><span class="sxs-lookup"><span data-stu-id="9676c-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="9676c-146">ただし、このようなコンテナーの依存関係は、不十分多くの場合、Docker は、コンテナー レベルでのみチェックがあるためです。</span><span class="sxs-lookup"><span data-stu-id="9676c-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="9676c-147">場合があります (このケースの SQL Server) でサービスされませんがあります対応、ために、クライアント microservices 指数バックオフによる再試行ロジックを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9676c-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="9676c-148">このように、依存関係のコンテナーが短時間では、準備されていない場合、アプリケーションは引き続きできます回復力のあります。</span><span class="sxs-lookup"><span data-stu-id="9676c-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="9676c-149">外部サーバーへのアクセスを許可するように構成されます: 余分な\_ホストの設定では、外部のサーバーまたは Docker ホストの外部でのマシンにアクセスすることができます (つまり、既定値は開発 Docker Linux VM の外部ホスト)、ローカルの SQL など開発 PC 上のサーバー インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="9676c-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="9676c-150">またより高度な docker compose.yml 設定が、以下のセクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9676c-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="9676c-151">使用して docker の構成ファイルを複数の環境を対象とする</span><span class="sxs-lookup"><span data-stu-id="9676c-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="9676c-152">Docker compose.yml ファイルは、定義ファイルし、その形式を理解している複数のインフラストラクチャで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="9676c-153">最も簡単なツールは、docker にコマンドの作成が、(たとえば、Docker Swarm) orchestrators も理解してそのファイルと同じようにその他のツールです。</span><span class="sxs-lookup"><span data-stu-id="9676c-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="9676c-154">使用して、そのため、docker の構成コマンドを次の主なシナリオを対象にできます。</span><span class="sxs-lookup"><span data-stu-id="9676c-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="9676c-155">開発環境</span><span class="sxs-lookup"><span data-stu-id="9676c-155">Development environments</span></span>

<span data-ttu-id="9676c-156">アプリケーションを開発するときに、分離開発環境でアプリケーションを実行できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="9676c-157">使用することができます、docker-作成 CLI コマンドをその環境を作成または使用して docker-を構成するは背後で Visual Studio を使用します。</span><span class="sxs-lookup"><span data-stu-id="9676c-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="9676c-158">Docker compose.yml ファイルを使用すると、構成およびすべてのアプリケーションのサービスの依存関係 (その他のサービス、キャッシュ、データベース、キューなど) を文書化できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="9676c-159">使用して、CLI コマンドを docker 構成、作成して 1 つのコマンドを使用してそれぞれの依存関係の 1 つまたは複数のコンテナーを開始 (docker で作成する)。</span><span class="sxs-lookup"><span data-stu-id="9676c-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="9676c-160">Docker compose.yml は Docker エンジンによって解釈される構成ファイルが、複数のコンテナー アプリケーションの構成に関する便利なドキュメント ファイルとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="9676c-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="9676c-161">テスト環境</span><span class="sxs-lookup"><span data-stu-id="9676c-161">Testing environments</span></span>

<span data-ttu-id="9676c-162">継続的なデプロイ (CD) や継続的インテグレーション (CI) プロセスの重要な部分は、単体テストおよび統合テストです。</span><span class="sxs-lookup"><span data-stu-id="9676c-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="9676c-163">これらの自動テストでは、これらは、ユーザーまたはアプリケーションのデータに他の変更による影響を受けませんように分離された環境が必要です。</span><span class="sxs-lookup"><span data-stu-id="9676c-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="9676c-164">Docker Compose によるを作成してから、コマンド プロンプトまたはスクリプトは、次のコマンドと同様に、いくつかのコマンドで非常に簡単に分離された環境を破棄します。</span><span class="sxs-lookup"><span data-stu-id="9676c-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="9676c-165">運用展開</span><span class="sxs-lookup"><span data-stu-id="9676c-165">Production deployments</span></span>

<span data-ttu-id="9676c-166">リモート Docker エンジンを展開する構成を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="9676c-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="9676c-167">一般的なケースは、1 つの Docker ホスト インスタンスを展開する (実稼働 VM またはサーバーを使用してプロビジョニング[Docker マシン](https://docs.docker.com/machine/overview/))。</span><span class="sxs-lookup"><span data-stu-id="9676c-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="9676c-168">全体の場合もありますが、 [Docker Swarm](https://docs.docker.com/swarm/overview/)クラスター、クラスターは、docker compose.yml ファイルとの互換性もあるためです。</span><span class="sxs-lookup"><span data-stu-id="9676c-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="9676c-169">その他の orchestrator (Azure Service Fabric、Mesos DC/OS、Kubernetes など) を使用している場合は、docker compose.yml、でもは他の orchestrator で必要な形式のものと同様のセットアップとメタデータの構成設定を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="9676c-170">いずれの場合は、docker の構成で開発、テスト、運用環境のワークフローの場合に便利なツールとメタデータ形式が使用して orchestrator を運用環境のワークフローが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="9676c-171">複数を使用して docker の構成ファイルを複数の環境を処理するには</span><span class="sxs-lookup"><span data-stu-id="9676c-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="9676c-172">さまざまな環境を対象とする場合は、複数を使用する必要がありますファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="9676c-173">これにより、環境に応じて複数の構成バリアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="9676c-174">基本 docker-compose ファイルを上書き</span><span class="sxs-lookup"><span data-stu-id="9676c-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="9676c-175">前のセクションで示すように簡略化された例のように、1 つの docker compose.yml ファイルを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="9676c-176">ただし、ほとんどのアプリケーションは推奨はされません。</span><span class="sxs-lookup"><span data-stu-id="9676c-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="9676c-177">既定では、新規作成は、2 つのファイル、docker compose.yml および省略可能な docker compose.override.yml ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="9676c-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="9676c-178">ように図 8-11 では、Visual Studio を使用する Docker のサポートを有効にすると、Visual Studio もが作成されるとそれらのファイルとその他のファイルのデバッグに使用します。</span><span class="sxs-lookup"><span data-stu-id="9676c-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates those files plus some additional files used for debugging.</span></span>

![](./media/image12.png)

<span data-ttu-id="9676c-179">**図 8. ~ 11.**です。</span><span class="sxs-lookup"><span data-stu-id="9676c-179">**Figure 8-11**.</span></span> <span data-ttu-id="9676c-180">Visual Studio 2017 内のファイルを docker 構成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="9676c-181">Visual Studio Code または Sublime などの任意のエディター docker-compose ファイルを編集し、アプリケーションを実行することができます、docker 構成コマンドします。</span><span class="sxs-lookup"><span data-stu-id="9676c-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="9676c-182">慣例により、docker compose.yml ファイルには、基本の構成とその他の静的な設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9676c-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="9676c-183">つまり、サービスの構成が対象となる展開環境に合わせて変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="9676c-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="9676c-184">Docker compose.override.yml ファイルには名前が示すように、デプロイ環境に依存するための構成など、基本構成をオーバーライドする構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9676c-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="9676c-185">また複数のオーバーライド ファイルを異なる名前を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9676c-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="9676c-186">通常、オーバーライド ファイルには、環境または展開には特定のアプリケーションで必要な追加の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9676c-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="9676c-187">複数の環境を対象とします。</span><span class="sxs-lookup"><span data-stu-id="9676c-187">Targeting multiple environments</span></span>

<span data-ttu-id="9676c-188">一般的なユース ケースが複数定義するときに作成ファイル CI、または開発、ステージング、実稼働環境でのように、複数の環境を対象できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9676c-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="9676c-189">これらの相違点をサポートするためには、図 8-12 を示すように、複数のファイルを作成する構成を分割できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="9676c-190">**図 8-12**です。</span><span class="sxs-lookup"><span data-stu-id="9676c-190">**Figure 8-12**.</span></span> <span data-ttu-id="9676c-191">複数の docker 構成ファイルの基本の docker compose.yml ファイル内の値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9676c-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="9676c-192">基本の docker compose.yml ファイルから開始できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="9676c-193">この基本ファイルに、環境に合わせて変更されないベース、または静的な構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9676c-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="9676c-194">たとえば、eShopOnContainers では、基本ファイルとして次の docker compose.yml ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="9676c-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '2'

services:
  basket.api:
    image: eshop/basket.api
    build:
    context: ./src/Services/Basket/Basket.API
    dockerfile: Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api
    build:
    context: ./src/Services/Catalog/Catalog.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  identity.api:
    image: eshop/identity.api
    build:
    context: ./src/Services/Identity/Identity.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    build:
    context: ./src/Services/Ordering/Ordering.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  webspa:
    image: eshop/webspa
    build:
    context: ./src/Web/WebSPA
    dockerfile: Dockerfile
    depends_on:
      - identity.api
      - basket.api

  webmvc:
    image: eshop/webmvc
    build:
    context: ./src/Web/WebMVC
    dockerfile: Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api

  sql.data:
    image: microsoft/mssql-server-linux
    basket.data:
    image: redis
    expose:
      - "6379"
    rabbitmq:
    image: rabbitmq
    ports:
      - "5672:5672"

  webstatus:
    image: eshop/webstatus
    build:
    context: ./src/Web/WebStatus
    dockerfile: Dockerfile
```

<span data-ttu-id="9676c-195">基本 docker compose.yml ファイル内の値が別のターゲット展開環境のために変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="9676c-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="9676c-196">たとえば、webmvc サービス定義に注目する場合、その情報は、どのような環境を対象とする可能性がありますに関係なくほとんど同じ方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="9676c-197">次の情報があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-197">You have the following information:</span></span>

-   <span data-ttu-id="9676c-198">サービス名: webmvc です。</span><span class="sxs-lookup"><span data-stu-id="9676c-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="9676c-199">コンテナーのカスタム イメージ: eshop/webmvc です。</span><span class="sxs-lookup"><span data-stu-id="9676c-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="9676c-200">どの Dockerfile を使用することを示すカスタムの Docker イメージを構築するコマンドです。</span><span class="sxs-lookup"><span data-stu-id="9676c-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="9676c-201">他の依存関係のコンテナーが開始されるまで、このコンテナーが開始しないように、他のサービスに依存します。</span><span class="sxs-lookup"><span data-stu-id="9676c-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="9676c-202">追加の構成を持つことができますが、重要な点は、基本の docker compose.yml ファイルでだけします環境間で共通する情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="9676c-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="9676c-203">Docker compose.override.yml または実稼働またはステージングの同様のファイルで、各環境に固有の構成を配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="9676c-204">通常、docker compose.override.yml は eShopOnContainers から次の例のように、開発環境に合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="9676c-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '2'

services:
# Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database=Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Pass@word
      - ExternalCatalogBaseUrl=http://localhost:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:5105
    - SpaClient=http://localhost:5104
    - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
    - MvcClient=http://localhost:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://localhost:5101
      - OrderingUrl=http://localhost:5102
      - IdentityUrl=http://localhost:5105
      - BasketUrl=http:// localhost:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="9676c-205">この例では開発の構成の上書きをホストにいくつかのポートを公開する、定義環境変数をリダイレクト Url、および開発環境の接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="9676c-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="9676c-206">これらの設定だけは、開発環境です。</span><span class="sxs-lookup"><span data-stu-id="9676c-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="9676c-207">実行すると、上の docker 構成 (または Visual Studio から起動)、コマンドの読み込みのオーバーライドに自動的に両方のファイルをマージした場合、します。</span><span class="sxs-lookup"><span data-stu-id="9676c-207">When you run docker-compose up (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="9676c-208">別の構成値を持つ、運用環境の別の構成ファイルを表示するとします。</span><span class="sxs-lookup"><span data-stu-id="9676c-208">Suppose that you want another Compose file for the production environment, with different configuration values.</span></span> <span data-ttu-id="9676c-209">次のように、別のオーバーライド ファイルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="9676c-209">You can create another override file, like the following.</span></span> <span data-ttu-id="9676c-210">(このファイル可能性がありますを別の Git リポジトリに格納されているか、管理および保護別のチームによって。)</span><span class="sxs-lookup"><span data-stu-id="9676c-210">(This file might be stored in a different Git repo or managed and secured by a different team.)</span></span>

```yml
#docker-compose.prod.yml (Extended config for PRODUCTION env.)
version: '2'

services:
  # Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database = Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Prod@Pass
      - ExternalCatalogBaseUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5105
      - SpaClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5104
      - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
      - MvcClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT= Production
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
      - OrderingUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5102
      - IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
      - BasketUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Prod@Pass
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="9676c-211">特定のオーバーライド ファイルと共に展開する方法</span><span class="sxs-lookup"><span data-stu-id="9676c-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="9676c-212">を別の名前で複数のオーバーライド ファイル、またはオーバーライド ファイルを使用するのには、で-f オプションを使用することができます、docker にコマンドを作成し、ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="9676c-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="9676c-213">コマンドラインで指定された順序でマージ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="9676c-214">次の例では、上書きファイルと共に展開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9676c-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="9676c-215">環境変数の使用の docker の構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9676c-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="9676c-216">特におが前の例に示すように、環境変数から構成情報を取得できる、実稼働環境では、便利です。</span><span class="sxs-lookup"><span data-stu-id="9676c-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="9676c-217">構文を使用して、docker-compose ファイルで環境変数を参照する\${MY\_VAR}。</span><span class="sxs-lookup"><span data-stu-id="9676c-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="9676c-218">Docker compose.prod.yml ファイルから次の行は、環境変数の値を参照する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9676c-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="9676c-219">環境変数が作成され、ホスト環境に応じて、さまざまな方法で初期化 (Linux、Windows、クラウド クラスターなどです。)。</span><span class="sxs-lookup"><span data-stu-id="9676c-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="9676c-220">ただし、便利な方法では、.env ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9676c-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="9676c-221">Docker-compose ファイルは、.env ファイルで既定の環境変数を宣言することをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9676c-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="9676c-222">これらの環境変数の値は、既定値です。</span><span class="sxs-lookup"><span data-stu-id="9676c-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="9676c-223">それぞれ自分の環境の (ホスト OS またはクラスターから環境変数) で定義した値によってオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="9676c-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="9676c-224">この .env ファイル、フォルダーに配置する場所、docker 構成からコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9676c-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="9676c-225">次の例は、.env ファイルと同様に、 [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers アプリケーション用のファイルです。</span><span class="sxs-lookup"><span data-stu-id="9676c-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="9676c-226">必要ですが、.env ファイルの形式での各行の docker 構成&lt;変数&gt;=&lt;値&gt;です。</span><span class="sxs-lookup"><span data-stu-id="9676c-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="9676c-227">常に、ランタイム環境で設定された値が .env ファイル内で定義されている値をオーバーライドすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9676c-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="9676c-228">同様の方法で、コマンド ライン コマンド引数を介して渡される値は、.env ファイルで設定された既定値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9676c-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9676c-229">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9676c-229">Additional resources</span></span>

-   <span data-ttu-id="9676c-230">**Docker の概要作成**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="9676c-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="9676c-231">**複数の構成ファイル**
    [*https://docs.docker.com/compose/extends/\#複数を構成ファイル*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="9676c-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="9676c-232">ビルドは、ASP.NET Core Docker イメージを最適化します。</span><span class="sxs-lookup"><span data-stu-id="9676c-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="9676c-233">Docker と .NET Core は、インターネット上のソースの検索は、Dockerfile を示す、わかりやすくするためのコンテナーに、ソースをコピーして、Docker イメージの構築が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9676c-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="9676c-234">これらの例では、単純な構成を使用するはできること、Docker イメージでは、アプリケーションにパッケージ化、環境を提案します。</span><span class="sxs-lookup"><span data-stu-id="9676c-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="9676c-235">次の例では、このに簡単な Dockerfile を示します。</span><span class="sxs-lookup"><span data-stu-id="9676c-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="9676c-236">次のように、Dockerfile は動作します。</span><span class="sxs-lookup"><span data-stu-id="9676c-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="9676c-237">ただし、特に実稼働イメージ、イメージを大幅に最適化できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="9676c-238">コンテナーと microservices モデルでは、コンテナー継続的に開始します。</span><span class="sxs-lookup"><span data-stu-id="9676c-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="9676c-239">コンテナーの使用の一般的な方法では、コンテナーが破棄可能なために、スリープ状態のコンテナーは再起動しません。</span><span class="sxs-lookup"><span data-stu-id="9676c-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="9676c-240">Orchestrators (Docker Swarm、Kubernetes、DCOS または Azure Service Fabric) などは、単に、イメージの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="9676c-241">これは意味をインスタンス化のプロセスが向上するためのビルド時にアプリケーションをプリコンパイル最適化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="9676c-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="9676c-242">コンテナーが開始されるは、実行できる状態にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9676c-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="9676c-243">ない復元し、実行時にコンパイルする必要があります、ビルドを使用した dotnet 復元と dotnet dotnet CLI からコマンドを .NET Core と Docker に関する多くのブログ投稿でします。</span><span class="sxs-lookup"><span data-stu-id="9676c-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="9676c-244">.NET チームに .NET Core と ASP.NET Core コンテナー用に最適化されたフレームワークを作成する重要な作業を行っています。</span><span class="sxs-lookup"><span data-stu-id="9676c-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="9676c-245">.NET Core は小規模メモリ フット プリント; を使用して軽量の framework だけでなく、します。チームが起動時のパフォーマンスに重点を置いて、ような一部の最適化の Docker イメージを生成、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)で使用できるイメージ[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)、比較、正規[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)または[microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile)イメージ。</span><span class="sxs-lookup"><span data-stu-id="9676c-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="9676c-246">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) aspnetcore の自動設定を提供するイメージ\_url のポート 80 およびアセンブリの事前 ngend キャッシュに高速スタートアップと、これら両方の設定。</span><span class="sxs-lookup"><span data-stu-id="9676c-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9676c-247">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9676c-247">Additional resources</span></span>

-   <span data-ttu-id="9676c-248">**ビルド最適化 ASP.NET Core を使用してイメージを Docker**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="9676c-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="9676c-249">ビルド (CI) のコンテナーからのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="9676c-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="9676c-250">Docker のもう 1 つの利点は、事前に構成されたコンテナーからアプリケーションをビルドすることができます図 8-13 のため、ビルド コンピューターまたはアプリケーションをビルドする VM を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9676c-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="9676c-251">使用したり、開発用コンピューターで実行してそのビルド コンテナーをテストできます。</span><span class="sxs-lookup"><span data-stu-id="9676c-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="9676c-252">新機能が、もっと興味深い CI (継続的インテグレーション) パイプラインから同じビルド コンテナーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9676c-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="9676c-253">**図 8-13**です。</span><span class="sxs-lookup"><span data-stu-id="9676c-253">**Figure 8-13**.</span></span> <span data-ttu-id="9676c-254">コンポーネントをコンテナーから .NET ビットの構築</span><span class="sxs-lookup"><span data-stu-id="9676c-254">Components building .NET bits from a container</span></span>

<span data-ttu-id="9676c-255">このシナリオでは、説明、 [microsoft/aspnetcore-ビルド](https://hub.docker.com/r/microsoft/aspnetcore-build/)イメージで、コンパイルし、ASP.NET Core アプリケーションの構築に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9676c-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="9676c-256">基づくイメージで出力を配置、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)前述のとおり、実行時の最適化されたイメージのイメージです。</span><span class="sxs-lookup"><span data-stu-id="9676c-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="9676c-257">Aspnetcore ビルド イメージには、.NET Core では、ASP.NET の SDK、npm など、ASP.NET Core アプリケーションをコンパイルするために必要なものが含まれている Bower、Gulp などです。</span><span class="sxs-lookup"><span data-stu-id="9676c-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="9676c-258">ビルド時にこれらの依存関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="9676c-258">We need these dependencies at build time.</span></span> <span data-ttu-id="9676c-259">たくないアプリケーションでこれらを実行時に実行するために、イメージが不必要に大きなためです。</span><span class="sxs-lookup"><span data-stu-id="9676c-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="9676c-260">EShopOnContainers アプリケーションでは、アプリケーションをビルドすることができます、コンテナーだけを実行してから、次 docker-作成コマンド。</span><span class="sxs-lookup"><span data-stu-id="9676c-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="9676c-261">図 8-14 では、コマンドラインで実行されているこのコマンドを示します。</span><span class="sxs-lookup"><span data-stu-id="9676c-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="9676c-262">**図 8-14 です。**</span><span class="sxs-lookup"><span data-stu-id="9676c-262">**Figure 8-14.**</span></span> <span data-ttu-id="9676c-263">コンテナーから .NET アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="9676c-263">Building your .NET application from a container</span></span>

<span data-ttu-id="9676c-264">実行しているコンテナーが ci ビルドがわかるように、\_1 のコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="9676c-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="9676c-265">これは、コンパイル、お使いの PC からの代わりにそのコンテナー内からアプリケーション全体をビルドできるように、aspnetcore ビルド イメージに基づいています。</span><span class="sxs-lookup"><span data-stu-id="9676c-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="9676c-266">理由は実際にはビルドおり Linux での .NET Core プロジェクトをコンパイルする、そのコンテナーが既定の Docker Linux ホストで実行されているためです。</span><span class="sxs-lookup"><span data-stu-id="9676c-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="9676c-267">[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml)ファイルは、そのイメージ (eShopOnContainers の一部) には、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9676c-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="9676c-268">ビルド コンテナーを使用して、開始されるを参照してください、 [microsoft/aspnetcore-ビルド](https://hub.docker.com/r/microsoft/aspnetcore-build/)イメージ。</span><span class="sxs-lookup"><span data-stu-id="9676c-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '2'
  services:
    ci-build:
      image: microsoft/aspnetcore-build:1.0-1.1
      volumes:
        - .:/src
      working_dir: /src
      command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && pushd ./../../.. && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"
```

* <span data-ttu-id="9676c-269">以降で**.NET Core 2.0**、`dotnet restore`コマンドが自動的に実行されるときに、`dotnet publish`コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9676c-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="9676c-270">ビルド コンテナーが起動して稼働すると、.NET SDK dotnet 復元を実行し、dotnet は、.NET ビットをコンパイルするために、ソリューションのすべてのプロジェクトに対してコマンドを発行します。</span><span class="sxs-lookup"><span data-stu-id="9676c-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="9676c-271">この場合、eShopOnContainers では、クライアント コードの TypeScript および角に基づく、SPA もが、必要もあります npm での JavaScript の依存関係を確認するアクションが .NET bits に関連していないことがします。</span><span class="sxs-lookup"><span data-stu-id="9676c-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="9676c-272">Dotnet コマンド ビルドを発行する各プロジェクトのフォルダー内でコンパイルされた出力を発行していく、.図 8-15 を示す/obj/Docker/publish フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="9676c-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="9676c-273">**図 8 ~ 15 です。**</span><span class="sxs-lookup"><span data-stu-id="9676c-273">**Figure 8-15.**</span></span> <span data-ttu-id="9676c-274">バイナリ ファイルが、dotnet によって生成されたコマンドを発行します。</span><span class="sxs-lookup"><span data-stu-id="9676c-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="9676c-275">CLI から Docker イメージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="9676c-276">(各プロジェクトの場合) 内の関連するフォルダーに、アプリケーションの出力を発行すると、次の手順は、実際に Docker イメージを作成するは。</span><span class="sxs-lookup"><span data-stu-id="9676c-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="9676c-277">これを行うには、docker-compose ビルドを使用して、docker の構成コマンドを図 8 ~ 16 が示すようにします。</span><span class="sxs-lookup"><span data-stu-id="9676c-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="9676c-278">**図 8 ~ 16 です。**</span><span class="sxs-lookup"><span data-stu-id="9676c-278">**Figure 8-16.**</span></span> <span data-ttu-id="9676c-279">Docker イメージを構築して、コンテナーを実行しています。</span><span class="sxs-lookup"><span data-stu-id="9676c-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="9676c-280">図 8-17、docker-compose がコマンドの実行を構築する方法を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9676c-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="9676c-281">**図 8-17**です。</span><span class="sxs-lookup"><span data-stu-id="9676c-281">**Figure 8-17**.</span></span> <span data-ttu-id="9676c-282">Docker と Docker イメージを構築する-ビルド コマンドの作成</span><span class="sxs-lookup"><span data-stu-id="9676c-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="9676c-283">Docker-compose 間の違いは、ビルドおよびを docker 構成コマンドは、docker のビルドと開始のイメージの両方を作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="9676c-284">Visual Studio を使用すると、これらすべての手順は内部で実行されます。</span><span class="sxs-lookup"><span data-stu-id="9676c-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="9676c-285">Visual Studio、.NET アプリケーションをコンパイルするには、Docker イメージを作成および Docker ホストに、コンテナーを展開します。</span><span class="sxs-lookup"><span data-stu-id="9676c-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="9676c-286">Visual Studio では、Visual Studio から直接、Docker で実行されているのコンテナーをデバッグする機能など、追加の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9676c-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="9676c-287">全体的な takeway をここでは、CI/CD パイプラインが構築する必要がある方法と同じようにアプリケーションをビルドできる: の代わりにローカル コンピューターからのコンテナーからです。</span><span class="sxs-lookup"><span data-stu-id="9676c-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="9676c-288">イメージを作成した後、だけ実行する必要が、docker を使用して、Docker イメージのコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="9676c-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9676c-289">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="9676c-289">Additional resources</span></span>

-   <span data-ttu-id="9676c-290">**コンテナーからのビットを構築します Windows CLI 環境 (dotnet CLI、Docker CLI と VS Code) で eShopOnContainers ソリューションをセットアップ**
    [*https://github.com/dotnet/eShopOnContainers/wiki/。03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="9676c-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="9676c-291">[前](データのドリブン-crud-microservice.md) [次へ] (データベース サーバー container.md)</span><span class="sxs-lookup"><span data-stu-id="9676c-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
