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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Docker compose.yml でアプリケーションを複数のコンテナーを定義します。 

このガイドで、 [docker compose.yml](https://docs.docker.com/compose/compose-file/)ファイルは、セクションで導入された[手順 4 です。複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスの定義](#step4_define_svcs_in_docker_compose_yml)です。 ただし、さらに詳しく検討する価値がある docker-compose ファイルを使用するその他の方法があります。

たとえば、明示的に記述できます docker compose.yml ファイルで、複数のコンテナー アプリケーションを配置する方法。 必要に応じて、移動する、カスタムの Docker イメージを構築する方法を記述できます。 (カスタム Docker images も構築できます Docker CLI を使用しています。)

基本的には、各コンテナーを展開すると各コンテナー展開の特定の特性を定義します。 によってコーディネートされます。 1 つのアクションで全体のソリューションを配置することができます、複数のコンテナーの展開の記述ファイルを作成したら、[を docker 構成](https://docs.docker.com/compose/overview/)CLI コマンド、またはすることができます、透過的に Visual Studio からデプロイします。 それ以外の場合は Docker CLI を使用して、コマンドラインからコマンドを実行する、docker を使用して、複数の手順でコンテナーはコンテナーでを展開する必要があります。 したがって、docker compose.yml で定義された各サービスはただ 1 つのイメージを指定またはビルドする必要があります。 その他のキーはオプションであり、docker コマンド ライン古くての実行に似ています。

次の YAML コードは、eShopOnContainers サンプルの可能なグローバルが単一 docker-compose.yml ファイルの定義です。 EShopOnContainers から実際 docker-compose ファイルではありません。 最適なは、1 つのファイルに簡単で統合のバージョンでは代わりに、方法を使用する docker-構成ファイル、後で説明したようです。

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

このファイルのルート キーはサービスです。 配置および実行するときに実行するサービスを定義するキーの下で、コマンドまたはこの docker compose.yml ファイルを使用して Visual Studio からのデプロイを docker 構成します。 この例では、docker compose.yml ファイルでは、次の一覧に示すように定義されている場合、複数のサービスがいます。

-   webmvc サーバー側 C から microservices を消費する ASP.NET Core MVC アプリケーションを含むコンテナー\#

-   catalog.api カタログ ASP.NET Core Web API マイクロ サービスを含むコンテナー

-   ordering.api ASP.NET Core Web API の順序付けマイクロ サービスを含むコンテナー

-   sql.data microservices データベースを保持して、Linux 用 SQL Server を実行中のコンテナー

-   バスケット ASP.NET Core Web API マイクロ サービスを basket.api コンテナー

-   basket.data REDIS キャッシュとしてバスケット データベースに REDIS cache サービスを実行中のコンテナー

### <a name="a-simple-web-service-api-container"></a>単純な Web サービス API コンテナー

1 つのコンテナーに焦点を当てた、catalog.api コンテナー マイクロ サービスを使うと、簡単な定義があります。

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

このコンテナー サービスには、次の基本的な構成があります。

-   カスタム eshop/catalog.api イメージに基づいています。 わかりやすくするために、ビルドはありません。 キー ファイルの設定。 つまり、イメージ必要がありますが既にビルドされて (docker ビルド) には任意の Docker レジストリから (コマンドを使用して、docker プル) ダウンロードされました。

-   カタログ データ モデルを含む SQL Server インスタンスにアクセスする Entity Framework で使用する接続文字列の ConnectionString をという名前の環境変数を定義します。 この場合、同じ SQL Server のコンテナーには、複数のデータベースが保持しています。 したがってより少ないメモリは、Docker 用に開発用コンピューターで必要。 ただし、マイクロ サービス データベースごとに 1 つの SQL Server のコンテナーを展開することもできます。

-   SQL Server 名は sql.data、Linux 用 SQL Server インスタンスが実行されているコンテナーで使用される同じ名前です。 これは、方法は便利です。この名前解決 (内部、Docker ホストへ) を使用できることを他のコンテナーにアクセスするコンテナーの内部 ip アドレスを知る必要はありません、ネットワーク アドレスが解決されます。

接続文字列が環境変数で定義されているため、別のメカニズムを使用し、別の時点でその変数を設定する可能性があります。 たとえば、最終的なホスト、または VSTS または優先 DevOps システムで、構成項目/CD パイプラインから手順を実行して、実稼働環境に展開するときに、別の接続文字列を設定できます。

-   内部サービスへのアクセス、catalog.api Docker ホスト内でポート 80 を公開します。 ホストは、Linux VM では現在 for Linux Docker イメージ上に基づきますが、代わりに、Windows イメージ上で実行するコンテナーを構成することもあるためです。

-   公開されているポート 80、Docker ホスト コンピューター (Linux VM) にポート 5101 コンテナー上を転送します。

-   Web サービスを sql.data サービス (コンテナーで実行されている Linux データベースの SQL Server のインスタンス) にリンクします。 この依存関係を指定すると、catalog.api コンテナーまでは起動しません sql.data コンテナーが既に開始します。これは重要なは、SQL Server データベースでセットアップを catalog.api 必要があるためされ実行されている最初です。 ただし、このようなコンテナーの依存関係は、不十分多くの場合、Docker は、コンテナー レベルでのみチェックがあるためです。 場合があります (このケースの SQL Server) でサービスされませんがあります対応、ために、クライアント microservices 指数バックオフによる再試行ロジックを実装することをお勧めします。 このように、依存関係のコンテナーが短時間では、準備されていない場合、アプリケーションは引き続きできます回復力のあります。

-   外部サーバーへのアクセスを許可するように構成されます: 余分な\_ホストの設定では、外部のサーバーまたは Docker ホストの外部でのマシンにアクセスすることができます (つまり、既定値は開発 Docker Linux VM の外部ホスト)、ローカルの SQL など開発 PC 上のサーバー インスタンスです。

またより高度な docker compose.yml 設定が、以下のセクションについて説明します。

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>使用して docker の構成ファイルを複数の環境を対象とする

Docker compose.yml ファイルは、定義ファイルし、その形式を理解している複数のインフラストラクチャで使用できます。 最も簡単なツールは、docker にコマンドの作成が、(たとえば、Docker Swarm) orchestrators も理解してそのファイルと同じようにその他のツールです。

使用して、そのため、docker の構成コマンドを次の主なシナリオを対象にできます。

#### <a name="development-environments"></a>開発環境

アプリケーションを開発するときに、分離開発環境でアプリケーションを実行できる必要があります。 使用することができます、docker-作成 CLI コマンドをその環境を作成または使用して docker-を構成するは背後で Visual Studio を使用します。

Docker compose.yml ファイルを使用すると、構成およびすべてのアプリケーションのサービスの依存関係 (その他のサービス、キャッシュ、データベース、キューなど) を文書化できます。 使用して、CLI コマンドを docker 構成、作成して 1 つのコマンドを使用してそれぞれの依存関係の 1 つまたは複数のコンテナーを開始 (docker で作成する)。

Docker compose.yml は Docker エンジンによって解釈される構成ファイルが、複数のコンテナー アプリケーションの構成に関する便利なドキュメント ファイルとしても機能します。

#### <a name="testing-environments"></a>テスト環境

継続的なデプロイ (CD) や継続的インテグレーション (CI) プロセスの重要な部分は、単体テストおよび統合テストです。 これらの自動テストでは、これらは、ユーザーまたはアプリケーションのデータに他の変更による影響を受けませんように分離された環境が必要です。

Docker Compose によるを作成してから、コマンド プロンプトまたはスクリプトは、次のコマンドと同様に、いくつかのコマンドで非常に簡単に分離された環境を破棄します。

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>運用展開

リモート Docker エンジンを展開する構成を行うこともできます。 一般的なケースは、1 つの Docker ホスト インスタンスを展開する (実稼働 VM またはサーバーを使用してプロビジョニング[Docker マシン](https://docs.docker.com/machine/overview/))。 全体の場合もありますが、 [Docker Swarm](https://docs.docker.com/swarm/overview/)クラスター、クラスターは、docker compose.yml ファイルとの互換性もあるためです。

その他の orchestrator (Azure Service Fabric、Mesos DC/OS、Kubernetes など) を使用している場合は、docker compose.yml、でもは他の orchestrator で必要な形式のものと同様のセットアップとメタデータの構成設定を追加する必要があります。

いずれの場合は、docker の構成で開発、テスト、運用環境のワークフローの場合に便利なツールとメタデータ形式が使用して orchestrator を運用環境のワークフローが異なる場合があります。

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>複数を使用して docker の構成ファイルを複数の環境を処理するには

さまざまな環境を対象とする場合は、複数を使用する必要がありますファイルを作成します。 これにより、環境に応じて複数の構成バリアントを作成できます。

#### <a name="overriding-the-base-docker-compose-file"></a>基本 docker-compose ファイルを上書き

前のセクションで示すように簡略化された例のように、1 つの docker compose.yml ファイルを使用する可能性があります。 ただし、ほとんどのアプリケーションは推奨はされません。

既定では、新規作成は、2 つのファイル、docker compose.yml および省略可能な docker compose.override.yml ファイルを読み取ります。 ように図 8-11 では、Visual Studio を使用する Docker のサポートを有効にすると、Visual Studio もが作成されるとそれらのファイルとその他のファイルのデバッグに使用します。

![](./media/image12.png)

**図 8. ~ 11.**です。 Visual Studio 2017 内のファイルを docker 構成します。

Visual Studio Code または Sublime などの任意のエディター docker-compose ファイルを編集し、アプリケーションを実行することができます、docker 構成コマンドします。

慣例により、docker compose.yml ファイルには、基本の構成とその他の静的な設定が含まれています。 つまり、サービスの構成が対象となる展開環境に合わせて変更しないでください。

Docker compose.override.yml ファイルには名前が示すように、デプロイ環境に依存するための構成など、基本構成をオーバーライドする構成設定が含まれています。 また複数のオーバーライド ファイルを異なる名前を持つことができます。 通常、オーバーライド ファイルには、環境または展開には特定のアプリケーションで必要な追加の情報が含まれます。

#### <a name="targeting-multiple-environments"></a>複数の環境を対象とします。

一般的なユース ケースが複数定義するときに作成ファイル CI、または開発、ステージング、実稼働環境でのように、複数の環境を対象できるようにします。 これらの相違点をサポートするためには、図 8-12 を示すように、複数のファイルを作成する構成を分割できます。

![](./media/image13.png)

**図 8-12**です。 複数の docker 構成ファイルの基本の docker compose.yml ファイル内の値をオーバーライドします。

基本の docker compose.yml ファイルから開始できます。 この基本ファイルに、環境に合わせて変更されないベース、または静的な構成設定が含まれています。 たとえば、eShopOnContainers では、基本ファイルとして次の docker compose.yml ファイルがあります。

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

基本 docker compose.yml ファイル内の値が別のターゲット展開環境のために変更しないでください。

たとえば、webmvc サービス定義に注目する場合、その情報は、どのような環境を対象とする可能性がありますに関係なくほとんど同じ方法を確認できます。 次の情報があります。

-   サービス名: webmvc です。

-   コンテナーのカスタム イメージ: eshop/webmvc です。

-   どの Dockerfile を使用することを示すカスタムの Docker イメージを構築するコマンドです。

-   他の依存関係のコンテナーが開始されるまで、このコンテナーが開始しないように、他のサービスに依存します。

追加の構成を持つことができますが、重要な点は、基本の docker compose.yml ファイルでだけします環境間で共通する情報を設定します。 Docker compose.override.yml または実稼働またはステージングの同様のファイルで、各環境に固有の構成を配置する必要があります。

通常、docker compose.override.yml は eShopOnContainers から次の例のように、開発環境に合わせて使用されます。

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

この例では開発の構成の上書きをホストにいくつかのポートを公開する、定義環境変数をリダイレクト Url、および開発環境の接続文字列を指定します。 これらの設定だけは、開発環境です。

実行すると、上の docker 構成 (または Visual Studio から起動)、コマンドの読み込みのオーバーライドに自動的に両方のファイルをマージした場合、します。

別の構成値を持つ、運用環境の別の構成ファイルを表示するとします。 次のように、別のオーバーライド ファイルを作成することができます。 (このファイル可能性がありますを別の Git リポジトリに格納されているか、管理および保護別のチームによって。)

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

#### <a name="how-to-deploy-with-a-specific-override-file"></a>特定のオーバーライド ファイルと共に展開する方法

を別の名前で複数のオーバーライド ファイル、またはオーバーライド ファイルを使用するのには、で-f オプションを使用することができます、docker にコマンドを作成し、ファイルを指定します。 コマンドラインで指定された順序でマージ ファイルを作成します。 次の例では、上書きファイルと共に展開する方法を示します。

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>環境変数の使用の docker の構成ファイル

特におが前の例に示すように、環境変数から構成情報を取得できる、実稼働環境では、便利です。 構文を使用して、docker-compose ファイルで環境変数を参照する\${MY\_VAR}。 Docker compose.prod.yml ファイルから次の行は、環境変数の値を参照する方法を示します。

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

環境変数が作成され、ホスト環境に応じて、さまざまな方法で初期化 (Linux、Windows、クラウド クラスターなどです。)。 ただし、便利な方法では、.env ファイルを使用します。 Docker-compose ファイルは、.env ファイルで既定の環境変数を宣言することをサポートします。 これらの環境変数の値は、既定値です。 それぞれ自分の環境の (ホスト OS またはクラスターから環境変数) で定義した値によってオーバーライドできます。 この .env ファイル、フォルダーに配置する場所、docker 構成からコマンドを実行します。

次の例は、.env ファイルと同様に、 [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers アプリケーション用のファイルです。

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

必要ですが、.env ファイルの形式での各行の docker 構成&lt;変数&gt;=&lt;値&gt;です。

常に、ランタイム環境で設定された値が .env ファイル内で定義されている値をオーバーライドすることに注意してください。 同様の方法で、コマンド ライン コマンド引数を介して渡される値は、.env ファイルで設定された既定値をオーバーライドします。

#### <a name="additional-resources"></a>その他の技術情報

-   **Docker の概要作成**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **複数の構成ファイル**
    [*https://docs.docker.com/compose/extends/\#複数を構成ファイル*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>ビルドは、ASP.NET Core Docker イメージを最適化します。

Docker と .NET Core は、インターネット上のソースの検索は、Dockerfile を示す、わかりやすくするためのコンテナーに、ソースをコピーして、Docker イメージの構築が表示されます。 これらの例では、単純な構成を使用するはできること、Docker イメージでは、アプリケーションにパッケージ化、環境を提案します。 次の例では、このに簡単な Dockerfile を示します。

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

次のように、Dockerfile は動作します。 ただし、特に実稼働イメージ、イメージを大幅に最適化できます。

コンテナーと microservices モデルでは、コンテナー継続的に開始します。 コンテナーの使用の一般的な方法では、コンテナーが破棄可能なために、スリープ状態のコンテナーは再起動しません。 Orchestrators (Docker Swarm、Kubernetes、DCOS または Azure Service Fabric) などは、単に、イメージの新しいインスタンスを作成します。 これは意味をインスタンス化のプロセスが向上するためのビルド時にアプリケーションをプリコンパイル最適化するために必要です。 コンテナーが開始されるは、実行できる状態にする必要があります。 ない復元し、実行時にコンパイルする必要があります、ビルドを使用した dotnet 復元と dotnet dotnet CLI からコマンドを .NET Core と Docker に関する多くのブログ投稿でします。

.NET チームに .NET Core と ASP.NET Core コンテナー用に最適化されたフレームワークを作成する重要な作業を行っています。 .NET Core は小規模メモリ フット プリント; を使用して軽量の framework だけでなく、します。チームが起動時のパフォーマンスに重点を置いて、ような一部の最適化の Docker イメージを生成、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)で使用できるイメージ[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)、比較、正規[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)または[microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile)イメージ。 [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) aspnetcore の自動設定を提供するイメージ\_url のポート 80 およびアセンブリの事前 ngend キャッシュに高速スタートアップと、これら両方の設定。

#### <a name="additional-resources"></a>その他の技術情報

-   **ビルド最適化 ASP.NET Core を使用してイメージを Docker**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>ビルド (CI) のコンテナーからのアプリケーションの作成

Docker のもう 1 つの利点は、事前に構成されたコンテナーからアプリケーションをビルドすることができます図 8-13 のため、ビルド コンピューターまたはアプリケーションをビルドする VM を作成する必要はありません。 使用したり、開発用コンピューターで実行してそのビルド コンテナーをテストできます。 新機能が、もっと興味深い CI (継続的インテグレーション) パイプラインから同じビルド コンテナーを使用することができます。

![](./media/image14.png)

**図 8-13**です。 コンポーネントをコンテナーから .NET ビットの構築

このシナリオでは、説明、 [microsoft/aspnetcore-ビルド](https://hub.docker.com/r/microsoft/aspnetcore-build/)イメージで、コンパイルし、ASP.NET Core アプリケーションの構築に使用することができます。 基づくイメージで出力を配置、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)前述のとおり、実行時の最適化されたイメージのイメージです。

Aspnetcore ビルド イメージには、.NET Core では、ASP.NET の SDK、npm など、ASP.NET Core アプリケーションをコンパイルするために必要なものが含まれている Bower、Gulp などです。

ビルド時にこれらの依存関係が必要です。 たくないアプリケーションでこれらを実行時に実行するために、イメージが不必要に大きなためです。 EShopOnContainers アプリケーションでは、アプリケーションをビルドすることができます、コンテナーだけを実行してから、次 docker-作成コマンド。

```
  docker-compose -f docker-compose.ci.build.yml up
```

図 8-14 では、コマンドラインで実行されているこのコマンドを示します。

![](./media/image15.png)

**図 8-14 です。** コンテナーから .NET アプリケーションのビルド

実行しているコンテナーが ci ビルドがわかるように、\_1 のコンテナーです。 これは、コンパイル、お使いの PC からの代わりにそのコンテナー内からアプリケーション全体をビルドできるように、aspnetcore ビルド イメージに基づいています。 理由は実際にはビルドおり Linux での .NET Core プロジェクトをコンパイルする、そのコンテナーが既定の Docker Linux ホストで実行されているためです。

[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml)ファイルは、そのイメージ (eShopOnContainers の一部) には、次のコードが含まれています。 ビルド コンテナーを使用して、開始されるを参照してください、 [microsoft/aspnetcore-ビルド](https://hub.docker.com/r/microsoft/aspnetcore-build/)イメージ。

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

* 以降で**.NET Core 2.0**、`dotnet restore`コマンドが自動的に実行されるときに、`dotnet publish`コマンドを実行します。

ビルド コンテナーが起動して稼働すると、.NET SDK dotnet 復元を実行し、dotnet は、.NET ビットをコンパイルするために、ソリューションのすべてのプロジェクトに対してコマンドを発行します。 この場合、eShopOnContainers では、クライアント コードの TypeScript および角に基づく、SPA もが、必要もあります npm での JavaScript の依存関係を確認するアクションが .NET bits に関連していないことがします。

Dotnet コマンド ビルドを発行する各プロジェクトのフォルダー内でコンパイルされた出力を発行していく、.図 8-15 を示す/obj/Docker/publish フォルダーです。

![](./media/image16.png)

**図 8 ~ 15 です。** バイナリ ファイルが、dotnet によって生成されたコマンドを発行します。

#### <a name="creating-the-docker-images-from-the-cli"></a>CLI から Docker イメージを作成します。

(各プロジェクトの場合) 内の関連するフォルダーに、アプリケーションの出力を発行すると、次の手順は、実際に Docker イメージを作成するは。 これを行うには、docker-compose ビルドを使用して、docker の構成コマンドを図 8 ~ 16 が示すようにします。

![](./media/image17.png)

**図 8 ~ 16 です。** Docker イメージを構築して、コンテナーを実行しています。

図 8-17、docker-compose がコマンドの実行を構築する方法を確認できます。

![](./media/image18.png)

**図 8-17**です。 Docker と Docker イメージを構築する-ビルド コマンドの作成

Docker-compose 間の違いは、ビルドおよびを docker 構成コマンドは、docker のビルドと開始のイメージの両方を作成します。

Visual Studio を使用すると、これらすべての手順は内部で実行されます。 Visual Studio、.NET アプリケーションをコンパイルするには、Docker イメージを作成および Docker ホストに、コンテナーを展開します。 Visual Studio では、Visual Studio から直接、Docker で実行されているのコンテナーをデバッグする機能など、追加の機能を提供します。

全体的な takeway をここでは、CI/CD パイプラインが構築する必要がある方法と同じようにアプリケーションをビルドできる: の代わりにローカル コンピューターからのコンテナーからです。 イメージを作成した後、だけ実行する必要が、docker を使用して、Docker イメージのコマンドを作成します。

#### <a name="additional-resources"></a>その他の技術情報

-   **コンテナーからのビットを構築します Windows CLI 環境 (dotnet CLI、Docker CLI と VS Code) で eShopOnContainers ソリューションをセットアップ**
    [*https://github.com/dotnet/eShopOnContainers/wiki/。03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[前](データのドリブン-crud-microservice.md) [次へ] (データベース サーバー container.md)
