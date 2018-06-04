---
title: dotnet sln コマンド - .NET Core CLI
description: dotnet-sln コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: dd77281b55b3e7fc7c293e402d11de016ef73cf8
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696713"
---
# <a name="dotnet-sln"></a><span data-ttu-id="19019-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="19019-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="19019-104">name</span><span class="sxs-lookup"><span data-stu-id="19019-104">Name</span></span>

<span data-ttu-id="19019-105">`dotnet sln` - .NET Core ソリューション ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="19019-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="19019-106">構文</span><span class="sxs-lookup"><span data-stu-id="19019-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="19019-107">説明</span><span class="sxs-lookup"><span data-stu-id="19019-107">Description</span></span>

<span data-ttu-id="19019-108">`dotnet sln` コマンドは、ソリューション ファイルでプロジェクトを追加、削除、一覧表示するための便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="19019-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="19019-109">コマンド</span><span class="sxs-lookup"><span data-stu-id="19019-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="19019-110">ソリューション ファイルに 1 つまたは複数のプロジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="19019-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="19019-111">[Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="19019-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="19019-112">ソリューション ファイルから 1 つまたは複数のプロジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="19019-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="19019-113">[Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="19019-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="19019-114">ソリューション ファイルのすべてのプロジェクトを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="19019-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="19019-115">引数</span><span class="sxs-lookup"><span data-stu-id="19019-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="19019-116">使用するソリューション ファイル。</span><span class="sxs-lookup"><span data-stu-id="19019-116">Solution file to use.</span></span> <span data-ttu-id="19019-117">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="19019-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="19019-118">ディレクトリに複数のソリューション ファイルがある場合、1 つを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19019-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="19019-119">オプション</span><span class="sxs-lookup"><span data-stu-id="19019-119">Options</span></span>

`-h|--help`

<span data-ttu-id="19019-120">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="19019-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="19019-121">使用例</span><span class="sxs-lookup"><span data-stu-id="19019-121">Examples</span></span>

<span data-ttu-id="19019-122">ソリューションに 1 つの C# プロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="19019-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="19019-123">ソリューションから 1 つの C# プロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="19019-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="19019-124">ソリューションに複数の C# プロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="19019-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="19019-125">ソリューションから複数の C# プロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="19019-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="19019-126">glob パターンを使用して、C# ソリューションに複数のプロジェクトを追加する:</span><span class="sxs-lookup"><span data-stu-id="19019-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="19019-127">glob パターンを使用して、C# ソリューションから複数のプロジェクトを削除する:</span><span class="sxs-lookup"><span data-stu-id="19019-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
