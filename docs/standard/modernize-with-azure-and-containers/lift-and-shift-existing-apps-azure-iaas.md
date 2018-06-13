---
title: リフトし、既存の .NET アプリケーションを Azure IaaS (クラウド インフラストラクチャの準備完了) にシフト
description: 既存の .NET アプリケーションと Azure のクラウドと Windows コンテナーを開放します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 458b1bd1fc9fc24ce43d0926655fe0767aabc43c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956449"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>リフトし、既存の .NET アプリケーションを Azure IaaS (クラウド インフラストラクチャの準備完了) にシフト

> ビジョン: 最初の手順としてをハードウェアの内部設置型への投資と総コストを削減し、クラウド内の既存のアプリケーションを再ホスト ネットワークのメンテナンス、単純にします。

入る前に*方法*Azure infrastructure as a service (IaaS) プラットフォームを既存のアプリケーションを移行することが理由を分析する重要*理由*IaaS に直接移行します。azure です。 この近代化成熟度レベルのシナリオでは引き続き、現在、内部設置型インフラストラクチャを使用してではなく、クラウド内の Vm の使用を開始を本質的にします。

分析に別のポイントが*理由*詳細設定で、Azure 管理サービスを追加するだけではなく純粋な IaaS クラウドへ移行する場合があります。 確認の場合があります最初の場所に IaaS を必要とします。

図 2-1 では、クラウド インフラストラクチャの準備完了のアプリケーションを配置近代化成熟度レベルで。

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-1.png)

> **図 2-1** クラウド インフラストラクチャの準備完了のアプリケーションの配置

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Azure IaaS に既存の .NET web アプリケーションを移行する理由

初期の IaaS レベルでも、クラウドに移行する主な理由は、コストの削減を実現するためにです。 多くの管理されたインフラストラクチャ サービスを使用すると、組織はハードウェアのメンテナンス、サーバーまたは VM のプロビジョニングし配置、およびインフラストラクチャの管理で、投資収益率を下げることができます。

アプリをクラウドに移動する意思決定を行うと、選択する理由が IaaS PaaS は単純にするようより高度なオプションではなく、IaaS 環境主な理由は、他の一般的なになります。 現在次のような環境への移動、オンプレミス環境には、低い習得、これにより、クラウドが最速のパスを提供します。

ただし、クラウドに移行する最も簡単な方法を選ぶわけでは、アプリケーション、クラウドで実行する必要がなくなりますほとんどの利益を得ることがあります。 任意の組織には、既に導入された、クラウドに最適化されたとクラウド ネイティブの成熟度レベルでのクラウド移行から最も重要な利点が獲得できません。

これもが明らかになりますアプリケーションは改革し、IaaS 上であっても、クラウドで既に実行されている場合、後で再構築しやすくします。 アプリケーション データの移行は既に実現されています。 また、組織が、クラウドでの作業に必要なスキルを獲得しようし、shift キーを押し"クラウド culture"で動作しています。

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>代わりに PaaS に IaaS に移行するときに

次のセクションでは、クラウドに最適化されたは、ほとんどの場合に基づくアプリケーションの PaaS プラットフォームおよびサービスについて説明します。 これらのアプリによって、クラウドへの移行からほとんどの利点がわかります。 

目標は、既存のアプリケーションをクラウドに移動することだけが場合、は、最初に、Azure App Service で実行するに大幅な変更を必要とせず、既存のアプリケーションを特定します。 これらのアプリでの最初の候補をする必要がありますクラウドに向けて最適化されました。 

次に、アプリを引き続きに移動できません Windows コンテナーと PaaS App Service または Azure Service Fabric のような orchestrators を移行できる単純なプレーンな vm (IaaS) など。 

しかし、正しく構成、セキュリティ保護、および Vm の維持が必要である多くの時間と azure PaaS サービスを使用する場合に比べて IT 専門知識に注意してください。 Azure の仮想マシンを検討している場合は、更新プログラム、更新、および VM 環境の管理に必要な継続的な保守作業を考慮するを確認します。 Azure の仮想マシンは、IaaS です。

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Azure の移行を使用して分析し、既存のアプリケーションを Azure に移行

クラウドへの移行は、困難であるがありません。 多くの組織が、環境とアプリケーション、ワークロード、およびデータの間で緊密な依存関係の詳細表示の開始に苦労します。 その可視性なしは、移行パスを計画するが困難ができます。 移行の成功のために必要な新機能の詳細な情報がない場合、組織内で右のメッセージ交換ことはできません。 潜在的なメリットをコストについて十分かわからないまたはかどうかワークロードまたはことがだけリフトと-シフト大幅な修正を正常に移行する必要があります。 当然と多くの組織になる躊躇します。

[Azure 移行](https://aka.ms/azuremigrate)ガイダンス、insights、および Azure への移行を支援するために必要なメカニズムを提供する新しいサービスは、します。 Azure の移行を提供します。

- 探索と内部設置型の仮想マシンの評価

- 多階層アプリケーションの信頼性の高い検出用の組み込みの依存関係のマッピング

- Azure の仮想マシンをインテリジェント右側のサイズ変更

- 潜在的な問題を修復するためのガイドラインとレポートの互換性

- データベースの検出と移行のための Azure Database Management Service との統合

Azure の移行では、信頼度のワークロードが業務に影響を最小限に移行し、Azure で期待どおりに実行できます。 適切なツールとガイダンスでは、最大の重要なパフォーマンスを確保しながら投資回収を実現でき、信頼性のニーズを満たしています。

図 2-2 では、Azure の移行によって実行されるすべてのサーバーとアプリケーションの接続の組み込みの依存関係のマッピングを示します。

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-2.png)

> **図 2-2 です。** クラウド インフラストラクチャの準備完了のアプリケーションの配置

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Azure Site Recovery を使用して、既存の Vm を Azure Vm に移行するには

エンド ツー エンドの一部として[Azure 移行](https://aka.ms/azuremigrate)、 [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) Azure での Vm に web アプリを簡単に移行に使用できるツールです。 内部設置型 Vm と物理サーバーを Azure にレプリケートする、またはセカンダリ オンプレミスの場所にこれらをレプリケートするには、Site Recovery を使用することができます。 サポートされている Azure 仮想マシンの場合、内部設置型上で実行されているワークロードをレプリケートすることもできます*HYPER-V* VM の*VMware* VM、または Windows または Linux の物理サーバーにします。 Azure へのレプリケーションでは、コストとセカンダリ データ センターを維持するための複雑さを排除します。

サイトの回復が部分的であるハイブリッド環境の具体的には行われたも、内部設置型と一部の Azure です。 Site Recovery の Vm で実行されているアプリを保持することでビジネス継続性によりと内部設置型で利用できる物理サーバー、サイトがダウンした場合。 実行されている仮想マシンおよび物理サーバー上で常に利用可能なセカンダリの場所に、プライマリ サイトが利用できない場合のワークロードをレプリケートします。 これが上向きのとき、プライマリ サイトを再実行してワークロードを回復します。

図 2-3 では、Azure Site Recovery を使用して、複数の VM の移行の実行を示します。

![クラウド インフラストラクチャの準備完了のアプリケーションの配置](./media/image2-3.png)

> **図 2-3。** クラウド インフラストラクチャの準備完了のアプリケーションの配置

### <a name="additional-resources"></a>その他の技術情報

- **Azure 移行データシート**

    [https://aka.ms/azuremigration\_データシート](https://aka.ms/azuremigration\_datasheet)

- **Azure を移行します。**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Site Recovery と Azure への移行します。**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Azure Site Recovery サービスの概要**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **AWS を Azure Vm で Vm を移行します。**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[前へ](index.md)
[次へ](migrate-your-relational-databases-to-azure.md)
