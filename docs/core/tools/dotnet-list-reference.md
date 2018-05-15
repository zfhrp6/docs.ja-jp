---
title: dotnet list reference コマンド - .NET Core CLI
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 24cb1124fc3f8707afe727e6a73d35d5dde39937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="0d1e8-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0d1e8-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0d1e8-104">name</span><span class="sxs-lookup"><span data-stu-id="0d1e8-104">Name</span></span>

<span data-ttu-id="0d1e8-105">`dotnet list reference` - プロジェクト間参照を列挙します。</span><span class="sxs-lookup"><span data-stu-id="0d1e8-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d1e8-106">構文</span><span class="sxs-lookup"><span data-stu-id="0d1e8-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="0d1e8-107">説明</span><span class="sxs-lookup"><span data-stu-id="0d1e8-107">Description</span></span>

<span data-ttu-id="0d1e8-108">`dotnet list reference` コマンドは、特定のプロジェクトのプロジェクト参照を列挙する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="0d1e8-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="0d1e8-109">引数</span><span class="sxs-lookup"><span data-stu-id="0d1e8-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0d1e8-110">参照の一覧取得に使うプロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d1e8-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="0d1e8-111">指定されていない場合、プロジェクト ファイルの現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="0d1e8-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="0d1e8-112">オプション</span><span class="sxs-lookup"><span data-stu-id="0d1e8-112">Options</span></span>

`-h|--help`

<span data-ttu-id="0d1e8-113">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0d1e8-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="0d1e8-114">使用例</span><span class="sxs-lookup"><span data-stu-id="0d1e8-114">Examples</span></span>

<span data-ttu-id="0d1e8-115">指定したプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="0d1e8-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="0d1e8-116">現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="0d1e8-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
