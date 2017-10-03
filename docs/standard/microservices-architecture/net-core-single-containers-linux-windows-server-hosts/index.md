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
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: a50c2ad3183c80fd76e6db042674e49367d7ffc9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Linux または Windows Nano Server ホスト上で 1 つのコンテナー ベースの NET Core Web アプリケーションを展開する

*Docker コンテナーは、単純な Web アプリケーションのモノリシックな展開に使用できます。これにより継続的な統合と継続的な展開のパイプラインが向上し、展開から実稼働を成功に導くのために役立ちます。"自分のコンピューターでは動作するのに実稼働環境では動作しないのはなぜ" と悩むことがなくなります。*

マイクロサービスベースのアーキテクチャには、多くの利点がありますが、それらの利点のために複雑さが増加します。 場合によっては、コストが利点を上回り、1 つのコンテナーまたは少数のコンテナーで実行されているモノリシック展開アプリケーションの方が有効なことがあります。 

モノリシック アプリケーションを適切に区切られたマイクロサービスに簡単に分解できない場合があります。 これらは機能別にパーティション化する必要があることは学習しました。マイクロサービスは相互に独立して起動することで、より回復力のあるアプリケーションを提供します。 アプリケーションの機能のスライスを提供できない場合、分割しても複雑さが増加するだけです。

場合によっては、アプリケーションを機能に依存せずに拡張できる必要があります たとえば、eShopOnContainers 参照アプリケーションの有効期間の早い段階で、トラフィックには、機能を複数の異なるマイクロサービスに分割する理由がないとします。 トラフィックは、十分に小さく、1 つのサービスにリソースを追加することは、一般的にすべてのサービスにリソースを追加することを意味しました。 アプリケーションを個別のサービスに分割する追加の作業からは最小限のメリットしか得られませんでした。

さらにアプリケーション開発の早い段階では、自然の機能的な境界を明確に把握できないことがあります。 最小の実行可能な製品を開発したときには、自然な境界がまだ明らかにならないことがあります。

これらの条件の一部は、一時的な可能性があります。 最初にモノリシック アプリケーションを作成し、後で一部の個別の機能を開発して、マイクロサービスとして展開する場合があります。 その他の条件はアプリケーションの問題の領域に不可欠な場合があります。つまり、アプリケーションを複数マイクロサービスに分割しない場合があります。

多くの個別のプロセスにアプリケーションを分割すると、オーバーヘッドも発生します。 別のプロセスに機能を分離することで、複雑さが増します。 通信プロトコルはより複雑になります。 メソッドの呼び出しではなく、サービス間の非同期通信を使用する必要があります。 マイクロサービス アーキテクチャに移動するきには、eShopOnContainers アプリケーションのマイクロサービス バージョンに実装される多くの構築ブロックを追加する必要があります。つまり、イベント バスの処理、メッセージの回復性と再試行、最終的な整合性などです。

EShopOnContainers の大幅に簡略化したバージョン (名前付き[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) で同じ GitHub リポジトリに含まれる) は、モノリシックな MVC アプリケーションとして実行され、説明したように、この設計を選択するといくつか利点が提供されます。 GitHub からこのアプリケーションのソースをダウンロードして、ローカルで実行できます。 このモノリシック アプリケーションは、コンテナー環境で展開すると有益です。

1 つは、コンテナー化した展開は、アプリケーションのすべてのインスタンスが同じ環境で実行されることを意味します。 これには、初期のテストと開発を行う開発者環境が含まれます。 開発チームは、実稼働環境に一致するコンテナー化した環境でアプリケーションを実行できます。

さらに、コンテナー化アプリケーションは低コストでスケールアウトされます。 先ほど見たように、コンテナー環境では、従来の VM 環境よりも多くのリソースを共有できます。

最後に、アプリケーションのコンテナー化は、強制的にビジネス ロジックと記憶域サーバーの間を分離します。 アプリケーションのスケール アウト時には、複数のコンテナーはすべて単一の物理記憶域メディアに移動します。 通常、SQL Server データベースを実行している高可用性サーバーになります。

## <a name="application-tour"></a>アプリケーション ツアー

[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) アプリケーションでは、モノリシック アプリケーション (.NET Core で実行されている ASP.NET Core MVC ベースのアプリケーション) として実行されているいくつかの eShopOnContainers アプリケーションを表します。 主に、前のセクションで説明したカタログ参照機能を提供します。

アプリケーションは、カタログ ストレージのために SQL Server データベースを使用します。 コンテナー ベースの展開では、このモノリシックなアプリケーションはマイクロサービス ベースのアプリケーションと同じデータ ストアにアクセスできます。 アプリケーションはモノリシック アプリケーションと共にコンテナー内で SQL Server を実行するように構成されます。 実稼働環境では、SQL Server は、Docker ホストの外部の高可用性コンピューターで実行されます。 開発またはテスト環境の利便性のために、独自のコンテナーで SQL Server を実行することをお勧めします。

初期機能セットは、カタログの参照のみを有効にします。 更新プログラムは、コンテナー化アプリケーションの完全な機能セットを有効にします。 モノリシックな Web アプリケーションのアーキテクチャの詳細については、「[ASP.NET Web Application architecture practices](https://aka.ms/webappebook)」(ASP.NET Web アプリケーションのアーキテクチャのプラクティス) 電子ブックおよび関連する [eShopOnWeb サンプル アプリケーション](http://aka.ms/WebAppArchitecture) を参照してください。ただし、その場合は、シナリオは ASP.NET Core を使用した一般的な Web 開発に焦点を当てているため Docker コンテナー上では実行されていません。

ただし、Docker コンテナーで実行される eShopOnContainers (eShopWeb) で簡略化されたバージョンを使用できます。

## <a name="docker-support"></a>Docker のサポート

eShopOnWeb プロジェクトは、.NET Core で実行されます。 そのため、Windows ベースまたは Linux ベースのコンテナーで実行できます。 Docker の展開の場合、SQL Server に同じホストの種類を使用する必要があります。 Linux ベースのコンテナーは、小さなフット プリントが可能なので優先されます。

Visual Studio には、ソリューションに Docker のサポートを追加するプロジェクト テンプレートが用意されています。 プロジェクトを右クリックし、[**追加**] をクリックして、その後に [**Docker サポート**] を選択します。 テンプレートでは、Dockerfile をプロジェクトに追加し、最初に使用する docker compose.yml ファイルを提供する新しい **docker-compose** プロジェクトを追加します。 GitHub からダウンロードする eShopOnWeb プロジェクトでは、この手順は既に実行されています。 図 6-1 に示すように、ソリューションに **eShopOnWeb** プロジェクトおよび **docker-compose** プロジェクトが含まれています。

![](./media/image1.png)

**図 6-1**。 単一コンテナーの Web アプリケーションの **docker-compose** プロジェクト

これらのファイルは、すべての Docker プロジェクトと一貫性のある標準の docker-compose ファイルです。 これらは、Visual Studio で、またはコマンドラインから使用できます。 このアプリケーションは、.NET Core で実行され、Linux コンテナーを使用するため、Mac または Linux マシンでコーディング、ビルド、および実行できます。

docker-compose.yml ファイルには、どのようなイメージをビルドしてどのようなコンテナーを起動するかに関する情報が含まれています。 テンプレートでは、eshopweb イメージを構築して、アプリケーションのコンテナーを起動する方法を指定します。 依存関係のイメージ (たとえば mssql-server-linux) を含めることによって、SQL Server 上の依存関係を追加する必要があり、コンテナーをビルドして起動するために Docker 用の sql.data イメージのサービスを追加する必要があります。 これらの設定を次の例に示します。

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

depends\_on ディレクティブは、eShopWeb イメージが sql.data イメージに依存することを Docker に指示します。 その下の行は、microsoft/mssql-server-linux イメージ使用して、sql.data をターゲットとするイメージを構築する手順です。

**docker-compose** プロジェクトは、メインの docker-compose.yml ノードの下に他の docker-compose ファイルを表示し、これらのファイルが関連付けられていることを視覚的に示します。 docker-compose-override.yml ファイルには、接続文字列、他のアプリケーション設定などの両方のサービスの設定が含まれています。

次の例では、Visual Studio でのデバッグに使用される設定を含む docker compose.vs.debug.yml ファイルを示します。 このファイルでは、eshopweb イメージに dev タグが追加されています。 これは、リリース イメージからデバッグを分離するために役立ち、運用環境にデバッグ情報を誤って展開しないようにします。

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

追加された最後のファイルは、docker compose.ci.build.yml です。 これを、コマンドラインから使用し、CI サーバーからプロジェクトをビルドします。 この構成ファイルでは、アプリケーションに必要なイメージを構築する Docker コンテナーを開始します。 docker-compose.ci.build.yml ファイルの内容の例を次に示します。

```yml
version: '2'
  
services:
  ci-build:
    image: microsoft/aspnetcore-build:1.0-1.1
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

イメージは、ASP.NET Core ビルド イメージであることに注意してください。 そのイメージには、アプリケーションをビルドし、必要なイメージを作成するための SDK とビルド ツールが含まれています。 このファイルを使用して、**docker-compose** プロジェクトを実行すると、イメージからビルド コンテナーが開始され、そのコンテナー内でアプリケーションのイメージが構築されます。 その docker-compose ファイルをコマンドラインの一部として指定し、Docker コンテナーでアプリケーションをビルドしてからこれを起動します。

Visual Studio で、**docker-compose** プロジェクトをスタートアップ プロジェクトとして選択して、Docker コンテナーでアプリケーションを実行し、その後で他のアプリケーションと同じように、Ctrl キーを押しながら F5 キー (デバッグのための F5) を押すことができます。 **docker-compose** プロジェクトを開始すると、Visual Studio が docker-compose.yml ファイル、docker-compose.override.yml ファイル、およびいずれかの docker-compose.vs.\* ファイルを使用して **docker-compose** を実行します。 アプリケーションが開始されると、Visual Studio がブラウザーを起動します。

デバッガーでアプリケーションを起動した場合、Visual Studio は、Docker で実行中のアプリケーションに接続します。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、コンテナーをローカルで実行した場合に発生する可能性があるいくつかの問題と、推奨される解決方法について説明します。

### <a name="stopping-docker-containers"></a>Docker コンテナーを停止する 

コンテナー化アプリケーションを起動した後、デバッグを停止した後もコンテナーは引き続き実行されます。 コマンドラインから docker ps コマンドを実行し、どのコンテナーが実行されているを確認できます。 docker stop コマンドは、図 6-2 に示すように、実行中のコンテナーを停止します。

![](./media/image2.png)

**図 6-2**。 docker ps および docker stop CLI コマンドを使用したコンテナーの一覧表示と停止

場合によっては、さまざまな構成を切り替えるときにプロセスの実行を停止する必要があります。 それ以外の場合、Web アプリケーションを実行しているコンテナーは、アプリケーション用のポート (この例では 5106) を使用します。

### <a name="adding-docker-to-your-projects"></a>Docker をプロジェクトに追加する

Docker のサポートを追加するウィザードは、実行中の Docker プロセスと通信します。 ウィザードを起動するときに、Docker が実行されていない場合、ウィザードは正しく実行されません。 さらに、ウィザードでは、正しい Docker のサポートを追加するためにコンテナーの現在の選択について説明します。 Windows コンテナーのサポートを追加する場合は、Windows コンテナーが構成された状態で Docker が実行されているときに、ウィザードを実行する必要があります。 Linux コンテナーのサポートを追加する場合は、Linux コンテナーが構成された状態で Docker が実行されているときに、ウィザードを実行する必要があります。

>[!div class="step-by-step"]
[Previous] (../docker-application-development-process/docker-app-development-workflow.md) [Next] (../containerize-net-framework-applications/index.md)

