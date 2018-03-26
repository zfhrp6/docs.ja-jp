---
title: docker-compose.yml で複数のコンテナー アプリケーションを定義する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | docker-compose.yml で複数のコンテナー アプリケーションを定義する'
keywords: Docker, マイクロサービス, ASP.NET, コンテナー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>docker-compose.yml で複数のコンテナー アプリケーションを定義する 

このガイドでは、[docker-compose.yml](https://docs.docker.com/compose/compose-file/) ファイルは、「[手順 4 複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスを定義します](#step4_define_svcs_in_docker_compose_yml)」セクションで導入されました。 しかし、docker-compose ファイルには他の使い方もあり、さらに詳しく検討する価値があります。

たとえば、マルチコンテナー アプリケーションの展開方法を、docker-compose.yml ファイルで明示的に記述することができます。 必要に応じて、カスタム Docker イメージのビルド方法も記述できます  (カスタム Docker イメージは、Docker CLI を使用してビルドすることもできます)。

基本的には、展開する各コンテナーを定義することに加え、各コンテナー展開に対して特定の特性も定義します。 マルチコンテナー展開の記述ファイルを作成したら、全体のソリューションを、[docker-compose up](https://docs.docker.com/compose/overview/) CLI コマンドで調整された 1 つのアクションで展開することができます。または、Visual Studio から透過的に展開することもできます。 それ以外の場合は、Docker CLI を使用して、コマンドラインから docker run コマンドを使用して、複数の手順でコンテナーごとに展開する必要があります。 そのため、docker-compose.yml で定義された各サービスは、イメージまたはビルドを 1 つだけ指定する必要があります。 その他のキーは省略可能で、その対応する docker run コマンド ラインと似ています。

次の YAML コードは、グローバルに使用できる定義ですが、eShopOnContainers サンプル用の 1 つの docker-compose.yml ファイルです。 これは eShopOnContainers からの実際の docker-compose ファイルではありません。 むしろ、簡素化され、1 つのファイルに統合されたバージョンです。後述しますが、これは docker-compose ファイルで使用するには最善の方法ではありません。

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

このファイルのルート キーはサービスです。 そのキーの下で、docker-compose up コマンドを実行する場合、または docker-compose.yml ファイルを使用して Visual Studio から展開する場合に、展開および実行するサービスを定義します。 この例では、次の一覧に示すように、docker-compose.yml ファイルには複数の定義済みのサービスがあります。

-   サーバー側 C\# からマイクロサービスを消費する ASP.NET Core MVC アプリケーションを含む webmvc コンテナー

-   Catalog ASP.NET Core Web API マイクロサービスを含む catalog.api コンテナー

-   Ordering ASP.NET Core Web API マイクロサービスを含む ordering.api コンテナー

-   マイクロサービス データベースを保持する、SQL Server for Linux を実行する sql.data コンテナー

-   basket.api コンテナーと Basket ASP.NET Core Web API マイクロサービス

-   REDIS キャッシュ サービスを実行し、REDIS キャッシュとしてバスケット データベースを持つ basket.data コンテナー

### <a name="a-simple-web-service-api-container"></a>単純な Web サービス API コンテナー

1 つのコンテナーに集中することで、catalog.api container-microservice の定義が単純になります。

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

このコンテナー化されたサービスには、次の基本的な構成があります。

-   カスタムの eshop/catalog.api イメージに基づいています。 わかりやすくするために、ファイル内にビルドやキーの設定はありません。 つまりイメージが、(docker build を使用して) 既にビルドされているか、(docker pull コマンドを使用して) 任意の Docker レジストリからダウンロードされている必要があります。

-   接続文字列を使用して ConnectionString という名前の環境変数を定義します。この変数は、カタログ データ モデルを含む SQL Server インスタンスにアクセスするために Entity Framework によって使用されます。 この例では、同じ SQL Server コンテナーに複数のデータベースが保持されています。 そのため、Docker 用に開発用コンピューターで必要なメモリ量が減ります。 ただし、マイクロサービス データベースごとに 1 つの SQL Server のコンテナーを展開することもできます。

-   SQL Server 名は sql.data で、Linux の SQL Server インスタンスが実行されているコンテナーで使用されているのと同じ名前です。 これは便利な方法です。この名前解決 (内部から Docker ホストへ) を使用できることで、ネットワーク アドレスが解決されるため、他のコンテナーからアクセスするコンテナーの内部 IP アドレスを知る必要はありません。

接続文字列は環境変数によって定義されるため、異なる時点で別のメカニズムを使用して、その変数を設定することができます。 たとえば、最後のホストで運用に展開するときに、または VSTS の CI/CD パイプラインから、または優先する DevOps システムから、別の接続文字列を設定できます。

-   Docker ホスト内で catalog.api サービスへの内部アクセス用に、ポート 80 を公開します。 ホストは、Linux の Docker イメージに基づいているため、現在は Linux VM ですが、代わりに Windows イメージ上で実行するようにコンテナーを構成することもできます。

-   コンテナー上で公開されているポート 80 を、Docker ホスト コンピューター (Linux VM) 上のポート 5101 に転送します。

-   Web サービスを sql.data サービス (コンテナーで実行されている Linux データベースの SQL Server インスタンス) にリンクします。 この依存関係を指定すると、catalog.api コンテナーは、sql.data コンテナーが起動するまで起動しなくなります。これが重要なのは、catalog.api には、SQL Server データベースが先に起動していて、実行されている必要があるからです。 ただし、このようなコンテナーの依存関係は、Docker がコンテナー レベルでしかチェックしないため、多くの場合、不十分です。 サービス (この場合は SQL Server) がまだ準備できていない場合もあるため、クライアント マイクロサービスで指数バックオフによる再試行ロジックを実装することをお勧めします。 そうすることで、依存関係のコンテナーが少しの間、準備できない場合でも、アプリケーションが回復力を保つことができます。

-   外部サーバーへのアクセスを許可するように構成されます: extra\_hosts 設定により、開発 PC 上のローカル SQL Server インスタンスなど、外部サーバーまたは Docker ホストの外部のマシン (つまり、開発 Docker ホストである既定の Linux VM の外側) にアクセスすることができます。

より高度な他の docker-compose.yml 設定もあります。これについては以降のセクションで説明します。

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>docker-compose ファイルを使用して複数の環境をターゲットにする

docker-compose.yml ファイルは定義ファイルで、その形式を理解する複数のインフラストラクチャで使用できます。 最も簡単なツールは、docker-compose コマンドですが、オーケストレーターのような他のツール (Docker Swarm など) でもこの形式は理解されます。

そのため、docker-compose コマンドを使用することで、次の主なシナリオをターゲットにすることができます。

#### <a name="development-environments"></a>開発環境

アプリケーションを開発するときには、アプリケーションを分離開発環境で実行できることが重要です。 docker-compose CLI コマンドを使用してその環境を作成するか、内部で docker-compose を使用する Visual Studio を使用できます。

docker-compose.yml ファイルを使用すると、アプリケーションのすべてのサービスの依存関係 (その他のサービス、キャッシュ、データベース、キューなど) を構成および文書化できます。 docker-compose CLI コマンドを使用すると、1 つのコマンド (docker-compose up) を使用して、依存関係ごとに 1 つ以上のコンテナーを作成して起動することができます。

docker-compose.yml ファイルは、Docker エンジンによって解釈される構成ファイルですが、マルチコンテナー アプリケーションの構成に関する便利なドキュメント ファイルとしても機能します。

#### <a name="testing-environments"></a>テスト環境

継続的配置 (CD) または継続的インテグレーション (CI) プロセスの重要な部分は、単体テストと統合テストです。 これらの自動テストでは、ユーザーまたはアプリケーションのデータ内の他の変更による影響を受けないように、分離環境が必要です。

Docker Compose を使用すると、コマンド プロンプトまたはスクリプトから、次のようないくつかのコマンドでその分離環境を非常に簡単に作成および破棄することができます。

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>運用展開

Compose を使用してリモート Docker エンジンに展開することもできます。 一般的なケースは、(運用 VM または [Docker マシン](https://docs.docker.com/machine/overview/)でプロビジョニングされたサーバーのように) 1 つの Docker ホスト インスタンスに展開することです。 ただし、クラスターも docker-compose.yml ファイルと互換性があるため、[Docker Swarm](https://docs.docker.com/swarm/overview/) クラスター全体にも可能です。

他の任意のオーケストレーター (Azure Service Fabric、Mesos DC/OS、Kubernetes など) を使用している場合は、docker-compose.yml にあるようなセットアップとメタデータの構成設定を、他のオーケストレーターで必要な形式で追加する必要がある場合があります。

いずれの場合も、docker-compose は、開発、テスト、運用ワークフローにとって便利なツールとメタデータ形式ですが、運用ワークフローはお使いのオーケストレーターによって異なる場合があります。

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>複数の docker-compose ファイルを使用して複数の環境を処理する

さまざまな環境をターゲットとする場合は、複数の compose ファイルを使用する必要があります。 これにより、環境に応じて複数の構成バリアントを作成できます。

#### <a name="overriding-the-base-docker-compose-file"></a>基本の docker-compose ファイルを上書きする

前のセクションで示した簡略化された例のように、1 つの docker-compose.yml ファイルを使用できます。 ただし、これはほとんどのアプリケーションにはお勧めできません。

既定では、Compose は docker-compose.yml と省略可能な docker-compose.override.yml の 2 つのファイルを読み取ります。 図 8-11 に示すように、Visual Studio を使用して Docker サポートを有効にしている場合、VSTS と同じように CI/CD パイプラインから使用するため、Visual Studio によって追加の docker-compose.ci.build.yml ファイルも作成されます。

![](./media/image12.png)

**図 8-11** Visual Studio 2017 の docker-compose ファイル

Visual Studio Code や Sublime などの任意のエディターを使用して docker-compose ファイルを編集し、docker-compose up コマンドを使用してアプリケーションを実行することができます。

慣例により、docker-compose.yml ファイルには、基本構成とその他の静的な設定が含まれています。 つまり、ターゲットとしている展開環境に合わせてサービス構成を変更しないでください。

docker-compose.override.yml ファイルには、その名前が示すように、基本構成 (展開環境に依存する構成など) を上書きする構成設定が含まれています。 また、複数の override ファイルを異なる名前で持つことができます。 override ファイルには通常、アプリケーションで必要な、環境または展開に固有の追加情報が含まれています。

#### <a name="targeting-multiple-environments"></a>複数の環境をターゲットにする

一般的なユース ケースは、運用、ステージング、CI、開発などの複数の環境をターゲットにできるように、複数の compose ファイルを定義する場合です。 これらの相違点をサポートするため、図 8-12 示すように、Compose 構成を複数のファイルに分割できます。

![](./media/image13.png)

**図 8-12** 基本の docker-compose.yml ファイル内の値を上書きする複数の docker-compose ファイル

基本の docker-compose.yml ファイルから開始します。 この基本ファイルには、環境に合わせて変更されない基本構成または静的な構成設定が含まれている必要があります。 たとえば、eShopOnContainers には、基本ファイルとして次の docker-compose.yml ファイルがあります。

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

基本の docker-compose.yml ファイル内の値は、ターゲット展開環境が異なるため、変更しないでください。

たとえば、webmvc サービス定義に注目すると、ターゲットとする環境が何であれ、その情報がほとんど同じであることがわかります。 次の情報があります。

-   サービス名: webmvc

-   コンテナーのカスタム イメージ: eshop/webmvc

-   使用する Dockerfile を示す、カスタム Docker イメージをビルドするコマンド

-   他の依存関係コンテナーが起動されるまで、このコンテナーを起動しないようする、他のサービスへの依存関係

追加の構成を持つことはできますが、重要な点は、基本の docker-compose.yml ファイルでは、環境間で共通する情報だけを設定することです。 その後、docker-compose.override.yml または運用またはステージングの同様のファイルで、各環境に固有の構成を配置する必要があります。

通常、docker-compose.override.yml は、eShopOnContainers からの次の例のように、開発環境のために使用されます。

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

この例では、開発上書き構成でいくつかのポートをホストに公開し、リダイレクト URL で環境変数を定義し、開発環境への接続文字列を指定します。 これらの設定はすべて、開発環境のためだけのものです。

`docker-compose up` を実行 (または Visual Studio から起動) すると、コマンドは両方の上書きを、2 つのファイルがマージされているかのように、自動的に読み取ります。

運用環境用に、異なる構成値、ポート、または接続文字列を持つ別の Compose ファイルが必要だとします。 異なる設定と環境変数を使用して、`docker-compose.prod.yml` という名前の別の override ファイルを作成できます。  そのファイルは、別の Git リポジトリに格納したり、別のチームによって管理および保護することができます。

#### <a name="how-to-deploy-with-a-specific-override-file"></a>特定の override ファイルによる展開方法

複数の override ファイルを使用する、または異なる名前の override ファイルを使用するには、docker-compose コマンドで -f オプションを使用してファイルを指定することができます。 Compose によって、コマンドラインで指定された順序でファイルがマージされます。 次の例は、override ファイルを使用した展開方法を示しています。

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>docker-compose ファイルで環境変数を使用する

前の例に示したように、特に運用環境では、環境変数から構成情報を取得できると便利です。 構文 \${MY\_VAR} を使用して、docker-compose ファイル内の環境変数を参照します。 docker-compose.prod.yml ファイルからの次の行は、環境変数の値の参照方法を示しています。

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

環境変数が作成され、ホスト環境 (Linux、Windows、クラウド クラスターなど) に応じて、さまざまな方法で初期化されます。 しかし、便利な方法は、.env ファイルを使用することです。 docker-compose ファイルは、.env ファイルで既定の環境変数を宣言することをサポートします。 環境変数のこれらの値が既定値です。 ただしこれらは、それぞれの環境 (ホスト OS またはクラスターからの環境変数) で定義した値によって上書きできます。 この .env ファイルを、docker-compose コマンドが実行される場所に配置します。

次の例は、eShopOnContainers アプリケーション用の [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) ファイルと同様の .env ファイルを示しています。

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose は、.env ファイル内の各行が &lt;変数&gt;=&lt;値&gt; の形式になることを想定しています。

ランタイム環境で設定された値は、.env ファイル内で定義されている値を常に上書きすることに注意してください。 同様の方法で、コマンドラインのコマンド引数を介して渡される値も、.env ファイルで設定された既定値を上書きします。

#### <a name="additional-resources"></a>その他の技術情報

-   **Docker の概要を作成します。**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **複数の構成ファイル**
    [*https://docs.docker.com/compose/extends/\#複数を構成ファイル*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>最適化された ASP.NET Core Docker イメージをビルドする

インターネット上のソースで Docker や .NET Core を検索すると、ソースをコンテナーにコピーして Docker イメージを簡単にビルドする方法を示す Dockerfile が見つかります。 これらの例では、単純な構成を使用することで、ご利用のアプリケーションにパッケージ化された環境で Docker イメージを持つことができます。 次の例は、このような単純な Dockerfile を示しています。

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

このような Dockerfile は機能します。 ただし、イメージ、とりわけ運用イメージは大幅に最適化できます。

コンテナーとマイクロサービス モデルでは、常にコンテナーを起動します。 コンテナーは破棄可能なため、コンテナーの一般的な使用方法では、スリープ状態のコンテナーを再起動しません。 オーケストレーター (Docker Swarm、Kubernetes、DCOS または Azure Service Fabric など) は、イメージの新しいインスタンスを単に作成します。 これは、インスタンス化のプロセスを高速化するため、アプリケーションのビルド時に、アプリケーションをプリコンパイルして最適化する必要があることを意味します。 コンテナーは起動すると、実行できる状態になります。 .NET Core と Docker に関する多くのブログ記事で見られるような、dotnet CLI から dotnet restore コマンドおよび dotnet build コマンドを使用した、実行時の復元およびコンパイルは行わないでください。

.NET チームは、.NET Core と ASP.NET Core をコンテナー用に最適化されたフレームワークにするための重要な作業を行っています。 .NET Core は、メモリの使用量を抑えた軽量のフレームワークというだけではありません。チームは起動時のパフォーマンスに重点を置いて、いくつかの最適化された Docker イメージを作成してきました。これには、通常の [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) または [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) イメージと比較して、[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/) で使用可能な [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージなどがあります。 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージでは、aspnetcore\_url のポート 80 への自動設定とアセンブリの pre-ngend キャッシュの自動設定が提供されます。これらの設定はどちらも起動時間を短縮します。

#### <a name="additional-resources"></a>その他の技術情報

-   **ビルドと ASP.NET Core Docker Images の最適化**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>ビルド (CI) コンテナーからアプリケーションをビルドする

Docker のもう 1 つの利点は、図 8-13 に示すように、事前に構成されたコンテナーからアプリケーションをビルドできるため、アプリケーションをビルドするためにビルド コンピューターや VM を作成する必要がないことです。 そのビルド コンテナーは、開発用コンピューターで実行することで、使用またはテストすることができます。 しかし、より興味深いことは、お使いの CI (継続的インテグレーション) パイプラインから同じビルド コンテナーを使用できることです。

![](./media/image14.png)

**図 8-13** .NET バイナリをコンパイルする Docker ビルド コンテナー 

このシナリオのために、ASP.NET Core アプリのコンパイルとビルドに使用できる、[microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) が提供されています。 出力は、前述したように、最適化されたランタイム イメージの [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージに基づくイメージに配置されます。

aspnetcore-build イメージには、.NET Core、ASP.NET SDK、npm、Bower、Gulp など、ASP.NET Core アプリケーションをコンパイルするために必要なものがすべて含まれています。

ビルド時にはこれらの依存関係が必要です。 しかし、起動時にアプリケーションでこれらすべてを実行すると、イメージが不必要に大きくなってしまうため、これを回避します。 eShopOnContainers アプリケーションでは、次の docker-compose コマンドを実行するだけで、コンテナーからアプリケーションをビルドすることができます。

```
  docker-compose -f docker-compose.ci.build.yml up
```

図 8-14 は、コマンドラインで実行されているこのコマンドを示しています。

![](./media/image15.png)

**図 8-14** コンテナーから .NET アプリケーションをビルドする

ご覧のとおり、実行されているコンテナーが ci-build\_1 コンテナーです。 これは aspnetcore-build イメージに基づいているため、お使いの PC からではなく、そのコンテナー内からアプリケーション全体をコンパイルしてビルドすることができます。 そのコンテナーが既定の Docker Linux ホストで実行されているため、これが、実際には Linux で .NET Core プロジェクトがビルドされコンパイルされる理由です。

そのイメージ (eShopOnContainers の一部) の [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) ファイルには、次のコードが含まれています。 このコードでは、[microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) イメージを使用してビルド コンテナーを起動していることがわかります。

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

* **.NET Core 2.0** 以降では、`dotnet publish` コマンドが実行されるときに、`dotnet restore` コマンドが自動的に実行されます。

ビルド コンテナーが起動されて稼働すると、.NET bits をコンパイルするために、.NET SDK dotnet restore コマンドと dotnet publish コマンドがソリューション内のすべてのプロジェクトに対して実行されます。 この例では、eShopOnContainers には TypeScript に基づく SPA とクライアント コードの Angular もあるため、npm を使用して JavaScript の依存関係をチェックする必要もありますが、そのアクションは .NET bits とは関係ありません。

dotnet publish コマンドにより、各プロジェクトのフォルダー内でコンパイルされた出力がビルドされ、図 8-15 に示すように、../obj/Docker/publish フォルダーに発行されます。

![](./media/image16.png)

**図 8-15** dotnet publish コマンドによって生成されたバイナリ ファイル

#### <a name="creating-the-docker-images-from-the-cli"></a>CLI から Docker イメージを作成する

アプリケーションの出力が (各プロジェクト内の) 関連するフォルダーに発行されたら、次のステップは、実際に Docker イメージを作成することです。 これを行うには、図 8-16 に示すように、docker-compose build コマンドと docker-compose up コマンドを使用します。

![](./media/image17.png)

**図 8-16** Docker イメージのビルドとコンテナーの実行

図 8-17 では、docker-compose build コマンドがどのように実行されるかがわかります。

![](./media/image18.png)

**図 8-17** docker-compose build コマンドを使用して Docker イメージをビルドする

docker-compose build コマンドと docker-compose up コマンドの違いは、docker-compose up はイメージのビルドと開始の両方ができることです。

Visual Studio を使用すると、これらすべての手順は内部で実行されます。 .NET アプリケーションのコンパイル、Docker イメージの作成、および Docker ホストへのコンテナーの展開は、Visual Studio によって行われます。 Visual Studio では、Docker で実行中のコンテナーをデバッグするための機能など、追加の機能が Visual Studio から直接提供されます。

全体的に見て重要なことは、CI/CD パイプラインでビルドするのと同じ方法で、ローカル コンピューターからではなくコンテナーから、アプリケーションをビルドできることです。 イメージを作成した後に必要なのは、docker-compose up コマンドを使用して Docker イメージを実行するだけです。

#### <a name="additional-resources"></a>その他の技術情報

-   **コンテナーからのビットの構築: eShopOnContainers ソリューションを Windows CLI 環境 (dotnet CLI、Docker CLI と VS Code) で設定**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI、- Docker - CLI- と -VS-コード)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[前へ] (data-driven-crud-microservice.md) [次へ] (database-server-container.md)
