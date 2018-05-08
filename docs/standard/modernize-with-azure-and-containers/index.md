---
title: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する
description: リフト アンド シフト既存のアプリケーションを Azure クラウドおよび電子書籍とコンテナーを説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 3109cac1bd64587bb096a057f6f4ae99b055352a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>Azure クラウドおよび Windows コンテナー (v1.0) で既存の .NET アプリケーションを最新化する

![カバーの画像](./media/cover.png)

発行者  
マイクロソフト プレスと Microsoft DevDiv  
Divisions of Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2017 by Microsoft Corporation  

All rights reserved. 本書のいかなる部分も、書面による発行者の許可なしに、いかなる形式または方法によっても、複製することを禁じます。

このブックはなど、電子書籍の (電子書籍) マイクロソフトの複数のチャネルを通じて使用可能な形式で無料で利用できるhttp://dot.net/architectureです。

この書籍で電子メールに関連する質問がある場合は、[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book) に電子メールをお送りください。

本書は "現状有姿" で提供され、著者の見解と意見を表しています。 ビュー、意見、および URL やその他のインターネット web サイトの参照を含め、このドキュメントで表現される情報は、通知なく変更可能性があります。

ここに記載したいくつかの例は、説明のためだけに提供された架空のものです。 実在のものとの関連性または関係性は一切ありません。

Microsoft およびに記載されている商標http://www.microsoft.com「商標」web ページには、Microsoft グループ企業各社の商標です。 その他のすべてのマークは、該当する各社が所有しています。

作成者:
> **Cesar de la Torre**、Microsoft corp.、.NET 製品チーム、シニア PM

参加者とレビュー担当者:
> **Scott Hunter**、Microsoft、.NET チーム、パートナー ディレクター PM  
> **Paul Yuknewicz**、Microsoft、Visual Studio Tools チーム、主任 PM マネージャー  
> **Lisa Guthrie**、シニア Microsoft、Visual Studio Tools チーム、PM  
> **Ankit Asthana**、Microsoft、.NET チーム、主任 PM マネージャー  
> **Unai Zorrilla**、開発者リーダー、Plain Concepts  
> **Javier Valero**、Grupo Solutio の最高執行責任者  

## <a name="introduction"></a>はじめに

Web アプリケーションを最新化し、クラウドに移動すると決定した場合は、アプリを完全に再構築する必要があるとは限りません。 マイクロサービスのような高度なアプローチを使用したアプリケーションの再構築は、コストと時間の制約があるため必ずしも選択肢となりません。 アプリケーションの種類に応じて、アプリの再構築も必要ない場合があります。 組織のクラウドの移行戦略のコストを最適化するには、ビジネスのニーズとアプリの要件を考慮することが重要です。 次のことを決定する必要があります。

- どのアプリの変換と再設計が必要か。

- どのアプリの部分的な再構築のみが必要か。

- どのアプリをクラウドに直接 "リフト アンド シフト" することができるか。

## <a name="about-this-guide"></a>このガイドについて

このガイドでは、"リフト アンド シフト" シナリオと既存の Microsoft .NET Framework Web アプリケーションまたはサービス指向アプリケーションの初期最新化に主に焦点を当てています。 リフト アンド シフトは、アプリケーションのコードや基本的なアーキテクチャを変更せずに、ワークロードを新しい最新化された環境に移行する作業です。

このガイドでは、アプリケーション全体を最構築または再コーディングせずに、特定の領域を最新化することによって、既存の.NET Framework サーバー アプリケーションを直接クラウドに移行する方法について説明します。

このガイドでは、アプリをクラウドに移動し、Windows のコンテナーや Azure のオーケストレーターなどの新しいテクノロジやアプローチの特定のセットを使用してアプリを部分的に最新化する場合のメリットも説明します。

## <a name="path-to-the-cloud-for-existing-net-applications"></a>既存の .NET アプリケーションのクラウドへのパス

組織は、通常のアプリケーションで得ることができる機敏性と速度のために、クラウドへの移行を選択します。 オンプレミス サーバーのセットアップには一般的に数週間かかるのと比べて、クラウドでは数千のサーバー (VM) を数分でセットアップできます。

アプリケーションをクラウドに移行するための 1 つの万能型の戦略はありません。 右側の移行の戦略は、組織のニーズと優先度、および移行するアプリケーションの種類によって異なります。 すべてのアプリケーションがサービスとしてのプラットフォーム ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) モデルへの移行や[クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) アプリケーション モデルの開発の投資を保証するわけではありません。 多くの場合は、ビジネス ニーズに基づいて、資産をクラウドに移行する際に段階的なまたは増分アプローチで投資を実行できます。

最適な長期的機敏性と組織のための価値を持つ最新のアプリケーションの場合、*クラウドに向けて最適化された**クラウド ネイティブ*のアプリケーション アーキテクチャに投資するとメリットが得られることがあります。 ただし、既存のアプリケーションまたは従来の資産にとって重要なのは、クラウドに移行するときにかかる時間とコストを最小限に抑えながら (再設計やコード変更なしで)、大きなメリットを実現することです。

図 1-1 は、既存の .NET アプリケーションを段階的なフェーズでクラウドに移動する場合に実行できる可能性のあるパスを示しています。

 ![既存の .NET アプリケーションとサービスの最新化パス](./media/image1-1.png)

> **(図 1-1)**。 既存の .NET アプリケーションとサービスの最新化パス

各移行アプローチには、さまざまな利点とそれを使用する理由があります。 アプリをクラウドに移行するときには単一のアプローチを選択することも、複数のアプローチから特定のコンポーネントを選択することもできます。 個々 のアプリケーションは、1 つのアプローチまたは成熟度の状態に制限されません。 たとえば、一般的なハイブリッド アプローチには、オンプレミスのコンポーネントに加えてその他のコンポーネントがクラウドにあります。

最初の 2 つの移行レベルで、アプリケーションのリフト アンド シフトのみを実行できます。

**Level 1: クラウド インフラストラクチャの準備完了**: この移行アプローチでは、単純に現在のオンプレミス アプリケーションをサービスとしてのインフラストラクチャ ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) プラットフォームに再ホストまたは移動します。 アプリの構成は前とほとんど変わりませんが、クラウド内の VM に展開します。

**レベル 2: クラウド DevOps 対応**: このレベルでは、初期リフト アンド シフトの後に、ここでも再設計やコードを変更なしで、クラウドでのアプリの実行による多くの利点を得られます。 エンタープライズ開発操作 (DevOps) プロセスが調整され、すばやく出荷するためのアプリケーションの機敏性が向上します。 これを実現するには、Docker エンジンに基づく Windows コンテナーなどのテクノロジを使用します。 コンテナーは、複数の段階的で展開するときに、アプリケーションの依存関係によって引き起こされる摩擦を取り除きます。 コンテナーは、データ、監視、および継続的な統合/継続的な展開 (CI/CD) パイプラインに関連するその他のクラウドで管理されたサービスにも使用します。

3 番目の成熟度レベルは、クラウドの最終的な目標ですが、多くのアプリでは省略可能であり、このガイドの主な焦点ではありません。

**レベル 3: クラウド最適化**: この移行アプローチは、一般的にビジネス ニーズによって推進され、ミッション クリティカルなアプリケーションの刷新を目標とします。 このレベルでは、PaaS サービスを使用してアプリを PaaS コンピューティング インフラストラクチャに移行します。 [クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) アプリケーションおよびマイクロサービス アーキテクチャを実装して長期的な機敏性を持つようにアプリケーションを発展させ、新しい制限にスケールを設定します。 このタイプの最新化は、通常、クラウド用の特別な構築が必要です。 多くの場合、新しいコードを書き込まれなければなりません、特にクラウド ネイティブ アプリケーションとマイクロ サービスに基づくモデルに移動する場合に必要です。 このアプローチは、モノリシックなオンプレミス アプリケーション環境では実現することが困難なメリットを得ることができます。

表 1-1 は、各移行または最新化アプローチを選択する理由との主な利点を説明しています。

| **クラウド インフラストラクチャの準備完了** <br /> *リフト アンド シフト* | **クラウド DevOps の準備完了** <br /> *リフト アンド シフト* | **クラウド最適化** *最新化/リファクター/書き換え* |
|---|---|---|
| **アプリケーションの計算対象** |
| Azure の VM にデプロイされたアプリケーション | VM、Azure Service Fabric、または Azure Container Service (つまり Kubernetes) にデプロイされたコンテナー化されたモノリシックまたは N 層アプリケーション | Azure App Service、Azure Service Fabric、または Azure Container Service (つまり Kubernetes) 上の PaaS に基づくコンテナー化されたマイクロサービスまたは通常のアプリケーション |
| **データの対象** |
| SQL または VM 上の任意のリレーショナル データベース | Azure SQL データベースのマネージ インスタンス | Azure SQL データベース、Azure Cosmos DB、またはその他の NoSQL |
| **長所**|
| <li>再設計や新しいコードがない <li> 最小限の労力による迅速な移行 <li> Azure でサポートされる最小公倍数 <li> 基本的な可用性の保証 <li> クラウドへの移行後にする方が簡単な最新化 | <li>再設計や新しいコードがない <li> コンテナーは、VM よりも小さな増分の作業を提供する <li> コンテナーに展開とリリースのための DevOps の機敏性の改善 <li> 密度の増大と展開コストの削減 <li> アプリとの依存関係の移植性 <li> Azure Container Service (または Kubernetes) および Azure Service Fabric の使用により高可用性とオーケストレーションを提供 <li> Service Fabric でのノード/VM の修正プログラムの適用 <li> ホストのターゲットの柔軟性: Azure の仮想マシンまたはバーチャル マシンのスケール設定すると、Azure コンテナー サービス (または Kubernetes)、Service Fabric と将来のコンテナーに基づく選択 | <li>クラウド、リファクター、必要な新しいコードの設計 <li> マイクロサービス クラウドネイティブ アプローチ <li> 新しい Web アプリ、モノリシック、N 層、クラウドの回復力、クラウド最適化 <li> 完全に管理されたサービス <li> 自動修正プログラム適用 <li> スケールに最適化 <li> サブシステムによる自律的な機敏性に最適化 <li> 展開と DevOps 上の構築 <li> スロットや展開戦略などの DevOps の機能強化 <li> PaaS とオーケストレーターの対象: Azure App Service、Azure Container Service (または Kubernetes)、Azure Service Fabric、および将来のコンテナー ベースの PaaS |
| **課題** |
| <li> 運用費のシフトまたはデータセンターの閉鎖以外の小さなクラウドの価値 <li> 管理対象がほとんどない: OS またはミドルウェア修正プログラムの適用がない、Terraform、Spinnaker、Puppet などのインフラストラクチャ ソリューション | <li> コンテナー化は学習カーブの追加の手順で不変である必要がある | <li> 重要なコードのリファクタリングまたは書き換えが必要な可能税がある (時間および予算の増加) |
> **表 1-1** 既存の .NET アプリケーションとサービスの最新化パスのメリットと課題

### <a name="key-technologies-and-architectures-by-maturity-level"></a>成熟度レベル別の主要なテクノロジおよびアーキテクチャ

.NET Framework アプリケーションは、2001 年後半にリリースされた .NET Framework バージョン 1.0 から始まりました。 その後企業は新しいバージョン (2.0、3.5、.NET 4.x など) に移行しました。 それらのアプリケーションのほとんどは、Windows サーバーとインターネット インフォメーション サーバー (IIS) 上で実行されたし、SQL Server、Oracle、MySQL、またはその他の任意の RDBMS のように、リレーショナル データベースを使用します。

ほとんどの既存の .NET アプリケーションは現在、.NET Framework 4.x または .NET Framework 3.5 を基にし、ASP.NET MVC、ASP.NET Web Forms、ASP.NET Web API、Windows Communication Foundation (WCF)、ASP.NET SignalR、ASP.NET Web ページなどの Web フレームワークを使用しています。 これらの確立された .NET Framework テクノロジは Windows に依存しています。 レガシ アプリケーションを移行するだけで、アプリケーションのインフラストラクチャの変更を最小限にする場合は、その依存関係を考慮することが重要です。

図 1-2 は、3 つの各クラウド成熟度レベルで使用する主要なテクノロジとアーキテクチャ スタイルを示しています。

![既存の .NET Web アプリケーションの最新化のための成熟度レベルごとの主要なテクノロジ](./media/image1-2.png)

> **図 1-2** 既存の .NET Web アプリケーションの最新化のための成熟度レベルごとの主要なテクノロジ

図 1-2 では、最も一般的なシナリオが強調表示されていますが、アーキテクチャについては多くハイブリッドと混在のバリエーションが使用可能です。 たとえば、成熟度モデルは、既存の Web アプリのモノリシック アーキテクチャだけでなく、サービス指向、N 層、およびその他のアーキテクチャのスタイルのバリエーションにも適用されます。

最新化プロセス内の各成熟度レベルは、次の主要なテクノロジおよびアプローチに関連付けられています。

- **クラウド インフラストラクチャ準備完了** (再ホストまたは基本的なリフト アンド シフト): 最初のステップとして、多くの組織はクラウド移行戦略を迅速に実行することのみを希望します。 この場合、アプリケーションは単純に再ホストされます。 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)、[Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) などのクラウドツールを基にした Azure への移行を支援するために必要なガイダンス、洞察、メカニズムを提供するサービスである [Azure Migrate](https://aka.ms/azuremigrate) を使用することで、ほとんどの再ホストは自動化することができます。 レガシ アプリケーションをクラウドに移動するときに、資産についてインフラストラクチャの詳細を確認することができるように、再ホストを手動で変更を設定することもできます。 たとえば、ほとんど変更せずに (おそらく少しの構成変更だけで) Azure の VM にアプリケーションを移動することができます。 特に Azure で仮想ネットワークを作成する場合、このケースでのネットワークは、オンプレミス環境に似ています。

- **クラウド DevOps 準備完了** (改善されたリフト アンド シフト): このモデルでは、アプリケーションの主要なアーキテクチャを変更することなく、クラウドからのいくつかの重要な利点を取得するために、いくつかの重要な展開の最適化を行います。 ここでの基本的な手順は、[Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/) サポートを既存の .NET Framework アプリケーションに追加することです。 この重要な手順 (コンテナー化) は、コードを操作しないので、全体的なリフト アンド シフトの作業が非常に少なくなります。 [Image2Docker](https://github.com/docker/communitytools-image2docker-win) や Visual Studio などのツールと、[Docker](https://www.docker.com/) 用のツールを使用できます。 Visual Studio は、ASP.NET アプリケーションおよび Windows コンテナー イメージ用のスマート有効な既定値を自動的に選択します。 これらのツールは、迅速な内側のループと Azure へのコンテナーを取得する高速なパスの両方を提供します。 複数の環境に展開するときの機敏性が向上します。 次に、実稼働環境に移動し、Windows コンテナーを [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) または [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes、DC/OS、または Swarm) などのオーケストレーターに展開します。 この初期最新化中に、[Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) などのツールによる監視、[Visual Studio Team Services](https://www.visualstudio.com/team-services/) を使用したアプリ ライフサイクルの CI/CD パイプライン、および Azure で使用可能な多数のデータ リソース サービスなどのクラウドの資産を追加することもできます。 たとえば、従来の [ASP.NET Web Forms](https://www.asp.net/web-forms) や [ASP.NET MVC](https://www.asp.net/mvc) を使用して最初に開発され、しかし現在は Windows コンテナーを使用して展開されるモノリシック Web アプリを変更することができます。 Windows コンテナーを使用するときには、データも [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/)のデータベースに移行する必要があります。アプリケーションの主要なアーキテクチャを変更せずにすべてを移行できます。

- **クラウド最適化**: 前に述べたように、クラウドでアプリケーションを最新化するときにの最終的な目標は、[Azure App Service](https://azure.microsoft.com/services/app-service/) のような PaaS プラットフォームをシステムの基盤にすることです。 最新の Web アプリケーションを重視した PaaS プラットフォーム、および[サーバーレス コンピューティング](https://azure.microsoft.com/overview/serverless-computing/)とのようなプラットフォームと [Azure Functions](https://azure.microsoft.com/services/functions/) のようなプラットフォームを基にした新しいサービスでアプリを拡張します。 この成熟度モデルの 2 番目のより高度なシナリオは、マイクロサービス アーキテクチャと[クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)なアプリケーションです。これらは一般的に、[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) や [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes、DC/OS、Swarm) などのオーケストレーターを使用します。 これらのオーケストレーターは、マイクロサービスとマルチコンテナー アプリケーション向けに特別に作成されています。 これらのすべてのアプローチ (マイクロサービスと PaaS など) は、一般的に、特定の PaaS プラットフォームに適合される新しいコードを作成するか、マイクロサービスなどの特定のアーキテクチャに適合するコードを作成する必要があります。

図 1-3 は、成熟度レベルごとに使用できる内部のテクノロジを示しています。

![各最新化成熟度レベルの内部のテクノロジ](./media/image1-3.png)

> **図 1-3** 各最新化成熟度レベルの内部のテクノロジ

## <a name="lift-and-shift-scenarios"></a>リフト アンド シフトのシナリオ

リフト アンド シフトの移行では、アプリケーションのシナリオでリフト アンド シフトの多くの異なるバリエーションを使用できることに注意してください。 アプリケーションの再ホストのみを行う場合は、図 1-4 に示すようなシナリオを使用することがあります。この場合、アプリケーションおよびデータベース サーバー用にのみクラウドで VM を使用します。

![クラウドの純粋な IaaS シナリオの例](./media/image1-4.png)

> **図 1-4** クラウドの純粋な IaaS シナリオの例

さらに進めて、その成熟度レベルからのみの要素を使用する純粋なクラウド DevOps 対応アプリケーションを使用する場合があります。 また、図 1-5 のようにクラウド インフラストラクチャ準備完了からのいくつかの要素、およびクラウド DevOps 準備完了からの他の要素を含む中間的な状態のアプリケーションもあります ("選択" または混在モデル)。

![IaaS 上のデータベース、DevOps、およびコンテナー化資産を含む "選択" シナリオの例](./media/image1-5.png)

> **図 1-5** IaaS 上のデータベース、DevOps、およびコンテナー化資産を含む "選択" シナリオの例

次に、移行を既存の .NET Framework アプリケーションを多くのシナリオとしては理想的処理量が少ないからメリットを取得する、クラウド DevOps 対応アプリケーションを移行することができます。 このアプローチは、将来的に実行可能なステップとしてクラウドの最適化もセットアップします。 図 1-6 に例を示します。

![Windows コンテナーと管理サービスを使用するクラウド DevOps 準備完了アプリ シナリオの例](./media/image1-6.png)

> **図 1-6** Windows コンテナーと管理サービスを使用するクラウド DevOps 準備完了アプリ シナリオの例

さらに進んで、特定のシナリオ用のいくつかのマイクロサービスを追加することで、既存のクラウド DevOps 準備完了アプリケーションを拡張することができます。 これは、クラウド最適化モデル内で部分的にクラウド ネイティブのレベルに移動しますが、現在のガイダンスの重点ではありません。


## <a name="what-this-guide-does-not-cover"></a>このガイドに含まれないもの

このガイドでは、図 1-7 に示すように、サンプル シナリオの特定のサブセットについて説明します。 このガイドでは、リフト アンド シフトのシナリオおよび最終的にクラウド DevOps 準備完了モデルにのみ焦点を当てています。 クラウド DevOps 準備完了モデルでは、Windows コンテナーと、監視や CI/CD パイプラインなどの追加のコンポーネントを使用して.NET Framework アプリケーションを最新化します。 各コンポーネントは、クラウドに迅速かつ機敏に展開するための基礎です。

![クラウド DevOps 準備完了アプリケーションへのリフト アンド シフトおよび初期最新化](./media/image1-7.png)

> **図 1-7** クラウド DevOps 準備完了アプリケーションへのリフト アンド シフトおよび初期最新化

このガイドの目的は固有です。 再設計なしでコードを変更しないでをリフト アンド シフト、既存の .NET アプリケーションを実現するためのパスを示します。 最終的には、方法を示しますクラウド DevOps 対応アプリケーションにします。

このガイドでは、microservices アーキテクチャに発展させる方法などのクラウド ネイティブ アプリケーションを操作する方法を示します。 アプリケーションを再構築するかマイクロサービスに基づく新しいアプリケーションを作成するには、電子ブック『[.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook)』(.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ) を参照してください。

### <a name="additional-resources"></a>その他の技術情報

- **Microsoft プラットフォームとツールのアプリケーションのライフ サイクルの Docker のコンテナー** (ダウンロード可能な電子書籍)。 [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET Microservices: コンテナーの .NET アプリケーションのアーキテクチャ**(ダウンロード可能な電子書籍)。 [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **ASP.NET Core と Azure での最新の web アプリケーションの設計**(ダウンロード可能な電子書籍)。 [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>対象読者

このガイドは、開発者および配布し、アプリケーションを解放するの機敏性の向上の .NET Framework に基づく既存の ASP.NET アプリケーションを最新化するソリューション設計者向けに記述されています。

Microsoft Azure を使用するときに Windows コンテナーを使用し、クラウドに展開することによって得られるメリットの概要が知りたいだけのエンタープライズ アーキテクトや開発担当者などの技術的な意思決定者の場合にもこのガイドが役に立つことがあります。

## <a name="how-to-use-this-guide"></a>このガイドの使用方法

このガイドでは、既存のアプリケーションを最新化する必要がある "理由"、およびアプリをクラウドに移行するときに Windows コンテナーを使用することによって得られる具体的なメリットについて説明します。 このガイドの最初のいくつかの章の内容は、概要を知る必要はあっても、実装および技術的な詳細手順を知る必要はないアーキテクトおよび技術的意思決定者向けに設計されています。

このガイドの最後の章では、特定の展開シナリオにフォーカスを当てた複数のチュートリアルを紹介します。 このガイドは、シナリオの概要と、その利点を強調表示、チュートリアルの短いバージョンを提供します。 完全なチュートリアルでは、セットアップおよび実装の詳細にドリル ダウンし、関連のサンプル アプリが置かれている (次のセクションで説明します) 同じ公開されている [GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing) 内の [wiki 投稿](https://github.com/dotnet-architecture/eShopModernizing/wiki)のセットとして公開されています。 最後の章および GitHub のステップ バイ ステップの wiki のチュートリアルは、実装の詳細に重点を置く必要がある開発者とアーキテクトにとってより興味深い内容になっています。

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>レガシ アプリケーションの最新化のためのアプリのサンプル: eShopModernizing

GitHub の [EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) リポジトリは、レガシ モノリシックな Web アプリケーションをシミュレートする 2 つのサンプル アプリケーションを提供します。 1 つ目の Web アプリは ASP.NET MVC を使用して開発され、2 つ目の Web アプリは、ASP.NET Web フォームを使用して開発されています。 両方の Web アプリは、従来の .NET Framework に基づいています。 これらのサンプル アプリでは .NET Core または ASP.NET Core は使用しません。これは、これらが最新化される既存の/レガシ .NET Framework アプリケーションと見なされるためです。

両方のサンプル アプリで、最新化されたコードを持つ、単純な 2 つ目のバージョンを使用します。 アプリのバージョン間で最も重要な違いは、2 つ目のバージョンでは Windows コンテナーを展開の選択肢として使用することです。 2 つ目のバージョンには、イメージ管理のための Azure Storage Blobs、セキュリティ管理のための Azure Active Directory、アプリケーションの監視と監査のための Azure Application Insights などのいくつかの追加機能もあります。

## <a name="send-your-feedback"></a>お客様のフィードバックを送信します。

このガイドは、向上し、既存の .NET web アプリケーションを刷新のオプションについて理解するために作成されました。 ガイドと関連するサンプル アプリケーションは進化しています。 お客様のフィードバックは、ようこそ! このガイドを改善する方法についてご意見があれば、[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book) に送信してください。

>[!div class="step-by-step"]
[次へ](lift-and-shift-existing-apps-azure-iaas.md)
