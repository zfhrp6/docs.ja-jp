---
title: .NET Core CLI ツールの製品利用統計情報
description: 利用情報を収集して分析する .NET Core ツールの製品利用統計情報機能と収集されるデータについて、およびこの機能を無効にする方法を説明します。
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.openlocfilehash: 4c04867f5db512ef53c23ec41ea66db570a82021
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="9aa33-103">.NET Core CLI ツールの製品利用統計情報</span><span class="sxs-lookup"><span data-stu-id="9aa33-103">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="9aa33-104">[.NET Core SDK](index.md) には、利用情報を収集する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="9aa33-105">.NET Team がこのツールがどのように利用されているかを理解することが重要です。それにより、ツールが改善されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-105">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="9aa33-106">詳細については、「[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)」 (.NET Core SDK 製品利用統計情報からわかったこと) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aa33-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="9aa33-107">収集されたデータは匿名で、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で、Microsoft とコミュニティの両者が利用するために集計された形で公開されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="9aa33-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="9aa33-108">Scope</span></span>

<span data-ttu-id="9aa33-109">`dotnet` コマンドは、アプリと .NET Core CLI の両方の起動に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="9aa33-110">`dotnet` コマンド自体は製品利用統計情報を収集しません。</span><span class="sxs-lookup"><span data-stu-id="9aa33-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="9aa33-111">`dotnet` コマンドで実行される .NET Core CLI コマンドが製品利用統計情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="9aa33-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="9aa33-112">コマンドを添付せずに `dotnet` コマンドそのものを使うと、製品利用統計情報は*有効になりません*。</span><span class="sxs-lookup"><span data-stu-id="9aa33-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="9aa33-113">次のような [.NET Core CLI コマンド](index.md)を使用すると、製品利用統計情報が*有効になります*。</span><span class="sxs-lookup"><span data-stu-id="9aa33-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="9aa33-114">動作</span><span class="sxs-lookup"><span data-stu-id="9aa33-114">Behavior</span></span>

<span data-ttu-id="9aa33-115">.NET Core CLI ツールの製品利用統計情報機能は既定では有効になっています。</span><span class="sxs-lookup"><span data-stu-id="9aa33-115">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="9aa33-116">`DOTNET_CLI_TELEMETRY_OPTOUT` 環境変数を `1` または `true` に設定して、製品利用統計情報の機能をオプトアウトします。</span><span class="sxs-lookup"><span data-stu-id="9aa33-116">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="9aa33-117">データ ポイント</span><span class="sxs-lookup"><span data-stu-id="9aa33-117">Data points</span></span>

<span data-ttu-id="9aa33-118">この機能は次のデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="9aa33-118">The feature collects the following data:</span></span>

- <span data-ttu-id="9aa33-119">呼び出しのタイムスタンプ&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="9aa33-120">呼び出されたコマンド ("build" など)&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="9aa33-121">地理的な場所を決定するために使用する 3 つのオクテットの IP アドレス&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="9aa33-122">コマンドの `ExitCode`</span><span class="sxs-lookup"><span data-stu-id="9aa33-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="9aa33-123">(テスト プロジェクトの) テスト ランナー</span><span class="sxs-lookup"><span data-stu-id="9aa33-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="9aa33-124">オペレーティング システムとバージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="9aa33-125">ランタイム ノードにランタイム ID が存在するかどうか</span><span class="sxs-lookup"><span data-stu-id="9aa33-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="9aa33-126">.NET Core SDK バージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="9aa33-127">&#8224; このメトリックは公開されています。</span><span class="sxs-lookup"><span data-stu-id="9aa33-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="9aa33-128">.NET Core SDK 2.0 以降では、新しいデータ ポイントが収集されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="9aa33-129">`dotnet` コマンドの引数とオプション: (任意の文字列ではなく) 既知の引数とオプションのみが収集されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="9aa33-130">SDK がコンテナーで実行されているかどうか。</span><span class="sxs-lookup"><span data-stu-id="9aa33-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="9aa33-131">ターゲット フレームワーク。</span><span class="sxs-lookup"><span data-stu-id="9aa33-131">Target frameworks.</span></span>
- <span data-ttu-id="9aa33-132">ハッシュされた MAC アドレス: 暗号化の面で (SHA256) 匿名であり、マシンの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="9aa33-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="9aa33-133">このメトリックは公開されていません。</span><span class="sxs-lookup"><span data-stu-id="9aa33-133">This metric is not published.</span></span>
- <span data-ttu-id="9aa33-134">ハッシュされた現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="9aa33-134">Hashed current working directory.</span></span>

<span data-ttu-id="9aa33-135">この機能では、ユーザー名やメール アドレスなどの個人データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="9aa33-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="9aa33-136">コードはスキャンされず、名前、リポジトリ、作成者などのプロジェクト レベルの機密データは抽出されません。</span><span class="sxs-lookup"><span data-stu-id="9aa33-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="9aa33-137">データは [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) テクノロジを使用して Microsoft サーバーに安全に送信され、制限されたアクセスの下で保持され、厳格なセキュリティ コントロールの下で安全な [Azure Storage](https://azure.microsoft.com/services/storage/) システムから公開されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="9aa33-138">ツールで構築しているものではなく、ツールがどのように使われ、問題なく機能しているかどうかを知るためのものです。</span><span class="sxs-lookup"><span data-stu-id="9aa33-138">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="9aa33-139">利用統計情報で機密情報が収集されているのではないか、またはデータがセキュリティ上問題がある方法でまたは不適切に処理されているのではないかという疑いがある場合は、調査のために [dotnet/cli リポジトリの問題で問題を提起](https://github.com/dotnet/cli/issues)してください。</span><span class="sxs-lookup"><span data-stu-id="9aa33-139">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="9aa33-140">公開データ</span><span class="sxs-lookup"><span data-stu-id="9aa33-140">Published data</span></span>

<span data-ttu-id="9aa33-141">公開データは四半期ごとに利用可能で、「[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)」 (.NET core SDK の使用状況データ) に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="9aa33-142">データ ファイルの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9aa33-142">The columns of a data file are:</span></span>
- <span data-ttu-id="9aa33-143">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="9aa33-143">Timestamp</span></span>
- <span data-ttu-id="9aa33-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="9aa33-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="9aa33-145">コマンド</span><span class="sxs-lookup"><span data-stu-id="9aa33-145">Command</span></span>
- <span data-ttu-id="9aa33-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="9aa33-146">Geography&#8225;</span></span>
- <span data-ttu-id="9aa33-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="9aa33-147">OSFamily</span></span>
- <span data-ttu-id="9aa33-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="9aa33-148">RuntimeID</span></span>
- <span data-ttu-id="9aa33-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="9aa33-149">OSVersion</span></span>
- <span data-ttu-id="9aa33-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="9aa33-150">SDKVersion</span></span>

<span data-ttu-id="9aa33-151">&#8224; *Occurrences* 列には、その行のメトリックに対するコマンドの使用回数の、その日の合計数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="9aa33-152">&#8225; 通常、*Geography* 列には、国の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="9aa33-153">場合によっては、調査担当者が南極や不正な場所データを使用して .NET Core を使用していることが原因で、この列に南極大陸が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="9aa33-154">例</span><span class="sxs-lookup"><span data-stu-id="9aa33-154">Example</span></span>

| <span data-ttu-id="9aa33-155">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="9aa33-155">Timestamp</span></span>      | <span data-ttu-id="9aa33-156">Occurrences</span><span class="sxs-lookup"><span data-stu-id="9aa33-156">Occurrences</span></span> | <span data-ttu-id="9aa33-157">コマンド</span><span class="sxs-lookup"><span data-stu-id="9aa33-157">Command</span></span> | <span data-ttu-id="9aa33-158">Geography</span><span class="sxs-lookup"><span data-stu-id="9aa33-158">Geography</span></span> | <span data-ttu-id="9aa33-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="9aa33-159">OSFamily</span></span> | <span data-ttu-id="9aa33-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="9aa33-160">RuntimeID</span></span>     | <span data-ttu-id="9aa33-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="9aa33-161">OSVersion</span></span> | <span data-ttu-id="9aa33-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="9aa33-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="9aa33-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="9aa33-163">4/16/2017 0:00</span></span> | <span data-ttu-id="9aa33-164">8</span><span class="sxs-lookup"><span data-stu-id="9aa33-164">8</span></span>           | <span data-ttu-id="9aa33-165">実行</span><span class="sxs-lookup"><span data-stu-id="9aa33-165">run</span></span>     | <span data-ttu-id="9aa33-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="9aa33-166">Uganda</span></span>    | <span data-ttu-id="9aa33-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="9aa33-167">Darwin</span></span>   | <span data-ttu-id="9aa33-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="9aa33-168">osx.10.12-x64</span></span> | <span data-ttu-id="9aa33-169">10.12</span><span class="sxs-lookup"><span data-stu-id="9aa33-169">10.12</span></span>     | <span data-ttu-id="9aa33-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="9aa33-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="9aa33-171">データセット</span><span class="sxs-lookup"><span data-stu-id="9aa33-171">Datasets</span></span>

[<span data-ttu-id="9aa33-172">2016 - Q3</span><span class="sxs-lookup"><span data-stu-id="9aa33-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="9aa33-173">2016 - Q4</span><span class="sxs-lookup"><span data-stu-id="9aa33-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="9aa33-174">2017 - Q1</span><span class="sxs-lookup"><span data-stu-id="9aa33-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="9aa33-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="9aa33-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="9aa33-176">追加のデータセットは、標準の URL 形式を使用してポストされます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-176">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="9aa33-177">`<YEAR>` を年で置き換え、`<QUARTER>` を四半期に置き換えます (`1`、`2`、`3`、 または `4` を使用)。</span><span class="sxs-lookup"><span data-stu-id="9aa33-177">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="9aa33-178">ファイルはタブ区切り値 (*TSV*) 形式です。</span><span class="sxs-lookup"><span data-stu-id="9aa33-178">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="9aa33-179">ライセンス</span><span class="sxs-lookup"><span data-stu-id="9aa33-179">License</span></span>

<span data-ttu-id="9aa33-180">Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-180">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="9aa33-181">このライセンスには、製品利用統計情報を有効にするために、次のように "DATA" セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9aa33-181">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="9aa33-182">[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)は同じライセンスを使用しますが、製品利用統計情報を有効にしません (「[スコープ](#scope)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="9aa33-182">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="9aa33-183">データ。</span><span class="sxs-lookup"><span data-stu-id="9aa33-183">DATA.</span></span> <span data-ttu-id="9aa33-184">このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-184">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="9aa33-185">Microsoft は製品とサービスの向上のために情報を利用することがあります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-185">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="9aa33-186">データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-186">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="9aa33-187">ソフトウェアはこのような慣行に同意した上での利用になります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-187">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="9aa33-188">開示</span><span class="sxs-lookup"><span data-stu-id="9aa33-188">Disclosure</span></span>

<span data-ttu-id="9aa33-189">いずれかのコマンド (`dotnet restore` など) をはじめて実行するときに、.NET Core CLI ツールでは次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-189">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="9aa33-190">テキストは、実行している SDK のバージョンによって多少異なります。</span><span class="sxs-lookup"><span data-stu-id="9aa33-190">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="9aa33-191">この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="9aa33-191">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="9aa33-192">関連項目</span><span class="sxs-lookup"><span data-stu-id="9aa33-192">See also</span></span>

[<span data-ttu-id="9aa33-193">.NET Core SDK 製品利用統計情報からわかったこと</span><span class="sxs-lookup"><span data-stu-id="9aa33-193">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="9aa33-194">[製品利用統計情報の参照のソース (dotnet/cli リポジトリ、リリース/2.0.0 ブランチ)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span><span class="sxs-lookup"><span data-stu-id="9aa33-194">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span></span>  
[<span data-ttu-id="9aa33-195">.NET core SDK の使用状況データ</span><span class="sxs-lookup"><span data-stu-id="9aa33-195">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
