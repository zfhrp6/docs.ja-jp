---
title: .NET Core グローバル ツール
description: .NET Core グローバル ツールとそれらに使用できる .NET Core CLI コマンドの概要。
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697093"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="8478d-103">.NET core グローバル ツールの概要</span><span class="sxs-lookup"><span data-stu-id="8478d-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="8478d-104">.NET Core グローバル ツールは、コンソール アプリケーションを含む特殊な NuGet パッケージです。</span><span class="sxs-lookup"><span data-stu-id="8478d-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="8478d-105">グローバル ツールは、PATH 環境変数に含まれている既定の場所またはカスタムの場所のマシンにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="8478d-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="8478d-106">.NET Core グローバル ツールを使用する場合は、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="8478d-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="8478d-107">ツールに関する情報を検索します (通常は Web サイトまたは GitHub ページ)。</span><span class="sxs-lookup"><span data-stu-id="8478d-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="8478d-108">フィードのホーム (通常は NuGet.org) で作成者と統計情報を確認します。</span><span class="sxs-lookup"><span data-stu-id="8478d-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="8478d-109">ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8478d-109">Install the tool.</span></span>
* <span data-ttu-id="8478d-110">ツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8478d-110">Call the tool.</span></span>
* <span data-ttu-id="8478d-111">ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="8478d-111">Update the tool.</span></span>
* <span data-ttu-id="8478d-112">ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="8478d-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8478d-113">.NET Core グローバル ツールは、パス上に表示され、完全な信頼で実行されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="8478d-114">作成者が信頼できる場合を除き、.NET Core グローバル ツールをインストールしないでください。</span><span class="sxs-lookup"><span data-stu-id="8478d-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="8478d-115">.NET Core グローバル ツールの検索</span><span class="sxs-lookup"><span data-stu-id="8478d-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="8478d-116">現時点では、.NET Core コマンド ライン インターフェイス (CLI) には、グローバル ツールの検索機能はありません。</span><span class="sxs-lookup"><span data-stu-id="8478d-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="8478d-117">.NET Core グローバル ツールは、[NuGet](https://www.nuget.org) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8478d-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="8478d-118">ただし、NuGet では、具体的に .NET Core グローバル ツールを検索することはまだできません。</span><span class="sxs-lookup"><span data-stu-id="8478d-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="8478d-119">ブログの投稿や [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub リポジトリでも、ツールの推奨事項を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="8478d-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="8478d-120">また、[aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub リポジトリでは、ASP.NET チームによって作成されたグローバル ツールのソース コードを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="8478d-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="8478d-121">作成者と統計情報の確認</span><span class="sxs-lookup"><span data-stu-id="8478d-121">Check the author and statistics</span></span>

<span data-ttu-id="8478d-122">.NET Core グローバル ツールは、完全な信頼で実行され、通常はパス上にインストールされるため、非常に強力です。</span><span class="sxs-lookup"><span data-stu-id="8478d-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="8478d-123">信頼できないユーザーからツールをダウンロードしないでください。</span><span class="sxs-lookup"><span data-stu-id="8478d-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="8478d-124">ツールが NuGet でホストされている場合は、ツールを検索することで作成者と統計情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8478d-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="8478d-125">グローバル ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="8478d-125">Install a Global Tool</span></span>

<span data-ttu-id="8478d-126">グローバル ツールをインストールするには、[dotnet tool install](dotnet-tool-install.md) .NET Core CLI コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8478d-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="8478d-127">次の例では、既定の場所にグローバル ツールをインストールする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8478d-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="8478d-128">ツールがインストールできない場合は、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="8478d-129">予定していたフィードがチェックされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8478d-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="8478d-130">ツールのプレリリース バージョンまたは特定のバージョンをインストールしようとしている場合は、次の形式を使用してバージョン番号を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8478d-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="8478d-131">インストールが成功すると、ツールの呼び出しに使用したコマンドとインストールされたバージョンを示す、次の例のようなメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="8478d-132">グローバル ツールは、既定のディレクトリ内または特定の場所にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="8478d-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="8478d-133">既定のディレクトリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8478d-133">The default directories are:</span></span>

| <span data-ttu-id="8478d-134">OS</span><span class="sxs-lookup"><span data-stu-id="8478d-134">OS</span></span>          | <span data-ttu-id="8478d-135">パス</span><span class="sxs-lookup"><span data-stu-id="8478d-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="8478d-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="8478d-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="8478d-137">Windows</span><span class="sxs-lookup"><span data-stu-id="8478d-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="8478d-138">これらの場所は、そこにインストールされたグローバル ツールを直接呼び出せるように、SDK が最初に実行されるときにユーザーのパスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="8478d-139">グローバル ツールは、マシン全体ではなく、ユーザーに固有であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8478d-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="8478d-140">ユーザーに固有であることは、そのマシンのすべてのユーザーが使用できるグローバル ツールをインストールできないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="8478d-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="8478d-141">このツールは、ツールがインストールされた各ユーザー プロファイルでしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="8478d-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="8478d-142">グローバル ツールは、特定のディレクトリにインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8478d-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="8478d-143">特定のディレクトリにインストールした場合は、ユーザーはコマンドが使用できることを確認する必要があります。それには、そのディレクトリをパスに含めるか、指定されたディレクトリでコマンドを呼び出すか、指定したディレクトリ内からツールを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8478d-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="8478d-144">この場合、.NET Core CLI によりこの場所が PATH 環境変数に自動的に追加されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8478d-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="8478d-145">ツールの使用</span><span class="sxs-lookup"><span data-stu-id="8478d-145">Use the tool</span></span>

<span data-ttu-id="8478d-146">ツールをインストールすると、そのコマンドを使用してツールを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8478d-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="8478d-147">コマンドが、パッケージ名と異なる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8478d-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="8478d-148">コマンドが `dotnetsay` の場合、次を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8478d-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="8478d-149">ツールの作成者が `dotnet` プロンプトのコンテキストにツールを表示するようにした場合は、次のように、`dotnet <command>` として呼び出す方法でツールを記述している場合があります。</span><span class="sxs-lookup"><span data-stu-id="8478d-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="8478d-150">インストールしたグローバル ツール パッケージに含まれているツールを確認するには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用してインストールされているパッケージを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8478d-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="8478d-151">ツールの使用方法については、ツールの Web サイトで検索するか、次のいずれかのコマンドを入力して検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="8478d-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="8478d-152">起こりうる問題</span><span class="sxs-lookup"><span data-stu-id="8478d-152">What could go wrong</span></span>

<span data-ttu-id="8478d-153">グローバル ツールは、[フレームワークに依存するアプリケーション](../deploying/index.md#framework-dependent-deployments-fdd)です。つまり、お使いのマシンにインストールされている .NET Core ランタイムに依存します。</span><span class="sxs-lookup"><span data-stu-id="8478d-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="8478d-154">予定していたランタイムが見つからない場合、ツールは次のような通常の .NET Core ランタイムのロール フォワード ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="8478d-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="8478d-155">アプリケーションは、指定されたメジャー バージョンおよびマイナー バージョンの最上位の修正プログラム リリースにロール フォワードされます。</span><span class="sxs-lookup"><span data-stu-id="8478d-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="8478d-156">一致するメジャー バージョン番号とマイナー バージョン番号と一致するランタイムがない場合は、次に高いマイナー バージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="8478d-157">ランタイムのプレビュー バージョン間、またはプレビュー バージョンとリリース バージョン間では、ロール フォワードは発生しません。</span><span class="sxs-lookup"><span data-stu-id="8478d-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="8478d-158">したがって、プレビュー バージョンを使用して作成されたグローバル ツールは、作成者がリビルドして再パブリッシュしてから再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8478d-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="8478d-159">.NET Core 2.1 Preview 1 で作成されたグローバル ツールでは、その他の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8478d-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="8478d-160">詳細については、「[.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md)」 (.NET Core 2.1 Preview 2 の既知の問題) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8478d-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="8478d-161">アプリケーションで適切なランタイムが見つからない場合は、実行が失敗し、エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="8478d-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="8478d-162">発生する可能性がある別の問題は、以前のプレビュー時に作成されたグローバル ツールが、現在インストールされている .NET Core ランタイムで実行できない場合があることです。</span><span class="sxs-lookup"><span data-stu-id="8478d-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="8478d-163">次のコマンドを使用して、お使いのマシンにインストールされているランタイムを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="8478d-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="8478d-164">グローバル ツールの作成者に連絡して、ツール パッケージを再コンパイルして、NuGet に更新されたバージョン番号で再パブリッシュできるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8478d-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="8478d-165">作成者が NuGet でパッケージを更新したら、自分のコピーを更新できます。</span><span class="sxs-lookup"><span data-stu-id="8478d-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="8478d-166">.NET Core CLI は、初めて使用したときに既定の場所を PATH 環境変数に追加しようとします。</span><span class="sxs-lookup"><span data-stu-id="8478d-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="8478d-167">ただし、次のようなシナリオでは、既定の場所が PATH に追加されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8478d-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="8478d-168">`DOTNET_SKIP_FIRST_TIME_EXPERIENCE` 環境変数を設定している場合</span><span class="sxs-lookup"><span data-stu-id="8478d-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="8478d-169">macOS で、*.pkg* ではなく *.tar.gz* ファイルを使用して .NET Core SDK をインストールしている場合</span><span class="sxs-lookup"><span data-stu-id="8478d-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="8478d-170">Linux で、パスを構成するためにシェル環境ファイルを編集する必要がある場合</span><span class="sxs-lookup"><span data-stu-id="8478d-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="8478d-171">その他の CLI コマンド</span><span class="sxs-lookup"><span data-stu-id="8478d-171">Other CLI commands</span></span>

<span data-ttu-id="8478d-172">.NET Core SDK には、.NET Core グローバル ツールをサポートするその他のコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8478d-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="8478d-173">次のいずれかのオプションを使用して、任意の `dotnet tool` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8478d-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="8478d-174">`--global` または `-g` は、コマンドがユーザー全体のグローバル ツールに適用可能なことを指定します。</span><span class="sxs-lookup"><span data-stu-id="8478d-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="8478d-175">`--tool-path` は、グローバル ツールのカスタムの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8478d-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="8478d-176">グローバル ツールで使用できるコマンドを調べるには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8478d-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="8478d-177">グローバル ツールを更新するには、ツールをアンインストールしてから、最新の安定バージョンで再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8478d-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="8478d-178">グローバル ツールを更新するには、[dotnet tool update](dotnet-tool-update.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8478d-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="8478d-179">[dotnet tool uninstall](dotnet-tool-uninstall.md) を使用してグローバル ツールを削除します。</span><span class="sxs-lookup"><span data-stu-id="8478d-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="8478d-180">マシンに現在インストールされているすべてのグローバル ツールと、それらのバージョンとコマンドを表示するには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8478d-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```