---
title: "dotnet new コマンド - .NET Core CLI"
description: "dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: f5815e1ad2a36a8ef3279f6ff83465dba9ec5d50
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="8cfa3-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8cfa3-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="8cfa3-105">name</span><span class="sxs-lookup"><span data-stu-id="8cfa3-105">Name</span></span>

<span data-ttu-id="8cfa3-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8cfa3-107">構文</span><span class="sxs-lookup"><span data-stu-id="8cfa3-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8cfa3-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8cfa3-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="8cfa3-110">説明</span><span class="sxs-lookup"><span data-stu-id="8cfa3-110">Description</span></span>

<span data-ttu-id="8cfa3-111">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="8cfa3-112">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="8cfa3-113">引数</span><span class="sxs-lookup"><span data-stu-id="8cfa3-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="8cfa3-114">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8cfa3-115">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8cfa3-116">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8cfa3-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="8cfa3-118">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-118">The command contains a default list of templates.</span></span> <span data-ttu-id="8cfa3-119">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="8cfa3-120">次の表は、.NET Core 2.0 SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="8cfa3-121">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8cfa3-122">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="8cfa3-122">Template description</span></span>                          | <span data-ttu-id="8cfa3-123">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="8cfa3-123">Template name</span></span>  | <span data-ttu-id="8cfa3-124">言語</span><span class="sxs-lookup"><span data-stu-id="8cfa3-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="8cfa3-125">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8cfa3-125">Console application</span></span>                          | <span data-ttu-id="8cfa3-126">コンソール</span><span class="sxs-lookup"><span data-stu-id="8cfa3-126">console</span></span>        | <span data-ttu-id="8cfa3-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8cfa3-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8cfa3-128">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-128">Class library</span></span>                                | <span data-ttu-id="8cfa3-129">classlib</span><span class="sxs-lookup"><span data-stu-id="8cfa3-129">classlib</span></span>       | <span data-ttu-id="8cfa3-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8cfa3-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8cfa3-131">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8cfa3-131">Unit test project</span></span>                            | <span data-ttu-id="8cfa3-132">mstest</span><span class="sxs-lookup"><span data-stu-id="8cfa3-132">mstest</span></span>         | <span data-ttu-id="8cfa3-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8cfa3-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8cfa3-134">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8cfa3-134">xUnit test project</span></span>                           | <span data-ttu-id="8cfa3-135">xunit</span><span class="sxs-lookup"><span data-stu-id="8cfa3-135">xunit</span></span>          | <span data-ttu-id="8cfa3-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="8cfa3-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="8cfa3-137">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="8cfa3-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="8cfa3-138">Web</span><span class="sxs-lookup"><span data-stu-id="8cfa3-138">web</span></span>            | <span data-ttu-id="8cfa3-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-139">[C#], F#</span></span>      |
| <span data-ttu-id="8cfa3-140">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="8cfa3-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="8cfa3-141">mvc</span><span class="sxs-lookup"><span data-stu-id="8cfa3-141">mvc</span></span>            | <span data-ttu-id="8cfa3-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-142">[C#], F#</span></span>      |
| <span data-ttu-id="8cfa3-143">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="8cfa3-144">razor</span><span class="sxs-lookup"><span data-stu-id="8cfa3-144">razor</span></span>          | <span data-ttu-id="8cfa3-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-145">[C#]</span></span>          |
| <span data-ttu-id="8cfa3-146">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa3-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="8cfa3-147">angular</span><span class="sxs-lookup"><span data-stu-id="8cfa3-147">angular</span></span>        | <span data-ttu-id="8cfa3-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-148">[C#]</span></span>          |
| <span data-ttu-id="8cfa3-149">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa3-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="8cfa3-150">react</span><span class="sxs-lookup"><span data-stu-id="8cfa3-150">react</span></span>          | <span data-ttu-id="8cfa3-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-151">[C#]</span></span>          |
| <span data-ttu-id="8cfa3-152">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8cfa3-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="8cfa3-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="8cfa3-153">reactredux</span></span>     | <span data-ttu-id="8cfa3-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-154">[C#]</span></span>          |
| <span data-ttu-id="8cfa3-155">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8cfa3-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="8cfa3-156">webapi</span><span class="sxs-lookup"><span data-stu-id="8cfa3-156">webapi</span></span>         | <span data-ttu-id="8cfa3-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-157">[C#], F#</span></span>      |
| <span data-ttu-id="8cfa3-158">global.json file</span><span class="sxs-lookup"><span data-stu-id="8cfa3-158">global.json file</span></span>                             | <span data-ttu-id="8cfa3-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="8cfa3-159">globaljson</span></span>     |               |
| <span data-ttu-id="8cfa3-160">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="8cfa3-160">Nuget config</span></span>                                 | <span data-ttu-id="8cfa3-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="8cfa3-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="8cfa3-162">Web 構成</span><span class="sxs-lookup"><span data-stu-id="8cfa3-162">Web config</span></span>                                   | <span data-ttu-id="8cfa3-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="8cfa3-163">webconfig</span></span>      |               |
| <span data-ttu-id="8cfa3-164">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="8cfa3-164">Solution file</span></span>                                | <span data-ttu-id="8cfa3-165">sln</span><span class="sxs-lookup"><span data-stu-id="8cfa3-165">sln</span></span>            |               |
| <span data-ttu-id="8cfa3-166">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-166">Razor page</span></span>                                   | <span data-ttu-id="8cfa3-167">ページ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-167">page</span></span>           |               |
| <span data-ttu-id="8cfa3-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="8cfa3-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="8cfa3-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="8cfa3-169">viewimports</span></span>    |               |
| <span data-ttu-id="8cfa3-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="8cfa3-170">MVC ViewStart</span></span>                                | <span data-ttu-id="8cfa3-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="8cfa3-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8cfa3-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8cfa3-173">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-173">The command contains a default list of templates.</span></span> <span data-ttu-id="8cfa3-174">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="8cfa3-175">次の表は、.NET Core 1.x SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="8cfa3-176">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8cfa3-177">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="8cfa3-177">Template description</span></span>  | <span data-ttu-id="8cfa3-178">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="8cfa3-178">Template name</span></span>  | <span data-ttu-id="8cfa3-179">言語</span><span class="sxs-lookup"><span data-stu-id="8cfa3-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="8cfa3-180">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8cfa3-180">Console application</span></span>  | <span data-ttu-id="8cfa3-181">コンソール</span><span class="sxs-lookup"><span data-stu-id="8cfa3-181">console</span></span>        | <span data-ttu-id="8cfa3-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-182">[C#], F#</span></span>  |
| <span data-ttu-id="8cfa3-183">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-183">Class library</span></span>        | <span data-ttu-id="8cfa3-184">classlib</span><span class="sxs-lookup"><span data-stu-id="8cfa3-184">classlib</span></span>       | <span data-ttu-id="8cfa3-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-185">[C#], F#</span></span>  |
| <span data-ttu-id="8cfa3-186">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8cfa3-186">Unit test project</span></span>    | <span data-ttu-id="8cfa3-187">mstest</span><span class="sxs-lookup"><span data-stu-id="8cfa3-187">mstest</span></span>         | <span data-ttu-id="8cfa3-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-188">[C#], F#</span></span>  |
| <span data-ttu-id="8cfa3-189">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8cfa3-189">xUnit test project</span></span>   | <span data-ttu-id="8cfa3-190">xunit</span><span class="sxs-lookup"><span data-stu-id="8cfa3-190">xunit</span></span>          | <span data-ttu-id="8cfa3-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-191">[C#], F#</span></span>  |
| <span data-ttu-id="8cfa3-192">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="8cfa3-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="8cfa3-193">Web</span><span class="sxs-lookup"><span data-stu-id="8cfa3-193">web</span></span>            | <span data-ttu-id="8cfa3-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-194">[C#]</span></span>      |
| <span data-ttu-id="8cfa3-195">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="8cfa3-196">mvc</span><span class="sxs-lookup"><span data-stu-id="8cfa3-196">mvc</span></span>            | <span data-ttu-id="8cfa3-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8cfa3-197">[C#], F#</span></span>  |
| <span data-ttu-id="8cfa3-198">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8cfa3-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="8cfa3-199">webapi</span><span class="sxs-lookup"><span data-stu-id="8cfa3-199">webapi</span></span>         | <span data-ttu-id="8cfa3-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="8cfa3-200">[C#]</span></span>      |
| <span data-ttu-id="8cfa3-201">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="8cfa3-201">Nuget config</span></span>         | <span data-ttu-id="8cfa3-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="8cfa3-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="8cfa3-203">Web 構成</span><span class="sxs-lookup"><span data-stu-id="8cfa3-203">Web config</span></span>           | <span data-ttu-id="8cfa3-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="8cfa3-204">webconfig</span></span>      |           |
| <span data-ttu-id="8cfa3-205">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="8cfa3-205">Solution file</span></span>        | <span data-ttu-id="8cfa3-206">sln</span><span class="sxs-lookup"><span data-stu-id="8cfa3-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="8cfa3-207">オプション</span><span class="sxs-lookup"><span data-stu-id="8cfa3-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8cfa3-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="8cfa3-209">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="8cfa3-210">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8cfa3-211">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-211">Prints out help for the command.</span></span> <span data-ttu-id="8cfa3-212">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="8cfa3-213">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="8cfa3-214">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="8cfa3-215">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="8cfa3-216">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8cfa3-217">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="8cfa3-218">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-218">The language of the template to create.</span></span> <span data-ttu-id="8cfa3-219">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8cfa3-220">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8cfa3-221">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-221">The name for the created output.</span></span> <span data-ttu-id="8cfa3-222">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8cfa3-223">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-223">Location to place the generated output.</span></span> <span data-ttu-id="8cfa3-224">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="8cfa3-225">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-225">Filters templates based on available types.</span></span> <span data-ttu-id="8cfa3-226">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="8cfa3-227">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="8cfa3-228">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="8cfa3-229">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="8cfa3-230">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8cfa3-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="8cfa3-232">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="8cfa3-233">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="8cfa3-234">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="8cfa3-235">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-235">Prints out help for the command.</span></span> <span data-ttu-id="8cfa3-236">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="8cfa3-237">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="8cfa3-238">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8cfa3-239">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="8cfa3-240">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-240">The language of the template to create.</span></span> <span data-ttu-id="8cfa3-241">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8cfa3-242">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8cfa3-243">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-243">The name for the created output.</span></span> <span data-ttu-id="8cfa3-244">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8cfa3-245">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-245">Location to place the generated output.</span></span> <span data-ttu-id="8cfa3-246">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="8cfa3-247">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="8cfa3-247">Template options</span></span>

<span data-ttu-id="8cfa3-248">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-248">Each project template may have additional options available.</span></span> <span data-ttu-id="8cfa3-249">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="8cfa3-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="8cfa3-251">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="8cfa3-252">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-253">**classlib**</span></span>

<span data-ttu-id="8cfa3-254">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8cfa3-255">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="8cfa3-256">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="8cfa3-257">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-258">**mstest, xunit**</span></span>

<span data-ttu-id="8cfa3-259">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="8cfa3-260">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-261">**globaljson**</span></span>

<span data-ttu-id="8cfa3-262">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="8cfa3-263">**web**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-263">**web**</span></span>

<span data-ttu-id="8cfa3-264">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8cfa3-265">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-266">**webapi**</span></span>

<span data-ttu-id="8cfa3-267">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8cfa3-268">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-268">The possible values are:</span></span>

- <span data-ttu-id="8cfa3-269">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8cfa3-270">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8cfa3-271">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8cfa3-272">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8cfa3-273">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8cfa3-274">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8cfa3-275">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="8cfa3-276">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8cfa3-277">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-278">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8cfa3-279">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8cfa3-280">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8cfa3-281">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8cfa3-282">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="8cfa3-283">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8cfa3-284">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8cfa3-285">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="8cfa3-286">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8cfa3-287">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8cfa3-288">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="8cfa3-289">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8cfa3-290">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8cfa3-291">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8cfa3-292">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8cfa3-293">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8cfa3-294">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-295">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-296">**mvc, razor**</span></span>

<span data-ttu-id="8cfa3-297">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="8cfa3-298">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-298">The possible values are:</span></span>

- <span data-ttu-id="8cfa3-299">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="8cfa3-300">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="8cfa3-301">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="8cfa3-302">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="8cfa3-303">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="8cfa3-304">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="8cfa3-305">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="8cfa3-306">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="8cfa3-307">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="8cfa3-308">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="8cfa3-309">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-310">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="8cfa3-311">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-312">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="8cfa3-313">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-314">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="8cfa3-315">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="8cfa3-316">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="8cfa3-317">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="8cfa3-318">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="8cfa3-319">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="8cfa3-320">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="8cfa3-321">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="8cfa3-322">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="8cfa3-323">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="8cfa3-324">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="8cfa3-325">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="8cfa3-326">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="8cfa3-327">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="8cfa3-328">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="8cfa3-329">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="8cfa3-330">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="8cfa3-331">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="8cfa3-332">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="8cfa3-333">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="8cfa3-334">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="8cfa3-335">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="8cfa3-336">**page**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-336">**page**</span></span>

<span data-ttu-id="8cfa3-337">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8cfa3-338">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="8cfa3-339">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="8cfa3-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-340">**viewimports**</span></span>

<span data-ttu-id="8cfa3-341">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="8cfa3-342">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="8cfa3-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="8cfa3-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="8cfa3-344">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="8cfa3-345">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8cfa3-346">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8cfa3-347">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8cfa3-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-348">**classlib**</span></span>

<span data-ttu-id="8cfa3-349">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8cfa3-350">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="8cfa3-351">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="8cfa3-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="8cfa3-352">**mvc**</span></span>

<span data-ttu-id="8cfa3-353">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8cfa3-354">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="8cfa3-355">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="8cfa3-356">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="8cfa3-357">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="8cfa3-358">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-358">The default value is `None`.</span></span>

<span data-ttu-id="8cfa3-359">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="8cfa3-360">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-360">Values: `true` or `false`.</span></span> <span data-ttu-id="8cfa3-361">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="8cfa3-362">使用例</span><span class="sxs-lookup"><span data-stu-id="8cfa3-362">Examples</span></span>

<span data-ttu-id="8cfa3-363">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="8cfa3-364">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core 2.0 SDK またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="8cfa3-365">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。 .NET Core 2.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="8cfa3-366">.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="8cfa3-367">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8cfa3-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="8cfa3-368">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cfa3-368">See also</span></span>

[<span data-ttu-id="8cfa3-369">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="8cfa3-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="8cfa3-370">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="8cfa3-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="8cfa3-371">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="8cfa3-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="8cfa3-372">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="8cfa3-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
