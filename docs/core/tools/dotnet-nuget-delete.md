---
title: dotnet nuget delete コマンド - .NET Core CLI
description: dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 639ade54bfed5eb2de89bdb3b7f451393b4be187
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="ceb08-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="ceb08-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ceb08-104">name</span><span class="sxs-lookup"><span data-stu-id="ceb08-104">Name</span></span>

<span data-ttu-id="ceb08-105">`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ceb08-106">構文</span><span class="sxs-lookup"><span data-stu-id="ceb08-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="ceb08-107">説明</span><span class="sxs-lookup"><span data-stu-id="ceb08-107">Description</span></span>

<span data-ttu-id="ceb08-108">`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="ceb08-109">[nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="ceb08-110">引数</span><span class="sxs-lookup"><span data-stu-id="ceb08-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="ceb08-111">削除するパッケージです。</span><span class="sxs-lookup"><span data-stu-id="ceb08-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="ceb08-112">削除するパッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="ceb08-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="ceb08-113">オプション</span><span class="sxs-lookup"><span data-stu-id="ceb08-113">Options</span></span>

`-h|--help`

<span data-ttu-id="ceb08-114">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="ceb08-115">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-115">Specifies the server URL.</span></span> <span data-ttu-id="ceb08-116">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ceb08-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="ceb08-117">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="ceb08-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="ceb08-118">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="ceb08-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="ceb08-119">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="ceb08-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="ceb08-120">コマンドライン出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="ceb08-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="ceb08-121">使用例</span><span class="sxs-lookup"><span data-stu-id="ceb08-121">Examples</span></span>

<span data-ttu-id="ceb08-122">`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="ceb08-123">ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="ceb08-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`