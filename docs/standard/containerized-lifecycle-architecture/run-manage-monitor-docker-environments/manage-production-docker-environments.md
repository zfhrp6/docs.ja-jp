---
title: Docker の本番環境を管理します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 169ffa7ba61fa5dff09229410adb534f8e34a35c
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104586"
---
# <a name="manage-production-docker-environments"></a>Docker の本番環境を管理します。

クラスターの管理およびオーケストレーションは、ホストのグループを制御するプロセスです。 これには、追加および削除のホスト クラスターでは、ホストとコンテナーの現在の状態に関する情報を取得し、開始およびプロセスの停止を実行できます。 クラスターの管理およびオーケストレーションはスケジュールのため、スケジューラは、クラスター内の各ホストへのアクセスをサービスをスケジュールするためがある必要に密接に結び付けられます。 このためは、同じツールは多くの場合に両方の目的に使用されます。

## <a name="container-service-and-management-tools"></a>コンテナー サービスと管理ツール

コンテナー サービスは、人気のオープン ソース コンテナーのクラスタ リング ボリュームとオーケストレーションのソリューションの迅速なデプロイを提供します。 Docker イメージを使用して、アプリケーションのコンテナーが完全に移植可能であることを確認します。 コンテナー サービスを使用すると、DC/OS (続きして Apache Mesos 電源) を展開することができ、Azure リソース マネージャーのテンプレートまたは数千ものにこれらのアプリケーションの規模を設定できることを確認してください Azure ポータルを使用するクラスタ Docker Swarm — 万も — の。コンテナーです。

Azure 仮想マシン スケール セットを使用してこれらのクラスターを展開して、Azure のネットワークおよび記憶域サービスのクラスターを利用します。 コンテナー サービスにアクセスするには、Azure サブスクリプションが必要です。 コンテナー サービスでは、オーケストレーション層に指定するなど、アプリケーションの移植性を維持しながら Azure のエンタープライズ レベルの機能を活用がかかります。

表 6-1 は、その orchestrators、スケジューラ、およびクラスタ リングのプラットフォームに関連する一般的な管理ツールを一覧表示します。

表 6-1: Docker の管理ツール


| 管理ツール      | 説明           | 関連する orchestrators |
|-----------------------|-----------------------|-----------------------|
| コンテナー サービス\(Azure ポータルで UI 管理) | [コンテナー サービス](https://azure.microsoft.com/en-us/services/container-service/)簡単に提供する方法を開始[Azure でコンテナー クラスターを展開](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment)続き DC/OS、Kubernetes Docker Swarm などの一般的な orchestrators に基づいて。 <br /><br /> コンテナー サービスは、これらのプラットフォームの構成を最適化します。 だけ、サイズ、ホストの数と、orchestrator ツールの選択肢を選択する必要があり、コンテナー サービスでは、他のすべてを処理します。 | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Docker ユニバーサル制御プレーン\(オンプレミスまたはクラウド) | [Docker ユニバーサル制御プレーン](https://docs.docker.com/v1.11/ucp/overview/)Docker からエンタープライズ レベルのクラスター管理ソリューションです。 1 つの場所から、クラスター全体を管理するときに役立ちます。 <br /><br /> Docker ユニバーサル コントロール平面は商用製品 Docker Swarm、制御プレーンのユニバーサル Docker と Docker Trusted Registry を提供する Docker データ センターをという名前の一部として含めるです。 <br /><br /> Docker のデータ センターでは、インストールされている内部設置型を指定できます。 または Azure などのパブリック クラウドをプロビジョニングします。 | Docker Swarm\(コンテナー サービスでサポートされている) |
| Docker のクラウド\(Tutum; クラウド SaaS とも呼ばれます) | [Docker のクラウド](https://docs.docker.com/docker-cloud/)ビルドとテストの施設 Dockerized アプリケーション イメージは、設定し、ホスト インフラストラクチャを管理するのに役立つツールとオーケストレーションの機能と Docker のレジストリを提供するホストされている管理サービス (SaaS) は、イメージ、具体的なインフラストラクチャを展開するを自動化するのに役立つ機能を展開します。 SaaS Docker のクラウド アカウントは、Docker Swarm クラスターを実行しているコンテナー サービスでお客様のインフラストラクチャに接続できます。 | Docker Swarm\(コンテナー サービスでサポートされている) |
| 続きマラソン\(オンプレミスまたはクラウド) | [マラソン](https://mesosphere.github.io/marathon/docs/marathon-ui.html)続きの DC/OS と Apache Mesos は実稼働レベルのコンテナーのオーケストレーションとスケジューラのプラットフォームです。 <br /><br /> Mesos と連携して (DC/OS は Apache Mesos に基づく) 実行時間の長いのコントロールにサービスを示し、[プロセスとコンテナーの管理用 web UI](https://mesosphere.github.io/marathon/docs/marathon-ui.html)です。 Web UI の管理ツールを提供します。 | 続き DC/OS\(Apache に基づいて Mesos; コンテナー サービスでサポートされている) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access)の調整、スケジュール、およびクラスター インフラストラクチャにまたがるです。 これは、コンテナー指向のインフラストラクチャを提供するホストのクラスター間での展開、スケーリング、およびアプリケーションのコンテナーの操作を自動化するためのオープン ソース プラットフォームです。 | Google Kubernetes\(コンテナー サービスでサポートされている) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

クラスター展開および管理用の別の選択肢は、Azure Service Fabric です。 [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/)開発者と同様にコンテナーのオーケストレーションを含む Microsoft microservices プラットフォームは、拡張性が高く microservices アプリケーションを構築するモデルをプログラミングします。 Service Fabric では、現在のバージョンの Linux プレビューでは、Docker をサポートように、 [Linux 上の Service Fabric プレビュー](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)、および Windows コンテナーの[次のリリースで](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)です。

サービス ファブリック管理ツールを次に示します。

-   [Azure ポータルの Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)クラスターに関連する操作 (作成/更新/削除)、クラスターまたは (Vm、ロード バランサー機器、ネットワークなど) のインフラストラクチャを構成します。

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) insights とノード/Vm の観点から、アプリケーションとサービスの観点からは、Service Fabric クラスター上の特定の操作を提供する特殊な web UI ツールです。


>[!div class="step-by-step"]
[前へ](run-microservices-based-applications-in-production.md)
[次へ](monitor-containerized-application-services.md)
