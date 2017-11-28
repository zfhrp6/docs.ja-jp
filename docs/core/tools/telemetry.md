---
title: ".NET Core CLI ツールの製品利用統計情報"
description: "利用情報を収集して分析する .NET Core ツールの製品利用統計情報機能と収集されるデータについて、およびこの機能を無効にする方法を説明します。"
keywords: ".NET、.NET Core、製品利用統計情報"
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.openlocfilehash: 34183792a235391f66fbec211ff00f06f85134fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="168aa-104">.NET Core CLI ツールの製品利用統計情報</span><span class="sxs-lookup"><span data-stu-id="168aa-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="168aa-105">[.NET Core SDK](index.md) には、利用情報を収集する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。</span><span class="sxs-lookup"><span data-stu-id="168aa-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="168aa-106">.NET Team がこのツールがどのように利用されているかを理解することが重要です。それにより、ツールが改善されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="168aa-107">詳細については、「[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)」 (.NET Core SDK 製品利用統計情報からわかったこと) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="168aa-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="168aa-108">収集されたデータは匿名で、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で、Microsoft とコミュニティの両者が利用するために集計された形で公開されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="168aa-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="168aa-109">Scope</span></span>

<span data-ttu-id="168aa-110">`dotnet` コマンドは、アプリと .NET Core CLI の両方の起動に使用されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="168aa-111">`dotnet` コマンド自体は製品利用統計情報を収集しません。</span><span class="sxs-lookup"><span data-stu-id="168aa-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="168aa-112">`dotnet` コマンドで実行される .NET Core CLI コマンドが製品利用統計情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="168aa-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="168aa-113">コマンドを添付せずに `dotnet` コマンドそのものを使うと、製品利用統計情報は*有効になりません*。</span><span class="sxs-lookup"><span data-stu-id="168aa-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="168aa-114">次のような [.NET Core CLI コマンド](index.md)を使用すると、製品利用統計情報が*有効になります*。</span><span class="sxs-lookup"><span data-stu-id="168aa-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="168aa-115">動作</span><span class="sxs-lookup"><span data-stu-id="168aa-115">Behavior</span></span>

<span data-ttu-id="168aa-116">.NET Core CLI ツールの製品利用統計情報機能は既定では有効になっています。</span><span class="sxs-lookup"><span data-stu-id="168aa-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="168aa-117">`DOTNET_CLI_TELEMETRY_OPTOUT` 環境変数を `1` または `true` に設定して、製品利用統計情報の機能をオプトアウトします。</span><span class="sxs-lookup"><span data-stu-id="168aa-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="168aa-118">データ ポイント</span><span class="sxs-lookup"><span data-stu-id="168aa-118">Data points</span></span>

<span data-ttu-id="168aa-119">この機能は次のデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="168aa-119">The feature collects the following data:</span></span>

- <span data-ttu-id="168aa-120">呼び出しのタイムスタンプ&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="168aa-121">呼び出されたコマンド ("build" など)&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="168aa-122">地理的な場所を決定するために使用する 3 つのオクテットの IP アドレス&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="168aa-123">コマンドの `ExitCode`</span><span class="sxs-lookup"><span data-stu-id="168aa-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="168aa-124">(テスト プロジェクトの) テスト ランナー</span><span class="sxs-lookup"><span data-stu-id="168aa-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="168aa-125">オペレーティング システムとバージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="168aa-126">ランタイム ノードにランタイム ID が存在するかどうか</span><span class="sxs-lookup"><span data-stu-id="168aa-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="168aa-127">.NET Core SDK バージョン&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="168aa-128">&#8224; このメトリックは公開されています。</span><span class="sxs-lookup"><span data-stu-id="168aa-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="168aa-129">.NET Core SDK 2.0 以降では、新しいデータ ポイントが収集されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="168aa-130">`dotnet` コマンドの引数とオプション: (任意の文字列ではなく) 既知の引数とオプションのみが収集されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="168aa-131">SDK がコンテナーで実行されているかどうか。</span><span class="sxs-lookup"><span data-stu-id="168aa-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="168aa-132">ターゲット フレームワーク。</span><span class="sxs-lookup"><span data-stu-id="168aa-132">Target frameworks.</span></span>
- <span data-ttu-id="168aa-133">ハッシュされた MAC アドレス: 暗号化の面で (SHA256) 匿名であり、マシンの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="168aa-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="168aa-134">このメトリックは公開されていません。</span><span class="sxs-lookup"><span data-stu-id="168aa-134">This metric is not published.</span></span>
- <span data-ttu-id="168aa-135">ハッシュされた現在の作業ディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="168aa-135">Hashed current working directory.</span></span>

<span data-ttu-id="168aa-136">この機能では、ユーザー名やメール アドレスなどの個人データは収集されません。</span><span class="sxs-lookup"><span data-stu-id="168aa-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="168aa-137">コードはスキャンされず、名前、リポジトリ、作成者などのプロジェクト レベルの機密データは抽出されません。</span><span class="sxs-lookup"><span data-stu-id="168aa-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="168aa-138">データは [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) テクノロジを使用して Microsoft サーバーに安全に送信され、制限されたアクセスの下で保持され、厳格なセキュリティ コントロールの下で安全な [Azure Storage](https://azure.microsoft.com/services/storage/) システムから公開されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="168aa-139">ツールで構築しているものではなく、ツールがどのように使われ、問題なく機能しているかどうかを知るためのものです。</span><span class="sxs-lookup"><span data-stu-id="168aa-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="168aa-140">利用統計情報で機密情報が収集されているのではないか、またはデータがセキュリティ上問題がある方法でまたは不適切に処理されているのではないかという疑いがある場合は、調査のために [dotnet/cli リポジトリの問題で問題を提起](https://github.com/dotnet/cli/issues)してください。</span><span class="sxs-lookup"><span data-stu-id="168aa-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="168aa-141">公開データ</span><span class="sxs-lookup"><span data-stu-id="168aa-141">Published data</span></span>

<span data-ttu-id="168aa-142">公開データは四半期ごとに利用可能で、「[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)」 (.NET core SDK の使用状況データ) に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="168aa-143">データ ファイルの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="168aa-143">The columns of a data file are:</span></span>
- <span data-ttu-id="168aa-144">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="168aa-144">Timestamp</span></span>
- <span data-ttu-id="168aa-145">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="168aa-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="168aa-146">コマンド</span><span class="sxs-lookup"><span data-stu-id="168aa-146">Command</span></span>
- <span data-ttu-id="168aa-147">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="168aa-147">Geography&#8225;</span></span>
- <span data-ttu-id="168aa-148">OSFamily</span><span class="sxs-lookup"><span data-stu-id="168aa-148">OSFamily</span></span>
- <span data-ttu-id="168aa-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="168aa-149">RuntimeID</span></span>
- <span data-ttu-id="168aa-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="168aa-150">OSVersion</span></span>
- <span data-ttu-id="168aa-151">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="168aa-151">SDKVersion</span></span>

<span data-ttu-id="168aa-152">&#8224; *Occurrences* 列には、その行のメトリックに対するコマンドの使用回数の、その日の合計数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="168aa-153">&#8225; 通常、*Geography* 列には、国の名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="168aa-154">場合によっては、調査担当者が南極や不正な場所データを使用して .NET Core を使用していることが原因で、この列に南極大陸が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="168aa-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="168aa-155">例</span><span class="sxs-lookup"><span data-stu-id="168aa-155">Example</span></span>

| <span data-ttu-id="168aa-156">タイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="168aa-156">Timestamp</span></span>      | <span data-ttu-id="168aa-157">Occurrences</span><span class="sxs-lookup"><span data-stu-id="168aa-157">Occurrences</span></span> | <span data-ttu-id="168aa-158">コマンド</span><span class="sxs-lookup"><span data-stu-id="168aa-158">Command</span></span> | <span data-ttu-id="168aa-159">Geography</span><span class="sxs-lookup"><span data-stu-id="168aa-159">Geography</span></span> | <span data-ttu-id="168aa-160">OSFamily</span><span class="sxs-lookup"><span data-stu-id="168aa-160">OSFamily</span></span> | <span data-ttu-id="168aa-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="168aa-161">RuntimeID</span></span>     | <span data-ttu-id="168aa-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="168aa-162">OSVersion</span></span> | <span data-ttu-id="168aa-163">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="168aa-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="168aa-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="168aa-164">4/16/2017 0:00</span></span> | <span data-ttu-id="168aa-165">8</span><span class="sxs-lookup"><span data-stu-id="168aa-165">8</span></span>           | <span data-ttu-id="168aa-166">実行</span><span class="sxs-lookup"><span data-stu-id="168aa-166">run</span></span>     | <span data-ttu-id="168aa-167">Uganda</span><span class="sxs-lookup"><span data-stu-id="168aa-167">Uganda</span></span>    | <span data-ttu-id="168aa-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="168aa-168">Darwin</span></span>   | <span data-ttu-id="168aa-169">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="168aa-169">osx.10.12-x64</span></span> | <span data-ttu-id="168aa-170">10.12</span><span class="sxs-lookup"><span data-stu-id="168aa-170">10.12</span></span>     | <span data-ttu-id="168aa-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="168aa-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="168aa-172">データセット</span><span class="sxs-lookup"><span data-stu-id="168aa-172">Datasets</span></span>

[<span data-ttu-id="168aa-173">2016 - Q3</span><span class="sxs-lookup"><span data-stu-id="168aa-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="168aa-174">2016 - Q4</span><span class="sxs-lookup"><span data-stu-id="168aa-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="168aa-175">2017 - Q1</span><span class="sxs-lookup"><span data-stu-id="168aa-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="168aa-176">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="168aa-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="168aa-177">追加のデータセットは、標準の URL 形式を使用してポストされます。</span><span class="sxs-lookup"><span data-stu-id="168aa-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="168aa-178">`<YEAR>` を年で置き換え、`<QUARTER>` を四半期に置き換えます (`1`、`2`、`3`、 または `4` を使用)。</span><span class="sxs-lookup"><span data-stu-id="168aa-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="168aa-179">ファイルはタブ区切り値 (*TSV*) 形式です。</span><span class="sxs-lookup"><span data-stu-id="168aa-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="168aa-180">ライセンス</span><span class="sxs-lookup"><span data-stu-id="168aa-180">License</span></span>

<span data-ttu-id="168aa-181">Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="168aa-182">このライセンスには、製品利用統計情報を有効にするために、次のように "DATA" セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="168aa-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="168aa-183">[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)は同じライセンスを使用しますが、製品利用統計情報を有効にしません (「[スコープ](#scope)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="168aa-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="168aa-184">データ。</span><span class="sxs-lookup"><span data-stu-id="168aa-184">DATA.</span></span> <span data-ttu-id="168aa-185">このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="168aa-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="168aa-186">Microsoft は製品とサービスの向上のために情報を利用することがあります。</span><span class="sxs-lookup"><span data-stu-id="168aa-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="168aa-187">データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。</span><span class="sxs-lookup"><span data-stu-id="168aa-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="168aa-188">ソフトウェアはこのような慣行に同意した上での利用になります。</span><span class="sxs-lookup"><span data-stu-id="168aa-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="168aa-189">開示</span><span class="sxs-lookup"><span data-stu-id="168aa-189">Disclosure</span></span>

<span data-ttu-id="168aa-190">いずれかのコマンド (`dotnet restore` など) をはじめて実行するときに、.NET Core CLI ツールでは次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="168aa-191">テキストは、実行している SDK のバージョンによって多少異なります。</span><span class="sxs-lookup"><span data-stu-id="168aa-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="168aa-192">この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="168aa-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="168aa-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="168aa-193">See also</span></span>

[<span data-ttu-id="168aa-194">.NET Core SDK 製品利用統計情報からわかったこと</span><span class="sxs-lookup"><span data-stu-id="168aa-194">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="168aa-195">[製品利用統計情報の参照のソース (dotnet/cli リポジトリ、リリース/2.0.0 ブランチ)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span><span class="sxs-lookup"><span data-stu-id="168aa-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span></span>  
[<span data-ttu-id="168aa-196">.NET core SDK の使用状況データ</span><span class="sxs-lookup"><span data-stu-id="168aa-196">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
