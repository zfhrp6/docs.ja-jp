---
title: "dotnet-remove パッケージ コマンド - .NET Core CLI"
description: "dotnet-remove パッケージ コマンドは、NuGet パッケージ参照をプロジェクトから削除する便利なオプションを提供します。"
keywords: "dotnet-remove, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2fcc8d37-16b3-4581-8038-832160e72d36
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a3fef846d5850e2c2a158ccd1f30a84e8f23f793
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-remove-package"></a><span data-ttu-id="ed9ae-104">dotnet-remove パッケージ</span><span class="sxs-lookup"><span data-stu-id="ed9ae-104">dotnet-remove package</span></span>

## <a name="name"></a><span data-ttu-id="ed9ae-105">名前</span><span class="sxs-lookup"><span data-stu-id="ed9ae-105">Name</span></span>

<span data-ttu-id="ed9ae-106">`dotnet-remove package` - プロジェクト ファイルからパッケージ参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-106">`dotnet-remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ed9ae-107">構文</span><span class="sxs-lookup"><span data-stu-id="ed9ae-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="ed9ae-108">説明</span><span class="sxs-lookup"><span data-stu-id="ed9ae-108">Description</span></span>

<span data-ttu-id="ed9ae-109">`dotnet remove package` コマンドは、NuGet パッケージ参照をプロジェクトから削除する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="ed9ae-110">引数</span><span class="sxs-lookup"><span data-stu-id="ed9ae-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ed9ae-111">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-111">Specifies the project file.</span></span> <span data-ttu-id="ed9ae-112">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-112">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="ed9ae-113">削除するパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="ed9ae-114">オプション</span><span class="sxs-lookup"><span data-stu-id="ed9ae-114">Options</span></span>

`-h|--help`

<span data-ttu-id="ed9ae-115">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="ed9ae-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ed9ae-116">例</span><span class="sxs-lookup"><span data-stu-id="ed9ae-116">Examples</span></span>

<span data-ttu-id="ed9ae-117">現在のディレクトリにあるプロジェクトから `Newtonsoft.Json` NuGet パッケージを削除する:</span><span class="sxs-lookup"><span data-stu-id="ed9ae-117">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`

