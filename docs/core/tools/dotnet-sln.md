---
title: "dotnet-sln コマンド - .NET Core CLI"
description: "dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。"
keywords: "dotnet-sln, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 04/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e5a72d3e-c14b-4b0a-a978-c5e54a0988c6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 606929fbcafddf47abf5da6d3c8ce97d5af06909
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-sln"></a><span data-ttu-id="12333-104">dotnet-sln</span><span class="sxs-lookup"><span data-stu-id="12333-104">dotnet-sln</span></span>

## <a name="name"></a><span data-ttu-id="12333-105">名前</span><span class="sxs-lookup"><span data-stu-id="12333-105">Name</span></span>

<span data-ttu-id="12333-106">`dotnet-sln` - .NET Core ソリューション ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="12333-106">`dotnet-sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="12333-107">構文</span><span class="sxs-lookup"><span data-stu-id="12333-107">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="12333-108">説明</span><span class="sxs-lookup"><span data-stu-id="12333-108">Description</span></span>

<span data-ttu-id="12333-109">`dotnet sln` コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="12333-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="12333-110">コマンド</span><span class="sxs-lookup"><span data-stu-id="12333-110">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="12333-111">ソリューション ファイルに 1 つまたは複数のプロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="12333-111">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="12333-112">[Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="12333-112">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="12333-113">ソリューション ファイルから 1 つまたは複数のプロジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="12333-113">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="12333-114">[Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="12333-114">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="12333-115">ソリューション ファイルのすべてのプロジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="12333-115">List all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="12333-116">引数</span><span class="sxs-lookup"><span data-stu-id="12333-116">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="12333-117">使用するソリューション ファイル。</span><span class="sxs-lookup"><span data-stu-id="12333-117">Solution file to use.</span></span> <span data-ttu-id="12333-118">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="12333-118">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="12333-119">ディレクトリに複数のソリューション ファイルがある場合、1 つを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12333-119">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="12333-120">オプション</span><span class="sxs-lookup"><span data-stu-id="12333-120">Options</span></span>

`-h|--help`

<span data-ttu-id="12333-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="12333-121">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="12333-122">例</span><span class="sxs-lookup"><span data-stu-id="12333-122">Examples</span></span>

<span data-ttu-id="12333-123">ソリューションに 1 つの C# プロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="12333-123">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="12333-124">ソリューションから 1 つの C# プロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="12333-124">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="12333-125">ソリューションに複数の C# プロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="12333-125">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="12333-126">ソリューションから複数の C# プロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="12333-126">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="12333-127">glob パターンを使用して、C# ソリューションに複数のプロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="12333-127">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="12333-128">glob パターンを使用して、C# ソリューションから複数のプロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="12333-128">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

