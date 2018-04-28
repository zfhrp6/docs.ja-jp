---
title: dotnet new のカスタム テンプレート
description: あらゆる種類の .NET プロジェクトまたはファイルのカスタム テンプレートについて説明します。
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 1915c2609391d0aa1ff32ea9ebb011cf0f925aa8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="07428-103">dotnet new のカスタム テンプレート</span><span class="sxs-lookup"><span data-stu-id="07428-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="07428-104">[.NET Core SDK](https://www.microsoft.com/net/download/core) には、[`dotnet new` コマンド](dotnet-new.md)で使用するさまざまなテンプレートが既にインストールされています。</span><span class="sxs-lookup"><span data-stu-id="07428-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates pre-installed to use with the [`dotnet new` command](dotnet-new.md).</span></span> <span data-ttu-id="07428-105">.NET Core 2.0 以降から、アプリ、サービス、ツール、クラス ライブラリなど、あらゆる種類のプロジェクトを対象に独自のテンプレートを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="07428-105">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="07428-106">構成ファイルなど、1 つまたは複数の独立ファイルを出力するテンプレートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="07428-106">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="07428-107">カスタム テンプレートは、あらゆる NuGet フィードで NuGet パッケージからインストールできます。NuGet *nupkg* ファイルを直接参照するか、テンプレートが含まれるファイル システム ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="07428-107">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="07428-108">テンプレート エンジンの機能を利用すると、値を置換したり、ファイルやファイルの領域を追加したり、除外したり、テンプレートの利用時に独自の処理操作を実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="07428-108">The template engine offers features that allow you to replace values, include and exclude files and regions of files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="07428-109">テンプレート エンジンはオープン ソースです。オンライン コード リポジトリは GitHub の [dotnet/templating](https://github.com/dotnet/templating/) にあります。</span><span class="sxs-lookup"><span data-stu-id="07428-109">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="07428-110">テンプレートのサンプルが必要であれば、[dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) リポジトリをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07428-110">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="07428-111">GitHub の「[Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)」 (dotnet new で利用できるテンプレート) には、サードパーティのテンプレートなど、テンプレートが他にもあります。</span><span class="sxs-lookup"><span data-stu-id="07428-111">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="07428-112">カスタム テンプレートの作成と利用の詳細については、「[dotnet new の独自のテンプレートを作成する方法](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)」と「[dotnet/templating GitHub リポジトリ Wiki](https://github.com/dotnet/templating/wiki)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07428-112">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="07428-113">チュートリアルでテンプレートを作成するには、「[dotnet new のカスタム テンプレートを作成する](~/docs/core/tutorials/create-custom-template.md)」チュートリアルをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="07428-113">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

## <a name="configuration"></a><span data-ttu-id="07428-114">構成</span><span class="sxs-lookup"><span data-stu-id="07428-114">Configuration</span></span>

<span data-ttu-id="07428-115">テンプレートは次の要素から構成されます。</span><span class="sxs-lookup"><span data-stu-id="07428-115">A template is composed of the following components:</span></span>

- <span data-ttu-id="07428-116">ソース ファイルとフォルダー</span><span class="sxs-lookup"><span data-stu-id="07428-116">Source files and folders</span></span>
- <span data-ttu-id="07428-117">構成ファイル (*template.json*)</span><span class="sxs-lookup"><span data-stu-id="07428-117">A configuration file (*template.json*)</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="07428-118">ソース ファイルとフォルダー</span><span class="sxs-lookup"><span data-stu-id="07428-118">Source files and folders</span></span>

<span data-ttu-id="07428-119">ソース ファイルとフォルダーには、`dotnet new <TEMPLATE>` コマンドの実行時にテンプレート エンジンで使用されるあらゆるファイルとフォルダーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="07428-119">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is executed.</span></span> <span data-ttu-id="07428-120">テンプレート エンジンは、ソース コードとして*実行可能なプロジェクト*を利用し、プロジェクトを生成するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="07428-120">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="07428-121">これにはいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="07428-121">This has several benefits:</span></span>

- <span data-ttu-id="07428-122">テンプレート エンジンでは、プロジェクトのソース コードに特別なトークンを挿入することを必要としません。</span><span class="sxs-lookup"><span data-stu-id="07428-122">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="07428-123">コード ファイルは特別なファイルではなく、テンプレート エンジンで利用するために変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="07428-123">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="07428-124">そのため、プロジェクトの利用時に通常利用しているツールでテンプレート コンテンツに対応できます。</span><span class="sxs-lookup"><span data-stu-id="07428-124">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="07428-125">他のプロジェクトの場合と同じように、テンプレート プロジェクトをビルドし、実行し、デバッグします。</span><span class="sxs-lookup"><span data-stu-id="07428-125">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="07428-126">*template.json* 構成ファイルをプロジェクトに追加するだけで、既存のプロジェクトからテンプレートを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="07428-126">You can quickly create a template from an existing project just by adding a *template.json* configuration file to the project.</span></span>

<span data-ttu-id="07428-127">テンプレートに保存されるファイルやフォルダーは、.NET Core や .NET Framework ソリューションなど、正式な種類の .NET プロジェクトに限定されません。</span><span class="sxs-lookup"><span data-stu-id="07428-127">Files and folders stored in the template aren't limited to formal .NET project types, such as .NET Core or .NET Framework solutions.</span></span> <span data-ttu-id="07428-128">ソース ファイルとフォルダーは、テンプレートの利用時に作成するあらゆるコンテンツで構成できます。構成ファイルやソリューション ファイルなど、テンプレート エンジンでファイルが 1 つだけ生成される場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="07428-128">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file for its output, such as a configuration file or a solution file.</span></span> <span data-ttu-id="07428-129">たとえば、*web.config* ソース ファイルを含み、テンプレートの利用時、プロジェクトに対して、変更された *web.config* ファイルを作成するテンプレートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="07428-129">For example, you can create a template that contains a *web.config* source file and creates a modified *web.config* file for projects where the template is used.</span></span> <span data-ttu-id="07428-130">ソース ファイルの変更は、*template.json* 構成ファイルのロジックと設定、およびユーザーが `dotnet new <TEMPLATE>` コマンドにオプションとして渡した値に基づきます。</span><span class="sxs-lookup"><span data-stu-id="07428-130">The modifications to source files are based on logic and settings you've provided in the *template.json* configuration file along with values provided by the user passed as options to the `dotnet new <TEMPLATE>` command.</span></span>

### <a name="templatejson"></a><span data-ttu-id="07428-131">template.json</span><span class="sxs-lookup"><span data-stu-id="07428-131">template.json</span></span>

<span data-ttu-id="07428-132">*template.json* ファイルは、テンプレートのルート ディレクトリの *.template.config* フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="07428-132">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="07428-133">このファイルは、テンプレート エンジンに構成情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="07428-133">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="07428-134">最小構成には、次の表に示すメンバーが必要です。この最小構成があれば、実際に機能するテンプレートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="07428-134">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="07428-135">メンバー</span><span class="sxs-lookup"><span data-stu-id="07428-135">Member</span></span>            | <span data-ttu-id="07428-136">型</span><span class="sxs-lookup"><span data-stu-id="07428-136">Type</span></span>          | <span data-ttu-id="07428-137">説明</span><span class="sxs-lookup"><span data-stu-id="07428-137">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="07428-138">URI</span><span class="sxs-lookup"><span data-stu-id="07428-138">URI</span></span>           | <span data-ttu-id="07428-139">*template.json* ファイルの JSON スキーマ。</span><span class="sxs-lookup"><span data-stu-id="07428-139">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="07428-140">エディターが JSON スキーマ対応であれば、スキーマの指定時、JSON 編集機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="07428-140">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="07428-141">たとえば、[Visual Studio Code](https://code.visualstudio.com/) の場合、IntelliSense を有効にするためにこのメンバーが必要になります。</span><span class="sxs-lookup"><span data-stu-id="07428-141">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="07428-142">値として `http://json.schemastore.org/template` を使用します。</span><span class="sxs-lookup"><span data-stu-id="07428-142">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="07428-143">string</span><span class="sxs-lookup"><span data-stu-id="07428-143">string</span></span>        | <span data-ttu-id="07428-144">テンプレートの作成者。</span><span class="sxs-lookup"><span data-stu-id="07428-144">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="07428-145">array(string)</span><span class="sxs-lookup"><span data-stu-id="07428-145">array(string)</span></span> | <span data-ttu-id="07428-146">テンプレートのゼロ以上の特性。ユーザーがこれを利用し、テンプレートを探すことがあります。</span><span class="sxs-lookup"><span data-stu-id="07428-146">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="07428-147"><code>dotnet new -l&#124;--list</code> コマンドでテンプレートの一覧を生成したとき、*Tags* 列が表示される場合、この列にも分類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="07428-147">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the <code>dotnet new -l&#124;--list</code> command.</span></span> |
| `identity`        | <span data-ttu-id="07428-148">string</span><span class="sxs-lookup"><span data-stu-id="07428-148">string</span></span>        | <span data-ttu-id="07428-149">このテンプレートの一意の名前。</span><span class="sxs-lookup"><span data-stu-id="07428-149">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="07428-150">string</span><span class="sxs-lookup"><span data-stu-id="07428-150">string</span></span>        | <span data-ttu-id="07428-151">ユーザーに対して表示されるテンプレートの名前。</span><span class="sxs-lookup"><span data-stu-id="07428-151">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="07428-152">string</span><span class="sxs-lookup"><span data-stu-id="07428-152">string</span></span>        | <span data-ttu-id="07428-153">テンプレートを選択するための既定の省略名 (短い名前)。テンプレート名が GUI 経由で選択されるのではなく、ユーザーによって指定される環境に適用されます。</span><span class="sxs-lookup"><span data-stu-id="07428-153">A default shorthand for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="07428-154">たとえば、CLI コマンドでコマンド プロンプトからテンプレートを利用するときに省略名が便利です。</span><span class="sxs-lookup"><span data-stu-id="07428-154">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

#### <a name="example"></a><span data-ttu-id="07428-155">例:</span><span class="sxs-lookup"><span data-stu-id="07428-155">Example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

<span data-ttu-id="07428-156">*template.json* ファイルの完全スキーマは [JSON Schema Store](http://json.schemastore.org/template) にあります。</span><span class="sxs-lookup"><span data-stu-id="07428-156">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span>

## <a name="net-default-templates"></a><span data-ttu-id="07428-157">.NET の既定のテンプレート</span><span class="sxs-lookup"><span data-stu-id="07428-157">.NET default templates</span></span>

<span data-ttu-id="07428-158">[.NET Core SDK](https://www.microsoft.com/net/download/core) をインストールすると、コンソール アプリ、クラス ライブラリ、単体テスト プロジェクト、ASP.NET Core アプリ ([Angular](https://angular.io/) プロジェクトと [React](https://facebook.github.io/react/) プロジェクトを含む)、構成ファイルなど、プロジェクトやファイルを作成するための 12 個を超える組み込みテンプレートが与えられます。</span><span class="sxs-lookup"><span data-stu-id="07428-158">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="07428-159">`-l|--list` オプションを付けて `dotnet new` コマンドを実行すると、組み込みテンプレートの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="07428-159">To list the built-in templates, execute the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="07428-160">テンプレートをパッケージ化し、NuGet パッケージ (nupkg ファイル) を作成する</span><span class="sxs-lookup"><span data-stu-id="07428-160">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="07428-161">現在のところ、カスタム テンプレートを Windows でパッケージ化するとき、[dotnet pack](dotnet-pack.md) ではなく、[nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) が利用されます。</span><span class="sxs-lookup"><span data-stu-id="07428-161">Currently, a custom template is packed on Windows with [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (not [dotnet pack](dotnet-pack.md)).</span></span> <span data-ttu-id="07428-162">プラットフォームに依存しないパッケージ化の場合、[NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000) の利用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="07428-162">For cross-platform packaging, consider using [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).</span></span>

<span data-ttu-id="07428-163">プロジェクト フォルダーの中身はその *.template.config/template.json* ファイルと共に *content* という名前のフォルダーに置かれます。</span><span class="sxs-lookup"><span data-stu-id="07428-163">The contents of the project folder, together with its *.template.config/template.json* file, are placed into a folder named *content*.</span></span> <span data-ttu-id="07428-164">*content* フォルダーの隣に [*nuspec*](/nuget/create-packages/creating-a-package) ファイルを追加します。このファイルは XML マニフェスト ファイルであり、パッケージの中身が記述され、NuGet パッケージの作成プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="07428-164">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package), which is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span> <span data-ttu-id="07428-165">*nuspec* ファイルの **\<packageTypes>** 要素の中に、**\<packageType>** 要素を追加し、`name` 属性の値を `Template` にします。</span><span class="sxs-lookup"><span data-stu-id="07428-165">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="07428-166">*content* フォルダーと *nuspec* ファイルの両方を同じディレクトリに入れます。</span><span class="sxs-lookup"><span data-stu-id="07428-166">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="07428-167">下の表は、NuGet パッケージとしてテンプレートを生成するために必要な *nuspec* ファイルの最小要素をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="07428-167">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

| <span data-ttu-id="07428-168">要素</span><span class="sxs-lookup"><span data-stu-id="07428-168">Element</span></span>            | <span data-ttu-id="07428-169">型</span><span class="sxs-lookup"><span data-stu-id="07428-169">Type</span></span>   | <span data-ttu-id="07428-170">説明</span><span class="sxs-lookup"><span data-stu-id="07428-170">Description</span></span> |
| ------------------ | ------ | ----------- |
| <span data-ttu-id="07428-171">**\<authors>**</span><span class="sxs-lookup"><span data-stu-id="07428-171">**\<authors>**</span></span>     | <span data-ttu-id="07428-172">string</span><span class="sxs-lookup"><span data-stu-id="07428-172">string</span></span> | <span data-ttu-id="07428-173">パッケージ作成者の一覧。コンマで区切られています。nuget.org のプロファイル名と一致します。作成者は nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="07428-173">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
| <span data-ttu-id="07428-174">**\<description>**</span><span class="sxs-lookup"><span data-stu-id="07428-174">**\<description>**</span></span> | <span data-ttu-id="07428-175">string</span><span class="sxs-lookup"><span data-stu-id="07428-175">string</span></span> | <span data-ttu-id="07428-176">UI 画面用のパッケージの長い説明。</span><span class="sxs-lookup"><span data-stu-id="07428-176">A long description of the package for UI display.</span></span> |
| <span data-ttu-id="07428-177">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="07428-177">**\<id>**</span></span>          | <span data-ttu-id="07428-178">string</span><span class="sxs-lookup"><span data-stu-id="07428-178">string</span></span> | <span data-ttu-id="07428-179">パッケージの識別子で、大文字と小文字が区別されます。nuget.org 全体で、あるいはパッケージが置かれるギャラリーで一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="07428-179">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="07428-180">ID には、URL によっては無効なスペースや文字が含まれることがあります。また、一般的に、.NET の名前空間ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="07428-180">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="07428-181">手引きについては、「[Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)」 (一意のパッケージ識別子を選択し、バージョン番号を設定する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07428-181">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
| <span data-ttu-id="07428-182">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="07428-182">**\<packageType>**</span></span> | <span data-ttu-id="07428-183">string</span><span class="sxs-lookup"><span data-stu-id="07428-183">string</span></span> | <span data-ttu-id="07428-184">この要素を **\<metadata>** 要素の中の **\<packageTypes>** 要素内に置きます。</span><span class="sxs-lookup"><span data-stu-id="07428-184">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="07428-185">**\<packageType>** 要素の `name` 属性を `Template` に設定します。</span><span class="sxs-lookup"><span data-stu-id="07428-185">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
| <span data-ttu-id="07428-186">**\<version>**</span><span class="sxs-lookup"><span data-stu-id="07428-186">**\<version>**</span></span>     | <span data-ttu-id="07428-187">string</span><span class="sxs-lookup"><span data-stu-id="07428-187">string</span></span> | <span data-ttu-id="07428-188">パッケージのバージョン。major.minor.patch パターンになります。</span><span class="sxs-lookup"><span data-stu-id="07428-188">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="07428-189">「[プレリリース バージョン](/nuget/create-packages/prerelease-packages#semantic-versioning)」トピックに説明があるように、バージョン番号にはプレリリース接尾辞が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="07428-189">Version numbers may include a pre-release suffix as described in the [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning) topic.</span></span> |

<span data-ttu-id="07428-190">*nuspec* ファイルの完全スキーマについては、[.nuspec リファレンス](/nuget/schema/nuspec)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="07428-190">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span> <span data-ttu-id="07428-191">テンプレートのサンプル *nuspec* ファイルは、「[dotnet new のカスタム テンプレートを作成する](~/docs/core/tutorials/create-custom-template.md)」チュートリアルにあります。</span><span class="sxs-lookup"><span data-stu-id="07428-191">An example *nuspec* file for a template appears in the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

<span data-ttu-id="07428-192">`nuget pack <PATH_TO_NUSPEC_FILE>` コマンドで[パッケージを作成](/nuget/create-packages/creating-a-package#creating-the-package)します。</span><span class="sxs-lookup"><span data-stu-id="07428-192">[Create a package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span>

## <a name="installing-a-template"></a><span data-ttu-id="07428-193">テンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="07428-193">Installing a template</span></span>

<span data-ttu-id="07428-194">カスタム テンプレートは、あらゆる NuGet フィードで NuGet パッケージからインストールできます。*nupkg* ファイルを直接参照するか、テンプレートを作成する構成が含まれるファイル システム ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="07428-194">Install a custom template from a NuGet package on any NuGet feed by referencing a *nupkg* file directly or by specifying a file system directory that contains a templating configuration.</span></span> <span data-ttu-id="07428-195">[dotnet new](dotnet-new.md) コマンドで `-i|--install` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="07428-195">Use the `-i|--install` option with the [dotnet new](dotnet-new.md) command.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="07428-196">nuget.org に保存されている NuGet パッケージからテンプレートをインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-196">To install a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="07428-197">ローカル nupkg ファイルからテンプレートをインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-197">To install a template from a local nupkg file</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="07428-198">ファイル システム ディレクトリからテンプレートをインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-198">To install a template from a file system directory</span></span>

<span data-ttu-id="07428-199">`FILE_SYSTEM_DIRECTORY` は、プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="07428-199">The `FILE_SYSTEM_DIRECTORY` is the project folder containing the project and the *.template.config* folder:</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a><span data-ttu-id="07428-200">テンプレートをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="07428-200">Uninstalling a template</span></span>

<span data-ttu-id="07428-201">カスタム テンプレートをアンインストールするには、その `id` で NuGet パッケージを参照するか、テンプレートを作成する構成が含まれるファイル システム ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="07428-201">Uninstall a custom template by referencing a NuGet package by its `id` or by specifying a file system directory that contains a templating configuration.</span></span> <span data-ttu-id="07428-202">[dotnet new](dotnet-new.md) コマンドで `-u|--uninstall` インストール オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="07428-202">Use the `-u|--uninstall` install option with the [dotnet new](dotnet-new.md) command.</span></span>

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="07428-203">nuget.org に保存されている NuGet パッケージからテンプレートをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-203">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="07428-204">ローカル nupkg ファイルからテンプレートをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-204">To uninstall a template from a local nupkg file</span></span>

<span data-ttu-id="07428-205">テンプレートをアンインストールするとき、*nupkg* ファイルのパスを利用しないでください。</span><span class="sxs-lookup"><span data-stu-id="07428-205">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="07428-206">*`dotnet new -u <PATH_TO_NUPKG_FILE>` でテンプレートをアンインストールしようとすると失敗します。*</span><span class="sxs-lookup"><span data-stu-id="07428-206">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="07428-207">パッケージはその `id` で参照してください。</span><span class="sxs-lookup"><span data-stu-id="07428-207">Reference the package by its `id`:</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a><span data-ttu-id="07428-208">ファイル システム ディレクトリからテンプレートをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="07428-208">To uninstall a template from a file system directory</span></span>

<span data-ttu-id="07428-209">`FILE_SYSTEM_DIRECTORY` は、プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="07428-209">The `FILE_SYSTEM_DIRECTORY` is the project folder containing the project and the *.template.config* folder:</span></span>

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="07428-210">カスタム テンプレートを利用してプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="07428-210">Create a project using a custom template</span></span>

<span data-ttu-id="07428-211">テンプレートがインストールされたら、事前インストールされている他のテンプレートの場合と同様に、`dotnet new <TEMPLATE>` コマンドを実行してテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="07428-211">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="07428-212">[オプション](dotnet-new.md#options)を `dotnet new` コマンドに指定することもできます。テンプレート設定で構成した、テンプレート固有のオプションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="07428-212">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template specific options you configured in the template settings.</span></span> <span data-ttu-id="07428-213">テンプレートの省略名 (短い名前) をコマンドに直接指定します。</span><span class="sxs-lookup"><span data-stu-id="07428-213">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="07428-214">関連項目</span><span class="sxs-lookup"><span data-stu-id="07428-214">See also</span></span>

[<span data-ttu-id="07428-215">dotnet new のカスタム テンプレートを作成する (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="07428-215">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)  
[<span data-ttu-id="07428-216">dotnet/templating GitHub リポジトリ Wiki</span><span class="sxs-lookup"><span data-stu-id="07428-216">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="07428-217">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="07428-217">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="07428-218">dotnet new の独自のテンプレートを作成する方法</span><span class="sxs-lookup"><span data-stu-id="07428-218">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="07428-219">JSON Schema Store の *template.json* スキーマ</span><span class="sxs-lookup"><span data-stu-id="07428-219">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
