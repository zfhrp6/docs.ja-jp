---
title: Docker に関する用語
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 0b13f28f4314ef72fbcaffe894bf823486665d3f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106098"
---
# <a name="docker-terminology"></a>Docker に関する用語

用語と定義する必要がありますを理解しておく Docker を深く掘り下げる前に、このセクションの内容が一覧表示 (さらに、定義を参照してください、広範な[用語集](https://docs.docker.com/glossary/)に Docker によって提供される<https://docs.docker.com/glossary/>:

-   **コンテナー イメージ** すべての依存関係とコンテナーを作成するために必要な情報を使用してパッケージです。 イメージには、すべての (フレームワーク) などの依存関係との展開とコンテナー ランタイムを使用する構成が含まれています。 通常、イメージから派生する複数の基本イメージをレイヤー積み重ねられて、コンテナーのファイル システムを形成する他の上に 1 つ。 作成した後は、イメージを変更できません。

-   **コンテナー** Docker イメージのインスタンス。 コンテナーでは、1 つのアプリケーション、プロセス、またはサービス用のランタイムを表します。 Docker イメージ、ランタイム環境、および標準的な一連の命令の内容で構成されます。 サービスを拡大縮小する場合は、同じイメージからコンテナーの複数のインスタンスを作成します。 または、バッチ ジョブは、インスタンスごとに異なるパラメーターを渡す、同じイメージから複数のコンテナーを作成できます。

-   **タグ** マークまたはラベルをさまざまなイメージまたは (バージョン番号、送信先の環境に応じて) 同じイメージのバージョンを識別できるように、イメージに適用することができます。

-   **Dockerfile** Docker イメージを構築するための手順を含むテキスト ファイルです。

-   **ビルド** 情報とその Dockerfile だけでなく、イメージが構成されているフォルダーに追加のファイルによって提供されるコンテキストに基づいて、コンテナー イメージの構築のアクション。 Docker docker ビルド コマンドを使用してイメージを構築できます。

-   **リポジトリ (リポジトリとも呼ばれます)** イメージのバージョンを示すタグが付いた関連の Docker イメージのコレクション。 いくつかのリポジトリは (高い負荷に対応)、Sdk (明るい) ランタイムのみを含むイメージを含むイメージなどの特定のイメージの複数のバリエーションを含めるようにします。 そのようなバリアントは、タグでマーク付けすることができます。 1 つのリポジトリには、Linux イメージと Windows イメージなどのプラットフォームのバリエーションを含めることができます。

-   **レジストリ** リポジトリへのアクセスを提供するサービスです。 ほとんどのパブリック イメージの既定のレジストリは [Docker Hub](https://hub.docker.com/) です (Docker によって組織として所有されている)。 レジストリには、通常、複数のチームからのリポジトリが含まれています。 企業には、多くの場合、プライベート レジストリに格納され、自身で作成したイメージの管理があります。 *Azure にコンテナー レジストリ*別の例を示します。

-   **Docker Hub** をパブリック レジストリ イメージをアップロードし、それと連動します。 Docker Hub は、Docker イメージ ホスティング、パブリックまたはプライベート レジストリ、ビルド トリガーおよび Web フック、さらに GitHub および Bitbucket との統合を提供します。

-   **Azure にコンテナー レジストリ** Docker images と Azure では、そのコンポーネントを操作するためのパブリック リソース。 これは、Azure で利用しているデプロイに近く、アクセスに対する制御権を付与するレジストリです。これにより、Azure Active Directory のグループとアクセス許可が使用できるようになります。

-   **Docker 信頼されたレジストリ (DTR)** A Docker レジストリ サービス (から Docker) をインストールすることができます、オンプレミス組織のデータ センターとネットワーク内に存在することができるようにします。 企業内で管理する必要があるプライベート イメージにおいて便利です。 Docker Trusted Registry は Docker Datacenter 製品の一部として含められています。 詳細についてを参照してください[ https://docs.docker.com/docker-trusted-registry/overview/](https://docs.docker.com/docker-trusted-registry/overview/)です。

-   **Docker Community Edition (CE)** Windows や macOS 構築、実行、およびコンテナーをローカルのテストのための開発ツールです。 Docker for Windows CE は、Linux コンテナーと Windows コンテナーの両方に開発環境を提供します。 Windows 上の Linux Docker ホストの電源がに基づいて、 [HYPER-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM です。 Windows コンテナーのホストは、Windows に直接基づいています。 Mac 用 docker CE は、Apple ハイパーバイザー フレームワークに基づいて、 [xhyve ハイパーバイザー](https://github.com/mist64/xhyve)、Oracle VirtualBox を基盤とする Docker ツールボックスが置き換えられます Linux Docker ホスト VM と Mac の Mac OS x. Docker Windows CE を提供します。

-   **Docker の Enterprise Edition (EE)** エンタープライズ規模のバージョンの Linux と Windows 開発用の Docker ツールです。

-   **作成** コマンド ライン ツールと YAML ファイル形式のメタデータを定義および multicontainer アプリケーションを実行するとします。 複数のイメージに基づく単一のアプリケーションを定義するには、環境に応じて値をオーバーライドできる 1 つまたは複数の .yml ファイルを使用します。 1 つのコマンドを使用して multicontainer アプリケーション全体を展開するには、定義を作成した後 (docker-を作成)、Docker ホストにイメージごとのコンテナーを作成します。

-   **クラスター** の Docker ホストの場合と同様、1 つの仮想 Docker ホスト アプリケーションは、サービスの複数のインスタンスに拡張できるように公開されているコレクションは、クラスター内の複数のホストに分散します。 Docker のクラスターを作成するには、Docker Swarm、続き DC/OS、Kubernetes、および Azure Service Fabric を使用します。 (クラスターを管理するために Docker Swarm を使用する場合、通常はそのクラスターをクラスターとしてではなく "*スウォーム*" として参照します)。

-   **Orchestrator** クラスターと Docker ホストの管理を簡略化するツールです。 Orchestrators を使用すると、そのイメージ、コンテナー、および CLI またはグラフィカル ユーザー インターフェイスを介してホストを管理できます。 コンテナー ネットワーク、構成、負荷分散、サービス検出、高可用性、Docker ホストの構成などを管理することができます。 オーケストレーターは、ノードのコレクション全体にわたりワークロードの実行、配布、スケーリング、修復を担当します。 通常、オーケストレーター製品は、Mesosphere DC/OS、Kubernetes、Docker Swarm、Azure Service Fabric などのクラスター インフラストラクチャを提供する製品です。


>[!div class="step-by-step"]
[前へ](what-is-docker.md)
[次へ](docker-containers-images-and-registries.md)
