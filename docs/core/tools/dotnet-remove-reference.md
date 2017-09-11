---
title: "dotnet-remove 参照コマンド - .NET Core CLI"
description: "dotnet-remove 参照コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 889c6b7e-a313-40b1-9fd3-6a6f4c52f1d0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e22f64370be4b56597a303d79d3aabe1ff22a78a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-remove-reference"></a><span data-ttu-id="381a7-104">dotnet-remove 参照</span><span class="sxs-lookup"><span data-stu-id="381a7-104">dotnet-remove reference</span></span>

## <a name="name"></a><span data-ttu-id="381a7-105">名前</span><span class="sxs-lookup"><span data-stu-id="381a7-105">Name</span></span>

<span data-ttu-id="381a7-106">`dotnet-remove reference` - プロジェクト間参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="381a7-106">`dotnet-remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="381a7-107">構文</span><span class="sxs-lookup"><span data-stu-id="381a7-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="381a7-108">説明</span><span class="sxs-lookup"><span data-stu-id="381a7-108">Description</span></span>

<span data-ttu-id="381a7-109">`dotnet remove reference` コマンドは、プロジェクトからプロジェクト参照を削除する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="381a7-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="381a7-110">引数</span><span class="sxs-lookup"><span data-stu-id="381a7-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="381a7-111">ターゲット プロジェクト ファイル。</span><span class="sxs-lookup"><span data-stu-id="381a7-111">Target project file.</span></span> <span data-ttu-id="381a7-112">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="381a7-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="381a7-113">削除するプロジェクト間 (P2P) 参照。</span><span class="sxs-lookup"><span data-stu-id="381a7-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="381a7-114">1 つまたは複数のプロジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="381a7-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="381a7-115">[glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="381a7-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="381a7-116">オプション</span><span class="sxs-lookup"><span data-stu-id="381a7-116">Options</span></span>

`-h|--help`

<span data-ttu-id="381a7-117">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="381a7-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="381a7-118">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="381a7-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="381a7-119">例</span><span class="sxs-lookup"><span data-stu-id="381a7-119">Examples</span></span>

<span data-ttu-id="381a7-120">指定したプロジェクトからプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="381a7-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="381a7-121">現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="381a7-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="381a7-122">Unix/Linux で glob パターンを使用して複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="381a7-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`

