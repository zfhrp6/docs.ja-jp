---
title: ".NET Core の Docker イメージのビルド"
description: "Docker イメージと .NET Core について"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a>.NET Core アプリケーションの Docker イメージのビルド

 このチュートリアルでは Docker で .NET Core を使用する方法について説明します。 最初に、提供され、Microsoft とユース ケースで保持されているさまざまな Docker イメージをについて説明します。 ビルドし、ASP.NET Core アプリケーションの dockerize 方法を学習します。

このチュートリアルの中には、次の操作を説明します。
> [!div class="checklist"]
> * Microsoft .NET Core Docker イメージについてください。 
> * ASP.NET Core Dockerize するサンプル アプリを取得します。
> * ASP.NET サンプル アプリをローカルで実行します。
> * ビルドおよび Docker を使用した Linux コンテナーのサンプルを実行します。
> * ビルドおよび Docker for Windows コンテナーでサンプルを実行します。

## <a name="docker-image-optimizations"></a>Docker イメージの最適化

開発者向けの Docker イメージをビルドするにあたり、次の主な 3 つのシナリオに重点を置きました。

* .NET Core アプリの開発に使用されるイメージ
* .NET Core アプリのビルドに使用されるイメージ
* .NET Core アプリの実行に使用されるイメージ

3 つのイメージである理由は、
開発、構築、およびコンテナー化アプリケーションを実行している、ときに、異なる優先順位があります。

* **開発:**優先順位について重点的に説明は、変更、および変更をデバッグする機能にすばやく反復処理します。 イメージのサイズが、重要ではないではなくことができます、コードに変更を加えるそれらをすばやく確認しますか。

* **ビルド:**このイメージには、コンパイラとバイナリを最適化するために他の依存関係を含むアプリのコンパイルに必要なすべてが含まれています。  実稼働のイメージに配置する資産を作成するのにビルド イメージを使用するとします。 ビルド イメージが、継続的インテグレーションは、またはビルド環境で使用されます。 これにより、ビルド エージェントをコンパイルし、ビルドの画像インスタンスの (すべての必要な依存関係を持つ) アプリケーションをビルドすることができます。 この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。

* **実稼働:**どの程度の速度を配置して、イメージを起動できますか。 Docker レジストリから Docker ホストのネットワーク パフォーマンスが最適化されたために、このイメージは小さなです。 コンテンツは実行できる状態であるため、Docker の実行から結果の処理までを最速で行うことができます。 動的なコード コンパイル Docker モデルでは必要ありません。 このイメージに配置するコンテンツは、アプリケーションの実行に必要なバイナリとコンテンツに制限されます。

    たとえば、`dotnet publish`出力が含まれます。

    * コンパイル済みバイナリ
    * .js および .css ファイル


含める理由、`dotnet publish`運用イメージのコマンドの出力が保存されますその ' サイズを最小限にします。

一部の画像を .NET Core は、比較的軽量プロセスは、最新のタグをダウンロードするための別のタグの間のレイヤーを共有します。 コンピューターに既に以前のバージョンが場合、このアーキテクチャは、必要なディスク領域を減少します。

複数のアプリケーションでは、一般的なイメージを使用して、同じコンピューター上、ときに、メモリは、共通のイメージの間で共有されます。 イメージは、共有する同じである必要があります。

## <a name="docker-image-variations"></a>Docker イメージのバリエーション

上記の目標を達成するには、するには、イメージのバリエーションを指定お[ `microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/)です。

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) このイメージには、.NET Core およびコマンドライン ツール (CLI) を含む、.NET Core SDK が含まれています。 このイメージは **開発シナリオ** にマップされます。 このイメージを使用して、ローカルの開発、デバッグ、および単体テストをします。 このイメージは、**ビルド** シナリオでも使用できます。 使用して`microsoft/dotnet:sdk`常に最新バージョンを使用します。

> [!TIP]
> 使用する場合、不明なニーズに関する場合、`microsoft/dotnet:<version>-sdk`イメージ。 「事実上」のイメージとして設計となっており、throw として使用する退席中のコンテナー (ソース コードをマウントおよびアプリを起動するコンテナーを起動) と、基本イメージから他のイメージを構築します。

* `microsoft/dotnet:<version>-runtime`: このイメージは、.NET Core (ランタイムおよびライブラリ) が含まれており、で .NET Core アプリを実行するために最適化された**運用**です。

## <a name="alternative-images"></a>その他のイメージ

開発、ビルドおよび実稼働の最適化されたシナリオに加え、次の追加イメージが提供されます。

* `microsoft/dotnet:<version>-runtime-deps`**ランタイム deps**イメージには、すべての .NET Core で必要なネイティブの依存関係と、オペレーティング システムが含まれています。 このイメージは[自己完結型アプリケーション](https://docs.microsoft.com/dotnet/core/deploying/index)です。

各バリアントの最新バージョン:

* `microsoft/dotnet`または`microsoft/dotnet:latest`(SDK のイメージの別名)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>サンプルを探索するには

* [この ASP.NET Core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)ASP.NET Core 実稼働環境用のアプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。 このサンプルは、Linux と Windows の両方のコンテナーで動作します。

* この .NET Core Docker サンプルのベスト プラクティス パターン[実稼働用アプリの .NET Core Docker イメージを構築します。](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>最初の ASP.NET Core Docker アプリ

このチュートリアルでは、dockerize するアプリの ASP.NET Core Docker サンプル アプリケーションを使用することができます。 この ASP.NET Core Docker サンプル アプリケーションでは、実稼働環境用のアプリを ASP.NET Core 用 Docker イメージを構築するためのベスト プラクティス パターンを示します。 このサンプルは、Linux と Windows の両方のコンテナーで動作します。

Dockerfile の例では、ASP.NET Core ランタイム Docker の基本イメージに基づく ASP.NET Core アプリケーション Docker イメージを作成します。

使用して、 [Docker 複数段階の機能をビルドする](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)に。

* 基づくコンテナーでサンプルをビルド、**大きい**ASP.NET Core ビルド Docker 基本イメージ 
* 基づいた Docker イメージに、最後のビルド結果をコピー、**小さい**ASP.NET Core Docker ランタイムの基本イメージ

> [!Note]
> ビルド イメージには、実行時のイメージではありませんが、アプリケーションの構築に必要なツールが含まれています。

### <a name="prerequisites"></a>必須コンポーネント

でビルドして実行するには、次の項目をインストールします。

#### <a name="net-core-20-sdk"></a>.NET 2.0 SDK をコアします。

* インストール[.NET Core SDK 2.0](https://www.microsoft.com/net/core)です。

* まだ行っていない場合、好きなコード エディターをインストールします。

> [!TIP]
> コード エディターをインストールする必要がありますか。 再試行[Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Docker クライアントをインストールします。

インストール[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/)またはそれ以降の Docker クライアント。

Docker クライアントをインストールすることができます。

* Linux ディストリビューション

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/)です。

#### <a name="installing-git-for-sample-repository"></a>サンプル リポジトリの Git のインストール

* インストール[git](https://git-scm.com/download)リポジトリを複製する場合。

### <a name="getting-the-sample-application"></a>サンプル アプリケーションを取得します。

サンプルを入手する最も簡単な方法は、複製することによって、[サンプル リポジトリ](https://github.com/dotnet/dotnet-docker-samples)git で、次の手順を使用します。 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

(小さなは) リポジトリは .NET Core Docker サンプル リポジトリから zip としてダウンロードすることもできます。

### <a name="run-the-aspnet-app-locally"></a>ASP.NET アプリケーションをローカルで実行します。

参照ポイントとして、アプリケーションをコンテナー化する前に、まず、アプリケーションをローカルで実行します。

ビルドおよび (、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して、.NET Core 2.0 SDK と、アプリケーションをローカルで実行できます。

```console
cd aspnetapp
dotnet run
```

アプリケーションが起動したらを参照してください。 **http://localhost:5000** web ブラウザーにします。

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>ビルドおよび Docker を使用した Linux コンテナーのサンプルを実行します。

ビルドして、(、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して Linux コンテナーを使用して、Docker でサンプルを実行することができます。

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] `docker run` '-P' 引数のマップ、ローカル コンピューターのポート 80 をコンテナーに 5000 のポート (ポート マッピング形式は`host:container`)。 詳細については、次を参照してください。、[実行 docker](https://docs.docker.com/engine/reference/commandline/exec/)コマンド ライン パラメーターで参照します。

アプリケーションが起動したらを参照してください。 **http://localhost:5000** web ブラウザーにします。

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>ビルドおよび Docker for Windows コンテナーでサンプルを実行します。

ビルドして、(、手順には、リポジトリのルートが想定しています)、次のコマンドを使用して Windows コンテナーを使用して、Docker でサンプルを実行することができます。

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> 移動する必要があります、**コンテナーの IP アドレス**(http://localhost) ではなく直接ブラウザーで Windows コンテナーを使用する場合。 次の手順で、コンテナーの IP アドレスを取得できます。

* 別のコマンド プロンプトを開きます。
* 実行`docker ps`に、実行中のコンテナーを参照してください。 "Aspnetcore_sample"コンテナーが存在する必要があります。
* `docker exec aspnetcore_sample ipconfig` を実行します。
* コンテナーの IP アドレスをコピーし、ブラウザー (たとえば、172.29.245.43) に貼り付けます。

> [!Note]
> Docker exec には、名前とハッシュ識別用のコンテナーがサポートされています。 名前 (aspnetcore_sample) は、この例で使用されます。

次の実行中の Windows コンテナーの IP アドレスを取得する方法の例を参照してください。

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> Docker exec は、実行中のコンテナーで新しいコマンドを実行します。 詳細については、次を参照してください。、 [docker exec リファレンス](https://docs.docker.com/engine/reference/commandline/exec/)コマンド ライン パラメーターにします。

使用してローカルで実稼働環境に展開する準備が整っているアプリケーションを作成することができます、 [dotnet 発行](../tools/dotnet-publish.md)コマンド。

```console
dotnet publish -c release -o published
```

> [!Note]
> -C リリース引数は、リリース モード (既定ではデバッグ モード) でアプリケーションを構築します。 詳細については、次を参照してください。、 [dotnet run リファレンス](../tools/dotnet-run.md)コマンド ライン パラメーターにします。

アプリケーションを実行できる**Windows**次のコマンドを使用します。

```console
dotnet published\aspnetapp.dll
```

アプリケーションを実行できる**Linux**または**macOS**次のコマンドを使用します。

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>このサンプルで使用する docker イメージ

次の Docker イメージは、このサンプルで使用されます。

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

おめでとうございます!  だけがある場合。
> [!div class="checklist"]
> * Microsoft .NET Core Docker images 学習
> * ASP.NET Core Dockerize するサンプル アプリを取得しました
> * ASP.NET サンプル アプリをローカルに実行されていました
> * 構築され、Docker を使用した Linux コンテナーのサンプルを実行
> * 構築され、Docker for Windows コンテナーで、サンプルの実行


**次の手順**

ここでは、いくつか次の手順を実行できます。

* [Visual Studio Docker ツールの使用](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio のコードでデバッグ](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [手 Visual Studio での取得 Mac、コンテナー、およびサーバーなしのコード、クラウド内](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Mac のラボの Docker と Visual Studio の概要](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。
