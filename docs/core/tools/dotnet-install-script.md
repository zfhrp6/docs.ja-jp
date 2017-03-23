---
title: "dotnet-install スクリプト | Microsoft Docs"
description: ".NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。"
keywords: "dotnet-install, dotnet-install スクリプト, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
translationtype: Human Translation
ms.sourcegitcommit: 99254f84873003496ee00214d55ff908f9fd47d3
ms.openlocfilehash: 6301fb61be27d7dac6ead57159c0d9461b3eacb5
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-install-scripts-reference"></a>dotnet-install スクリプト参照

## <a name="name"></a>名前

`dotnet-install.ps1` | `dotnet-install.sh` - .NET Core コマンドライン インターフェイス (CLI) ツールと共有ランタイムをインストールするために使用するスクリプトです。

## <a name="synopsis"></a>構文
Windows の場合:

```
dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture]
    [-SharedRuntime] [-DebugSymbols] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress]
```

macOS/Linux の場合:

```
dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
```

## <a name="description"></a>説明
`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。 スクリプトは [CLI GitHub リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain)からダウンロードできます。 

その主なユース ケースは、自動化シナリオと非管理者インストールに役立ちます。 このスクリプトは&2; つ (Windows で動作する PowerShell 用と、Linux/OS X で動作する bash スクリプト用にそれぞれ&1; つずつ) あります。両方とも動作は同じです。 bash スクリプトでは PowerShell スイッチも "認識される" ため、全体で使用できます。 

インストール スクリプトは CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `--install-dir` で指定された場所へのインストールに進みます。 既定では、インストール スクリプトは SDK をダウンロードしてインストールします。共有ランタイムのみを取得する場合は、`--shared-runtime` 引数を指定できます。 

既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。 `--no-path` 引数を使用すれば、これをオーバーライドできます。 

スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールしてください。

`--version` 引数を使用して、特定のバージョンをインストールすることができます。 バージョンは 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合、既定で、`version` プロパティを含む、スクリプトが呼び出されるフォルダーの上の階層にある最初の [global.json](global-json.md) ファイルに設定されます。 存在しない場合は、最新のものが使用されます。

このスクリプトで `--debug` 引数を使用して、デバッグ シンボルを含む SDK または共有ランタイム デバッグ バイナリを取得することもできます。 最初のインストール時にこれを行わず、後でデバッグ シンボルが必要であることに気付いた場合は、この引数と、インストールしたビットのバージョンを指定してスクリプトを再実行できます。 

## <a name="options"></a>オプション
オプションはスクリプトの実装によって異なります。 

### <a name="powershell-windows"></a>PowerShell (Windows)
`-Channel [CHANNEL]`

インストール元のチャネル (`future`、`preview`、`production` など) です。 既定値は `production` です。

`-Version [VERSION]`

インストールする CLI のバージョン。 3 部構成のバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。 存在しない場合は、最新のものが使用されます。

`-InstallDir [DIR]`

インストール先のパスです。 存在しない場合は、ディレクトリが作成されます。 既定値は *%LocalAppData%\.dotnet* です。

`-Architecture [ARCH]`

インストールする .NET Core バイナリのアーキテクチャ。 使用できる値は &lt;auto&gt;、x64、および x86 です。 既定値は &lt;auto&gt; です。これは実行中の OS アーキテクチャを示します。

`-SharedRuntime`

設定すると、SDK 全体ではなく共有ランタイム ビットのみがインストールされます。

`-DebugSymbols`

設定すると、インストールにデバッグ シンボルが含まれます。

> [!NOTE]
> このスイッチはまだ機能しません。

`-DryRun`

設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET CLI を常にインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。
また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

`-NoPath`

設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

`-AzureFeed`

このインストーラーで使用される Azure フィードの URL。 変更しないことをお勧めします。 既定値は、`https://dotnetcli.azureedge.net/dotnet` です。

`-ProxyAddress`

設定すると、インストーラーで Web 要求を行うときにプロキシが使用されます。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture]
    [--shared-runtime] [--debug-symbols] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--help]
`

`--channel [CHANNEL]`

インストール元のチャネル ("future"、"dev"、"production" など) です。 既定値は "production" です。

`--version [VERSION]`

インストールする CLI のバージョン。 3 部構成のバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。 存在しない場合は、最新のものが使用されます。

`--install-dir [DIR]`

インストール先のパスです。 存在しない場合は、ディレクトリが作成されます。 既定値は `$HOME/.dotnet` です。

`--architecture [ARCH]`

インストールする .NET バイナリのアーキテクチャ。 使用できる値は &lt;auto&gt;、x64、および amd64 です。 既定値は &lt;auto&gt; です。これは実行中の OS アーキテクチャを示します。

`--shared-runtime`

設定すると、SDK 全体ではなく共有ランタイム ビットのみがインストールされます。

`--debug-symbols`

設定すると、インストールにデバッグ シンボルが含まれます。

> [!NOTE]
> このスイッチはまだ機能しません。

`--dry-run`

設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET CLI を常にインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。
また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

`--no-path`

設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

`--verbose`

診断情報を表示します。

`--azure-feed`

このインストーラーで使用される Azure フィードの URL。 変更しないことをお勧めします。 既定値は、`https://dotnetcli.azureedge.net/dotnet` です。

`--help`

スクリプトのヘルプを出力します。

## <a name="examples"></a>例

開発用の最新バージョンを既定の場所にインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel Future`

macOS/Linux の場合:

`./dotnet-install.sh --channel Future`

指定した場所に最新のプレビューをインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel preview -InstallDir C:\cli`

macOS/Linux の場合:

`./dotnet-install.sh --channel preview --install-dir ~/cli`
