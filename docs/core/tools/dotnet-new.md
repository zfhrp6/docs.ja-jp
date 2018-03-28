---
title: dotnet new コマンド - .NET Core CLI
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
author: mairaw
ms.author: mairaw
ms.date: 03/21/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2cbd42195d0ec713d2ccb4af823075ece950ceff
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="5620d-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5620d-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5620d-104">name</span><span class="sxs-lookup"><span data-stu-id="5620d-104">Name</span></span>

<span data-ttu-id="5620d-105">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5620d-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5620d-106">構文</span><span class="sxs-lookup"><span data-stu-id="5620d-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="5620d-107">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5620d-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5620d-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5620d-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="5620d-109">説明</span><span class="sxs-lookup"><span data-stu-id="5620d-109">Description</span></span>

<span data-ttu-id="5620d-110">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="5620d-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="5620d-111">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="5620d-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="5620d-112">引数</span><span class="sxs-lookup"><span data-stu-id="5620d-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="5620d-113">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="5620d-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="5620d-114">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="5620d-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="5620d-115">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5620d-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="5620d-116">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5620d-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="5620d-117">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5620d-117">The command contains a default list of templates.</span></span> <span data-ttu-id="5620d-118">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="5620d-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="5620d-119">次の表は、.NET Core 2.0 SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="5620d-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="5620d-120">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5620d-121">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="5620d-121">Template description</span></span>                          | <span data-ttu-id="5620d-122">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="5620d-122">Template name</span></span> | <span data-ttu-id="5620d-123">言語</span><span class="sxs-lookup"><span data-stu-id="5620d-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="5620d-124">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="5620d-124">Console application</span></span>                          | `console`     | <span data-ttu-id="5620d-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5620d-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5620d-126">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="5620d-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="5620d-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5620d-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5620d-128">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="5620d-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="5620d-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5620d-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5620d-130">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="5620d-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="5620d-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="5620d-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="5620d-132">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="5620d-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="5620d-133">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-133">[C#], F#</span></span>      |
| <span data-ttu-id="5620d-134">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="5620d-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="5620d-135">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-135">[C#], F#</span></span>      |
| <span data-ttu-id="5620d-136">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="5620d-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="5620d-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-137">[C#]</span></span>          |
| <span data-ttu-id="5620d-138">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5620d-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="5620d-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-139">[C#]</span></span>          |
| <span data-ttu-id="5620d-140">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5620d-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="5620d-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-141">[C#]</span></span>          |
| <span data-ttu-id="5620d-142">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5620d-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="5620d-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-143">[C#]</span></span>          |
| <span data-ttu-id="5620d-144">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="5620d-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="5620d-145">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-145">[C#], F#</span></span>      |
| <span data-ttu-id="5620d-146">global.json file</span><span class="sxs-lookup"><span data-stu-id="5620d-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="5620d-147">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="5620d-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="5620d-148">Web 構成</span><span class="sxs-lookup"><span data-stu-id="5620d-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="5620d-149">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="5620d-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="5620d-150">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="5620d-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="5620d-151">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="5620d-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="5620d-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="5620d-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5620d-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5620d-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5620d-154">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5620d-154">The command contains a default list of templates.</span></span> <span data-ttu-id="5620d-155">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="5620d-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="5620d-156">次の表は、.NET Core 1.x SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="5620d-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="5620d-157">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="5620d-158">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="5620d-158">Template description</span></span>  | <span data-ttu-id="5620d-159">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="5620d-159">Template name</span></span> | <span data-ttu-id="5620d-160">言語</span><span class="sxs-lookup"><span data-stu-id="5620d-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="5620d-161">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="5620d-161">Console application</span></span>  | `console`     | <span data-ttu-id="5620d-162">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-162">[C#], F#</span></span>  |
| <span data-ttu-id="5620d-163">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="5620d-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="5620d-164">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-164">[C#], F#</span></span>  |
| <span data-ttu-id="5620d-165">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="5620d-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="5620d-166">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-166">[C#], F#</span></span>  |
| <span data-ttu-id="5620d-167">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="5620d-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="5620d-168">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-168">[C#], F#</span></span>  |
| <span data-ttu-id="5620d-169">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="5620d-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="5620d-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-170">[C#]</span></span>      |
| <span data-ttu-id="5620d-171">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="5620d-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="5620d-172">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="5620d-172">[C#], F#</span></span>  |
| <span data-ttu-id="5620d-173">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="5620d-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="5620d-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="5620d-174">[C#]</span></span>      |
| <span data-ttu-id="5620d-175">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="5620d-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="5620d-176">Web 構成</span><span class="sxs-lookup"><span data-stu-id="5620d-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="5620d-177">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="5620d-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="5620d-178">オプション</span><span class="sxs-lookup"><span data-stu-id="5620d-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="5620d-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5620d-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="5620d-180">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="5620d-181">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="5620d-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5620d-182">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="5620d-182">Prints out help for the command.</span></span> <span data-ttu-id="5620d-183">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5620d-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="5620d-184">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="5620d-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="5620d-185">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5620d-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="5620d-186">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="5620d-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="5620d-187">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5620d-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="5620d-188">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5620d-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="5620d-189">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="5620d-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="5620d-190">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5620d-191">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="5620d-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="5620d-192">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="5620d-192">The language of the template to create.</span></span> <span data-ttu-id="5620d-193">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5620d-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5620d-194">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="5620d-194">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5620d-195">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="5620d-195">The name for the created output.</span></span> <span data-ttu-id="5620d-196">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5620d-197">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="5620d-197">Location to place the generated output.</span></span> <span data-ttu-id="5620d-198">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="5620d-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="5620d-199">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="5620d-199">Filters templates based on available types.</span></span> <span data-ttu-id="5620d-200">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="5620d-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="5620d-201">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5620d-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="5620d-202">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5620d-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="5620d-203">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5620d-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="5620d-204">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="5620d-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5620d-205">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5620d-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="5620d-206">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="5620d-207">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="5620d-208">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="5620d-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="5620d-209">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="5620d-209">Prints out help for the command.</span></span> <span data-ttu-id="5620d-210">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5620d-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="5620d-211">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="5620d-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="5620d-212">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="5620d-213">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="5620d-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="5620d-214">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="5620d-214">The language of the template to create.</span></span> <span data-ttu-id="5620d-215">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5620d-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="5620d-216">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="5620d-216">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="5620d-217">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="5620d-217">The name for the created output.</span></span> <span data-ttu-id="5620d-218">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="5620d-219">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="5620d-219">Location to place the generated output.</span></span> <span data-ttu-id="5620d-220">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="5620d-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="5620d-221">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="5620d-221">Template options</span></span>

<span data-ttu-id="5620d-222">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5620d-222">Each project template may have additional options available.</span></span> <span data-ttu-id="5620d-223">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="5620d-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="5620d-224">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5620d-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="5620d-225">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="5620d-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="5620d-226">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-227">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5620d-227">**classlib**</span></span>

<span data-ttu-id="5620d-228">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5620d-229">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="5620d-230">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="5620d-231">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-232">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="5620d-232">**mstest, xunit**</span></span>

<span data-ttu-id="5620d-233">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5620d-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="5620d-234">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="5620d-235">**globaljson**</span></span>

<span data-ttu-id="5620d-236">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="5620d-237">**web**</span><span class="sxs-lookup"><span data-stu-id="5620d-237">**web**</span></span>

<span data-ttu-id="5620d-238">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="5620d-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5620d-239">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-240">**webapi**</span><span class="sxs-lookup"><span data-stu-id="5620d-240">**webapi**</span></span>

<span data-ttu-id="5620d-241">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="5620d-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5620d-242">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5620d-242">The possible values are:</span></span>

- <span data-ttu-id="5620d-243">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="5620d-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5620d-244">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5620d-245">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5620d-246">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5620d-247">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5620d-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5620d-248">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5620d-249">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="5620d-250">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5620d-251">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-252">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="5620d-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5620d-253">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5620d-254">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5620d-255">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5620d-256">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="5620d-257">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5620d-258">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="5620d-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5620d-259">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="5620d-260">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5620d-261">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5620d-262">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="5620d-263">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5620d-264">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="5620d-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5620d-265">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5620d-266">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="5620d-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5620d-267">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5620d-268">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-269">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-270">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="5620d-270">**mvc, razor**</span></span>

<span data-ttu-id="5620d-271">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="5620d-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="5620d-272">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5620d-272">The possible values are:</span></span>

- <span data-ttu-id="5620d-273">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="5620d-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="5620d-274">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="5620d-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="5620d-275">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="5620d-276">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="5620d-277">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="5620d-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="5620d-278">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="5620d-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="5620d-279">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5620d-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="5620d-280">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="5620d-281">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="5620d-282">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="5620d-283">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-284">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="5620d-285">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-286">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="5620d-287">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-288">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="5620d-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="5620d-289">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="5620d-290">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="5620d-291">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="5620d-292">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="5620d-293">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="5620d-294">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="5620d-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="5620d-295">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="5620d-296">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="5620d-297">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="5620d-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="5620d-298">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="5620d-299">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="5620d-300">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="5620d-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="5620d-301">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="5620d-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="5620d-302">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="5620d-303">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="5620d-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="5620d-304">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="5620d-305">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="5620d-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="5620d-306">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="5620d-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="5620d-307">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="5620d-308">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="5620d-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="5620d-309">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="5620d-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="5620d-310">**page**</span><span class="sxs-lookup"><span data-stu-id="5620d-310">**page**</span></span>

<span data-ttu-id="5620d-311">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="5620d-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5620d-312">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="5620d-313">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="5620d-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="5620d-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="5620d-314">**viewimports**</span></span>

<span data-ttu-id="5620d-315">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="5620d-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="5620d-316">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5620d-317">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5620d-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5620d-318">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="5620d-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="5620d-319">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5620d-320">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5620d-321">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5620d-322">**classlib**</span><span class="sxs-lookup"><span data-stu-id="5620d-322">**classlib**</span></span>

<span data-ttu-id="5620d-323">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5620d-324">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="5620d-325">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="5620d-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="5620d-326">**mvc**</span></span>

<span data-ttu-id="5620d-327">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="5620d-328">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="5620d-329">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="5620d-330">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="5620d-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="5620d-331">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="5620d-332">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-332">The default value is `None`.</span></span>

<span data-ttu-id="5620d-333">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5620d-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="5620d-334">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-334">Values: `true` or `false`.</span></span> <span data-ttu-id="5620d-335">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="5620d-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5620d-336">使用例</span><span class="sxs-lookup"><span data-stu-id="5620d-336">Examples</span></span>

<span data-ttu-id="5620d-337">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5620d-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#`

<span data-ttu-id="5620d-338">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core 2.0 SDK またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="5620d-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="5620d-339">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。 .NET Core 2.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="5620d-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="5620d-340">.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5620d-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="5620d-341">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5620d-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="5620d-342">ASP.NET Core のシングル ページ アプリケーション テンプレートのバージョン 2.0 をインストールします (コマンド オプションは .NET Core SDK 1.1 以降のバージョンでのみ使用できます):</span><span class="sxs-lookup"><span data-stu-id="5620d-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="5620d-343">関連項目</span><span class="sxs-lookup"><span data-stu-id="5620d-343">See also</span></span>

[<span data-ttu-id="5620d-344">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="5620d-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="5620d-345">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="5620d-345">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="5620d-346">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="5620d-346">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="5620d-347">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="5620d-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
