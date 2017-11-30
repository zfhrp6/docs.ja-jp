---
title: "公式の .NET Docker イメージ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |公式の .NET Docker イメージ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6f14bd0cf55a552f3881d755ebe7389f000975d8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="official-net-docker-images"></a>公式の .NET Docker イメージ

公式の .NET Docker イメージは、Microsoft を作成、最適化の Docker イメージです。 上の Microsoft リポジトリに公開されている[Docker Hub](https://hub.docker.com/u/microsoft/)です。 各リポジトリには、.NET のバージョンと、OS と (Linux Debian、Alpine Linux、Windows Nano Server、Windows Server Core など) のバージョンによって、複数のイメージを含めることができます。

.NET リポジトリ用の Microsoft のビジョンには詳細な焦点を当てておりのリポジトリをリポジトリが特定のシナリオやワークロードを表します。 インスタンス、 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)開始時間を短縮それら ASP.NET Core のイメージは、さらに最適化はコンテナーを提供するため、Docker で ASP.NET Core を使用するときに、イメージを使用する必要があります。

その一方で、.NET Core イメージ (microsoft/dotnet) は、.NET Core に基づいてコンソール アプリを意図しています。 たとえば、バッチ処理、Azure web ジョブ、およびその他のコンソール シナリオは、.NET Core を使用する必要があります。 それらのイメージでは、小さいコンテナーのイメージの結果として得られる、ASP.NET Core スタックは含まれません。

ほとんどのイメージ リポジトリは、だけでなく、特定のフレームワークのバージョンを選択するため、OS (Linux ディストリビューションまたは Windows のバージョン) を選択にも、広範なタグ付けを提供します。

Microsoft が提供する公式 .NET Docker イメージの詳細については、次を参照してください。、 [.NET Docker Images 概要](https://aka.ms/dotnetdockerimages)です。

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core と Docker のイメージの運用と開発のための最適化

開発者向けの Docker イメージを構築するときに、Microsoft は、次の主なシナリオでフォーカスしています。

-   使用するイメージ*開発*と .NET Core アプリをビルドします。

-   使用するイメージ*実行*.NET Core アプリ。

なぜ複数のイメージですか? 開発、構築、およびコンテナー化アプリケーションを実行している、ときに、通常優先度が異なる必要があります。 これら個別のタスク、さまざまなイメージを提供することによっては、Microsoft は、開発、構築、およびアプリの展開の個別のプロセスを最適化することができます。

### <a name="during-development-and-build"></a>開発およびビルド中には

開発中は、重要な点はどの程度の速度を繰り返し処理できる変更、および変更をデバッグする機能です。 イメージのサイズは、コードを変更して、変更をすばやく確認する機能と同じくらい重要ではありません。 一部のツールおよび「ビルド エージェント コンテナー」開発中、の開発 ASP.NET Core のイメージ (microsoft/aspnetcore-ビルド) を使用してとプロセスをビルドします。 Docker コンテナー内のビルド時に重要な側面は、アプリをコンパイルするために必要な要素です。 これには、コンパイラが含まれます、その他の .NET の依存関係に加えて、npm などの web 開発の依存関係 Gulp、Bower です。

この種類のビルド イメージが重要な理由 実稼働環境には、このイメージは展開しません。 代わりに、使用して実稼働のイメージに配置するコンテンツをビルドするイメージを勧めします。 このイメージは、継続的インテグレーション (CI) 環境またはビルド環境で使用されます。 たとえば、ビルド エージェントで直接、すべてのアプリケーションの依存関係を手動でインストールするのではなく VM をホスト (など)、ビルド エージェントは、アプリケーションをビルドするために必要なすべての依存関係を持つ .NET Core ビルド イメージをインスタンス化します。 この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。 これは、CI の環境を簡略化されより予測可能になります。

### <a name="in-production"></a>実稼働環境で

実稼働環境で重要な点は、どの程度の速度を配置して、実稼働 .NET Core イメージに基づいて、コンテナーを開始できます。 したがって、ランタイムのみのイメージがに基づいて[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)は上を移動できます迅速にネットワーク経由で Docker レジストリからの Docker ホストにあるために、小さいです。 内容は、結果を処理するコンテナーの開始から時間が最速の有効化を実行する準備ができています。 モデルでは、Docker、C からのコンパイルの必要はありません\#コードは、そことして、またはその dotnet 発行時に dotnet ビルドを実行するとコンテナーを使用してビルドします。

この最適化されたイメージには、バイナリのみと、アプリケーションを実行するために必要なその他のコンテンツを配置します。 Dotnet で作成されたコンテンツの発行など、コンパイルされた .NET バイナリ、イメージ、.js、および .css ファイルのみが含まれています。 時間の経過と共に、jit のパッケージを含むイメージが表示されます。

.NET Core および ASP.NET Core のイメージの複数のバージョンがありますが、これらはすべて基本レイヤーを含む 1 つまたは複数のレイヤーを共有します。 そのため、イメージの格納に必要なディスク領域量が少ないです。カスタム イメージとその基本画像間のデルタののみで構成されます。 レジストリからイメージをプルする簡単であることになります。

Docker Hub に .NET イメージ リポジトリを探索するときに、分類またはタグでマークされた複数のイメージのバージョンが表示されます。 これらのタグは、使用するにはバージョンによっては、次の表に示すように、必要な決定に役立ちます。

-   microsoft/**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft/**aspnetcore-ビルド: 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[前](net-コンテナーの os-targets.md) [次へ] (../architect-microservice-container-applications/index.md)
