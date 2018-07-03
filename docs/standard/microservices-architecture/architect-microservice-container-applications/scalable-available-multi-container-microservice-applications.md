---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: aab939af29849ceeef76d6f61b3d4f59d701094c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105463"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する

アプリケーションがマイクロサービスに基づく場合や、単に複数のコンテナーに分割されている場合、運用可能なアプリケーションのオーケストレーターを使用することが不可欠です。 前述のとおり、マイクロサービス ベースの方法では、マイクロサービスはそれぞれモデルとデータを所有しているため、開発と展開の観点から自立していることになります。 ただし、複数のサービスで構成される従来のアプリケーション (SOA など) を使用する場合でも、分散システムとして展開する必要がある単一のビジネス アプリケーションを構成する複数のコンテナーまたはサービスを使用する場合もあります。 この種のシステムはスケールアウトや管理が複雑であるため、運用可能でスケーラブルな複数のコンテナー アプリケーションを使用する場合、どうしてもオーケストレーターが必要になります。

図 4-23 は、複数のマイクロサービス (コンテナー) で構成されるアプリケーションのクラスターへの展開を示しています。

![](./media/image23.PNG)

**図 4-23**.  コンテナーのクラスター

これは論理的な方法のように見えます。 しかし、これらの構成されたアプリケーションの負荷分散、ルーティング、オーケストレーションはどのように処理するのでしょうか。

単一の Docker ホストのプレーン Docker エンジンは 1 つのホストでの単一のイメージ インスタンスの管理に関するニーズを満たしますが、より複雑な分散アプリケーションの複数のホストに展開されている複数のコンテナーの管理に関しては対応できません。 ほとんどの場合、管理プラットフォームが必要になります。このプラットフォームは自動的にコンテナーを開始し、イメージごとに複数のインスタンスでコンテナーをスケールアウトし、必要に応じて一時停止またはシャットダウンします。また、ネットワークおよびデータ ストレージなどのリソースへのアクセス方法を制御するのが理想的です。

個々のコンテナーまたは非常に単純な構成アプリを管理するだけでなく、マイクロサービスを使用してより大きなエンタープライズ アプリケーションを管理するには、オーケストレーションおよびクラスタリング プラットフォームが必要になります。

アーキテクチャと開発の観点から、マイクロサービス ベースのアプリケーションで構成される大規模なエンタープライズを構築する場合、高度なシナリオをサポートする次のプラットフォームと製品を理解することが重要です。

**クラスターとオーケストレーター**。 多くの Docker ホストでアプリケーションをスケールアウトする必要がある場合は、基になるプラットフォームの複雑さを抽象化し、これらすべてのホストを単一のクラスターとして管理できるようにすることが重要です。 これが、コンテナー クラスターとオーケストレーターで提供されるものです。 オーケストレーターの例として、Azure Service Fabric、Kubernetes、Docker Swarm、Mesosphere DC/OS があります。 最後の 3 つのオープンソース オーケストレーターは、Azure Container Service を介して Azure で使用できます。

**スケジューラ**。 *スケジューリング* は、管理者がクラスターのコンテナーを起動して、UI も提供できるようにすることを意味します。 クラスター スケジューラにはいくつかの役割があります。たとえば、クラスターのリソースを効率的に使用すること、ユーザーによって指定される制約を設定すること、ノードまたはホスト全体でのコンテナーの負荷分散を効率的に行うこと、高可用性を提供すると同時にエラーに対して堅牢であることなどです。

クラスターとスケジューラの概念は密接に関連しており、さまざまなベンダーによって提供される製品では、多くの場合、両方の機能セットが提供されます。 以下のリストに、クラスターとスケジューラーで最も重要なプラットフォームとソフトウェアの選択肢を示します。 これらのオーケストレーターは、通常、Azure などのパブリック クラウドで提供されます。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>コンテナーのクラスタリング、オーケストレーション、スケジューリングのためのソフトウェア プラットフォーム

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes はオープンソースの製品であり、クラスターのインフラストラクチャとコンテナーのスケジューリングからオーケストレーション機能までの機能を提供します。 ホストのクラスター全体のアプリケーション コンテナーの展開、スケーリング、操作を自動化できます。
>
> Kubernetes ではコンテナー中心のインフラストラクチャが提供され、アプリケーション コンテナーを論理ユニットにグループ化し、管理と検出を容易にします。
>
> Kubernetes は Linux では完成されていますが、Windows では未完成です。

Docker Swarm

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Docker Swarm では Docker コンテナーのクラスタリングとスケジューリングを行うことができます。 Swarm を使用することで、Docker ホストのプールを単一の仮想 Docker ホストにすることができます。 クライアントは、ホストの場合と同じ方法で Swarm に対して API 要求を行うことができます。これは、Swarm を使用することで、複数のホストへのアプリケーションのスケーリングが容易になることを意味します。
>
> Docker Swarm は Docker 社の製品です。
>
> Docker v1.12 以降ではネイティブの組み込み Swarm モードを実行できます。

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Mesosphere Enterprise DC/OS (Apache Mesos に基づく) は、コンテナーと分散アプリケーションを実行するための運用可能なプラットフォームです。
>
> DC/OS は、クラスターで使用可能なリソースのコレクションを抽象化し、これらのリソースをその上に構築されたコンポーネントで使用できるようにすることで機能します。 Marathon は通常、DC/OS と統合されたスケジューラとして使用されます。
>
> DC/OS は Linux では完成されていますが、Windows では未完成です。

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) は、アプリケーションを構築するための Microsoft マイクロサービス プラットフォームです。 サービスの[オーケストレーター](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)であり、マシンのクラスターを作成します。 Service Fabric は、サービスをコンテナーまたはプレーン プロセスとして展開できます。 同じアプリケーションとクラスター内にコンテナーのサービスとプロセスのサービスを混在させることもできます。
>
> Service Fabric は、[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction) や[ステートフル サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)などの追加の省略可能な規範的な [Service Fabric プログラミング モデル](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)を提供します。
>
> Service Fabric は Windows (年々進化している Windows) では完成されていますが、Linux では未完成です。 
> Linux と Windows の両方のコンテナーは、2017 年以降の Service Fabric でサポートされています。

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure でのコンテナー ベースのオーケストレーターの使用

いくつかのクラウド ベンダーでは Docker コンテナーのサポートに加え、Docker クラスターおよびオーケストレーション サポート (Microsoft Azure、Amazon EC2 Container Service、Google Container Engine を含む) が提供されます。 Microsoft Azure では、次のセクションの説明のとおり、Azure Container Service (ACS) を介して Docker クラスターおよびオーケストレーション サポートが提供されます。

Linux と Windows の両方のコンテナーに基づく Docker もサポートする、Microsoft Azure Service Fabric (マイクロサービス プラットフォーム) を使用することもできます。 Service Fabric は Azure またはその他のクラウドで実行され、[オンプレミス](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)でも実行されます。

## <a name="using-azure-container-service"></a>Azure Container Service の使用

Docker クラスターは複数の Docker ホストをプールし、単一の Docker ホストとして公開するため、複数のコンテナーをクラスターに展開できます。 クラスターは、スケーラビリティや正常性など、複雑な管理機能をすべて処理します。 図 4-24 に、Docker が構成されたアプリケーションの Docker クラスターがどのように Azure Container Service (ACS) にマップされるかが示されています。

ACS は、コンテナー化されたアプリケーションを実行するように事前に構成されている仮想マシンのクラスターの作成、構成、および管理を簡略化する方法を提供します。 一般的なオープンソースのスケジューリングおよびオーケストレーション ツールの最適化された構成を使用することで、ACS では、コンテナー ベースのアプリケーションを Microsoft Azure でデプロイして管理するための専門知識を持つ増加し続けるコミュニティを利用するか、既存のスキルを使用することができます。

Azure Container Service では、一般的な Docker クラスタリング オープンソース ツールとテクノロジの構成を Azure 専用に最適化します。 コンテナーとアプリケーションの構成の両方に移植性を提供するオープン ソリューションが得られます。 ユーザーはサイズ、ホストの数、オーケストレーター ツールを選択し、Container Service は他のすべてを処理します。

![](./media/image28.png)

**図 4-24** Azure Container Service でのクラスタリングの選択肢

ACS では Docker イメージを活用して、アプリケーション コンテナーを完全に移植できるようにします。 DC/OS (Apache Mesos を採用)、Kubernetes (Google によって最初に作成された)、および Docker Swarm などのオープンソースのオーケストレーション プラットフォームを選択でき、これらのアプリケーションが数千または数万ものコンテナーにスケーリングできるようにします。

Azure Container Service では、オーケストレーション レイヤーなどで、アプリケーションの移植性を維持しながら、Azure のエンタープライズ レベルの機能を活用できます。

![](./media/image29.png)

**図 4-25** ACS のオーケストレーター

図 4-25 に示すように、Azure Container Service は、DC/OS、Kubernetes または Docker Swarm をデプロイするために Azure によって提供される単なるインフラストラクチャですが、追加のオーケストレーターを実装しません。 したがって、ACS はそのようなオーケストレーターではなく、コンテナーの既存のオープンソース オーケストレーターを活用する単なるインフラストラクチャです。

使用の観点からは、Azure Container Service の目的は、一般的なオープンソース ツールとテクノロジを使用して、コンテナーのホスト環境を提供することです。 この目的を達成するために、選択されたオーケストレーターの標準的な API エンドポイントが公開されます。 これらのエンドポイントを使用することで、エンドポイントとの通信が可能な任意のソフトウェアを活用できます。 たとえば、Docker Swarm エンドポイントの場合、Docker コマンド ライン インターフェイス (CLI) を使用するよう選択できます。 DC/OS では、DC/OS CLI を使用するよう選択できます。

### <a name="getting-started-with-azure-container-service"></a>Azure Container Service の使用の開始 

Azure Container Service の使用を開始するには、Azure Resource Manager テンプレートまたは [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli) を使用して、Azure Portal から Azure Container Service クラスターをデプロイします。 使用可能なテンプレートには、[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、[Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)、[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos) があります。 追加の、または高度な Azure 構成を含めるためにクイック スタート テンプレートを変更することができます。 Azure Container Service クラスターの詳細については、Azure Web サイトの [Azure Container Service クラスターのデプロイ](https://docs.microsoft.com/azure/container-service/container-service-deployment)に関するページを参照してください。

ACS の一部として既定でインストールされるソフトウェアはいずれも無料です。 既定のすべてのオプションはオープン ソース ソフトウェアと共に実装されます。

ACS は、現在、Azure の標準 A、D、DS、G、GS シリーズの Linux 仮想マシンで使用可能です。 選択されたコンピューティング インスタンスと、ストレージやネットワーキングなどの利用された他の基になるインフラストラクチャ リソースにのみ課金されます。 ACS 自体の増分料金はありません。

## <a name="additional-resources"></a>その他の技術情報

-   **Azure Container Service を使用した Docker コンテナー ホスティング ソリューションの概要**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker Swarm 概要**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Swarm モード概要**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Mesosphere DC/OS 概要**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes。** 公式サイト。\
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[前へ](resilient-high-availability-microservices.md)
[次へ](using-azure-service-fabric.md)
