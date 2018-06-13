---
title: リレーショナル データベースを azure に移行します。
description: Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |リレーショナル データベースを azure に移行します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: fe1bf5820c2306beb380749b34d5a56964e016e4
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956086"
---
# <a name="migrate-your-relational-databases-to-azure"></a>リレーショナル データベースを azure に移行します。

ビジョン: Azure では、最も包括的なデータベースの移行を提供します。

Azure では、(純粋なリフト アンド シフト) の IaaS Vm に直接、データベース サーバーを移行することもその他の利点の Azure SQL Database に移行することができます。 Azure SQL データベースでは、マネージ インスタンスおよび完全データベース-as a service (DBaaS) オプションを提供します。 図 3-1 は、Azure で利用可能な移行パスが、複数のリレーショナル データベースを示しています。

![Azure でのデータベースの移行パス](./media/image3-1.png)

> **図 3-1.** Azure でのデータベースの移行パス

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL データベースのマネージ インスタンスに移行に適した状況

ほとんどの場合は、Azure SQL データベースのマネージ インスタンスを Azure にデータを移行する際に考慮する最善の対処方法となります。 SQL Server データベースを移行して、ほぼ 100% ことを保証するデータまたはデータ アクセス コードをアプリケーションを再構築または変更する必要はありません必要があるの場合は、Azure SQL Database のマネージ インスタンスの機能を選択します。

Azure SQL データベースのマネージ インスタンスは、SQL Server インスタンス レベルの機能の追加要件または標準の Azure SQL データベース (1 つのデータベース モデル) で提供される機能以外の分離の要件がある場合に最適なオプションです。 この最後の 1 つは、最も PaaS 指向の選択は、従来の SQL server のと同じ機能を提供していません。 移行では、frictions を表面化可能性があります。

たとえば、インスタンス レベルの SQL Server 機能の詳細な投資を行ってきましたする組織は恩恵をマネージ インスタンスの SQL への移行します。 例としてインスタンス レベルの SQL Server 機能の SQL 共通言語ランタイム (CLR) 統合、SQL Server エージェントやデータベースにまたがるクエリを実行します。 これらの機能のサポートでは、標準の Azure SQL データベース (単一データベース モデル) で使用できません。

厳しくの業界で動作して、セキュリティのための分離を維持する必要がある組織もメリットがあるマネージ インスタンスの SQL モデルを選択します。

Azure SQL データベースでのマネージ インスタンスには、次の特徴があります。

- Azure の仮想ネットワーク経由のセキュリティの分離

- 画面とアプリケーションの互換性、これらの機能:

  - SQL Server エージェントおよび SQL Server Profiler

  - データベースにまたがる参照およびクエリ、SQL CLR のレプリケーション、変更データ キャプチャ (CDC)、および Service Broker

- データベースのサイズを最大 35 TB

- 最小のダウンタイムでの移行、これらの機能:

  - Azure のデータベース移行サービス

  - ネイティブのバックアップと復元、およびログ配布

これらの機能により、Azure SQL データベースに既存のアプリケーション データベースを移行するときに、マネージ インスタンスのモデルでは、Paas の利点のほぼ 100% for SQL Server。 マネージ インスタンスは、インスタンス レベルの機能を使用して、アプリケーションの設計を変更することがなく引き続き SQL Server 環境です。

マネージ インスタンスが現在使用している SQL Server とクラウド内のネットワーク セキュリティの柔軟性を必要とする企業に最適では可能性があります。 SQL データベース用のプライベート仮想ネットワークを持つようになります。

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL Database への移行に適した状況

前述のように、標準の Azure SQL Database は、完全に管理されたリレーショナル DBaaS がします。 現在、SQL データベースは、世界中の 38 データ センター間で何百万もの実稼働データベースを管理します。 これは、さまざまなアプリケーションや世界規模での高度なデータ処理を必要とするデータが集中する、ミッション クリティカルなアプリケーションにするために、簡単なトランザクション データの管理からのワークロードをサポートします。

その完全 PaaS 機能のための価格よりの最終的なコストの削減と -に移行する標準の Azure SQL Database、「既定の選択肢」としてそのは basic、standard SQL データベース、および追加のインスタンスの機能がないアプリケーションがある場合。 SQL CLR 統合、SQL Server エージェント、およびデータベースにまたがるクエリを実行するように SQL Server の機能は標準の Azure SQL データベースではサポートされていません。 これらの機能が、Azure SQL データベースのマネージ インスタンス モデルでのみ使用できます。

Azure SQL データベースは、アプリの開発者に組み込まれているのみインテリジェント クラウド データベース サービスです。 場で、マルチ テナント アプリケーションを効率的に配信するため、ダウンタイムなしのスケールを設定するだけのクラウド データベース サービスです。 最終的には、Azure SQL データベース状態のままに導入するより多くの時間とに要する時間、高速化します。 セキュリティで保護されたアプリをビルドし、言語と使用するプラットフォームを使用して、SQL データベースに接続できます。

Azure SQL Database には次の利点があります。

- 組み込みのインテリジェンス (機械学習) を学習して、アプリへの対応

- オンデマンドのデータベースの準備

- すべてのワークロード向けの情報の範囲

- 可用性 99.99% の SLA、ゼロのメンテナンス

- データ保護のために Geo レプリケーションと復元のサービス

- Azure SQL データベース特定時点に復元機能

- ハイブリッドおよび移行を含む、SQL Server 2016 との互換性

標準の Azure SQL データベースでは、Azure SQL データベースのマネージ インスタンスよりは、PaaS に近づきます。 管理対象のクラウドから多くのメリットになるために、標準の Azure SQL データベースを選びます。 しかし、Azure SQL データベースは正規の主な相違点あり、内部設置型 SQL Server インスタンス。 、、、既存のアプリケーションのデータベースの要件、および企業の要件とポリシーに応じて、できない可能性があります最善の選択、クラウドへの移行を計画するときにします。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>場合に、元の RDBMS を VM (IaaS) に移動するには

移行オプションの 1 つは、元のリレーショナル データベース管理システム (RDBMS)、Oracle、IBM DB2、MySQL、PostgreSQL、または SQL Server を含む Azure VM で実行されているようなサーバーを移動します。 最小限の変更、またはまったく変更せずにクラウドへの移行を最も高速をまったく必要とする既存のアプリケーションがある場合は、IaaS クラウドへの移行を直接が正当なオプションにあります。 クラウドのすべての利点を活用する最善の方法ができない可能性がありますが、最も高速な初期パスである可能性があります。

現在、Microsoft Azure サポートされている最大[331 の別のデータベース サーバー](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) IaaS Vm としてデプロイします。 これらには、SQL Server、Oracle、MySQL、PostgreSQL、および IBM DB2 の場合のような一般的な RDBMS および Cloudera したり MariaDB、DataStax、MongoDB、Cassandra などその他の多くの NoSQL データベースが含まれます。

> [!NOTE]
> 移動するは、Azure VM に、RDBMS 可能性があります (であるため IaaS) クラウドにデータを移行する最も簡単な方法は、この方法には、IT チーム (データベース管理者および IT 担当者向け) で多大な投資が必要があります。 企業内のチームを設定して高可用性、災害復旧、および SQL Server の修正プログラムの適用を管理できるようにする必要があります。 このコンテキストでは、カスタマイズされた環境に、完全な管理者権限も必要です。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>仮想マシン (IaaS) として SQL Server に移行に適した状況

まだ必要がある通常の仮想マシンとしての SQL Server に移行するいくつかの場合もあります。 シナリオの例は、SQL Server Reporting Services を使用する必要があるかどうかです。 ほとんどの場合は、Azure SQL データベースのマネージ インスタンス提供できますすべての SQL Server VM への移行は、最後の手段を試すには、内部設置型 SQL サーバーから移行する必要があります。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure データベースの移行サービスを使用して、リレーショナル データベースを Azure に移行するには 

SQL Server、Oracle、MySQL などのリレーショナル データベースを Azure に移行するのに Azure データベースの移行サービスを使用するには、ターゲット データベースが Azure SQL Database、Azure SQL データベース管理されているインスタンス、または Azure VM 上の SQL Server であるかどうか。

評価がレポートで、自動化されたワークフローでは、データベースを移行する前にする必要がある変更を説明します。 準備ができたら、サービスは、ソース データベースを Azure に移行します。

元の RDBMS を変更するたびに再テストする必要があります。 また、SQL 文またはテストの結果に応じて、アプリケーション内のオブジェクト リレーショナル マッピング (ORM) コードを変更する必要があります。

他のデータベース (たとえば、IBM DB2) がある場合、リフト アンド シフトのアプローチを選択する場合は、ことができますを引き続き Azure では、IaaS Vm としてそれらのデータベースを使用するより複雑なデータ移行を実行する意思がない場合。 複雑なデータの移行は、新しいスキーマと異なるプログラミング ライブラリを持つ別のデータベース型に移行するため、追加の作業が必要です。

Azure データベースの移行サービスを使用してデータベースを移行する方法については、次を参照してください。[クラウドの Azure SQL データベースのマネージ インスタンスと Azure データベースの移行サービスでより迅速に取得](https://channel9.msdn.com/Events/Build/2017/P4008)です。

## <a name="additional-resources"></a>その他の技術情報

- **クラウド SQL Server のオプションを選択します Azure SQL データベース (PaaS) または Azure の仮想マシン (IaaS) 上の SQL Server。**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **クラウドの Azure SQL DB マネージ インスタンスおよびデータベースの移行サービスでより迅速に取得します。**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **クラウド内の SQL データベースに SQL Server データベースの移行**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **仮想マシン上の SQL Server**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[前へ](lift-and-shift-existing-apps-azure-iaas.md)
[次へ](modernize-existing-apps-to-cloud-optimized/index.md)