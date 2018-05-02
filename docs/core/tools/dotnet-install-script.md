---
title: dotnet-install スクリプト
description: .NET Core CLI ツールと共有ランタイムをインストールする dotnet-install スクリプトについて説明します。
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 96336df087ea2ad01584010f0715ad31e079b663
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="a26c6-103">dotnet-install スクリプト参照</span><span class="sxs-lookup"><span data-stu-id="a26c6-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="a26c6-104">name</span><span class="sxs-lookup"><span data-stu-id="a26c6-104">Name</span></span>

<span data-ttu-id="a26c6-105">`dotnet-install.ps1` | `dotnet-install.sh` - .NET Core CLI ツールと共有ランタイムをインストールするために使うスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a26c6-106">構文</span><span class="sxs-lookup"><span data-stu-id="a26c6-106">Synopsis</span></span>

<span data-ttu-id="a26c6-107">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="a26c6-108">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="a26c6-109">説明</span><span class="sxs-lookup"><span data-stu-id="a26c6-109">Description</span></span>

<span data-ttu-id="a26c6-110">`dotnet-install` スクリプトは、.NET Core CLI ツールや共有ランタイムが含まれる .NET Core SDK の非管理者インストールを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="a26c6-111">[.NET Core のメインの Web サイト](https://dot.net)でホストされる安定したバージョンを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="a26c6-112">スクリプトへの直接パスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="a26c6-113">https://dot.net/v1/dotnet-install.sh (Bash、UNIX)</span><span class="sxs-lookup"><span data-stu-id="a26c6-113">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="a26c6-114">https://dot.net/v1/dotnet-install.ps1 (PowerShell、Windows)</span><span class="sxs-lookup"><span data-stu-id="a26c6-114">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="a26c6-115">これらのスクリプトの主な有用性は、オートメーションのシナリオと管理者以外のインストールにおいてです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="a26c6-116">2 つのスクリプトがあります。1 つは、Windows で動作する PowerShell スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="a26c6-117">その他のスクリプトは、Linux/macOS で動作する bash スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="a26c6-118">スクリプトの動作は両方とも同じです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="a26c6-119">bash スクリプトは PowerShell のスイッチも読み取るので、Linux/macOS システムのスクリプトで PowerShell のスイッチを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="a26c6-120">インストール スクリプトは CLI ビルド ドロップから ZIP/tarball ファイルをダウンロードし、既定の場所または `-InstallDir|--install-dir` で指定された場所へのインストールに進みます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="a26c6-121">既定では、インストール スクリプトは SDK をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="a26c6-122">共有ランタイムの取得だけを行いたい場合は、`--shared-runtime` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="a26c6-123">既定では、スクリプトはインストールの場所を現在のセッションの $PATH に追加します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="a26c6-124">`--no-path` 引数を指定することによってこの既定の動作をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-124">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="a26c6-125">スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="a26c6-126">`--version` 引数を使用して、特定のバージョンをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="a26c6-127">バージョンは 3 つの部分からなるバージョン (1.0.0-13232 など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a26c6-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="a26c6-128">省略した場合、`latest` バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="a26c6-129">オプション</span><span class="sxs-lookup"><span data-stu-id="a26c6-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="a26c6-130">インストールのソース チャネルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="a26c6-131">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-131">The possible values are:</span></span>

- <span data-ttu-id="a26c6-132">`Current` - 最新リリース</span><span class="sxs-lookup"><span data-stu-id="a26c6-132">`Current` - Current release</span></span>
- <span data-ttu-id="a26c6-133">`LTS`- 長期的なサポート チャネル (サポートされている最新リリース)</span><span class="sxs-lookup"><span data-stu-id="a26c6-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="a26c6-134">特定のリリースを表す X.Y 形式の 2 部構成のバージョン (たとえば、`2.0` または `1.0`)</span><span class="sxs-lookup"><span data-stu-id="a26c6-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="a26c6-135">ブランチ名 [たとえば、`master` ブランチの最新は `release/2.0.0`、`release/2.0.0-preview2`、または `master` ("bleeding edge (最先端)" のナイトリー リリース)]</span><span class="sxs-lookup"><span data-stu-id="a26c6-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="a26c6-136">既定値は `LTS` です。</span><span class="sxs-lookup"><span data-stu-id="a26c6-136">The default value is `LTS`.</span></span> <span data-ttu-id="a26c6-137">.NET のサポート チャネルの詳細については、[.NET Core サポート ライフサイクル](https://www.microsoft.com/net/core/support)に関するトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a26c6-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="a26c6-138">特定のビルド バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-138">Represents a specific build version.</span></span> <span data-ttu-id="a26c6-139">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-139">The possible values are:</span></span>

- <span data-ttu-id="a26c6-140">`latest` - チャネルの最新ビルド (`-Channel` オプションで使用)</span><span class="sxs-lookup"><span data-stu-id="a26c6-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="a26c6-141">`coherent` - チャネルの最新のコヒーレント ビルド。最新の安定版パッケージの組み合わせを使用します (ブランチ名の `-Channel` オプションで使用)</span><span class="sxs-lookup"><span data-stu-id="a26c6-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="a26c6-142">特定のビルド バージョンを表す X.Y.Z 形式の 3 部構成のバージョン。`-Channel` オプションよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="a26c6-143">例: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="a26c6-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="a26c6-144">省略した場合、`-Version` の既定値は `latest` になります。</span><span class="sxs-lookup"><span data-stu-id="a26c6-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="a26c6-145">インストール パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-145">Specifies the installation path.</span></span> <span data-ttu-id="a26c6-146">存在しない場合は、ディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="a26c6-147">既定値は *%LocalAppData%\.dotnet* です。</span><span class="sxs-lookup"><span data-stu-id="a26c6-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="a26c6-148">ディレクトリに直接バイナリを配置していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a26c6-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="a26c6-149">インストールする .NET Core バイナリのアーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="a26c6-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="a26c6-150">可能性のある値は、`auto`、`x64`、および `x86` です。</span><span class="sxs-lookup"><span data-stu-id="a26c6-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="a26c6-151">既定値は `auto` です。これは実行中の OS アーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="a26c6-152">設定すると、このスイッチは共有ランタイムにインストールを制限します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="a26c6-153">SDK 全体はインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a26c6-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="a26c6-154">設定すると、スクリプトでインストールは実行されませんが、現在要求されているバージョンの .NET Core CLI を一貫してインストールするために使用するコマンド ラインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="a26c6-155">たとえば、バージョン `latest` を指定すると、そのバージョンのリンクが表示されるので、ビルド スクリプトで確定的にこのコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="a26c6-156">また、自分でインストールまたはダウンロードしたい場合、バイナリの場所も表示されます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="a26c6-157">設定すると、prefix/installdir は現在のセッションのパスにはエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="a26c6-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="a26c6-158">既定では、スクリプトによって PATH が変更されます。その結果、インストール後すぐに CLI ツールを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a26c6-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="a26c6-159">Azure フィードの URL をインストーラーに指定します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="a26c6-160">この値は変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="a26c6-161">既定値は、`https://dotnetcli.azureedge.net/dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="a26c6-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="a26c6-162">設定すると、インストーラーで Web 要求を行うときにプロキシが使われます。</span><span class="sxs-lookup"><span data-stu-id="a26c6-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="a26c6-163">(Windows でのみ有効)</span><span class="sxs-lookup"><span data-stu-id="a26c6-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="a26c6-164">診断情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="a26c6-165">スクリプトのヘルプを出力します。</span><span class="sxs-lookup"><span data-stu-id="a26c6-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="a26c6-166">使用例</span><span class="sxs-lookup"><span data-stu-id="a26c6-166">Examples</span></span>

<span data-ttu-id="a26c6-167">最新の長期サポート (LST) バージョンを既定の場所にインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="a26c6-168">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="a26c6-169">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="a26c6-170">2.0 チャネルから、最新バージョンを指定した場所にインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="a26c6-171">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="a26c6-172">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="a26c6-173">共有ランタイムの 1.1.0 バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="a26c6-174">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="a26c6-175">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="a26c6-176">スクリプトを入手し、.NET Core CLI の 1 行コードのサンプルをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a26c6-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="a26c6-177">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="a26c6-178">macOS/Linux の場合:</span><span class="sxs-lookup"><span data-stu-id="a26c6-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="a26c6-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="a26c6-179">See also</span></span>

<span data-ttu-id="a26c6-180">[.NET Core のリリース](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="a26c6-180">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="a26c6-181">.NET Core ランタイムと SDK ダウンロード アーカイブ</span><span class="sxs-lookup"><span data-stu-id="a26c6-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
