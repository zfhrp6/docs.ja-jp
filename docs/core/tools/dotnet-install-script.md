---
title: "dotnet-install スクリプト | Microsoft Docs"
description: ".NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。"
keywords: "dotnet-install, dotnet-install スクリプト, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 59b9c456-2bfd-4adc-8202-a1c6a0a6c787
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 8c5812828b5a19646d6ccbfe9f7cf2215889201f

---

#<a name="dotnet-install-scripts-reference"></a>dotnet-install スクリプト参照

> [!WARNING]
> このトピックは .NET Core Tools Preview 2 を対象としています。 .NET Core Tools RC4 バージョンについては、「[dotnet-install スクリプト参照 (.NET Core Tools RC4)](../preview3/tools/dotnet-install-script.md)」トピックを参照してください。

## <a name="name"></a>名前
`dotnet-install.ps1` | `dotnet-install.sh` - コマンド ライン インターフェイス (CLI) ツールと共有ランタイムをインストールするために使用するスクリプトです。

## <a name="synopsis"></a>構文
Windows の場合:

`dotnet-install.ps1 [-Channel] [-Version]
    [-InstallDir] [-Debug] [-NoPath] 
    [-SharedRuntime]`

macOS/Linux の場合:

`dotnet-install.sh [--channel] [--version]
    [--install-dir] [--debug] [--no-path] 
    [--shared-runtime]`

## <a name="description"></a>説明
`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。 スクリプトは [CLI GitHub リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/scripts/obtain)からダウンロードできます。 

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

インストールする CLI のバージョンです。3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。存在しない場合は、最新のものが使用されます。     

`-InstallDir [DIR]`

インストール先のパスです。 存在しない場合は、ディレクトリが作成されます。 既定値は *%LocalAppData%\Microsoft\dotnet*です。

`-Debug`

デバッグ シンボルを含むより大きなパッケージを使用するように指定する場合は `true`、それ以外の場合は `false`。 既定値は `false` です。

`-NoPath`

プレフィックス/installdir を現在のセッションのパスにエクスポートされないように指定する場合は `true`、それ以外の場合は `false`。 既定値は `false` です (つまり、パスが変更されます)。 これにより、インストール直後に CLI ツールが使用可能になります。 

`-SharedRuntime`

`true` の場合は共有ランタイム ビットのみがインストールされ、`false` の場合は SDK 全体がインストールされます。 既定値は `false` です。

### <a name="bash-macoslinux"></a>Bash (macOS/Linux)
`--channel [CHANNEL]`

インストール元のチャネル ("future", "preview", "production" など) です。 既定値は "production" です。

`--version [VERSION]`

インストールする CLI のバージョンです。3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合は、既定で `version` プロパティを含む最初の [global.json](global-json.md) に設定されます。存在しない場合は、最新のものが使用されます。     

`--install-dir [DIR]`

インストール先のパスです。 存在しない場合は、ディレクトリが作成されます。 既定値は `$HOME/.dotnet` です。

`--debug`

デバッグ シンボルを含むより大きなパッケージを使用するように指定する場合は `true`、それ以外の場合は `false`。 既定値は `false` です。

`--no-path`

プレフィックス/installdir を現在のセッションのパスにエクスポートされないように指定する場合は `true`、それ以外の場合は `false`。 既定値は `false` です (つまり、パスが変更されます)。 これにより、インストール直後に CLI ツールが使用可能になります。  

`--shared-runtime`

`true` の場合は共有ランタイム ビットのみがインストールされ、`false` の場合は SDK 全体がインストールされます。 既定値は `false` です。

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



<!--HONumber=Feb17_HO2-->


