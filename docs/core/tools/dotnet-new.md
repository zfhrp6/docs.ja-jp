---
title: dotnet new コマンド - .NET Core CLI
description: dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ae24c4145cc67ca863c07e4d22af8a1c2c2dd732
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570464"
---
# <a name="dotnet-new"></a><span data-ttu-id="f4cf7-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f4cf7-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f4cf7-104">name</span><span class="sxs-lookup"><span data-stu-id="f4cf7-104">Name</span></span>

<span data-ttu-id="f4cf7-105">`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f4cf7-106">構文</span><span class="sxs-lookup"><span data-stu-id="f4cf7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f4cf7-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f4cf7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f4cf7-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f4cf7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f4cf7-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f4cf7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f4cf7-110">説明</span><span class="sxs-lookup"><span data-stu-id="f4cf7-110">Description</span></span>

<span data-ttu-id="f4cf7-111">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-111">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="f4cf7-112">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-112">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="f4cf7-113">引数</span><span class="sxs-lookup"><span data-stu-id="f4cf7-113">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="f4cf7-114">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-114">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="f4cf7-115">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-115">Each template might have specific options you can pass.</span></span> <span data-ttu-id="f4cf7-116">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-116">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f4cf7-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f4cf7-117">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="f4cf7-118">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-118">The command contains a default list of templates.</span></span> <span data-ttu-id="f4cf7-119">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-119">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f4cf7-120">次の表は、.NET Core SDK 2.1.300 にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-120">The following table shows the templates that come pre-installed with the .NET Core SDK 2.1.300.</span></span> <span data-ttu-id="f4cf7-121">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-121">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f4cf7-122">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="f4cf7-122">Template description</span></span>                          | <span data-ttu-id="f4cf7-123">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="f4cf7-123">Template name</span></span>   | <span data-ttu-id="f4cf7-124">言語</span><span class="sxs-lookup"><span data-stu-id="f4cf7-124">Languages</span></span>     |
|----------------------------------------------|-----------------|---------------|
| <span data-ttu-id="f4cf7-125">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f4cf7-125">Console application</span></span>                          | `console`       | <span data-ttu-id="f4cf7-126">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-126">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-127">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-127">Class library</span></span>                                | `classlib`      | <span data-ttu-id="f4cf7-128">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-128">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-129">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-129">Unit test project</span></span>                            | `mstest`        | <span data-ttu-id="f4cf7-130">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-130">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-131">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-131">xUnit test project</span></span>                           | `xunit`         | <span data-ttu-id="f4cf7-132">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-132">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-133">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-133">Razor page</span></span>                                   | `page`          | <span data-ttu-id="f4cf7-134">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-134">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-135">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f4cf7-135">MVC ViewImports</span></span>                              | `viewimports`   | <span data-ttu-id="f4cf7-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-136">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-137">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f4cf7-137">MVC ViewStart</span></span>                                | `viewstart`     | <span data-ttu-id="f4cf7-138">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-138">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-139">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="f4cf7-139">ASP.NET Core empty</span></span>                           | `web`           | <span data-ttu-id="f4cf7-140">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-140">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-141">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="f4cf7-141">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`           | <span data-ttu-id="f4cf7-142">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-142">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-143">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-143">ASP.NET Core Web App</span></span>                         | `razor`         | <span data-ttu-id="f4cf7-144">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-144">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-145">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-145">ASP.NET Core with Angular</span></span>                    | `angular`       | <span data-ttu-id="f4cf7-146">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-146">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-147">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-147">ASP.NET Core with React.js</span></span>                   | `react`         | <span data-ttu-id="f4cf7-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-148">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-149">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-149">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`    | <span data-ttu-id="f4cf7-150">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-150">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-151">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f4cf7-151">ASP.NET Core Web API</span></span>                         | `webapi`        | <span data-ttu-id="f4cf7-152">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-152">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-153">Razor クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-153">Razor class library</span></span>                          | `razorclasslib` | <span data-ttu-id="f4cf7-154">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-154">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-155">global.json file</span><span class="sxs-lookup"><span data-stu-id="f4cf7-155">global.json file</span></span>                             | `globaljson`    |               |
| <span data-ttu-id="f4cf7-156">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-156">NuGet config</span></span>                                 | `nugetconfig`   |               |
| <span data-ttu-id="f4cf7-157">Web 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-157">Web config</span></span>                                   | `webconfig`     |               |
| <span data-ttu-id="f4cf7-158">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="f4cf7-158">Solution file</span></span>                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f4cf7-159">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f4cf7-159">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="f4cf7-160">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-160">The command contains a default list of templates.</span></span> <span data-ttu-id="f4cf7-161">使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-161">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="f4cf7-162">次の表は、.NET Core SDK 2.0 にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-162">The following table shows the templates that come pre-installed with the .NET Core SDK 2.0.</span></span> <span data-ttu-id="f4cf7-163">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-163">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f4cf7-164">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="f4cf7-164">Template description</span></span>                          | <span data-ttu-id="f4cf7-165">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="f4cf7-165">Template name</span></span> | <span data-ttu-id="f4cf7-166">言語</span><span class="sxs-lookup"><span data-stu-id="f4cf7-166">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="f4cf7-167">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f4cf7-167">Console application</span></span>                          | `console`     | <span data-ttu-id="f4cf7-168">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-168">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-169">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-169">Class library</span></span>                                | `classlib`    | <span data-ttu-id="f4cf7-170">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-170">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-171">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-171">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="f4cf7-172">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-172">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-173">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-173">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="f4cf7-174">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="f4cf7-174">[C#], F#, VB</span></span>  |
| <span data-ttu-id="f4cf7-175">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="f4cf7-175">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="f4cf7-176">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-176">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-177">ASP.NET Core Web アプリ (モデル ビュー コントローラー)</span><span class="sxs-lookup"><span data-stu-id="f4cf7-177">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="f4cf7-178">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-178">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-179">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-179">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="f4cf7-180">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-180">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-181">Angular 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-181">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="f4cf7-182">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-182">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-183">React.js 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-183">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="f4cf7-184">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-184">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-185">React.js および Redux 付きの ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f4cf7-185">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="f4cf7-186">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-186">[C#]</span></span>          |
| <span data-ttu-id="f4cf7-187">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f4cf7-187">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="f4cf7-188">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-188">[C#], F#</span></span>      |
| <span data-ttu-id="f4cf7-189">global.json file</span><span class="sxs-lookup"><span data-stu-id="f4cf7-189">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="f4cf7-190">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-190">NuGet config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="f4cf7-191">Web 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-191">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="f4cf7-192">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="f4cf7-192">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="f4cf7-193">Razor ページ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-193">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="f4cf7-194">MVC ViewImports</span><span class="sxs-lookup"><span data-stu-id="f4cf7-194">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="f4cf7-195">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="f4cf7-195">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f4cf7-196">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f4cf7-196">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f4cf7-197">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-197">The command contains a default list of templates.</span></span> <span data-ttu-id="f4cf7-198">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-198">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="f4cf7-199">次の表は、.NET Core SDK 1.x にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-199">The following table shows the templates that come pre-installed with the .NET Core SDK 1.x.</span></span> <span data-ttu-id="f4cf7-200">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-200">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="f4cf7-201">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="f4cf7-201">Template description</span></span>  | <span data-ttu-id="f4cf7-202">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="f4cf7-202">Template name</span></span> | <span data-ttu-id="f4cf7-203">言語</span><span class="sxs-lookup"><span data-stu-id="f4cf7-203">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="f4cf7-204">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f4cf7-204">Console application</span></span>  | `console`     | <span data-ttu-id="f4cf7-205">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-205">[C#], F#</span></span>  |
| <span data-ttu-id="f4cf7-206">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-206">Class library</span></span>        | `classlib`    | <span data-ttu-id="f4cf7-207">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-207">[C#], F#</span></span>  |
| <span data-ttu-id="f4cf7-208">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-208">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="f4cf7-209">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-209">[C#], F#</span></span>  |
| <span data-ttu-id="f4cf7-210">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f4cf7-210">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="f4cf7-211">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-211">[C#], F#</span></span>  |
| <span data-ttu-id="f4cf7-212">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="f4cf7-212">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="f4cf7-213">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-213">[C#]</span></span>      |
| <span data-ttu-id="f4cf7-214">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-214">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="f4cf7-215">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="f4cf7-215">[C#], F#</span></span>  |
| <span data-ttu-id="f4cf7-216">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="f4cf7-216">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="f4cf7-217">[C#]</span><span class="sxs-lookup"><span data-stu-id="f4cf7-217">[C#]</span></span>      |
| <span data-ttu-id="f4cf7-218">NuGet 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-218">NuGet config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="f4cf7-219">Web 構成</span><span class="sxs-lookup"><span data-stu-id="f4cf7-219">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="f4cf7-220">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="f4cf7-220">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="f4cf7-221">オプション</span><span class="sxs-lookup"><span data-stu-id="f4cf7-221">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f4cf7-222">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f4cf7-222">.NET Core 2.1</span></span>](#tab/netcore21)

`--force`

<span data-ttu-id="f4cf7-223">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-223">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f4cf7-224">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-224">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f4cf7-225">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-225">Prints out help for the command.</span></span> <span data-ttu-id="f4cf7-226">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-226">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="f4cf7-227">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-227">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f4cf7-228">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-228">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f4cf7-229">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-229">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="f4cf7-230">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-230">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="f4cf7-231">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-231">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="f4cf7-232">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-232">Lists templates containing the specified name.</span></span> <span data-ttu-id="f4cf7-233">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-233">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f4cf7-234">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-234">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="f4cf7-235">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-235">The language of the template to create.</span></span> <span data-ttu-id="f4cf7-236">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-236">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f4cf7-237">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-237">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f4cf7-238">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-238">The name for the created output.</span></span> <span data-ttu-id="f4cf7-239">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-239">If no name is specified, the name of the current directory is used.</span></span>

`--nuget-source`

<span data-ttu-id="f4cf7-240">インストール中に使用する NuGet ソースを 1 つ指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-240">Specifies a NuGet source to use during install.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f4cf7-241">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-241">Location to place the generated output.</span></span> <span data-ttu-id="f4cf7-242">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-242">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="f4cf7-243">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-243">Filters templates based on available types.</span></span> <span data-ttu-id="f4cf7-244">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-244">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="f4cf7-245">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-245">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="f4cf7-246">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-246">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f4cf7-247">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-247">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f4cf7-248">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-248">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f4cf7-249">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f4cf7-249">.NET Core 2.0</span></span>](#tab/netcore20)

`--force`

<span data-ttu-id="f4cf7-250">既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-250">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="f4cf7-251">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-251">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f4cf7-252">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-252">Prints out help for the command.</span></span> <span data-ttu-id="f4cf7-253">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-253">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="f4cf7-254">指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-254">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="f4cf7-255">テンプレート パッケージのプレリリース版をインストールする場合は、`<package-name>::<package-version>` の形式でバージョンを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-255">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="f4cf7-256">既定では、`dotnet new` は、バージョンに対して \* を渡します。これは最後の安定したパッケージのバージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-256">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="f4cf7-257">「[使用例](#examples)」のセクションで、例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-257">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="f4cf7-258">カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-258">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="f4cf7-259">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-259">Lists templates containing the specified name.</span></span> <span data-ttu-id="f4cf7-260">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-260">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f4cf7-261">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-261">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="f4cf7-262">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-262">The language of the template to create.</span></span> <span data-ttu-id="f4cf7-263">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-263">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f4cf7-264">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-264">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f4cf7-265">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-265">The name for the created output.</span></span> <span data-ttu-id="f4cf7-266">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-266">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f4cf7-267">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-267">Location to place the generated output.</span></span> <span data-ttu-id="f4cf7-268">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-268">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="f4cf7-269">使用可能な種類に基づいて、テンプレートをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-269">Filters templates based on available types.</span></span> <span data-ttu-id="f4cf7-270">定義済みの値は、"project"、"item"、または "other" です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-270">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="f4cf7-271">指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-271">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="f4cf7-272">`PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-272">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="f4cf7-273">たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-273">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="f4cf7-274">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-274">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f4cf7-275">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f4cf7-275">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="f4cf7-276">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-276">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="f4cf7-277">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-277">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="f4cf7-278">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-278">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="f4cf7-279">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-279">Prints out help for the command.</span></span> <span data-ttu-id="f4cf7-280">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-280">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="f4cf7-281">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-281">Lists templates containing the specified name.</span></span> <span data-ttu-id="f4cf7-282">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-282">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="f4cf7-283">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-283">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="f4cf7-284">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-284">The language of the template to create.</span></span> <span data-ttu-id="f4cf7-285">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-285">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="f4cf7-286">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-286">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="f4cf7-287">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-287">The name for the created output.</span></span> <span data-ttu-id="f4cf7-288">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-288">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="f4cf7-289">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-289">Location to place the generated output.</span></span> <span data-ttu-id="f4cf7-290">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-290">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="f4cf7-291">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="f4cf7-291">Template options</span></span>

<span data-ttu-id="f4cf7-292">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-292">Each project template may have additional options available.</span></span> <span data-ttu-id="f4cf7-293">コア テンプレートの場合、次のオプションが追加されています。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-293">The core templates have the following additional options:</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f4cf7-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f4cf7-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="f4cf7-295">**console, angular, react, reactredux, razorclasslib**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-295">**console, angular, react, reactredux, razorclasslib**</span></span>

  <span data-ttu-id="f4cf7-296">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-296">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-297">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-297">**classlib**</span></span>

<span data-ttu-id="f4cf7-298">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-298">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f4cf7-299">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-299">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f4cf7-300">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-300">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="f4cf7-301">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-301">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-302">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-302">**mstest, xunit**</span></span>

<span data-ttu-id="f4cf7-303">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-303">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="f4cf7-304">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-304">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-305">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-305">**globaljson**</span></span>

<span data-ttu-id="f4cf7-306">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-306">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="f4cf7-307">**web**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-307">**web**</span></span>

<span data-ttu-id="f4cf7-308">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-308">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-309">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-309">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-310">**webapi**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-310">**webapi**</span></span>

<span data-ttu-id="f4cf7-311">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-311">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f4cf7-312">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-312">The possible values are:</span></span>

- <span data-ttu-id="f4cf7-313">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-313">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f4cf7-314">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-314">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f4cf7-315">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-315">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f4cf7-316">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-316">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f4cf7-317">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-317">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f4cf7-318">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-318">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-319">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-319">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f4cf7-320">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-320">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f4cf7-321">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-321">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-322">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-322">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f4cf7-323">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-323">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-324">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-324">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f4cf7-325">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-325">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f4cf7-326">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-326">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-327">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-327">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f4cf7-328">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-328">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f4cf7-329">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-329">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-330">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-330">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f4cf7-331">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-331">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f4cf7-332">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-332">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-333">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-333">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f4cf7-334">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-334">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f4cf7-335">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-335">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f4cf7-336">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-336">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-337">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-337">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f4cf7-338">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-338">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-339">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-339">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-340">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-340">**mvc, razor**</span></span>

<span data-ttu-id="f4cf7-341">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-341">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f4cf7-342">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-342">The possible values are:</span></span>

- <span data-ttu-id="f4cf7-343">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-343">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f4cf7-344">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-344">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="f4cf7-345">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-345">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f4cf7-346">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-346">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f4cf7-347">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-347">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="f4cf7-348">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-348">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f4cf7-349">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-349">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f4cf7-350">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-350">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-351">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-351">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f4cf7-352">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-352">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f4cf7-353">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-353">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-354">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-354">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="f4cf7-355">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-355">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-356">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-356">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="f4cf7-357">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-357">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-358">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-358">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f4cf7-359">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-359">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f4cf7-360">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-360">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f4cf7-361">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-361">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f4cf7-362">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-362">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f4cf7-363">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-363">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f4cf7-364">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-364">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f4cf7-365">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-365">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-366">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-366">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f4cf7-367">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-367">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f4cf7-368">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-368">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-369">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-369">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f4cf7-370">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-370">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f4cf7-371">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-371">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-372">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-372">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="f4cf7-373">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-373">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f4cf7-374">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-374">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f4cf7-375">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-375">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-376">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-376">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="f4cf7-377">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-377">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f4cf7-378">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-378">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-379">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-379">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-380">**page**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-380">**page**</span></span>

<span data-ttu-id="f4cf7-381">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-381">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f4cf7-382">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-382">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="f4cf7-383">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-383">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="f4cf7-384">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-384">**viewimports**</span></span>

<span data-ttu-id="f4cf7-385">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-385">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f4cf7-386">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-386">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f4cf7-387">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f4cf7-387">.NET Core 2.0</span></span>](#tab/netcore20)

<span data-ttu-id="f4cf7-388">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-388">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="f4cf7-389">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-389">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-390">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-390">**classlib**</span></span>

<span data-ttu-id="f4cf7-391">`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-391">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f4cf7-392">値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-392">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="f4cf7-393">既定値は `netstandard2.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-393">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="f4cf7-394">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-394">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-395">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-395">**mstest, xunit**</span></span>

<span data-ttu-id="f4cf7-396">`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-396">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="f4cf7-397">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-397">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-398">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-398">**globaljson**</span></span>

<span data-ttu-id="f4cf7-399">`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-399">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="f4cf7-400">**web**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-400">**web**</span></span>

<span data-ttu-id="f4cf7-401">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-401">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-402">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-402">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-403">**webapi**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-403">**webapi**</span></span>

<span data-ttu-id="f4cf7-404">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-404">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f4cf7-405">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-405">The possible values are:</span></span>

- <span data-ttu-id="f4cf7-406">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-406">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f4cf7-407">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f4cf7-408">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f4cf7-409">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-409">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f4cf7-410">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-410">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f4cf7-411">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-411">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-412">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-412">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f4cf7-413">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-413">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f4cf7-414">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-414">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-415">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-415">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f4cf7-416">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-416">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-417">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-417">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f4cf7-418">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-418">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f4cf7-419">`IndividualB2C` 認証または `SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-419">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-420">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-420">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f4cf7-421">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-421">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f4cf7-422">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-422">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-423">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-423">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f4cf7-424">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-424">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f4cf7-425">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-425">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-426">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-426">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f4cf7-427">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-427">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f4cf7-428">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-428">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f4cf7-429">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-429">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-430">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-430">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f4cf7-431">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-431">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-432">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-432">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-433">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-433">**mvc, razor**</span></span>

<span data-ttu-id="f4cf7-434">`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-434">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="f4cf7-435">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-435">The possible values are:</span></span>

- <span data-ttu-id="f4cf7-436">`None` - 認証は行われません (既定)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-436">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="f4cf7-437">`Individual` - 個別認証です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-437">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="f4cf7-438">`IndividualB2C` - Azure AD B2C での個別認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-438">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="f4cf7-439">`SingleOrg` - 単一のテナントに対する組織認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-439">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="f4cf7-440">`MultiOrg` - 複数のテナントに対する組織認証です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-440">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="f4cf7-441">`Windows` - Windows 認証。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-441">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="f4cf7-442">`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-442">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="f4cf7-443">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-443">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-444">既定値は `https://login.microsoftonline.com/tfp/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-444">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="f4cf7-445">`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-445">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="f4cf7-446">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-446">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-447">`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-447">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="f4cf7-448">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-448">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-449">`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-449">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="f4cf7-450">`IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-450">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-451">`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-451">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="f4cf7-452">`SingleOrg` 認証または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-452">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="f4cf7-453">既定値は `https://login.microsoftonline.com/` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-453">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="f4cf7-454">`--client-id <ID>` - このプロジェクトのクライアント ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-454">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="f4cf7-455">`IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-455">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="f4cf7-456">既定値は `11111111-1111-1111-11111111111111111` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-456">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="f4cf7-457">`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-457">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="f4cf7-458">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-458">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-459">既定値は `qualified.domain.name` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-459">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="f4cf7-460">`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-460">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="f4cf7-461">`SingleOrg` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-461">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="f4cf7-462">既定値は `22222222-2222-2222-2222-222222222222` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-462">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="f4cf7-463">`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-463">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="f4cf7-464">`SingleOrg` 認証または `IndividualB2C` 認証で使用します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-464">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="f4cf7-465">既定値は `/signin-oidc` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-465">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="f4cf7-466">`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-466">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="f4cf7-467">`SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-467">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="f4cf7-468">`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-468">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="f4cf7-469">`--use-browserlink` - プロジェクトに BrowserLink を含めます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-469">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="f4cf7-470">`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-470">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="f4cf7-471">`Individual` 認証または `IndividualB2C` 認証にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-471">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="f4cf7-472">`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-472">`--no-restore` - Doesn't execute an implicit restore during project creation.</span></span>

<span data-ttu-id="f4cf7-473">**page**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-473">**page**</span></span>

<span data-ttu-id="f4cf7-474">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-474">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f4cf7-475">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-475">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="f4cf7-476">`-np|--no-pagemodel` - PageModel なしでページを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-476">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="f4cf7-477">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-477">**viewimports**</span></span>

<span data-ttu-id="f4cf7-478">`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-478">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="f4cf7-479">既定値は `MyApp.Namespace` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-479">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f4cf7-480">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f4cf7-480">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="f4cf7-481">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-481">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="f4cf7-482">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-482">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f4cf7-483">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-483">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f4cf7-484">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-484">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f4cf7-485">**classlib**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-485">**classlib**</span></span>

<span data-ttu-id="f4cf7-486">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-486">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f4cf7-487">値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-487">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="f4cf7-488">既定値は `netstandard1.4` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-488">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="f4cf7-489">**mvc**</span><span class="sxs-lookup"><span data-stu-id="f4cf7-489">**mvc**</span></span>

<span data-ttu-id="f4cf7-490">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-490">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="f4cf7-491">値: `netcoreapp1.0` または `netcoreapp1.1` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-491">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="f4cf7-492">既定値は `netcoreapp1.0` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-492">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="f4cf7-493">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-493">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="f4cf7-494">値: `None` または `Individual` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-494">Values: `None` or `Individual`.</span></span> <span data-ttu-id="f4cf7-495">既定値は `None` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-495">The default value is `None`.</span></span>

<span data-ttu-id="f4cf7-496">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-496">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="f4cf7-497">値: `true` または `false` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-497">Values: `true` or `false`.</span></span> <span data-ttu-id="f4cf7-498">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-498">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f4cf7-499">使用例</span><span class="sxs-lookup"><span data-stu-id="f4cf7-499">Examples</span></span>

<span data-ttu-id="f4cf7-500">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-500">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="f4cf7-501">指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core SDK 2.0 またはそれ以降のバージョンでのみ使用可能)。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-501">Create a .NET Standard class library project in the specified directory (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="f4cf7-502">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。 .NET Core 2.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-502">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="f4cf7-503">.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-503">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="f4cf7-504">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-504">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="f4cf7-505">ASP.NET Core のシングル ページ アプリケーション テンプレートのバージョン 2.0 をインストールします (コマンド オプションは .NET Core SDK 1.1 以降のバージョンでのみ使用できます):</span><span class="sxs-lookup"><span data-stu-id="f4cf7-505">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

<span data-ttu-id="f4cf7-506">SDK バージョン 2.0.0 (.NET Core SDK 2.0 以降のバージョンでのみ使用できます) を設定している現在のディレクトリ内に *global.json* を作成します。</span><span class="sxs-lookup"><span data-stu-id="f4cf7-506">Create a *global.json* in the current directory setting the SDK version to 2.0.0 (available only with .NET Core SDK 2.0 or later versions):</span></span>

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="f4cf7-507">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4cf7-507">See also</span></span>

[<span data-ttu-id="f4cf7-508">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="f4cf7-508">Custom templates for dotnet new</span></span>](custom-templates.md)  
[<span data-ttu-id="f4cf7-509">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="f4cf7-509">Create a custom template for dotnet new</span></span>](~/docs/core/tutorials/create-custom-template.md)  
[<span data-ttu-id="f4cf7-510">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="f4cf7-510">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="f4cf7-511">dotnet new で使用できるテンプレート</span><span class="sxs-lookup"><span data-stu-id="f4cf7-511">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)