---
title: "dotnet-install スクリプト | Microsoft Docs"
description: ".NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。"
keywords: "dotnet-install, dotnet-install スクリプト, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 4a1f0c88fb1ccd6694f8d4f5687431646adbe000
ms.openlocfilehash: fbc1ce8d864a5c2150c61f4b8bf7cb8544921634
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-install-scripts-reference"></a>dotnet-install スクリプト参照

## <a name="name"></a>名前

`dotnet-install.ps1` | `dotnet-install.sh` - .NET Core コマンドライン インターフェイス (CLI) ツールと共有ランタイムをインストールするために使うスクリプトです。

## <a name="synopsis"></a>構文

Windows の場合:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]`

macOS/Linux の場合:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

## <a name="description"></a>説明

`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。 スクリプトは [CLI GitHub リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain)からダウンロードできます。 

これらのスクリプトの主な有用性は、オートメーションのシナリオと管理者以外のインストールにおいてです。 2 つのスクリプトがあります。1 つは、Windows で動作する PowerShell スクリプトです。 もう 1 つは、Linux/OS X で動作する bash スクリプトです。どちらのスクリプトも動作は同じです。 bash スクリプトは PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで PowerShell のスイッチを使うことができます。 

インストール スクリプトは CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `-InstallDir|--install-dir` で指定された場所へのインストールに進みます。 既定では、インストール スクリプトは SDK をダウンロードしてインストールします。 共有ランタイムの取得だけを行いたい場合は、`--shared-runtime` 引数を指定します。 

既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。 `--no-path` 引数を指定することによってこの既定の動作をオーバーライドします。 

スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。

`--version` 引数を使用して、特定のバージョンをインストールすることができます。 バージョンは 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合、既定で、`version` プロパティを含む、スクリプトが呼び出されるフォルダーの上の階層にある最初の [global.json](global-json.md) ファイルに設定されます。 それが存在しない場合は、最新のバージョンが使われます。

このスクリプトで `--debug` 引数を使って、デバッグ シンボルを含む SDK または共有ランタイム デバッグ バイナリを取得することもできます。 最初のインストールでこの実行に失敗し、デバッグ シンボルが必要であることに後になって気付いた場合は、`--debug` 引数とインストールした SDK のバージョンを指定してスクリプトを実行し直し、デバッグ シンボルを取得できます。 

## <a name="options"></a>オプション

注: オプションはスクリプトの実装によって異なります。 

### <a name="powershell-windows"></a>PowerShell (Windows)

`-Channel <CHANNEL>`

インストールのソース チャネルを指定します。 値は、`future`、`preview`、`production` です。 既定値は `production` です。

`-Version <VERSION>`

インストールする CLI のバージョンを指定します。 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。 それが存在しない場合は、最新のバージョンが使われます。

`-InstallDir <DIRECTORY>`

インストール パスを指定します。 存在しない場合は、ディレクトリが作成されます。 既定値は *%LocalAppData%\.dotnet* です。

`-Architecture <ARCHITECTURE>`

インストールする .NET Core バイナリのアーキテクチャです。 可能性のある値は、`auto`、`x64`、および `x86` です。 既定値は `auto` です。これは実行中の OS アーキテクチャを示します。

`-SharedRuntime`

設定すると、このスイッチは共有ランタイムにインストールを制限します。 SDK 全体はインストールされません。

`-DebugSymbols` (注を参照)

設定すると、インストールにデバッグ シンボルが含まれます。

> [!NOTE]
> `-DebugSymbols` スイッチは現在は使用できませんが、将来のリリースでは計画されています。

`-DryRun`

設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET CLI を常にインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。 また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

`-NoPath`

設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

`-AzureFeed`

Azure フィードの URL をインストーラーに指定します。 この値は変更しないことをお勧めします。 既定値は、`https://dotnetcli.azureedge.net/dotnet` です。

`-ProxyAddress`

設定すると、インストーラーで Web 要求を行うときにプロキシが使われます。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]`

`--channel <CHANNEL>`

インストールのソース チャネルを指定します。 値は、`future`、`dev`、`production` です。 既定値は `production` です。

`--version <VERSION>`

インストールする CLI のバージョンを指定します。 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。 それが存在しない場合は、最新のバージョンが使われます。

`--install-dir <DIRECTORY>`

インストール パスを指定します。 存在しない場合は、ディレクトリが作成されます。 既定値は `$HOME/.dotnet` です。

`--architecture <ARCHITECTURE>`

インストールする .NET Core バイナリのアーキテクチャです。 指定できる値は、`auto`、`x64`、`amd64` です。 既定値は `auto` です。これは実行中の OS アーキテクチャを示します。

`--shared-runtime`

設定すると、このスイッチは共有ランタイムにインストールを制限します。 SDK 全体はインストールされません。

`--debug-symbols`

設定すると、インストールにデバッグ シンボルが含まれます。

> [!NOTE]
> このスイッチは現在は使えませんが、将来のリリースでは計画されています。

`--dry-run`

設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET CLI を常にインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。 また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

`--no-path`

設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

`--verbose`

診断情報を表示します。

`--azure-feed`

Azure フィードの URL をインストーラーに指定します。 この値は変更しないことをお勧めします。 既定値は、`https://dotnetcli.azureedge.net/dotnet` です。

`--help`

スクリプトのヘルプを出力します。

## <a name="examples"></a>例

最新の開発バージョンを既定の場所にインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel Future`

macOS/Linux の場合:

`./dotnet-install.sh --channel Future`

指定した場所に最新のプレビューをインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux の場合:

`./dotnet-install.sh --channel preview --install-dir ~/cli`
