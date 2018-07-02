---
title: .NET Core SDK 製品利用統計情報
description: 利用情報を収集して分析する .NET Core SDK の製品利用統計情報機能と収集されるデータについて、およびこの機能を無効にする方法を説明します。
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: f60a1eaa7b869676dfbb67529e7878ca9b9ca34a
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314878"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="7fdee-103">.NET Core SDK 製品利用統計情報</span><span class="sxs-lookup"><span data-stu-id="7fdee-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="7fdee-104">[.NET Core SDK](index.md) には、利用情報を収集する[製品利用統計情報機能](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)があります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="7fdee-105">このツールがどのように利用されているかを .NET Team が理解することが重要です。それにより、ツールを改善できます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="7fdee-106">詳細については、「[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)」 (.NET Core SDK 製品利用統計情報からわかったこと) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fdee-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="7fdee-107">収集されたデータは匿名で、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で、Microsoft とコミュニティの両者が利用するために集計された形で公開されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="7fdee-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="7fdee-108">Scope</span></span>

<span data-ttu-id="7fdee-109">`dotnet` コマンドは、アプリと .NET Core CLI の両方の起動に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="7fdee-110">`dotnet` コマンド自体は製品利用統計情報を収集しません。</span><span class="sxs-lookup"><span data-stu-id="7fdee-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="7fdee-111">`dotnet` コマンドで実行される .NET Core CLI コマンドが製品利用統計情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="7fdee-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="7fdee-112">コマンドを添付せずに `dotnet` コマンドそのものを使うと、製品利用統計情報は*有効になりません*。</span><span class="sxs-lookup"><span data-stu-id="7fdee-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="7fdee-113">次のような [.NET Core CLI コマンド](index.md)を使用すると、製品利用統計情報が*有効になります*。</span><span class="sxs-lookup"><span data-stu-id="7fdee-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="7fdee-114">オプトアウトする方法</span><span class="sxs-lookup"><span data-stu-id="7fdee-114">How to opt out</span></span>

<span data-ttu-id="7fdee-115">.NET Core SDK の製品利用統計情報機能は既定では有効になっています。</span><span class="sxs-lookup"><span data-stu-id="7fdee-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="7fdee-116">`DOTNET_CLI_TELEMETRY_OPTOUT` 環境変数を `1` または `true` に設定して、製品利用統計情報の機能をオプトアウトします。</span><span class="sxs-lookup"><span data-stu-id="7fdee-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="7fdee-117">データ ポイント</span><span class="sxs-lookup"><span data-stu-id="7fdee-117">Data points</span></span>

<span data-ttu-id="7fdee-118">この機能は次のデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="7fdee-118">The feature collects the following data:</span></span>

- <span data-ttu-id="7fdee-119">呼び出しのタイムスタンプ&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="7fdee-120">呼び出されたコマンド ("build" など)&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="7fdee-121">地理的な場所を決定するために使用する 3 つのオクテットの IP アドレス&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="7fdee-122">コマンドの `ExitCode`</span><span class="sxs-lookup"><span data-stu-id="7fdee-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="7fdee-123">(テスト プロジェクトの) テスト ランナー</span><span class="sxs-lookup"><span data-stu-id="7fdee-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="7fdee-124">オペレーティング システムとバージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="7fdee-125">ランタイム ノードにランタイム ID が存在するかどうか</span><span class="sxs-lookup"><span data-stu-id="7fdee-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="7fdee-126">.NET Core SDK バージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="7fdee-127">&#8224; このメトリックは公開されています。</span><span class="sxs-lookup"><span data-stu-id="7fdee-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="7fdee-128">.NET Core SDK 2.0 以降では、新しいデータ ポイントが収集されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="7fdee-129">`dotnet` コマンドの引数とオプション: (任意の文字列ではなく) 既知の引数とオプションのみが収集されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="7fdee-130">SDK がコンテナーで実行されているかどうか。</span><span class="sxs-lookup"><span data-stu-id="7fdee-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="7fdee-131">ターゲット フレームワーク。</span><span class="sxs-lookup"><span data-stu-id="7fdee-131">Target frameworks.</span></span>
- <span data-ttu-id="7fdee-132">ハッシュされた MAC アドレス: 暗号化の面で (SHA256) 匿名であり、マシンの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7fdee-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="7fdee-133">このメトリックは公開されていません。</span><span class="sxs-lookup"><span data-stu-id="7fdee-133">This metric isn't published.</span></span>
- <span data-ttu-id="7fdee-134">ハッシュされた現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="7fdee-134">Hashed current working directory.</span></span>

<span data-ttu-id="7fdee-135">この機能では、ユーザー名やメール アドレスなどの個人データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="7fdee-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="7fdee-136">コードはスキャンされず、名前、リポジトリ、作成者などのプロジェクト レベルの機密データは抽出されません。</span><span class="sxs-lookup"><span data-stu-id="7fdee-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="7fdee-137">データは [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) テクノロジを使用して Microsoft サーバーに安全に送信され、制限されたアクセスの下で保持され、厳格なセキュリティ コントロールの下で安全な [Azure Storage](https://azure.microsoft.com/services/storage/) システムから公開されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="7fdee-138">.NET チームは、ツールで構築しているものではなく、ツールがどのように使われ、問題なく機能しているかどうかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="7fdee-139">利用統計情報で機密情報が収集されているのではないか、データがセキュリティ上問題がある、不適切な方法で処理されているのではないかという疑いがある場合は、調査のために [dotnet/cli](https://github.com/dotnet/cli/issues) リポジトリで問題を提起してください。</span><span class="sxs-lookup"><span data-stu-id="7fdee-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="7fdee-140">公開データ</span><span class="sxs-lookup"><span data-stu-id="7fdee-140">Published data</span></span>

<span data-ttu-id="7fdee-141">公開データは四半期ごとに利用可能で、「[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)」 (.NET core SDK の使用状況データ) に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="7fdee-142">データ ファイルの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7fdee-142">The columns of a data file are:</span></span>

- <span data-ttu-id="7fdee-143">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="7fdee-143">Timestamp</span></span>
- <span data-ttu-id="7fdee-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="7fdee-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="7fdee-145">コマンド</span><span class="sxs-lookup"><span data-stu-id="7fdee-145">Command</span></span>
- <span data-ttu-id="7fdee-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="7fdee-146">Geography&#8225;</span></span>
- <span data-ttu-id="7fdee-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="7fdee-147">OSFamily</span></span>
- <span data-ttu-id="7fdee-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="7fdee-148">RuntimeID</span></span>
- <span data-ttu-id="7fdee-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="7fdee-149">OSVersion</span></span>
- <span data-ttu-id="7fdee-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="7fdee-150">SDKVersion</span></span>

<span data-ttu-id="7fdee-151">&#8224; *Occurrences* 列には、その行のメトリックに対するコマンドの使用回数の、その日の合計数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="7fdee-152">&#8225; 通常、*Geography* 列には、国の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="7fdee-153">場合によっては、調査担当者が南極や不正な場所データを使用して .NET Core を使用していることが原因で、この列に南極大陸が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="7fdee-154">例</span><span class="sxs-lookup"><span data-stu-id="7fdee-154">Example</span></span>

| <span data-ttu-id="7fdee-155">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="7fdee-155">Timestamp</span></span>      | <span data-ttu-id="7fdee-156">Occurrences</span><span class="sxs-lookup"><span data-stu-id="7fdee-156">Occurrences</span></span> | <span data-ttu-id="7fdee-157">コマンド</span><span class="sxs-lookup"><span data-stu-id="7fdee-157">Command</span></span> | <span data-ttu-id="7fdee-158">Geography</span><span class="sxs-lookup"><span data-stu-id="7fdee-158">Geography</span></span> | <span data-ttu-id="7fdee-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="7fdee-159">OSFamily</span></span> | <span data-ttu-id="7fdee-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="7fdee-160">RuntimeID</span></span>     | <span data-ttu-id="7fdee-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="7fdee-161">OSVersion</span></span> | <span data-ttu-id="7fdee-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="7fdee-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="7fdee-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="7fdee-163">4/16/2017 0:00</span></span> | <span data-ttu-id="7fdee-164">8</span><span class="sxs-lookup"><span data-stu-id="7fdee-164">8</span></span>           | <span data-ttu-id="7fdee-165">実行</span><span class="sxs-lookup"><span data-stu-id="7fdee-165">run</span></span>     | <span data-ttu-id="7fdee-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="7fdee-166">Uganda</span></span>    | <span data-ttu-id="7fdee-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="7fdee-167">Darwin</span></span>   | <span data-ttu-id="7fdee-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="7fdee-168">osx.10.12-x64</span></span> | <span data-ttu-id="7fdee-169">10.12</span><span class="sxs-lookup"><span data-stu-id="7fdee-169">10.12</span></span>     | <span data-ttu-id="7fdee-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="7fdee-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="7fdee-171">データセット</span><span class="sxs-lookup"><span data-stu-id="7fdee-171">Datasets</span></span>

[<span data-ttu-id="7fdee-172">2016 - Q3</span><span class="sxs-lookup"><span data-stu-id="7fdee-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="7fdee-173">2016 - Q4</span><span class="sxs-lookup"><span data-stu-id="7fdee-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="7fdee-174">2017 - Q1</span><span class="sxs-lookup"><span data-stu-id="7fdee-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="7fdee-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="7fdee-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="7fdee-176">2017 - Q3</span><span class="sxs-lookup"><span data-stu-id="7fdee-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="7fdee-177">2017 - Q4</span><span class="sxs-lookup"><span data-stu-id="7fdee-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="7fdee-178">追加のデータセットは、標準の URL 形式を使用してポストされます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="7fdee-179">`<YEAR>` を年で置き換え、`<QUARTER>` を四半期に置き換えます (`1`、`2`、`3`、 または `4` を使用)。</span><span class="sxs-lookup"><span data-stu-id="7fdee-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="7fdee-180">ファイルはタブ区切り値 (*TSV*) 形式です。</span><span class="sxs-lookup"><span data-stu-id="7fdee-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="7fdee-181">ライセンス</span><span class="sxs-lookup"><span data-stu-id="7fdee-181">License</span></span>

<span data-ttu-id="7fdee-182">Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="7fdee-183">このライセンスには、製品利用統計情報を有効にするために、次のように "DATA" セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fdee-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="7fdee-184">[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)は同じライセンスを使用しますが、製品利用統計情報を有効にしません (「[スコープ](#scope)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="7fdee-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="7fdee-185">データ。</span><span class="sxs-lookup"><span data-stu-id="7fdee-185">DATA.</span></span> <span data-ttu-id="7fdee-186">このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="7fdee-187">Microsoft は製品とサービスの向上のために情報を利用することがあります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="7fdee-188">データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-188">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="7fdee-189">ソフトウェアはこのような慣行に同意した上での利用になります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="7fdee-190">開示</span><span class="sxs-lookup"><span data-stu-id="7fdee-190">Disclosure</span></span>

<span data-ttu-id="7fdee-191">いずれかの [.NET Core CLI コマンド](index.md) (`dotnet restore` など) をはじめて実行するときに、.NET Core SDK では次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="7fdee-192">テキストは、実行している SDK のバージョンによって多少異なります。</span><span class="sxs-lookup"><span data-stu-id="7fdee-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="7fdee-193">この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdee-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. 
The data is anonymous and doesn't include command-line arguments. 
The data is collected by Microsoft and shared with the community. 
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="7fdee-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fdee-194">See also</span></span>

[<span data-ttu-id="7fdee-195">.NET Core SDK 製品利用統計情報からわかったこと</span><span class="sxs-lookup"><span data-stu-id="7fdee-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[<span data-ttu-id="7fdee-196">製品利用統計情報の参照のソース (dotnet/cli リポジトリ)</span><span class="sxs-lookup"><span data-stu-id="7fdee-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)  
[<span data-ttu-id="7fdee-197">.NET core SDK の使用状況データ</span><span class="sxs-lookup"><span data-stu-id="7fdee-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)  
