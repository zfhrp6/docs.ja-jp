---
title: ハイブリッド クラウド シナリオへの移行します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |ハイブリッド クラウド シナリオへの移行します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957892"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>ハイブリッド クラウド シナリオへの移行します。

組織や企業によっては、Microsoft Azure などのパブリック クラウドに、アプリケーションの一部または規制や独自のポリシーのための他の任意のパブリック クラウドに移行できません。 ただし、どのような組織は、パブリック クラウドおよびその他のアプリケーション、オンプレミスでのアプリケーションの一部がなくなりますメリットがある可能性がありますです。 混在する環境がさまざまなプラットフォームと内部設置型環境とパブリック クラウドで使用されているテクノロジのための環境での複雑度が高くを招くことができます。

Microsoft では、最適なハイブリッド クラウド ソリューションを提供する、既存の資産を最適化できますいずれか、オンプレミスと Azure のハイブリッド クラウド内の一貫性を確保するときに、パブリック クラウドでします。 既存のスキルを最大化し、クラウドまたはオンプレミスで Azure スタック (オンプレミス) と Azure (パブリック クラウド) のおかげで実行できるアプリを構築するための柔軟で、統一されたアプローチを取得できます。

セキュリティに関しては、ときに、ハイブリッド クラウドの間で管理およびセキュリティを一元化できます。 内部設置型へのシングル サインオンを指定して、クラウド データ センターからすべての資産の制御を取得し、クラウド アプリできます。 ためには、Active Directory のハイブリッド クラウドに拡張および id 管理を使用しています。

最後に、配布しシームレスにデータを分析、クラウドとオンプレミスの資産に同じクエリ言語を使用し、適用できます分析と深いをその元に関係なく、データを強化する Azure で学習します。

## <a name="azure-stack"></a>Azure のスタック

Azure のスタックは、ハイブリッド クラウド プラットフォームできるように、組織のデータ センターから Azure サービスを提供します。 Azure のスタックは、エッジと接続されていない環境では、または特定のセキュリティとコンプライアンス要件を満たすように、主要なシナリオで、最新のアプリケーション用の新しいオプションをサポートするために設計されています。

図 4-13 では、Microsoft が提供する場合は true。 ハイブリッド クラウド プラットフォームの概要を示します。

![Azure のスタックは、Azure で Microsoft ハイブリッド クラウド プラットフォーム](./media/image13.jpg)

> **図 4-13。** Azure のスタックは、Azure で Microsoft ハイブリッド クラウド プラットフォーム

Azure のスタックは、ニーズに合わせて、展開の 2 つのオプションで提供されています。

-   Azure のスタックは、システムを統合

-   Azure のスタック開発キット

### <a name="azure-stack-integrated-systems"></a>Azure のスタックは、システムを統合

Microsoft とハードウェア パートナーのパートナーシップでは、azure スタック統合システムが提供します。 パートナーシップでは、わかりやすくするための管理の分散クラウド ペース革新性を実現するソリューションを作成します。 ハードウェアとソフトウェアの統合システムとして、Azure のスタックが提供されるため、まだクラウドから革新を採用しているときに柔軟性と制御、適切な量を取得します。 Azure 統合スタック システムでは、12 のノードに 4 からサイズの範囲し、ハードウェア パートナーと Microsoft によって共同でサポートされます。 Azure スタック統合システムを使用すると、実稼働ワークロードの新しいシナリオを実装します。

### <a name="azure-stack-development-kit"></a>Azure のスタック開発キット

Microsoft Azure スタック Development Kit では、評価し、Azure の履歴に関する学習を行うこともできる Azure スタックの単一ノード展開です。 またするツールと一貫性がある Azure して Api を使用して開発できます。 ここで、開発環境として Azure スタック開発キットを使用することができます。 Azure スタック Development Kit は、実稼働環境として使用するものではありません。

### <a name="additional-resources"></a>その他の技術情報

-   **Azure のハイブリッド クラウド**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Windows コンテナーの active Directory のサービス アカウントします。**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **サポートが Active Directory コンテナーを作成します。**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Azure のハイブリッド特典ライセンス**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[前へ](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[次へ](../walkthroughs-technical-get-started-overview.md)
