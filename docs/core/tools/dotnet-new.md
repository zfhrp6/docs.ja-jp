---
title: "dotnet-new コマンド - .NET Core CLI"
description: "dotnet-new コマンドは、現在のディレクトリに新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 56033295b2448b045d5a51dbd84d5429aed77451
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-new"></a><span data-ttu-id="8475a-104">dotnet-new</span><span class="sxs-lookup"><span data-stu-id="8475a-104">dotnet-new</span></span>

## <a name="name"></a><span data-ttu-id="8475a-105">名前</span><span class="sxs-lookup"><span data-stu-id="8475a-105">Name</span></span>

<span data-ttu-id="8475a-106">`dotnet-new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8475a-106">`dotnet-new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8475a-107">構文</span><span class="sxs-lookup"><span data-stu-id="8475a-107">Synopsis</span></span>

```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="8475a-108">説明</span><span class="sxs-lookup"><span data-stu-id="8475a-108">Description</span></span>

<span data-ttu-id="8475a-109">`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="8475a-109">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span> 

<span data-ttu-id="8475a-110">このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。</span><span class="sxs-lookup"><span data-stu-id="8475a-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="8475a-111">引数</span><span class="sxs-lookup"><span data-stu-id="8475a-111">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="8475a-112">コマンドが呼び出されたときにインスタンス化するテンプレート。</span><span class="sxs-lookup"><span data-stu-id="8475a-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="8475a-113">各テンプレートには、渡すことができるオプションが存在する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8475a-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="8475a-114">詳細については、[テンプレートのオプション](#template-options)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8475a-114">For more information, see [Template options](#template-options).</span></span>

<span data-ttu-id="8475a-115">このコマンドには、テンプレートの既定の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8475a-115">The command contains a default list of templates.</span></span> <span data-ttu-id="8475a-116">使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。</span><span class="sxs-lookup"><span data-stu-id="8475a-116">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="8475a-117">次の表は、SDK にプレインストールされているテンプレートの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8475a-117">The following table shows the templates that come pre-installed with the SDK.</span></span> <span data-ttu-id="8475a-118">テンプレートの既定の言語は、角かっこで示されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-118">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="8475a-119">テンプレートの説明</span><span class="sxs-lookup"><span data-stu-id="8475a-119">Template description</span></span>  | <span data-ttu-id="8475a-120">テンプレート名</span><span class="sxs-lookup"><span data-stu-id="8475a-120">Template name</span></span>  | <span data-ttu-id="8475a-121">言語</span><span class="sxs-lookup"><span data-stu-id="8475a-121">Languages</span></span> |
|----------------------|----------------|-----------|
| <span data-ttu-id="8475a-122">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="8475a-122">Console application</span></span>  | <span data-ttu-id="8475a-123">コンソール</span><span class="sxs-lookup"><span data-stu-id="8475a-123">console</span></span>        | <span data-ttu-id="8475a-124">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8475a-124">[C#], F#</span></span>  |
| <span data-ttu-id="8475a-125">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8475a-125">Class library</span></span>        | <span data-ttu-id="8475a-126">classlib</span><span class="sxs-lookup"><span data-stu-id="8475a-126">classlib</span></span>       | <span data-ttu-id="8475a-127">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8475a-127">[C#], F#</span></span>  |
| <span data-ttu-id="8475a-128">単体テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8475a-128">Unit test project</span></span>    | <span data-ttu-id="8475a-129">mstest</span><span class="sxs-lookup"><span data-stu-id="8475a-129">mstest</span></span>         | <span data-ttu-id="8475a-130">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8475a-130">[C#], F#</span></span>  |
| <span data-ttu-id="8475a-131">xUnit テスト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="8475a-131">xUnit test project</span></span>   | <span data-ttu-id="8475a-132">xunit</span><span class="sxs-lookup"><span data-stu-id="8475a-132">xunit</span></span>          | <span data-ttu-id="8475a-133">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8475a-133">[C#], F#</span></span>  |
| <span data-ttu-id="8475a-134">ASP.NET Core 空</span><span class="sxs-lookup"><span data-stu-id="8475a-134">ASP.NET Core empty</span></span>   | <span data-ttu-id="8475a-135">Web</span><span class="sxs-lookup"><span data-stu-id="8475a-135">web</span></span>            | <span data-ttu-id="8475a-136">[C#]</span><span class="sxs-lookup"><span data-stu-id="8475a-136">[C#]</span></span>      |
| <span data-ttu-id="8475a-137">ASP.NET Core Web アプリ</span><span class="sxs-lookup"><span data-stu-id="8475a-137">ASP.NET Core web app</span></span> | <span data-ttu-id="8475a-138">mvc</span><span class="sxs-lookup"><span data-stu-id="8475a-138">mvc</span></span>            | <span data-ttu-id="8475a-139">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="8475a-139">[C#], F#</span></span>  |
| <span data-ttu-id="8475a-140">ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="8475a-140">ASP.NET Core web api</span></span> | <span data-ttu-id="8475a-141">webapi</span><span class="sxs-lookup"><span data-stu-id="8475a-141">webapi</span></span>         | <span data-ttu-id="8475a-142">[C#]</span><span class="sxs-lookup"><span data-stu-id="8475a-142">[C#]</span></span>      |
| <span data-ttu-id="8475a-143">Nuget 構成</span><span class="sxs-lookup"><span data-stu-id="8475a-143">Nuget config</span></span>         | <span data-ttu-id="8475a-144">nugetconfig</span><span class="sxs-lookup"><span data-stu-id="8475a-144">nugetconfig</span></span>    |           |
| <span data-ttu-id="8475a-145">Web 構成</span><span class="sxs-lookup"><span data-stu-id="8475a-145">Web config</span></span>           | <span data-ttu-id="8475a-146">webconfig</span><span class="sxs-lookup"><span data-stu-id="8475a-146">webconfig</span></span>      |           |
| <span data-ttu-id="8475a-147">ソリューション ファイル</span><span class="sxs-lookup"><span data-stu-id="8475a-147">Solution file</span></span>        | <span data-ttu-id="8475a-148">sln</span><span class="sxs-lookup"><span data-stu-id="8475a-148">sln</span></span>            |           |

## <a name="options"></a><span data-ttu-id="8475a-149">オプション</span><span class="sxs-lookup"><span data-stu-id="8475a-149">Options</span></span>

`-h|--help`

<span data-ttu-id="8475a-150">コマンドのヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="8475a-150">Prints out help for the command.</span></span> <span data-ttu-id="8475a-151">`dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8475a-151">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="8475a-152">指定した名前を含むテンプレートを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8475a-152">Lists templates containing the specified name.</span></span> <span data-ttu-id="8475a-153">`dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-153">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="8475a-154">たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。</span><span class="sxs-lookup"><span data-stu-id="8475a-154">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="8475a-155">作成するテンプレートの言語。</span><span class="sxs-lookup"><span data-stu-id="8475a-155">The language of the template to create.</span></span> <span data-ttu-id="8475a-156">使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8475a-156">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="8475a-157">一部のテンプレートでは無効です。</span><span class="sxs-lookup"><span data-stu-id="8475a-157">Not valid for some templates.</span></span>

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="8475a-158">作成される出力の名前です。</span><span class="sxs-lookup"><span data-stu-id="8475a-158">The name for the created output.</span></span> <span data-ttu-id="8475a-159">名前が指定されていない場合、現在のディレクトリの名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-159">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="8475a-160">生成された出力を配置する場所。</span><span class="sxs-lookup"><span data-stu-id="8475a-160">Location to place the generated output.</span></span> <span data-ttu-id="8475a-161">既定値は、現在のディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="8475a-161">The default is the current directory.</span></span>

`-all|--show-all`

<span data-ttu-id="8475a-162">`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-162">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="8475a-163">`dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-163">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="8475a-164">これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="8475a-164">This is required when the output directory already contains a project.</span></span>

## <a name="template-options"></a><span data-ttu-id="8475a-165">テンプレート オプション</span><span class="sxs-lookup"><span data-stu-id="8475a-165">Template options</span></span>

<span data-ttu-id="8475a-166">プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8475a-166">Each project template may have additional options available.</span></span> <span data-ttu-id="8475a-167">コア テンプレートの場合、次のオプションが与えられています。</span><span class="sxs-lookup"><span data-stu-id="8475a-167">The core templates have the following options:</span></span>

<span data-ttu-id="8475a-168">**console、xunit、mstest、web、webapi**</span><span class="sxs-lookup"><span data-stu-id="8475a-168">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="8475a-169">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8475a-169">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8475a-170">値: `netcoreapp1.0` または `netcoreapp1.1` (既定値: `netcoreapp1.0`)</span><span class="sxs-lookup"><span data-stu-id="8475a-170">Values: `netcoreapp1.0` or `netcoreapp1.1` (Default: `netcoreapp1.0`)</span></span>

<span data-ttu-id="8475a-171">**mvc**</span><span class="sxs-lookup"><span data-stu-id="8475a-171">**mvc**</span></span>

<span data-ttu-id="8475a-172">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8475a-172">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8475a-173">値: `netcoreapp1.0` または `netcoreapp1.1` (`Default: netcoreapp1.0`)</span><span class="sxs-lookup"><span data-stu-id="8475a-173">Values: `netcoreapp1.0` or `netcoreapp1.1` (`Default: netcoreapp1.0`)</span></span>

<span data-ttu-id="8475a-174">`-au|--auth` - 使う認証の種類。</span><span class="sxs-lookup"><span data-stu-id="8475a-174">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="8475a-175">値: `None` または `Individual` (既定値: `None`)</span><span class="sxs-lookup"><span data-stu-id="8475a-175">Values: `None` or `Individual` (Default: `None`)</span></span>

<span data-ttu-id="8475a-176">`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8475a-176">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="8475a-177">値: `true` または `false` (既定値: `false`)</span><span class="sxs-lookup"><span data-stu-id="8475a-177">Values: `true` or `false` (Default: `false`)</span></span>

<span data-ttu-id="8475a-178">**classlib**</span><span class="sxs-lookup"><span data-stu-id="8475a-178">**classlib**</span></span>

<span data-ttu-id="8475a-179">`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="8475a-179">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="8475a-180">値: `netcoreapp1.0`、`netcoreapp1.1`、`netstandard1.0` から `netstandard1.6` (既定値: `netstandard1.4`)</span><span class="sxs-lookup"><span data-stu-id="8475a-180">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6` (Default: `netstandard1.4`)</span></span>

## <a name="examples"></a><span data-ttu-id="8475a-181">例</span><span class="sxs-lookup"><span data-stu-id="8475a-181">Examples</span></span>

<span data-ttu-id="8475a-182">現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8475a-182">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang f#` 
   
<span data-ttu-id="8475a-183">現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。.NET Core 1.0 を対象にする認証はありません。</span><span class="sxs-lookup"><span data-stu-id="8475a-183">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 1.0:</span></span>  

`dotnet new mvc -au None -f netcoreapp1.0`
 
<span data-ttu-id="8475a-184">.NET Core 1.1 を対象にする新しい xUnit アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8475a-184">Create a new xUnit application targeting .NET Core 1.1:</span></span>

`dotnet new xunit --framework netcoreapp1.1`

<span data-ttu-id="8475a-185">MVC に利用できるすべてのテンプレートを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8475a-185">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

