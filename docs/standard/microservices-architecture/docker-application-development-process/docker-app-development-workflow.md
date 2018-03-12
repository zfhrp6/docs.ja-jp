---
title: "Docker アプリの開発ワークフロー"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker アプリの開発ワークフロー"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8537b1db27f512ec0bfc2f23589efe8199ca3287
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="development-workflow-for-docker-apps"></a>Docker アプリの開発ワークフロー

アプリケーション開発のライフサイクルは、各開発者のコンピューターで開始されます。このとき、アプリケーションは、開発者は好みの言語で記述され、ローカルでテストされます。 このワークフローでは、開発者が選択している言語、フレームワークおよびプラットフォームにかかわらず、常に Docker コンテナーはローカルで開発およびテストされます。

各コンテナー (Docker イメージのインスタンス) には、次のコンポーネントが含まれています。

-   選択したオペレーティング システム (例: Linux ディストリビューション、Windows Nano Server、または Windows Server Core)。

-   開発者が追加したファイル (アプリケーションのバイナリなど)。

-   構成情報 (環境の設定および依存関係)。

## <a name="workflow-for-developing-docker-container-based-applications"></a>Docker のコンテナー ベースのアプリケーションを開発するためのワークフロー

このセクションでは、Docker のコンテナー ベースのアプリケーションの*内側のループ*の開発ワークフローについて説明します。 内側のループのワークフローとは、DevOps のより全体的なワークフローではなく、開発者のコンピューター上で実行される開発作業のみを意味しています。 環境を設定する初期手順は、一度のみ実行されるものなので含まれていません。

アプリケーションは、自分のサービスと追加のライブラリ (依存関係) で構成されます。 Docker アプリケーションを構築するときの基本手順を次の図 5-1 に示します。

![](./media/image1.png)

**図 5-1** Docker のコンテナー化されたアプリケーションを開発するための詳細なワークフロー

このガイドでは、すべての手順が詳細に記載されており、主要な各手順は、Visual Studio の環境を使用して説明しています。

エディターと CLI を使用する開発手法 (例: Visual Studio Code と macOS または Windows 上の Docker CLI) を使用する場合、Visual Studio を使用する場合よりも、通常はより詳細に全手順を把握している必要があります。 CLI 環境での作業の詳細については、電子書籍、「[Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/)」 (Microsoft のプラットフォームおよびツールとコンテナー化された Docker アプリケーションのライフサイクル) を参照してください。

Visual Studio 2015 または Visual Studio 2017 を使用している場合、これらの手順の多くは自動処理されるので、生産性が大幅に向上します。 これは、Visual Studio 2017 で、複数のコンテナー アプリケーションを対象としているとき特にそうです。 たとえば、マウスを 1 回クリックするだけで、Visual Studio では、アプリケーションに適した構成で Dockerfile と docker-compose.yml ファイルをプロジェクトに追加できます。 そのアプリケーションを Visual Studio で実行すると、Docker イメージが構築され、Docker で直接マルチコンテナー アプリケーションが実行されます。また、一度に複数のコンテナーをデバッグすることもできます。 これらの機能により、開発の速度が向上します。

ただし、Visual Studio によって、これらの手順が自動化されるからといって、Docker の背後で何が起こっているのか知らなくてもよいというわけではありません。 そのため、次のガイダンスでは、各手順を詳細に説明します。

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>手順 1. コーディングを開始して、初期アプリケーションまたはサービス ベースラインを作成します。

Docker アプリケーションの開発方法は、Docker を使用しないアプリケーションの開発方法と似ています。 違いは、Docker 用を開発している場合、ローカル環境で Docker コンテナー内で実行するアプリケーションまたはサービスを開発またはテストするということです。 コンテナーには、Linux コンテナーまたは Windows コンテナーのいずれも使用できます。

### <a name="set-up-your-local-environment-with-visual-studio"></a>Visual Studio でのローカル環境のセットアップ

最初に、次の手順で説明する、Windows 用の [Docker Community Edition (CE)](https://www.docker.com/community-edition) がインストールされていることを確認します。

[Get started with Docker CE for Windows](https://docs.docker.com/docker-for-windows/) (Windows 用の Docker CE の概要)

Visual Studio 2017 もインストールされている必要があります。 Visual Studio 2017 には、コンテナーのデバッグのサポートなど、Docker をサポートするより高度な機能があるため、Visual Studio Tools for Docker アドインが組み込まれた Visual Studio 2015 よりも適しています。 Visual Studio 2017 には、インストール時に **.NET Core と Docker** ワークロードを選択した場合、図 5-2 のように Docker 用のツールが含まれます。

![](./media/image3.png)

**図 5-2** Visual Studio 2017 のセットアップ時の **.NET Core と Docker** ワークロードの選択

アプリケーションのコーディングは、アプリケーションで Docker を有効にし、Docker を展開してテストする前から、単純な .NET で開始することができます (コンテナーを使用する計画がある場合、通常は .NET Core)。 ただし、実際の環境となることに加え、問題が早く検出されるため、できるだけ早く Docker で作業を開始することをお勧めします。 Docker は、Visual Studio では、ほとんど透過的で、使用しやすくなっているため、このようにすることが推奨されます。この最良の例は、Visual Studio からのマルチコンテナー アプリケーションのデバッグです。

### <a name="additional-resources"></a>その他の技術情報

-   **Get started with Docker CE for Windows (Docker CE for Windows の概要)**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>手順 2. 既存の .NET 基本イメージに関連する Dockerfile を作成します。

Dockerfile は、構築するカスタム イメージごとに必要です。また、Visual Studio から自動的に展開する場合も、Docker CLI (docker run および docker-compose コマンド) を使用して手動で展開する場合も、展開するコンテナーごとに Dockerfile が必要です。 アプリケーションにカスタム サービスが 1 つ含まれている場合、Dockerfile が 1 つ必要です。 (マイクロサービス アーキテクチャの場合のように) アプリケーションに複数のサービスが含まれる場合、サービスごとに Dockerfile が 1 つ必要です。

Dockerfile は、アプリケーションまたはサービスのルート フォルダーにあります。 これには、コンテナーでアプリケーションまたはサービスを設定して実行する方法を Docker に指示するコマンドが含まれています。 手動でコードに Dockerfile を作成し、.NET の依存関係と共にプロジェクトに追加できます。

Visual Studio と Docker 用のツールでは、このタスクはマウスを何度かクリックするのみで実行できます。 Visual Studio 2017 で新しいプロジェクトを作成する場合、図 5-3 に示す **[Enable Docker Support]**\(Docker サポートを有効にする\) というオプションがあります。

![](./media/image5.png)

**図 5-3** Visual Studio 2017 で新しいプロジェクトを作成するときの Docker サポートの有効化

Visual Studio でプロジェクト ファイルを右クリックし、図 5-4 のとおり、**[追加]、[Docker プロジェクト サポート]** の順にオプションを選択しても、新規、または既存のプロジェクトで Docker サポートを有効にすることができます。

![](./media/image6.png)

**図 5-4** 既存の Visual Studio 2017 プロジェクトでの Docker サポートの有効化

(ASP.NET Web アプリケーションや Web API サービスなどの) プロジェクトでこの操作を実行すると、必要な構成で、プロジェクトに Dockerfile が追加されます。 また、ソリューション全体に docker-compose.yml ファイルが追加されます。 次のセクションでは、それらの各ファイルに書き込まれる情報について説明します。 この作業は、Visual Studio が実行してくれますが、Dockerfile に何が書き込まれるかを理解しておくと便利です。

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>オプション A: 既存の公式の .NET Docker イメージを使用してプロジェクトを作成する

通常、公式のリポジトリである [Docker Hub](https://hub.docker.com/) レジストリから取得できる基本イメージ上にコンテナーのカスタム イメージをビルドします。 Visual Studio で Docker のサポートを有効にした場合、背後ではこれがまさに発生します。 Dockerfile では、既存の aspnetcore イメージを使用します。

選択した OS とフレームワークによって、使用できる Docker イメージとリポジトリについては、既に説明しています。 たとえば、ASP.NET Core (Linux または Windows) を使用したい場合は、microsoft/aspnetcore:2.0 のイメージを使用します。 この場合は、コンテナーに使用する基本の Docker イメージのみを指定する必要があります。 これは、Dockerfile に FROM microsoft/aspnetcore:2.0 を追加することによって行います。 これは、Visual Studio が自動的に実行しますが、バージョンを更新する場合は、この値を更新する必要があります。

バージョン番号を使用して Docker Hub の公式の .NET イメージ リポジトリを使うと、同じ言語機能が (開発、テスト、および実稼働環境などの) すべてのコンピューターで使用できるようになります。

次の例では、ASP.NET Core コンテナー用のサンプルの Dockerfile を示しています。

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

この場合、コンテナーは、公式の ASP.NET Core Docker イメージ (Linux および Windows 用マルチアーチ) のバージョン 2.0 に基づいています。 この設定は、`FROM microsoft/aspnetcore:2.0` です。 (この基本イメージの詳細については、「[ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/)」 (ASP.NET Core Docker イメージ) ページと「[.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/)」 (.NET Core Docker イメージ) ページを参照してください)。Dockerfile では、実行時に使用する、リッスンする TCP ポートを、Docker に指示する必要があります (ここでは、EXPOSE 設定で構成したポート 80)。

使用している言語とフレームワークによっては、Dockerfile に別の構成設定を指定できます。 たとえば、\["dotnet", "MySingleContainerWebApp.dll"\] の ENTRYPOINT 行では、.NET Core アプリケーションを実行するよう Docker に指示しています。 SDK と .NET Core CLI (dotnet CLI) を使用して、.NET アプリケーションをビルドおよび実行している場合、設定はこれとは別になります。 つまり、アプリケーションに選択した言語とプラットフォームにより、ENTRYPOINT 行とその他の設定は別になります。

### <a name="additional-resources"></a>その他の技術情報

-   **Building Docker Images for .NET Core Applications (.NET Core アプリケーション用の Docker イメージのビルド)**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **Build your own image (独自のイメージのビルド)**。 Docker の公式なドキュメント内にあります。
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>マルチアーキテクチャ イメージ リポジトリの使用

単一のリポジトリには、Linux イメージや Windows イメージなどのプラットフォーム バリアントを含めることができます。 この機能では、Microsoft (基本イメージの作成者) などのベンダーが、複数のプラットフォーム (つまり、Linux および Windows) に対応できるリポジトリを 1 つ作成できます。 たとえば、Docker Hub レジストリにある [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) リポジトリでは、同じリポジトリ名を使用して Linux および Windows Nano Server をサポートしています。

タグを指定する場合、次の場合のように、明示的にプラットフォームを指定できます。

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

しかし、これは 2017 年の中ごろからのものであり、同じイメージ名を指定した場合、同じタグを使用した場合でも、次の例で示すように、(マルチアーキテクチャをサポートする aspnetcore イメージなどの) 新しいマルチアーキテクチャ イメージは、展開する Docker ホストの OS に応じて Linux または Windows バージョンが使用されます。

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

この場合、Windows ホストからイメージをプルした場合、Windows バリアントがプルされ、同じイメージ名が Linux ホストからプルされた場合、Linux バリアントがプルされます。

### <a name="option-b-creating-your-base-image-from-scratch"></a>オプション B: 一から基本イメージを作成する

独自の Docker 基本イメージを一から作成することができます。 このシナリオは、Docker を初めて使用するユーザーには推奨されませんが、独自の基本イメージの特定のビットを設定したい場合にそれを行うことができます。

### <a name="additional-resources"></a>その他の技術情報

-   **Multi-arch .NET Core images** (マルチアーキテクチャの .NET Core のイメージ)
https://github.com/dotnet/announcements/issues/14 
-   **Create a base image** (基本イメージを作成する) Docker の公式なドキュメントです。
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>手順 3. カスタマイズした Docker イメージを作成し、それにアプリケーションまたはサービスを埋め込みます。

アプリケーションの各サービスには、関連イメージを作成する必要があります。 アプリケーションが 1 つのサービスまたは Web アプリケーションで構成されている場合、イメージは 1 つのみ必要です。

Docker イメージは、Visual Studio が自動的に構築することに注意してください。 次の手順は、エディター/CLI ワークフローにのみ必要であり、背後で何が起こっているのか説明するために示しています。

開発者は、完全な機能をプッシュできるか、(GitHub などの) ソース管理システムに変更するまで、ローカルで開発およびテストする必要があります。 つまり、Docker イメージを作成してローカルの Docker ホスト (Windows または Linux VM) にコンテナーを展開し、それらのローカルのコンテナーに対して実行、テスト、およびデバッグをする必要があることを意味します。

Docker CLI と Dockerfile を使用して、ローカルの環境にカスタム イメージを作成するには、図 5-5 のとおり、docker build コマンドを使用します。

![](./media/image8.png)

**図 5-5** カスタム Docker イメージの作成

必要に応じて、プロジェクト フォルダーから docker build を直接実行する代わりに、dotnet publish を実行して必要な .NET ライブラリとバイナリを使用して、展開可能なフォルダーをまず生成し、次いで docker build コマンドを使用します。

これにより、cesardl/netcore-webapi-microservice-docker:first という名前の Docker イメージが作成されます。 このとき、:first は特定のバージョンを表すタグです。 この手順は、構成した Docker アプリケーション用に作成する必要のある各カスタム イメージで繰り返します。

アプリケーションが複数のコンテナーで作成されている場合 (つまり、マルチコンテナー アプリケーションの場合)、docker-compose up ビルド コマンドでは、関連する docker-compose.yml ファイルで公開されているメタデータを使用して、1 つのコマンドですべての関連イメージを作成できます。

図 5-6 の docker images コマンドを使用すると、ローカル リポジトリの既存のイメージを検索できます。

![](./media/image9.png)

**図 5-6** docker images コマンドを使用した既存のイメージの表示

### <a name="creating-docker-images-with-visual-studio"></a>Visual Studio での Docker イメージの作成

Visual Studio を使用して、Docker のサポートでプロジェクトを作成する場合、イメージは明示的には作成されません。 代わりに、F5 キーを押し、Docker 化されたアプリケーションまたはサービスを実行することによって、イメージは作成されます。 この手順は Visual Studio では自動的に行われ、それが実行されるのを見ることはできませんが、背後で何が行われているか知ることは重要です。

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>手順 4. マルチ コンテナー Docker アプリケーションを構築するときの docker-compose.yml へのサービスの定義

[docker-compose.yml](https://docs.docker.com/compose/compose-file/) ファイルでは、展開用のコマンドを使用して構成済みのアプリケーションとして関連サービスのセットを定義できます。

docker-compose.yml ファイルを使用する場合、メインまたはルート ソリューション フォルダーに、次の例と類似した内容でファイルを作成する必要があります。

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

なお、この docker-compose.yml ファイルは、簡略化され、結合されたバージョンです。 これには、必ずある (カスタム イメージ名などの) 各コンテナー用の静的な構成データと、展開環境によっては異なる場合のある、接続文字列などの構成情報が含まれています。 後半のセクションでは、複数の docker-compose ファイルに docker-compose.yml 構成を分割し、環境と実行の種類 (デバッグまたはリリース) に応じて、値をオーバーライドする方法について学習します。

docker-compose.yml ファイルの例では、webmvc サービス (Web アプリケーション)、2 つのマイクロサービス (catalog.api および ordering.api)、1 つのデータ ソース コンテナー、コンテナーとして実行される Linux 用 SQL Server の sql.data の 5 つのサービスが定義されています。 各サービスはコンテナーとして展開されるので、それぞれに Docker イメージが必要です。

docker-compose.yml ファイルでは、どのコンテナーが使用されているかのみでなく、それらがどのように個々に構成されるかが指定されています。 たとえば、.yml ファイルの webmvc コンテナーの定義は次のとおりです。

-   事前にビルドされている eshop/web:latest イメージが使用されています。 ただし、docker-compose の実行の一部として、docker-compose ファイルの build: セクションの追加構成を加え、イメージがビルドされるように構成することもできます。

-   2 つの環境変数 (CatalogUrl および OrderingUrl) を初期化します。

-   コンテナー上の公開されているポート 80 を、ホスト コンピューター上の外部ポート 80 に転送します。

-   depends\_on 設定を使用して、カタログと順序付けサービスに Web アプリをリンクします。 これにより、サービスは、それらのサービスが開始されるまで待機するようになります。

docker-compose.yml ファイルについては、マイクロサービスとマルチコンテナー アプリを実装する方法について説明する後のセクションで、再確認します。

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Visual Studio 2017 での docker-compose.yml の操作

図 5-7 のように、Visual Studio ソリューションのサービス プロジェクトに Docker ソリューションのサポートを追加する場合、Visual Studio ではプロジェクトに Dockerfile を追加し、docker-compose.yml ファイルでソリューションにサービス セクション (プロジェクト) を追加します。 これでは、マルチコンテナー ソリューションを簡単に作成開始できます。 その後、docker-compose.yml ファイルを開き、追加機能で更新することができます。

![](./media/image6.png)

**図 5-7** Visual Studio 2017 への ASP.NET Core プロジェクトの右クリックでの Docker サポートの追加

Visual Studio に Docker のサポートを追加すると、プロジェクトに Dockerfile が追加されるだけでなく、ソリューション レベルで設定されているいくつかのグローバル docker-compose.yml ファイルに構成情報が追加されます。

Visual Studio でソリューションに Docker のサポートを追加すると、図 5-8 のとおり、追加された docker compose.yml ファイルが含まれた新しいノード (docker-compose.dcproj プロジェクト ファイル) がソリューション エクスプローラーに表示されます。

![](./media/image11.PNG)

**図 5-8**. Visual Studio 2017 のソリューション エクスプローラーに追加された **docker-compose** ツリー ノード

docker-compose up コマンドを使用すると、1 つの docker-compose.yml ファイルで、マルチコンテナー アプリケーションを展開することができます。 ただし、Visual Studio がそれらのグループを追加するので、環境 (開発対本番) と実行の種類 (リリース対デバッグ) に応じて値を上書きする必要があります。 この機能は、後のセクションで説明します。

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>手順 5. Docker アプリケーションのビルドと実行

アプリケーションにコンテナーが 1 つしかない場合、Docker ホスト (仮想マシンまたは物理サーバー) に展開して実行することができます。 ただし、アプリケーションに複数のサービスが含まれている場合、単一の CLI コマンド (docker-compose up) を使用するか、背後でそのコマンドを使用する Visual Studio を使用して、構成されたアプリケーションとして展開することができます。 別のオプションを見てみましょう。

### <a name="option-a-running-a-single-container-with-docker-cli"></a>オプション A: Docker CLI で単一のコンテナーを実行する

図 5-9 のとおり、docker run コマンドを使用して Docker コンテナーを実行できます。

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**図 5-9** docker run コマンドを使用した Docker コンテナーの実行

この場合、このコマンドによって、コンテナーの内部ポート 5000 がホスト コンピューターのポート 80 にバインドされます。 つまり、ホストはポート 80 をリッスンし、コンテナーのポート 5000 に転送することを意味します。

### <a name="option-b-running-a-multi-container-application"></a>オプション B: マルチコンテナー アプリケーションを実行する

多くのエンタープライズ シナリオでは、Docker アプリケーションは複数のサービスで構成されています。つまり、図 5-10 のようにマルチコンテナーのアプリケーションを実行する必要があります。

![](./media/image14.png)

**図 5-10** Docker コンテナーが展開された VM

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Docker CLI を使用したマルチコンテナー アプリケーションの実行

Docker CLI を使用してマルチコンテナー アプリケーションを実行するには、docker-compose up コマンドを実行します。 このコマンドでは、ソリューション レベルにある、マルチコンテナー アプリケーションを展開する docker compose.yml ファイルを使用します。 図 5-11 は、docker-compose.yml ファイルを含む、メインのプロジェクト ディレクトリからコマンドを実行した結果を示しています。

![](./media/image15.png)

**図 5-11** docker-compose up コマンドの実行結果の例

docker-compose up コマンドを実行すると、アプリケーションとその関連コンテナーが、図 5-10 の VM の図のとおり、Docker ホストに展開されます。

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Visual Studio を使用したマルチコンテナー アプリケーションの実行とデバッグ 

Visual Studio 2017 を使用したマルチコンテナー アプリケーションの実行は非常に簡単です。 Visual Studio で標準のブレークポイントを設定すると、マルチコンテナー アプリケーションを実行するのみでなく、そのコンテナーをすべて直接デバッグすることができるようになります。

既に説明したとおり、ソリューション内のプロジェクトに Docker ソリューションのサポートを追加するたびに、そのプロジェクトは、グローバル (ソリューション レベル) docker-compose.yml ファイルに構成され、一度にソリューション全体を実行またはデバッグできるようになります。 Visual Studio では、Docker ソリューションのサポートが有効になっているプロジェクトごとに 1 つのコンテナーが起動され、内部のすべての手順をユーザーのために実行してくれます (dotnet publish、docker build など)。

ここで重要なのは、図 5-12 のとおり、Visual Studio 2017 には、F5 のアクション用に追加の **Docker** コマンドがあることです。 このオプションでは、ソリューション レベルで docker-compose.yml ファイルに定義されているすべてのコンテナーを実行して、マルチコンテナー アプリケーションを実行またはデバッグできます。 マルチコンテナー ソリューションをデバッグできるということは、異なるプロジェクト (コンテナー) にそれぞれブレークポイントを設定でき (いくつかブレークポイントを設定でき)、Visual Studio でデバッグする際、別のプロジェクトに定義され、別のコンテナーで実行されているブレークポイントで停止されることを意味します。

![](./media/image16.png)

**図 5-12** Visual Studio 2017 でのマルチコンテナー アプリの実行

### <a name="additional-resources"></a>その他の技術情報

-   **Deploy an ASP.NET container to a remote Docker host (ASP.NET コンテナーをリモートの Docker ホストに展開する)**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>オーケストレーターを使用したテストと展開に関する注意事項

docker-compose up および docker run コマンド (または Visual Studio でのコンテナーの実行およびデバッグ) を使用して、開発環境でコンテナーを十分にテストできます。 ただし、Docker クラスター、Docker Swarm、Mesosphere DC/OS、Kubernetes などのオーケストレーターをターゲットとしている場合は、このアプローチは使用しないようにする必要があります。 [Docker Swarm モード](https://docs.docker.com/engine/swarm/) (Docker CE for Windows および Mac のバージョン 1.12 以降で利用可能) などのクラスターを使用している場合、1 つのサービスに [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) などのその他のコマンドを使用して展開およびテストをする必要があります。 いくつかのコンテナーで構成されるアプリケーションを展開する場合、[docker compose bundle](https://docs.docker.com/compose/reference/bundle/) および [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) を使用して、構成されたアプリケーションを*スタック*として展開できます。 詳細については、Docker サイト上の Docker ドキュメント「[Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/)」(実験的な分散アプリケーション バンドルの概要) のブログ投稿を参照してください 。

[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) と [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) については、同様に別の展開用のコマンドとスクリプトを使用する必要があります。

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>手順 6. ローカル Docker ホストを使用した Docker アプリケーションのテスト

この手順は、アプリケーションで何が実行されているかによって異なります。 単一のコンテナーやサービスとして展開された単純な .NET Core Web アプリケーションでは、図 5-13 のように、Docker ホストでブラウザーを開き、サイトに移動して、サービスにアクセスできます。 (Dockerfile の構成で、コンテナーがホストの 80 以外のポートにマップされる場合、この URL にホスト ポストを含めます。)

![](./media/image18.png)

**図 5-13** localhost を使用したローカルでの Docker アプリケーションのテスト例

localhost が Docker ホスト IP をポイントしていない場合 (Docker CE を使用している場合、既定ではしている必要があります)、サービスに移動するには、コンピューターのネットワーク カードの IP アドレスを使用します。

なお、ブラウザーのこの URL では、説明している特定のコンテナーの例に、ポート 80 を使用しています。 ただし、前の手順で説明したとおり、docker run コマンドで展開されたとおり、要求は内部でポート 5000 にリダイレクトされています。

図 5-14 のとおり、ターミナルからカールを使用して、アプリケーションをテストすることも可能です。 Windows の Docker インストールでは、既定の Docker ホスト IP は、常にマシンの実際の IP アドレスに 10.0.75.1 を加えたものです。

![](./media/image19.png)

**図 5-14** カールを使用したローカルでの Docker アプリケーションのテスト例

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Visual Studio 2017 を使用したコンテナーのテストおよびデバッグ

Visual Studio 2017 でコンテナーを実行またはデバッグする場合、.NET アプリケーションのデバッグは、コンテナーを使用しないでデバッグするのとほぼ同じ方法で実行できます。

### <a name="testing-and-debugging-without-visual-studio"></a>Visual Studio を使用しないデバッグおよびテスト

エディター/CLI アプローチを使用して開発をする場合、コンテナーのデバッグはより難しいので、トレースを生成してデバッグした方がよいでしょう。

### <a name="additional-resources"></a>その他の技術情報

-   **ローカルの Docker コンテナーでアプリをデバッグする**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **作成者: Steve Lasker。Docker を使用した ASP.NET Core アプリのビルド、デバッグおよび展開。** ビデオ。
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Visual Studio でのコンテナー開発の簡略ワークフロー

Visual Studio を使用するワークフローは、エディター/CLI アプローチを使用するワークフローよりも、実際はるかに簡単になります。 Dockerfile と docker-compose.yml ファイルに関係する Docker で必要な多くの手順は、図 5-15 のとおり、Visual Studio では背後で実行されるか、簡略化されます。

![](./media/image20.png)

**図 5-15**。 Visual Studio での開発の簡略ワークフロー

これに加え、(プロジェクトに Docker のサポートを追加する) 手順 2 を、一度のみ実行する必要があります。 つまり、ワークフローは、他の任意の開発に .NET を使用する場合の通常の開発タスクと似たものになります。 背後で何が起こっているのか (イメージのビルド手順、使用している基本イメージ、コンテナーの展開など) を理解しておく必要があり、動作をカスタマイズするのに Dockerfile または docker-compose.yml ファイルを編集する必要がある場合もあります。 しかし、多くの作業は Visual Studio を使用することで大幅に簡略化され、ユーザーの生産性を向上させます。

### <a name="additional-resources"></a>その他の技術情報

-   **作成者: Steve Lasker。 .NET Docker Development with Visual Studio 2017 (Visual Studio 2017 を使用した .NET Docker の開発)**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **作成者: Jeffrey T. Fritz。Put a .NET Core App in a Container with the new Docker Tools for Visual Studio (Visual Studio 用の新しい Docker ツールを使用してコンテナーに .NET Core アプリを入れる)**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Windows コンテナーを設定するための PowerShell コマンドの使用 

[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)は、既存の Windows アプリケーションを Docker イメージに変換して、Docker エコシステムの残りと同じツールで展開できます。 Windows コンテナーを使用するには、次の例のように、Dockerfile で PowerShell コマンドを実行します。

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

この場合は、Windows Server Core 基本イメージ (FROM 設定) を使用して、PowerShell コマンド (RUN 設定) で IIS をインストールしています。 同様に、PowerShell コマンドを使用して、ASP.NET 4.x、.NET 4.6、またはその他の任意の Windows ソフトウェアなどの追加コンポーネントを設定することもできます。 たとえば、Dockerfile の次のコマンドでは、ASP.NET 4.5 が設定されます。

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>その他の技術情報

-   **aspnet-docker/Dockerfile.** Windows の機能を含めるために dockerfile から実行する Powershell コマンドの例です。
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[前へ] (index.md) [次へ] (../net-core-single-containers-linux-windows-server-hosts/index.md)
