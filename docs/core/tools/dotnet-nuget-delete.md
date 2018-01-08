---
title: "dotnet nuget delete コマンド - .NET Core CLI"
description: "dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 3c09556fe90a5c447b181bc1ac5b36f014399e4f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="4e075-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="4e075-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4e075-104">name</span><span class="sxs-lookup"><span data-stu-id="4e075-104">Name</span></span>

<span data-ttu-id="4e075-105">`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="4e075-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4e075-106">構文</span><span class="sxs-lookup"><span data-stu-id="4e075-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="4e075-107">説明</span><span class="sxs-lookup"><span data-stu-id="4e075-107">Description</span></span>

<span data-ttu-id="4e075-108">`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="4e075-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="4e075-109">[nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="4e075-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="4e075-110">引数</span><span class="sxs-lookup"><span data-stu-id="4e075-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="4e075-111">削除するパッケージです。</span><span class="sxs-lookup"><span data-stu-id="4e075-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="4e075-112">削除するパッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="4e075-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="4e075-113">オプション</span><span class="sxs-lookup"><span data-stu-id="4e075-113">Options</span></span>

`-h|--help`

<span data-ttu-id="4e075-114">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4e075-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="4e075-115">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e075-115">Specifies the server URL.</span></span> <span data-ttu-id="4e075-116">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e075-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="4e075-117">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="4e075-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="4e075-118">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="4e075-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="4e075-119">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="4e075-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="4e075-120">コマンドライン出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="4e075-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="4e075-121">使用例</span><span class="sxs-lookup"><span data-stu-id="4e075-121">Examples</span></span>

<span data-ttu-id="4e075-122">`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="4e075-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="4e075-123">ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="4e075-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`