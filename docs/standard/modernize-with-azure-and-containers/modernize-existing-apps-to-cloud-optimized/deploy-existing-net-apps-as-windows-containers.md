---
title: Windows コンテナーとして既存の .NET アプリを展開します。
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |Windows コンテナーとして既存の .NET アプリを展開します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 829f33aba14d79d7d9003d1ac7472a19060d401a
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958002"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Windows コンテナーとして既存の .NET アプリを展開します。

Windows コンテナーに基づいた展開は、クラウドに最適化されたアプリケーションやクラウド ネイティブ アプリケーションに適用されます。

ただし、このガイドで、次のセクションでは、特にでほとんどの場合に焦点を Windows コンテナーを使用して*クラウドに向けて最適化された*アプリケーションを再構築する必要のないアプリケーションです。

## <a name="what-are-containers-linux-or-windows"></a>コンテナーとは? (Linux または Windows)

コンテナーは、分離された独自のパッケージにアプリケーションをラップする方法です。 アプリケーションは、そのコンテナーに、コンテナーの外部に存在するアプリケーションまたはプロセスによって影響はありません。 すべてのアプリケーションに依存実行が正常に、プロセスが、コンテナー内にあるとします。 任意の場所のコンテナーが移動する可能性があります、アプリケーションの要件が常に満たされる直接的な依存関係の観点から (ライブラリの依存関係、ランタイム、およびなど) を実行する必要があるすべてのものが、バンドルされているためです。

コンテナーの主な特性をしやすくなる環境同じ別の展開全体でため、コンテナー自体が付属して必要なすべての依存関係です。 コンピューターにアプリケーションをデバッグし、別のコンピューターに保証される同じ環境に展開できます。

コンテナーは、コンテナー イメージのインスタンスです。 コンテナー イメージは、アプリや (snapshot) などのサービスをパッケージ化し、信頼性が高く、再現可能な方法で展開する方法です。 Docker ではないことのみ、テクノロジのも理念およびプロセスとする可能性があります。

業界全体「の配置単位です」になっているコンテナーが毎日より一般的になると、

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>コンテナー (Linux または Windows 上の Docker エンジン) の利点

コンテナーのどちらを使用してアプリケーションを構築する可能性がありますもとして定義されている軽量のビルド ブロックは大幅に増加アジリティ構築、配布、および、インフラストラクチャ全体にわたって、すべてのアプリケーションを実行しているのためです。

コンテナーでは、すべてのアプリの開発から運用環境にほとんどまたはまったくないコード変更により、Microsoft 開発者ツール、オペレーティング システムとクラウド間の Docker 統合感謝を実行できます。

普通の Vm を展開するときに既に ASP.NET アプリケーションの Vm を展開するためにメソッドがあります。 ただし、メソッドに含まれている複数の手動手順や複雑な自動プロセス、Puppet などの展開ツールまたは同様のツールを使用して、可能性があります。 構成項目の変更、サーバー間でのアプリケーションのコンテンツをコピーおよびテスト後に、.msi 設定に基づいて対話形式のセットアップ プログラムを実行するようにタスクを実行する必要があります。 展開内のこれらのすべての手順は、展開する時間およびリスクを追加します。 依存関係が、ターゲット環境に存在しないときにエラーが表示されます。

Windows コンテナーでアプリケーションのパッケージ化のプロセスが完全に自動化されます。 Windows コンテナーは、自動更新、およびコンテナーの展開のロールバックを提供する Docker プラットフォームに基づいています。 Docker エンジンを使用してから取得するメインの向上は、すべての依存関係と、アプリケーションのスナップショットは、イメージを作成することです。 イメージは、Docker イメージ (Windows コンテナー イメージ、ここでは) です。 イメージは、ソース コードに戻されることがなく、コンテナーでは、ASP.NET アプリを実行します。 コンテナーのスナップショットでは、配置の単位になります。

多くの組織では、次の理由でモノリシックな既存のアプリケーションを containerizing は。

-   **クラウドに改善された展開をリリース**です。 コンテナーは、開発と運用の間で一貫性のある展開のコントラクトを提供します。 コンテナーを使用するときと開発者が聞こえません () で"、私のコンピューターでは、しないのはなぜ実稼働環境でですか?" 言った、"、"として実行されます、コンテナー、実稼働環境で実行するためです。 およびすべての依存関係のパッケージ化されたアプリケーションは、サポートされているコンテナー ベース環境で実行できます。 すべての配置対象 (dev、QA、ステージング、実稼働) で実行する意図された方法で実行されます。 1 つの段階から次に、展開を大幅に向上させるに移動する、コンテナーがほとんど frictions を排除し、高速化を出荷することができます。

-   **コスト削減**です。 コンテナーは、統合と既存のハードウェア、またはハードウェアの単位あたり高密度でアプリケーションを実行してから削除するか、コスト削減につながります。

-   **移植性**です。 コンテナーは、モジュール形式およびポータブルです。 Docker コンテナーは、任意のサーバー オペレーティング システム (Linux と Windows) のメジャーのパブリック クラウド (Microsoft Azure、Amazon AWS、Google、IBM) は、オンプレミスおよびプライベートまたはハイブリッド クラウド環境でサポートされます。

-   **コントロール**です。 コンテナーは、コンテナー レベルで制御される柔軟かつセキュリティで保護された環境を提供します。 コンテナーのセキュリティで保護された、分離、およびコンテナーの実行ポリシーの制約を設定しても制限されます。 Windows コンテナーに関するセクションで詳細なとしては、Windows Server 2016 と HYPER-V コンテナーは、その他のエンタープライズ サポート オプションを提供します。

アジリティ、移植性、およびコントロールでの大きな改善点最終的に発生するコストを大幅に削減開発およびアプリケーションを管理するコンテナーを使用する場合。

## <a name="what-is-docker"></a>Docker について

[Docker](https://www.docker.com/)は、[オープン ソース プロジェクト](https://github.com/docker/docker)クラウドまたは内部設置型で実行でき、移植可能で自分のコンテナーとしてのアプリケーションの展開を自動化します。 Docker は、このテクノロジを促進および進化させる[会社](https://www.docker.com/)でもあります。 会社は、クラウド、Linux、およびなどの Microsoft Windows ベンダーと共同で動作します。

![](./media/image6.png)

> **図 4 ~ 6 です。** Docker は、ハイブリッド クラウドのすべてのレイヤーでコンテナーを展開します。

他の人に、仮想マシンを使い慣れてコンテナーする可能性がありますよく似ています。 コンテナーは、オペレーティング システムを実行、なファイル システムおよび物理または仮想コンピューターのシステムと同じように、ネットワーク経由でアクセスできます。 ただし、テクノロジ、およびコンテナーの背後にある概念は、仮想マシンから大幅に異なるです。 開発者の観点からコンテナー扱う必要があるより 1 つのプロセスと同様にします。 実際には、コンテナーは、1 つのプロセスの 1 つのエントリ ポイントがします。

Docker コンテナー (わかりやすくするため、*コンテナー*) Linux と Windows 上でネイティブに実行できます。 Windows コンテナーを Windows ホスト (ホスト サーバーまたは VM) でのみ実行できます正規のコンテナーを実行する場合と、Linux コンテナーは、Linux ホストでのみ実行できます。 ただし、最近のバージョンの Windows Server と HYPER-V コンテナーでは、Linux コンテナーも実行できますネイティブ Windows Server では現在、Windows Server コンテナーでのみ使用する HYPER-V の分離テクノロジを使用しています。

近い将来、Linux と Windows の両方のコンテナーが存在する混在環境には、可能であり、一般的なでもがなります。

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>既存の .NET アプリケーションの Windows コンテナーの利点

Windows コンテナーを使用する利点は基本的には同様の利点が一般にコンテナーから取得します。 Windows コンテナーを使用するには、アジリティ、移植性、および制御が大幅に向上に関するです。

既存の .NET アプリケーションでは、.NET Framework を使用して作成されたこれらのアプリケーションを参照してください。 たとえば、従来の ASP.NET web アプリケーションがあります-新しいしてプラットフォーム間を実行する .NET Core を使用していない Linux、Windows、および MacOS にします。

.NET Framework の主要な依存関係は、Windows です。 従来の ASP.NET では、IIS、および System.Web のように、セカンダリの依存関係もあります。

.NET Framework アプリケーションを Windows では、期間実行する必要があります。 既存の .NET Framework アプリケーションを containerize するかどうかとできないか、.NET Core への移行に投資する必要のない唯一の選択肢でのコンテナーがある場合は、Windows コンテナーを使用する ("場合は正常に動作しないこと") を移行します。

したがって、Windows コンテナーの主な利点の 1 つを発揮するコンテナリゼーション Windows 経由で実行されている既存の .NET Framework アプリケーションを最新化する方法です。 最終的には、Windows コンテナーを取得するコンテナー アジリティ、移植性、および制御を強化を使用して、探している利点です。

## <a name="choose-an-os-to-target-with-net-based-containers"></a>ターゲットに OS を選択します。NET ベースのコンテナー

.NET Framework と .NET Core の違いと同様に Docker、によってサポートされているオペレーティング システムの多様性を指定するには、特定の OS とを使用しているフレームワークに基づいて特定のバージョンをターゲットする必要があります。

Windows の場合、Windows Server Core または Windows Nano Server を使用できます。 これらのバージョンの Windows には、.NET Framework または .NET Core アプリケーションによって必要になる可能性があります (Kestrel と同様に、自己ホスト型の web サーバーと IIS) などの別の特性が実現します。

Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。

図 4-7 は、.NET Framework のアプリのバージョンによっては、対象できます OS バージョンを示しています。

![](./media/image7.png)

> **図 4 ~ 7 です。** .NET Framework のバージョンに基づき、ターゲットのオペレーティング システム

.NET Framework アプリケーションに基づく既存または従来のアプリケーションの移行のシナリオでは、メインの依存関係が、Windows と IIS でします。 唯一のオプションでは、Windows Server Core と .NET Framework に基づいた Docker イメージを使用します。

Dockerfile は、ファイルをイメージ名を追加する場合は、.NET Framework ベースの Windows コンテナー イメージの次の例のように、タグを使用して、オペレーティング システムとバージョンを選択できます。

> | **タグ** | **システムとバージョン** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | .NET framework 4.x を Windows Server Core |
> | **microsoft/aspnet:4.x-windowsservercore** | .NET framework 4.x で Windows Server Core での他の ASP.NET カスタマイズ |

.NET core (Linux と Windows はクロス プラットフォーム)、タグは、次のようになります。

> | **タグ** | **システムとバージョン**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 Linux 上のランタイムのみ |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 Windows Nano Server でのランタイムのみ |

### <a name="multi-arch-images"></a>マルチ arch イメージ

2017 中旬以降、使うこともできます、新しい機能と呼ばれる Docker で[マルチ arch](https://github.com/moby/moby/issues/15866)イメージ。 .NET core Docker イメージは、マルチ arch タグを使用できます。 Dockerfile ファイルを対象となるオペレーティング システムを定義する必要が不要になった。 マルチ arch 機能は、複数コンピューター構成で使用する 1 つのタグを使用します。 たとえば、複数のアーキテクチャでは、1 つの共通タグ使用できます: **microsoft/dotnet:2.0.0-runtime**です。 Linux コンテナー環境からそのタグをプルする場合は、Debian ベースのイメージを取得します。 Windows コンテナー環境からそのタグをプルする場合は、Nano Server ベースのイメージを取得します。

.NET Framework のイメージ、従来の .NET Framework は、Windows のみをサポートしているためには、マルチ arch 機能を使用することはできません。

## <a name="windows-container-types"></a>Windows コンテナーの種類

Linux コンテナーと同様に Windows Server コンテナーは、Docker エンジンを使用して管理されます。 Linux コンテナーとは異なりは、Windows コンテナーは、次の 2 つの異なるコンテナー型を含めるか、回数-Windows Server コンテナーと HYPER-V の分離を実行します。

**Windows Server コンテナー**: プロセスと名前空間の分離テクノロジを使用してアプリケーションの分離を提供します。 Windows Server コンテナーは、コンテナー ホストとホストで実行されているすべてのコンテナーとカーネルを共有します。 これらのコンテナーでは、悪意のあるセキュリティの境界を指定しないと、信頼されていないコードを分離は使用できません。 これらのコンテナーでは、共有カーネル領域がないため、同じカーネルのバージョンと構成が必要です。

**HYPER-V 分離**: 各コンテナーを大幅に最適化された VM で実行して Windows Server コンテナーによって提供される分離を展開します。 この構成では、コンテナー ホストのカーネルは、同じホスト上の他のコンテナーとは共有されません。 これらのコンテナーは、悪意のあるマルチ テナントをホストするため、VM の同様のセキュリティ保証と設計されています。 これらのコンテナーは、ホストまたはホスト上の他のコンテナーで、カーネルを共有しないするためのカーネル異なるバージョン (サポートされているバージョン) の構成を実行できます。 たとえば、Windows 10 上のすべての Windows コンテナーは、Windows Server カーネルのバージョンと構成を利用するのに HYPER-V 分離を使用します。

HYPER-V 分離の有無は、windows コンテナーを実行すると、実行時の意思決定です。 最初に、HYPER-V の分離を使用したコンテナーの作成を選択し、実行時に、代わりに、Windows Server のコンテナーとして実行を選択する可能性があります。

### <a name="additional-resources"></a>その他の技術情報

-   **Windows コンテナーのドキュメント**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Windows コンテナーの基礎**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **インフォ グラフィック: Microsoft とコンテナー**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)


## <a name="the-container-ecosystem-in-azure"></a>Azure でコンテナーのエコシステム

前のセクションで説明しましただけでなく、特定のコンテナー イメージは、.NET アプリケーションの詳細については Docker コンテナーの利点があります。 すべての一般的な情報については、開発またはアプリケーションを containerize するために不可欠です。
ただし、運用配置環境または QA および開発/テスト環境であっても、検討するとき、Microsoft Azure は、開かれていて、広範なさまざまな選択肢、(次の図に示すように) クラウドで完全コンテナーのエコシステムを提供します。 特定のアプリケーションのニーズに応じて、1 つまたは別の Azure 製品を選択してください。

![](./media/image7.5.png)

> **図 4-7.5 です。** Azure でコンテナーのエコシステム

Azure では、次の製品のインフラストラクチャと見なされるコンテナーをサポートするコンテナーのエコシステム: から
-   **Azure のコンテナー インスタンス (ACI)**
-   **Azure の仮想マシン**(のコンテナーのサポート)
-   **Azure の仮想マシン スケール セット**(のコンテナーのサポート)

これら 3 つから ACI は非常に大きな利点、これは、基になる OS をする必要もありませんアップグレード/修正プログラムなどを維持する必要はありませんが、ACI まだが配置されているより適切にこのブックの今後のセクションで説明されていると、インフラストラクチャ レベルのファクトを提供します。

レベルは、PaaS (サービスとしてのプラットフォーム) 内で複数の配置、同時に Azure のサポートのコンテナーでは、製品は次のとおりです。

-   **Azure App Service**
-   **Azure の Kubernetes サービス (AKS と ACS)**
-   **Azure Service Fabric** 
-   **Azure Batch** 

次に、Azure コンテナー レジストリは、すべての以前の製品を登録して、カスタム コンテナー イメージを展開するときに使用できる Azure でホストされる高のスケーラブルなコンテナー レジストリがします。

さらに、コンテナーから使用できる他のマネージ サービスなどの Azure SQL Database、Azure Redis キャッシュでは、Azure Cosmos DB などの Azure でします。 さらに、サード パーティ製のソリューション/プラットフォームでは Azure Marketplace クラウド Foundry など OpenShift Azure 内のコンテナーも使用できます。 

次のセクションでは、特に Windows コンテナーを対象とするときに、それらの Azure の製品やソリューションの各を使用する場合の Microsoft の推奨事項を調べることができます。


>[!div class="step-by-step"]
[前へ](what-about-cloud-native-applications.md)
[次へ](when-not-to-deploy-to-windows-containers.md)
