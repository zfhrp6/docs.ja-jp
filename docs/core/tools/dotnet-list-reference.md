---
title: "dotnet-list 参照コマンド - .NET Core CLI"
description: "dotnet-list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。"
keywords: "dotnet-list, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8f954a0c-03f8-4fbc-a529-b313ab12c623
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 701345e4db51d26b9eefe8f02b6c0526934de5c9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-list-reference"></a><span data-ttu-id="70c94-104">dotnet-list 参照</span><span class="sxs-lookup"><span data-stu-id="70c94-104">dotnet-list reference</span></span>

## <a name="name"></a><span data-ttu-id="70c94-105">名前</span><span class="sxs-lookup"><span data-stu-id="70c94-105">Name</span></span>

<span data-ttu-id="70c94-106">`dotnet-list reference` - プロジェクト間参照を列挙します。</span><span class="sxs-lookup"><span data-stu-id="70c94-106">`dotnet-list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="70c94-107">構文</span><span class="sxs-lookup"><span data-stu-id="70c94-107">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="70c94-108">説明</span><span class="sxs-lookup"><span data-stu-id="70c94-108">Description</span></span>

<span data-ttu-id="70c94-109">`dotnet list reference` コマンドは、特定のプロジェクトのプロジェクト参照を列挙する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="70c94-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="70c94-110">引数</span><span class="sxs-lookup"><span data-stu-id="70c94-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="70c94-111">参照の一覧取得に使うプロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="70c94-111">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="70c94-112">指定されていない場合、プロジェクト ファイルの現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="70c94-112">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="70c94-113">オプション</span><span class="sxs-lookup"><span data-stu-id="70c94-113">Options</span></span>

`-h|--help`

<span data-ttu-id="70c94-114">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="70c94-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="70c94-115">例</span><span class="sxs-lookup"><span data-stu-id="70c94-115">Examples</span></span>

<span data-ttu-id="70c94-116">指定したプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="70c94-116">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="70c94-117">現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="70c94-117">List the project references for the project in the current directory:</span></span>

`dotnet list reference`

