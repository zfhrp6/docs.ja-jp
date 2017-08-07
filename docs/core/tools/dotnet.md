---
title: "dotnet コマンド - .NET Core CLI"
description: "dotnet コマンド (.NET Core CLI ツールの一般的なドライバー) とその使用法について説明します。"
keywords: "dotnet, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/20/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 256e468e-eaaa-4715-b5fb-8cbddcf80e69
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1f377ea55278ae382f56a0dc0cbcf1bb99f49eca
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-command"></a>dotnet コマンド

## <a name="name"></a>名前

`dotnet` - コマンドラインのコマンドを実行するための一般的なドライバーです。

## <a name="synopsis"></a>構文

`dotnet [command] [arguments] [--version] [--info] [-d|--diagnostics] [-v|--verbose] [--fx-version] [--additionalprobingpath] [-h|--help]`

## <a name="description"></a>説明

`dotnet` は、コマンド ライン インターフェイス (CLI) ツールチェーンの一般的なドライバーです。 単独で呼び出され、簡単な使用方法を提供します。

特定の機能がそれぞれコマンドとして実装されます。 機能を使用するには、[`dotnet build`](dotnet-build.md) のように、`dotnet` の後にコマンドを指定します。 コマンドに続く引数はすべて独自の引数です。

`dotnet` が単独でコマンドとして使用されるのは、[フレームワークに依存するアプリ](../deploying/index.md)を実行する場合のみです。 アプリケーションを実行する場合は、`dotnet` の動詞の後にアプリケーション DLL を指定します (`dotnet myapp.dll` など)。

## <a name="options"></a>オプション

`-v|--verbose`

詳細出力を有効にします。

`-d|--diagnostics`

診断出力を有効にします。

`--fx-version <VERSION>`

アプリケーションを実行するために使用するインストール済みの Shared Framework のバージョンです。

`--additionalprobingpath <PATH>`

プローブ ポリシーとプローブするアセンブリを含むパスです。

`--version`

CLI ツールのバージョンを印刷します。

`--info`

現在のオペレーティング システム、バージョンのコミット SHA、およびその他の情報など、CLI ツールと環境の詳細情報を印刷します。

`-h|--help`

コマンドの短いヘルプを印刷します。 `dotnet` で使用すると、使用可能なコマンドのリストも印刷されます。

## <a name="dotnet-commands"></a>dotnet コマンド

### <a name="general"></a>全般

コマンド | 関数
--- | ---
[dotnet-build](dotnet-build.md) | .NET Core アプリケーションをビルドします。
[dotnet-clean](dotnet-clean.md) | クリーン ビルド出力。
[dotnet-migrate](dotnet-migrate.md) | 有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。
[dotnet-msbuild](dotnet-msbuild.md) | MSBuild コマンド ラインへのアクセスを提供します。
[dotnet-new](dotnet-new.md) | 指定されたテンプレートの C# または F# プロジェクトを初期化します。
[dotnet-pack](dotnet-pack.md) | コードの NuGet パッケージを作成します。
[dotnet-publish](dotnet-publish.md) | .NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。
[dotnet-restore](dotnet-restore.md) | 指定されたアプリケーションの依存関係を復元します。
[dotnet-run](dotnet-run.md) | ソースからアプリケーションを実行します。
[dotnet-sln](dotnet-sln.md) | ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。
[dotnet-test](dotnet-test.md) | テスト ランナーを使用してテストを実行します。

### <a name="project-references"></a>プロジェクト参照

コマンド | 関数
--- | ---
[dotnet-add 参照](dotnet-add-reference.md) | プロジェクト参照を追加します。
[dotnet-list 参照](dotnet-list-reference.md) | プロジェクト参照をリストします。
[dotnet-remove 参照](dotnet-remove-reference.md) | プロジェクト参照を削除します。

### <a name="nuget-packages"></a>NuGet パッケージ

コマンド | 関数
--- | ---
[dotnet-add パッケージ](dotnet-add-package.md) | NuGet パッケージを追加します。
[dotnet-remove パッケージ](dotnet-remove-package.md) | NuGet パッケージを削除します。

### <a name="nuget-commands"></a>NuGet コマンド

コマンド | 関数
--- | ---
[dotnet-nuget delete](dotnet-nuget-delete.md) | サーバーからパッケージを削除または一覧から削除します。
[dotnet-nuget locals](dotnet-nuget-locals.md) | HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。
[dotnet-nuget push](dotnet-nuget-push.md) | パッケージをサーバーにプッシュして発行します。

## <a name="examples"></a>例

コンパイルして実行できるサンプルの .NET Core コンソール アプリケーションを初期化します。

`dotnet new console`

指定されたアプリケーションの依存関係を復元します。

`dotnet restore`

指定されたディレクトリにプロジェクトとその依存関係をビルドします。

`dotnet build`

`myapp.dll` という名前のフレームワークに依存するアプリを実行します。

`dotnet myapp.dll`

## <a name="environment-variables"></a>環境変数

`DOTNET_PACKAGES`

プライマリ パッケージのキャッシュです。 設定されていない場合は、既定で `$HOME/.nuget/packages` (Unix の場合) または `%HOME%\NuGet\Packages` (Windows の場合) になります。

`DOTNET_SERVICING`

ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。 `true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。 設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。

