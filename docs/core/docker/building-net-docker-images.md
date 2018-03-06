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
ms.workload:
- dotnetcore
ms.openlocfilehash: d5631bdbc0334640b290c08df17cba0bfe99fe85
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="building-docker-images-for-net-core-applications"></a>.NET Core アプリケーションの Docker イメージのビルド

 このチュートリアルでは、Docker で .NET Core を使用する方法を紹介します。 最初に、Microsoft が提供し、保守管理しているさまざま Docker イメージと使用例について考察します。 次に、ASP.NET Core アプリをビルドし、Docker で動作させる方法について学習します。

このチュートリアルを通して、以下のことを学びます。
> [!div class="checklist"]
> * Microsoft .NET Core Docker イメージについて学習する 
> * Docker で動作させる ASP.NET Core サンプル アプリを取得する
> * ASP.NET サンプル アプリをローカルで実行する
> * サンプルをビルドし、Docker for Linux コンテナーで実行する
> * サンプルをビルドし、Docker for Windows コンテナーで実行する

## <a name="docker-image-optimizations"></a>Docker イメージの最適化

開発者向けの Docker イメージをビルドするにあたり、次の主な 3 つのシナリオに重点を置きました。

* .NET Core アプリの開発に使用されるイメージ
* .NET Core アプリのビルドに使用されるイメージ
* .NET Core アプリの実行に使用されるイメージ

3 つのイメージである理由は、
コンテナー化されたアプリケーションを開発、ビルドおよび実行する場合、優先順位がそれぞれ異なるためです。

* **開発:** 変更をどれだけ速く繰り返せるかと変更のデバッグ機能が優先されます。 イメージのサイズはそれほど重要ではなく、むしろ、コードを変更し、それをすばやく確認できるかが重要になります。

* **ビルド:** このイメージには、コンパイラやバイナリを最適化するその他の依存関係など、アプリのコンパイルに必要なすべてが含まれます。  ビルド イメージを使用し、実稼働イメージに置くアセットを作成します。 ビルド イメージは継続的インテグレーション、またはビルド環境で使用されます。 この手法では、ビルド エージェントがビルド イメージ インスタンスで (必要なすべての依存関係と共に) アプリケーションをコンパイルし、ビルドできます。 この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。

* **実稼働:** イメージをどれだけ速く配置し、開始できるか。 このイメージは小さく、Docker レジストリから Docker ホストまでのネットワーク パフォーマンスが最適化されます。 コンテンツは実行できる状態であるため、Docker の実行から結果の処理までを最速で行うことができます。 動的コード コンパイルは Docker モデルで必要ありません。 このイメージに配置するコンテンツは、アプリケーションの実行に必要なバイナリとコンテンツに制限されます。

    たとえば、`dotnet publish` 出力には次が含まれています。

    * コンパイルされたバイナリ
    * .js ファイルと .css ファイル


実稼働イメージに `dotnet publish` コマンド出力を含める理由は、そのサイズを最小限に抑えることにあります。

一部の .NET Core イメージは異なるタグの間で層を共有します。そのため、最新のタグをダウンロードするプロセスが比較的軽くなります。 コンピューターに以前のバージョンがインストールされている場合、このアーキテクチャで必要なディスク領域が減ります。

複数のアプリケーションが同じコンピューターで共通のイメージを使用するとき、共通のイメージ間でメモリが共有されます。 共有するイメージは同じものにする必要があります。

## <a name="docker-image-variations"></a>Docker イメージのバリエーション

上記の目標を達成するために、[`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/) にはイメージ バリアントが用意されています。

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) このイメージには、.NET Core とコマンド ライン ツール (CLI) を含む .NET Core SDK が含まれています。 このイメージは **開発シナリオ** にマップされます。 このイメージは、ローカル開発、デバッグおよび単体テストに使用します。 このイメージは、**ビルド** シナリオでも使用できます。 `microsoft/dotnet:sdk` を使用すると、常に最新版が取得されます。

> [!TIP]
> 要件が確定していない場合、`microsoft/dotnet:<version>-sdk` イメージの使用をお勧めします。 これは "事実上標準の" イメージであり、使い捨てのコンテナーとして使用されます (ソース コードをマウントし、コンテナーを起動してアプリを開始します)。また、基礎イメージとして使用し、これに基づいて他のイメージをビルドします。

* `microsoft/dotnet:<version>-runtime`: このイメージには .NET Core が含まれ (ランタイムとライブラリ)、**実稼働**で .NET Core アプリを実行するために最適化されています。

## <a name="alternative-images"></a>その他のイメージ

開発、ビルドおよび実稼働の最適化されたシナリオに加え、次の追加イメージが提供されます。

* `microsoft/dotnet:<version>-runtime-deps`: **runtime-deps** イメージには、オペレーティング システムと .NET Core で必要とされるすべてのネイティブ依存関係が含まれます。 このイメージは[自己完結型アプリケーション](../deploying/index.md)用です。

各バリアントの最新バージョン:

* `microsoft/dotnet` または `microsoft/dotnet:latest` (SDK イメージのエイリアス)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>お試しいただきたいサンプル

* [この ASP.NET Core の Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp)は、運用向けの ASP.NET Core アプリの Docker イメージを構築するためのベスト プラクティス パターンを示します。 このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。

* この .NET Core の Docker サンプルでは、[運用環境用の .NET Core アプリの Docker イメージをビルドする](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)方法に関するベスト プラクティス パターンを示します。

## <a name="your-first-aspnet-core-docker-app"></a>初めての ASP.NET Core Docker アプリ

このチュートリアルでは、Docker で動作させるアプリに ASP.NET Core Docker サンプル アプリケーションを使用しましょう。 この ASP.NET Core Docker サンプル アプリケーションでは、運用環境向け ASP.NET Core アプリの Docker イメージをビルドする場合のベスト プラクティス パターンを確認できます。 このサンプルは Linux コンテナーと Windows コンテナーのどちらでも動作します。

このサンプル Dockerfile は、ASP.NET Core Runtime Docker ベース イメージに基づき、ASP.NET Core アプリケーション Docker イメージを作成します。

[Docker のマルチステージ ビルド機能](https://docs.docker.com/engine/userguide/eng-image/multistage-build/)を利用し、次のことを行います。

* **より大きな** ASP.NET Core Build Docker ベース イメージに基づき、コンテナーでサンプルをビルドする 
* **より小さい** ASP.NET Core Docker Runtime ベース イメージに基づき、最終的なビルド結果を Docker イメージにコピーする

> [!NOTE]
> このビルド イメージには、アプリケーションのビルドに必要なツールが含まれています。ランタイム イメージにはそれが含まれていません。

### <a name="prerequisites"></a>必須コンポーネント

ビルドし、実行するには、次のアイテムをインストールします。

#### <a name="net-core-20-sdk"></a>.NET Core 2.0 SDK

* [.NET Core SDK 2.0](https://www.microsoft.com/net/core) をインストールします。

* コード エディターをまだインストールしていなければ、お気に入りのエディターをインストールしてください。

> [!TIP]
> コード エディターをインストールする必要がありますか。 [Visual Studio](https://visualstudio.com/downloads) をお試しください。

#### <a name="installing-docker-client"></a>Docker クライアントをインストールする

[Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) 以降の Docker クライアントをインストールします。

Docker クライアントがインストール可能な OS:

* Linux ディストリビューション

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/)

#### <a name="installing-git-for-sample-repository"></a>サンプル リポジトリとして Git をインストールする

* リポジトリを複製する場合、[git](https://git-scm.com/download) をインストールします。

### <a name="getting-the-sample-application"></a>サンプル アプリケーションを入手する

サンプルを用意する最も簡単な方法は、git で[サンプル レジストリ](https://github.com/dotnet/dotnet-docker-samples)を複製することです。次の指示に従ってください。 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

.NET Core Docker サンプル リポジトリから zip ファイルとしてリポジトリ (小さい) をダウンロードすることもできます。

### <a name="run-the-aspnet-app-locally"></a>ASP.NET アプリをローカルで実行する

参照ポイントとして、アプリケーションをコンテナー化する前に、まず、アプリケーションをローカルで実行します。

.NET Core 2.0 SDK を利用し、アプリケーションをビルドし、ローカルで実行できます。次のコマンドを利用します (この指示では、リポジトリのルートを想定しています)。

```console
cd aspnetapp
dotnet run
```

アプリケーションが起動したら、お使いの Web ブラウザーで **http://localhost:5000** にアクセスします。

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>サンプルをビルドし、Docker for Linux コンテナーで実行する

Linux コンテナーを利用し、Docker でサンプルをビルドし、実行できます。次のコマンドを利用します (この指示では、リポジトリのルートを想定しています)。

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> `docker run` '-p' 引数は、コンピューターのポート 5000 をコンテナーのポート 80 にマッピングします (ポート マッピングの形式は `host:container` です)。 詳細については、コマンドライン パラメーターの [docker run](https://docs.docker.com/engine/reference/commandline/exec/) 参照をご覧ください。

アプリケーションが起動したら、お使いの Web ブラウザーで **http://localhost:5000** にアクセスします。

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>サンプルをビルドし、Docker for Windows コンテナーで実行する

Window コンテナーを利用し、Docker でサンプルをビルドし、実行できます。次のコマンドを利用します (この指示では、リポジトリのルートを想定しています)。

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Windows コンテナーの利用時、お使いのブラウザーで (http://localhost ではなく) **コンテナー IP アドレス**に移動する必要があります。 次の手順でコンテナーの IP アドレスを取得できます。

* 別のコマンド プロンプトを開きます。
* `docker ps` を実行し、実行中のコンテナーを確認します。 "aspnetcore_sample" コンテナーを確認できるはずです。
* `docker exec aspnetcore_sample ipconfig` を実行します。
* コンテナー IP アドレスをコピーし、ブラウザーに貼り付けます (たとえば、172.29.245.43)。

> [!NOTE]
> Docker exec は、名前やハッシュでコンテナーを識別できます。 今回のサンプルでは名前 (aspnetcore_sample) が使用されています。

次の例では、実行中の Windows コンテナーの IP アドレスを取得する方法を確認できます。

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

> [!NOTE]
> Docker exec は、実行中のコンテナーで新しいコマンドを実行します。 詳細については、コマンドライン パラメーターの [docker exec 参照](https://docs.docker.com/engine/reference/commandline/exec/)をご覧ください。

[dotnet publish](../tools/dotnet-publish.md) コマンドを利用し、運用環境にローカル展開できるアプリケーションを生成できます。

```console
dotnet publish -c release -o published
```

> [!NOTE]
> -c リリース引数はリリース モードでアプリケーションをビルドします (既定はデバッグ モードです)。 詳細については、コマンドライン パラメーターの [dotnet run 参照](../tools/dotnet-run.md)をご覧ください。

次のコマンドを利用し、**Windows** でアプリケーションを実行できます。

```console
dotnet published\aspnetapp.dll
```

次のコマンドを利用し、**Linux** または **macOS** でアプリケーションを実行できます。

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>このサンプルで使用されている Docker イメージ

次の Docker イメージはこのサンプルで使用されています

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

おめでとうございます!  今回の成果:
> [!div class="checklist"]
> * Microsoft .NET Core Docker イメージについて学習しました
> * Docker で動作させる ASP.NET Core サンプル アプリを取得しました
> * ASP.NET サンプル アプリをローカルで実行しました
> * サンプルをビルドし、Docker for Linux コンテナーで実行しました
> * サンプルをビルドし、Docker for Windows コンテナーで実行しました


**次の手順**

次の手順としては以下のものを用意しています。

* [Visual Studio Docker ツールの使用](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure Container Registry から Azure Container Instances に Docker イメージを配置する](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Visual Studio Code でのデバッグ](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [クラウドにおける Visual Studio for Mac、コンテナー、サーバーレス コードの入門](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Docker と Visual Studio for Mac の入門ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Azure サブスクリプションをお持ちでない場合は、[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)して 30 日間の無料アカウントと 200 ドル分の Azure クレジットを取得し、お好きな Azure サービスの組み合わせを試しましょう。
