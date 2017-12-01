---
title: ".NET Core と Docker を基礎します。"
description: "Docker と .NET Core の基本チュートリアル"
keywords: ".NET、.NET core、Docker、チュートリアル"
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
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>.NET Core と Docker を基礎します。

このチュートリアルでは、Docker コンテナーをビルドおよび .NET Core アプリケーションのタスクの配置で説明します。 このチュートリアルの中には、次の操作を説明します。

> [!div class="checklist"]
> * Dockerfile を作成する方法
> * .NET Core アプリケーションを作成する方法。
> * Docker コンテナーにアプリを展開する方法です。

[Docker プラットフォーム](https://docs.docker.com/engine/docker-overview/#the-docker-platform)を使用して、 [Docker エンジン](https://docs.docker.com/engine/docker-overview/#docker-engine)速やかに構築してとしてアプリをパッケージ化[Docker images](https://docs.docker.com/glossary/?term=image)です。 これらのイメージが記述された、 [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile)を展開し実行する形式、[コンテナー階層化](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers)です。

## <a name="net-core-easiest-way-to-get-started"></a>作業を開始する最も簡単な方法を .NET core:

Docker イメージを作成する前に、containerize するアプリケーションを作成する必要があります。 これは、Linux、MacOS、または Windows に作成できます。 行うには最速で簡単な方法では、.NET Core を使用します。

.NET Core CLI ツールセットに慣れていない場合は、「[.NET Core SDK overview](../tools/index.md)」(.NET Core SDK の概要) を参照してください。

Windows と Linux の両方のコンテナーをビルドする[マルチ arch ベース タグ](https://github.com/dotnet/announcements/issues/14)です。

## <a name="your-first-net-core-docker-app"></a>最初の .NET Core Docker アプリ

### <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了します。

#### <a name="net-core-20-sdk"></a>.NET 2.0 SDK をコアします。

* インストール[.NET Core SDK 2.0](https://www.microsoft.com/net/core)です。

.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。

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

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Dockerization のコンソール アプリケーションを .NET Core 2.0 を作成します。

コマンド プロンプトを開き、*Hello* という名前のフォルダーを作成します。 作成したフォルダーに移動し、次のコマンドを入力します。

```console
dotnet new console
dotnet run
```

簡単に説明します。

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) は、コンソール アプリのビルドに必要な依存関係を含む最新の `Hello.csproj` プロジェクト ファイルを作成します。  また、アプリケーションのエントリ ポイントを含む基本的なファイルである `Program.cs` も作成します。
   
   `Hello.csproj`:

   プロジェクト ファイルでは、依存関係を復元し、プログラムをビルドするために必要なすべてのものを指定します。

   * `OutputType` タグは、実行可能ファイル (つまり、コンソール アプリケーション) をビルドすることを示します。
   * `TargetFramework` タグは、対象の .NET 実装を指定します。 高度なシナリオでは、複数のターゲット フレームワークを指定して、単一の操作で指定されたフレームワークを作成します。 このチュートリアルでは、.NET Core 2.0 おビルドします。

   `Program.cs`:

   プログラムの起動`using System`です。 このステートメントは、次の場合、"すべての取り込み、`System`のこのファイルのスコープに名前空間です"。 `System` 名前空間には、`string` などの基本的な構造、または数値型が含まれます。

   次に、`Hello` という名前空間を定義します。 名前空間は、自分の好きを変更できます。 `Program` という名前のクラスは、引数として文字列配列を使用する `Main` メソッドで、その名前空間内に定義されます。 この配列には、コンパイル済みプログラムの呼び出し時に渡される引数のリストが含まれます。 この例では、プログラムのみを書き込みます"Hello World!" 記述するだけです。

2. `$ dotnet restore`

   .NET Core で 2.x、 **dotnet 新しい**実行、 [ `dotnet restore` ](../tools/dotnet-restore.md)コマンド。 **Dotnet 復元**との依存関係のツリーを復元する[NuGet](https://www.nuget.org/)(.NET パッケージ マネージャー) 呼び出し。
   NuGet では、次のタスクを実行します。
   * 分析し、 *Hello.csproj*ファイル 
   * ファイルのダウンロードの依存関係 (またはコンピューターのキャッシュから grabs)
   * 書き込みます、 *obj/project.assets.json*ファイル

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   *Project.assets.json*ファイルは、NuGet の依存関係グラフ、バインディングの解像度、およびその他のアプリのメタデータの完全なセット。 ファイルがなどの他のツールで使用が必要なこの[ `dotnet build` ](../tools/dotnet-build.md)と[ `dotnet run` ](../tools/dotnet-run.md)、ソース コードを処理します。
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)呼び出し[ `dotnet build` ](../tools/dotnet-build.md)が正常に構築し、呼び出しを確認する`dotnet <assembly.dll>`アプリケーションを実行します。
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    高度なシナリオは、次を参照してください。 [.NET Core アプリケーションの配置](../deploying/index.md)詳細についてはします。

## <a name="dockerize-the-net-core-application"></a>.NET Core アプリケーションを dockerize します。

こんにちは .NET Core コンソール アプリは正常にローカルで実行されます。 今すぐみましょうステップを実行すること、さらに、ビルドおよび Docker でアプリを実行します。

### <a name="your-first-dockerfile"></a>最初の Dockerfile

テキスト エディターを開き、始めましょう! まだでアプリを構築しましたこんにちはディレクトリから取り組んでいます。

いずれかの Linux の次の Docker 命令を追加または[Windows コンテナー](https://docs.microsoft.com/virtualization/windowscontainers/about/)を新しいファイル。 完了したら、としてこんにちはディレクトリのルートに保存**Dockerfile**、拡張子のない (にファイルの種類を設定する必要があります`All types (*.*)`または似た)。

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Dockerfile には、順番に実行される Docker ビルド命令が含まれています。

最初の命令である必要があります[ **FROM**](https://docs.docker.com/engine/reference/builder/#from)です。 この命令は、新しいビルド ステージを初期化し、残りの手順については、ベース イメージを設定します。 マルチ arch タグでは、Windows または Linux のいずれかのコンテナーをプル Docker for Windows に応じて[コンテナー モード](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)です。 この例のベース イメージが microsoft/dotnet リポジトリから 2.0 sdk イメージです。

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir)命令セット、作業ディレクトリ、残りの実行、CMD、エントリ ポイント、コピー、および追加の Dockerfile の命令。 ディレクトリが存在しない場合は作成されます。 この場合、WORKDIR はアプリのディレクトリに設定されます。

```Dockerfile
WORKDIR /app
```

[**コピー** ](https://docs.docker.com/engine/reference/builder/#copy)命令がソース パスから新しいファイルまたはディレクトリをコピーし、変換先コンテナー ファイル システムに追加します。 この命令で、c# プロジェクト ファイルをコンテナーおコピーします。

```Dockerfile
COPY *.csproj ./
```

[**実行**](https://docs.docker.com/engine/reference/builder/#run)命令は、現在のイメージの上に新しいレイヤーでどのようなコマンドを実行し、結果をコミットします。 結果のコミットされたイメージは、Dockerfile の次の手順に使用されます。 実行中**dotnet 復元**c# プロジェクト ファイルの必要な依存関係を取得します。 

```Dockerfile
RUN dotnet restore
```

これは、**コピー**コードは、コピー、ファイルの残りの部分に、コンテナーに新しい[レイヤー](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers)です。

```Dockerfile
COPY . ./
```

これを使用してアプリを公開**実行**命令します。 [ **Dotnet 発行**](../tools/dotnet-publish.md)コマンド、アプリケーションをコンパイルでは、その依存関係をプロジェクト ファイルで指定された読み取り、結果として得られる一連のファイルをディレクトリに発行します。 アプリが発行された、**リリース**構成と既定のディレクトリに出力します。

```Dockerfile
RUN dotnet publish -c Release -o out
```

[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint)命令により、実行可能ファイルとして実行するコンテナーです。

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

これで、Dockerfile を。

* イメージへのアプリをコピーします。
* イメージに、アプリの依存関係
* 実行可能ファイルとして実行するアプリをビルドします。

### <a name="build-and-run-the-hello-net-core-20-app"></a>ビルドおよび実行するこんにちは .NET Core 2.0 アプリ

#### <a name="essential-docker-commands"></a>必須の Docker コマンド

これらの Docker コマンドは、不可欠な。

* [docker のビルド](https://docs.docker.com/engine/reference/commandline/build/)
* [docker の実行](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker イメージ](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>ビルドおよび実行します。

Dockerfile; を作成します。今すぐ Docker では、アプリをビルドして、コンテナーを実行します。

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

出力、`docker build`コマンドを次のコンソール出力に似たものにする必要があります。

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

出力からわかるように、Docker エンジンは、コンテナーの構築に Dockerfile を使用します。

出力、`docker run`コマンドを次のコンソール出力に似たものにする必要があります。

```console
Hello World!
```

おめでとうございます!  だけがある場合。
> [!div class="checklist"]
> * .NET Core のローカルのアプリケーションの作成
> * 最初のコンテナーを作成する Dockerfile を作成
> * 構築され、Dockerized アプリの実行



## <a name="next-steps"></a>次の手順

ここでは、いくつか次の手順を実行できます。

* [.NET Docker イメージのビデオの概要](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio、Docker と Azure のコンテナー インスタンス高度な連携します。](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Azure クイック スタートの docker](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Azure の Docker でのアプリを展開します。](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Azure のサブスクリプションを持っていない場合[今すぐサインアップ](https://azure.microsoft.com/free/?b=16.48)30 日間の無料のアカウントと Azure サービスの任意の組み合わせを試す Azure クレジットの get $200 です。

## <a name="docker-images-used-in-this-sample"></a>このサンプルで使用する docker イメージ

次の Docker イメージは、このサンプルで使用されます。

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>関連資料

* [.NET core Docker サンプル](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Windows コンテナー上の Dockerfile](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [.NET framework の Docker のサンプル](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core dockerhub を使用しての](https://hub.docker.com/r/microsoft/aspnetcore/)
* [.NET Core アプリケーションの Docker のチュートリアルを dockerize します。](https://docs.docker.com/engine/examples/dotnetcore/)
* [Visual Studio Docker ツールの使用](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Azure のコンテナー インスタンスを Azure のコンテナー レジストリから Docker イメージを展開します。](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)