---
title: "dotnet list reference コマンド - .NET Core CLI"
description: "dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="b9ee7-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="b9ee7-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b9ee7-104">名前</span><span class="sxs-lookup"><span data-stu-id="b9ee7-104">Name</span></span>

<span data-ttu-id="b9ee7-105">`dotnet list reference` - プロジェクト間参照を列挙します。</span><span class="sxs-lookup"><span data-stu-id="b9ee7-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b9ee7-106">構文</span><span class="sxs-lookup"><span data-stu-id="b9ee7-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="b9ee7-107">説明</span><span class="sxs-lookup"><span data-stu-id="b9ee7-107">Description</span></span>

<span data-ttu-id="b9ee7-108">`dotnet list reference` コマンドは、特定のプロジェクトのプロジェクト参照を列挙する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="b9ee7-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b9ee7-109">引数</span><span class="sxs-lookup"><span data-stu-id="b9ee7-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b9ee7-110">参照の一覧取得に使うプロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9ee7-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="b9ee7-111">指定されていない場合、プロジェクト ファイルの現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="b9ee7-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="b9ee7-112">オプション</span><span class="sxs-lookup"><span data-stu-id="b9ee7-112">Options</span></span>

`-h|--help`

<span data-ttu-id="b9ee7-113">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b9ee7-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="b9ee7-114">例</span><span class="sxs-lookup"><span data-stu-id="b9ee7-114">Examples</span></span>

<span data-ttu-id="b9ee7-115">指定したプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="b9ee7-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="b9ee7-116">現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="b9ee7-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
