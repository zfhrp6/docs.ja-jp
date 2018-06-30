---
title: Microservices および multicontainer アプリケーション高いスケーラビリティと可用性を調整すること
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5c7016fa8b731170a63f5d0f9d9bed3b72090be4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106380"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Microservices および multicontainer アプリケーション高いスケーラビリティと可用性を調整すること

アプリケーションがマイクロサービスに基づく場合や、単に複数のコンテナーに分割されている場合、運用可能なアプリケーションのオーケストレーターを使用することが不可欠です。 前述のとおり、マイクロサービス ベースの方法では、マイクロサービスはそれぞれモデルとデータを所有しているため、開発と展開の観点から自立していることになります。 (SOA) のような複数のサービスで構成される従来のアプリケーションがある場合でもも複数のコンテナーまたは分散システムとして展開する必要がある 1 つのビジネス アプリケーションを構成するサービス。 このようなシステムは複雑でスケール アウトおよび管理できます。したがって、どうしても必要な orchestrator と拡張性を運用環境で multicontainer アプリケーションがある場合。

図 4. ~ 6. は、複数 microservices (コンテナー) から成るアプリケーションのクラスターへのデプロイを示しています。

![](./media/image6.png)

図 4 ~ 6: クラスターの場合、コンテナー

これは論理的な方法のように見えます。 どのようにする処理の負荷分散、ルーティング、およびこれらの構成されたアプリケーションを調整しますか。

Docker コマンド ライン インターフェイス (CLI) には、1 つのホスト上の 1 つのコンテナーの管理のニーズより複雑な分散アプリケーションに対して複数のホストに展開されている複数のコンテナーを管理する際に簡単にします。 ほとんどの場合は、管理プラットフォームは自動的にコンテナーを開始、停止、またはシャット ダウンする必要な場合、および理想的にはも制御ネットワークとデータ ストレージなどのリソースにアクセスする方法を必要があります。

個々のコンテナーまたは非常に単純な構成アプリを管理するだけでなく、マイクロサービスを使用してより大きなエンタープライズ アプリケーションを管理するには、オーケストレーションおよびクラスタリング プラットフォームが必要になります。

アーキテクチャと開発の観点から、microservices ベースの構築、大規模なエンタープライズをする場合は、アプリケーションが重要次のプラットフォームと高度なシナリオをサポートする製品について理解します。

-   **クラスターと orchestrators** 拡張する必要がある場合に、多くの Docker ホストにわたるアプリケーションをなど、大きな microservices ベース アプリケーションにすることが重要で 1 つのクラスターとしてそれらのホストのすべてを管理できるように基になるプラットフォームの複雑さを抽象化します。 これが、コンテナー クラスターとオーケストレーターで提供されるものです。 Orchestrators には、Docker Swarm、続き DC/OS、Kubernetes (最初の 3 つ Azure コンテナー サービスを使用)、および Azure Service Fabric があります。

-   **スケジューラ** *スケジュール*管理者もユーザー インターフェイスを提供するように、クラスター内のコンテナーを起動するための機能を搭載することを意味します。 クラスター スケジューラは、いくつかの役割: クラスターのリソースを効率的に使用する、ノードまたはホスト間で効率的に負荷を分散コンテナーに、ユーザーによって提供される制約を設定してエラーに対する堅牢な高しつつである可用性。

クラスターとスケジューラの概念は密接に関連しており、さまざまなベンダーによって提供される製品では、多くの場合、両方の機能セットが提供されます。 表 4-1 には、最も重要なプラットフォームとクラスターとスケジューラのソフトウェア選択肢が一覧表示します。 これらのクラスターは、Azure などのパブリック クラウドで一般に提供されます。

表 4-1: ソフトウェア プラットフォーム コンテナーのクラスタ リング、オーケストレーション、およびスケジュール設定

| プラットフォーム | 説明 |
|---|---|
| Docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Docker 群を使用すると、クラスターと Docker コンテナーをスケジュールできます。 Swarm を使用することで、Docker ホストのプールを単一の仮想 Docker ホストにすることができます。 クライアントは、ホスト、いる群を簡単にアプリケーションをスケールを複数のホストを意味するのと同様に、群に API 要求を行うことができます。 <br /><br /> Docker Swarm は Docker 社の製品です。 <br /><br /> Docker v1.12 以降ではネイティブの組み込み Swarm モードを実行できます。 |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  Mesosphere Enterprise DC/OS (Apache Mesos に基づく) は、コンテナーと分散アプリケーションを実行するための運用可能なプラットフォームです。 <br /><br /> DC/OS は、クラスターで使用可能なリソースのコレクションを抽象化し、これらのリソースをその上に構築されたコンポーネントで使用できるようにすることで機能します。 Marathon は通常、DC/OS と統合されたスケジューラとして使用されます。 |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes はオープンソースの製品であり、クラスターのインフラストラクチャとコンテナーのスケジューリングからオーケストレーション機能までの機能を提供します。 ホストのクラスター間での展開、スケーリング、およびアプリケーションのコンテナーの操作を自動化できます。 <br /><br /> Kubernetes ではコンテナー中心のインフラストラクチャが提供され、アプリケーション コンテナーを論理ユニットにグループ化し、管理と検出を容易にします。 |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) は、アプリケーションを構築するための Microsoft マイクロサービス プラットフォームです。 サービスの[オーケストレーター](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)であり、マシンのクラスターを作成します。 既定では、Service Fabric 配置し、プロセスとしてサービスがアクティブになりますが、Service Fabric は、Docker コンテナー イメージのサービスを展開できます。 重要な同じアプリケーション内のコンテナー内のサービスとプロセスにサービスが混在することができます。 <br /><br /> 2017 年、月の時点で、Docker コンテナーとして展開するサービスをサポートするサービス ファブリックの機能はプレビュー状態です。 <br /><br /> 使用してから、さまざまな方法での Service Fabric サービスを開発することができます、[プログラミング モデル Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)展開[ゲストの実行可能ファイル](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app)コンテナーだけでなくです。 Service Fabric のように規範的なアプリケーション モデルをサポートしている[ステートフル サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。

## <a name="using-container-based-orchestrators-in-azure"></a>Azure でのコンテナーに基づく orchestrators の使用

いくつかのクラウドのベンダーは、Docker コンテナーのサポートと Docker のクラスターと Azure、Amazon EC2 コンテナー サービス、および Google コンテナー エンジンをなど、オーケストレーションのサポートを提供します。 Azure は、次のセクションで説明したように、Docker の Azure コンテナー サービスを通じたクラスターと orchestrator のサポートを提供します。

他の選択肢では、Linux と Windows コンテナーに基づいた Docker もサポートする Azure Service Fabric を使用します。 Service Fabric が Azure またはその他のクラウドで実行されると、[オンプレミス](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)です。

## <a name="using-azure-container-service"></a>Azure Container Service の使用

Docker クラスターは複数の Docker ホストをプールし、単一の Docker ホストとして公開するため、複数のコンテナーをクラスターに展開できます。 クラスターでは、スケーラビリティと正常性などのすべての複雑な管理機能を処理します。 図 4-7 では、構成されたアプリケーションは、Docker クラスターがコンテナー サービスをどのようにマップする方法を表します。

コンテナー サービスは、作成、構成、およびコンテナー化アプリケーションを実行する事前に構成された Vm のクラスターの管理を簡略化する方法を提供します。 人気のオープン ソースのスケジュール設定とオーケストレーション ツールの構成を最適化を使用して、コンテナー サービスですることが、既存のスキルを使用するか、コミュニティの専門知識を展開し、コンテナー ベースの管理の発展し続けている本文上の描画Azure でのアプリケーションです。

コンテナー サービスは、Azure の具体的には一般的な Docker クラスタ リングのオープン ソース ツールとテクノロジの構成を最適化します。 コンテナーとアプリケーションの構成の両方に移植性を提供するオープン ソリューションが得られます。 ユーザーはサイズ、ホストの数、オーケストレーター ツールを選択し、Container Service は他のすべてを処理します。

コンテナー サービスでは、Docker images を使って、アプリケーションのコンテナーが完全に移植可能であることを確認します。 これらのアプリケーションが数千またはでも万のコンテナーに拡張できることを確認するオーケストレーションのオープン ソース プラットフォーム DC/OS、Kubernetes、Docker Swarm などの選択肢がサポートしています。

Azure コンテナー サービスを使用には、オーケストレーション層に指定するなど、アプリケーションの移植性を維持しながら Azure のエンタープライズ レベルの機能の利点がかかります。

![](./media/image11.png)

図 4-7: Azure コンテナー サービスでの選択内容をクラスタ リング

図 4-8 に示すように、コンテナー サービス DC/OS、Kubernetes、Docker Swarm を展開するために Azure によって提供されるインフラストラクチャだけでは、その他の orchestrator が実装していません。 したがって、コンテナー サービスにはない、orchestrator では、そのためです。のみであるインフラストラクチャをコンテナー用の既存のオープン ソース orchestrators を活用することをお勧めします。

![](./media/image12.png)

コンテナー サービスで、図 4-8: Orchestrators

使用量の観点からは、コンテナー サービスの目的は、人気のオープン ソース ツールとテクノロジを使用して、コンテナーのホスト環境を提供します。 この目的を達成するために、選択されたオーケストレーターの標準的な API エンドポイントが公開されます。 これらのエンドポイントを使用すると、それらのエンドポイントと通信できる任意のソフトウェアを使用することができます。 たとえばの場合は、Docker Swarm エンドポイントすることもできます Docker CLI を使用します。 DC/OS では、DC/OS CLI を使用するよう選択できます。

### <a name="getting-started-with-container-service"></a>コンテナー サービスの概要

コンテナー サービスの使用を開始するには、Azure Resource Manager テンプレートを使用して、Azure ポータルからコンテナー サービスのクラスターを展開する、または[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)です。 使用可能なテンプレートには、[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)、[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos) があります。 Azure の構成を追加または高度なを含めるのクイック スタート テンプレートを変更することができます。

**詳細については** 、Azure の web サイトのコンテナー サービス クラスターの展開の詳細については、読み取り[クラスターを展開する Azure コンテナー サービス](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)です。

ACS の一部として既定でインストールされるソフトウェアはいずれも無料です。 既定のすべてのオプションはオープン ソース ソフトウェアと共に実装されます。

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
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Service Fabric を使用します。

Service Fabric からサービスを提供することをスタイルで通常モノリシック個、「ボックス」製品を提供するマイクロソフトの移行が発生し、します。 構築し、規模では、Azure SQL Database、Azure Document DB、Azure Service Bus、Cortana のバックエンドなどの大規模なサービスを運用環境では、Service Fabric を形です。 プラットフォームは時間をかけてより多くのサービスを採用するように進化しました。 重要なのは、Service Fabric は、Azure 内だけでなく、スタンドアロン Windows Server の展開でも実行する必要があることです。

Service Fabric の目的を構築およびサービスを実行してチームが microservices アプローチを使用するビジネス上の問題を解決できるようにインフラストラクチャ リソースを効率的に利用する困難な問題を解決するために、します。

Service Fabric は、マイクロサービス アプローチを使用するアプリケーションの構築に役立つ 2 つの広範な領域を提供します。

-   展開、拡張、アップグレード、検出のためのシステム サービス、失敗したサービスの再起動、サービスの場所の検出、状態の管理、正常性の監視を提供するプラットフォーム。 これらのシステム サービスを使用して、前に説明した microservices の特性の多く有効で提供します。

-   アプリケーションをマイクロサービスとして構築するために役立つプログラミング API またはフレームワーク: [Reliable Actors と Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)。 もちろん、マイクロサービスを構築するための任意のコードを選択できますが、これらの API によってジョブがさらにわかりやすくなり、より深いレベルでプラットフォームと統合されます。 この方法で正常性情報と診断情報を取得し、信頼できる状態管理を利用することができます。

Service Fabric は、サービスの構築方法に依存しないので、任意のテクノロジを使用することができます。 ただし、マイクロサービスをビルドしやすくする組み込みのプログラミング API を提供します。

図 4-9 では、作成および簡単なプロセス、または Docker のコンテナーとして、Service Fabric で microservices を実行する方法について説明します。 コンテナーベースのマイクロサービスとプロセッサーベースのマイクロサービスを同じ Service Fabric クラスター内に混在させることもできます。

![](./media/image13.png)

図 4. ~ 9.: プロセス、または Azure Service Fabric 内のコンテナーとして microservices を展開します。

Linux と Windows のホストに基づいて Service Fabric クラスターには、Docker Linux コンテナーと Windows コンテナーを実行できます。

**詳細については** 最新の状態について Service Fabric でのコンテナーのサポートは、Azure の web サイト「 [Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

Service Fabric は、異なる論理アーキテクチャ (ビジネス microservices または範囲指定されたコンテキスト) 物理的な実装を定義するプラットフォームの良い例です。 実装する場合など、[ステートフル Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)で[Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)、次のセクションで導入されたを"[ステートレスとステートフル microservices](#stateless-versus-stateful-microservices)、"複数の物理サービスを含むビジネス マイクロ サービスの概念がある場合。

図 4-10、および Service Fabric ステートフルの信頼性の高いサービスを実装する場合、論理/ビジネス マイクロ サービスの観点から考えることに示す、通常必要がありますを 2 層のサービスを実装します。 1 つ目は、バック エンド ステートフルな信頼性の高いサービスで複数のパーティションを処理します。 2 つ目は、フロントエンド サービスまたはゲートウェイ サービスで、複数のパーティションまたはステートフル サービス インスタンス間のルーティングとデータの集計を担当します。 ゲートウェイ サービスは、Service Fabric と組み合わせて使用するバックエンド サービスにアクセスする再試行ループでクライアント側の通信を処理するも[リバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)です。

![](./media/image14.png)

Service Fabric でいくつかのステートフルとステートレスなサービスを使って図 4-10: ビジネス マイクロ サービス

いずれの場合でも、Service Fabric ステートフル Reliable Services を使用する場合、通常は複数の物理サービスで構成される論理的/ビジネス マイクロサービス (境界指定されたコンテキスト) も使用できます。 それぞれに、ゲートウェイ サービス、およびパーティションのサービスのアドレスは、図 4 ~ 10 のように、ASP.NET Web API サービスとして実装できます。

Service Fabric では、サービスをグループ化して、サービスのグループを [Service Fabric アプリケーション](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)として展開することができます。これは、オーケストレーターおよびクラスター用のパッケージ化および展開の単位です。 そのため、Service Fabric アプリケーションにもこの自律的なビジネスおよび論理マイクロ サービス境界または範囲指定のコンテキストにマップします。

### <a name="service-fabric-and-containers"></a>Service Fabric とコンテナー

サービス ファブリック内のコンテナー、に関してもに、Service Fabric クラスター内のコンテナー イメージのサービスを展開できます。 図 4-11 は、そのほとんどのサービスごとの 1 つだけのコンテナーがある場合を示しています。

![](./media/image15.png)

Service Fabric でいくつかのサービス (コンテナー) で、図 4-11: ビジネスのマイクロ サービス

ただし、いわゆる「サイドカー」コンテナー (論理サービスの一部としてまとめて配置する必要のある 2 つのコンテナー) が Service Fabric 可能もです。 重要な点は、ビジネス マイクロサービスが、いくつかのまとまりのある要素を囲む論理的な境界であることです。 多くの場合、1 つのデータ モデルを含む 1 つのサービスかもしれませんが、場合によっては他の物理的ないくつかのサービスもする必要があります。

この書き込み (2017 年 4 月) の時点で Service Fabric でできないサービスを配置する SF 信頼性の高いステートフル コンテナーの — ゲスト コンテナー、ステートレスなサービス、またはコンテナー内のアクター サービスのみに展開することができます。 図 4-12 のように、同じ Service Fabric アプリケーション内のコンテナーでのプロセスでのサービスとサービスを混在させることがある注意してください。

![](./media/image16.png)

図 4-12: ビジネス マイクロ サービスのコンテナーとステートフル サービスの Service Fabric アプリケーションにマップされています。

サポートは、Docker コンテナーを Linux または Windows コンテナーを使用しているかどうかに応じて異なるもできます。 Service Fabric でコンテナーのサポートは、今後のリリースで展開されます。 Service Fabric で、Azure の web サイトのコンテナーのサポートについての最新のニュース読み取り[Service Fabric とコンテナー](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

## <a name="stateless-versus-stateful-microservices"></a>ステートレス マイクロサービスとステートフル マイクロサービスの比較

前述のように、各マイクロサービス (論理的な境界指定されたコンテキスト) は、ドメイン モデル (データとロジック) を所有している必要があります。 ステートレス microservices の場合、データベースは、外部、SQL Server のようなリレーショナル オプションまたは MongoDB または Azure DocumentDB などの NoSQL オプションを採用することになります。

サービス自体もできる、ステートフルなマイクロ サービス内でデータが格納されていることを意味します。 このデータはだけでなく、同じサーバーが、メモリ内のマイクロ サービス プロセス内で可能性がありますが存在してドライブに保存し、その他のノードにレプリケートします。 図 4-13 では、別の方法を示します。

![](./media/image17.png)

図 4-13: ステートレスとステートフル microservices

ステートレスな方法は、完全に有効なアプローチは、従来の既知のパターンに似ています、ステートフルな microservices よりを実装する方が簡単です。 ステートレス マイクロサービスは、プロセスおよびデータ ソース間の遅延を強制します。 追加のキャッシュとキューを使用してパフォーマンスを改善しようとしている場合は、含まれる移動する部分が増加します。 結果として、階層の数が多すぎる複雑なアーキテクチャになる可能性があります。

これに対し、[ステートフル microservices](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)ドメイン ロジックとデータ間の待機時間がないために、高度なシナリオで excel ことができます。 大量のデータ処理、ゲーム バックエンド、データベースを対象として、サービス、およびローカル状態を高速アクセスを提供、ステートフルなサービスの恩恵をすべてその他の低待機時間シナリオです。

ステートレス サービスおよびステートフル サービスは相互に補完します。 たとえば、ステートフルなサービスは、複数のパーティションに分割する可能性があります。 それらのパーティションにアクセスするには、パーティション キーに基づく各パーティションへのアドレス指定方法を知っているゲートウェイ サービスとして、ステートレス サービスが動作する必要があります。

ステートフル サービスには欠点があります。 スケール アウトを許可するための複雑さのレベルをかけます。通常外部データベース システムによって実装される機能は、ステートフル マイクロサービスにまたがるレプリケーションや、データのパーティション分割などの機能として対処する必要があります。 ただし、これは、orchestrator のような領域の 1 つ[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture)でその[ステートフルな信頼性の高いサービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis)最も役立つことができます: 開発とステートフルのライフ サイクルを簡略化microservices を使用して、 [Services API の信頼性の高い](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。

ステートフル サービスを許可し、Actor パターンをサポートし、ビジネス ロジックとデータ間のフォールト トレランスと遅延を改善する他のマイクロサービス フレームワークは、Microsoft [Orleans](https://github.com/dotnet/orleans)、Microsoft Research、および [Akka.NET](https://getakka.net/) です。 両方のフレームワークは、現在 Docker のサポートを向上させています。

Docker コンテナーはそれ自身ステートレスなことに注意してください。 ステートフル サービスを実装する場合は、前に説明した追加の規範的で高度なフレームワークの 1 つが必要です。 ただし、現時点では、Service Fabric でのステートフルなサービスはサポートされていません plain microservices としてのみのコンテナーとして。 コンテナーで信頼性の高いサービス サポートは、Service Fabric の今後のバージョンで使用されます。


>[!div class="step-by-step"]
[前へ](soa-applications.md)
[次へ](docker-apps-development-environment.md)
