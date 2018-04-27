---
title: リレーショナル データベースを azure に移行します。
description: Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |リレーショナル データベースを azure に移行します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aa23d525c80d02ae19783a32f197a412276db36e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="59a2d-103">リレーショナル データベースを azure に移行します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-103">Migrate your relational databases to azure</span></span>

<span data-ttu-id="59a2d-104">ビジョン: Azure では、最も包括的なデータベースの移行を提供します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="59a2d-105">Azure では、(純粋なリフト アンド シフト) の IaaS Vm に直接、データベース サーバーを移行することもその他の利点の Azure SQL Database に移行することができます。</span><span class="sxs-lookup"><span data-stu-id="59a2d-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="59a2d-106">Azure SQL データベースでは、マネージ インスタンスおよび完全データベース-as a service (DBaaS) オプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-106">Azure SQL Database offers managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="59a2d-107">図 3-1 は、Azure で利用可能な移行パスが、複数のリレーショナル データベースを示しています。</span><span class="sxs-lookup"><span data-stu-id="59a2d-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![Azure でのデータベースの移行パス](./media/image3-1.png)

> <span data-ttu-id="59a2d-109">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="59a2d-109">**Figure 3-1.**</span></span> <span data-ttu-id="59a2d-110">Azure でのデータベースの移行パス</span><span class="sxs-lookup"><span data-stu-id="59a2d-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="59a2d-111">Azure SQL データベースのマネージ インスタンスに移行に適した状況</span><span class="sxs-lookup"><span data-stu-id="59a2d-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="59a2d-112">ほとんどの場合は、Azure SQL データベースのマネージ インスタンスを Azure にデータを移行する際に考慮する最善の対処方法となります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="59a2d-113">SQL Server データベースを移行して、ほぼ 100% ことを保証するデータまたはデータ アクセス コードをアプリケーションを再構築または変更する必要はありません必要があるの場合は、Azure SQL Database のマネージ インスタンスの機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to re-architect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="59a2d-114">Azure SQL データベースのマネージ インスタンスは、SQL Server インスタンス レベルの機能の追加要件または標準の Azure SQL データベース (1 つのデータベース モデル) で提供される機能以外の分離の要件がある場合に最適なオプションです。</span><span class="sxs-lookup"><span data-stu-id="59a2d-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="59a2d-115">この最後の 1 つは、最も PaaS 指向の選択は、従来の SQL server のと同じ機能を提供していません。</span><span class="sxs-lookup"><span data-stu-id="59a2d-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="59a2d-116">移行では、frictions を表面化可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-116">Migration might surface frictions.</span></span>

<span data-ttu-id="59a2d-117">たとえば、インスタンス レベルの SQL Server 機能の詳細な投資を行ってきましたする組織は恩恵をマネージ インスタンスの SQL への移行します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="59a2d-118">例としてインスタンス レベルの SQL Server 機能の SQL 共通言語ランタイム (CLR) 統合、SQL Server エージェントやデータベースにまたがるクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="59a2d-119">これらの機能のサポートは、標準の Azure SQL データベース (単一データベース モデル) でご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="59a2d-119">Support for these features are not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="59a2d-120">厳しくの業界で動作して、セキュリティのための分離を維持する必要がある組織もメリットがあるマネージ インスタンスの SQL モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="59a2d-121">Azure SQL データベースでのマネージ インスタンスには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="59a2d-122">Azure の仮想ネットワーク経由のセキュリティの分離</span><span class="sxs-lookup"><span data-stu-id="59a2d-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="59a2d-123">画面とアプリケーションの互換性、これらの機能:</span><span class="sxs-lookup"><span data-stu-id="59a2d-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="59a2d-124">SQL Server エージェントおよび SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="59a2d-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="59a2d-125">データベースにまたがる参照およびクエリ、SQL CLR のレプリケーション、変更データ キャプチャ (CDC)、および Service Broker</span><span class="sxs-lookup"><span data-stu-id="59a2d-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="59a2d-126">データベースのサイズを最大 35 TB</span><span class="sxs-lookup"><span data-stu-id="59a2d-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="59a2d-127">最小のダウンタイムでの移行、これらの機能:</span><span class="sxs-lookup"><span data-stu-id="59a2d-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="59a2d-128">Azure のデータベース移行サービス</span><span class="sxs-lookup"><span data-stu-id="59a2d-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="59a2d-129">ネイティブのバックアップと復元、およびログ配布</span><span class="sxs-lookup"><span data-stu-id="59a2d-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="59a2d-130">これらの機能により、Azure SQL データベースに既存のアプリケーション データベースを移行するときに、マネージ インスタンスのモデルでは、Paas の利点のほぼ 100% for SQL Server。</span><span class="sxs-lookup"><span data-stu-id="59a2d-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of Paas for SQL Server.</span></span> <span data-ttu-id="59a2d-131">マネージ インスタンスは、インスタンス レベルの機能を使用して、アプリケーションの設計を変更することがなく引き続き SQL Server 環境です。</span><span class="sxs-lookup"><span data-stu-id="59a2d-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="59a2d-132">マネージ インスタンスが現在使用している SQL Server とクラウド内のネットワーク セキュリティの柔軟性を必要とする企業に最適では可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="59a2d-133">SQL データベース用のプライベート仮想ネットワークを持つようになります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="59a2d-134">Azure SQL Database への移行に適した状況</span><span class="sxs-lookup"><span data-stu-id="59a2d-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="59a2d-135">前述のように、標準の Azure SQL Database は、完全に管理されたリレーショナル DBaaS がします。</span><span class="sxs-lookup"><span data-stu-id="59a2d-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="59a2d-136">現在、SQL データベースは、世界中の 38 データ センター間で何百万もの実稼働データベースを管理します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="59a2d-137">これは、さまざまなアプリケーションや世界規模での高度なデータ処理を必要とするデータが集中する、ミッション クリティカルなアプリケーションにするために、簡単なトランザクション データの管理からのワークロードをサポートします。</span><span class="sxs-lookup"><span data-stu-id="59a2d-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="59a2d-138">その完全 PaaS 機能によるものであり、効率的料金の最終的なコストの削減と -に移行する標準の Azure SQL Database、「既定の選択肢」としてそのは basic、standard SQL データベース、および追加のインスタンスの機能がないアプリケーションがある場合。</span><span class="sxs-lookup"><span data-stu-id="59a2d-138">Because of its full PaaS features and better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="59a2d-139">SQL CLR 統合、SQL Server エージェント、およびデータベースにまたがるクエリを実行するように SQL Server の機能は標準の Azure SQL データベースではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="59a2d-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="59a2d-140">これらの機能が、Azure SQL データベースのマネージ インスタンス モデルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="59a2d-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="59a2d-141">Azure SQL データベースは、アプリの開発者に組み込まれているのみインテリジェント クラウド データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="59a2d-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="59a2d-142">場で、マルチ テナント アプリケーションを効率的に配信するため、ダウンタイムなしのスケールを設定するだけのクラウド データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="59a2d-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="59a2d-143">最終的には、Azure SQL データベース状態のままに導入するより多くの時間とに要する時間、高速化します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="59a2d-144">セキュリティで保護されたアプリケーションをビルドし、言語と使用するプラットフォームを使用して、SQL データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="59a2d-144">You can build secure apps, and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="59a2d-145">Azure SQL Database には次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="59a2d-146">組み込みのインテリジェンス (機械学習) を学習して、アプリへの対応</span><span class="sxs-lookup"><span data-stu-id="59a2d-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="59a2d-147">オンデマンドのデータベースの準備</span><span class="sxs-lookup"><span data-stu-id="59a2d-147">On-demand database provisioning</span></span>

- <span data-ttu-id="59a2d-148">すべてのワークロード向けの情報の範囲</span><span class="sxs-lookup"><span data-stu-id="59a2d-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="59a2d-149">可用性 99.99% の SLA、ゼロのメンテナンス</span><span class="sxs-lookup"><span data-stu-id="59a2d-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="59a2d-150">データ保護のために Geo レプリケーションと復元のサービス</span><span class="sxs-lookup"><span data-stu-id="59a2d-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="59a2d-151">Azure SQL データベース特定時点に復元機能</span><span class="sxs-lookup"><span data-stu-id="59a2d-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="59a2d-152">ハイブリッドおよび移行を含む、SQL Server 2016 との互換性</span><span class="sxs-lookup"><span data-stu-id="59a2d-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="59a2d-153">標準の Azure SQL データベースでは、Azure SQL データベースのマネージ インスタンスよりは、PaaS に近づきます。</span><span class="sxs-lookup"><span data-stu-id="59a2d-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="59a2d-154">マネージ クラウドから複数のメリットになるため、使用可能な場合に試してください。</span><span class="sxs-lookup"><span data-stu-id="59a2d-154">You should try to use it, if possible, because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="59a2d-155">しかし、Azure SQL データベースは正規の主な相違点あり、内部設置型 SQL Server インスタンス。</span><span class="sxs-lookup"><span data-stu-id="59a2d-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="59a2d-156">、、、既存のアプリケーションのデータベースの要件、および企業の要件とポリシーに応じて、できない可能性があります最善の選択、クラウドへの移行を計画するときにします。</span><span class="sxs-lookup"><span data-stu-id="59a2d-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="59a2d-157">場合に、元の RDBMS を VM (IaaS) に移動するには</span><span class="sxs-lookup"><span data-stu-id="59a2d-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="59a2d-158">移行オプションの 1 つは、元のリレーショナル データベース管理システム (RDBMS)、Oracle、IBM DB2、MySQL、PostgreSQL、または SQL Server を含む Azure VM で実行されているようなサーバーを移動します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="59a2d-159">最小限の変更、またはまったく変更せずにクラウドへの移行を最も高速をまったく必要とする既存のアプリケーションがある場合は、IaaS クラウドへの移行を直接が正当なオプションにあります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="59a2d-160">クラウドのすべての利点を活用する最善の方法ができない可能性がありますが、最も高速な初期パスである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="59a2d-161">現在、Microsoft Azure サポートされている最大[331 の別のデータベース サーバー](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) IaaS Vm としてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="59a2d-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="59a2d-162">SQL Server、Oracle、MySQL、PostgreSQL、および IBM DB2 の場合のような一般的な Rdbms および Cloudera したり MariaDB、DataStax、MongoDB、Cassandra などその他の多くの NoSQL データベースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a2d-162">These include popular RDBMSes like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="59a2d-163">移動するは、Azure VM に、RDBMS 可能性があります (であるため IaaS) クラウドにデータを移行する最も簡単な方法は、この方法には、IT チーム (データベース管理者および IT 担当者向け) で多大な投資が必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="59a2d-164">企業内のチームを設定して高可用性、災害復旧、および SQL Server の修正プログラムの適用を管理できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="59a2d-165">このコンテキストでは、カスタマイズされた環境に、完全な管理者権限も必要です。</span><span class="sxs-lookup"><span data-stu-id="59a2d-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="59a2d-166">仮想マシン (IaaS) として SQL Server に移行に適した状況</span><span class="sxs-lookup"><span data-stu-id="59a2d-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="59a2d-167">まだ必要がある通常の仮想マシンとしての SQL Server に移行するいくつかの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="59a2d-168">シナリオの例は、SQL Server Reporting Services を使用する必要があるかどうかです。</span><span class="sxs-lookup"><span data-stu-id="59a2d-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="59a2d-169">ほとんどの場合は、Azure SQL データベースのマネージ インスタンス提供できますすべての SQL Server VM への移行は、最後の手段を試すには、内部設置型 SQL サーバーから移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="59a2d-170">Azure データベースの移行サービスを使用して、リレーショナル データベースを Azure に移行するには</span><span class="sxs-lookup"><span data-stu-id="59a2d-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span> 

<span data-ttu-id="59a2d-171">SQL Server、Oracle、MySQL などのリレーショナル データベースを Azure に移行するのに Azure データベースの移行サービスを使用するには、ターゲット データベースが Azure SQL Database、Azure SQL データベース管理されているインスタンス、または Azure VM 上の SQL Server であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="59a2d-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="59a2d-172">評価がレポートで、自動化されたワークフローでは、データベースを移行する前にする必要がある変更を説明します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="59a2d-173">準備ができたら、サービスは、ソース データベースを Azure に移行します。</span><span class="sxs-lookup"><span data-stu-id="59a2d-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="59a2d-174">元の RDBMS を変更するたびに再テストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="59a2d-175">また、SQL 文またはテストの結果に応じて、アプリケーション内のオブジェクト リレーショナル マッピング (ORM) コードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59a2d-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="59a2d-176">他のデータベース (たとえば、IBM DB2) がある場合、リフト アンド シフトのアプローチを選択する場合は、ことができますを引き続き Azure では、IaaS Vm としてそれらのデータベースを使用するより複雑なデータ移行を実行する意思がない場合。</span><span class="sxs-lookup"><span data-stu-id="59a2d-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="59a2d-177">複雑なデータの移行は、新しいスキーマと異なるプログラミング ライブラリを持つ別のデータベース型に移行するため、追加の作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="59a2d-177">A more complex data migration will require additional effort, because you'd be migrating to a different database type with new schema and different programming libraries.</span></span>

<span data-ttu-id="59a2d-178">Azure データベースの移行サービスを使用してデータベースを移行する方法については、次を参照してください。[クラウドの Azure SQL データベースのマネージ インスタンスと Azure データベースの移行サービスでより迅速に取得](https://channel9.msdn.com/Events/Build/2017/P4008)です。</span><span class="sxs-lookup"><span data-stu-id="59a2d-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59a2d-179">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="59a2d-179">Additional resources</span></span>

- <span data-ttu-id="59a2d-180">**クラウド SQL Server のオプションを選択します Azure SQL データベース (PaaS) または Azure の仮想マシン (IaaS) 上の SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="59a2d-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- <span data-ttu-id="59a2d-181">**クラウドの Azure SQL DB マネージ インスタンスおよびデータベースの移行サービスでより迅速に取得します。**</span><span class="sxs-lookup"><span data-stu-id="59a2d-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- <span data-ttu-id="59a2d-182">**クラウド内の SQL データベースに SQL Server データベースの移行**</span><span class="sxs-lookup"><span data-stu-id="59a2d-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- <span data-ttu-id="59a2d-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="59a2d-183">**Azure SQL Database**</span></span>

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- <span data-ttu-id="59a2d-184">**仮想マシン上の SQL Server**</span><span class="sxs-lookup"><span data-stu-id="59a2d-184">**SQL Server on virtual machines**</span></span>

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
<span data-ttu-id="59a2d-185">[前へ](lift-and-shift-existing-apps-azure-iaas.md)
[次へ](lift-and-shift-existing-apps-devops/index.md)</span><span class="sxs-lookup"><span data-stu-id="59a2d-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](lift-and-shift-existing-apps-devops/index.md)</span></span>