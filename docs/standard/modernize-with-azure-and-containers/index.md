---
title: 既存 .NET アプリケーションで Azure のクラウドと Windows コンテナーを最新化 (第 2 版)
description: リフトしシフトし、既存のアプリケーションを Azure クラウドおよび電子書籍とコンテナーを最新化する方法を学習します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 4/28/2018
ms.openlocfilehash: 3fcfdca68e05494785148cbbe149cdc2f812c577
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 (第 2 版)

![カバーの画像](./media/cover.png)

発行者  
マイクロソフト プレスと Microsoft DevDiv  
Divisions of Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © by Microsoft Corporation 2018  

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

Web アプリケーションまたはサービスを最新化し、クラウドに移動する場合は、アプリを完全に再構築しがないとは限りません。 Microservices のような高度なアプローチを使用してアプリケーションをよう再設計することができません常にコストと時間の制約が原因です。 アプリケーションの種類、によってアプリよう再設計するもは必要ありません。 組織のクラウドの移行戦略のコストを最適化するには、ビジネスのニーズとアプリの要件を考慮することが重要です。 次のことを決定する必要があります。

- どのアプリが変換が必要か、よう再設計します。

- どのアプリの部分的な再構築のみが必要か。

- どのアプリをクラウドに直接 "リフト アンド シフト" することができるか。

## <a name="about-this-guide"></a>このガイドについて

このガイド重点的に既存の Microsoft .NET Framework web またはサービス指向アプリケーションの初期近代化新しいまたは最新の環境にアプリケーションのコードを大幅に変更することがなく、ワークロードを移動アクションの意味で基本的なアーキテクチャ。 

このガイドでは、アプリをクラウドに移動し、新しいテクノロジおよび Windows コンテナーと Windows コンテナーをサポートする Azure のコンピューティング プラットフォームで関連するなどの方法の特定のセットを使用してアプリを部分的に刷新の利点も強調表示されます。

## <a name="path-to-the-cloud-for-existing-net-applications"></a>既存の .NET アプリケーションのクラウドへのパス

組織は、通常のアプリケーションで得ることができる機敏性と速度のために、クラウドへの移行を選択します。 オンプレミス サーバーのセットアップには一般的に数週間かかるのと比べて、クラウドでは数千のサーバー (VM) を数分でセットアップできます。

アプリケーションをクラウドに移行するための 1 つの万能型の戦略はありません。 右側の移行の戦略は、組織のニーズと優先度、および移行するアプリケーションの種類によって異なります。 すべてのアプリケーションがサービスとしてのプラットフォーム ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) モデルへの移行や[クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) アプリケーション モデルの開発の投資を保証するわけではありません。 多くの場合は、ビジネス ニーズに基づいて、資産をクラウドに移行する際に段階的なまたは増分アプローチで投資を実行できます。

最適な長期的な機敏性と組織の値を持つモダン アプリケーションの場合への投資からメリットがある*クラウド ネイティブ*アプリケーション アーキテクチャ。 、既存のアプリケーションまたは従来の資産は、キーが大きなメリットを実現する、クラウドに移動しながら、最小限の時間とコスト (よう再設計するか、コード変更なし) を費やすです。

図 1-1 は、既存の .NET アプリケーションを段階的なフェーズでクラウドに移動する場合に実行できる可能性のあるパスを示しています。

 ![既存の .NET アプリケーションとサービスの最新化パス](./media/image1-1.png)

> **(図 1-1)**。 既存の .NET アプリケーションとサービスの最新化パス

各移行アプローチには、さまざまな利点とそれを使用する理由があります。 アプリをクラウドに移行するときには単一のアプローチを選択することも、複数のアプローチから特定のコンポーネントを選択することもできます。 個々 のアプリケーションは、1 つのアプローチまたは成熟度の状態に制限されません。 たとえば、一般的なハイブリッド アプローチには、オンプレミスのコンポーネントに加えてその他のコンポーネントがクラウドにあります。

次の定義と各アプリケーションの成熟度レベルの簡単な説明を示します。

**Level 1: クラウド インフラストラクチャの準備完了**アプリケーション: この移行の方法では、単に移行またはするサービスとしてのインフラストラクチャを現在の内部設置型アプリケーションを再ホスト ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) プラットフォームです。 アプリの構成は前とほとんど変わりませんが、クラウド内の VM に展開します。
この単純な種類の移行は、"リフト & シフト"として業界で通常呼びます

**レベル 2: クラウドの最適化された**アプリケーション: このレベルで、または重要なコードを変更するよう再設計することがなく引き続きクラウド内のコンテナーと同様に、追加の最新テクノロジのアプリを実行してからその他の利点をすることができますクラウドで管理されたサービス。 エンタープライズ開発操作 (DevOps) プロセスが調整され、すばやく出荷するためのアプリケーションの機敏性が向上します。 これを実現するには、Docker エンジンに基づく Windows コンテナーと同様のテクノロジを使用します。 コンテナーは、複数の段階的に展開するときに、アプリケーションの依存関係によって引き起こされる摩擦を削除します。 この成熟度モデルでは IaaS 上のコンテナーを展開することができます。 またはその他の使用中に PaaS サービス、監視、および継続的な統合/継続的なデプロイとして (CI/CD) パイプラインとのキャッシュのクラウドで管理されたサービスが、データベースに関連します。

3 番目の成熟度レベルは、クラウドの最終的な目標ですが、多くのアプリでは省略可能であり、このガイドの主な焦点ではありません。

**Level 3: クラウド ネイティブ**アプリケーション: 通常この移行方法がビジネス ニーズと、ミッション クリティカルなアプリケーションを刷新ターゲットによって実行ができます。 このレベルでは、PaaS サービスを使用してアプリを PaaS コンピューティング インフラストラクチャに移行します。 [クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) アプリケーションおよびマイクロサービス アーキテクチャを実装して長期的な機敏性を持つようにアプリケーションを発展させ、新しい制限にスケールを設定します。 このタイプの最新化は、通常、クラウド用の特別な構築が必要です。 多くの場合、新しいコードを書き込まれなければなりません、特にクラウド ネイティブ アプリケーションとマイクロ サービスに基づくモデルに移動する場合に必要です。 このアプローチは、モノリシックなオンプレミス アプリケーション環境では実現することが困難なメリットを得ることができます。

表 1-1 は、各移行または最新化アプローチを選択する理由との主な利点を説明しています。

| **クラウド インフラストラクチャの準備完了** <br /> *リフト アンド シフト* | **クラウドに最適化されました。** <br /> *最新化します。* | **クラウド ネイティブ** <br /> *最新化、再構築およびを書き換える* |
|---|---|---|
| **アプリケーションの計算対象** |
| Azure の VM にデプロイされたアプリケーション | モノリシックまたはコンテナー、Azure Service Fabric または AKS (Azure Kubernetes サービス) と Azure App Service、Azure コンテナー インスタンス (ACI)、Vm に展開された N 層アプリケーション | Azure Kubernetes サービス (AKS)、Service Fabric Azure 関数に基づいてサーバーなしの microservices にコンテナー化 microservices です。 |
| **データの対象** |
| SQL または VM 上の任意のリレーショナル データベース | Azure SQL データベースのマネージ インスタンスまたはクラウドで管理されている別のデータベースです。 | マイクロ サービス、Azure SQL Database、Azure Cosmos DB、またはクラウド内の別の管理対象データベースに基づくごとの粒度が罰金データベース |
| **長所**|
| <li>よう再設計する、新しいコードはありません。 <li> 最小限の労力による迅速な移行 <li> Azure でサポートされる最小公倍数 <li> 基本的な可用性の保証 <li> クラウドへの移行後にする方が簡単な最新化 | <li> ないよう再設計します。 <li> 最小限のコードと構成の変更 <li> コンテナーに展開とリリースのための DevOps の機敏性の改善 <li> 密度の増大と展開コストの削減 <li> アプリとの依存関係の移植性 <li> ホストのターゲットの柔軟性: PaaS アプローチまたは IaaS | <li> 設計者、クラウドのクラウドから最大のメリットを取得するが、新しいコードが必要 <li> マイクロサービス クラウドネイティブ アプローチ <li> クラウドの回復力のある、最新のミッション クリティカルなアプリケーションで拡張性の高いハイパー <li> 完全に管理されたサービス <li> スケールに最適化 <li> サブシステムによる自律的な機敏性に最適化 <li> 展開と DevOps 上の構築 |
| **課題** |
| <li> 運用費のシフトまたはデータセンターの閉鎖以外の小さなクラウドの価値 <li> ほとんどは管理: なし、OS またはミドルウェア修正プログラムを適用します。Terraform、Spinnaker、Puppet などのインフラストラクチャ ソリューションの使用可能性があります。 | <li> 開発者と IT 運用の習得期間で、追加の手順は、containerizing <li> DevOps と CI/CD のパイプラインは、'必須' この方法では通常です。 しない場合、現在のカルチャ、組織の存在、かもしれませんが、追加の課題| <li> クラウドのネイティブ アプリやマイクロ サービス アーキテクチャの見直しと通常 重要なコードのリファクタリングまたは書き換え刷新するとき (時間が長くおよび予算) が必要です。 <li> DevOps と CI/CD のパイプラインは、'必須' この方法では通常です。 しない場合、現在のカルチャ、組織の存在、かもしれませんが、追加の課題|
> **表 1-1** 既存の .NET アプリケーションとサービスの最新化パスのメリットと課題

### <a name="key-technologies-and-architectures-by-maturity-level"></a>成熟度レベル別の主要なテクノロジおよびアーキテクチャ

.NET Framework アプリケーションは、2001 年後半にリリースされた .NET Framework バージョン 1.0 から始まりました。 その後企業は新しいバージョン (2.0、3.5、.NET 4.x など) に移行しました。 それらのアプリケーションのほとんどは、Windows サーバーとインターネット インフォメーション サーバー (IIS) 上で実行されたし、SQL Server、Oracle、MySQL、またはその他の任意の RDBMS のように、リレーショナル データベースを使用します。

ほとんどの既存の .NET アプリケーションは現在、.NET Framework 4.x または .NET Framework 3.5 を基にし、ASP.NET MVC、ASP.NET Web Forms、ASP.NET Web API、Windows Communication Foundation (WCF)、ASP.NET SignalR、ASP.NET Web ページなどの Web フレームワークを使用しています。 これらの確立された .NET Framework テクノロジは Windows に依存しています。 レガシ アプリケーションを移行するだけで、アプリケーションのインフラストラクチャの変更を最小限にする場合は、その依存関係を考慮することが重要です。

図 1-2 は、3 つの各クラウド成熟度レベルで使用する主要なテクノロジとアーキテクチャ スタイルを示しています。

![既存の .NET Web アプリケーションの最新化のための成熟度レベルごとの主要なテクノロジ](./media/image1-2.png)

> **図 1-2** 既存の .NET Web アプリケーションの最新化のための成熟度レベルごとの主要なテクノロジ

図 1-2 では、最も一般的なシナリオが強調表示されていますが、アーキテクチャについては多くハイブリッドと混在のバリエーションが使用可能です。 たとえば、成熟度モデルは、既存の Web アプリのモノリシック アーキテクチャだけでなく、サービス指向、N 層、およびその他のアーキテクチャのスタイルのバリエーションにも適用されます。 高いフォーカスまたは 1 つまたは別のアーキテクチャの種類と関連技術上の比率は、アプリケーションの全体的な成熟度レベルを決定します。

最新化プロセス内の各成熟度レベルは、次の主要なテクノロジおよびアプローチに関連付けられています。

- **クラウド インフラストラクチャの準備完了**(再ホストまたは basic リフト & シフト): まず、多くの組織のみが必要なクラウド移行戦略を迅速に実行します。 この場合、アプリケーションが再ホストされました。 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)、[Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) などのクラウドツールを基にした Azure への移行を支援するために必要なガイダンス、洞察、メカニズムを提供するサービスである [Azure Migrate](https://aka.ms/azuremigrate) を使用することで、ほとんどの再ホストは自動化することができます。 レガシ アプリケーションをクラウドに移動するときに、資産についてインフラストラクチャの詳細を確認することができるように、再ホストを手動で変更を設定することもできます。 ほとんどの Azure で Vm にアプリケーションを移行するなど、構成の変更だけで変更の可能性があります。 特に Azure で仮想ネットワークを作成する場合、このケースでのネットワークは、オンプレミス環境に似ています。

- **クラウドに最適化された**(管理されたサービスと Windows コンテナー): このモデルでは、アプリケーションの主要なアーキテクチャを変更することがなく、クラウドからのいくつかの重要な利点を取得するために、いくつかの重要な展開の最適化を行うについて説明します。 ここでの基本的な手順は、[Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/) サポートを既存の .NET Framework アプリケーションに追加することです。 この重要な手順 (コンテナリゼーション) は、リフト アンド シフトの全体的な労力がライトであるため、コードと接触している必要はありません。 [Image2Docker](https://github.com/docker/communitytools-image2docker-win) や Visual Studio などのツールと、[Docker](https://www.docker.com/) 用のツールを使用できます。 Visual Studio は、ASP.NET アプリケーションおよび Windows コンテナー イメージ用のスマート有効な既定値を自動的に選択します。 これらのツールは、迅速な内側のループと Azure へのコンテナーを取得する高速なパスの両方を提供します。 複数の環境に展開するときの機敏性が向上します。 次に、実稼働環境に移動、することができます、Windows コンテナーの展開に[コンテナー用の Azure Web アプリ](https://azure.microsoft.com/en-us/services/app-service/containers/)、[Azure のコンテナー インスタンス (ACI) と Azure Vm で Windows Server 2016 とコンテナー IaaS アプローチしたい場合。 少し複雑なマルチ コンテナー アプリケーションの場合と同様に orchestrators に[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)または[Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/)です。 この初期最新化中に、[Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) などのツールによる監視、[Visual Studio Team Services](https://www.visualstudio.com/team-services/) を使用したアプリ ライフサイクルの CI/CD パイプライン、および Azure で使用可能な多数のデータ リソース サービスなどのクラウドの資産を追加することもできます。 たとえば、従来の [ASP.NET Web Forms](https://www.asp.net/web-forms) や [ASP.NET MVC](https://www.asp.net/mvc) を使用して最初に開発され、しかし現在は Windows コンテナーを使用して展開されるモノリシック Web アプリを変更することができます。 Windows コンテナーを使用するときには、データも [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/)のデータベースに移行する必要があります。アプリケーションの主要なアーキテクチャを変更せずにすべてを移行できます。

- **クラウド ネイティブ**: 導入際に、設計に関する考慮[クラウド ネイティブ](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)大規模で複雑なアプリケーションを対象と複数の独立した開発チームで作業しているときに、アプリケーション開発および自律的に展開できるさまざまな microservices します。 マイクロ サービスあたり granularized と独立したスケーラビリティまた、原因です。 これらアーキテクチャの方法は非常に重要な課題と複雑さに直面していますが、PaaS クラウドを使用して、大幅に簡略化および orchestrators like [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/) (マネージ Kubernetes)、[Azure サービスファブリックと[Azure 関数](https://azure.microsoft.com/services/functions/)サーバーなしのアプローチです。 これら (microservices およびサーバーなし) と同様の方法はすべて通常必要とすると、クラウドの構築し、新しいコードを記述-特定の PaaS プラットフォームに適用されるコードまたは microservices と同様に、特定のアーキテクチャに合うコード。

図 1-3 は、成熟度レベルごとに使用できる内部のテクノロジを示しています。

![各最新化成熟度レベルの内部のテクノロジ](./media/image1-3.png)

> **図 1-3** 各最新化成熟度レベルの内部のテクノロジ

## <a name="lift-and-shift-scenario"></a>リフト アンド シフトのシナリオ

リフト アンド シフトの移行では、アプリケーションのシナリオでリフト アンド シフトの多くの異なるバリエーションを使用できることに注意してください。 アプリケーションの再ホストのみを行う場合は、図 1-4 に示すようなシナリオを使用することがあります。この場合、アプリケーションおよびデータベース サーバー用にのみクラウドで VM を使用します。

![クラウドの純粋な IaaS シナリオの例](./media/image1-4.png)

> **図 1-4** クラウドの純粋な IaaS シナリオの例

## <a name="modernization-scenarios"></a>近代化シナリオ

近代化のシナリオでは、成熟度レベルからのみ要素を使用する純粋なクラウドに向けて最適化されたアプリケーションがあります。 また、クラウド インフラストラクチャの準備完了してからクラウドに向けて最適化されたその他の要素からいくつかの要素で中間状態のアプリケーションもあります (「選択」、または混合モデル)、図 1-5 と同様にします。

![IaaS 上のデータベース、DevOps、およびコンテナー化資産を含む "選択" シナリオの例](./media/image1-5.png)

> **図 1-5** IaaS 上のデータベース、DevOps、およびコンテナー化資産を含む "選択" シナリオの例

次に、移行を既存の .NET Framework アプリケーションを多くのシナリオとしては理想的処理量が少ないからメリットを取得する、クラウドに最適化されたアプリケーションを移行することができます。 このアプローチもセットをネイティブでクラウド用に考えられる今後進化として。 図 1-6 に例を示します。

![Windows コンテナーと管理サービスのサンプル アプリをクラウドに最適化されたシナリオ](./media/image1-6.png)

> **図 1-6** Windows コンテナーと管理サービスのサンプル アプリをクラウドに最適化されたシナリオ

さらに進んで、特定のシナリオのいくつかの microservices を追加することで、既存のクラウドに最適化されたアプリケーションを拡張する可能性があります。 これは、部分的に移動存在ガイダンスの主題ではないネイティブ クラウド モデルのレベル。


## <a name="what-this-guide-does-not-cover"></a>このガイドに含まれないもの

このガイドでは、図 1-7 に示すように、サンプル シナリオの特定のサブセットについて説明します。 このガイドでは、リフト アンド シフトのシナリオでのみ、最終的に、クラウドに最適化されたモデルに焦点を当てています。 モデルでは、クラウドに最適化された、Windows コンテナーと監視などの追加コンポーネントを使用して、.NET Framework のアプリケーションが最新化され、CI/CD パイプラインします。 各コンポーネントは、クラウドに迅速かつ機敏に展開するための基礎です。

![クラウド ネイティブは、このガイドで説明されていません。](./media/image1-7.png)

> **図 1-7** クラウド ネイティブは、このガイドで説明されていません。

このガイドの目的は固有です。 あり/なしよう再設計する、コードを変更しないで、リフト アンド シフト、既存の .NET アプリケーションを実現するためのパスを示します。 最終的には、方法を示します、アプリケーションをクラウドに最適化されました。

このガイドでは、microservices アーキテクチャに発展させる方法などのクラウド ネイティブ アプリケーションを作成する方法を示します。 アプリケーションを再構築または microservices に基づくまったく新しいアプリケーションを作成するには、電子書籍を参照してください。 [.NET Microservices: コンテナーの .NET アプリケーションのアーキテクチャ](https://aka.ms/microservicesebook)です。

### <a name="additional-resources"></a>その他の技術情報

- **Microsoft プラットフォームとツールのアプリケーションのライフ サイクルの Docker のコンテナー** (ダウンロード可能な電子書籍)。 [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET Microservices: コンテナーの .NET アプリケーションのアーキテクチャ**(ダウンロード可能な電子書籍)。 [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **ASP.NET Core と Azure での最新の web アプリケーションの設計**(ダウンロード可能な電子書籍)。 [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>対象読者

このガイドは、開発者や既存の ASP.NET web アプリケーションや出荷、アプリケーションを開放することで機敏性の向上の .NET Framework に基づいた WCF サービスを最新化を必要とするソリューション設計者向けに記述されています。

Microsoft Azure を使用するときに Windows コンテナーを使用し、クラウドに展開することによって得られるメリットの概要が知りたいだけのエンタープライズ アーキテクトや開発担当者などの技術的な意思決定者の場合にもこのガイドが役に立つことがあります。

## <a name="how-to-use-this-guide"></a>このガイドの使用方法

このガイドでは、既存のアプリケーションを最新化する必要がある "理由"、およびアプリをクラウドに移行するときに Windows コンテナーを使用することによって得られる具体的なメリットについて説明します。 このガイドの最初のいくつかの章の内容は、概要を知る必要はあっても、実装および技術的な詳細手順を知る必要はないアーキテクトおよび技術的意思決定者向けに設計されています。

このガイドの最後の章では、特定の展開シナリオにフォーカスを当てた複数のチュートリアルを紹介します。 このガイドは、シナリオの概要と、その利点を強調表示、チュートリアルの短いバージョンを提供します。 完全なチュートリアルでは、セットアップおよび実装の詳細にドリル ダウンし、関連のサンプル アプリが置かれている (次のセクションで説明します) 同じ公開されている [GitHub リポジトリ](https://github.com/dotnet-architecture/eShopModernizing) 内の [wiki 投稿](https://github.com/dotnet-architecture/eShopModernizing/wiki)のセットとして公開されています。 最後の章および GitHub のステップ バイ ステップの wiki のチュートリアルは、実装の詳細に重点を置く必要がある開発者とアーキテクトにとってより興味深い内容になっています。

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>レガシ アプリケーションの最新化のためのアプリのサンプル: eShopModernizing

GitHub の [EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) リポジトリは、レガシ モノリシックな Web アプリケーションをシミュレートする 2 つのサンプル アプリケーションを提供します。 ASP.NET MVC; を使用して、1 つの web アプリは開発します。ASP.NET Web フォームを使用して、2 番目の web アプリを開発し、3 番目のアプリは、WCF サービスのバックエンドを消費して WinForms クライアント デスクトップ アプリで N 層アプリ。 これらすべてのアプリは、従来の .NET Framework に基づいています。 これらのサンプル アプリでは .NET Core または ASP.NET Core は使用しません。これは、これらが最新化される既存の/レガシ .NET Framework アプリケーションと見なされるためです。

これらのサンプル アプリを最新のコードの 2 つ目のバージョンであるか、非常に簡単です。 アプリのバージョン間で最も重要な違いは、2 つ目のバージョンでは Windows コンテナーを展開の選択肢として使用することです。 2 つ目のバージョンには、イメージ管理のための Azure Storage Blobs、セキュリティ管理のための Azure Active Directory、アプリケーションの監視と監査のための Azure Application Insights などのいくつかの追加機能もあります。

## <a name="send-your-feedback"></a>お客様のフィードバックを送信します。

このガイドは、向上し、既存の .NET web アプリケーションを刷新のオプションについて理解するために作成されました。 ガイドと関連するサンプル アプリケーションは進化しています。 お客様のフィードバックは、ようこそ! このガイドを改善する方法についてご意見があれば、[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book) に送信してください。

>[!div class="step-by-step"]
[次へ](lift-and-shift-existing-apps-azure-iaas.md)
