---
title: "Docker の用語集"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker の用語集"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 885b1fbd3369dec54ebde21a5378630c764f852d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="docker-terminology"></a>Docker の用語集

このセクションでは、用語と定義する必要があります慣れて Docker に深くを取得する前に一覧表示します。 さらに、定義を参照してください、広範な[用語集](https://docs.docker.com/v1.11/engine/reference/glossary/)Docker によって提供されます。

**コンテナー イメージ**: すべての依存関係とコンテナーを作成するために必要な情報を含むパッケージ。 イメージには、さらに、コンテナー ランタイムを使用する展開および実行の構成 (フレームワーク) などのすべての依存関係が含まれています。 通常、イメージは、コンテナーのファイルシステムをフォームに相互に積み重ねられたレイヤーは、複数の基本イメージから派生します。 作成した後は、イメージを変更できません。

**コンテナー**: Docker のイメージのインスタンス。 コンテナーでは、1 つのアプリケーション、プロセス、またはサービスの実行を表します。 Docker イメージや実行環境では、標準的な一連の命令の内容で構成されます。 サービスを拡張するときに、同じイメージからコンテナーの複数のインスタンスを作成します。 または、バッチ ジョブは、インスタンスごとに異なるパラメーターを渡す、同じイメージから複数のコンテナーを作成できます。

**タグ**: マークまたはラベルのさまざまなイメージまたは (バージョン番号または対象となる環境) に応じて、同じイメージのバージョンを識別できるように、イメージに適用することができます。

**Dockerfile**: Docker のイメージを構築するための手順を含むテキスト ファイルです。

**ビルド**: 情報と、Dockerfile とイメージが構成されているフォルダーに追加のファイルによって提供されるコンテキストに基づいて、コンテナー イメージの構築のアクション。 Docker docker ビルド コマンドを使用してイメージを構築できます。

**リポジトリ (リポジトリ)**: イメージのバージョンを示すタグが付いた関連の Docker イメージのコレクション。 いくつかのリポジトリには (高い負荷に対応)、Sdk のみランタイム (明るい) を含むイメージを含むイメージなどなどの特定のイメージの複数のバリエーションが含まれます。これらのバリアントは、タグでマークされたことができます。 1 つのリポジトリには、Linux イメージと Windows イメージなどのプラットフォームのバリエーションを含めることができます。

**レジストリ**: リポジトリへのアクセスを提供するサービスです。 一般的なイメージの既定のレジストリが[Docker Hub](https://hub.docker.com/) (組織として Docker によって所有されている)。 通常、レジストリには、複数のチームからのリポジトリが含まれます。 企業には、多くの場合、プライベート レジストリに格納され、自身で作成したイメージの管理があります。 Azure にコンテナー レジストリは、別の例を示します。

**Docker Hub**: イメージをアップロードし、それと連動するパブリック レジストリです。 Docker Hub は、Docker イメージをホストしている、パブリックまたはプライベート レジストリ、ビルド トリガーと web フック、および GitHub や Bitbucket との統合を提供します。

**Azure にコンテナー レジストリ**: Docker images と Azure では、そのコンポーネントを操作するためのパブリック リソース。 これにより、レジストリで、Azure でデプロイの近くにあるし、アクセスできるように経由でのコントロールを提供する、Azure Active Directory グループとアクセス許可を使用します。

**Docker 信頼されたレジストリ (DTR)**: A Docker レジストリからサービスを (Docker) ことができるに内部設置型がインストールされている場合、組織のデータ センターとネットワーク内で存在するようにします。 プライベート イメージの場合、企業内で管理する必要があると便利です。 Docker Trusted Registry は Docker のデータ センターの製品の一部として含めるです。 詳細については、次を参照してください。 [Docker 信頼されたレジストリ (DTR)](https://docs.docker.com/docker-trusted-registry/overview/)です。

**Docker Community Edition (CE)**: Windows および macOS 構築、実行、およびコンテナーをローカルのテストのための開発ツールです。 Docker for Windows CE では、Linux と Windows コンテナーの両方の開発環境を提供します。 Windows 上の Linux Docker ホストの電源がに基づいて、 [HYPER-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx)仮想マシン。 Windows コンテナーのホストは、Windows に直接基づいています。 Mac 用 docker CE は、Apple ハイパーバイザー フレームワークに基づいて、 [xhyve ハイパーバイザー](https://github.com/mist64/xhyve)、Docker ツールボックスは、Oracle に基づいていましたが置き換えられます Linux Docker ホストの仮想マシンは、Mac OS x. Docker CE for Windows と Mac を提供VirtualBox です。

**Docker の Enterprise Edition (EE)**: エンタープライズ規模のバージョンの Linux と Windows 開発用の Docker ツールです。

**作成**: コマンド ライン ツールと YAML ファイルを定義するアプリケーションおよび実行する複数のコンテナーのメタデータの形式です。 環境によっての値をオーバーライドできる 1 つまたは複数の .yml ファイルで複数のイメージに基づく 1 つのアプリケーションを定義します。 単一のコマンドでマルチ コンテナー全体のアプリケーションを配置するには、定義を作成した後 (docker-を作成)、Docker ホストにイメージごとのコンテナーを作成します。

**クラスター**: アプリケーションは、サービスの複数のインスタンスに拡張できるように 1 つの仮想 Docker ホストの場合と同様に公開される Docker ホストのコレクションが、クラスター内の複数のホストに分散します。 Docker Swarm、続き DC/OS、Kubernetes、および Azure Service Fabric では、docker のクラスターを作成できます。 (通常、クラスターを参照してください、クラスターの管理に Docker Swarm を使用する場合、 *swarm*クラスターではなくです)。

**Orchestrator**: クラスターと Docker ホストの管理を簡略化するツールです。 Orchestrators を使用すると、そのイメージ、コンテナー、およびコマンド ライン インターフェイス (CLI) を使用してホストを管理またはグラフィカルな UI。 コンテナーのネットワーク、構成、負荷分散、サービスの検出、高可用性、Docker ホストの構成、および詳細を管理することができます。 オーケストレーターを実行して、配布、スケール、およびノードのコレクション全体でワークロードを修復します。 通常は、orchestrator 製品は、続き DC/OS、Kubernetes、Docker Swarm、および Azure Service Fabric のように、クラスターのインフラストラクチャを提供する同じ製品です。


>[!div class="step-by-step"]
[前](docker defined.md) [次へ] (docker でコンテナーのイメージ-registries.md)
