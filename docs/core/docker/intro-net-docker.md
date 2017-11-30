---
title: ".NET と Docker の概要"
description: "Understanding Docker と .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a>.NET と Docker の概要

 この記事では、概要と Docker の .NET を使用する概念の背景を提供します。 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: を展開して任意の場所を実行するアプリをパッケージ化

[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined)をビルドするには、開発者および管理者を有効にするオープン プラットフォームは、[イメージ](https://docs.docker.com/glossary/?term=image)、出荷、およびと呼ばれる疎に分離された環境で分散アプリケーションを実行、[コンテナー](https://www.docker.com/what-container). この方法には、開発、品質保証、および運用環境間で効率的なアプリケーション ライフ サイクル管理ができます。
 
[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)を使用して、 [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)速やかに構築してとしてアプリをパッケージ化[Docker images](https://docs.docker.com/glossary/?term=image)で記述されたファイルを使用して作成された、 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)が展開されているし、で実行する形式、[コンテナー階層化](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)です。

作成することも、独自[画像上層](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)dockerfile または既存のものから使用すると、[レジストリ](https://docs.docker.com/glossary/?term=registry)と同様、 [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub)です。

[Docker コンテナー、画像、およびレジストリの関係](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries)重要な概念と[を設計および構築コンテナー詰めアプリケーションまたは microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/)です。 この方法では、開発と配置までの時間が大幅に短縮されます。

### <a name="further-reading-and-watching"></a>関連項目 (および監視)

* [Windows ベースのコンテナー: エンタープライズ レベルの制御を使用した最新のアプリの開発。](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Docker の概要](https://docs.docker.com/engine/docker-overview/)
* [Windows コンテナー上の Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Dockerfile を記述するためのベスト プラクティス](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [.NET Core アプリケーションの Docker イメージの構築](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>.NET Docker イメージを取得します。

公式の .NET Docker イメージが作成され、Microsoft によって最適化します。 Docker Hub に Microsoft リポジトリにはパブリックに使用です。 各リポジトリには、.NET のバージョンや OS のバージョンに基づいて、複数のイメージを含めることができます。 ほとんどのイメージ リポジトリは、特定のフレームワークのバージョンと OS (Linux ディストリビューションまたは Windows のバージョン) の両方を選択するための広範なタグ付けを提供します。

## <a name="scenario-based-guidance"></a>シナリオ ベースのガイダンス

.NET リポジトリ用の Microsoft の目的は、特定のシナリオやワークロードを表す焦点を当てており、詳細なリポジトリにはします。

`microsoft/aspnetcore`イメージが最適化されているため、Docker に ASP.NET Core アプリケーション コンテナー開始時間を短縮します。

.NET Core イメージ (`microsoft/dotnet`) ベースの .NET Core コンソール アプリを意図しています。 たとえば、バッチ処理、Azure web ジョブ、およびその他のコンソール シナリオは、最適化の .NET Core イメージを使用する必要があります。

Docker と .NET アプリケーションを使用して最もわかりやすいの水平方向のシナリオは運用環境のデプロイとホストです。 結局、運用環境は 1 つのシナリオとその他のものがある均等に便利です。 これらのシナリオでは、.NET に固有ではありませんが、ほとんどの開発者向けプラットフォームに適用する必要があります。

* **低摩擦インストール**— .NET をローカルにインストールせずに試みることができます。 だけで、.NET を使用して Docker イメージをダウンロードします。

* **コンテナーで開発**— (開発者のマシン上のグローバル状態などの問題を回避できます) のような開発および運用環境を作成、一貫性のある環境で開発できます。 Docker 用の visual Studio Tools を Visual Studio から直接、コンテナーを起動することもできます。

* **コンテナーでテスト**: 正しく構成されていない環境による障害を減らすことをコンテナーでテストできますまたはその他の変更が最後のテストから残されました。

* **コンテナーにビルド**— 複数の環境の共有のビルド コンピューターを正しく構成しますが、"BYOC"に移動する代わりにする必要性を回避する、コンテナー内のコードを構築できます (独自のコンテナーを bring) アプローチです。

* **すべての環境で展開**— すべて自分の環境のイメージを展開することができます。 この方法は、通常動作を変更する、イメージ外部構成 (たとえば、挿入された環境変数など) を使用して、構成の違いによるエラーを軽減します。

[一般的なガイダンス](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance)Docker コンテナーの開発の .NET Core と .NET Framework 間を決定するためです。

### <a name="common-docker-development-scenarios"></a>一般的な Docker 開発シナ リオ

#### <a name="net-core"></a>.NET Core

**.NET core リソース**

 関心のある、シナリオに合わせて .NET Core のサンプルを選択します。 すべての手順の例では、Windows、Linux、または macOS ホストからの Windows または Linux Docker のイメージを対象にする方法について説明します。

サンプルは、.NET Core 2.0 を使用します。 Docker を使用している[マルチ ステージのビルド](https://github.com/dotnet/announcements/issues/18)と[マルチ arch タグ](https://github.com/dotnet/announcements/issues/14)適切な場合です。

* [Dockerhub を使用して上の .NET core イメージ](https://hub.docker.com/r/microsoft/dotnet/)

* [.NET Core アプリケーションを dockerize します。](https://docs.docker.com/engine/examples/dotnetcore/)

* この .NET Core Docker がサンプル方法[Docker を使用して、.NET Core 開発工程で](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev)です。 このサンプルは、Linux と Windows の両方のコンテナーで動作します。

* この .NET Core Docker サンプルのベスト プラクティス パターン[実稼働用アプリの .NET Core Docker イメージを構築します。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) このサンプルは、Linux と Windows の両方のコンテナーで動作します。

* これは、 [.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained)用 Docker イメージを構築するためのベスト プラクティス パターンを示します[自己完結型の .NET Core アプリケーション](https://docs.microsoft.com/dotnet/core/deploying/)です。 利点も最小運用コンテナーの使用[コンテナー間での基本イメージを共有](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/)です。 ただし、Docker の下位のレイヤーを共有する可能性があります。

#### <a name="arm32--raspberry-pi"></a>ARM32 Raspberry π/

* [.NET core ランタイム ARM32 ビルド アナウンス](https://github.com/dotnet/announcements/issues/29)

* [ARM32 Raspberry Pi .NET Core のイメージ DockerHub に/](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 Raspberry Pi .NET Core Docker サンプル GitHub を/](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Dockerhub を使用して上の .NET framework イメージ](https://hub.docker.com/r/microsoft/dotnet-framework/)このリポジトリにはさまざまな .NET Framework の Docker 構成を示すサンプルが含まれています。 これらのイメージは、独自の Docker イメージのベースとして使用できます。

**.NET framework 4.7**

[、 [Dotnet-フレームワーク: 4.7 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7)の基本的な"hello world"の使用を示します、 [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47)です。 作成および証明書利用者アプリケーションを配置する方法を示します、 [.NET Framework 4.7 docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile)です。

**.NET framework 4.6.2**

[Dotnet-フレームワーク: 4.6.2 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2)の基本的な"hello world"の使用を示します、 [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462)です。 作成および証明書利用者アプリケーションを配置する方法を示します、 [.NET Framework 4.6.2 docker イメージ](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2)です。

**.NET framework 3.5**

 [Dotnet-framework: 3.5 サンプル](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5)の基本的な"hello world"の使用を示します[.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5)です。 ビルドし、Docker で .NET Framework 3.5 に依存するプロジェクトを配置する方法を示します。

#### <a name="aspnet-core"></a>ASP.NET Core

* [この ASP.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)ASP.NET Core 実稼働環境用のアプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。 このサンプルは、Linux と Windows の両方のコンテナーで動作します。

* [Dockerhub を使用して上の ASP.NET Core イメージ](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [GitHub 上の ASP.NET Core イメージ](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET フレームワーク 

* [Dockerhub を使用して上の ASP.NET フレームワークの画像](https://hub.docker.com/r/microsoft/aspnet/)

* [.NET Framework 4.6.2 サンプルの ASP.NET Web フォーム アプリケーション](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Dockerhub を使用して上の Windows Communication Framework (WCF) イメージ](https://hub.docker.com/r/microsoft/wcf/)

* [GitHub の Windows Communication Framework (WCF) イメージ](https://github.com/microsoft/iis-docker)

* [.NET Framework 4.6.2 完全を使用する Windows Communication Framework (WCF) Docker サンプル](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>インターネット インフォメーション サービス (IIS)

* [DockerHub にインターネット インフォメーション サーバー (IIS) のイメージ](https://hub.docker.com/r/microsoft/iis/)

* [GitHub 上のインターネット インフォメーション サーバー (IIS) の画像](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>その他の Microsoft スタック コンテナー イメージとの対話します。

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Docker クイック スタートで Linux 2017 コンテナー イメージが、Microsoft SQL Server を実行します。](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Linux イメージ dockerhub を使用して Microsoft SQL Server](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Dockerhub を使用して上の Microsoft SQL Server の Windows コンテナー イメージ](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Dockerhub を使用して上の Windows コンテナー用の Microsoft SQL Server Express Edition イメージ](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Dockerhub を使用して上の Windows コンテナー用の Microsoft SQL Server Developer Edition イメージ](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Visual Studio Team Services (VSTS) エージェント

* [Dockerhub を使用して visual Studio Team Services (VSTS) エージェントをイメージ](https://hub.docker.com/r/microsoft/vsts-agent/)

* [GitHub 上の visual Studio Team Services (VSTS) エージェント イメージ](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Operations Management Suite (OMS) Linux エージェント

* [Operations Management Suite (OMS) Linux エージェントの概要](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [DockerHub に operations Management Suite (OMS) のイメージ](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [GitHub で operations Management Suite (OMS) のイメージ](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Microsoft Azure コマンド ライン インターフェイス (CLI)

* [Dockerhub を使用して上の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ](Docker image for Microsoft Azure Command Line Interface) 

* [GitHub の Microsoft Azure コマンド ライン インターフェイス (CLI) イメージ](https://github.com/Microsoft/OMS-docker)

> [!Note]
> Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Microsoft Azure Cosmos DB エミュレーター (Windows コンテナーのみ)

* [Dockerhub を使用して上の Microsoft Azure Cosmos DB エミュレーター イメージ](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [ローカルの開発およびテスト用 Azure Cosmos DB エミュレーターの使用](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>豊富な Docker 開発エコシステムを調べる

Docker プラットフォームとさまざまな Docker イメージについて説明しましたが、これで、次の手順では、豊富な Docker エコシステムを調査します。 次のリンクは、Microsoft のツールがコンテナーの開発を補完する方法を示します。

* [.NET と Docker の併用](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [デザインおよび複数のコンテナーおよびマイクロ サービス ベースの .NET アプリケーションを開発します。](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [Visual Studio コード Docker 拡張機能](https://code.visualstudio.com/docs/languages/dockerfile) 
* [Azure Service Fabric を使用する方法をについてください。](https://docs.microsoft.com/azure/service-fabric/) 
* [Service Fabric 作業の開始サンプル](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Windows コンテナーの利点](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [Visual Studio Docker ツールの使用](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio のコードでデバッグ](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [手 Visual Studio での取得 Mac、コンテナー、およびサーバーなしのコード、クラウド内](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac のラボの Docker と Visual Studio の概要](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>次の手順

* [.NET Core と Docker を基礎します。](../docker/docker-basics-dotnet-core.md)
* [.NET Core Docker イメージを構築します。](../docker/building-net-docker-images)