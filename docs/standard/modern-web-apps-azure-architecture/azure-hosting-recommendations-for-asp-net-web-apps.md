---
title: "ASP.NET Core web アプリ用の推奨事項をホストしている azure"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |ASP.NET web アプリ用の推奨事項をホストしている azure"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 868f1b7ce452be9e29b921888f90d128e074ba13
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Core Web アプリ用の推奨事項をホストしている azure

> "基幹業務リーダー everywhere がクラウド (別名 SaaS) からアプリケーションを取得すると共に、IT 部門のバイパスと支払いそれらの雑誌の講読と同じようにします。 左上隅にある未使用ありません装置と、サブスクリプションを取り消すことができます、サービスが必要でなくなったときにします。"  
> _\- Daryl Plummer、Gartner アナリスト_

## <a name="summary"></a>まとめ

これは、アプリケーションのニーズとアーキテクチャ、Windows Azure でサポートできます。 ホスティングのニーズは非常に高度なアプリケーション数十個サービスの構成に静的な web サイトと同じくらい簡単にできます。 ASP.NET Core モノリシックな web アプリケーションおよびサポート サービスでは、推奨されるいくつかのよく知られている構成があります。 次の推奨事項は、ホストされているかどうか完全なアプリケーション、個別のプロセス、またはデータをリソースの種類に従ってグループ化されます。

## <a name="web-applications"></a>Web アプリケーション

Web アプリケーションをホストできます。

-   App Service Web Apps

-   コンテナー

-   Azure Service Fabric

-   仮想マシン (Vm)

、App Service Web Apps はほとんどのシナリオの方法をお勧めします。 マイクロ サービス アーキテクチャでは、コンテナー ベースのアプローチでは、またはサービス ファブリックを検討してください。 アプリケーションを実行しているマシンより詳細に制御を必要がある場合は、Azure の仮想マシンを検討してください。

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps は、web アプリケーションをホストするために最適化された完全に管理されたプラットフォームを提供します。 内容を実行し、アプリをスケールにより Azure インフラストラクチャの処理中に、ビジネス ロジックに集中することが必要である platform-as-a-service(PaaS) することをお勧めします。 App Service Web Apps のいくつか主な機能:

-   DevOps の最適化 (継続的インテグレーションと配信、複数の環境では、A/テスト、スクリプトのサポート、B)

-   グローバルの拡張性と高可用性

-   SaaS プラットフォームと、内部設置型データへの接続

-   セキュリティとコンプライアンス

-   Visual Studio の統合環境

Azure App Service は、ほとんどの web アプリに最適な選択肢です。 展開と管理は、プラットフォームに統合されて、大量のトラフィックの負荷を処理するサイトをすばやくスケールできますおよび組み込みの負荷分散とトラフィック マネージャーは、高可用性を実現します。 Azure App Service に簡単に、オンラインでの移行ツールを使用して既存のサイトのオープン ソース アプリケーションを使用して、Web アプリケーション ギャラリーから、またはフレームワークと任意のツールを使用して新しいサイトを作成を行うことができます。 Web ジョブ機能により、簡単に App Service web アプリを処理するバック グラウンド ジョブを追加します。

### <a name="containers-and-azure-container-service"></a>コンテナーとコンテナーの Azure サービス

Azure のコンテナー サービスが簡単にすると、作成、構成、およびコンテナー化アプリケーションを実行する事前に構成されている仮想マシンのクラスターを管理します。 一般的なオープン ソースのスケジュール設定およびオーケストレーションのツールの構成を最適化を使用します。 これにより、既存のスキルを使用したり、Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する、コミュニティの専門知識の発展し続けている本文に描画することができます。

Azure のコンテナー サービスが簡単にすると、作成、構成、およびコンテナー化アプリケーションを実行する事前に構成されている仮想マシンのクラスターを管理します。 一般的なオープン ソースのスケジュール設定およびオーケストレーションのツールの構成を最適化を使用します。 これにより、既存のスキルを使用したり、Microsoft Azure でコンテナー ベースのアプリケーション展開および管理する、コミュニティの専門知識の発展し続けている本文に描画することができます。

Azure コンテナー サービスの 1 つの目標は、今日はマイクロソフトのお客様の間でよく使用するオープン ソース ツールとテクノロジを使用して、コンテナー ホスト環境を提供します。 この end には、Azure コンテナー サービスは、(DC/OS、Docker Swarm、または Kubernetes)、選択した orchestrator の標準 API エンドポイントを公開します。 これらのエンドポイントを使用すると、それらのエンドポイントと通信できる任意のソフトウェアを利用できます。 たとえばの場合は、Docker Swarm エンドポイントすることもできます Docker コマンド ライン インターフェイス (CLI) を使用します。 DC/OS DCOS CLI を選択できます。 Kubernetes、kubectl を選択できます。 図 11-1 では、コンテナー、クラスターを管理するこれらのエンドポイントを使用する方法を示します。

![](./media/image11-1.png)

**図 11-1。** Docker、Kubernetes、または DC/OS エンドポイントで azure のコンテナー サービスの管理。

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric は、新しいアプリの作成または再マイクロ サービス アーキテクチャを使用する既存のアプリを記述する場合、適切な選択です。 マシンの共有プールで実行すると、アプリでは、小さな開始でき、数百または数千の必要に応じてマシンでの大規模なスケールに拡大することができます。 ステートフルなサービスしやすい一貫したと確実には、アプリの状態を格納し、Service Fabric はサービスがパーティション分割、スケール、および可用性を自動的に管理するとします。 Service Fabric には、.NET (OWIN) および ASP.NET Core の Open Web Interface と WebAPI もサポートしています。 App Service と比較して、Service Fabric も提供以上の制御、または基になるインフラストラクチャに直接アクセスします。 リモート サーバーにしたり、サーバーのスタートアップ タスクを構成できます。

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

App Service または Service Fabric で実行するの大幅な変更が必要となる既存のアプリケーションがあれば、クラウドへの移行を簡素化するために仮想マシンを選択できます。 ただし、正しく構成、セキュリティ、および保守 Vm が必要です、さまざまな時間と Azure App Service と Service Fabric と比較して IT の専門知識。 Azure の仮想マシンを検討している場合は、考慮する修正プログラム、更新、および VM 環境の管理に必要な継続的なメンテナンス作業を確認します。 Azure の仮想マシンは、App Service と Service Fabric プラットフォーム-as a Service (Paas) されているときにインフラストラクチャ-as a Service (IaaS) がします。

#### <a name="feature-comparison"></a>機能の比較

| App Service を機能します。 | Service Fabric | 仮想マシン |
|---------|----------|----------|
| ほぼ即時の配置 | x | x | |
| 再配置することがなく大型のコンピューターにスケール アップ | x | x | |
| インスタンスを共有コンテンツと構成です。再展開または拡張するときに再構成する必要はありません。 | x | x | |
| 複数のデプロイ環境 (運用環境、ステージング) | x | x | |
| OS の自動更新の管理 | x | | |
| シームレスな 32/64 ビットのプラットフォーム間の切り替え | x | | |
| Git、FTP によるコードを配置します。 | x | | x |
| Web Deploy によるコードを配置します。 | x | | x |
| TFS によるコードを配置します。 | x | X | x |
| ホスト web または多層アーキテクチャの web サービス層 | x | X | x |
| Service Bus、Storage、SQL データベースのような Azure サービスへのアクセスします。 | x | X | x |
| 任意のカスタム MSI をインストールします。 | | x | x |

## <a name="logical-processes"></a>論理プロセス

個々 の論理プロセスで、アプリケーションの残りの部分から切り離すことができます展開することがない個別に Azure 関数「なし」のようにします。 Azure 機能では、特定の問題について、それを実行するアプリケーションまたはインフラストラクチャを気にせず、必要なコードを書き込むだけことができます。 さまざまな C などのプログラミング言語から選択できる\#、F\#Node.js、Python、PHP、当面タスクの生産性のほとんどの言語を選択することができます。 ほとんどのクラウド ベースのソリューションと同様に、使用時間分だけ支払うおよび必要に応じてスケール アップする Azure 機能を信頼することができます。

## <a name="data"></a>データ

Azure は、アプリケーションは、該当するデータの適切なデータ プロバイダーを使用できるように、さまざまなデータ記憶域オプションを提供します。

トランザクション、リレーショナル データの場合は、Azure SQL データベースは、最適なオプションです。 高パフォーマンス通常は読み取り専用データ、Azure SQL データベースでバックアップ Redis cache は良いソリューションです。

さまざまな DocumentDB に Blob または Azure ストレージ内のテーブルに列を SQL データベースからの方法では、JSON の非構造化データを格納できます。 これらのうち、DocumentDB 最適なクエリ機能を提供しています、大量のクエリをサポートする必要がある JSON ベースのドキュメントに推奨されるオプション。

アプリケーションの動作を調整するために使用される一時的なコマンドまたはイベント ベースのデータには、Azure Service Bus または Azure ストレージ キューを使用できます。 Azure の記憶域バスも高い柔軟性し、内およびアプリケーション間では、重要なメッセージングのための推奨されるサービスです。

## <a name="architecture-recommendations"></a>アーキテクチャの推奨事項

アプリケーションの要件が、アーキテクチャを指定する必要があります。 多くのさまざまな Azure サービスが利用可能な重要な判断を右側の 1 つを選択します。 Microsoft では、一般的なシナリオ用に最適化された一般的なアーキテクチャを識別できるように参照アーキテクチャのギャラリーを提供します。 マップ、アプリケーションの要件に最も近いまたは少なくとも開始点が用意されている参照アーキテクチャをバインドすることがあります。

図 11-2 では、参照アーキテクチャの例を示します。 この図では、marketing 用に最適化された Sitecore コンテンツ管理システム web サイトの推奨アーキテクチャ アプローチについて説明します。

![](./media/image11-2.png)

**図 11-2 です。** Web サイトの参照アーキテクチャのマーケティング Sitecore です。

**– Azure の推奨事項をホスティングの参照**

-   Azure ソリューション Architectures\
    <https://azure.microsoft.com/solutions/architecture/>

-   Azure 開発者 Guide\
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   Azure App Service は何ですか? \
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Azure App Service、仮想マシン、Service Fabric およびクラウド サービスの比較 \
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[前](開発のプロセス-の-azure.md)
