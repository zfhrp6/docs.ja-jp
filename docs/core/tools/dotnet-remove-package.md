---
title: dotnet remove package コマンド - .NET Core CLI
description: dotnet remove package コマンドは、プロジェクトへの NuGet パッケージ参照を削除する便利なオプションを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 6a18be1a853119be245623e8fa0a0e44ed819e8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="e2aa0-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="e2aa0-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e2aa0-104">name</span><span class="sxs-lookup"><span data-stu-id="e2aa0-104">Name</span></span>

<span data-ttu-id="e2aa0-105">`dotnet remove package` - プロジェクト ファイルからパッケージ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e2aa0-106">構文</span><span class="sxs-lookup"><span data-stu-id="e2aa0-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="e2aa0-107">説明</span><span class="sxs-lookup"><span data-stu-id="e2aa0-107">Description</span></span>

<span data-ttu-id="e2aa0-108">`dotnet remove package` コマンドは、NuGet パッケージ参照をプロジェクトから削除する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="e2aa0-109">引数</span><span class="sxs-lookup"><span data-stu-id="e2aa0-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e2aa0-110">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-110">Specifies the project file.</span></span> <span data-ttu-id="e2aa0-111">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="e2aa0-112">削除するパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="e2aa0-113">オプション</span><span class="sxs-lookup"><span data-stu-id="e2aa0-113">Options</span></span>

`-h|--help`

<span data-ttu-id="e2aa0-114">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="e2aa0-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="e2aa0-115">使用例</span><span class="sxs-lookup"><span data-stu-id="e2aa0-115">Examples</span></span>

<span data-ttu-id="e2aa0-116">現在のディレクトリにあるプロジェクトから `Newtonsoft.Json` NuGet パッケージを削除する:</span><span class="sxs-lookup"><span data-stu-id="e2aa0-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
