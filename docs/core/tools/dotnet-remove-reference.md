---
title: "dotnet remove reference コマンド - .NET Core CLI"
description: "dotnet remove reference コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 691fd77c7605b6476adc764f20e59b51abd7d914
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="53f5b-104">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="53f5b-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="53f5b-105">name</span><span class="sxs-lookup"><span data-stu-id="53f5b-105">Name</span></span>

<span data-ttu-id="53f5b-106">`dotnet remove reference` - プロジェクト間参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="53f5b-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="53f5b-107">構文</span><span class="sxs-lookup"><span data-stu-id="53f5b-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="53f5b-108">説明</span><span class="sxs-lookup"><span data-stu-id="53f5b-108">Description</span></span>

<span data-ttu-id="53f5b-109">`dotnet remove reference` コマンドは、プロジェクトからプロジェクト参照を削除する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="53f5b-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="53f5b-110">引数</span><span class="sxs-lookup"><span data-stu-id="53f5b-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="53f5b-111">ターゲット プロジェクト ファイル。</span><span class="sxs-lookup"><span data-stu-id="53f5b-111">Target project file.</span></span> <span data-ttu-id="53f5b-112">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="53f5b-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="53f5b-113">削除するプロジェクト間 (P2P) 参照。</span><span class="sxs-lookup"><span data-stu-id="53f5b-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="53f5b-114">1 つまたは複数のプロジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="53f5b-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="53f5b-115">[glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="53f5b-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="53f5b-116">オプション</span><span class="sxs-lookup"><span data-stu-id="53f5b-116">Options</span></span>

`-h|--help`

<span data-ttu-id="53f5b-117">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="53f5b-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="53f5b-118">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="53f5b-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="53f5b-119">使用例</span><span class="sxs-lookup"><span data-stu-id="53f5b-119">Examples</span></span>

<span data-ttu-id="53f5b-120">指定したプロジェクトからプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="53f5b-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="53f5b-121">現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="53f5b-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="53f5b-122">Unix/Linux で glob パターンを使用して複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="53f5b-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
