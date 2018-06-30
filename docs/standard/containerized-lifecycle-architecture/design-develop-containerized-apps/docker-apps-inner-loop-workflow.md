---
title: Docker アプリ用の内部ループ開発ワークフロー
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 9e578599c61053704202946772c43bdb5ef895c2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105590"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Docker アプリ用の内部ループ開発ワークフロー

サイクル全体の DevOps のまたがりメモリ割り当て、外側のループ ワークフローをトリガーする前に、各開発者のコンピューターで、アプリ自体をコーディング、言語またはプラットフォームを使用して、およびそれをローカルでのテスト (図 4-14) はすべて開始します。 すべてのケースでする必要が非常に重要なポイント共通に、選択した言語、フレームワーク、またはプラットフォームに関係なく。 この特定のワークフローで常に開発およびテストして、Docker コンテナーなくローカルです。

![](./media/image18.png)

図 4-14: 内部ループ開発コンテキスト

これらのコンポーネントは、コンテナーまたは Docker イメージのインスタンスが含まれます。

-   たとえば、Linux ディストリビューション (Windows) オペレーティング システムの選択

-   Developer (アプリのバイナリなど) によって追加されたファイル

-   (たとえば、環境の設定と依存関係) の構成

-   Docker によって実行するどのようなプロセスの手順

(次のセクションで説明) のプロセスとして Docker を使用する内部ループ開発ワークフローを設定することができます。 考慮する、環境をセットアップする最初の手順は含まれず、1 回だけを行う必要があるため。

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Visual Studio Code と Docker CLI を使用して、Docker コンテナー内の 1 つのアプリの構築

アプリは、独自のサービスと追加のライブラリ (依存関係) から構成されています。

図 4-15 では、通常、各ステップの詳細な説明を続けて、Docker アプリを構築するときに実行するために必要な基本手順を示します。

![](./media/image19.png)

Docker CLI を使用する Docker コンテナー詰めアプリケーション ライフ サイクルの図 4-15: 高度なワークフロー

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>手順 1: Visual Studio のコードでコーディングを開始し、初期アプリケーション/サービスの基準を作成します。

アプリケーションを開発する方法は、Docker なく行う方法に非常に似ています。 違いは、開発中に展開しているアプリケーションまたは (Linux VM または Windows) など、ローカル環境に配置している Docker コンテナー内で実行されているサービスをテストします。

**ローカル環境の設定**

Mac および Windows 向けの Docker の最新のバージョンがこれまでに、Docker のアプリケーションの開発よりも簡単と、セットアップは簡単です。

**詳細については** Docker for Windows の設定手順についてを参照してください[ https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)です。

Mac の Docker を設定する方法についてを参照してください<https://docs.docker.com/docker-for-mac/>です。

さらに、実際に Docker CLI を使用しているときにアプリケーションを開発することができるように、コード エディターが必要があります。

Microsoft は、軽量なコード エディターで IntelliSense を示し、Mac、Windows、および Linux ではサポートされているは、Visual Studio のコードを提供[の多数の言語サポート](https://code.visualstudio.com/docs/languages/overview)(JavaScript、.NET、移動、Java、Ruby、Python、およびほとんど最新の言語)、[デバッグ](https://code.visualstudio.com/Docs/editor/debugging)、 [Git と統合](https://code.visualstudio.com/Docs/editor/versioncontrol)と[拡張機能のサポート](https://code.visualstudio.com/docs/extensions/overview)です。 このエディターは、Mac および Linux の開発者にとって最適です。 Windows もに、完全な Visual Studio アプリケーションを使用できます。

**詳細については** か、Visual Studio for Windows、Mac、Linux をインストールする方法の詳細についてを参照してください[ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/)です。

Docker CLI を使用して、コード エディターを使用して、コードの記述が Visual Studio のコードを使用する場合、作成者 Dockerfile を容易に行えます、docker compose.yml ファイル ワークスペースにします。 さらに、下に Docker CLI を使用して詳細な操作を実行できるスクリプトを要求する IDE から Visual Studio のコードのタスクを実行できます。

Visual Studio のコードは、インストールする必要があります拡張機能によって提供されます。 そのためには、キーを押して Ctrl + Shift + P、次のように入力します。 **ext インストール**、拡張機能を実行し: Marketplace 拡張機能の一覧を表示する拡張機能のインストール コマンド。 次に、入力**docker**結果をフィルター処理し、図 4-16 の図のように、Dockerfile と Docker 構成ファイル (yml) サポートの拡張機能を選択します。

![](./media/image20.png)

図 4-16: Visual Studio のコードに Docker 拡張機能をインストールします。

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>手順 2: 既存のイメージ (plain OS または開発環境を .NET Core、Node.js、および Ruby など) に関連する DockerFile を作成します。

カスタム イメージを構築および配置するコンテナーごとに、DockerFile は必要があります、したがって、1 つのカスタム サービスのアプリが構成されている場合する必要があります単一 DockerFile です。 しかし、アプリが複数のサービス (microservices アーキテクチャ) のように構成されている場合は、サービスごとの 1 つの Dockerfile を必要があります。

DockerFile は通常、アプリやサービスのルート フォルダー内に配置しているし、その Docker を設定し、そのアプリやサービスを実行する方法を認識するために必要なコマンドが含まれています。 DockerFile を作成し、コードと共にプロジェクトに追加することができます (node.js、.NET Core など)、または、環境に新しい場合は、次のヒントを確認します。

> [!TIP]
> というコマンド ライン ツールを使用する[yo docker](https://github.com/Microsoft/generator-docker)を選択して、必要な Docker 構成ファイルに追加の言語のプロジェクトからファイルをスキャフォールディングします。 基本的には、開発者が作業の開始を支援するために作成、適切な DockerFile で docker compose.yml、およびその他の関連付けられているスクリプトをビルドして、Docker コンテナーを実行します。 この yeoman ジェネレーターに、選択した開発言語と移行先コンテナーのホストを確認するいくつかの質問を求められます。

![yo docker](./media/image21.png)

たとえば、図 4-17 を示しています、端末から 2 つのスクリーン ショット windows と Mac では、どちらの場合も、実行されている yo、docker で動作するよう既に構成サンプルのコード プロジェクト (.NET Core では現在、Golang、および Node.js としてサポートされている言語) を生成します。Docker の上部に表示。

![](./media/image22.PNG)  ![](./media/image23.png)

図 4-17: yo docker コマンド ツール ウィンドウ (左) と、Mac 上

図 4-18 では、docker を使用した yo を作成したら、既存の .NET Core プロジェクトをスキャフォールディングする例を示します。

![](./media/image24.PNG)

図 4 ~ 18: yo 既存の .NET Core の docker でプロジェクトを配置

DockerFile からは、(microsoft/dotnet:1.0.0-core"から"を使用して) などが使用されるどのような基本の Docker イメージを指定します。 任意の正式なリポジトリから取得できる基本イメージの上にカスタム イメージ ビルドは通常、 [Docker Hub レジストリ](https://hub.docker.com/)(と同様に、 [.NET Core のイメージ](https://hub.docker.com/r/microsoft/dotnet/)または 1 個[for Node.js](https://hub.docker.com/_/node/)).

***オプション a: を使用する既存の正式な Docker イメージ***

バージョン番号を持つ言語スタックの公式のリポジトリを使うと、同じ言語の機能が (開発、テスト、および実稼働環境を含む) すべてのマシンで使用できることができます。

.NET Core コンテナー用 DockerFile のサンプルを次に示します。

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

この場合、使用されている公式の ASP.NET Core Docker イメージのバージョン 1.0.1 for Linux microsoft/aspnetcore:1.0.1 をという名前です。 詳細についてを参照してください、 [ASP.NET Core Docker イメージ ページ](https://hub.docker.com/r/microsoft/aspnetcore/)と[.NET Core Docker イメージ ページ](https://hub.docker.com/r/microsoft/dotnet/)です。 でした使用するノード: 4 などの別の比較可能なイメージ-Node.js、または開発言語で提供されているその他の多くの事前構成済みイメージの onbuild [Docker Hub](https://hub.docker.com/explore/)です。

DockerFile で (ポート 80) などの実行時に使用する TCP ポートをリッスンするように Docker に指示する必要があります。

Docker は、アプリを実行する方法を認識しているように、dockerfile を使用している言語/フレームワークによって追加できる構成の他の行があります。 インスタンスでは、ENTRYPOINT 行が必要な\["dotnet"、"MyCustomMicroservice.dll"\]をビルドして、サービスを実行する方法に応じて複数のバリアントを持つことができますが、.NET Core のアプリを実行します。 .NET アプリをビルドして、実行、SDK と dotnet CLI を使用している場合は、若干異なるがなります。 一番下の行が、ENTRYPOINT 行と追加の行になりますアプリケーション用に選択した言語またはプラットフォームによって異なります。

**詳細については** .NET Core アプリケーションの Docker イメージを構築する方法についてを参照してください<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>です。

独自のイメージの構築に関する詳細については、するには[ https://docs.docker.com/engine/\ チュートリアル/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)です。

**マルチプラット フォームのイメージ リポジトリ**

Windows コンテナーより多く使用されているになると、1 つのリポジトリは Linux と Windows イメージなどのプラットフォームのバリエーションを含めることができます。 これは、新しい機能により、複数のプラットフォームを対象に 1 つのリポジトリを使用する仕入先の Docker が受け取った[microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) dockerhub を使用してレジストリで利用可能なリポジトリ。 機能が有効になると、このイメージを Windows ホストからプルすると、Linux バリアントがプルする Linux ホストから同じイメージの名前をプルする一方には Windows バリアントが除去されます。

***基本イメージを最初からオプション b: を作成***

これで説明したよう、最初から独自 Docker の基本イメージを作成することができます[記事](https://docs.docker.com/engine/userguide/eng-image/baseimages/)Docker からです。 これは、シナリオ Docker、によって起動した場合に、最適な可能性がありますが、独自の基本イメージの特定のビットを設定する場合は、行うことができます。

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>手順 3: 埋め込みことで、サービス、カスタム Docker イメージを作成します。

サービスごとにカスタム アプリを構成するには、関連するイメージを作成する必要があります。 1 つのサービスまたは web アプリのアプリが構成されている場合は、1 つのイメージを必要があります。

> [!NOTE]
> "外側のループ DevOps workflow"を考慮に入れて、イメージから作成されます自動ビルド プロセスによって、ソース コードをリポジトリにプッシュ Git (継続的インテグレーション) ため、イメージはグローバル環境で作成されるたびに、ソース コードです。

しかし、その外側のループのルートに、考慮する前に、Docker アプリケーションが実際には正しく動作するソース管理システム (Git など) が正しく動作しないコードをプッシュしないようにすることを確認する必要があります。

そのため、各開発者が最初にために必要な内部ループ プロセス全体をローカルでテストし、完全な機能をプッシュまたはソース管理システムを変更するまでの開発を続行します。

図 4-19 に示すように、ローカル環境と、DockerFile を使用してイメージを作成するに docker ビルド コマンドを使用することができます (実行することもできます docker 構成設定によっていくつかのコンテナー/サービスで構成されたアプリケーションの構築) します。

![](./media/image25.png)

図 4-19: docker のビルドの実行

必要に応じて、docker を直接実行する代わりに、プロジェクトのフォルダーからビルド最初できますを生成して、配置可能なフォルダー実行 dotnet を使用してコマンドを発行し、docker ビルドを実行に必要な .NET ライブラリとします。

この例では、名前 cesardl/netcore-webapi-マイクロ サービスを Docker イメージを作成これ-docker: 最初 (: 1 つ目は、特定のバージョンと同様に、タグ)。 複数のコンテナーを使用して構成済みの Docker アプリケーションを作成する必要がカスタム イメージごとにこの手順を実行できます。

既存のイメージ、ローカル リポジトリ (開発用コンピューター) に、docker を使用してイメージ コマンドは検索できます、図 4-20 を示すようにします。

![](./media/image26.png)

図 4-20: docker のイメージを使用して既存のイメージを表示します。

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>手順 4: (省略可能) を定義する docker compose.yml の複数のサービスで構成される Docker アプリを構築するときに、サービス

Docker compose.yml ファイルでは、次の手順」セクションで説明する展開コマンドを使用して構築されたアプリケーションとして展開に関連するサービスのセットを定義できます。

その、main でファイルまたはソリューションのルート フォルダー; を作成する必要があります。類似のコンテンツは、次の docker compose.yml ファイルにこれが必要です。

```yml
version: '2'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

この特定のケースでは、このファイルは 2 つのサービスを定義します。 web サービス (カスタム サービス) と redis サービス (一般的なキャッシュ サービス)。 各サービスには、コンテナーとしてデプロイため、各具象 Docker イメージを使用する必要があります。 この特定の web サービスのイメージは、以下を行う必要があります。

-   現在のディレクトリに、DockerFile をビルドします。

-   公開されているポート 80 をコンテナー ホスト マシン上のポート 81 上を転送します。

-   /Code、コンテナー内にイメージを再作成しなくても、コードを変更できるようにするホスト上のプロジェクト ディレクトリをマウントします。

-   Redis サービスへの web サービスをリンクします。

Redis サービスが使用、[最新公開 redis イメージ](https://hub.docker.com/_/redis/)Docker Hub レジストリから取得します。 [redis](https://redis.io/)はサーバー側アプリケーション用のキャッシュが非常に一般的なシステムです。

### <a name="step-5-build-and-run-your-docker-app"></a>手順 5: ビルドし、Docker のアプリの実行

アプリに 1 つのコンテナーのみがある場合だけ、(VM または物理サーバー) は Docker ホストに展開することで実行する必要があります。 ただし、複数のサービス、アプリが構成されている場合必要*組み立てる*、すぎます。 さまざまなオプションを確認してみましょう。

***A: 実行の 1 つのコンテナーまたはサービスをオプションします。***

次に示すように docker run コマンドを使用して、Docker イメージを実行できます。

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

この特定の展開のおありますリダイレクト 5000 内部ポートにポート 80 に送信された要求に注意してください。 ここで、外部ポート 80、ホスト レベルで、アプリケーションがリッスンしています。

***オプション b: 作成と実行、複数のコンテナー アプリケーション***

ほとんどのエンタープライズ シナリオでは、Docker アプリケーションを複数のサービスはから構成されます。 このような場合は、コマンドを実行して docker 構成を (図 4-21)、以前作成した可能性があります、docker compose.yml ファイルを使用します。 このコマンドを実行するいると、そのすべての関連するコンテナーで構成されるアプリケーションが展開します。

![](./media/image27.png)

図 4-21:「docker の構成を」コマンドの実行結果

Docker を実行した後に作成、展開するアプリケーションとその関連するコンテナー、Docker ホストに VM 形式を図 4-22 を示すようにします。

![](./media/image28.png)

図 4-22: VM 展開されている Docker コンテナーを

注 docker の構成と docker の実行は、開発環境で、コンテナーのテストに対して十分である可能性がありますがいないそれらを使用するすべての場合は Docker クラスターの操作を必要として、orchestrators などの Docker Swarm 続き DC/OS、Kubernetesためにスケール アップします。 ようにクラスターを使用している場合[Docker Swarm モード](https://docs.docker.com/engine/swarm/)(以降で使用可能では、Docker for Windows と Mac バージョン 1.12)、する必要がある配置した場合など、docker サービスを 1 つのサービスの作成やその他のコマンドをテストするにはバンドルを作成 docker を使用して複数のコンテナーで構成したアプリの配置、および docker が記事で説明したように、スタックとして構成済みのアプリを展開することで myBundleFile を展開[アプリケーション バンドルの分散](https://blog.docker.com/2016/06/docker-app-bundle/)Docker からです。

[DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/)と[Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment)は、さまざまな展開コマンドと、スクリプトを使用します。

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>手順 6: (ローカル CD VM) では、ローカルで Docker アプリケーションをテストします。

この手順は、アプリが何によって異なります。

非常に単純な .NET Core Web API"Hello World"が 1 つのコンテナーまたはサービスとしてデプロイされている、DockerFile で指定された TCP ポートを提供することにより、サービスにアクセスするはだけです。

サービスに移動する localhost が有効でない場合は、このコマンドを使用して、マシンの IP アドレスを検出します。

docker-machine ip *your-container-name*

Docker ホストのブラウザーを開き、およびそのサイトに移動図 4-23 に示すようにを実行しているアプリ/サービスが表示されます。

![](./media/image29.png)

図 4-23: localhost を使用してローカルで Docker アプリケーションのテスト

上の説明に従って、実行、docker を使用した展開された方法であるためにはポート 80 が使用が内部的に 5000 のポートにリダイレクトされましたされていることに注意してください。

端末から CURL を使用して、これをテストすることができます。 図 4 ~ 24 の図のよう、Windows で Docker のインストールでは、既定の IP、10.0.75.1、です。

![](./media/image30.png)

図 4 ~ 24: CURL を使用してローカルでの Docker アプリケーションのテスト

**Docker で実行されているコンテナーのデバッグ**

Visual Studio のコードは、Node.js と .NET Core コンテナーのようなその他のプラットフォームを使用している場合に、Docker のデバッグをサポートします。

デバッグすることもできます Docker でコンテナーを .NET Core、Visual Studio を使用する場合、次のセクションで説明されているようです。

**詳細情報:** Node.js Docker コンテナーのデバッグに関する詳細については、するには<https://blog.docker.com/2016/07/live-debugging-docker/>と[https://blogs.msdn.microsoft.com/\ユーザー\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/)です。


>[!div class="step-by-step"]
[前へ](docker-apps-development-environment.md)
[次へ](visual-studio-tools-for-docker.md)
