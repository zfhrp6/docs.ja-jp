---
title: ".NET Core の Docker イメージのビルド"
description: "Docker イメージと .NET Core について"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 9dc52f3a8c74c1aa575a83cb3bbd579b93fae9ae
ms.openlocfilehash: 0e679ffc22f52de5e2ce8194942efbb2f5299ee4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---

#<a name="building-docker-images-for-net-core-applications"></a>.NET Core アプリケーションの Docker イメージのビルド

 
> [!IMPORTANT]
> .NET Core 2.0 は現在、更新作業中です。 下記の手順は最新ではありません。 ご迷惑をおかけして申し訳ありません。

.NET Core と Docker を一緒に使用する方法を理解するには、まず、提供されるさまざまな Docker イメージと、適切な使用のタイミングを把握する必要があります。 ここでは、提供されるバリエーションを確認し、ASP.NET Core Web API をビルドし、Yeoman Docker ツールを使用してデバッグ可能なコンテナーを作成し、さらにプロセスにおいて Visual Studio Code がどのように役立つかを簡単に確認します。 

## <a name="docker-image-optimizations"></a>Docker イメージの最適化

開発者向けの Docker イメージをビルドするにあたり、次の主な 3 つのシナリオに重点を置きました。

- .NET Core アプリの開発に使用されるイメージ
- .NET Core アプリのビルドに使用されるイメージ
- .NET Core アプリの実行に使用されるイメージ

3 つのイメージである理由は、
コンテナー化されたアプリケーションを開発、ビルドおよび実行する場合、優先順位がそれぞれ異なるためです。
- **開発:**  変更をどれだけ速く繰り返せるかと、変更のデバッグ機能。 イメージのサイズはそれほど重要ではなく、むしろ、コードを変更し、それをすばやく確認できるかが重要になります。 Visual Studio Code で使用する [yo docker](https://aka.ms/yodocker) などの一部のツールでは、開発時にこのイメージを使用します。 
- **ビルド:** アプリのコンパイルに必要なもの。 これには、コンパイラと、バイナリを最適化するためのその他の依存関係が含まれます。 このイメージは配置するのではなく、実稼働イメージに配置するコンテンツをビルドする場合に使用します。 このイメージは継続的インテグレーション、またはビルド環境で使用されます。 たとえば、ビルド エージェントに直接すべての依存関係をインストールするのではなく、ビルド エージェントがビルド イメージをインスタンス化し、イメージ内に含まれるアプリのビルドに必要なすべての依存関係と共にアプリケーションをコンパイルします。 この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。 
- **実稼働:** イメージをどれだけ速く配置し、開始できるか。 このイメージは小さいため、Docker レジストリから Docker ホストにネットワーク経由ですばやく移動できます。 コンテンツは実行できる状態であるため、Docker の実行から結果の処理までを最速で行うことができます。 変更できない Docker モデルの場合は、コードを動的にコンパイルする必要はありません。 このイメージに配置するコンテンツは、アプリケーションの実行に必要なバイナリとコンテンツに制限されます。 たとえば、`dotnet publish` を使用して発行された出力には、コンパイル済みのバイナリ、イメージ、.js および .css ファイルが含まれます。 時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされたパッケージを含むイメージが表示されます。  

複数のバージョンの .NET Core イメージがありますが、すべて 1 つ以上のレイヤーを共有します。 格納に必要なディスク容量やレジストリからプルするデルタは、全体よりはるかに少なくなります。これは、すべてのイメージが同じ基本レイヤーとおそらく他のレイヤーを共有しているためです。  

## <a name="docker-image-variations"></a>Docker イメージのバリエーション

上記の目標を達成するために、[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) にはイメージ バリアントが用意されています。

- `microsoft/dotnet:<version>-sdk`: **microsoft/dotnet:1.0.0-preview2-sdk** です。このイメージには、.NET Core とコマンド ライン ツール (CLI) を含む .NET Core SDK が含まれています。 このイメージは **開発シナリオ** にマップされます。 このイメージは、ローカル開発、デバッグおよび単体テストに使用します。 たとえば、コードをチェックインする前に、すべての開発を行います。 このイメージは、**ビルド** シナリオでも使用できます。

- `microsoft/dotnet:<version>-core`: **microsoft/dotnet:1.0.0-core** です。このイメージは[ポータブル .NET Core アプリケーション](../deploying/index.md)を実行します。**実稼働**でアプリケーションを実行するために最適化されます。 これには SDK が含まれていません。`dotnet publish` の最適化された出力を取得するためのものです。 ポータブル ランタイムは、共有イメージ レイヤーによる利点が得られるため、複数のコンテナーを実行する Docker コンテナー シナリオに最適です。  

## <a name="alternative-images"></a>その他のイメージ

開発、ビルドおよび実稼働の最適化されたシナリオに加え、次の追加イメージが提供されます。

- `microsoft/dotnet:<version>-onbuild`: **microsoft/dotnet:1.0.0-preview2-onbuild** です。これには [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild) トリガーが含まれます。 このビルドではアプリケーションを[コピー](https://docs.docker.com/engine/reference/builder/#/copy)し、`dotnet restore` を実行して [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) の `dotnet run` 命令を作成して、Docker イメージの実行時にアプリケーションを実行します。 実稼働用にイメージは最適化されませんが、単にソース コードをイメージにコピーして実行する際に便利な場合があります。 

- `microsoft/dotnet:<version>-core-deps`: **microsoft/dotnet:1.0.0-core-deps** です。自己完結型アプリケーションを実行する場合は、このイメージを使用します。 これには、.NET Core で必要なすべてのネイティブの依存関係があるオペレーティング システムが含まれます。 このイメージを、独自のカスタム CoreFX または CoreCLR ビルドの基本イメージとして使用することもできます。 **onbuild** バリアントは単にコードをイメージに配置して実行するために最適化されますが、このイメージは、アプリケーションと共にパッケージ化された .NET ランタイムがある .NET Core アプリの実行に必要なオペレーティング システムの依存関係のみを持つように最適化されます。 通常、このイメージは同じホスト上の複数の .NET Core コンテナーを実行するために最適化されません。これは、イメージにはそれぞれアプリケーション内に .NET Core ランタイムがあるためです。イメージをレイヤー化する利点はありません。   

各バリアントの最新バージョン:

- `microsoft/dotnet` または `microsoft/dotnet:latest` (SDK を含む)
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

ここでは、さまざまなサイズを表示するための開発用コンピューターでの `docker pull <imagename>` の実行後のイメージのリストを示します。 開発/ビルド バリアントの `microsoft/dotnet:1.0.0-preview2-sdk` には、アプリケーションの開発とビルドのための SDK が含まれているため、サイズが大きくなっていることに注目してください。 実稼働バリアントの `microsoft/dotnet:core` には .NET Core ランタイムのみが含まれるため、サイズは小さくなっています。 Linux で使用できる最小イメージの `core-deps` は非常に小さくなっていますが、アプリケーションはこれと一緒に .NET ランタイムのプライベート コピーをコピーする必要があります。 コンテナーは既にプライベート分離バリアになっているため、複数の dotnet ベース コンテナーを実行するとその最適化が失われます。 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a>必須コンポーネント

ビルドと実行には、以下のいくつかのものをインストールする必要があります。

- [.NET Core](http://dot.net)
- [Docker](https://www.docker.com/products/docker)。Docker コンテナーをローカルで実行するためのものです。
- [Node.js](https://nodejs.org/)
- [ASP.NET の Yeoman ジェネレーター](https://github.com/omnisharp/generator-aspnet)。Web API アプリケーションを作成するためのものです。
- [Docker の Yeoman ジェネレーター](http://aka.ms/yodocker)。Microsoft が提供するものです。

以下の npm を使用して、ASP.NET Core と Docker の Yeoman ジェネレーターをインストールします。 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> このサンプルでは、エディターに [Visual Studio Code](http://code.visualstudio.com) を使用します。

## <a name="creating-the-web-api-application"></a>Web API アプリケーションの作成

参照ポイントとして、アプリケーションをコンテナー化する前に、まず、アプリケーションをローカルで実行します。 

完成したアプリケーションは [GitHub の dotnet/docs リポジトリ](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images)にあります。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

アプリケーションのディレクトリを作成します。

そのディレクトリでコマンドまたはターミナル セッションを開き、以下のように入力して ASP.NET Yeoman ジェネレーターを使用します。
```
yo aspnet
```

**Web API アプリケーション**を選択し、アプリ名として **api** と入力してから Enter をタップします。  アプリケーションがスキャフォールディングされたら、`/api` ディレクトリに変更し、`dotnet restore` を使用して NuGet 依存関係を復元します。

```
cd api
dotnet restore
```

`dotnet run` を使用し、**http://localhost:5000/api/values** を参照してアプリケーションをテストします。

```javascript
[
    "value1",
    "value2"
]
```

`Ctrl+C` を使用してアプリケーションを停止します。

## <a name="adding-docker-support"></a>Docker サポートの追加

プロジェクトへの Docker サポートの追加は、Microsoft の Yeoman ジェネレーターを使用して行います。 現在、コンテナー内でのプロジェクトのビルドと実行に役立つ Dockerfile とスクリプトを作成するにより、.NET Core、Node.js および Go プロジェクトをサポートしています。 エディターのデバッグとコマンド パレットのサポートのために Visual Studio Code 固有のファイル (launch.json、tasks.json) も追加されます。

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- プロジェクトの種類として `.NET Core` を選択します。
- `rtm`: .NET Core のバージョン用。
- `Y`: プロジェクトで Web サーバーを使用します。
- `5000`: Web API アプリケーションがリッスンしているポート (http://localhost:5000) です。
- `api`: イメージ名用。
- `api`: サービス名用。
- `api`: 構成プロジェクト用。 
- `Y`: 現在の Dockerfile を上書きします。

ジェネレーターが完了すると、以下のファイルがプロジェクトに追加されます。

- .vscode/launch.json
- Dockerfile.debug
- Dockerfile
- docker-compose.debug.yml
- docker-compose.yml
- dockerTask.ps1
- dockerTask.sh
- .vscode/tasks.json

ジェネレーターは 2 つの Dockerfile を作成します。

**Dockerfile.debug** - このファイルは **microsoft/dotnet:1.0.0-preview2-sdk** イメージに基づいています。イメージ バリアント リストのイメージの場合は、SDK、CLI および .NET Core が含まれ、開発やデバッグ (F5) 用に使用されます。 これらすべてのコンポーネントを含めると、サイズが約 540 MB の大きなイメージが生成されます。

**Dockerfile** - このイメージは **microsoft/dotnet:1.0.0-core** に基づくリリース イメージで、実稼働で使用する必要があります。 ビルド時のこのイメージは約 253 MB です。

### <a name="creating-the-docker-images"></a>Docker イメージの作成
`dockerTask.sh` または `dockerTask.ps1` スクリプトを使用して、特定の環境の **api** アプリケーション用にイメージとコンテナーをビルドまたは構成することができます。 以下のコマンドを実行して、**debug** イメージをビルドします。

```bash
./dockerTask.sh build debug
```

このイメージでは ASP.NET アプリケーションをビルドし、`dotnet restore` を実行して、デバッガーをイメージに追加し、`ENTRYPOINT` を設定して最後にアプリをイメージにコピーします。 その結果、`TAG` が *debug* の *api* という名前の Docker イメージが生成されます。  `docker images` を使用した場合のコンピューター上のイメージは以下のようになります。

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

イメージを生成し、Docker コンテナー内でアプリケーションを実行する別の方法は、Visual Studio Code でアプリケーションを開き、デバッグ ツールを使用することです。 

Visual Studio Code の左側にあるビュー バーのデバッグ アイコンを選択します。

![vscode デバッグ アイコン](./media/building-net-docker-images/debugging_debugicon.png)

次に、再生アイコンまたは F5 をタップして、イメージを生成し、コンテナー内でアプリケーションを起動します。 Web API は、http://localhost:5000 の既定の Web ブラウザーを使用して起動されます。

![VSCode Docker ツールのデバッグ](./media/building-net-docker-images/docker-tools-vscode-f5.png)

アプリケーションがコンテナー内ではなく、開発用コンピューターでローカルに実行されている場合と同じように、アプリケーションでのブレーク ポイントの設定やステップスルーなどを行うことができます。 コンテナー内でのデバッグのメリットは、運用環境に配置されるイメージと同じであることです。

リリースまたは実稼働イメージを作成する場合、`release` 環境名を渡すターミナルからコマンドを実行するだけです。

```bash
./dockerTask build release
```

このコマンドは、より小さな **microsoft/dotnet:core** 基本イメージに基づいてイメージを作成し、ポート 5000 を[公開](https://docs.docker.com/engine/reference/builder/#/expose)し、`dotnet api.dll` の [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) を設定して `/app` ディレクトリにコピーします。 デバッガー、SDK または `dotnet restore` がない場合、イメージは非常に小さくなります。 イメージの名前は **api** で、`TAG` は **latest** になります。

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a>まとめ

Docker ジェネレーターを使用して Web API アプリケーションに必要なファイルを追加することで、開発および実稼働バージョンのイメージを作成するプロセスが簡単になりました。  また、クロス プラットフォームのツールを使用し、PowerShell スクリプトを指定することで、コンテナー内のアプリケーションのステップ スルー デバッグを提供する Windows と Visual Studio Code の統合と同じ結果が得られるようになります。 イメージ バリアントとターゲット シナリオを理解することで、実稼働配置用に最適化されたイメージを生成できるだけでなく、内部ループの開発プロセスを最適化できます。  



