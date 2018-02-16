---
title: "Docker アプリケーションの外側のループ DevOps ワークフローの手順を実行します。"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe51fc4b5026d17f0f9b93e7fd0dedde93ef4a3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker アプリケーションの外側のループ DevOps ワークフローの手順を実行します。

図 5-1 では、DevOps 外側のループのワークフローを構成する手順の説明、エンド ツー エンドの図を表示します。

![](./media/image1.png)

Microsoft ツールと Docker のアプリケーションの図 5-1: DevOps 外側のループのワークフロー

ここで、これらの各手順で詳しく調べてみましょう。

## <a name="step-1-inner-loop-development-workflow"></a>手順 1: 内部ループ開発ワークフロー

この手順の第 4 章で詳しく説明していますに要約すると、ここでは外側のループ開始位置となる、開発者が CI パイプライン アクションの開始 (Git) のようなソース管理の管理システムにコードをプッシュする時点。

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>手順 2: ソース コード管理の統合と Visual Studio Team Services および Git と管理

この手順で、チーム内で複数の開発者からのすべてのコードの統合のバージョンを収集するバージョン コントロール システムに用意する必要があります。

アプリケーションに Docker イメージを送信する必要がありますいないを強調する重要な場合でも、ソース コード管理 (SCC) とソース コード管理には、1 秒性質 DevOps ライフで Docker アプリケーションを作成するときにほとんどの開発者のサイクルがないように見えるあります、直接、グローバル Docker レジストリに (Azure コンテナー レジストリや Docker Hub) など、開発者のマシンからです。 反対に、グローバル ビルドまたは (Git) のようなソース コード リポジトリに基づく CI パイプラインでは統合されているソース コードでのみがリリースされ、運用環境に展開するには、Docker イメージを作成しなければなりません。

独自のマシン内でテストするときに、開発者だけでそれ自体には、開発者によって生成されるローカルのイメージを使用してください。 これは、DevOps パイプライン SCC コードからアクティブ化が必要であるためです。

Visual Studio Team Services と Team Foundation Server は、Git と Team Foundation バージョン管理をサポートします。 それらの間を選択して、エンド ツー エンドの Microsoft のエクスペリエンスを使用します。 ただし、管理することもできます (GitHub、内部設置型の Git リポジトリ、Subversion など) の外部のリポジトリで自分のコードに接続して、DevOps CI パイプラインの開始点として、コードを取得することもできます。

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>手順 3: ビルド、構成項目、統合、および Visual Studio Team Services と Docker を使用してテスト

最新のソフトウェアのテストおよび配信のための標準として CI が生じました。 Docker ソリューションでは、開発と運用チーム間での問題を明確に分離を維持します。 Docker images の不変性により、どのような開発、テスト CI、を通じてし、実稼働環境で実行の間で反復可能な配置。 開発者ラップトップの docker エンジンが展開されているし、テスト インフラストラクチャは、環境間でのコンテナーをポータブルです。

この時点では、送信の正しいコードのバージョン管理システムにある場合は、後にする必要があります、*ビルド サービス*にコードを取得し、グローバルのビルドとテストを実行します。

ここでは (構成項目、ビルド、テスト) の内部ワークフローでは、コード リポジトリ (Git など)、ビルド サーバーに、(Visual Studio Team Services)、Docker エンジンと Docker のレジストリで構成される CI パイプラインの構築に関するです。

行えます Visual Studio Team Services 基盤としてのアプリケーションを構築および、CI パイプラインを設定し、組み込みの「アイテム」を公開するため"アーティファクト リポジトリに、"次の手順で説明されています。

Docker を使用して、展開、「最終的なアイテム」のときに展開するのには、アプリケーションまたはサービスを使用してイメージを Docker 内に埋め込まれます。 それらのイメージのプッシュまたはに発行された、 *Docker レジストリ*(Azure コンテナー レジストリに持つことができますなまたは Docker Hub レジストリには、一般的な公式の基本イメージの使用と同様にパブリックのいずれかのようにプライベート リポジトリ)。

ここでは、基本的な概念: 構成項目のパイプラインは Git などのソース コード管理リポジトリへのコミットによってオフ開始になります。 図 5-2 に示すように、コミットは Docker コンテナー内でビルド ジョブを実行し、そのジョブの正常完了時に、Docker イメージを Docker レジストリにプッシュする Visual Studio Team Services になります。

![](./media/image2.png)

図 5-2: 必要な手順で構成項目

Docker と Visual Studio Team Services でワークフローの構成項目の基本的な手順を次に示します。

1.  開発者は、(Git または Visual Studio Team Services、GitHub など) のソース コード管理リポジトリへのコミットをプッシュします。

2.  Visual Studio Team Services または Git を使用している構成項目は、Visual Studio Team Services で、チェック ボックスを選択するだけであることを意味するには、構築されます。 (GitHub) などの外部の SCC を使用している場合、 *webhook*更新プログラムの Visual Studio Team Services の通知または Git と GitHub にプッシュされます。

3.  Visual Studio Team Services では、イメージだけでなく、アプリケーションおよびテストのコードを記述する、DockerFile を含む、ソース コード管理リポジトリを取得します。

4.  Visual Studio Team Services では、Docker イメージをビルドし、ビルド番号のラベル付けします。

5.  Visual Studio Team Services では、プロビジョニング済みの Docker ホスト内で、Docker コンテナーをインスタンス化し、適切なテストを実行します。

6.  「試みられたビルド」がわかるように、イメージが最初にわかりやすい名前を付け、テストが成功した場合は、(のように"/1.0.0"またはその他の任意のラベル)、Docker レジストリ (Docker Hub、Azure にコンテナー レジストリ、DTR など) プッシュし、

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Visual Studio Team Services 用の Visual Studio Team Services と Docker 拡張機能を使用して、CI パイプラインの実装

[Visual Studio Team Services の Docker 拡張](https://aka.ms/vstsdockerextension)CI パイプラインを Docker イメージを作成、認証済みの Docker レジストリに Docker イメージをプッシュ、または実行する Docker images によって提供されるその他の操作を実行するタスクを追加しますDocker CLI です。 また、ビルド、プッシュ、および multicontainer Docker アプリケーションを実行または Docker 構成 CLI で提供される他の操作を実行して、図 5-3 に示すように使用できる Docker Compose のタスクを追加します。

![](./media/image3.png)

図 5-3: Visual Studio Team Services での Docker CI パイプライン

Docker 拡張機能は、Docker ホストとコンテナーのイメージ レジストリ、サービス エンドポイントを使用できます。 (現在必要カスタム Visual Studio Team Services エージェント) です。 使用可能な場合は、ローカル Docker ホストを使用する既定のタスクそれ以外の場合、Docker ホストの接続を提供することが必要です。 認証されると、イメージのプッシュなどの Docker レジストリに依存する操作は、レジストリの接続、Docker を提供することが必要です。

Visual Studio Team Services Docker 拡張機能では、Visual Studio Team Services アカウントで、次のコンポーネントがインストールされます。

-   Docker レジストリに接続するためのサービス エンドポイント

-   Docker コンテナー ホストに接続するためのサービス エンドポイント

-   Docker タスクを次を行うには:

-   イメージを構築します。

-   レジストリにイメージまたはリポジトリをプッシュします。

-   コンテナーのイメージを実行します。

-   Docker コマンドを実行します。

-   Docker Compose Docker Compose コマンドを実行するタスク

これらの Visual Studio Team Services タスクでビルド Linux Docker ホストと VM のプロビジョニングと優先 Docker レジストリ (Azure コンテナー レジストリ、Docker Hub、プライベートの Docker DTR またはその他の任意の Docker レジストリ) で、Docker CI パイプラインを作成することができます、非常に一貫した方法です。

***要件:***

-   Visual Studio Team Services、または内部設置型インストールの場合、Team Foundation Server 2015 Update 3 以降。

-   Docker バイナリが含まれている Visual Studio Team Services エージェント。

1 つ作成する簡単な方法は、Docker を使用して、Visual Studio Team Services エージェントの Docker イメージに基づいて、コンテナーを実行するにです。

**詳細については** パイプラインおよびチュートリアルを表示する、次のサイトを参照してください。 Visual Studio Team Services Docker CI をまとめることの詳細を読むため。

Docker のコンテナーとして、Visual Studio Team Services エージェントを実行している: [https://hub.docker.com/r/\ microsoft/vsts エージェント/](https://hub.docker.com/r/microsoft/vsts-agent/)

VSTS Docker 拡張機能: <https://aka.ms/vstsdockerextension>

Visual Studio Team Services と .NET Core Linux Docker イメージを構築します<https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/。>

Docker のサポートとマシンを作成する Visual Studio チーム Linux ベース サービスの構築: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>統合、テスト、および multicontainer Docker アプリケーションを検証

通常、ほとんどの Docker アプリケーションは 1 つのコンテナーではなく、複数のコンテナーの構成されます。 良い例は、マイクロ サービスあたり 1 つのコンテナーが microservices 指向アプリケーションです。 しかし、microservices アプローチ パターンに厳密に従うと、しなくてもは Docker アプリケーションは、複数のコンテナーまたはサービスの構成は非常に高い可能性。

したがって、CI パイプライン内のアプリケーションのコンテナーを作成するには後もする必要が展開、統合、および全体をそのすべてのコンテナーまたはさらに、コンテナーが、テスト クラスターにも統合 Docker ホスト内でアプリケーションをテストします。分散されます。

1 つのホストを使用している場合は、docker など Docker コマンドを使用するをビルドしてテストし、検証の 1 つの VM で Docker 環境に関連するコンテナーの展開を作成します。 しかし、DC/OS、Kubernetes、Docker Swarm など、orchestrator のクラスターで作業している場合、別のメカニズムや、選択したクラスター/スケジューラによって、orchestrator を使用してコンテナーを展開する必要があります。

Docker コンテナーに対して実行するテストのいくつかの種類を次に示します。

-   Docker コンテナーの単体テスト

-   相互に関連するアプリケーションまたは microservices のテストのグループ

-   運用環境と「カナリア」のリリースでのテストします。

重要な点は、統合および機能のテストを実行する場合は、コンテナーの外部からそれらのテストを実行する必要があります。 テストを定義できず、コンテナーは、実稼働環境にデプロイするものとまったく同じにする必要のある静的なイメージに基づいているために、展開する場合は、コンテナー内で実行する必要があります。

複数のクラスター (クラスター、ステージング クラスター、および運用クラスターのテスト) のテストより高度なシナリオをテストするときに、非常に可能なオプションは、さまざまなクラスターでテストをレジストリにイメージを発行することです。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>グローバル Docker レジストリをカスタム アプリケーションの Docker イメージをプッシュします。

Docker images をテストして検証した後にタグを付けるし、Docker レジストリに公開します。 Docker レジストリは Docker アプリケーション ライフ サイクルにおける重要な部分は QA および実稼働環境に展開する、カスタムのテスト (別名「試みられたイメージの場合」) を格納する一元的な場所になっているためです。

方法 (Git など)、ソース コード管理リポジトリに格納されているアプリケーション コードは、「ソースの情報源」と同様に、Docker レジストリは、「ソース唯一の情報源」QA または実稼働環境に展開するには、バイナリのアプリケーションまたはビット用です。

通常、する可能性がありますまたは必要なカスタム イメージのプライベート リポジトリ プライベート リポジトリのいずれか Azure コンテナー レジストリにまたは Docker Trusted Registry と同様に、内部設置型のレジストリに (のような制限されたアクセス権を持つパブリック クラウドのレジストリでDocker Hub) が、ここでは最後にコードがオープン ソースではない場合に、仕入先のセキュリティを信頼する必要があります。 どちらにしても、これによってこれを行う方法は非常に類似したと最終的には、docker push コマンドに基づいて、図 5-4 に示されているです。

![](./media/image4.png)

図 5-4: カスタム イメージを Docker レジストリに公開します。

Azure コンテナー レジストリ、Amazon Web Services コンテナー レジストリ、Google にコンテナー レジストリ、Quay レジストリなどのクラウドのベンダーから Docker レジストリの複数のサービス提供しています。

図 5-5 に示すようには、Visual Studio Team Services Docker 拡張機能を使用して、(Azure コンテナー レジストリ) のような認証済みの Docker レジストリへの複数のタグで、docker compose.yml ファイルで定義されているサービスのイメージのセットをプッシュできます。

![](./media/image5.png)

図 5-5: Docker のレジストリへの発行のカスタム イメージを Visual Studio Team Services を使用します。

**詳細については** 詳細を確認する Visual Studio Team Services の Docker 拡張機能についてに移動<https://aka.ms/vstsdockerextension>です。 Azure コンテナー レジストリに関する詳細については、するには<https://aka.ms/azurecontainerregistry>です。

## <a name="step-4-cd-deploy"></a>手順 4: CD、展開

Docker images の不変性により、反復可能な展開、新機能が開発された CI、を通じてテストや実稼働環境で実行されます。 所持している複数の環境に展開したり Docker レジストリ (プライベートまたはパブリック) に発行されたアプリケーションの Docker イメージを作成したら、(、品質保証、運用など、ステージング、) Visual Studio Team Services を使用して、CD パイプラインからパイプラインのタスクまたは Visual Studio Team Services のリリース管理されます。

ただし、この時点によって異なります Docker アプリケーションの種類を展開します。 ような複雑なアプリケーションを展開すると非常に異なるアプリケーションを配置する単純な (構成と展開の観点から)、モノリシックと同様に、いくつかのコンテナーやサービスを構成するアプリケーションで展開されたいくつかのサーバーまたは Vm には、ハイパー機能を備えた microservices 指向アプリケーションです。 これら 2 つのシナリオは、次のセクションで説明します。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Docker の複数の環境に Docker アプリケーションの展開で構成されます。

最初に、複雑なシナリオを確認してみましょう: 単純な Docker ホスト (Vm またはサーバー) が 1 つの環境または複数の環境に展開する (QA、ステージング、および実稼働)。 このシナリオで内部的には、CD パイプラインできますを使用して docker-図 5-6 に示すように、コンテナーまたはサービスの関連するそのセットと Docker アプリケーションを展開する (Visual Studio Team Services の展開タスク) から作成します。

![](./media/image6.png)

図 5-6: 単純な Docker ホスト環境のレジストリへのアプリケーションのコンテナーの展開

図 5-7 は、タスクの追加 ダイアログ ボックスで作成する Docker をクリックして、Visual Studio Team Services を使用して、QA/テスト環境に、ビルドの構成項目を接続する方法を示しています。 ただし、ステージング環境または実稼働環境に展開する、ときに通常機能を使用するリリース管理の複数の環境を処理 (などの QA、ステージング、および実稼働)。 を 1 つの Docker ホストに配置する場合、Visual Studio Team Services を使用して、タスクの"Docker Compose"(docker を呼び出すことです-フードの下部のコマンドを作成) します。 を Azure のコンテナー サービスに配置する場合は、次のセクションで説明するよう、Docker の展開タスクを使用します。

![](./media/image7.png)

図 5-7: Visual Studio Team Services パイプラインで Docker Compose タスクを追加します。

Visual Studio Team Services でリリースを作成するときに、一連の入力の成果物がかかります。 これらが意図されていないリリースの有効期間を通じて変更可能な複数の環境。 コンテナーを導入するときに、入力の成果物を展開するレジストリ内のイメージを識別します。 これら識別方法によっては同じリリースでは、"myimage:latest"docker-compose ファイルから参照するとき最も明白なケースの全期間にわたって、保証はありません。

Visual Studio Team Services の Docker 拡張機能により特定のレジストリのイメージが含まれているビルド成果物を生成する機能のダイジェスト バイナリと同じイメージを一意に識別することが保証されることができます。 これらは、何か、リリースへの入力として使用します。

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>Visual Studio Team Services のリリースの管理を使用して Docker 環境にリリースを管理します。

Visual Studio Team Services 拡張機能を使用することができます新しいイメージを構築する、Docker レジストリに発行して、Linux または Windows のホストで実行および docker などのコマンドを使用して、ビジュアルなどのアプリケーションが全体として複数のコンテナーを展開する構成Studio Team Services のリリース管理の機能は図 5-8 に示すように複数の環境の対象としています。

![](./media/image8.png)

図 5-8: Visual Studio Team Services のリリースの管理から Visual Studio Team Services Docker Compose のタスクを構成します。

ただしに注意してください、図 5-6 に示すように、図 5-8 での実装のシナリオは (単純な Docker ホストおよび Vm への導入とが 1 つのコンテナーやイメージごとのインスタンスは存在) 非常に基本的な可能性があります。、開発またはテスト sc に対してのみ使用する必要があります。enarios です。 ほとんどのエンタープライズ実稼働のシナリオでは、高可用性 (HA) が必要とし、負荷分散の間で複数のノード、サーバーを Vm、および「インテリジェント フェールオーバー」ようにする場合は、サーバーまたはノードの管理が容易なスケーラビリティが失敗した場合は、そのサービスとコンテナーは、別のホスト サーバーまたは VM に移動されます。 その場合は、コンテナーのクラスター、orchestrators、スケジューラなどのより高度なテクノロジする必要があります。 したがって、それらのクラスターを展開する方法は、次のセクションで説明されている高度なシナリオを正確にです。

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>複雑な Docker アプリケーション Docker clusters (DC/OS、Kubernetes と Docker Swarm) を展開します。

分散アプリケーションの性質は、分散もコンピューティング リソースが必要です。 実稼働スケール機能には、クラスタ リング高い拡張性を提供する機能がある必要があり、プールされたリソースに基づいて HA です。

コンテナーを Docker Swarm などの CLI ツールからそれらのクラスターを手動で展開でした (を使用するように[docker サービスを作成](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) または web UI など[続きマラソン](https://mesosphere.github.io/marathon/docs/marathon-ui.html)DC OS/クラスター、ですが、行う必要がありますまたは管理などの目的でスケール アウトまたは監視目的でのみ punctual 展開のテストを予約されています。

CD の観点から Visual Studio Team Services 具体的には、タスクを実行できます特別に作成された展開から、Visual Studio Team Services のリリース管理環境でクラスターの分散をコンテナー化アプリケーションを展開します。コンテナー サービス、図 5-9 に示すようにします。

![](./media/image9.png)

図 5-9: コンテナー サービスへの分散アプリケーションの展開

最初に、配置時に特定のクラスターまたは orchestrators は従来の特定の展開スクリプトと使用できます (つまり、続き DC/OS または Kubernetes Docker と Docker のさまざまな配置メカニズムがある各 orchestrator あたりメカニズムSwarm) の代わりに簡単かつ使いやすい docker-作成ツールの docker compose.yml 定義ファイルに基づいています。 ただし、図 5 ~ 10 に示すように、Microsoft Visual Studio Team Services Docker の展開のタスクのおかげで今すぐまたことができますに展開する DC/OS Microsoft では、「翻訳」を実行するために、使い慣れた docker compose.yml ファイルを使用するだけで (から、docker compose.yml ファイル DC/OS で必要なその他の形式)。

![](./media/image10.png)

図 5-10: Docker の展開タスクを環境の RM に追加します。

図 5-11 では、Docker の展開タスクを編集し、対象の型 (Azure コンテナー サービス DC/OS、ここでは)、Docker 構成ファイル、および Docker レジストリ接続 (Azure コンテナー レジストリ Docker Hub など) を指定する方法について説明します。 これは、タスクが DC OS/クラスター内のコンテナーとして配置するのにすぐに使用できるカスタム Docker イメージを取得する場所です。

![](./media/image11.png)

図 5-11: Docker の展開タスクの定義の展開を Azure コンテナー サービス DC/OS

**詳細については** 詳細を確認する、CD には、Visual Studio Team Services と Docker のパイプラインは、次のサイトを参照してください。

Docker と Azure のコンテナー サービスの visual Studio Team Services の拡張機能: [https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure のコンテナー サービス: <https://aka.ms/azurecontainerservice>

続き DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>手順 5: 実行し、管理

実行しており、アプリケーションを管理するため、運用版でエンタープライズ レベルは、されでは、それ自体の操作の種類のための主な話題と人数がそのレベル (IT 操作) のこの領域の大きいスコープだけでなく、全体を次に充てること説明にチャプターです。

## <a name="step-6-monitor-and-diagnose"></a>手順 6: 監視および診断

このトピックの内容もについては次のチャプター IT 運用チームで実稼働システムで実行されるタスクの一部としてただし、この手順で取得した情報は、アプリケーションが継続的に向上できるように、開発チームにフィードする必要がありますを強調する必要があります。 その観点も DevOps の一部が、タスクや操作がによって実行される通常 IT です。

監視と診断が 100 %devops の領域の場合にのみ、監視プロセスおよびテスト シナリオまたは beta 環境に対して、開発チームによって実行される分析です。 これには、ロード テストを実行するか、ベータ版または、ベータ テストしようとしている、新しいバージョンの QA 環境を監視するだけでは行われます。

>[!div class="step-by-step"]
[前](index.md) [次へ] (../run-manage-monitor-docker-environments/index.md)
