---
title: docker-compose.yml で複数のコンテナー アプリケーションを定義する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | docker-compose.yml で複数のコンテナー アプリケーションを定義する'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 430fbe3fc6d63fd3b90b578f32b42831c368ba10
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106305"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="8668d-103">docker-compose.yml で複数のコンテナー アプリケーションを定義する</span><span class="sxs-lookup"><span data-stu-id="8668d-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="8668d-104">このガイドでは、[docker-compose.yml](https://docs.docker.com/compose/compose-file/) ファイルは、「[手順 4 複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスを定義します](#step4_define_svcs_in_docker_compose_yml)」セクションで導入されました。</span><span class="sxs-lookup"><span data-stu-id="8668d-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="8668d-105">しかし、docker-compose ファイルには他の使い方もあり、さらに詳しく検討する価値があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="8668d-106">たとえば、マルチコンテナー アプリケーションの展開方法を、docker-compose.yml ファイルで明示的に記述することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="8668d-107">必要に応じて、カスタム Docker イメージのビルド方法も記述できます </span><span class="sxs-lookup"><span data-stu-id="8668d-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="8668d-108">(カスタム Docker イメージは、Docker CLI を使用してビルドすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="8668d-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="8668d-109">基本的には、展開する各コンテナーを定義することに加え、各コンテナー展開に対して特定の特性も定義します。</span><span class="sxs-lookup"><span data-stu-id="8668d-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="8668d-110">マルチコンテナー展開の記述ファイルを作成したら、全体のソリューションを、[docker-compose up](https://docs.docker.com/compose/overview/) CLI コマンドで調整された 1 つのアクションで展開することができます。または、Visual Studio から透過的に展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="8668d-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="8668d-111">それ以外の場合は、Docker CLI を使用して、コマンドラインから docker run コマンドを使用して、複数の手順でコンテナーごとに展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="8668d-112">そのため、docker-compose.yml で定義された各サービスは、イメージまたはビルドを 1 つだけ指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="8668d-113">その他のキーは省略可能で、その対応する docker run コマンド ラインと似ています。</span><span class="sxs-lookup"><span data-stu-id="8668d-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="8668d-114">次の YAML コードは、グローバルに使用できる定義ですが、eShopOnContainers サンプル用の 1 つの docker-compose.yml ファイルです。</span><span class="sxs-lookup"><span data-stu-id="8668d-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="8668d-115">これは eShopOnContainers からの実際の docker-compose ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="8668d-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="8668d-116">むしろ、簡素化され、1 つのファイルに統合されたバージョンです。後述しますが、これは docker-compose ファイルで使用するには最善の方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="8668d-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="8668d-117">このファイルのルート キーはサービスです。</span><span class="sxs-lookup"><span data-stu-id="8668d-117">The root key in this file is services.</span></span> <span data-ttu-id="8668d-118">そのキーの下で、docker-compose up コマンドを実行する場合、または docker-compose.yml ファイルを使用して Visual Studio から展開する場合に、展開および実行するサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="8668d-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="8668d-119">この例では、次の一覧に示すように、docker-compose.yml ファイルには複数の定義済みのサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="8668d-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="8668d-120">サーバー側 C\# からマイクロサービスを消費する ASP.NET Core MVC アプリケーションを含む webmvc コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="8668d-121">Catalog ASP.NET Core Web API マイクロサービスを含む catalog.api コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="8668d-122">Ordering ASP.NET Core Web API マイクロサービスを含む ordering.api コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="8668d-123">マイクロサービス データベースを保持する、SQL Server for Linux を実行する sql.data コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="8668d-124">basket.api コンテナーと Basket ASP.NET Core Web API マイクロサービス</span><span class="sxs-lookup"><span data-stu-id="8668d-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="8668d-125">REDIS キャッシュ サービスを実行し、REDIS キャッシュとしてバスケット データベースを持つ basket.data コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="8668d-126">単純な Web サービス API コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-126">A simple Web Service API container</span></span>

<span data-ttu-id="8668d-127">1 つのコンテナーに集中することで、catalog.api container-microservice の定義が単純になります。</span><span class="sxs-lookup"><span data-stu-id="8668d-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="8668d-128">このコンテナー化されたサービスには、次の基本的な構成があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="8668d-129">カスタムの eshop/catalog.api イメージに基づいています。</span><span class="sxs-lookup"><span data-stu-id="8668d-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="8668d-130">わかりやすくするために、ファイル内にビルドやキーの設定はありません。</span><span class="sxs-lookup"><span data-stu-id="8668d-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="8668d-131">つまりイメージが、(docker build を使用して) 既にビルドされているか、(docker pull コマンドを使用して) 任意の Docker レジストリからダウンロードされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="8668d-132">接続文字列を使用して ConnectionString という名前の環境変数を定義します。この変数は、カタログ データ モデルを含む SQL Server インスタンスにアクセスするために Entity Framework によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="8668d-133">この例では、同じ SQL Server コンテナーに複数のデータベースが保持されています。</span><span class="sxs-lookup"><span data-stu-id="8668d-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="8668d-134">そのため、Docker 用に開発用コンピューターで必要なメモリ量が減ります。</span><span class="sxs-lookup"><span data-stu-id="8668d-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="8668d-135">ただし、マイクロサービス データベースごとに 1 つの SQL Server のコンテナーを展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="8668d-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="8668d-136">SQL Server 名は sql.data で、Linux の SQL Server インスタンスが実行されているコンテナーで使用されているのと同じ名前です。</span><span class="sxs-lookup"><span data-stu-id="8668d-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="8668d-137">これは便利な方法です。この名前解決 (内部から Docker ホストへ) を使用できることで、ネットワーク アドレスが解決されるため、他のコンテナーからアクセスするコンテナーの内部 IP アドレスを知る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8668d-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="8668d-138">接続文字列は環境変数によって定義されるため、異なる時点で別のメカニズムを使用して、その変数を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="8668d-139">たとえば、最後のホストで運用に展開するときに、または VSTS の CI/CD パイプラインから、または優先する DevOps システムから、別の接続文字列を設定できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="8668d-140">Docker ホスト内で catalog.api サービスへの内部アクセス用に、ポート 80 を公開します。</span><span class="sxs-lookup"><span data-stu-id="8668d-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="8668d-141">ホストは、Linux の Docker イメージに基づいているため、現在は Linux VM ですが、代わりに Windows イメージ上で実行するようにコンテナーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8668d-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="8668d-142">コンテナー上で公開されているポート 80 を、Docker ホスト コンピューター (Linux VM) 上のポート 5101 に転送します。</span><span class="sxs-lookup"><span data-stu-id="8668d-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="8668d-143">Web サービスを sql.data サービス (コンテナーで実行されている Linux データベースの SQL Server インスタンス) にリンクします。</span><span class="sxs-lookup"><span data-stu-id="8668d-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="8668d-144">この依存関係を指定すると、catalog.api コンテナーは、sql.data コンテナーが起動するまで起動しなくなります。これが重要なのは、catalog.api には、SQL Server データベースが先に起動していて、実行されている必要があるからです。</span><span class="sxs-lookup"><span data-stu-id="8668d-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="8668d-145">ただし、このようなコンテナーの依存関係は、Docker がコンテナー レベルでしかチェックしないため、多くの場合、不十分です。</span><span class="sxs-lookup"><span data-stu-id="8668d-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="8668d-146">サービス (この場合は SQL Server) がまだ準備できていない場合もあるため、クライアント マイクロサービスで指数バックオフによる再試行ロジックを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8668d-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="8668d-147">そうすることで、依存関係のコンテナーが少しの間、準備できない場合でも、アプリケーションが回復力を保つことができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="8668d-148">外部サーバーへのアクセスを許可するように構成されます: extra\_hosts 設定により、開発 PC 上のローカル SQL Server インスタンスなど、外部サーバーまたは Docker ホストの外部のマシン (つまり、開発 Docker ホストである既定の Linux VM の外側) にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="8668d-149">より高度な他の docker-compose.yml 設定もあります。これについては以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="8668d-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="8668d-150">docker-compose ファイルを使用して複数の環境をターゲットにする</span><span class="sxs-lookup"><span data-stu-id="8668d-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="8668d-151">docker-compose.yml ファイルは定義ファイルで、その形式を理解する複数のインフラストラクチャで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="8668d-152">最も簡単なツールは、docker-compose コマンドですが、オーケストレーターのような他のツール (Docker Swarm など) でもこの形式は理解されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="8668d-153">そのため、docker-compose コマンドを使用することで、次の主なシナリオをターゲットにすることができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="8668d-154">開発環境</span><span class="sxs-lookup"><span data-stu-id="8668d-154">Development environments</span></span>

<span data-ttu-id="8668d-155">アプリケーションを開発するときには、アプリケーションを分離開発環境で実行できることが重要です。</span><span class="sxs-lookup"><span data-stu-id="8668d-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="8668d-156">docker-compose CLI コマンドを使用してその環境を作成するか、内部で docker-compose を使用する Visual Studio を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="8668d-157">docker-compose.yml ファイルを使用すると、アプリケーションのすべてのサービスの依存関係 (その他のサービス、キャッシュ、データベース、キューなど) を構成および文書化できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="8668d-158">docker-compose CLI コマンドを使用すると、1 つのコマンド (docker-compose up) を使用して、依存関係ごとに 1 つ以上のコンテナーを作成して起動することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="8668d-159">docker-compose.yml ファイルは、Docker エンジンによって解釈される構成ファイルですが、マルチコンテナー アプリケーションの構成に関する便利なドキュメント ファイルとしても機能します。</span><span class="sxs-lookup"><span data-stu-id="8668d-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="8668d-160">テスト環境</span><span class="sxs-lookup"><span data-stu-id="8668d-160">Testing environments</span></span>

<span data-ttu-id="8668d-161">継続的配置 (CD) または継続的インテグレーション (CI) プロセスの重要な部分は、単体テストと統合テストです。</span><span class="sxs-lookup"><span data-stu-id="8668d-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="8668d-162">これらの自動テストでは、ユーザーまたはアプリケーションのデータ内の他の変更による影響を受けないように、分離環境が必要です。</span><span class="sxs-lookup"><span data-stu-id="8668d-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="8668d-163">Docker Compose を使用すると、コマンド プロンプトまたはスクリプトから、次のようないくつかのコマンドでその分離環境を非常に簡単に作成および破棄することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="8668d-164">運用展開</span><span class="sxs-lookup"><span data-stu-id="8668d-164">Production deployments</span></span>

<span data-ttu-id="8668d-165">Compose を使用してリモート Docker エンジンに展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="8668d-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="8668d-166">一般的なケースは、(運用 VM または [Docker マシン](https://docs.docker.com/machine/overview/)でプロビジョニングされたサーバーのように) 1 つの Docker ホスト インスタンスに展開することです。</span><span class="sxs-lookup"><span data-stu-id="8668d-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="8668d-167">ただし、クラスターも docker-compose.yml ファイルと互換性があるため、[Docker Swarm](https://docs.docker.com/swarm/overview/) クラスター全体にも可能です。</span><span class="sxs-lookup"><span data-stu-id="8668d-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="8668d-168">他の任意のオーケストレーター (Azure Service Fabric、Mesos DC/OS、Kubernetes など) を使用している場合は、docker-compose.yml にあるようなセットアップとメタデータの構成設定を、他のオーケストレーターで必要な形式で追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="8668d-169">いずれの場合も、docker-compose は、開発、テスト、運用ワークフローにとって便利なツールとメタデータ形式ですが、運用ワークフローはお使いのオーケストレーターによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="8668d-170">複数の docker-compose ファイルを使用して複数の環境を処理する</span><span class="sxs-lookup"><span data-stu-id="8668d-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="8668d-171">さまざまな環境をターゲットとする場合は、複数の compose ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="8668d-172">これにより、環境に応じて複数の構成バリアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="8668d-173">基本の docker-compose ファイルをオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="8668d-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="8668d-174">前のセクションで示した簡略化された例のように、1 つの docker-compose.yml ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="8668d-175">ただし、これはほとんどのアプリケーションにはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="8668d-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="8668d-176">既定では、Compose は docker-compose.yml と省略可能な docker-compose.override.yml の 2 つのファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8668d-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="8668d-177">図 8-11 に示すように、Visual Studio を使用して Docker サポートを有効にしている場合、VSTS と同じように CI/CD パイプラインから使用するため、Visual Studio によって追加の docker-compose.ci.build.yml ファイルも作成されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="8668d-178">**図 8-11**</span><span class="sxs-lookup"><span data-stu-id="8668d-178">**Figure 8-11**.</span></span> <span data-ttu-id="8668d-179">Visual Studio 2017 の docker-compose ファイル</span><span class="sxs-lookup"><span data-stu-id="8668d-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="8668d-180">Visual Studio Code や Sublime などの任意のエディターを使用して docker-compose ファイルを編集し、docker-compose up コマンドを使用してアプリケーションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="8668d-181">慣例により、docker-compose.yml ファイルには、基本構成とその他の静的な設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8668d-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="8668d-182">つまり、ターゲットとしている展開環境に合わせてサービス構成を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="8668d-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="8668d-183">docker-compose.override.yml ファイルには、その名前が示すように、基本構成 (展開環境に依存する構成など) をオーバーライドする構成設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8668d-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="8668d-184">また、複数の override ファイルを異なる名前で持つことができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="8668d-185">override ファイルには通常、アプリケーションで必要な、環境または展開に固有の追加情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8668d-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="8668d-186">複数の環境をターゲットにする</span><span class="sxs-lookup"><span data-stu-id="8668d-186">Targeting multiple environments</span></span>

<span data-ttu-id="8668d-187">一般的なユース ケースは、運用、ステージング、CI、開発などの複数の環境をターゲットにできるように、複数の compose ファイルを定義する場合です。</span><span class="sxs-lookup"><span data-stu-id="8668d-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="8668d-188">これらの相違点をサポートするため、図 8-12 示すように、Compose 構成を複数のファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="8668d-189">**図 8-12**</span><span class="sxs-lookup"><span data-stu-id="8668d-189">**Figure 8-12**.</span></span> <span data-ttu-id="8668d-190">基本の docker-compose.yml ファイル内の値をオーバーライドする複数の docker-compose ファイル</span><span class="sxs-lookup"><span data-stu-id="8668d-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="8668d-191">基本の docker-compose.yml ファイルから開始します。</span><span class="sxs-lookup"><span data-stu-id="8668d-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="8668d-192">この基本ファイルには、環境に合わせて変更されない基本構成または静的な構成設定が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="8668d-193">たとえば、eShopOnContainers には、基本ファイルとして次の docker-compose.yml ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="8668d-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="8668d-194">基本の docker-compose.yml ファイル内の値は、ターゲット展開環境が異なるため、変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="8668d-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="8668d-195">たとえば、webmvc サービス定義に注目すると、ターゲットとする環境が何であれ、その情報がほとんど同じであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8668d-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="8668d-196">次の情報があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-196">You have the following information:</span></span>

-   <span data-ttu-id="8668d-197">サービス名: webmvc</span><span class="sxs-lookup"><span data-stu-id="8668d-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="8668d-198">コンテナーのカスタム イメージ: eshop/webmvc</span><span class="sxs-lookup"><span data-stu-id="8668d-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="8668d-199">使用する Dockerfile を示す、カスタム Docker イメージをビルドするコマンド</span><span class="sxs-lookup"><span data-stu-id="8668d-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="8668d-200">他の依存関係コンテナーが起動されるまで、このコンテナーを起動しないようする、他のサービスへの依存関係</span><span class="sxs-lookup"><span data-stu-id="8668d-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="8668d-201">追加の構成を持つことはできますが、重要な点は、基本の docker-compose.yml ファイルでは、環境間で共通する情報だけを設定することです。</span><span class="sxs-lookup"><span data-stu-id="8668d-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="8668d-202">その後、docker-compose.override.yml または運用またはステージングの同様のファイルで、各環境に固有の構成を配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8668d-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="8668d-203">通常、docker-compose.override.yml は、eShopOnContainers からの次の例のように、開発環境のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="8668d-204">この例では、開発オーバーライド構成でいくつかのポートをホストに公開し、リダイレクト URL で環境変数を定義し、開発環境への接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8668d-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="8668d-205">これらの設定はすべて、開発環境のためだけのものです。</span><span class="sxs-lookup"><span data-stu-id="8668d-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="8668d-206">`docker-compose up` を実行 (または Visual Studio から起動) すると、コマンドは両方のオーバーライドを、2 つのファイルがマージされているかのように、自動的に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8668d-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="8668d-207">運用環境用に、異なる構成値、ポート、または接続文字列を持つ別の Compose ファイルが必要だとします。</span><span class="sxs-lookup"><span data-stu-id="8668d-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="8668d-208">異なる設定と環境変数を使用して、`docker-compose.prod.yml` という名前の別の override ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="8668d-209">そのファイルは、別の Git リポジトリに格納したり、別のチームによって管理および保護することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="8668d-210">特定の override ファイルによる展開方法</span><span class="sxs-lookup"><span data-stu-id="8668d-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="8668d-211">複数の override ファイルを使用する、または異なる名前の override ファイルを使用するには、docker-compose コマンドで -f オプションを使用してファイルを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="8668d-212">Compose によって、コマンドラインで指定された順序でファイルがマージされます。</span><span class="sxs-lookup"><span data-stu-id="8668d-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="8668d-213">次の例は、override ファイルを使用した展開方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="8668d-214">docker-compose ファイルで環境変数を使用する</span><span class="sxs-lookup"><span data-stu-id="8668d-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="8668d-215">前の例に示したように、特に運用環境では、環境変数から構成情報を取得できると便利です。</span><span class="sxs-lookup"><span data-stu-id="8668d-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="8668d-216">構文 \${MY\_VAR} を使用して、docker-compose ファイル内の環境変数を参照します。</span><span class="sxs-lookup"><span data-stu-id="8668d-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="8668d-217">docker-compose.prod.yml ファイルからの次の行は、環境変数の値の参照方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="8668d-218">環境変数が作成され、ホスト環境 (Linux、Windows、クラウド クラスターなど) に応じて、さまざまな方法で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="8668d-219">しかし、便利な方法は、.env ファイルを使用することです。</span><span class="sxs-lookup"><span data-stu-id="8668d-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="8668d-220">docker-compose ファイルは、.env ファイルで既定の環境変数を宣言することをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8668d-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="8668d-221">環境変数のこれらの値が既定値です。</span><span class="sxs-lookup"><span data-stu-id="8668d-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="8668d-222">ただしこれらは、それぞれの環境 (ホスト OS またはクラスターからの環境変数) で定義した値によってオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="8668d-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="8668d-223">この .env ファイルを、docker-compose コマンドが実行される場所に配置します。</span><span class="sxs-lookup"><span data-stu-id="8668d-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="8668d-224">次の例は、eShopOnContainers アプリケーション用の [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) ファイルと同様の .env ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="8668d-225">Docker-compose は、.env ファイル内の各行が &lt;変数&gt;=&lt;値&gt; の形式になることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="8668d-226">ランタイム環境で設定された値は、.env ファイル内で定義されている値を常にオーバーライドすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8668d-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="8668d-227">同様の方法で、コマンドラインのコマンド引数を介して渡される値も、.env ファイルで設定された既定値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="8668d-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8668d-228">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="8668d-228">Additional resources</span></span>

-   <span data-ttu-id="8668d-229">**Docker Compose の概要**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="8668d-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="8668d-230">**複数の Compose ファイル**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="8668d-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="8668d-231">最適化された ASP.NET Core Docker イメージをビルドする</span><span class="sxs-lookup"><span data-stu-id="8668d-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="8668d-232">インターネット上のソースで Docker や .NET Core を検索すると、ソースをコンテナーにコピーして Docker イメージを簡単にビルドする方法を示す Dockerfile が見つかります。</span><span class="sxs-lookup"><span data-stu-id="8668d-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="8668d-233">これらの例では、単純な構成を使用することで、ご利用のアプリケーションにパッケージ化された環境で Docker イメージを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="8668d-234">次の例は、このような単純な Dockerfile を示しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="8668d-235">このような Dockerfile は機能します。</span><span class="sxs-lookup"><span data-stu-id="8668d-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="8668d-236">ただし、イメージ、とりわけ運用イメージは大幅に最適化できます。</span><span class="sxs-lookup"><span data-stu-id="8668d-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="8668d-237">コンテナーとマイクロサービス モデルでは、常にコンテナーを起動します。</span><span class="sxs-lookup"><span data-stu-id="8668d-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="8668d-238">コンテナーは破棄可能なため、コンテナーの一般的な使用方法では、スリープ状態のコンテナーを再起動しません。</span><span class="sxs-lookup"><span data-stu-id="8668d-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="8668d-239">オーケストレーター (Docker Swarm、Kubernetes、DCOS または Azure Service Fabric など) は、イメージの新しいインスタンスを単に作成します。</span><span class="sxs-lookup"><span data-stu-id="8668d-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="8668d-240">これは、インスタンス化のプロセスを高速化するため、アプリケーションのビルド時に、アプリケーションをプリコンパイルして最適化する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8668d-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="8668d-241">コンテナーは起動すると、実行できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="8668d-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="8668d-242">.NET Core と Docker に関する多くのブログ記事で見られるような、dotnet CLI から dotnet restore コマンドおよび dotnet build コマンドを使用した、実行時の復元およびコンパイルは行わないでください。</span><span class="sxs-lookup"><span data-stu-id="8668d-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="8668d-243">.NET チームは、.NET Core と ASP.NET Core をコンテナー用に最適化されたフレームワークにするための重要な作業を行っています。</span><span class="sxs-lookup"><span data-stu-id="8668d-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="8668d-244">.NET Core は、メモリの使用量を抑えた軽量のフレームワークというだけではありません。チームは起動時のパフォーマンスに重点を置いて、いくつかの最適化された Docker イメージを作成してきました。これには、通常の [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) または [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) イメージと比較して、[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/) で使用可能な [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージなどがあります。</span><span class="sxs-lookup"><span data-stu-id="8668d-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="8668d-245">[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージでは、aspnetcore\_url のポート 80 への自動設定とアセンブリの pre-ngend キャッシュの自動設定が提供されます。これらの設定はどちらも起動時間を短縮します。</span><span class="sxs-lookup"><span data-stu-id="8668d-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8668d-246">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="8668d-246">Additional resources</span></span>

-   <span data-ttu-id="8668d-247">**ASP.NET Core を使用して最適化された Docker イメージをビルドする**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="8668d-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="8668d-248">ビルド (CI) コンテナーからアプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="8668d-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="8668d-249">Docker のもう 1 つの利点は、図 8-13 に示すように、事前に構成されたコンテナーからアプリケーションをビルドできるため、アプリケーションをビルドするためにビルド コンピューターや VM を作成する必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="8668d-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="8668d-250">そのビルド コンテナーは、開発用コンピューターで実行することで、使用またはテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="8668d-251">しかし、より興味深いことは、お使いの CI (継続的インテグレーション) パイプラインから同じビルド コンテナーを使用できることです。</span><span class="sxs-lookup"><span data-stu-id="8668d-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="8668d-252">**図 8-13**</span><span class="sxs-lookup"><span data-stu-id="8668d-252">**Figure 8-13**.</span></span> <span data-ttu-id="8668d-253">.NET バイナリをコンパイルする Docker ビルド コンテナー</span><span class="sxs-lookup"><span data-stu-id="8668d-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="8668d-254">このシナリオのために、ASP.NET Core アプリのコンパイルとビルドに使用できる、[microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) が提供されています。</span><span class="sxs-lookup"><span data-stu-id="8668d-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="8668d-255">出力は、前述したように、最適化されたランタイム イメージの [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージに基づくイメージに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="8668d-256">aspnetcore-build イメージには、.NET Core、ASP.NET SDK、npm、Bower、Gulp など、ASP.NET Core アプリケーションをコンパイルするために必要なものがすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="8668d-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="8668d-257">ビルド時にはこれらの依存関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="8668d-257">We need these dependencies at build time.</span></span> <span data-ttu-id="8668d-258">しかし、起動時にアプリケーションでこれらすべてを実行すると、イメージが不必要に大きくなってしまうため、これを回避します。</span><span class="sxs-lookup"><span data-stu-id="8668d-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="8668d-259">eShopOnContainers アプリケーションでは、次の docker-compose コマンドを実行するだけで、コンテナーからアプリケーションをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="8668d-260">図 8-14 は、コマンドラインで実行されているこのコマンドを示しています。</span><span class="sxs-lookup"><span data-stu-id="8668d-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="8668d-261">**図 8-14**</span><span class="sxs-lookup"><span data-stu-id="8668d-261">**Figure 8-14.**</span></span> <span data-ttu-id="8668d-262">コンテナーから .NET アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="8668d-262">Building your .NET application from a container</span></span>

<span data-ttu-id="8668d-263">ご覧のとおり、実行されているコンテナーが ci-build\_1 コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="8668d-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="8668d-264">これは aspnetcore-build イメージに基づいているため、お使いの PC からではなく、そのコンテナー内からアプリケーション全体をコンパイルしてビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="8668d-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="8668d-265">そのコンテナーが既定の Docker Linux ホストで実行されているため、これが、実際には Linux で .NET Core プロジェクトがビルドされコンパイルされる理由です。</span><span class="sxs-lookup"><span data-stu-id="8668d-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="8668d-266">そのイメージ (eShopOnContainers の一部) の [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) ファイルには、次のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8668d-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="8668d-267">このコードでは、[microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) イメージを使用してビルド コンテナーを起動していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8668d-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* <span data-ttu-id="8668d-268">**.NET Core 2.0** 以降では、`dotnet publish` コマンドが実行されるときに、`dotnet restore` コマンドが自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="8668d-269">ビルド コンテナーが起動されて稼働すると、.NET bits をコンパイルするために、.NET SDK dotnet restore コマンドと dotnet publish コマンドがソリューション内のすべてのプロジェクトに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="8668d-270">この例では、eShopOnContainers には TypeScript に基づく SPA とクライアント コードの Angular もあるため、npm を使用して JavaScript の依存関係をチェックする必要もありますが、そのアクションは .NET bits とは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="8668d-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="8668d-271">dotnet publish コマンドにより、各プロジェクトのフォルダー内でコンパイルされた出力がビルドされ、図 8-15 に示すように、../obj/Docker/publish フォルダーに発行されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="8668d-272">**図 8-15**</span><span class="sxs-lookup"><span data-stu-id="8668d-272">**Figure 8-15.**</span></span> <span data-ttu-id="8668d-273">dotnet publish コマンドによって生成されたバイナリ ファイル</span><span class="sxs-lookup"><span data-stu-id="8668d-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="8668d-274">CLI から Docker イメージを作成する</span><span class="sxs-lookup"><span data-stu-id="8668d-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="8668d-275">アプリケーションの出力が (各プロジェクト内の) 関連するフォルダーに発行されたら、次のステップは、実際に Docker イメージを作成することです。</span><span class="sxs-lookup"><span data-stu-id="8668d-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="8668d-276">これを行うには、図 8-16 に示すように、docker-compose build コマンドと docker-compose up コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8668d-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="8668d-277">**図 8-16**</span><span class="sxs-lookup"><span data-stu-id="8668d-277">**Figure 8-16.**</span></span> <span data-ttu-id="8668d-278">Docker イメージのビルドとコンテナーの実行</span><span class="sxs-lookup"><span data-stu-id="8668d-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="8668d-279">図 8-17 では、docker-compose build コマンドがどのように実行されるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="8668d-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="8668d-280">**図 8-17**</span><span class="sxs-lookup"><span data-stu-id="8668d-280">**Figure 8-17**.</span></span> <span data-ttu-id="8668d-281">docker-compose build コマンドを使用して Docker イメージをビルドする</span><span class="sxs-lookup"><span data-stu-id="8668d-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="8668d-282">docker-compose build コマンドと docker-compose up コマンドの違いは、docker-compose up はイメージのビルドと開始の両方ができることです。</span><span class="sxs-lookup"><span data-stu-id="8668d-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="8668d-283">Visual Studio を使用すると、これらすべての手順は内部で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="8668d-284">.NET アプリケーションのコンパイル、Docker イメージの作成、および Docker ホストへのコンテナーの展開は、Visual Studio によって行われます。</span><span class="sxs-lookup"><span data-stu-id="8668d-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="8668d-285">Visual Studio では、Docker で実行中のコンテナーをデバッグするための機能など、追加の機能が Visual Studio から直接提供されます。</span><span class="sxs-lookup"><span data-stu-id="8668d-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="8668d-286">全体的に見て重要なことは、CI/CD パイプラインでビルドするのと同じ方法で、ローカル コンピューターからではなくコンテナーから、アプリケーションをビルドできることです。</span><span class="sxs-lookup"><span data-stu-id="8668d-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="8668d-287">イメージを作成した後に必要なのは、docker-compose up コマンドを使用して Docker イメージを実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="8668d-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8668d-288">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="8668d-288">Additional resources</span></span>

-   <span data-ttu-id="8668d-289">**コンテナーから bits をビルドする: Windows CLI 環境 (dotnet CLI、Docker CLI、VS Code) で eShopOnContainers ソリューションをセットアップする**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="8668d-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="8668d-290">[前へ](data-driven-crud-microservice.md)
[次へ](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="8668d-290">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
