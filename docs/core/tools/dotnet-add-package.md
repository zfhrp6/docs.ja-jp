---
title: "dotnet add package コマンド - .NET Core CLI"
description: "'dotnet add package' コマンドは、NuGet パッケージ参照をプロジェクトに追加する便利なオプションを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 3b372b55cbdd8e0e6cc6a6b1089915e0da802489
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-add-package"></a><span data-ttu-id="3df26-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3df26-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3df26-104">name</span><span class="sxs-lookup"><span data-stu-id="3df26-104">Name</span></span>

<span data-ttu-id="3df26-105">`dotnet add package` - プロジェクト ファイルにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3df26-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3df26-106">構文</span><span class="sxs-lookup"><span data-stu-id="3df26-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="3df26-107">説明</span><span class="sxs-lookup"><span data-stu-id="3df26-107">Description</span></span>

<span data-ttu-id="3df26-108">`dotnet add package` コマンドは、プロジェクト ファイルにパッケージ参照を追加する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="3df26-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="3df26-109">このコマンドの実行後に、パッケージがプロジェクト内のフレームワークと互換性があることを確認する互換性チェックがあります。</span><span class="sxs-lookup"><span data-stu-id="3df26-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="3df26-110">互換性チェックに合格すると、`<PackageReference>` 要素がプロジェクト ファイルに追加されて、[dotnet restore](dotnet-restore.md) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="3df26-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3df26-111">たとえば、`Newtonsoft.Json` を *ToDo.csproj* に追加すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3df26-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="3df26-112">この *ToDo.csproj* ファイルには、参照されるパッケージの [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3df26-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="3df26-113">引数</span><span class="sxs-lookup"><span data-stu-id="3df26-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="3df26-114">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="3df26-114">Specifies the project file.</span></span> <span data-ttu-id="3df26-115">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="3df26-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="3df26-116">追加するパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="3df26-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="3df26-117">オプション</span><span class="sxs-lookup"><span data-stu-id="3df26-117">Options</span></span>

`-h|--help`

<span data-ttu-id="3df26-118">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="3df26-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="3df26-119">パッケージのバージョン。</span><span class="sxs-lookup"><span data-stu-id="3df26-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3df26-120">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、パッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3df26-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="3df26-121">復元のプレビューと互換性チェックを実行せずにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="3df26-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="3df26-122">復元操作の間に特定の NuGet パッケージのソースを使います。</span><span class="sxs-lookup"><span data-stu-id="3df26-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="3df26-123">指定したディレクトリにパッケージを復元します。</span><span class="sxs-lookup"><span data-stu-id="3df26-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="3df26-124">使用例</span><span class="sxs-lookup"><span data-stu-id="3df26-124">Examples</span></span>

<span data-ttu-id="3df26-125">`Newtonsoft.Json` NuGet パッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="3df26-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="3df26-126">特定バージョンのパッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="3df26-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="3df26-127">特定の NuGet ソースを使用してパッケージを追加する:</span><span class="sxs-lookup"><span data-stu-id="3df26-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
