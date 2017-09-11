---
title: ".NET Core ツールの製品利用統計情報"
description: "利用情報を収集して分析する .NET Core ツールの製品利用統計情報機能について説明します。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1816b9fbad1f671820c9f970674c8af2147a230e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-tools-telemetry"></a><span data-ttu-id="6aeaa-104">.NET Core ツールの製品利用統計情報</span><span class="sxs-lookup"><span data-stu-id="6aeaa-104">.NET Core Tools Telemetry</span></span>

<span data-ttu-id="6aeaa-105">.NET Core ツールには、利用情報を回収する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-105">The .NET Core Tools include a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="6aeaa-106">.NET Team がこのツールの利用方法を理解しておくことが重要です。それにより、ツールが改善されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-106">It’s important that the .NET Team understands how the tools are being used so that we can improve them.</span></span>

<span data-ttu-id="6aeaa-107">回収されたデータは匿名であり、集計された上で公開され、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で Microsoft エンジニアとコミュニティ エンジニアの両者により利用されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-107">The data collected is anonymous and will be published in an aggregated form for use by both Microsoft and community engineers under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="6aeaa-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="6aeaa-108">Scope</span></span>

<span data-ttu-id="6aeaa-109">`dotnet` コマンドは、アプリと .NET Core ツールの両方の起動に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-109">The `dotnet` command is used to launch both apps and the .NET Core Tools.</span></span> <span data-ttu-id="6aeaa-110">`dotnet` コマンド自体は製品利用統計情報を回収しません。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-110">The `dotnet` command itself does not collect telemetry.</span></span> <span data-ttu-id="6aeaa-111">`dotnet` コマンドを介して実行される .NET Core ツールが製品利用統計情報を回収します。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-111">It is the .NET Core Tools that are run via the `dotnet` command that collect telemetry.</span></span>

<span data-ttu-id="6aeaa-112">.NET Core コマンド (製品利用統計情報は無効):</span><span class="sxs-lookup"><span data-stu-id="6aeaa-112">.NET Core commands (telemetry is not enabled):</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="6aeaa-113">.NET Core ツールの[コマンド](index.md) (製品利用統計情報は有効):</span><span class="sxs-lookup"><span data-stu-id="6aeaa-113">.NET Core Tools [commands](index.md) (telemetry is enabled), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="behavior"></a><span data-ttu-id="6aeaa-114">動作</span><span class="sxs-lookup"><span data-stu-id="6aeaa-114">Behavior</span></span>

<span data-ttu-id="6aeaa-115">.NET Core ツールの製品利用統計情報機能は既定では有効になっています。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-115">The .NET Core Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="6aeaa-116">製品利用統計情報機能は選択しないこともできます。その場合、環境変数 DOTNET_CLI_TELEMETRY_OPTOUT (たとえば、macOS/Linux の場合は `export`、Windows の場合は `set`) を true ("true" や 1 など) に設定します。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-116">You can opt-out of the telemetry feature by setting an environment variable DOTNET_CLI_TELEMETRY_OPTOUT (for example, `export` on macOS/Linux, `set` on Windows) to true (for example, "true", 1).</span></span>

## <a name="data-points"></a><span data-ttu-id="6aeaa-117">データ ポイント</span><span class="sxs-lookup"><span data-stu-id="6aeaa-117">Data Points</span></span>

<span data-ttu-id="6aeaa-118">この機能は次のデータを回収します。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-118">The feature collects the following pieces of data:</span></span>

- <span data-ttu-id="6aeaa-119">使用されているコマンド ("build" や "restore" など)</span><span class="sxs-lookup"><span data-stu-id="6aeaa-119">The command being used (for example, "build", "restore")</span></span>
- <span data-ttu-id="6aeaa-120">コマンドの ExitCode</span><span class="sxs-lookup"><span data-stu-id="6aeaa-120">The ExitCode of the command</span></span>
- <span data-ttu-id="6aeaa-121">テスト プロジェクトの場合、使用されているテスト ランナー</span><span class="sxs-lookup"><span data-stu-id="6aeaa-121">For test projects, the test runner being used</span></span>
- <span data-ttu-id="6aeaa-122">呼び出しのタイムスタンプ</span><span class="sxs-lookup"><span data-stu-id="6aeaa-122">The timestamp of invocation</span></span>
- <span data-ttu-id="6aeaa-123">使用されているフレームワーク</span><span class="sxs-lookup"><span data-stu-id="6aeaa-123">The framework used</span></span>
- <span data-ttu-id="6aeaa-124">"ランタイム" ノードにランタイム ID が存在するかどうか</span><span class="sxs-lookup"><span data-stu-id="6aeaa-124">Whether runtime IDs are present in the "runtimes" node</span></span>
- <span data-ttu-id="6aeaa-125">使用されている CLI バージョン</span><span class="sxs-lookup"><span data-stu-id="6aeaa-125">The CLI version being used</span></span>

<span data-ttu-id="6aeaa-126">この機能では、ユーザー名や電子メールなど、個人データは回収されません。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-126">The feature will not collect any personal data, such as usernames or emails.</span></span> <span data-ttu-id="6aeaa-127">コードをスキャンすることはありません。(project.json に設定している場合) 名前、リポジトリ、作成者など、機密と見なされるプロジェクト レベルのデータを抽出することはありません。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-127">It will not scan your code and not extract any project-level data that can be considered sensitive, such as name, repo or author (if you set those in your project.json).</span></span> <span data-ttu-id="6aeaa-128">ツールで構築しているものではなく、ツールの使われ方を知るためのものです。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-128">We want to know how the tools are used, not what you are building with the tools.</span></span> <span data-ttu-id="6aeaa-129">機密データが回収された場合、それはバグです。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-129">If you find sensitive data being collected, that’s a bug.</span></span> <span data-ttu-id="6aeaa-130">[問題を提出する](https://github.com/dotnet/cli/issues)と、解決されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-130">Please [file an issue](https://github.com/dotnet/cli/issues) and it will be fixed.</span></span>

## <a name="license"></a><span data-ttu-id="6aeaa-131">ライセンス</span><span class="sxs-lookup"><span data-stu-id="6aeaa-131">License</span></span>

<span data-ttu-id="6aeaa-132">Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-132">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="6aeaa-133">製品利用統計情報を有効にするために、下のように "DATA" セクションが再プリントされます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-133">This includes the "DATA" section re-printed below, to enable telemetry.</span></span>

<span data-ttu-id="6aeaa-134">[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)はこの同じライセンスを使用しますが、製品利用統計情報を有効にしません (上の「[範囲](#scope)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-134">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use this same license but do not enable telemetry (see [Scope](#scope) above).</span></span>

> 2. <span data-ttu-id="6aeaa-135">データ。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-135">DATA.</span></span> <span data-ttu-id="6aeaa-136">このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-136">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="6aeaa-137">Microsoft は製品とサービスの向上のために情報を利用することがあります。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-137">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="6aeaa-138">データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-138">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="6aeaa-139">ソフトウェアはこのような慣行に同意した上での利用になります。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-139">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="6aeaa-140">開示</span><span class="sxs-lookup"><span data-stu-id="6aeaa-140">Disclosure</span></span>

<span data-ttu-id="6aeaa-141">いずれかのコマンド (`dotnet restore` など) を始めて実行すると、.NET Core ツールでは次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-141">The .NET Core Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="6aeaa-142">この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-142">This "first run" experience is how Microsoft notifies you about data collection.</span></span> <span data-ttu-id="6aeaa-143">また、このとき、NET Core SDK のライブラリが NuGet キャッシュに入力されます。それらのライブラリに関する NuGet.org への要求 (あるいはその他の NuGet フィード) が回避されます。</span><span class="sxs-lookup"><span data-stu-id="6aeaa-143">This same experience also initially populates your NuGet cache with the libraries in the .NET Core SDK, avoiding requests to NuGet.org (or other NuGet feed) for these libraries.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

