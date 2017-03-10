---
title: ".NET Core コマンド ライン インターフェイス (CLI) ツール | Microsoft Docs"
description: "コマンドライン インターフェイス (CLI) とその主要な機能の概要"
keywords: "CLI, CLI ツール, .NET, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 7c5eee9f-d873-4224-8f5f-ed83df329a59
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 4e3137d8506342662d145481d5e9fde1d53b9ba3
ms.lasthandoff: 03/07/2017

---

# <a name="net-core-command-line-interface-tools-net-core-sdk-10-tools"></a>.NET Core コマンドライン インターフェイス ツール (.NET Core SDK 1.0 ツール)

.NET Core コマンドライン インターフェイス (CLI) は、.NET Core アプリケーションを開発するための新しい基本クロスプラットフォーム ツールチェーンです。 これは、統合開発環境 (IDE)、エディター、ビルド オーケストレーターなど、他の上位レベルのツールがビルド時に基にする主要なレイヤーなので、"基本" です。 

既定ではクロスプラットフォームでもあり、サポートされている各プラットフォーム上に同じアクセス領域を持ちます。 つまり、ツールの使用方法を学習するとき、サポートされているいずれのプラットフォームからも同じ方法でツールを使用できます。 

## <a name="installation"></a>インストール
他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。 シナリオにもよりますが、ネイティブ インストーラーで CLI をインストールしたり、インストール シェル スクリプトを利用したりできます。

開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。 CLI はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。 これらのインストーラーは、インストール直後、ユーザーが CLI を使用するために必要とする環境をインストールし、設定します。 ただし、コンピューター上で管理者特権も必要になります。 [.NET Core の概要ページ](https://aka.ms/dotnetcoregs)にインストール指示があります。

一方で、インストール スクリプトの場合、管理者特権は必要ありません。 ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。 スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。 詳細については、[インストール スクリプト参照](dotnet-install-script.md)に関するトピックを参照してください。 継続的インテグレーション (CI) ビルド サーバーで CLI を設定する方法については、[CLI および CI サーバー](using-ci-with-cli.md)に関するトピックを参照してください。 

既定では、CLI は SxS (side-by-side/横並び) 方式でインストールを実行します。 つまり、1 台のコンピューター上で複数のバージョンの CLI ツールが共存できます。 正しいバージョンを使用する方法の詳細については、[ドライバーに関するセクション](#driver)を参照してください。 

### <a name="what-commands-come-in-the-box"></a>既定で含まれるコマンド
既定では、次のコマンドがインストールされます。

* [new](dotnet-new.md)
* [migrate](dotnet-migrate.md)
* [restore](dotnet-restore.md)
* [run](dotnet-run.md)
* [build](dotnet-build.md)
* [test](dotnet-test.md)
* [publish](dotnet-publish.md)
* [pack](dotnet-pack.md)

また、プロジェクトごとに追加のコマンドをインポートしたり、独自のコマンドを追加することもできます。 さらなる詳細については、[機能拡張に関するセクション](#extensibility)を参照してください。 

## <a name="working-with-the-cli"></a>CLI の操作

さらなる詳細に進む前に、10,000 フィート ビューから CLI の操作がどのように見えるか確認しましょう。 次の例では、CLI 標準インストールから複数のコマンドを使用して、新しい単純なコンソール アプリケーションを初期化し、依存関係を復元して、アプリケーションをビルドしてから実行します。 

```console
dotnet new console
dotnet restore
dotnet build --output /stuff
dotnet /stuff/new.dll
```

前の例に示されるように、CLI ツールの使用方法にはパターンがあります。 そのパターン内で、各コマンドの次の&3; つの主要部分を特定できます。

1. [ドライバー ("dotnet")](#driver)
2. [コマンド ("動詞")](#the-verb)
3. [コマンド引数](#the-arguments)

### <a name="driver"></a>ドライバー
ドライバーの名前は [dotnet](dotnet.md) です。 これは最初に呼び出す部分です。 ドライバーには、次の&2; つの役割があります。

1. ポータブル アプリの実行
2. 動詞の実行

その役割は、コマンドラインで指定されている内容によって異なります。 最初のケースでは、`dotnet /path/to/your.dll` のように、`dotnet` が実行するポータブル アプリ DLL を指定します。 

2 つ目のケースでは、ドライバーは指定されたコマンドを呼び出そうとします。 これにより、CLI コマンド実行プロセスが起動します。 最初に、ドライバーは必要なツールのバージョンを決定します。 `version` プロパティを使用すると、[global.json](global-json.md) ファイルでバージョンを指定できます。 このプロパティを使用できない場合、ドライバーはディスク上にインストールされた最新バージョンを見つけ、そのバージョンを使用します。 バージョンが決定されたら、コマンドを実行します。 

### <a name="the-verb"></a>"動詞"
動詞は、単にアクションを実行するコマンドです。 `dotnet build` はコードをビルドします。 `dotnet publish` はコードを発行します。 動詞は、規則 `dotnet-{verb}` に従って名前付けされるコンソール アプリケーションとして実装されます。 すべてのロジックは、動詞を表すコンソール アプリケーションで実装されます。 

### <a name="the-arguments"></a>引数
コマンドラインで渡す引数は、呼び出される実際の動詞/コマンドへの引数です。 たとえば、`dotnet publish --output publishedapp` と入力すると、`--output` 引数が `publish` コマンドに渡されます。 

## <a name="types-of-application-portability"></a>アプリケーションの移植性の種類
CLI は、次の&2; つの主な方法でアプリケーションを移植できるようにします。

1. .NET Core がインストールされている任意の場所で実行される、完全に移植可能なアプリケーション
2. 自己完結型の展開

これらの両方の方法の詳細については、[.NET Core アプリケーション展開](../deploying/index.md)に関するトピックを参照してください。 

## <a name="migration-from-projectjson"></a>project.json からの移行
Preview 2 ツールおよび *project.json* プロジェクトを使用していた場合、コマンドの詳細およびプロジェクトの移行方法については、[dotnet migrate](dotnet-migrate.md) コマンドのドキュメントを参照してください。 

> [!NOTE]
> 現在、`dotnet migrate` コマンドでは、Preview 2 以前の *project.json* ファイルは移行されません。 

## <a name="extensibility"></a>機能拡張
もちろん、ワークフローで使用できるすべてのツールが Core CLI ツールに含まれるわけではありません。 ただし、.NET Core CLI には、プロジェクトに追加のツールを指定できるようにする機能拡張モデルがあります。 詳細については、[.NET Core CLI 機能拡張モデル](extensibility.md)に関するトピックを参照してください。

## <a name="summary"></a>まとめ
ここでは、CLI の最も重要な機能の簡潔な概要を示しました。 詳細については、このサイトのリファレンスおよび概念説明のトピックを参照してください。 使用できるその他のリソースもあります。
* [dotnet/CLI](https://github.com/dotnet/cli/) GitHub リポジトリ
* [作業開始手順](https://aka.ms/dotnetcoregs/)

