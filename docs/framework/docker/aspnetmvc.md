---
title: "Windows コンテナーへの ASP.NET MVC アプリケーションの移行"
description: "既存の ASP.NET MVC アプリケーションを取得し、Windows Docker コンテナーで実行する方法について説明します。"
keywords: "Windows コンテナー, Docker, ASP.NET MVC"
author: BillWagner
ms.author: wiwagn
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: dotnet-mvc
ms.devlang: dotnet
ms.assetid: c9f1d52c-b4bd-4b5d-b7f9-8f9ceaf778c4
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c81e9783499ede9a612969f16a7e85d77fa921c4

---

# <a name="migrating-aspnet-mvc-applications-to-windows-containers"></a>Windows コンテナーへの ASP.NET MVC アプリケーションの移行

Windows コンテナー内で既存の .NET Framework ベースのアプリケーションを実行するには、アプリケーションを含む Docker イメージを作成して、そのイメージを実行する 1 つまたは複数のコンテナーを開始する必要があります。 このトピックでは、既存の [ASP.NET MVC アプリケーション](http://www.asp.net/mvc) を取得し、Windows コンテナーに展開するために実行する必要があるタスクについて説明します。

既存の ASP.NET MVC アプリケーションから始めます。 次に、Visual Studio を使用して発行した資産をビルドします。 Docker を使用してアプリケーションを含むイメージを作成します。イメージを開始すると、そのアプリケーションが実行されます。 作業が完了したら、Windows コンテナーで実行しているサイトにブラウザーで接続し、アプリケーションが実行中であることを確認できます。

この記事を読むには、Docker の基本的な知識があることが前提となります。 Docker アーキテクチャの概念について不慣れな場合、詳細については、Docker サイトの「[Docker Overview](https://docs.docker.com/engine/understanding-docker/)」 (Docker の概要) を参照してください。

コンテナー内で実行するアプリケーションは、ランダムに質問に回答する単純な Web サイトです。 このアプリケーションは、Web 層をコンテナーに移行することに重点を置いた、認証のサポートやデータベース ストレージのない基本的な MVC アプリケーションです。 今後のトピックで、コンテナー化されたアプリケーションに永続的な記憶域を移動して管理する方法を説明します。

アプリケーションを移行する手順は次のとおりです。

1. [イメージの資産をビルドする発行タスクを作成します。](#publish-script)
2. [アプリケーションを実行する Docker イメージをビルドします。](#build-the-image)
3. [イメージを実行する Docker コンテナーを開始します。](#start-a-container)
4. [ブラウザーを使用してアプリケーションを検証します。](#verify-in-the-browser)

完成したアプリケーションは [GitHub の dotnet/core-docs リポジトリ](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator)にあります。

## <a name="prerequisites"></a>前提条件

少なくとも、開発用コンピューターで [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) または [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) を実行している必要があります。 

作業を始める前に、[Docker for Windows](https://docs.docker.com/docker-for-windows/) Version 1.12 Beta 26 またはそれ以降をインストールする必要があります。 現時点では Windows コンテナー サポートはベータ チャネルのみで使用できます。

> [!IMPORTANT]
> Windows Server 2016 を使用している場合は、Docker コンテナーを実行する前に「[コンテナー ホストの展開 - Windows Server](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment)」にある手順に従う必要があります。

Docker をインストールして開始した後、Windows ベースの Docker イメージを実行するために、トレイ アイコンを右クリックし、**[Switch to Windows containers]** (Windows コンテナーに切り替え) を選択する必要があります。 このコマンドの実行には数秒かかります。

![Windows コンテナー][windows-container]

## <a name="publish-script"></a>発行スクリプト

最初の手順として、Docker イメージに読み込む必要があるすべての資産を 1 か所に集めます。 Visual Studio の **[発行]** コマンドを使用してアプリケーションの発行プロファイルを作成できます。 このプロファイルですべての資産を 1 つのディレクトリ ツリーに集めます。このチュートリアルの後半で、そのディレクトリ ツリーをターゲット イメージにコピーします。

**発行の手順**

1. Visual Studio で Web プロジェクトを右クリックし、**[発行]** を選択します。
2. **[カスタム プロファイル]** ボタンをクリックし、方法として [ファイル システム] を選択します。
3. ディレクトリを選択します。 規則により、ダウンロードしたサンプルには `bin/PublishOutput` が使用されます。

![接続の発行][publish-connection]

次に、**[設定]** タブの **[ファイル発行オプション]** のセクションを開きます。 **[発行中にプリコンパイルする]** を選択します。 この最適化は、Docker コンテナー内のビューをコンパイルすることを意味し、プリコンパイル済みのビューをコピーすることになります。

![発行の設定][publish-settings]

**[発行]** をクリックすると、Visual Studio で必要なすべての資産がコピー先フォルダーにコピーされます。 

## <a name="build-the-image"></a>イメージのビルド

Docker イメージは Dockerfile 内に定義します。Dockerfile は、基本イメージ、追加のコンポーネント、実行するアプリケーション、その他の構成イメージに関する指示を含みます。  Dockerfile は、イメージを作成する `docker build` コマンドの入力です。

[Docker Hub](https://hub.docker.com/r/microsoft/aspnet/) にある `microsft/aspnet` イメージに基づいてイメージをビルドします。
基本イメージである `microsoft/aspnet` は、Windows Server イメージです。 Windows Server Core に加えて、IIS と ASP.NET 4.6.2 がインストールされ有効になっています。 このイメージをコンテナー内で実行すると、自動的に IIS が起動し、インストールされている Web サイトがアクティブになります。

イメージを作成する Dockerfile は、次のようになります。

```
# The `FROM` instruction specifies the base image. You are
# extending the `microsoft/aspnet` image.

FROM microsoft/aspnet

# Next, this Dockerfile creates a directory for your application
RUN mkdir C:\randomanswers

# configure the new site in IIS.
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "ASPNET" -PhysicalPath C:\randomanswers -BindingInformation "*:8000:"

# This instruction tells the container to listen on port 8000. 
EXPOSE 8000

# The final instruction copies the site you published earlier into the container.
ADD containerImage/ /randomanswers
```

この Dockfile に `ENTRYPOINT` コマンドは使用されていません。 使用する必要はありません。
基本イメージにより、コンテナー開始時に IIS が起動します。 

次に、ASP.NET アプリケーションを実行するイメージを作成する Docker ビルド コマンドを実行する必要があります。 これを行うには、PowerShell ウィンドウを開き、ソリューション ディレクトリで次のコマンドを入力します。

```
docker build -t mvcrandomanswers .
```

このコマンドは、Dockerfile 内の手順に従って新しいイメージをビルドします。 その手順には、[Docker Hub](http://hub.docker.com) から基本イメージをプルすることが含まれる場合があります。その後、そのイメージにアプリケーションが追加されます。

そのコマンドの完了後、`docker images` コマンドを実行して新しいイメージの情報を参照できます。

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
mvcrandomanswers              latest              86838648aab6        2 minutes ago       8.104 GB
```

IMAGE ID はコンピューターによって異なります。 では、アプリケーションを実行しましょう。

## <a name="start-a-container"></a>コンテナーの開始

コンテナーを開始するには、次の `docker run` コマンドを実行します。

```
docker run -d -p 8000:8000 --name randomanswers mvcrandomanswers
```

`-d` 引数は、デタッチ モードでイメージを開始するよう Docker に指示します。 つまり、Docker イメージは現在のシェルから切断された状態で実行されます。

`-p 8000:8000` 引数は、Docker に対して受信ポートのマップ方法を指示します。 この例では、ホストとコンテナーの両方でポート 8000 を使用しています。

`--name randomanswers` は、実行するコンテナーに名前を付けます。 この名前は、ほとんどのコマンドでコンテナー ID の代わりに使用できます。

`mvcrandomanswers` は、開始するイメージの名前です。

## <a name="verify-in-the-browser"></a>ブラウザーでの確認

> [!NOTE]
> 現在のリリースでは、`http://localhost` を使用してサイトを指定することはできません。 これは WinNAT での既知の動作によるもので、今後は解決されます。 解決されるまでは、コンテナーの IP アドレスを使用する必要があります。

コンテナーの開始後、実行中のコンテナーにブラウザーから接続できるように、コンテナーの IP アドレスを見つける必要があります。

```
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" randomanswers
172.31.194.61
```

実行中のコンテナーには、IPv4 アドレスと構成したポート (8000) を使用して接続できます。ここに示す例では `http://172.31.194.61:8000` となっています。 その URL をブラウザーに入力すると、実行中のサイトが表示されます。

> [!NOTE]
> 一部の VPN またはプロキシ ソフトウェアが原因でサイトに移動できない場合があります。
> コンテナーが動作していることを確認するために、それらを一時的に無効にできます。

GitHub のサンプル ディレクトリに含まれる [PowerShell スクリプト](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator/run.ps1)は、これらのコマンドを実行します。 PowerShell ウィンドウを開き、ソリューション ディレクトリに移動して、次のように入力します。

```
./run.ps1
```

これによりイメージをビルドし、コンピューターにイメージの一覧を表示して、コンテナーを開始した後、そのコンテナーの IP アドレスを表示します。 

作業完了後にコンテナーを停止する場合は、`docker
stop` コマンドを実行します。

```
docker stop randomanswers
```

コンテナーを削除するには、`docker rm` コマンドを実行します。

```
docker rm randomanswers
```

## <a name="summary"></a>まとめ

このトピックでは、既存の ASP.NET MVC アプリケーションを Windows Server コンテナーに移行して実行する手順を説明しました。 既存のアプリケーションを実行するためにアプリケーションに変更を加える必要はありません。 アプリケーションを発行し、Docker イメージをビルドして、新しいコンテナーでそのイメージを開始するタスクを実行する必要があります。 既存のアプリケーションをこの環境に移行するには、Windows Server コンテナーを利用することが最も簡単な方法です。

[windows-container]: media/aspnetmvc/SwitchContainer.png "Windows コンテナーへの切り替え"
[publish-connection]: media/aspnetmvc/PublishConnection.png "ファイル システムへの発行"
[publish-settings]: media/aspnetmvc/PublishSettings.png "発行の設定"



<!--HONumber=Jan17_HO3-->


