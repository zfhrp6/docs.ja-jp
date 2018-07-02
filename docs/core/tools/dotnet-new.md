---
title: dotnet new コマンド - .NET Core CLI
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
author: mairaw
ms.author: mairaw
ms.date: 06/12/2018
ms.openlocfilehash: f0ef91361dfbc2c2ba5532fbd607786289e98c69
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207783"
---
# <a name="dotnet-new"></a><span data-ttu-id="fcc1a-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="fcc1a-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fcc1a-104">name</span><span class="sxs-lookup"><span data-stu-id="fcc1a-104">Name</span></span>

<span data-ttu-id="fcc1a-105">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fcc1a-106">構文</span><span class="sxs-lookup"><span data-stu-id="fcc1a-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fcc1a-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fcc1a-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fcc1a-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fcc1a-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fcc1a-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fcc1a-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="fcc1a-110">説明</span><span class="sxs-lookup"><span data-stu-id="fcc1a-110">Description</span></span>

<span data-ttu-id="fcc1a-111">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="fcc1a-112">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="fcc1a-113">引数</span><span class="sxs-lookup"><span data-stu-id="fcc1a-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="fcc1a-114">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="fcc1a-115">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="fcc1a-116">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fcc1a-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fcc1a-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fcc1a-118">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-118">The command contains a default list of templates.</span></span> <span data-ttu-id="fcc1a-119">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="fcc1a-120">次の表は、.NET Core SDK 2.1.300 にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="fcc1a-121">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fcc1a-122">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="fcc1a-122">Template description</span></span>                          | <span data-ttu-id="fcc1a-123">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="fcc1a-123">Template name</span></span>   | <span data-ttu-id="fcc1a-124">言語</span><span class="sxs-lookup"><span data-stu-id="fcc1a-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="fcc1a-125">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fcc1a-125">Console application</span></span>                          | `console`       | <span data-ttu-id="fcc1a-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-127">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="fcc1a-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-129">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="fcc1a-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-131">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="fcc1a-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-133">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="fcc1a-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-134">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="fcc1a-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="fcc1a-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-136">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="fcc1a-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="fcc1a-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-138">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-139">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="fcc1a-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="fcc1a-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-140">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-141">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="fcc1a-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="fcc1a-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-142">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-143">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="fcc1a-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-144">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-145">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="fcc1a-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-146">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-147">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="fcc1a-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-148">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-149">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="fcc1a-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-150">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="fcc1a-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="fcc1a-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-152">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-153">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="fcc1a-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-154">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-155">global.json file</span><span class="sxs-lookup"><span data-stu-id="fcc1a-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="fcc1a-156">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="fcc1a-157">Web 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="fcc1a-158">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="fcc1a-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fcc1a-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fcc1a-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="fcc1a-160">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-160">The command contains a default list of templates.</span></span> <span data-ttu-id="fcc1a-161">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="fcc1a-162">次の表は、.NET Core SDK 2.0 にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="fcc1a-163">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fcc1a-164">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="fcc1a-164">Template description</span></span>                          | <span data-ttu-id="fcc1a-165">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="fcc1a-165">Template name</span></span> | <span data-ttu-id="fcc1a-166">言語</span><span class="sxs-lookup"><span data-stu-id="fcc1a-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="fcc1a-167">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fcc1a-167">Console application</span></span>                          | `console`     | <span data-ttu-id="fcc1a-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-169">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="fcc1a-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-171">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="fcc1a-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-173">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="fcc1a-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="fcc1a-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="fcc1a-175">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="fcc1a-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="fcc1a-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-176">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-177">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="fcc1a-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="fcc1a-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-178">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-179">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="fcc1a-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-180">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-181">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="fcc1a-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-182">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-183">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="fcc1a-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-184">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-185">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcc1a-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="fcc1a-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-186">[C#]</span></span>          |
| <span data-ttu-id="fcc1a-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="fcc1a-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="fcc1a-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-188">[C#], F#</span></span>      |
| <span data-ttu-id="fcc1a-189">global.json file</span><span class="sxs-lookup"><span data-stu-id="fcc1a-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="fcc1a-190">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="fcc1a-191">Web 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="fcc1a-192">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="fcc1a-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="fcc1a-193">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="fcc1a-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="fcc1a-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="fcc1a-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="fcc1a-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fcc1a-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fcc1a-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fcc1a-197">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-197">The command contains a default list of templates.</span></span> <span data-ttu-id="fcc1a-198">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="fcc1a-199">次の表は、.NET Core SDK 1.x にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="fcc1a-200">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="fcc1a-201">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="fcc1a-201">Template description</span></span>  | <span data-ttu-id="fcc1a-202">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="fcc1a-202">Template name</span></span> | <span data-ttu-id="fcc1a-203">言語</span><span class="sxs-lookup"><span data-stu-id="fcc1a-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="fcc1a-204">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fcc1a-204">Console application</span></span>  | `console`     | <span data-ttu-id="fcc1a-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-205">[C#], F#</span></span>  |
| <span data-ttu-id="fcc1a-206">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="fcc1a-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-207">[C#], F#</span></span>  |
| <span data-ttu-id="fcc1a-208">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="fcc1a-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-209">[C#], F#</span></span>  |
| <span data-ttu-id="fcc1a-210">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="fcc1a-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="fcc1a-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-211">[C#], F#</span></span>  |
| <span data-ttu-id="fcc1a-212">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="fcc1a-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="fcc1a-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-213">[C#]</span></span>      |
| <span data-ttu-id="fcc1a-214">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="fcc1a-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="fcc1a-215">[C#], F#</span></span>  |
| <span data-ttu-id="fcc1a-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="fcc1a-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="fcc1a-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="fcc1a-217">[C#]</span></span>      |
| <span data-ttu-id="fcc1a-218">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="fcc1a-219">Web 構成</span><span class="sxs-lookup"><span data-stu-id="fcc1a-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="fcc1a-220">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="fcc1a-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="fcc1a-221">オプション</span><span class="sxs-lookup"><span data-stu-id="fcc1a-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fcc1a-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fcc1a-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="fcc1a-223">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="fcc1a-224">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fcc1a-225">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-225">Prints out help for the command.</span></span> <span data-ttu-id="fcc1a-226">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="fcc1a-227">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="fcc1a-228">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="fcc1a-229">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="fcc1a-230">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="fcc1a-231">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="fcc1a-232">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="fcc1a-233">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fcc1a-234">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="fcc1a-235">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-235">The language of the template to create.</span></span> <span data-ttu-id="fcc1a-236">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fcc1a-237">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-237">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc1a-238">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-238">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="fcc1a-239">そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-239">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fcc1a-240">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-240">The name for the created output.</span></span> <span data-ttu-id="fcc1a-241">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-241">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="fcc1a-242">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-242">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fcc1a-243">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-243">Location to place the generated output.</span></span> <span data-ttu-id="fcc1a-244">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-244">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="fcc1a-245">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-245">Filters templates based on available types.</span></span> <span data-ttu-id="fcc1a-246">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-246">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="fcc1a-247">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-247">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc1a-248">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-248">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="fcc1a-249">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-249">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="fcc1a-250">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-250">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fcc1a-251">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fcc1a-251">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="fcc1a-252">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-252">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="fcc1a-253">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-253">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fcc1a-254">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-254">Prints out help for the command.</span></span> <span data-ttu-id="fcc1a-255">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-255">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="fcc1a-256">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-256">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="fcc1a-257">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-257">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="fcc1a-258">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-258">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="fcc1a-259">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-259">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="fcc1a-260">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-260">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="fcc1a-261">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-261">Lists templates containing the specified name.</span></span> <span data-ttu-id="fcc1a-262">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-262">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fcc1a-263">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-263">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="fcc1a-264">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-264">The language of the template to create.</span></span> <span data-ttu-id="fcc1a-265">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-265">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fcc1a-266">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-266">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc1a-267">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-267">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="fcc1a-268">そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-268">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fcc1a-269">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-269">The name for the created output.</span></span> <span data-ttu-id="fcc1a-270">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-270">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fcc1a-271">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-271">Location to place the generated output.</span></span> <span data-ttu-id="fcc1a-272">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-272">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="fcc1a-273">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-273">Filters templates based on available types.</span></span> <span data-ttu-id="fcc1a-274">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-274">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="fcc1a-275">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-275">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc1a-276">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-276">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="fcc1a-277">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-277">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="fcc1a-278">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-278">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fcc1a-279">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fcc1a-279">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="fcc1a-280">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-280">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="fcc1a-281">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-281">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="fcc1a-282">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-282">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="fcc1a-283">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-283">Prints out help for the command.</span></span> <span data-ttu-id="fcc1a-284">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-284">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="fcc1a-285">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-285">Lists templates containing the specified name.</span></span> <span data-ttu-id="fcc1a-286">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-286">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="fcc1a-287">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-287">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="fcc1a-288">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-288">The language of the template to create.</span></span> <span data-ttu-id="fcc1a-289">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-289">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="fcc1a-290">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-290">Not valid for some templates.</span></span>

> [!NOTE]
> <span data-ttu-id="fcc1a-291">一部のシェルは `#` を特殊文字として解釈します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-291">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="fcc1a-292">そのような場合は、`dotnet new console -lang "F#"` などの言語パラメーター値を囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-292">In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="fcc1a-293">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-293">The name for the created output.</span></span> <span data-ttu-id="fcc1a-294">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-294">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fcc1a-295">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-295">Location to place the generated output.</span></span> <span data-ttu-id="fcc1a-296">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-296">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="fcc1a-297">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="fcc1a-297">Template options</span></span>

<span data-ttu-id="fcc1a-298">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-298">Each project template may have additional options available.</span></span> <span data-ttu-id="fcc1a-299">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-299">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="fcc1a-300">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fcc1a-300">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="fcc1a-301">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-301">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="fcc1a-302">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-302">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-303">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-303">**classlib**</span></span>

<span data-ttu-id="fcc1a-304">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-304">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fcc1a-305">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-305">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="fcc1a-306">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-306">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="fcc1a-307">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-307">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-308">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-308">**mstest, xunit**</span></span>

<span data-ttu-id="fcc1a-309">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-309">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="fcc1a-310">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-310">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-311">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-311">**globaljson**</span></span>

<span data-ttu-id="fcc1a-312">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-312">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="fcc1a-313">**web**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-313">**web**</span></span>

<span data-ttu-id="fcc1a-314">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-314">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-315">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-315">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-316">**webapi**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-316">**webapi**</span></span>

<span data-ttu-id="fcc1a-317">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-317">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fcc1a-318">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-318">The possible values are:</span></span>

- <span data-ttu-id="fcc1a-319">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-319">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fcc1a-320">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-320">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fcc1a-321">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-321">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fcc1a-322">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-322">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fcc1a-323">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-323">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fcc1a-324">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-324">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-325">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-325">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fcc1a-326">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-326">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fcc1a-327">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-327">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-328">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-328">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fcc1a-329">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-329">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-330">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-330">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fcc1a-331">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-331">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fcc1a-332">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-332">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-333">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-333">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fcc1a-334">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-334">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fcc1a-335">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-335">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-336">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-336">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fcc1a-337">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-337">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fcc1a-338">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-338">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-339">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-339">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fcc1a-340">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-340">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fcc1a-341">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-341">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fcc1a-342">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-342">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-343">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-343">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fcc1a-344">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-344">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-345">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-345">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-346">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-346">**mvc, razor**</span></span>

<span data-ttu-id="fcc1a-347">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-347">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fcc1a-348">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-348">The possible values are:</span></span>

- <span data-ttu-id="fcc1a-349">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-349">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fcc1a-350">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-350">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="fcc1a-351">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-351">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fcc1a-352">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-352">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fcc1a-353">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-353">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="fcc1a-354">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-354">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fcc1a-355">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-355">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fcc1a-356">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-356">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-357">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-357">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fcc1a-358">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-358">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fcc1a-359">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-359">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-360">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-360">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="fcc1a-361">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-361">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-362">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-362">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="fcc1a-363">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-363">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-364">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-364">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fcc1a-365">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-365">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="fcc1a-366">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-366">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fcc1a-367">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-367">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fcc1a-368">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-368">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="fcc1a-369">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-369">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fcc1a-370">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-370">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fcc1a-371">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-372">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-372">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fcc1a-373">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-373">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fcc1a-374">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-374">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-375">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-375">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fcc1a-376">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-376">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="fcc1a-377">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-377">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-378">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-378">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="fcc1a-379">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-379">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fcc1a-380">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-380">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fcc1a-381">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-381">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-382">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-382">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="fcc1a-383">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-383">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fcc1a-384">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-384">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-385">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-385">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-386">**page**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-386">**page**</span></span>

<span data-ttu-id="fcc1a-387">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-387">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fcc1a-388">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-388">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="fcc1a-389">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-389">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="fcc1a-390">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-390">**viewimports**</span></span>

<span data-ttu-id="fcc1a-391">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-391">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fcc1a-392">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-392">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="fcc1a-393">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="fcc1a-393">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="fcc1a-394">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-394">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="fcc1a-395">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-395">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-396">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-396">**classlib**</span></span>

<span data-ttu-id="fcc1a-397">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-397">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fcc1a-398">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-398">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="fcc1a-399">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-399">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="fcc1a-400">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-400">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-401">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-401">**mstest, xunit**</span></span>

<span data-ttu-id="fcc1a-402">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-402">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="fcc1a-403">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-403">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-404">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-404">**globaljson**</span></span>

<span data-ttu-id="fcc1a-405">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-405">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="fcc1a-406">**web**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-406">**web**</span></span>

<span data-ttu-id="fcc1a-407">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-407">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-408">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-408">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-409">**webapi**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-409">**webapi**</span></span>

<span data-ttu-id="fcc1a-410">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-410">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fcc1a-411">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-411">The possible values are:</span></span>

- <span data-ttu-id="fcc1a-412">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-412">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fcc1a-413">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-413">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fcc1a-414">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-414">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fcc1a-415">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-415">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fcc1a-416">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-416">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fcc1a-417">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-417">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-418">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-418">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fcc1a-419">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-419">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fcc1a-420">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-420">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-421">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-421">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fcc1a-422">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-422">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-423">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-423">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fcc1a-424">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-424">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fcc1a-425">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-425">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-426">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-426">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fcc1a-427">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-427">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fcc1a-428">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-428">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-429">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-429">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fcc1a-430">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-430">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fcc1a-431">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-431">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-432">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-432">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fcc1a-433">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-433">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fcc1a-434">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-434">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fcc1a-435">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-435">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-436">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-436">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fcc1a-437">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-437">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-438">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-438">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-439">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-439">**mvc, razor**</span></span>

<span data-ttu-id="fcc1a-440">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-440">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="fcc1a-441">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-441">The possible values are:</span></span>

- <span data-ttu-id="fcc1a-442">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-442">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="fcc1a-443">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-443">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="fcc1a-444">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-444">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="fcc1a-445">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-445">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="fcc1a-446">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-446">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="fcc1a-447">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-447">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="fcc1a-448">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-448">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="fcc1a-449">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-449">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-450">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-450">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="fcc1a-451">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-451">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="fcc1a-452">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-452">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-453">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-453">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="fcc1a-454">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-454">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-455">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-455">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="fcc1a-456">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-456">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-457">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-457">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="fcc1a-458">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-458">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="fcc1a-459">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-459">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="fcc1a-460">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-460">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="fcc1a-461">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-461">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="fcc1a-462">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-462">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="fcc1a-463">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-463">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="fcc1a-464">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-465">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-465">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="fcc1a-466">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-466">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="fcc1a-467">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-467">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="fcc1a-468">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-468">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="fcc1a-469">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-469">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="fcc1a-470">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-470">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="fcc1a-471">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-471">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="fcc1a-472">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-472">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="fcc1a-473">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-473">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="fcc1a-474">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-474">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="fcc1a-475">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-475">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="fcc1a-476">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-476">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="fcc1a-477">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-477">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="fcc1a-478">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-478">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="fcc1a-479">**page**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-479">**page**</span></span>

<span data-ttu-id="fcc1a-480">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-480">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fcc1a-481">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-481">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="fcc1a-482">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-482">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="fcc1a-483">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-483">**viewimports**</span></span>

<span data-ttu-id="fcc1a-484">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-484">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="fcc1a-485">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-485">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fcc1a-486">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="fcc1a-486">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="fcc1a-487">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-487">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="fcc1a-488">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-488">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fcc1a-489">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-489">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fcc1a-490">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-490">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fcc1a-491">**classlib**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-491">**classlib**</span></span>

<span data-ttu-id="fcc1a-492">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-492">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fcc1a-493">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-493">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="fcc1a-494">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-494">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="fcc1a-495">**mvc**</span><span class="sxs-lookup"><span data-stu-id="fcc1a-495">**mvc**</span></span>

<span data-ttu-id="fcc1a-496">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-496">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="fcc1a-497">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-497">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="fcc1a-498">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-498">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="fcc1a-499">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-499">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="fcc1a-500">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-500">Values: `None` or `Individual`.</span></span> <span data-ttu-id="fcc1a-501">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-501">The default value is `None`.</span></span>

<span data-ttu-id="fcc1a-502">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-502">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="fcc1a-503">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-503">Values: `true` or `false`.</span></span> <span data-ttu-id="fcc1a-504">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-504">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="fcc1a-505">使用例</span><span class="sxs-lookup"><span data-stu-id="fcc1a-505">Examples</span></span>

<span data-ttu-id="fcc1a-506">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-506">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="fcc1a-507">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core SDK 2.0 またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-507">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="fcc1a-508">認証なしで、現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-508">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication:</span></span>

`dotnet new mvc -au None`

<span data-ttu-id="fcc1a-509">新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-509">Create a new xUnit application:</span></span>

`dotnet new xunit`

<span data-ttu-id="fcc1a-510">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-510">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="fcc1a-511">ASP.NET Core のシングル ページ アプリケーション テンプレートのバージョン 2.0 をインストールします (コマンド オプションは .NET Core SDK 1.1 以降のバージョンでのみ使用できます):</span><span class="sxs-lookup"><span data-stu-id="fcc1a-511">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="fcc1a-512">SDK バージョン 2.0.0 (.NET Core SDK 2.0 以降のバージョンでのみ使用できます) を設定している現在のディレクトリ内に *global.json* を作成します。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-512">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="fcc1a-513">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcc1a-513">See also</span></span>

[<span data-ttu-id="fcc1a-514">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="fcc1a-514">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="fcc1a-515">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="fcc1a-515">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="fcc1a-516">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="fcc1a-516">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="fcc1a-517">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="fcc1a-517">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
