---
title: "Docker とは何ですか。"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 7b429f84f7714454d49be1cfa4f450d99fc47f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="what-is-docker"></a>Docker とは何ですか。

[Docker](https://www.docker.com/)は、[オープン ソース プロジェクト](https://github.com/docker/docker)クラウドまたは内部設置型で実行でき、移植可能で自分のコンテナーとしてのアプリケーションの展開を自動化するため (を参照してください図 1-2)。 Docker はでも、[会社](https://www.docker.com/)を昇格し、このテクノロジは、クラウド、Linux、およびなどの Microsoft Windows ベンダーと共同で作業を開発します。

![](./media/image2.png)

図 1-2: ハイブリッド クラウドのすべてのレイヤーでコンテナーを展開する Docker

Docker イメージ コンテナーは、Linux と Windows 上でネイティブに実行できます。 ただし、Windows イメージは Windows ホストでのみ実行できます、Linux のイメージは、Linux、ホスト、ホスト サーバーまたは VM でのみ実行できます。

開発者は、Windows、Linux、または macOS を開発環境を使用することができます。 開発用コンピューターでは、開発者は、どの Docker イメージが展開、アプリとその依存関係を含む Docker ホストを実行します。 Linux または Mac で作業する開発者は、Linux ベース、Docker ホストを使用して、Linux コンテナーにのみイメージを作成することができます。 (Mac で作業する開発者はコードを編集したり、Docker コマンド ライン インターフェイスを実行\[CLI\]から macOS などが、このドキュメントの作成時点で、コンテナーが macOS 上で直接実行しないでください)。Windows で作業する開発者は、Linux または Windows コンテナーのいずれかのイメージを作成できます。

Docker が付属する開発環境でコンテナーをホストし、その他の開発者向けのツールを提供、 [Docker Community Edition (CE)](https://www.docker.com/community-edition) Windows または macOS です。 これらの製品では、必要な VM のコンテナーをホストする (、Docker ホスト) をインストールします。 Docker も使用できるように[Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition)エンタープライズ開発のために設計されていますが、IT チームがビルドによって使用されますが、出荷、および実稼働環境で大規模な基幹業務アプリケーションを実行します。

実行する[Windows コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)ランタイムの 2 種類があります。

-   **Windows Server コンテナー** このランタイムには、プロセスと名前空間の分離テクノロジによる分離をアプリケーションが用意されています。 Windows Server コンテナーは、コンテナー ホストとホストで実行されているすべてのコンテナーに、カーネルを共有します。

-   **HYPER-V コンテナー** で各コンテナーを大幅に最適化された VM で実行されている Windows Server コンテナーによって提供される分離性を展開します。 コンテナーでは、HYPER-V、分離性を提供することは、この構成では、コンテナー ホストのカーネルを共有されません。

これらのコンテナーのイメージは同じ方法で作成され、同じように機能します。 イメージからコンテナーを作成する方法に違いが、HYPER-V コンテナーの実行で追加のパラメーターが必要です。 詳細については、「 [Hyper-v コンテナー](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)です。

## <a name="comparing-docker-containers-with-vms"></a>Vm での Docker コンテナーの比較

図 1-3 の Vm と Docker の比較を表示するコンテナーです。

コンテナーがはるかに少ないリソースを必要とするため (たとえば、する必要はありません、完全な OS)、簡単に展開され、高速が開始します。 これにより、密度の高い、コストを減らす、ハードウェアの同じ単位でより多くのサービスを実行できることを意味することです。

同じカーネルを実行する副作用として Vm よりも低い分離を実現します。

イメージの主な目的は、することが環境 (依存関係) 同じ上でさまざまな展開です。 つまり、コンピューターにデバッグおよび保証同じ環境内の別のコンピューターに展開できます。

コンテナー イメージは、アプリやサービスをパッケージ化し、信頼性が高く、再現可能な方法で展開する方法です。 この点で、Docker は、テクノロジだけではありませんも理念され、処理します。

Docker を使用する場合と開発者を聞くことができません () で"、私のコンピューターしないのはなぜ実稼働環境でですか?" できます単に言われるように、「で実行される Docker、」Docker のパッケージ化されたアプリケーションは、サポートされている Docker 環境で実行でき、すべての配置先 (Dev、QA、ステージング、運用環境などです。) 上に意図された方法を実行するためです。

![](./media/image3.png)

Docker コンテナーへの従来の仮想マシンの図 1-3: 比較


>[!div class="step-by-step"]
[前](index.md) [次へ] (docker terminology.md)
