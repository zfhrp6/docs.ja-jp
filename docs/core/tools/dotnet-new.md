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
ms.workload:
- dotnetcore
ms.openlocfilehash: ea94c875ae6fe82d0e5d35ba8ca3fd47971fbbe6
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="adf77-104">dotnet new</span><span class="sxs-lookup"><span data-stu-id="adf77-104">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="adf77-105">name</span><span class="sxs-lookup"><span data-stu-id="adf77-105">Name</span></span>

<span data-ttu-id="adf77-106">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="adf77-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="adf77-107">構文</span><span class="sxs-lookup"><span data-stu-id="adf77-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="adf77-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="adf77-108">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="adf77-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="adf77-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="adf77-110">説明</span><span class="sxs-lookup"><span data-stu-id="adf77-110">Description</span></span>

<span data-ttu-id="adf77-111">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="adf77-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="adf77-112">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="adf77-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="adf77-113">引数</span><span class="sxs-lookup"><span data-stu-id="adf77-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="adf77-114">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="adf77-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="adf77-115">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="adf77-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="adf77-116">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adf77-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="adf77-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="adf77-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="adf77-118">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="adf77-118">The command contains a default list of templates.</span></span> <span data-ttu-id="adf77-119">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="adf77-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="adf77-120">次の表は、.NET Core 2.0 SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="adf77-120">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="adf77-121">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="adf77-122">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="adf77-122">Template description</span></span>                          | <span data-ttu-id="adf77-123">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="adf77-123">Template name</span></span> | <span data-ttu-id="adf77-124">言語</span><span class="sxs-lookup"><span data-stu-id="adf77-124">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="adf77-125">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="adf77-125">Console application</span></span>                          | `console`     | <span data-ttu-id="adf77-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="adf77-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="adf77-127">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="adf77-127">Class library</span></span>                                | `classlib`    | <span data-ttu-id="adf77-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="adf77-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="adf77-129">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="adf77-129">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="adf77-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="adf77-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="adf77-131">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="adf77-131">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="adf77-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="adf77-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="adf77-133">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="adf77-133">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="adf77-134">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-134">[C#], F#</span></span>      |
| <span data-ttu-id="adf77-135">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="adf77-135">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="adf77-136">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-136">[C#], F#</span></span>      |
| <span data-ttu-id="adf77-137">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="adf77-137">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="adf77-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-138">[C#]</span></span>          |
| <span data-ttu-id="adf77-139">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="adf77-139">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="adf77-140">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-140">[C#]</span></span>          |
| <span data-ttu-id="adf77-141">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="adf77-141">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="adf77-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-142">[C#]</span></span>          |
| <span data-ttu-id="adf77-143">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="adf77-143">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="adf77-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-144">[C#]</span></span>          |
| <span data-ttu-id="adf77-145">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="adf77-145">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="adf77-146">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-146">[C#], F#</span></span>      |
| <span data-ttu-id="adf77-147">global.json file</span><span class="sxs-lookup"><span data-stu-id="adf77-147">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="adf77-148">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="adf77-148">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="adf77-149">Web 構成</span><span class="sxs-lookup"><span data-stu-id="adf77-149">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="adf77-150">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="adf77-150">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="adf77-151">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="adf77-151">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="adf77-152">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="adf77-152">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="adf77-153">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="adf77-153">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="adf77-154">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="adf77-154">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="adf77-155">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="adf77-155">The command contains a default list of templates.</span></span> <span data-ttu-id="adf77-156">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="adf77-156">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="adf77-157">次の表は、.NET Core 1.x SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="adf77-157">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="adf77-158">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-158">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="adf77-159">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="adf77-159">Template description</span></span>  | <span data-ttu-id="adf77-160">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="adf77-160">Template name</span></span> | <span data-ttu-id="adf77-161">言語</span><span class="sxs-lookup"><span data-stu-id="adf77-161">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="adf77-162">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="adf77-162">Console application</span></span>  | `console`     | <span data-ttu-id="adf77-163">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-163">[C#], F#</span></span>  |
| <span data-ttu-id="adf77-164">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="adf77-164">Class library</span></span>        | `classlib`    | <span data-ttu-id="adf77-165">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-165">[C#], F#</span></span>  |
| <span data-ttu-id="adf77-166">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="adf77-166">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="adf77-167">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-167">[C#], F#</span></span>  |
| <span data-ttu-id="adf77-168">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="adf77-168">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="adf77-169">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-169">[C#], F#</span></span>  |
| <span data-ttu-id="adf77-170">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="adf77-170">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="adf77-171">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-171">[C#]</span></span>      |
| <span data-ttu-id="adf77-172">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="adf77-172">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="adf77-173">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="adf77-173">[C#], F#</span></span>  |
| <span data-ttu-id="adf77-174">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="adf77-174">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="adf77-175">[C#]</span><span class="sxs-lookup"><span data-stu-id="adf77-175">[C#]</span></span>      |
| <span data-ttu-id="adf77-176">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="adf77-176">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="adf77-177">Web 構成</span><span class="sxs-lookup"><span data-stu-id="adf77-177">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="adf77-178">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="adf77-178">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="adf77-179">オプション</span><span class="sxs-lookup"><span data-stu-id="adf77-179">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="adf77-180">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="adf77-180">.NET Core 2.x</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="adf77-181">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-181">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="adf77-182">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="adf77-182">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="adf77-183">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="adf77-183">Prints out help for the command.</span></span> <span data-ttu-id="adf77-184">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="adf77-184">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="adf77-185">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="adf77-185">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="adf77-186">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adf77-186">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="adf77-187">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="adf77-187">Lists templates containing the specified name.</span></span> <span data-ttu-id="adf77-188">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-188">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="adf77-189">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="adf77-189">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="adf77-190">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="adf77-190">The language of the template to create.</span></span> <span data-ttu-id="adf77-191">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="adf77-191">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="adf77-192">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="adf77-192">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="adf77-193">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="adf77-193">The name for the created output.</span></span> <span data-ttu-id="adf77-194">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-194">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="adf77-195">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="adf77-195">Location to place the generated output.</span></span> <span data-ttu-id="adf77-196">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="adf77-196">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="adf77-197">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="adf77-197">Filters templates based on available types.</span></span> <span data-ttu-id="adf77-198">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="adf77-198">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="adf77-199">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="adf77-199">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="adf77-200">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adf77-200">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="adf77-201">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="adf77-201">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="adf77-202">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="adf77-202">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="adf77-203">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="adf77-203">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="adf77-204">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-204">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="adf77-205">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-205">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="adf77-206">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="adf77-206">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="adf77-207">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="adf77-207">Prints out help for the command.</span></span> <span data-ttu-id="adf77-208">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="adf77-208">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="adf77-209">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="adf77-209">Lists templates containing the specified name.</span></span> <span data-ttu-id="adf77-210">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-210">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="adf77-211">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="adf77-211">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="adf77-212">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="adf77-212">The language of the template to create.</span></span> <span data-ttu-id="adf77-213">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="adf77-213">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="adf77-214">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="adf77-214">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="adf77-215">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="adf77-215">The name for the created output.</span></span> <span data-ttu-id="adf77-216">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-216">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="adf77-217">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="adf77-217">Location to place the generated output.</span></span> <span data-ttu-id="adf77-218">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="adf77-218">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="adf77-219">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="adf77-219">Template options</span></span>

<span data-ttu-id="adf77-220">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="adf77-220">Each project template may have additional options available.</span></span> <span data-ttu-id="adf77-221">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="adf77-221">The core templates have the following additional options:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="adf77-222">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="adf77-222">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="adf77-223">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="adf77-223">**console, angular, react, reactredux**</span></span>

<span data-ttu-id="adf77-224">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-224">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-225">**classlib**</span><span class="sxs-lookup"><span data-stu-id="adf77-225">**classlib**</span></span>

<span data-ttu-id="adf77-226">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-226">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="adf77-227">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-227">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="adf77-228">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-228">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="adf77-229">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-229">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-230">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="adf77-230">**mstest, xunit**</span></span>

<span data-ttu-id="adf77-231">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="adf77-231">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="adf77-232">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-232">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-233">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="adf77-233">**globaljson**</span></span>

<span data-ttu-id="adf77-234">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-234">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="adf77-235">**web**</span><span class="sxs-lookup"><span data-stu-id="adf77-235">**web**</span></span>

<span data-ttu-id="adf77-236">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="adf77-236">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="adf77-237">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-237">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-238">**webapi**</span><span class="sxs-lookup"><span data-stu-id="adf77-238">**webapi**</span></span>

<span data-ttu-id="adf77-239">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="adf77-239">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="adf77-240">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="adf77-240">The possible values are:</span></span>

- <span data-ttu-id="adf77-241">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="adf77-241">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="adf77-242">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-242">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="adf77-243">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-243">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="adf77-244">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-244">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="adf77-245">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="adf77-245">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="adf77-246">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-246">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="adf77-247">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-247">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="adf77-248">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-248">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="adf77-249">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-249">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-250">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="adf77-250">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="adf77-251">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-251">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="adf77-252">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-252">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="adf77-253">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-253">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="adf77-254">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-254">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="adf77-255">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-255">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="adf77-256">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="adf77-256">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="adf77-257">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-257">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="adf77-258">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-258">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="adf77-259">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-259">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="adf77-260">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-260">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="adf77-261">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-261">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="adf77-262">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="adf77-262">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="adf77-263">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-263">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="adf77-264">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="adf77-264">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="adf77-265">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-265">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="adf77-266">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-266">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-267">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-267">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-268">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="adf77-268">**mvc, razor**</span></span>

<span data-ttu-id="adf77-269">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="adf77-269">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="adf77-270">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="adf77-270">The possible values are:</span></span>

- <span data-ttu-id="adf77-271">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="adf77-271">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="adf77-272">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="adf77-272">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="adf77-273">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-273">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="adf77-274">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-274">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="adf77-275">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="adf77-275">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="adf77-276">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="adf77-276">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="adf77-277">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="adf77-277">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="adf77-278">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-278">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="adf77-279">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-279">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="adf77-280">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-280">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="adf77-281">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-281">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-282">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-282">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="adf77-283">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-284">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-284">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="adf77-285">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-286">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="adf77-286">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="adf77-287">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-287">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="adf77-288">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-288">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="adf77-289">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-289">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="adf77-290">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-290">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="adf77-291">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-291">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="adf77-292">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="adf77-292">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="adf77-293">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-293">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="adf77-294">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-294">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="adf77-295">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="adf77-295">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="adf77-296">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-296">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="adf77-297">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-297">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="adf77-298">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="adf77-298">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="adf77-299">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="adf77-299">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="adf77-300">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-300">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="adf77-301">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="adf77-301">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="adf77-302">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-302">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="adf77-303">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="adf77-303">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="adf77-304">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="adf77-304">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="adf77-305">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-305">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="adf77-306">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adf77-306">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="adf77-307">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="adf77-307">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="adf77-308">**page**</span><span class="sxs-lookup"><span data-stu-id="adf77-308">**page**</span></span>

<span data-ttu-id="adf77-309">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="adf77-309">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="adf77-310">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-310">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="adf77-311">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="adf77-311">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="adf77-312">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="adf77-312">**viewimports**</span></span>

<span data-ttu-id="adf77-313">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="adf77-313">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="adf77-314">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-314">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="adf77-315">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="adf77-315">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="adf77-316">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="adf77-316">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="adf77-317">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-317">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="adf77-318">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-318">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="adf77-319">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-319">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="adf77-320">**classlib**</span><span class="sxs-lookup"><span data-stu-id="adf77-320">**classlib**</span></span>

<span data-ttu-id="adf77-321">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-321">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="adf77-322">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-322">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="adf77-323">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-323">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="adf77-324">**mvc**</span><span class="sxs-lookup"><span data-stu-id="adf77-324">**mvc**</span></span>

<span data-ttu-id="adf77-325">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-325">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="adf77-326">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-326">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="adf77-327">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-327">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="adf77-328">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="adf77-328">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="adf77-329">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-329">Values: `None` or `Individual`.</span></span> <span data-ttu-id="adf77-330">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-330">The default value is `None`.</span></span>

<span data-ttu-id="adf77-331">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="adf77-331">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="adf77-332">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-332">Values: `true` or `false`.</span></span> <span data-ttu-id="adf77-333">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="adf77-333">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="adf77-334">使用例</span><span class="sxs-lookup"><span data-stu-id="adf77-334">Examples</span></span>

<span data-ttu-id="adf77-335">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="adf77-335">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="adf77-336">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core 2.0 SDK またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="adf77-336">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="adf77-337">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。 .NET Core 2.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="adf77-337">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="adf77-338">.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="adf77-338">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="adf77-339">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="adf77-339">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

## <a name="see-also"></a><span data-ttu-id="adf77-340">関連項目</span><span class="sxs-lookup"><span data-stu-id="adf77-340">See also</span></span>

[<span data-ttu-id="adf77-341">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="adf77-341">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="adf77-342">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="adf77-342">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="adf77-343">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="adf77-343">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="adf77-344">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="adf77-344">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
