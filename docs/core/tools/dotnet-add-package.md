---
title: "dotnet-add パッケージ コマンド - .NET Core CLI"
description: "dotnet-add パッケージ コマンドは、NuGet パッケージ参照をプロジェクトに追加する便利なオプションを提供します。"
keywords: "dotnet-add, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40ee7cac969d4752ede66ba8df6ff6cb3f439aec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-package"></a><span data-ttu-id="0a110-104">dotnet-add パッケージ</span><span class="sxs-lookup"><span data-stu-id="0a110-104">dotnet-add package</span></span>

## <a name="name"></a><span data-ttu-id="0a110-105">名前</span><span class="sxs-lookup"><span data-stu-id="0a110-105">Name</span></span>

<span data-ttu-id="0a110-106">`dotnet-add package` - プロジェクト ファイルにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a110-106">`dotnet-add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0a110-107">構文</span><span class="sxs-lookup"><span data-stu-id="0a110-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory] [-h|--help]`

## <a name="description"></a><span data-ttu-id="0a110-108">説明</span><span class="sxs-lookup"><span data-stu-id="0a110-108">Description</span></span>

<span data-ttu-id="0a110-109">`dotnet add package` コマンドは、プロジェクト ファイルにパッケージ参照を追加する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="0a110-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="0a110-110">このコマンドの実行後に、パッケージがプロジェクト内のフレームワークと互換性があることを確認する互換性チェックがあります。</span><span class="sxs-lookup"><span data-stu-id="0a110-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="0a110-111">互換性チェックに合格すると、`<PackageReference>` 要素がプロジェクト ファイルに追加されて、[dotnet restore](dotnet-restore.md) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0a110-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="0a110-112">たとえば、`Newtonsoft.Json` を *ToDo.csproj* に追加すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a110-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following:</span></span>

```
Microsoft (R) Build Engine version 15.1.545.13942
Copyright (C) Microsoft Corporation. All rights reserved.

Writing /var/folders/gj/1mgg_4jx7mbdqbhw1kgcpcjr0000gn/T/tmpm0kTMD.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'ToDo.csproj'.
log  : Restoring packages for ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 119ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg 27ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '9.0.1' added to file 'ToDo.csproj'.
```

<span data-ttu-id="0a110-113">この *ToDo.csproj* ファイルには、参照されるパッケージの [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a110-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="0a110-114">引数</span><span class="sxs-lookup"><span data-stu-id="0a110-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0a110-115">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0a110-115">Specifies the project file.</span></span> <span data-ttu-id="0a110-116">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="0a110-116">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0a110-117">追加するパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="0a110-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="0a110-118">オプション</span><span class="sxs-lookup"><span data-stu-id="0a110-118">Options</span></span>

`-h|--help`

<span data-ttu-id="0a110-119">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0a110-119">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="0a110-120">パッケージのバージョン。</span><span class="sxs-lookup"><span data-stu-id="0a110-120">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0a110-121">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、パッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a110-121">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="0a110-122">復元のプレビューと互換性チェックを実行せずにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a110-122">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0a110-123">復元操作の間に特定の NuGet パッケージのソースを使います。</span><span class="sxs-lookup"><span data-stu-id="0a110-123">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="0a110-124">指定したディレクトリにパッケージを復元します。</span><span class="sxs-lookup"><span data-stu-id="0a110-124">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="0a110-125">例</span><span class="sxs-lookup"><span data-stu-id="0a110-125">Examples</span></span>

<span data-ttu-id="0a110-126">`Newtonsoft.Json` NuGet パッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="0a110-126">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="0a110-127">特定バージョンのパッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="0a110-127">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="0a110-128">特定の NuGet ソースを使用してパッケージを追加する:</span><span class="sxs-lookup"><span data-stu-id="0a110-128">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

