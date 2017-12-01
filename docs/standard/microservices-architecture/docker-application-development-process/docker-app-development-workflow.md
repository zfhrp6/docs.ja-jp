---
title: "Docker のアプリの開発のワークフロー"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker のアプリの開発のワークフロー"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a>Docker のアプリの開発のワークフロー

アプリケーションの開発ライフ サイクルは、各開発者のマシンを開発者がコードを使用する言語を使用して、アプリケーションと、テストをローカルで開始されます。 どの言語、フレームワーク、および開発者が、このワークフローは、プラットフォームに関係なく、開発者は常に開発およびテストして、Docker コンテナーがローカルでこれ。

各コンテナー (Docker イメージのインスタンス) には、次のコンポーネントが含まれています。

-   オペレーティング システムの選択 (たとえば、Linux ディストリビューション、Windows Nano Server、または Windows Server Core)。

-   ファイル (アプリケーションのバイナリなど) は開発者が追加されました。

-   構成情報 (環境の設定と依存関係)。

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker コンテナー ベースのアプリケーションを開発するためのワークフロー

このセクションの内容について説明します、*内部ループ*Docker コンテナー ベースのアプリケーションでワークフローを開発します。 内部ループ ワークフローことを意味は加味していませんより広範な DevOps ワークフローだけでは開発者のコンピューターに、開発作業について説明します。 環境をセットアップする最初の手順が含まれているものが 1 回だけ実行されます。

アプリケーションは、独自のサービスと追加のライブラリ (依存関係) で構成されます。 通常行う Docker アプリケーションを構築するときに図 5-1 に示すように基本的な手順を次に示します。

![](./media/image1.png)

**図 5-1。** Docker コンテナー詰めアプリケーションを開発するためのステップ バイ ステップのワークフロー

このガイドでこのプロセス全体の詳細については、主要な手順の説明には、Visual Studio 環境に焦点を当てたです。

エディター/CLI 開発手法 (たとえば、Visual Studio Code と macos Docker CLI または Windows) を使用しているときに、Visual Studio を使用する場合よりも詳細には、通常、すべての手順を知る必要があります。 CLI 環境での作業の詳細については、電子書籍を参照してください[Microsoft プラットフォームとツールと Docker のコンテナー詰めアプリケーション ライフ サイクル](http://aka.ms/dockerlifecycleebook/)です。

Visual Studio 2015 または Visual Studio 2017 を使用しているときにこれらの手順の多くは自動的に処理、生産性を大幅に向上します。 これは、Visual Studio 2017 を使用して複数のコンテナー アプリケーションを対象とするときに特に当てはまります。 たとえば、1 つだけのマウス クリックでは、Visual Studio、Dockerfile と docker compose.yml ファイルを追加、プロジェクト、アプリケーションの構成を使用します。 Visual Studio でアプリケーションを実行するときに、Docker イメージを構築および Docker; で直接、複数のコンテナー アプリケーションを実行一度に複数のコンテナーをデバッグすることもできます。 これらの機能には、開発速度が上がります。

ただし、Visual Studio によって、これらの手順を自動化するためにだけないわけでは何が起こっているかを知る必要はありません docker の下。 そのため、方法を紹介内のすべてのステップを説明します。

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>手順 1. コーディングを開始し、初期アプリケーションまたはサービスの基準を作成

Docker アプリケーションを開発することは、Docker せずアプリケーションを開発する方法に似ています。 違いは、Docker の開発中に展開しているアプリケーションまたはサービス、ローカル環境での Docker コンテナー内で実行するテストです。 コンテナーには、Linux コンテナーまたは Windows コンテナーのいずれかを指定できます。

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio で、ローカル環境をセットアップします。

を開始するには、必ず確保[Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows がインストールされて、次の手順で説明したようにします。

[Docker for Windows CE を概要します。](https://docs.docker.com/docker-for-windows/)

さらに、Visual Studio 2017 年 1 をインストールする必要があります。 これは優先経由での Visual Studio 2015、Visual Studio Tools for Docker アドイン with Visual Studio 2017 がコンテナーのデバッグのサポートと同様に、Docker のサポートを高度なためです。 選択した場合、visual Studio 2017 は Docker のツールを含めます、 **.NET Core と Docker**図 5-2 に示すように、インストール中に負荷します。

![](./media/image3.png)

**図 5-2**です。 選択すると、 **.NET Core と Docker** Visual Studio 2017 セットアップ中にワークロード

(通常は .NET Core コンテナーの使用を計画している場合) での通常の .NET でアプリケーションをコーディングを開始して、アプリケーションで Docker を有効にすると、展開、および Docker でテストする前にします。 ただし、実際の環境となるし、問題をできるだけ早く検出できるため、できるだけ早く Docker で作業を開始することをお勧めします。 これを使用するように Visual Studio では、これを簡単に処理をほぼ感じる透過的な Docker のため、Visual Studio からの複数のコンテナー アプリケーションをデバッグするときに最適な例です。

### <a name="additional-resources"></a>その他の技術情報

-   **Docker for Windows CE の概要**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>手順 2. 既存の .NET 基本イメージに関連する Dockerfile を作成します。

を作成する各カスタム イメージの Dockerfile する必要がありますVisual Studio または Docker CLI を使用して手動でから自動的に展開するかどうかを展開するには、各コンテナーの Dockerfile が必要 (実行 docker と docker のコマンドを作成) します。 アプリケーションに 1 つのカスタム サービスが含まれている場合、1 つの Dockerfile 必要があります。 アプリケーション (microservices アーキテクチャ) のように複数のサービスが含まれている場合はサービスごとに 1 つの Dockerfile する必要があります。

Dockerfile は、アプリケーションまたはサービスのルート フォルダーに配置されます。 Docker を設定し、コンテナーで、アプリケーションまたはサービスを実行する方法を指示するコマンドが含まれています。 手動でコードで、Dockerfile を作成し、.NET の依存関係と共にプロジェクトに追加できます。

Visual Studio と Docker のツールでは、このタスクには、いくつかのマウス クリックが必要です。 という名前のオプションは Visual Studio 2017 で新しいプロジェクトを作成するときに**を有効にするコンテナー (Docker) サポート**ように、図 5-3。

![](./media/image5.png)

**図 5-3**です。 Visual Studio 2017 で新しいプロジェクトを作成する場合は、Docker のサポートを有効にします。

Visual Studio では、プロジェクト ファイルを右クリックし、オプションを選択して、新規または既存のプロジェクトでの Docker のサポートを有効にすることもできます**追加 Docker プロジェクトはサポート**図 5-4 に示すように、します。

![](./media/image6.png)

**図 5-4**です。 既存の Visual Studio 2017 プロジェクトでの Docker のサポートを有効にします。

(ASP.NET Web アプリケーションや Web API サービスの場合) などのプロジェクトでこの操作は、Dockerfile を必要な構成でプロジェクトに追加します。 また、ソリューション全体の docker compose.yml ファイルを追加します。 次のセクションでは、その各ファイルに書き込まれる情報について説明します。 Visual Studio は、この作業を行うことができますが、Dockerfile に何を理解すると便利です。

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>オプション a: 既存の公式 .NET Docker イメージを使用して、プロジェクトを作成します。

通常、公式のリポジトリから取得できます、基本イメージの上にコンテナーのカスタム イメージをビルドする、 [Docker Hub](https://hub.docker.com/)レジストリです。 ある正確に Visual Studio での Docker のサポートを有効にすると、バック グラウンドで動作します。 Dockerfile では、既存の aspnetcore イメージを使用します。

以前どの Docker images とフレームワークと選択した OS に応じて、使用できるリポジトリを説明します。 たとえば、ASP.NET Core (Linux または Windows) を使用する場合は、使用するイメージは、microsoft/aspnetcore:2.0 です。 したがって、のみ、どのようなコンテナーを使用する基本の Docker イメージを指定する必要があります。 Microsoft から追加することによって行うを/、Dockerfile を aspnetcore:2.0 です。 Visual Studio によって自動的に実行これがこの値を更新するバージョンを更新する場合は。

バージョン番号を Docker Hub からの公式の .NET イメージ リポジトリを使うと、同じ言語の機能が (開発、テスト、および実稼働環境を含む) すべてのマシンで使用できることができます。

次の例では、Dockerfile ASP.NET Core コンテナー用のサンプルを示します。

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

この場合、コンテナーは、バージョン 2.0 の公式の ASP.NET Core Docker イメージ (Linux と Windows のマルチ arch) に基づきます。 これは、設定`FROM microsoft/aspnetcore:2.0`です。 (この基本イメージに関する詳細については、次を参照してください、 [ASP.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/aspnetcore/)ページおよび[.NET Core Docker イメージ](https://hub.docker.com/r/microsoft/dotnet/)ページです。)。Dockerfile で (ここでは、ポート 80、公開設定で構成された) の実行時に使用する TCP ポートでリッスンするように Docker に指示する必要があります。

言語とを使用しているフレームワークによって、Dockerfile では、追加の構成設定を指定できます。 インスタンスでは、ENTRYPOINT 行\["dotnet"、"MySingleContainerWebApp.dll"\] .NET Core アプリケーションの実行に Docker に指示します。 SDK と .NET Core CLI (dotnet CLI) をビルドして、.NET アプリケーションの実行を使用している場合、この設定は別になります。 一番下の行が、エントリ ポイントの行とその他の設定になります、アプリケーション用に選択した言語とプラットフォームによって異なります。

### <a name="additional-resources"></a>その他の技術情報

-   **.NET Core アプリケーションの Docker イメージを構築**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)

-   **独自のイメージを構築**です。 Docker、公式のドキュメントです。
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>マルチ arch イメージ リポジトリを使用します。

1 つのリポジトリには、Linux イメージと Windows イメージなどのプラットフォームのバリエーションを含めることができます。 この機能は、Microsoft (基本イメージの作成者) のようなベンダーは (つまり、Linux および Windows) に複数のプラットフォームに対応する 1 つのリポジトリを作成するを使用します。 たとえば、 [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub レジストリに使用可能なリポジトリが同じリポジトリ名を使用して Linux および Windows Nano Server のサポートを提供します。

タグを指定すると、明示的なプラットフォームを対象とする場合は、次の場合と同様に。

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

しかし、これは、2017 中旬以降新しいを指定する場合、同じイメージの名前も、同じタグ (複数のアーキテクチャをサポートする aspnetcore イメージ) のような新しいマルチ arch イメージが展開して、Docker ホスト OS によって Linux または Windows のバージョンを使用して、、次の例で示すようにします。

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

この方法により、Windows ホストからイメージをプルするときは、その Windows バリアントをプルして、Linux バリアントがプルする Linux ホストから同じイメージの名前を取得します。

### <a name="option-b-creating-your-base-image-from-scratch"></a>オプション b: は最初から基本イメージを作成します。

独自 Docker の基本イメージは、最初から作成することができます。 Docker、によって開始しているユーザーに対してこのシナリオは推奨されませんが、独自の基本イメージの特定のビットを設定する場合は、これを行います。

### <a name="additional-resources"></a>その他の技術情報

-   **.NET Core イメージを複数 arch**です。
https://github.com/dotnet/announcements/issues/14 
-   **基本イメージを作成する**です。 Docker の正式なドキュメントです。
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>手順 3. カスタム Docker イメージを作成し、それらのアプリケーションまたはサービスを埋め込む

各サービスに対して、アプリケーションで、関連するイメージを作成する必要があります。 1 つのサービスまたは web アプリケーションのアプリケーションが構成されている場合は、1 つのイメージだけができます。

Docker images する用 Visual Studio でに自動的に構築されたに注意してください。 次の手順はのみエディター/CLI ワークフローに必要なし、わかりやすくするための下にどうなるかについて説明します。

Developer、する必要がありますプッシュ、完了するまでにローカルで開発およびテスト機能、または (GitHub) する場合など、ソース管理システムに変更します。 これは、Docker イメージを作成してローカルの Docker ホスト (Windows または Linux VM) にコンテナーを展開して実行、テスト、およびそれらのコンテナーをローカルでデバッグする必要があることを意味します。

Docker CLI と、Dockerfile を使用して、ローカル環境でカスタム イメージを作成するには、docker のビルド コマンド、図 5-5 を使用することができます。

![](./media/image8.png)

**図 5-5**です。 カスタム Docker イメージを作成します。

必要に応じて、プロジェクト フォルダーから docker ビルドを直接実行するには、代わりに最初に、必要な .NET ライブラリの配置可能なフォルダーを生成することができ、dotnet を実行して、バイナリは、発行、および、docker ビルド コマンドを使用します。

Docker イメージを作成、名前 cesardl/netcore-webapi-マイクロ サービスをこれには-docker: 最初。 この例では、: 特定のバージョンを表すタグを 1 つ目はします。 カスタム イメージが構成される Docker アプリケーションを作成する必要がありますごとには、この手順を繰り返します。

複数のコンテナーのアプリケーションが行われる場合 (つまり、これがマルチ コンテナー アプリケーションの場合)、使用することも、--関連で公開されるメタデータを使用して単一のコマンドですべての関連するイメージを作成するビルドのコマンドを docker 構成docker compose.yml ファイル。

既存のイメージ、ローカル リポジトリに docker を使用してイメージ コマンドは検索できます、図 5-6 に示すようにします。

![](./media/image9.png)

**図 5 ~ 6 です。** Docker イメージのコマンドを使用して既存のイメージを表示します。

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio で Docker イメージを作成します。

Visual Studio を使用して、Docker のサポートでプロジェクトを作成する場合は、明示的に作成しないイメージ。 代わりに、f5 キーを押して dockerized アプリケーションまたはサービスを実行するのイメージが作成されます。 この手順は Visual Studio で、自動と、発生することは表示されませんが行われている内容を知ることは重要であるにします。

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>手順 4. 複数のコンテナー Docker アプリケーションを構築するときに docker compose.yml で、サービスを定義します。

[Docker compose.yml](https://docs.docker.com/compose/compose-file/)ファイルでは、デプロイ コマンドで構成されるアプリケーションとして配置するのには関連するサービスのセットを定義することができます。

Docker compose.yml ファイルを使用するには、次の例に似たコンテンツを持つ、主にファイルまたはソリューションのルート フォルダーを作成する必要があります。

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

この docker compose.yml ファイルに簡略化し、マージされたバージョンがあることに注意してください。 接続文字列のように、デプロイ環境に依存している構成情報に加えて、常に適用される (など、カスタム イメージの名前)、各コンテナーの静的構成データが含まれています。 以降のセクションで、docker compose.yml 構成に複数の分割方法を学習は docker 構成ファイルと環境と実行の種類 (デバッグまたはリリース) によってオーバーライド値。

Docker compose.yml ファイルの例は、5 つのサービスを定義します。 webmvc サービス (web アプリケーション)、2 つの microservices (catalog.api および ordering.api)、および 1 つのデータ ソース コンテナー、sql.data、コンテナーとして実行されている Linux に SQL Server に基づいています。 各サービスは、Docker イメージはそれぞれに必要なため、コンテナーとして配置されます。

Docker compose.yml ファイルは、どのようなコンテナーを使用しているだけでなく、個別の構成方法を指定します。 たとえば、webmvc コンテナー ファイル内の定義、.yml:

-   構築済み eshop を使用して/web: 最新バージョンのイメージです。 ただしを構成することも、イメージの一部として作成される、docker 構成ビルドに基づいて実行を追加の構成: docker-compose ファイル内のセクションです。

-   2 つの環境変数 (CatalogUrl および OrderingUrl) を初期化します。

-   公開されているポート 80、ホスト コンピューター上の外部ポート 80 をコンテナー上を転送します。

-   カタログと順序付けのサービスに web アプリをリンク、依存\_設定にします。 これにより、それらのサービスを開始するまで待機するサービスです。

お microservices と複数のコンテナーのアプリを実装する方法について説明しているときに後のセクションで、docker compose.yml ファイルを再確認します。

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Visual Studio 2017 での docker compose.yml の操作

図 5-7 に示すように、Visual Studio ソリューションでサービス プロジェクトに Docker ソリューションのサポートを追加する場合は、Visual Studio がプロジェクトに Dockerfile を追加し、docker compose.yml ファイルとソリューションのサービス セクション (プロジェクト) を追加します。 これは、複数のコンテナー ソリューションの作成を開始する簡単な方法です。 Docker compose.yml ファイルを開くし、それらを他の機能も更新します。

![](./media/image6.png)

**図 5-7**です。 ASP.NET Core プロジェクトを右クリックして Visual Studio 2017 で Docker のサポートを追加します。

Visual Studio での Docker のサポートを追加するだけでなく、Dockerfile をプロジェクトに追加、構成情報をソリューション レベルで設定されているいくつかのグローバル docker compose.yml ファイルに追加します。

Visual Studio でソリューションに Docker のサポートを追加した後は、図 5-8 に示すように、追加の docker compose.yml ファイルを含むソリューション エクスプ ローラーで新しいノード (docker compose.dcproj プロジェクト ファイル) にも表示されます。

![](./media/image11.PNG)

**図 5-8**です。 **Docker 構成**ツリー ノードを Visual Studio 2017 のソリューション エクスプ ローラーの追加

使用して単一の docker compose.yml ファイルを使用して複数のコンテナー アプリケーションを展開する可能性があります、docker にコマンドを作成します。 環境 (運用と開発) と実行によっての値をオーバーライドするために、Visual Studio がそれらのグループを追加するただし、型 (デバッグとリリース)。 この機能は、以降のセクションで説明されます。

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>手順 5. ビルドおよび実行する、Docker アプリケーション

アプリケーションの 1 つのコンテナーのみの場合は、Docker ホスト (仮想マシンまたは物理サーバー) に展開することで実行できます。 ただし、アプリケーションに複数のサービスが含まれている場合として展開できますが、構成されたアプリケーションを 1 つの CLI コマンドを使用するか (docker の構成を)、または Visual Studio が、内部的には、そのコマンドを使用します。 さまざまなオプションを見てみましょう。

### <a name="option-a-running-a-single-container-with-docker-cli"></a>オプション a: Docker CLI での単一のコンテナーの実行

Docker run コマンド、図 5 ~ 9 を使用して Docker コンテナーを実行することができます。

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**図 5-9**です。 Docker run コマンドを使用して Docker コンテナーの実行

ここでは、コマンドは、ホスト コンピューターのポート 80 をコンテナーの内部ポート 5000 をバインドします。 これには、ホストがポート 80 でリッスンしていると、コンテナーに 5000 のポートに転送することを意味します。

### <a name="option-b-running-a-multi-container-application"></a>オプション b: 複数のコンテナー アプリケーションを実行します。

ほとんどのエンタープライズ シナリオで Docker アプリケーションはで構成される複数のサービスは図 5 ~ 10 に示すように複数のコンテナーのアプリケーションを実行する必要があります。

![](./media/image14.png)

**図 5-10**です。 展開されている Docker コンテナーでの VM

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Docker CLI を使用して複数のコンテナー アプリケーションを実行します。

Docker を実行するアプリケーションを実行する、複数のコンテナー Docker CLI を使用してのコマンドを作成します。 マルチ コンテナー アプリケーションを展開するソリューション レベルであるこのコマンドは docker compose.yml ファイルです。 図 5-11 は、docker compose.yml ファイルを含む、メイン プロジェクト ディレクトリから、コマンドを実行する場合、結果を示します。

![](./media/image15.png)

**図 5-11**です。 例の結果は実行されている場合、コマンドを docker 構成

Docker の後にコマンドの実行を作成、VM 形式を図 5 ~ 10 に示すように、Docker ホストに展開されたアプリケーションとその関連するコンテナーです。

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>実行していると、Visual Studio での複数のコンテナー アプリケーションのデバッグ 

Visual Studio 2017 を使用して複数のコンテナー アプリケーションを実行する単純なを取得できません。 ことができます実行だけでなく、複数のコンテナー アプリケーションが標準のブレークポイントを設定して Visual Studio から直接のすべてのコンテナーをデバッグすることです。

前述のたびに、ソリューション内のプロジェクトに Docker ソリューションのサポートを追加する前に、そのプロジェクトがソリューション全体を一度にデバッグまたは実行することができます、グローバル (ソリューション レベル) docker compose.yml ファイルで構成されます。 Visual Studio は Docker ソリューションのサポートが有効になっているプロジェクトごとに 1 つのコンテナーを起動し、内部のすべての手順を実行する (dotnet 発行、docker ビルドなどです。)。

ここで重要なは、図 5-12 に示すように、Visual Studio 2017 では、追加**Docker**コマンドで、F5 キーを操作します。 このオプションでは、ソリューション レベルで docker compose.yml ファイルで定義されているすべてのコンテナーを実行して、複数のコンテナー アプリケーションをデバッグまたは実行できることができます。 複数のコンテナー ソリューションをデバッグする機能にすると複数のブレークポイント、それぞれのブレークポイントを設定するには、別のプロジェクト (コンテナー) で Visual Studio からのデバッグ中には、別々 のプロジェクトで定義されているしで実行されているブレークポイントで停止別のコンテナーです。

![](./media/image16.png)

**図 5-12**です。 Visual Studio 2017 で複数のコンテナーのアプリの実行

### <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET コンテナー ホストに展開してリモート Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>テストと orchestrators と展開に関する注意事項

Docker 構成し、実行 docker コマンド (またはを実行していると Visual Studio でのコンテナーのデバッグ) が適切では、開発環境でコンテナーをテストします。 対象としている Docker クラスター orchestrators などの Docker Swarm 続き DC/OS、Kubernetes 場合に、このアプローチを使用しないでください。 ようにクラスターを使用している場合[Docker Swarm モード](https://docs.docker.com/engine/swarm/)(以降で使用可能で Docker CE および Windows 用の Mac バージョン 1.12)、する必要があります配置およびテストのような追加のコマンドで[docker サービスを作成](https://docs.docker.com/engine/reference/commandline/service_create/)の1 つのサービスです。 使用する場合は、複数のコンテナーから成るアプリケーションを展開する場合は、[バンドルを作成する docker](https://docs.docker.com/compose/reference/bundle/)と[docker 展開 myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/)として構成されたアプリケーションを配置する、*スタック*. 詳細については、ブログの投稿を参照してください。 [Introducing 実験的な分散アプリケーションのバンドル](https://blog.docker.com/2016/06/docker-app-bundle/)Docker のドキュメントにします。 Docker のサイトです。

[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)と[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/)さまざまな展開コマンドおよびスクリプトも使用します。

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>手順 6. Docker をローカルの Docker ホストを使用してアプリケーションをテストします。

この手順は、アプリケーションの実行内容によって異なります。 1 つのコンテナーまたはサービスとして展開されている単純な .NET Core の Web アプリケーションで Docker ホストのブラウザーを開き、図 5-13 ように、そのサイトに移動して、サービスにアクセスすることができます。 (場合は、Dockerfile の構成は、ポート 80 以外のものであるホストに、コンテナーをマップ ホスト ポスト URL に含める。)

![](./media/image18.png)

**図 5-13**です。 Localhost を使用してローカルで Docker アプリケーションのテストの例

Docker を localhost をポイントしていない場合は、IP をホスト (既定では、Docker の CE を使用する場合、その必要があります)、サービスに移動するには、マシンのネットワーク カードの IP アドレスを使用します。

ブラウザーでこの URL が説明されている例では、特定のコンテナーをポート 80 を使用することに注意してください。 ただし、内部的には、要求にリダイレクトされます-port 5000、前の手順で説明するよう、docker run コマンド、付きで展開されて方法があるためです。

図 5-14 に示すように、ターミナルから curl を使用してアプリケーションをテストすることもできます。 Windows 上の Docker のインストール、使用する既定値の Docker ホストの IP とは、常にコンピューターの実際の IP アドレスに加えて 10.0.75.1 です。

![](./media/image19.png)

**図 5-14**です。 Curl を使用してローカルで Docker アプリケーションのテストの例

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>テストと Visual Studio 2017 とコンテナーのデバッグ

実行するいると、Visual Studio 2017 とコンテナーのデバッグ、するコンテナーせずに実行する場合と、ほぼ同じ方法で、.NET アプリケーションをデバッグできます。

### <a name="testing-and-debugging-without-visual-studio"></a>テストと、Visual Studio を使用せずにデバッグ

エディター/CLI アプローチを使用して、開発する場合はより困難にコンテナーのデバッグとトレースを生成することでデバッグします。

### <a name="additional-resources"></a>その他の技術情報

-   **ローカルの Docker コンテナーでアプリをデバッグ**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker です。ビルド、デバッグ、Docker を使用した ASP.NET Core アプリを展開します。** ビデオ。
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio でのコンテナーを開発するときに、簡略化されたワークフロー

実際には、Visual Studio を使用するときに、ワークフローは、エディター/CLI アプローチを使用する場合よりもはるかに簡単です。 Dockerfile に関連するほとんどの Docker で必要な手順と docker compose.yml ファイルが非表示または図 5-15 に示すように、Visual Studio によって簡略化します。

![](./media/image20.png)

**図 5-15**です。 Visual Studio で開発するときに、簡略化されたワークフロー

さらに、手順 2. (プロジェクトに追加する Docker のサポート) を 1 回だけ実行する必要があります。 したがって、.NET を使用して、その他の開発時に、ワークフローは、通常開発タスクに似ています。 何が起こって (イメージ ビルド プロセス、どのような基本イメージを使用する、コンテナーなどの展開) の背後および場合によっては、Dockerfile またはファイルを編集 docker compose.yml の動作をカスタマイズする必要がありますも知っている必要があります。 ほとんどの作業がよりもずっと生産性を向上するので、Visual Studio を使用して、大幅に簡略化します。

### <a name="additional-resources"></a>その他の技術情報

-   **Steve Lasker です。Visual Studio 2017 を使用した .NET docker 開発**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz です。Visual Studio の新しい Docker ツールを使用して、コンテナーに置かれる .NET Core アプリ**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Dockerfile の PowerShell コマンドを使用して Windows コンテナーを設定するには 

[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)を Docker イメージに、既存の Windows アプリケーションを変換し、Docker エコシステムの残りの部分と同じツールを使用して展開できます。 Windows コンテナーを使用するには、PowerShell コマンドで実行する、Dockerfile では、次の例で示すように。

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

ここでは、私たちは Windows Server Core 基本イメージ (FROM の設定) を使用して、PowerShell コマンド (実行の設定) を使用して IIS をインストールします。 同様の方法で ASP.NET 4.x、.NET 4.6、またはその他の Windows ソフトウェアなどの追加コンポーネントを設定する PowerShell コマンドを使用することもできません。 たとえば、Dockerfile に次のコマンドは、ASP.NET 4.5 を設定します。

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>その他の技術情報

-   **aspnet-docker/Dockerfile です。** Windows の機能を組み込む dockerfile からを実行する Powershell コマンドの例です。
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[前](index.md) [次へ] (../net-core-single-containers-linux-windows-server-hosts/index.md)
