---
title: "Microservices と高いスケーラビリティと可用性のための複数のコンテナー アプリケーションの調整"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Microservices と高いスケーラビリティと可用性のための複数のコンテナー アプリケーションの調整"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Microservices と高いスケーラビリティと可用性のための複数のコンテナー アプリケーションの調整

アプリケーションが microservices に基づいてまたは単に複数のコンテナーに分割する場合は、この運用環境でアプリケーションに orchestrators を使用することが不可欠です。 以前は、マイクロ サービス ベースのアプローチで導入された各マイクロ サービスを所有してそのモデルとデータ、開発と展開の観点から自律的なことができるようにします。 (SOA) のような複数のサービスで構成される従来のアプリケーションがある場合でも必要があります複数のコンテナーまたは分散システムとして展開する必要がある 1 つのビジネス アプリケーションを構成するサービス。 このようなシステムは複雑でスケール アウトおよび管理できます。したがって、どうしても必要な orchestrator と拡張性を運用環境で複数のコンテナー アプリケーションがある場合。

図 4-23 複数 microservices (コンテナー) から成るアプリケーションのクラスターへのデプロイを示しています。

![](./media/image23.PNG)

**図 4-23**です。 コンテナーのクラスター

これは、論理的なアプローチのようになります。 アプリケーションで構成される処理の負荷分散、ルーティング、およびこれらを調整する方法は?

Docker ホストを 1 つの標準の Docker エンジンには、1 つのホスト上の 1 つのイメージ インスタンスを管理のニーズより複雑な分散アプリケーションに対して複数のホストに展開されている複数のコンテナーを管理する際に簡単にします。 ほとんどの場合、自動的にスケール アウト コンテナー イメージごとの複数のインスタンスで、コンテナーを開始、停止またはシャット ダウンする必要な場合、およびされる理想的には制御も、ネットワークとデータのようなリソースにアクセスする方法、管理プラットフォームが必要があります。記憶域。

個別のコンテナーまたは非常に単純な構成済みのアプリと microservices で大規模なエンタープライズ アプリケーションへの移行の管理を超えるに、オーケストレーションとプラットフォームをクラスタ リングを有効にする必要があります。

アーキテクチャと開発の観点から、microservices ベースのアプリケーションから成る大規模な企業を構築する場合はすることが重要次のプラットフォームと高度なシナリオをサポートする製品について理解します。

**クラスターと orchestrators**です。 必要がある場合、多くの Docker ホスト間でアプリケーションを拡張するように、大きなマイクロ サービス ベースのアプリケーションで、ときにすることが重要が基になるプラットフォームの複雑さを抽象化され、1 つのクラスターとしてこれらすべてのホストを管理できるようにします。 コンテナーのクラスターと orchestrators が提供するものです。 Orchestrators には、Azure Service Fabric、Kubernetes、Docker Swarm および続き DC/OS があります。 最後の 3 つのオープン ソース orchestrators Azure コンテナー サービスで Azure で利用できます。

**スケジューラ**です。 *スケジュール*も UI を提供するために、クラスター内のコンテナーを起動するには管理者の機能を搭載することを意味します。 クラスター スケジューラは、いくつかの役割: クラスターのリソースを効率的に使用する、ノードまたはホスト間で効率的に負荷を分散コンテナーに、ユーザーによって提供される制約を設定してエラーに対する堅牢な高しつつである可用性。

クラスターとスケジューラの概念は密接に関連、ので、多くの場合、さまざまなベンダーが提供する製品が両方の機能のセットを指定します。 次の一覧は、最も重要なプラットフォームとクラスターとスケジューラのソフトウェア選択肢を示します。 これら orchestrators は一般に、Azure などのパブリック クラウドで提供されます。

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>コンテナーのクラスタ リング、オーケストレーション、およびスケジュール設定ソフトウェア プラットフォーム

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes は、クラスター インフラストラクチャと機能の調整にスケジュール設定のコンテナーの範囲の機能を提供するオープン ソース製品です。 ホストのクラスター間での展開、スケーリング、およびアプリケーションのコンテナーの操作を自動化できます。
>
> Kubernetes は、簡単な管理と検出の論理ユニットにアプリケーションのコンテナーをグループ化するコンテナーを中心としたインフラストラクチャを提供します。
>
> Kubernetes は Linux では、Windows の小さい完成度の高い成熟したです。

Docker 群

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Docker 群では、クラスターし、Docker コンテナーのスケジュールを設定することができます。 群を使用すると、単一の仮想の Docker ホストに Docker ホストのプールを有効にすることができます。 クライアントは、API 要求 Swarm と同様に、ホストを群を簡単に複数のホストにアプリケーションを拡張するを行うことができます。
>
> Docker 群は、Docker、会社から製品です。
>
> Docker v1.12 後で、ネイティブ モードと組み込み Swarm モードを実行することもできます。

続き DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> 続きエンタープライズ DC/OS (Apache Mesos に基づく) は、コンテナーと分散アプリケーションを実行するための運用環境でプラットフォームです。
>
> DC/OS は、抽象化して、クラスターで利用可能なリソースのコレクションとそれらのリソース上に作成されたコンポーネントを利用することによって機能します。 通常、マラソンは DC/OS と統合されて、スケジューラとして使用されます。
>
> DC/OS は、Linux では、Windows の小さい完成度の高い成熟したです。

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)は、アプリケーションを構築するための Microsoft microservices プラットフォームです。 [Orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction)のサービスし、マシンのクラスターを作成します。 Service Fabric は、コンテナー、または標準のプロセスとして、サービスを展開できます。 でもミックス サービス プロセスで同一のアプリケーションおよびクラスター内のコンテナー内のサービスことができます。
>
> Service Fabric は、追加し、省略可能な規範的な[プログラミング モデル Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework)など[ステートフル サービス](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction)と[Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)です。
>
> Service Fabric は、Windows では (Windows では進化年)、少なく完成度の高い Linux で完成度の高いです。 
> Linux と Windows の両方のコンテナーは、2017 年以降 Service Fabric でサポートされます。

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure でコンテナー ベース orchestrators の使用

いくつかのクラウドのベンダーは、Docker コンテナーのサポートと Docker クラスターと Microsoft Azure、Amazon EC2 コンテナー サービス、および Google コンテナー エンジンをなど、オーケストレーションのサポートを提供します。 Microsoft Azure は、次のセクションで説明したように、Docker のクラスターと orchestrator サポートを介して Azure コンテナー サービス (ACS) を提供します。

他の選択肢では、Linux と Windows コンテナーに基づいた Docker もサポートする Microsoft Azure Service Fabric (microservices プラットフォーム) を使用します。 Service Fabric は、Azure またはその他のクラウドでは、上で実行され、また実行し、[オンプレミス](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)です。

## <a name="using-azure-container-service"></a>Azure のコンテナー サービスを使用します。

Docker クラスターでは、複数の Docker ホストをプールし、クラスター内に複数のコンテナーを展開できるように 1 つの仮想 Docker ホストとして公開します。 クラスターでは、スケーラビリティ、ヘルス、およびなどのように、すべての複雑な管理機能を処理します。 図 4-24 は、構成されたアプリケーションは、Docker クラスターが Azure コンテナー サービス (ACS) によってどのようにマップする方法を表します。

ACS は、作成、構成、およびコンテナー化アプリケーションを実行する事前に構成されている仮想マシンのクラスターの管理を簡略化する方法を提供します。 一般的なオープン ソースのスケジュール設定およびオーケストレーションのツールの構成を最適化を使用して、ACS を使用すると、既存のスキルを使用するか、Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する専門知識をコミュニティの発展し続けている本文上の描画.

Azure のコンテナー サービスは、Azure の具体的には一般的な Docker クラスタ リングのオープン ソース ツールとテクノロジの構成を最適化します。 コンテナーと、アプリケーションの構成の両方の移植性を提供する、開いているソリューションが表示されます。 サイズ、ホストの数と、orchestrator ツールを選択して、コンテナー サービスでは、他のすべてを処理します。

![](./media/image28.png)

**図 4-24**です。 Azure コンテナー サービスでのクラスタ リングの選択

ACS は、アプリケーションのコンテナーが完全に移植可能であることを確認するイメージを Docker を活用します。 これらのアプリケーションが数千にも数万件のコンテナーの拡大/縮小することを確認する DC/OS (電源 Apache Mesos を使用して)、Kubernetes (によって作成された Google)、Docker Swarm などのオープン ソース オーケストレーション プラットフォームの選択肢がサポートしています。

Azure コンテナー サービスでは、オーケストレーション層に指定するなど、アプリケーションの移植性を維持しながら、Azure のエンタープライズ レベルの機能の活用することができます。

![](./media/image29.png)

**図 4-25**です。 ACS で orchestrators

図 4-25 で示すように、Azure コンテナー サービス DC/OS、Kubernetes または Docker Swarm を展開するために Azure によって提供されるインフラストラクチャだけでは ACS は、その他の orchestrator を実装していません。 したがって、ACS は、orchestrator そのため、コンテナーの既存のオープン ソース orchestrators を活用して、インフラストラクチャではありません。

使用量の観点からは、Azure コンテナー サービスの目的は、人気のオープン ソース ツールとテクノロジを使用して、コンテナーのホスト環境を提供します。 このため、選択した orchestrator の標準 API エンドポイントを公開します。 これらのエンドポイントを使用すると、相互に通信できるエンドポイントを含め、ソフトウェアを利用できます。 たとえばの場合は、Docker Swarm エンドポイントすることもできます Docker コマンド ライン インターフェイス (CLI) を使用します。 DC/os、DC/OS CLI を使用することもできます。

### <a name="getting-started-with-azure-container-service"></a>Azure コンテナー サービスの概要 

Azure コンテナー サービスの使用を開始するには、Azure Resource Manager テンプレートを使用して、Azure ポータルから、Azure コンテナー サービスのクラスターを展開する、または[CLI](https://docs.microsoft.com/cli/azure/install-azure-cli)です。 使用可能なテンプレートが含まれる[Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm)、 [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes)、および[DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos)です。 クイック スタート テンプレートは、Azure 構成を追加または高度なを含めるように変更できます。 Azure コンテナー サービス クラスターの展開の詳細については、次を参照してください。[クラスターを展開する Azure コンテナー サービス](https://docs.microsoft.com/azure/container-service/container-service-deployment)、Azure web サイトです。

ACS の一部として既定でインストールされているソフトウェアのいずれかの料金はありません。 すべての既定のオプションは、オープン ソース ソフトウェアで実装されます。

ACS は標準 A、D、DS、G、および GS シリーズの Azure 内の Linux 仮想マシンを使用します。 選択すると、多くのコンピューティング インスタンスだけでなく他の記憶域やネットワークなど、使用されるインフラストラクチャの基になるリソースに対してのみ料金が発生します。 ACS 自体の増分の料金はありません。

## <a name="additional-resources"></a>その他の技術情報

-   **Azure コンテナー サービスとソリューションをホストしている Docker コンテナーの概要**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker 群概要**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **モードの概要を swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **続き DC/OS 概要**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes です。** 公式サイトです \。
    [*http://kubernetes.io/*](http://kubernetes.io/)


>[!div class="step-by-step"]
[前](耐障害性の高い-可用性-microservices.md) [次へ] (を使用して、azure のサービス-fabric.md)
