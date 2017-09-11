---
title: "継続的インテグレーション (CI) で .NET Core SDK とツールを使用する"
description: ".NET Core SDK とそのツールをビルド サーバーで使用する方法に関する情報。"
keywords: ".NET, .NET Core, 継続的インテグレーション, ci, ビルド, 自動化, Travis CI, AppVeyor, Visual Studio Team Services, vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 67c08dd9804f6b51961be250033161427159e66e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="75b3c-104">継続的インテグレーション (CI) で .NET Core SDK とツールを使用する</span><span class="sxs-lookup"><span data-stu-id="75b3c-104">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="75b3c-105">概要</span><span class="sxs-lookup"><span data-stu-id="75b3c-105">Overview</span></span>

<span data-ttu-id="75b3c-106">この文書では、.NET Core SDK とそのツールをビルド サーバーで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-106">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="75b3c-107">.NET Core ツールセットは対話式と自動の両方に対応しています。対話式の場合、開発者はコマンド プロンプトにコマンドを入力します。自動の場合、継続的インテグレーション (CI) サーバーがビルド スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-107">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="75b3c-108">コマンド、オプション、入力、出力は同じです。ユーザーは、ツールの取得方法とアプリを構築するシステムだけを指定します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-108">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="75b3c-109">このドキュメントでは、CI のツール取得のシナリオと、ビルド スクリプトの設計と構造化の方法に関する推奨事項を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-109">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="75b3c-110">CI ビルド サーバーのインストール オプション</span><span class="sxs-lookup"><span data-stu-id="75b3c-110">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="75b3c-111">ネイティブ インストーラーの使用</span><span class="sxs-lookup"><span data-stu-id="75b3c-111">Using the native installers</span></span>

<span data-ttu-id="75b3c-112">macOS、Linux、Windows の場合、ネイティブ インストーラーを利用できます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-112">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="75b3c-113">このインストーラーは、ビルド サーバーへの admin (sudo) アクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="75b3c-113">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="75b3c-114">ネイティブ インストーラーを使用することの利点は、ツールを実行するために必要なあらゆるネイティブ依存性がインストールされることです。</span><span class="sxs-lookup"><span data-stu-id="75b3c-114">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="75b3c-115">ネイティブ インストーラーはまた、システム全体に SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="75b3c-115">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="75b3c-116">macOS をご利用の場合、PKG インストーラーをお使いください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-116">macOS users should use the PKG installers.</span></span> <span data-ttu-id="75b3c-117">Linux の場合、フィードベースのパッケージ マネージャーを利用できます。Ubuntu の apt-get や CentOS の yum などです。あるいは、パッケージ自体、DEB または RPM を利用できます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-117">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="75b3c-118">Windows の場合、MSI インストーラーをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-118">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="75b3c-119">安定性に優れた最新のバイナリは「[Get Started with .NET Core](https://aka.ms/dotnetcoregs)」 (.NET Core を始める) にあります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-119">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="75b3c-120">最新の (安定性に欠ける可能性がある) プレリリース ツールを使用する場合、[dotnet/cli GitHub リポジトリ](https://github.com/dotnet/cli#installers-and-binaries)のリンクをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-120">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="75b3c-121">Linux ディストリビューションの場合、`tar.gz` アーカイブ (別名、`tarballs`) をご利用いただけます。アーカイブ内のインストール スクリプトを利用して .NET Core をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-121">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="75b3c-122">インストーラー スクリプトの使用</span><span class="sxs-lookup"><span data-stu-id="75b3c-122">Using the installer script</span></span>

<span data-ttu-id="75b3c-123">インストーラー スクリプトを使用すると、ビルド サーバーで管理者以外のインストールが可能になり、ツールの取得を簡単に自動化できます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-123">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="75b3c-124">スクリプトにツールがダウンロードされ、既定の場所か指定された場所に抽出されます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-124">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="75b3c-125">インストールするツールのバージョンと、SDK 全体をインストールするか、それとも共有ランタイムだけをインストールするかも指定できます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-125">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="75b3c-126">インストーラー スクリプトは、ビルドの開始時に実行され、必要なバージョンの SDK を取得し、インストールするように自動化されています。</span><span class="sxs-lookup"><span data-stu-id="75b3c-126">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="75b3c-127">*必要なバージョン*とは、プロジェクトのビルドに必要な SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="75b3c-127">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="75b3c-128">このスクリプトでは、サーバーのローカル ディレクトリに SDK をインストールし、インストールした場所からツールを実行し、ビルド後にクリーンアップできます (あるいは、CI サービスにクリーンアップさせます)。</span><span class="sxs-lookup"><span data-stu-id="75b3c-128">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="75b3c-129">これにより、ビルド プロセス全体にカプセル化と分離性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-129">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="75b3c-130">インストール スクリプト参照は [dotnet-install](dotnet-install-script.md) トピックにあります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-130">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="75b3c-131">インストーラー スクリプトの使用時、ネイティブ依存性は自動的にはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="75b3c-131">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="75b3c-132">オペレーティング システムにネイティブ依存性がない場合、それをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-132">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="75b3c-133">前提条件の一覧は [.NET Core ネイティブ前提条件](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-133">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="75b3c-134">CI セットアップ例</span><span class="sxs-lookup"><span data-stu-id="75b3c-134">CI setup examples</span></span>

<span data-ttu-id="75b3c-135">このセクションでは、PowerShell またはバッシュ スクリプトを利用した手動セットアップについて説明し、SaaS (サービスとしてのソフトウェア) CI (継続的インテグレーション) ソリューションをいくつか紹介します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-135">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="75b3c-136">SaaS CI ソリューションとしては、[Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/)、[Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview) を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-136">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://www.visualstudio.com/docs/build/overview).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="75b3c-137">手動セットアップ</span><span class="sxs-lookup"><span data-stu-id="75b3c-137">Manual setup</span></span>

<span data-ttu-id="75b3c-138">各 SaaS サービスには、ビルド プロセスを作成し、構成するための独自の方法があります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-138">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="75b3c-139">一覧に記載されている以外の SaaS ソリューションを使用する場合、あるいは事前にパッケージに含まれているサポート以上のカスタマイズが必要な場合、少なくとも一部に手動構成が必要になります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-139">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="75b3c-140">全般的に、手動セットアップでは、あるバージョンのツール (あるいはツールの最新のナイトリー ビルド) を取得し、ビルド スクリプトを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-140">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="75b3c-141">PowerShell またはバッシュ スクリプトを使用し、.NET Core コマンドを調整したり、プロジェクト ファイルを使用してビルド プロセスの概要を伝えたりできます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-141">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="75b3c-142">[オーケストレーション セクション](#orchestrating-the-build)で、これらのオプションについて詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="75b3c-142">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="75b3c-143">手動 CI ビルド サーバー セットアップを実行するスクリプトを作成したら、それを開発マシンで使用し、テスト目的でコードをローカルでビルドします。</span><span class="sxs-lookup"><span data-stu-id="75b3c-143">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="75b3c-144">スクリプトがローカルで問題なく動作していることを確認したら、CI ビルド サーバーに展開します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-144">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="75b3c-145">比較的単純な PowerShell スクリプトで、.NET Core SDK を取得し、Windows ビルド サーバーにインストールする方法を実演します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-145">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the 
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the 
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it 
#   does, it's removed. This is not strictly required, but it's a 
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the 
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://raw.githubusercontent.com/dotnet/cli/rel/1.0.1/scripts/obtain/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the 
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the 
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="75b3c-146">スクリプトの終わりで、自分のビルド プロセスの実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-146">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="75b3c-147">スクリプトはツールを取得し、ビルド プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-147">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="75b3c-148">UNIX マシンの場合、次のバッシュ スクリプトが PowerShell スクリプトに記載されているアクションを同様の方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-148">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
# Do not use an INSTALLDIR path containing spaces:
#   https://github.com/dotnet/cli/issues/5281
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://raw.githubusercontent.com/dotnet/cli/rel/1.0.1/scripts/obtain/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="75b3c-149">Travis CI</span><span class="sxs-lookup"><span data-stu-id="75b3c-149">Travis CI</span></span>

<span data-ttu-id="75b3c-150">`csharp` 言語と `dotnet` キーを使用して .NET Core SDK をインストールするように [Travis CI](https://travis-ci.org/) を構成できます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-150">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="75b3c-151">詳細については、公式 Travis CI ドキュメントの「[Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/)」 (C#、F#、または Visual Basic プロジェクトのビルド) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-151">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="75b3c-152">Travis CI 情報にアクセスするときは、コミュニティが保守管理している `language: csharp` 言語識別子は F# や Mono を含む、あらゆる .NET 言語で機能することにご留意ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-152">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="75b3c-153">Travis CI は、*ビルド マトリックス*において、macOS (OS X 10.11、OS X 10.12) ジョブと Linux (Ubuntu 14.04) ジョブの両方を実行できます。ビルド マトリックスでは、ランタイム、環境、除外/追加の組み合わせを指定し、アプリのビルド組み合わせを範囲に含めます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-153">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="75b3c-154">詳細については、[.travis.yml サンプル](https://github.com/dotnet/docs/blob/master/.travis.yml) ファイルと Travis CI ドキュメントの「[Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build)」 (ビルドをカスタマイズする) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-154">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="75b3c-155">MSBuild ベースのツールのパッケージには、LTS (1.0.x) ランタイムと Current (1.1.x) ランタイムが含まれています。SDK をインストールすることで、ビルドに必要なすべてが与えられます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-155">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="75b3c-156">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="75b3c-156">AppVeyor</span></span>

<span data-ttu-id="75b3c-157">[AppVeyor](https://www.appveyor.com/) は、`Visual Studio 2017` worker イメージで .NET Core 1.0.1 SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="75b3c-157">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="75b3c-158">別のバージョンの .NET Core SDK と他のビルド イメージを利用できます。詳細については、AppVeyor ドキュメントの 「[appveyor.yml サンプル](https://github.com/dotnet/docs/blob/master/appveyor.yml)」と 「[Build worker イメージ](https://www.appveyor.com/docs/build-environment/#build-worker-images)」 トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-158">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="75b3c-159">.NET Core SDK バイナリがインストール スクリプトを利用してダウンロードされ、解凍され、`PATH` 環境変数に追加されます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="75b3c-160">複数バージョンの .NET Core SDK との統合テストを実行するためにビルド マトリックスを追加する:</span><span class="sxs-lookup"><span data-stu-id="75b3c-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="75b3c-161">Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="75b3c-161">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="75b3c-162">以下のいずれかの手法で .NET Core プロジェクトをビルドするように、Visual Studio Team Services (VSTS) を構成します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-162">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="75b3c-163">コマンドを利用し、[手動セットアップ手順](#manual-setup)からスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="75b3c-164">.NET Core ツールを使用するように構成されたいくつかの VSTS 組み込みビルド タスクで構成されるビルドを作成します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-164">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="75b3c-165">いずれのソリューションも有効です。</span><span class="sxs-lookup"><span data-stu-id="75b3c-165">Both solutions are valid.</span></span> <span data-ttu-id="75b3c-166">ツールはビルドの一部としてダウンロードしているので、手動セットアップ スクリプトを使用し、取得したツールのバージョンを管理します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="75b3c-167">ビルドはスクリプトから実行されます。そのスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="75b3c-168">このトピックでは、手動オプションについてのみ説明します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-168">This topic only covers the manual option.</span></span> <span data-ttu-id="75b3c-169">VSTS ビルド タスクでビルドを作成する方法については、VSTS の「[Continuous integration and deployment](https://www.visualstudio.com/docs/build/overview)」 (継続的インテグレーションと展開) トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-169">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://www.visualstudio.com/docs/build/overview) topic.</span></span>

<span data-ttu-id="75b3c-170">VSTS で手動セットアップ スクリプトを使用するには、新しいビルド定義を作成し、ビルド手順で実行するスクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-170">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="75b3c-171">それには VSTS ユーザー インターフェイスを使います。</span><span class="sxs-lookup"><span data-stu-id="75b3c-171">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="75b3c-172">最初に新しいビルド定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-172">Start by creating a new build definition.</span></span> <span data-ttu-id="75b3c-173">作成するビルドの種類を定義するためのオプションを指定する画面が表示されたら、**[空]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![ビルド定義で空を選択する](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="75b3c-175">ビルドするリポジトリを構成すると、ビルド定義が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="75b3c-176">**[ビルド ステップの追加...]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-176">Select **Add build step**:</span></span>

   ![ビルド ステップの追加](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="75b3c-178">**[タスク カタログ]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75b3c-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="75b3c-179">このカタログには、ビルドで使用するタスクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="75b3c-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="75b3c-180">スクリプトがあるので、**PowerShell: Run a PowerShell スクリプト**の **[追加]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![PowerShell スクリプトの追加手順](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="75b3c-182">ビルド手順を構成します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-182">Configure the build step.</span></span> <span data-ttu-id="75b3c-183">ビルドしているリポジトリからスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-183">Add the script from the repository that you're building:</span></span>

   ![実行する PowerShell スクリプトを指定する](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="75b3c-185">ビルドの調整</span><span class="sxs-lookup"><span data-stu-id="75b3c-185">Orchestrating the build</span></span>

<span data-ttu-id="75b3c-186">この文書はその大半で .NET Core ツールの取得方法とさまざまな CI サービスの構成方法について説明しています。.NET Core でコードを調整する (*実際にビルドする*) 方法に関する情報はありません。</span><span class="sxs-lookup"><span data-stu-id="75b3c-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="75b3c-187">ビルド プロセスの構造化方法の選択肢は、ここでは取り上げることができないさまざまな要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-187">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="75b3c-188">[Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/)、[VSTS](https://www.visualstudio.com/docs/build/overview) でビルドを調整する方法については、それぞれの文書に記載されている資料とサンプルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-188">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://www.visualstudio.com/docs/build/overview) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="75b3c-189">.NET Core ツールを利用して .NET Core コードのビルド プロセスを構造化するとき、通常、2 つの手法があります。MSBuild を直接利用するか、.NET Core コマンドライン コマンドを利用します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="75b3c-190">いずれの手法を採用するかは、手法と複雑性との兼ね合いで使いやすいものを選択してください。</span><span class="sxs-lookup"><span data-stu-id="75b3c-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="75b3c-191">MSBuild を利用すれば、タスクやターゲットとしてビルド プロセスを表現できますが、MSBuild プロジェクト ファイルの構文は複雑で、学習の難易度が上がります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="75b3c-192">.NET Core コマンドライン ツールはおそらく、使い方がより単純です。ただし、`bash` や PowerShell のようなスクリプト記述言語でオーケストレーション ロジックを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75b3c-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="75b3c-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="75b3c-193">See also</span></span>

[<span data-ttu-id="75b3c-194">Ubuntu 取得手順</span><span class="sxs-lookup"><span data-stu-id="75b3c-194">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)   

