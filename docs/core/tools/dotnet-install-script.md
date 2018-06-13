---
title: dotnet-install スクリプト
description: .NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: acdf49950ebb49751c55ae72b3f623e590489202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214381"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet-install スクリプト参照

## <a name="name"></a>name

`dotnet-install.ps1` | `dotnet-install.sh` - .NET Core CLI ツールと共有ランタイムをインストールするために使うスクリプトです。

## <a name="synopsis"></a>構文

Windows の場合:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

macOS/Linux の場合:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>説明

`dotnet-install` スクリプトは、.NET Core CLI ツールや共有ランタイムが含まれる .NET Core SDK の非管理者インストールを実行するために使用されます。

[.NET Core のメインの Web サイト](https://dot.net)でホストされる安定したバージョンを使用することをお勧めします。 スクリプトへの直接パスは次のとおりです。

* https://dot.net/v1/dotnet-install.sh (Bash、UNIX)
* https://dot.net/v1/dotnet-install.ps1 (PowerShell、Windows)

これらのスクリプトの主な有用性は、オートメーションのシナリオと管理者以外のインストールにおいてです。 2 つのスクリプトがあります。1 つは、Windows で動作する PowerShell スクリプトです。 その他のスクリプトは、Linux/macOS で動作する bash スクリプトです。 スクリプトの動作は両方とも同じです。 bash スクリプトは PowerShell のスイッチも読み取るので、Linux/macOS システムのスクリプトで PowerShell のスイッチを使うことができます。 

インストール スクリプトは CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `-InstallDir|--install-dir` で指定された場所へのインストールに進みます。 既定では、インストール スクリプトは SDK をダウンロードしてインストールします。 共有ランタイムの取得だけを行いたい場合は、`--shared-runtime` 引数を指定します。 

既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。 `--no-path` 引数を指定することによってこの既定の動作をオーバーライドします。 

スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。

`--version` 引数を使用して、特定のバージョンをインストールすることができます。 バージョンは 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。 省略した場合、`latest` バージョンを使用します。

## <a name="options"></a>オプション

`-Channel <CHANNEL>`

インストールのソース チャネルを指定します。 次の値を指定できます。

- `Current` - 最新リリース
- `LTS`- 長期的なサポート チャネル (サポートされている最新リリース)
- 特定のリリースを表す X.Y 形式の 2 部構成のバージョン (たとえば、`2.0` または `1.0`)
- ブランチ名 [たとえば、`master` ブランチの最新は `release/2.0.0`、`release/2.0.0-preview2`、または `master` ("bleeding edge (最先端)" のナイトリー リリース)]

既定値は `LTS` です。 .NET のサポート チャネルの詳細については、[.NET Core サポート ライフサイクル](https://www.microsoft.com/net/core/support)に関するトピックをご覧ください。

`-Version <VERSION>`

特定のビルド バージョンを表します。 次の値を指定できます。

- `latest` - チャネルの最新ビルド (`-Channel` オプションで使用)
- `coherent` - チャネルの最新のコヒーレント ビルド。最新の安定版パッケージの組み合わせを使用します (ブランチ名の `-Channel` オプションで使用)
- 特定のビルド バージョンを表す X.Y.Z 形式の 3 部構成のバージョン。`-Channel` オプションよりも優先されます。 例: `2.0.0-preview2-006120`

省略した場合、`-Version` の既定値は `latest` になります。

`-InstallDir <DIRECTORY>`

インストール パスを指定します。 存在しない場合は、ディレクトリが作成されます。 既定値は *%LocalAppData%\.dotnet* です。 ディレクトリに直接バイナリを配置していることに注意してください。

`-Architecture <ARCHITECTURE>`

インストールする .NET Core バイナリのアーキテクチャです。 可能性のある値は、`auto`、`x64`、および `x86` です。 既定値は `auto` です。これは実行中の OS アーキテクチャを示します。

`-SharedRuntime`

設定すると、このスイッチは共有ランタイムにインストールを制限します。 SDK 全体はインストールされません。

`-DryRun`

設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET Core CLI を一貫してインストールするために使用するコマンド ラインが表示されます。 たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。 また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。

`-NoPath`

設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。 既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。

`-AzureFeed`

Azure フィードの URL をインストーラーに指定します。 この値は変更しないことをお勧めします。 既定値は、`https://dotnetcli.azureedge.net/dotnet` です。

`-ProxyAddress`

設定すると、インストーラーで Web 要求を行うときにプロキシが使われます。 (Windows でのみ有効)

`--verbose`

診断情報を表示します。

`--help`

スクリプトのヘルプを出力します。

## <a name="examples"></a>使用例

最新の長期サポート (LST) バージョンを既定の場所にインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel LTS`

macOS/Linux の場合:

`./dotnet-install.sh --channel LTS`

2.0 チャネルから、最新バージョンを指定した場所にインストールします。

Windows の場合:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

macOS/Linux の場合:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

共有ランタイムの 1.1.0 バージョンをインストールします。

Windows の場合:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

macOS/Linux の場合:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

スクリプトを入手し、.NET Core CLI の 1 行コードのサンプルをインストールします。

Windows の場合:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

macOS/Linux の場合:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>関連項目

[.NET Core のリリース](https://github.com/dotnet/core/releases)   
[.NET Core ランタイムと SDK ダウンロード アーカイブ](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
