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
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-new"></a><span data-ttu-id="f070b-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f070b-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f070b-105">名前</span><span class="sxs-lookup"><span data-stu-id="f070b-105">Name</span></span>

<span data-ttu-id="f070b-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f070b-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f070b-107">構文</span><span class="sxs-lookup"><span data-stu-id="f070b-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f070b-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f070b-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f070b-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f070b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f070b-110">説明</span><span class="sxs-lookup"><span data-stu-id="f070b-110">Description</span></span>

<span data-ttu-id="f070b-111">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f070b-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="f070b-112">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="f070b-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="f070b-113">引数</span><span class="sxs-lookup"><span data-stu-id="f070b-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="f070b-114">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="f070b-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f070b-115">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f070b-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f070b-116">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f070b-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f070b-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f070b-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f070b-118">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f070b-118">The command contains a default list of templates.</span></span> <span data-ttu-id="f070b-119">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="f070b-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f070b-120">次の表は、.NET Core 2.0 SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="f070b-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="f070b-121">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f070b-122">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="f070b-122">Template description</span></span>                          | <span data-ttu-id="f070b-123">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="f070b-123">Template name</span></span>  | <span data-ttu-id="f070b-124">言語</span><span class="sxs-lookup"><span data-stu-id="f070b-124">Languages</span></span>     |
|----------------------------------------------|----------------|---------------|
| <span data-ttu-id="f070b-125">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f070b-125">Console application</span></span>                          | <span data-ttu-id="f070b-126">コンソール</span><span class="sxs-lookup"><span data-stu-id="f070b-126">console</span></span>        | <span data-ttu-id="f070b-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f070b-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f070b-128">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f070b-128">Class library</span></span>                                | <span data-ttu-id="f070b-129">classlib</span><span class="sxs-lookup"><span data-stu-id="f070b-129">classlib</span></span>       | <span data-ttu-id="f070b-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f070b-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f070b-131">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f070b-131">Unit test project</span></span>                            | <span data-ttu-id="f070b-132">mstest</span><span class="sxs-lookup"><span data-stu-id="f070b-132">mstest</span></span>         | <span data-ttu-id="f070b-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f070b-133">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f070b-134">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f070b-134">xUnit test project</span></span>                           | <span data-ttu-id="f070b-135">xunit</span><span class="sxs-lookup"><span data-stu-id="f070b-135">xunit</span></span>          | <span data-ttu-id="f070b-136">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f070b-136">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f070b-137">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="f070b-137">ASP.NET Core empty</span></span>                           | <span data-ttu-id="f070b-138">Web</span><span class="sxs-lookup"><span data-stu-id="f070b-138">web</span></span>            | <span data-ttu-id="f070b-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-139">[C#], F#</span></span>      |
| <span data-ttu-id="f070b-140">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="f070b-140">ASP.NET Core Web App (Model-View-Controller)</span></span> | <span data-ttu-id="f070b-141">mvc</span><span class="sxs-lookup"><span data-stu-id="f070b-141">mvc</span></span>            | <span data-ttu-id="f070b-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-142">[C#], F#</span></span>      |
| <span data-ttu-id="f070b-143">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f070b-143">ASP.NET Core Web App</span></span>                         | <span data-ttu-id="f070b-144">razor</span><span class="sxs-lookup"><span data-stu-id="f070b-144">razor</span></span>          | <span data-ttu-id="f070b-145">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-145">[C#]</span></span>          |
| <span data-ttu-id="f070b-146">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f070b-146">ASP.NET Core with Angular</span></span>                    | <span data-ttu-id="f070b-147">angular</span><span class="sxs-lookup"><span data-stu-id="f070b-147">angular</span></span>        | <span data-ttu-id="f070b-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-148">[C#]</span></span>          |
| <span data-ttu-id="f070b-149">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f070b-149">ASP.NET Core with React.js</span></span>                   | <span data-ttu-id="f070b-150">react</span><span class="sxs-lookup"><span data-stu-id="f070b-150">react</span></span>          | <span data-ttu-id="f070b-151">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-151">[C#]</span></span>          |
| <span data-ttu-id="f070b-152">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f070b-152">ASP.NET Core with React.js and Redux</span></span>         | <span data-ttu-id="f070b-153">reactredux</span><span class="sxs-lookup"><span data-stu-id="f070b-153">reactredux</span></span>     | <span data-ttu-id="f070b-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-154">[C#]</span></span>          |
| <span data-ttu-id="f070b-155">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f070b-155">ASP.NET Core Web API</span></span>                         | <span data-ttu-id="f070b-156">webapi</span><span class="sxs-lookup"><span data-stu-id="f070b-156">webapi</span></span>         | <span data-ttu-id="f070b-157">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-157">[C#], F#</span></span>      |
| <span data-ttu-id="f070b-158">global.json file</span><span class="sxs-lookup"><span data-stu-id="f070b-158">global.json file</span></span>                             | <span data-ttu-id="f070b-159">globaljson</span><span class="sxs-lookup"><span data-stu-id="f070b-159">globaljson</span></span>     |               |
| <span data-ttu-id="f070b-160">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="f070b-160">Nuget config</span></span>                                 | <span data-ttu-id="f070b-161">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="f070b-161">nugetconfig</span></span>    |               |
| <span data-ttu-id="f070b-162">Web 構成</span><span class="sxs-lookup"><span data-stu-id="f070b-162">Web config</span></span>                                   | <span data-ttu-id="f070b-163">webconfig</span><span class="sxs-lookup"><span data-stu-id="f070b-163">webconfig</span></span>      |               |
| <span data-ttu-id="f070b-164">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="f070b-164">Solution file</span></span>                                | <span data-ttu-id="f070b-165">sln</span><span class="sxs-lookup"><span data-stu-id="f070b-165">sln</span></span>            |               |
| <span data-ttu-id="f070b-166">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="f070b-166">Razor page</span></span>                                   | <span data-ttu-id="f070b-167">ページ</span><span class="sxs-lookup"><span data-stu-id="f070b-167">page</span></span>           |               |
| <span data-ttu-id="f070b-168">MVC/ViewImports</span><span class="sxs-lookup"><span data-stu-id="f070b-168">MVC/ViewImports</span></span>                              | <span data-ttu-id="f070b-169">viewimports</span><span class="sxs-lookup"><span data-stu-id="f070b-169">viewimports</span></span>    |               |
| <span data-ttu-id="f070b-170">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f070b-170">MVC ViewStart</span></span>                                | <span data-ttu-id="f070b-171">viewstart</span><span class="sxs-lookup"><span data-stu-id="f070b-171">viewstart</span></span>      |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f070b-172">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f070b-172">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f070b-173">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f070b-173">The command contains a default list of templates.</span></span> <span data-ttu-id="f070b-174">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="f070b-174">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="f070b-175">次の表は、.NET Core 1.x SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="f070b-175">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="f070b-176">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-176">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f070b-177">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="f070b-177">Template description</span></span>  | <span data-ttu-id="f070b-178">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="f070b-178">Template name</span></span>  | <span data-ttu-id="f070b-179">言語</span><span class="sxs-lookup"><span data-stu-id="f070b-179">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="f070b-180">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f070b-180">Console application</span></span>  | <span data-ttu-id="f070b-181">コンソール</span><span class="sxs-lookup"><span data-stu-id="f070b-181">console</span></span>        | <span data-ttu-id="f070b-182">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-182">[C#], F#</span></span>  |
| <span data-ttu-id="f070b-183">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f070b-183">Class library</span></span>        | <span data-ttu-id="f070b-184">classlib</span><span class="sxs-lookup"><span data-stu-id="f070b-184">classlib</span></span>       | <span data-ttu-id="f070b-185">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-185">[C#], F#</span></span>  |
| <span data-ttu-id="f070b-186">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f070b-186">Unit test project</span></span>    | <span data-ttu-id="f070b-187">mstest</span><span class="sxs-lookup"><span data-stu-id="f070b-187">mstest</span></span>         | <span data-ttu-id="f070b-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-188">[C#], F#</span></span>  |
| <span data-ttu-id="f070b-189">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f070b-189">xUnit test project</span></span>   | <span data-ttu-id="f070b-190">xunit</span><span class="sxs-lookup"><span data-stu-id="f070b-190">xunit</span></span>          | <span data-ttu-id="f070b-191">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-191">[C#], F#</span></span>  |
| <span data-ttu-id="f070b-192">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="f070b-192">ASP.NET Core empty</span></span>   | <span data-ttu-id="f070b-193">Web</span><span class="sxs-lookup"><span data-stu-id="f070b-193">web</span></span>            | <span data-ttu-id="f070b-194">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-194">[C#]</span></span>      |
| <span data-ttu-id="f070b-195">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f070b-195">ASP.NET Core Web App</span></span> | <span data-ttu-id="f070b-196">mvc</span><span class="sxs-lookup"><span data-stu-id="f070b-196">mvc</span></span>            | <span data-ttu-id="f070b-197">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f070b-197">[C#], F#</span></span>  |
| <span data-ttu-id="f070b-198">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f070b-198">ASP.NET Core Web API</span></span> | <span data-ttu-id="f070b-199">webapi</span><span class="sxs-lookup"><span data-stu-id="f070b-199">webapi</span></span>         | <span data-ttu-id="f070b-200">[C#]</span><span class="sxs-lookup"><span data-stu-id="f070b-200">[C#]</span></span>      |
| <span data-ttu-id="f070b-201">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="f070b-201">Nuget config</span></span>         | <span data-ttu-id="f070b-202">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="f070b-202">nugetconfig</span></span>    |           |
| <span data-ttu-id="f070b-203">Web 構成</span><span class="sxs-lookup"><span data-stu-id="f070b-203">Web config</span></span>           | <span data-ttu-id="f070b-204">webconfig</span><span class="sxs-lookup"><span data-stu-id="f070b-204">webconfig</span></span>      |           |
| <span data-ttu-id="f070b-205">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="f070b-205">Solution file</span></span>        | <span data-ttu-id="f070b-206">sln</span><span class="sxs-lookup"><span data-stu-id="f070b-206">sln</span></span>            |           |

---

## <a name="options"></a><span data-ttu-id="f070b-207">オプション</span><span class="sxs-lookup"><span data-stu-id="f070b-207">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f070b-208">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f070b-208">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="f070b-209">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-209">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f070b-210">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f070b-210">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f070b-211">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f070b-211">Prints out help for the command.</span></span> <span data-ttu-id="f070b-212">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f070b-212">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="f070b-213">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f070b-213">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f070b-214">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f070b-214">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="f070b-215">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f070b-215">Lists templates containing the specified name.</span></span> <span data-ttu-id="f070b-216">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-216">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f070b-217">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="f070b-217">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="f070b-218">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="f070b-218">The language of the template to create.</span></span> <span data-ttu-id="f070b-219">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f070b-219">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f070b-220">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="f070b-220">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f070b-221">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="f070b-221">The name for the created output.</span></span> <span data-ttu-id="f070b-222">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-222">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f070b-223">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="f070b-223">Location to place the generated output.</span></span> <span data-ttu-id="f070b-224">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f070b-224">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="f070b-225">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="f070b-225">Filters templates based on available types.</span></span> <span data-ttu-id="f070b-226">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="f070b-226">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="f070b-227">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="f070b-227">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="f070b-228">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f070b-228">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f070b-229">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f070b-229">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f070b-230">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="f070b-230">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f070b-231">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f070b-231">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="f070b-232">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-232">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="f070b-233">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-233">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="f070b-234">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f070b-234">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f070b-235">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f070b-235">Prints out help for the command.</span></span> <span data-ttu-id="f070b-236">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f070b-236">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="f070b-237">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f070b-237">Lists templates containing the specified name.</span></span> <span data-ttu-id="f070b-238">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-238">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f070b-239">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="f070b-239">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="f070b-240">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="f070b-240">The language of the template to create.</span></span> <span data-ttu-id="f070b-241">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f070b-241">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f070b-242">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="f070b-242">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f070b-243">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="f070b-243">The name for the created output.</span></span> <span data-ttu-id="f070b-244">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-244">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f070b-245">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="f070b-245">Location to place the generated output.</span></span> <span data-ttu-id="f070b-246">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f070b-246">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="f070b-247">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="f070b-247">Template options</span></span>

<span data-ttu-id="f070b-248">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f070b-248">Each project template may have additional options available.</span></span> <span data-ttu-id="f070b-249">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="f070b-249">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="f070b-250">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="f070b-250">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="f070b-251">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="f070b-251">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="f070b-252">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-252">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-253">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f070b-253">**classlib**</span></span>

<span data-ttu-id="f070b-254">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-254">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f070b-255">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-255">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f070b-256">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-256">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="f070b-257">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-257">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-258">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="f070b-258">**mstest, xunit**</span></span>

<span data-ttu-id="f070b-259">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f070b-259">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="f070b-260">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-260">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-261">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="f070b-261">**globaljson**</span></span>

<span data-ttu-id="f070b-262">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-262">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="f070b-263">**web**</span><span class="sxs-lookup"><span data-stu-id="f070b-263">**web**</span></span>

<span data-ttu-id="f070b-264">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f070b-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f070b-265">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-265">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-266">**webapi**</span><span class="sxs-lookup"><span data-stu-id="f070b-266">**webapi**</span></span>

<span data-ttu-id="f070b-267">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f070b-267">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f070b-268">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f070b-268">The possible values are:</span></span>

- <span data-ttu-id="f070b-269">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f070b-269">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f070b-270">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-270">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f070b-271">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-271">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f070b-272">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-272">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f070b-273">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f070b-273">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f070b-274">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-274">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f070b-275">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-275">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f070b-276">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-276">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f070b-277">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-277">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-278">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f070b-278">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f070b-279">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-279">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f070b-280">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-280">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f070b-281">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-281">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f070b-282">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-282">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f070b-283">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-283">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f070b-284">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f070b-284">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f070b-285">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-285">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f070b-286">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-286">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f070b-287">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-287">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f070b-288">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-288">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f070b-289">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-289">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f070b-290">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f070b-290">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f070b-291">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-291">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f070b-292">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f070b-292">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f070b-293">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-293">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f070b-294">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-294">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-295">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-295">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-296">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="f070b-296">**mvc, razor**</span></span>

<span data-ttu-id="f070b-297">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f070b-297">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f070b-298">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f070b-298">The possible values are:</span></span>

- <span data-ttu-id="f070b-299">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f070b-299">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f070b-300">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="f070b-300">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="f070b-301">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-301">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f070b-302">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-302">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f070b-303">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="f070b-303">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="f070b-304">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f070b-304">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f070b-305">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f070b-305">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f070b-306">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-306">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f070b-307">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-307">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="f070b-308">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-308">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f070b-309">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-309">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-310">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-310">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="f070b-311">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-311">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-312">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-312">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="f070b-313">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-313">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-314">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f070b-314">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f070b-315">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-315">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f070b-316">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-316">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f070b-317">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-317">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f070b-318">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-318">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f070b-319">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-319">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f070b-320">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f070b-320">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f070b-321">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-321">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="f070b-322">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-322">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f070b-323">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f070b-323">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f070b-324">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-324">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="f070b-325">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-325">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f070b-326">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="f070b-326">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f070b-327">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f070b-327">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="f070b-328">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-328">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="f070b-329">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f070b-329">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f070b-330">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-330">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f070b-331">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f070b-331">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f070b-332">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="f070b-332">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="f070b-333">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-333">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f070b-334">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f070b-334">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f070b-335">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f070b-335">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="f070b-336">**page**</span><span class="sxs-lookup"><span data-stu-id="f070b-336">**page**</span></span>

<span data-ttu-id="f070b-337">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f070b-337">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f070b-338">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-338">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="f070b-339">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="f070b-339">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="f070b-340">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="f070b-340">**viewimports**</span></span>

<span data-ttu-id="f070b-341">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f070b-341">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f070b-342">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-342">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f070b-343">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f070b-343">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f070b-344">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="f070b-344">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="f070b-345">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-345">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f070b-346">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-346">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f070b-347">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-347">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f070b-348">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f070b-348">**classlib**</span></span>

<span data-ttu-id="f070b-349">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-349">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f070b-350">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-350">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="f070b-351">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-351">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="f070b-352">**mvc**</span><span class="sxs-lookup"><span data-stu-id="f070b-352">**mvc**</span></span>

<span data-ttu-id="f070b-353">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-353">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f070b-354">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-354">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f070b-355">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-355">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f070b-356">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f070b-356">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="f070b-357">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-357">Values: `None` or `Individual`.</span></span> <span data-ttu-id="f070b-358">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-358">The default value is `None`.</span></span>

<span data-ttu-id="f070b-359">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f070b-359">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="f070b-360">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-360">Values: `true` or `false`.</span></span> <span data-ttu-id="f070b-361">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f070b-361">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f070b-362">例</span><span class="sxs-lookup"><span data-stu-id="f070b-362">Examples</span></span>

<span data-ttu-id="f070b-363">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f070b-363">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="f070b-364">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core 2.0 SDK またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="f070b-364">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="f070b-365">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。.NET Core 2.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="f070b-365">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="f070b-366">.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f070b-366">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="f070b-367">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f070b-367">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="f070b-368">関連項目</span><span class="sxs-lookup"><span data-stu-id="f070b-368">See also</span></span>

[<span data-ttu-id="f070b-369">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="f070b-369">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="f070b-370">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="f070b-370">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="f070b-371">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="f070b-371">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="f070b-372">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="f070b-372">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
