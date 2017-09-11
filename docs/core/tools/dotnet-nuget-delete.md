---
title: "dotnet-nuget-delete コマンド - .NET Core CLI"
description: "dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。"
keywords: "dotnet-nuget-delete, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ce6886f2f4cc8cc633cfc61215fe17550f746c91
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-delete"></a><span data-ttu-id="16184-104">dotnet-nuget delete</span><span class="sxs-lookup"><span data-stu-id="16184-104">dotnet-nuget delete</span></span>

## <a name="name"></a><span data-ttu-id="16184-105">名前</span><span class="sxs-lookup"><span data-stu-id="16184-105">Name</span></span>

<span data-ttu-id="16184-106">`dotnet-nuget-delete` - サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="16184-106">`dotnet-nuget-delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="16184-107">構文</span><span class="sxs-lookup"><span data-stu-id="16184-107">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="16184-108">説明</span><span class="sxs-lookup"><span data-stu-id="16184-108">Description</span></span>

<span data-ttu-id="16184-109">`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="16184-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="16184-110">[nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="16184-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="16184-111">引数</span><span class="sxs-lookup"><span data-stu-id="16184-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="16184-112">削除するパッケージです。</span><span class="sxs-lookup"><span data-stu-id="16184-112">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="16184-113">削除するパッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="16184-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="16184-114">オプション</span><span class="sxs-lookup"><span data-stu-id="16184-114">Options</span></span>

`-h|--help`

<span data-ttu-id="16184-115">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="16184-115">Prints out a short help for the command.</span></span>  

`-s|--source <SOURCE>`

<span data-ttu-id="16184-116">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="16184-116">Specifies the server URL.</span></span> <span data-ttu-id="16184-117">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="16184-117">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="16184-118">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="16184-118">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="16184-119">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="16184-119">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="16184-120">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="16184-120">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="16184-121">コマンドライン出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="16184-121">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="16184-122">例</span><span class="sxs-lookup"><span data-stu-id="16184-122">Examples</span></span>

<span data-ttu-id="16184-123">`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="16184-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="16184-124">ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="16184-124">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`

