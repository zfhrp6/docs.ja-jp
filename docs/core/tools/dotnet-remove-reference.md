---
title: dotnet remove reference コマンド - .NET Core CLI
description: dotnet remove reference コマンドは、プロジェクト間参照を削除する便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="d6b2b-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d6b2b-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d6b2b-104">name</span><span class="sxs-lookup"><span data-stu-id="d6b2b-104">Name</span></span>

<span data-ttu-id="d6b2b-105">`dotnet remove reference` - プロジェクト間参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d6b2b-106">構文</span><span class="sxs-lookup"><span data-stu-id="d6b2b-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="d6b2b-107">説明</span><span class="sxs-lookup"><span data-stu-id="d6b2b-107">Description</span></span>

<span data-ttu-id="d6b2b-108">`dotnet remove reference` コマンドは、プロジェクトからプロジェクト参照を削除する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="d6b2b-109">引数</span><span class="sxs-lookup"><span data-stu-id="d6b2b-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d6b2b-110">ターゲット プロジェクト ファイル。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-110">Target project file.</span></span> <span data-ttu-id="d6b2b-111">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="d6b2b-112">削除するプロジェクト間 (P2P) 参照。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-112">Project to project (P2P references to remove.</span></span> <span data-ttu-id="d6b2b-113">1 つまたは複数のプロジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="d6b2b-114">[glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースの端末でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="d6b2b-115">オプション</span><span class="sxs-lookup"><span data-stu-id="d6b2b-115">Options</span></span>

`-h|--help`

<span data-ttu-id="d6b2b-116">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d6b2b-117">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="d6b2b-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d6b2b-118">使用例</span><span class="sxs-lookup"><span data-stu-id="d6b2b-118">Examples</span></span>

<span data-ttu-id="d6b2b-119">指定したプロジェクトからプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="d6b2b-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="d6b2b-120">現在のディレクトリ内のプロジェクトから複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="d6b2b-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="d6b2b-121">Unix/Linux で glob パターンを使用して複数のプロジェクト参照を削除する:</span><span class="sxs-lookup"><span data-stu-id="d6b2b-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
