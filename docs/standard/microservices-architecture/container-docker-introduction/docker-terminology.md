---
title: Docker に関する用語
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Docker 用語
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bbeff8c467e762e682fdaf99c8a11851b291db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="docker-terminology"></a>Docker に関する用語

このセクションでは、Docker を深く掘り下げて検討する前に、理解しておく必要がある用語と定義を一覧表示します。 その他の定義については、Docker によって提供されている広範囲にわたる[用語集](https://docs.docker.com/glossary/)を参照してください。

**コンテナー イメージ**: コンテナーを作成するために必要なすべての依存関係と情報を含むパッケージです。 イメージには、すべての依存関係 (フレームワークなど) に加えて、コンテナー ランタイムによって使用される展開および実行の構成が含まれています。 通常、イメージはコンテナーのファイルシステムを形成するために相互に積み重ねられたレイヤーである複数の基本イメージから派生します。 イメージは一旦作成されると変更できません。

**コンテナー**: Docker イメージのインスタンスです。 コンテナーは、単一のアプリケーション、プロセス、またはサービスの実行を表します。 Docker イメージのコンテンツ、実行環境、および標準的な命令セットで構成されます。 サービスを拡大縮小する場合は、同じイメージからコンテナーの複数のインスタンスを作成します。 または、バッチ ジョブで同じイメージから複数のコンテナーを作成し、各インスタンスにそれぞれ異なるパラメーターを渡します。

**タグ**: 各種イメージまたは同じイメージの各種バージョン (バージョン番号または対象となる環境に応じて異なる) を識別できるように、イメージに適用できるマークまたはラベルです。

**Dockerfile**: Docker イメージをビルドする方法の手順が含まれるテキスト ファイルです。

**ビルド**: Dockerfile によって提供される情報とコンテキストに加えて、イメージがビルドされるフォルダー内の追加のファイルに基づいてコンテナー イメージをビルドするアクションです。 Docker の docker build コマンドを使用してイメージをビルドできます。

**リポジトリ**: 関連する Docker イメージのコレクションであり、イメージのバージョンを示すタグでラベル付けされています。 一部のリポジトリには、特定のイメージのバリアントが複数含まれています。たとえば、SDK を含むイメージ (重い) やランタイムのみを含むイメージ (軽い) などが該当します。そのようなバリアントは、タグでマーク付けすることができます。 単一のリポジトリには、Linux イメージや Windows イメージなどのプラットフォーム バリアントを含めることができます。

**レジストリ**: リポジトリへのアクセス権を提供するサービスです。 ほとんどのパブリック イメージの既定のレジストリは [Docker Hub](https://hub.docker.com/) です (Docker によって組織として所有されている)。 レジストリには、通常、複数のチームからのリポジトリが含まれています。 企業は、多くの場合、自社で作成したイメージを格納および管理するためのプライベート レジストリを持っています。 Azure Container Registry は別の例となります。

**Docker Hub**: イメージをアップロードし、それらを操作するパブリック レジストリです。 Docker Hub は、Docker イメージ ホスティング、パブリックまたはプライベート レジストリ、ビルド トリガーおよび Web フック、さらに GitHub および Bitbucket との統合を提供します。

**Azure コンテナー レジストリ**: Azure 内で Docker イメージとそのコンポーネントを操作するためのパブリック リソースです。 これは、Azure で利用しているデプロイに近く、アクセスに対する制御権を付与するレジストリです。これにより、Azure Active Directory のグループとアクセス許可が使用できるようになります。

**Docker Trusted Registry (DTR)**: 組織のデータ センターやネットワーク内で有効になるようにオンプレミスにインストール可能な Docker レジストリ サービス (Docker からの) です。 企業内で管理する必要があるプライベート イメージにおいて便利です。 Docker Trusted Registry は Docker Datacenter 製品の一部として含められています。 詳細については、[Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/) に関するページを参照してください。

**Docker Community Edition (CE)**: コンテナーをローカルにビルド、実行、およびテストのための Windows および macOS 用の開発ツールです。 Docker for Windows CE は、Linux コンテナーと Windows コンテナーの両方に開発環境を提供します。 Windows 上の Linux Docker ホストは、[Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) 仮想マシンをベースにしています。 Windows コンテナーのホストは、Windows に直接基づいています。 Docker CE for Mac は、Apple Hypervisor フレームワークと [xhyve ハイパーバイザー](https://github.com/mist64/xhyve) (Mac OS X 上で Linux Docker ホスト仮想マシンを提供する) に基づいています。Docker CE for Windows と Docker CE for Mac は、Oracle VirtualBox に基づく Docker Toolbox に取って代わります。

**Docker Enterprise Edition (EE)**: Linux および Windows 開発用の Docker ツールのエンタープライズ規模のバージョンです。

**Compose**: 複数コンテナーのアプリケーションを定義および実行するためのメタデータを持つコマンドライン ツールと YAML ファイル形式です。 複数のイメージに基づく単一のアプリケーションを定義するには、環境に応じて値をオーバーライドできる 1 つまたは複数の .yml ファイルを使用します。 定義を作成したら、Docker ホスト上でイメージごとにコンテナーを作成する単一コマンド (docker-compose up) を使用して複数コンテナーのアプリケーション全体を展開することができます。

**クラスター**: クラスター内の複数のホストに分散されたサービスの複数のインスタンスに対応できるように、単一の仮想 Docker ホストであるかのように公開された Docker ホストのコレクションです。 Docker クラスターは、Docker Swarm、Mesosphere DC/OS、Kubernetes、Azure Service Fabric を使用して作成できます  (クラスターを管理するために Docker Swarm を使用する場合、通常はそのクラスターをクラスターとしてではなく "*スウォーム*" として参照します)。

**Orchestrator**: クラスターと Docker ホストの管理を簡略化するツールです。 Orchestrator を使用すると、そのイメージ、コンテナー、およびホストをコマンド ライン インターフェイス (CLI) またはグラフィカル UI を介して管理することができます。 コンテナー ネットワーク、構成、負荷分散、サービス検出、高可用性、Docker ホストの構成などを管理することができます。 オーケストレーターは、ノードのコレクション全体にわたりワークロードの実行、配布、スケーリング、修復を担当します。 通常、オーケストレーター製品は、Mesosphere DC/OS、Kubernetes、Docker Swarm、Azure Service Fabric などのクラスター インフラストラクチャを提供する製品です。


>[!div class="step-by-step"]
[Previous] (docker-defined.md) [Next] (docker-containers-images-registries.md)
