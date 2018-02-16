---
title: "Microservices および multicontainer アプリケーション高いスケーラビリティと可用性を調整すること"
description: "Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4345fe8f36ecc32a7dd8e72fce5338bff308ffdf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Microservices および multicontainer アプリケーション高いスケーラビリティと可用性を調整すること

アプリケーションが microservices に基づいてまたは単に複数のコンテナーに分割する場合は、この運用環境でアプリケーションに orchestrators を使用することが不可欠です。 以前は、マイクロ サービス ベースのアプローチで導入された各マイクロ サービスを所有してそのモデルとデータ、開発と展開の観点から自律的なことができるようにします。 (SOA) のような複数のサービスで構成される従来のアプリケーションがある場合でもも複数のコンテナーまたは分散システムとして展開する必要がある 1 つのビジネス アプリケーションを構成するサービス。 このようなシステムは複雑でスケール アウトおよび管理できます。したがって、どうしても必要な orchestrator と拡張性を運用環境で multicontainer アプリケーションがある場合。

図 4. ~ 6. は、複数 microservices (コンテナー) から成るアプリケーションのクラスターへのデプロイを示しています。

![](./media/image6.png)

図 4 ~ 6: クラスターの場合、コンテナー

これは、論理的なアプローチのようになります。 どのようにする処理の負荷分散、ルーティング、およびこれらの構成されたアプリケーションを調整しますか。

Docker コマンド ライン インターフェイス (CLI) には、1 つのホスト上の 1 つのコンテナーの管理のニーズより複雑な分散アプリケーションに対して複数のホストに展開されている複数のコンテナーを管理する際に簡単にします。 ほとんどの場合は、管理プラットフォームは自動的にコンテナーを開始、停止、またはシャット ダウンする必要な場合、および理想的にはも制御ネットワークとデータ ストレージなどのリソースにアクセスする方法を必要があります。

個別のコンテナーまたは非常に単純な構成済みのアプリと microservices で大規模なエンタープライズ アプリケーションへの移行の管理を超えるに、オーケストレーションとプラットフォームをクラスタ リングを有効にする必要があります。

アーキテクチャと開発の観点から、microservices ベースの構築、大規模なエンタープライズをする場合は、アプリケーションが重要次のプラットフォームと高度なシナリオをサポートする製品について理解します。

-   **クラスターと orchestrators** 拡張する必要がある場合に、多くの Docker ホストにわたるアプリケーションをなど、大きな microservices ベース アプリケーションにすることが重要で 1 つのクラスターとしてそれらのホストのすべてを管理できるように基になるプラットフォームの複雑さを抽象化します。 コンテナーのクラスターと orchestrators が提供するものです。 Orchestrators には、Docker Swarm、続き DC/OS、Kubernetes (最初の 3 つ Azure コンテナー サービスを使用)、および Azure Service Fabric があります。

-   **スケジューラ** *スケジュール*管理者もユーザー インターフェイスを提供するように、クラスター内のコンテナーを起動するための機能を搭載することを意味します。 クラスター スケジューラは、いくつかの役割: クラスターのリソースを効率的に使用する、ノードまたはホスト間で効率的に負荷を分散コンテナーに、ユーザーによって提供される制約を設定してエラーに対する堅牢な高しつつである可用性。

クラスターとスケジューラの概念は密接に関連、ので、多くの場合、さまざまなベンダーが提供する製品が両方の機能のセットを指定します。 表 4-1 には、最も重要なプラットフォームとクラスターとスケジューラのソフトウェア選択肢が一覧表示します。 これらのクラスターは、Azure などのパブリック クラウドで一般に提供されます。

表 4-1: ソフトウェア プラットフォーム コンテナーのクラスタ リング、オーケストレーション、およびスケジュール設定

| プラットフォーム | 説明 |
|---|---|
| Docker 群<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Docker 群を使用すると、クラスターと Docker コンテナーをスケジュールできます。 群を使用すると、単一の仮想の Docker ホストに Docker ホストのプールを有効にすることができます。 クライアントは、ホスト、いる群を簡単にアプリケーションをスケールを複数のホストを意味するのと同様に、群に API 要求を行うことができます。 <br /><br /> Docker 群は、Docker、会社から製品です。 <br /><br /> Docker v1.12 後で、ネイティブ モードと組み込み Swarm モードを実行することもできます。 |
| 続き DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  続きエンタープライズ DC/OS (Apache Mesos に基づく) は、コンテナーと分散アプリケーションを実行するための運用環境でプラットフォームです。 <br /><br /> DC/OS は、抽象化して、クラスターで利用可能なリソースのコレクションとそれらのリソース上に作成されたコンポーネントを利用することによって機能します。 通常、マラソンは DC/OS と統合されて、スケジューラとして使用されます。 |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes は、クラスター インフラストラクチャと機能の調整にスケジュール設定のコンテナーの範囲の機能を提供するオープン ソース製品です。 ホストのクラスター間での展開、スケーリング、およびアプリケーションのコンテナーの操作を自動化できます。 <br /><br /> Kubernetes は、簡単な管理と検出の論理ユニットにアプリケーションのコンテナーをグループ化するコンテナーを中心としたインフラストラクチャを提供します。 |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)は、アプリケーションを構築するための Microsoft microservices プラットフォームです。 [Orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)のサービスし、マシンのクラスターを作成します。 既定では、Service Fabric 配置し、プロセスとしてサービスがアクティブになりますが、Service Fabric は、Docker コンテナー イメージのサービスを展開できます。 重要な同じアプリケーション内のコンテナー内のサービスとプロセスにサービスが混在することができます。 <br /><br /> 2017 年、月の時点で、Docker コンテナーとして展開するサービスをサポートするサービス ファブリックの機能はプレビュー状態です。 <br /><br /> 使用してから、さまざまな方法での Service Fabric サービスを開発することができます、[プログラミング モデル Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)展開[ゲストの実行可能ファイル](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app)コンテナーだけでなくです。 Service Fabric のように規範的なアプリケーション モデルをサポートしている[ステートフル サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。

## <a name="using-container-based-orchestrators-in-azure"></a>Azure でのコンテナーに基づく orchestrators の使用

いくつかのクラウドのベンダーは、Docker コンテナーのサポートと Docker のクラスターと Azure、Amazon EC2 コンテナー サービス、および Google コンテナー エンジンをなど、オーケストレーションのサポートを提供します。 Azure は、次のセクションで説明したように、Docker の Azure コンテナー サービスを通じたクラスターと orchestrator のサポートを提供します。

他の選択肢では、Linux と Windows コンテナーに基づいた Docker もサポートする Azure Service Fabric を使用します。 Service Fabric が Azure またはその他のクラウドで実行されると、[オンプレミス](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)です。

## <a name="using-azure-container-service"></a>Azure のコンテナー サービスを使用します。

Docker クラスターでは、複数の Docker ホストをプールし、クラスター内に複数のコンテナーを展開できるように 1 つの仮想 Docker ホストとして公開します。 クラスターでは、スケーラビリティと正常性などのすべての複雑な管理機能を処理します。 図 4-7 では、構成されたアプリケーションは、Docker クラスターがコンテナー サービスをどのようにマップする方法を表します。

コンテナー サービスは、作成、構成、およびコンテナー化アプリケーションを実行する事前に構成された Vm のクラスターの管理を簡略化する方法を提供します。 人気のオープン ソースのスケジュール設定とオーケストレーション ツールの構成を最適化を使用して、コンテナー サービスですることが、既存のスキルを使用するか、コミュニティの専門知識を展開し、コンテナー ベースの管理の発展し続けている本文上の描画Azure でのアプリケーションです。

コンテナー サービスは、Azure の具体的には一般的な Docker クラスタ リングのオープン ソース ツールとテクノロジの構成を最適化します。 コンテナーと、アプリケーションの構成の両方の移植性を提供する、開いているソリューションが表示されます。 サイズ、ホストの数と、orchestrator ツールを選択して、コンテナー サービスでは、他のすべてを処理します。

コンテナー サービスでは、Docker images を使って、アプリケーションのコンテナーが完全に移植可能であることを確認します。 これらのアプリケーションが数千またはでも万のコンテナーに拡張できることを確認するオーケストレーションのオープン ソース プラットフォーム DC/OS、Kubernetes、Docker Swarm などの選択肢がサポートしています。

Azure コンテナー サービスを使用には、オーケストレーション層に指定するなど、アプリケーションの移植性を維持しながら Azure のエンタープライズ レベルの機能の利点がかかります。

![](./media/image11.png)

図 4-7: Azure コンテナー サービスでの選択内容をクラスタ リング

図 4-8 に示すように、コンテナー サービス DC/OS、Kubernetes、Docker Swarm を展開するために Azure によって提供されるインフラストラクチャだけでは、その他の orchestrator が実装していません。 したがって、コンテナー サービスにはない、orchestrator では、そのためです。のみであるインフラストラクチャをコンテナー用の既存のオープン ソース orchestrators を活用することをお勧めします。

![](./media/image12.png)

コンテナー サービスで、図 4-8: Orchestrators

使用量の観点からは、コンテナー サービスの目的は、人気のオープン ソース ツールとテクノロジを使用して、コンテナーのホスト環境を提供します。 このため、選択した orchestrator の標準 API エンドポイントを公開します。 これらのエンドポイントを使用すると、それらのエンドポイントと通信できる任意のソフトウェアを使用することができます。 たとえばの場合は、Docker Swarm エンドポイントすることもできます Docker CLI を使用します。 DC/os、DC/OS CLI を使用することもできます。

### <a name="getting-started-with-container-service"></a>コンテナー サービスの概要

コンテナー サービスの使用を開始するには、Azure Resource Manager テンプレートを使用して、Azure ポータルからコンテナー サービスのクラスターを展開する、または[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)です。 使用可能なテンプレートが含まれる[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、 [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)、および[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)です。 Azure の構成を追加または高度なを含めるのクイック スタート テンプレートを変更することができます。

**詳細については** 、Azure の web サイトのコンテナー サービス クラスターの展開の詳細については、読み取り[クラスターを展開する Azure コンテナー サービス](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)です。

ACS の一部として既定でインストールされているソフトウェアのいずれかの料金はありません。 すべての既定のオプションは、オープン ソース ソフトウェアで実装されます。

コンテナー サービスは、標準的な A、D、DS、G、および GS シリーズの Linux Vm で、Azure で現在使用できます。 その他の基になるインフラストラクチャ リソースが使用される、記憶域やネットワークなど、選択した多くのコンピューティング インスタンスに対してのみ料金が発生します。 料金はかかりません増分コンテナー サービスの自体です。

### <a name="additional-resources"></a>その他の技術情報

追加情報を検索する場所を次に示します。

-   ソリューション コンテナー サービスをホストしている Docker コンテナーの概要:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker 群の概要:  
    <https://docs.docker.com/swarm/overview/>

-   モードの概要を swarm:  
    <https://docs.docker.com/engine/swarm/>

-   続き DC/OS の概要:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (公式サイト):  
    <http://kubernetes.io/>

## <a name="using-service-fabric"></a>Service Fabric を使用します。

Service Fabric からサービスを提供することをスタイルで通常モノリシック個、「ボックス」製品を提供するマイクロソフトの移行が発生し、します。 構築し、規模では、Azure SQL Database、Azure Document DB、Azure Service Bus、Cortana のバックエンドなどの大規模なサービスを運用環境では、Service Fabric を形です。 プラットフォームはますます多くのサービスで採用して時間の経過と共に進歩しました。 重要なは、Service Fabric は、Azure では、スタンドアロン Windows Server の展開でもを実行する必要があります。

Service Fabric の目的を構築およびサービスを実行してチームが microservices アプローチを使用するビジネス上の問題を解決できるようにインフラストラクチャ リソースを効率的に利用する困難な問題を解決するために、します。

Service Fabric は、microservices アプローチを使用するアプリケーションを構築するための 2 つの広範な領域を提供します。

-   システム サービスを展開、拡張、アップグレード、検出すると、および失敗したサービスを再起動して、サービスの場所を検出、状態を管理、および正常性を監視を提供するプラットフォームです。 これらのシステム サービスを使用して、前に説明した microservices の特性の多く有効で提供します。

-   プログラミング Api、またはフレームワーク、microservices としてアプリケーションを構築できるようにする:[信頼性の高いアクターと信頼性の高いサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)です。 もちろん、マイクロ サービスを構築するためのコードを選択できますが、これらの Api ジョブさらにわかりやすい行い深いレベルでプラットフォームと統合します。 正常性と診断情報を取得するこの方法では、信頼性の高い状態管理を利用できます。

Service Fabric は、サービスを構築する方法に関して依存しないと、任意のテクノロジを使用することができます。 ただし、microservices をビルドしやすく組み込みのプログラミング Api を提供します。

図 4-9 では、作成および簡単なプロセス、または Docker のコンテナーとして、Service Fabric で microservices を実行する方法について説明します。 同じ Service Fabric クラスター内のプロセスに基づく microservices でコンテナー ベース microservices を混在させることもできます。

![](./media/image13.png)

図 4. ~ 9.: プロセス、または Azure Service Fabric 内のコンテナーとして microservices を展開します。

Linux と Windows のホストに基づいて Service Fabric クラスターには、Docker Linux コンテナーと Windows コンテナーを実行できます。

**詳細については** 最新の状態について Service Fabric でのコンテナーのサポートは、Azure の web サイト「 [Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

Service Fabric は、異なる論理アーキテクチャ (ビジネス microservices または範囲指定されたコンテキスト) 物理的な実装を定義するプラットフォームの良い例です。 実装する場合など、[ステートフル Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)で[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)、次のセクションで導入されたを"[ステートレスとステートフル microservices](#stateless-versus-stateful-microservices)、"複数の物理サービスを含むビジネス マイクロ サービスの概念がある場合。

図 4-10、および Service Fabric ステートフルの信頼性の高いサービスを実装する場合、論理/ビジネス マイクロ サービスの観点から考えることに示す、通常必要がありますを 2 層のサービスを実装します。 1 つ目は、バック エンド ステートフルな信頼性の高いサービスで複数のパーティションを処理します。 2 つ目は、フロント エンド サービスは、または複数のパーティションまたはステートフルなサービス インスタンス間のルーティングとデータの集計を担当する、ゲートウェイ サービスです。 ゲートウェイ サービスは、Service Fabric と組み合わせて使用するバックエンド サービスにアクセスする再試行ループでクライアント側の通信を処理するも[リバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)です。

![](./media/image14.png)

Service Fabric でいくつかのステートフルとステートレスなサービスを使って図 4-10: ビジネス マイクロ サービス

いずれの場合は、Service Fabric ステートフル Reliable Services を使用する場合もがある場合、論理またはビジネス マイクロ サービス (範囲指定されたコンテキスト) 複数の物理サービスで構成される通常します。 それぞれに、ゲートウェイ サービス、およびパーティションのサービスのアドレスは、図 4 ~ 10 のように、ASP.NET Web API サービスとして実装できます。

Service Fabric でグループ化し、としてのサービスのグループを展開、 [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)、これはパッケージ化と、orchestrator またはクラスターの配置の単位。 そのため、Service Fabric アプリケーションにもこの自律的なビジネスおよび論理マイクロ サービス境界または範囲指定のコンテキストにマップします。

### <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

サービス ファブリック内のコンテナー、に関してもに、Service Fabric クラスター内のコンテナー イメージのサービスを展開できます。 図 4-11 は、そのほとんどのサービスごとの 1 つだけのコンテナーがある場合を示しています。

![](./media/image15.png)

Service Fabric でいくつかのサービス (コンテナー) で、図 4-11: ビジネスのマイクロ サービス

ただし、いわゆる「サイドカー」コンテナー (論理サービスの一部としてまとめて配置する必要のある 2 つのコンテナー) が Service Fabric 可能もです。 重要な点は、ビジネス マイクロ サービスがいくつかのまとまりのある要素を囲む論理的な境界でことです。 多くの場合、1 つのデータ モデルを含む 1 つのサービスかもしれませんが、場合によっては他の物理的ないくつかのサービスもする必要があります。

この書き込み (2017 年 4 月) の時点で Service Fabric でできないサービスを配置する SF 信頼性の高いステートフル コンテナーの — ゲスト コンテナー、ステートレスなサービス、またはコンテナー内のアクター サービスのみに展開することができます。 図 4-12 のように、同じ Service Fabric アプリケーション内のコンテナーでのプロセスでのサービスとサービスを混在させることがある注意してください。

![](./media/image16.png)

図 4-12: ビジネス マイクロ サービスのコンテナーとステートフル サービスの Service Fabric アプリケーションにマップされています。

サポートは、Docker コンテナーを Linux または Windows コンテナーを使用しているかどうかに応じて異なるもできます。 Service Fabric でコンテナーのサポートは、今後のリリースで展開されます。 Service Fabric で、Azure の web サイトのコンテナーのサポートについての最新のニュース読み取り[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

## <a name="stateless-versus-stateful-microservices"></a>ステートレスとステートフル microservices

前述のように、各マイクロ サービス (論理範囲指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有する必要があります。 ステートレス microservices の場合、データベースは、外部、SQL Server のようなリレーショナル オプションまたは MongoDB または Azure DocumentDB などの NoSQL オプションを採用することになります。

サービス自体もできる、ステートフルなマイクロ サービス内でデータが格納されていることを意味します。 このデータはだけでなく、同じサーバーが、メモリ内のマイクロ サービス プロセス内で可能性がありますが存在してドライブに保存し、その他のノードにレプリケートします。 図 4-13 では、別の方法を示します。

![](./media/image17.png)

図 4-13: ステートレスとステートフル microservices

ステートレスな方法は、完全に有効なアプローチは、従来の既知のパターンに似ています、ステートフルな microservices よりを実装する方が簡単です。 ステートレス microservices プロセスおよびデータ ソース間の待機時間を強制します。 それに伴うより移動の個追加のキャッシュとキューのパフォーマンスを改善しようとします。 結果は、多数の階層のある複雑なアーキテクチャを持つ終了できます。

これに対し、[ステートフル microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)ドメイン ロジックとデータ間の待機時間がないために、高度なシナリオで excel ことができます。 大量のデータ処理、ゲーム バックエンド、データベースを対象として、サービス、およびローカル状態を高速アクセスを提供、ステートフルなサービスの恩恵をすべてその他の低待機時間シナリオです。

ステートレスおよびステートフルなサービスは、相互に補完します。 たとえば、ステートフルなサービスは、複数のパーティションに分割する可能性があります。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションに対処する方法を知っているゲートウェイ サービスとして動作するステートレスなサービスを必要があります。

ステートフルなサービスでは、欠点がします。 スケール アウトを許可するための複雑さのレベルをかけます。外部データベース システムで実装する場合と通常の機能は、ステートフルな microservices とデータのパーティション分割の間でデータのレプリケーションなどのタスクの対処をする必要があります。 ただし、これは、orchestrator のような領域の 1 つ[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)でその[ステートフルな信頼性の高いサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)最も役立つことができます: 開発とステートフルのライフ サイクルを簡略化microservices を使用して、 [Services API の信頼性の高い](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。

他のステートフルなサービス、Actor パターンをサポートして、フォールト トレランスとビジネス ロジックとデータ間の待機時間を向上できるようにするマイクロ サービス フレームワークは Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research とから[Akka.NET](http://getakka.net/)です。 両方のフレームワークは、現在 Docker のサポートを向上させます。

Docker コンテナーは自身のステートレスなことに注意してください。 ステートフルなサービスを実装する場合は、前に説明した追加の規範的な高度なフレームワークの 1 つ必要があります。 ただし、現時点では、Service Fabric でのステートフルなサービスはサポートされていません plain microservices としてのみのコンテナーとして。 コンテナーで信頼性の高いサービス サポートは、Service Fabric の今後のバージョンで使用されます。


>[!div class="step-by-step"]
[前](soa applications.md) [次へ] (docker-アプリの開発-environment.md)
