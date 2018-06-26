---
title: dotnet nuget delete コマンド - .NET Core CLI
description: dotnet-nuget-delete コマンドは、サーバーからパッケージを削除または一覧から削除します。
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728415"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="957c5-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="957c5-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="957c5-104">name</span><span class="sxs-lookup"><span data-stu-id="957c5-104">Name</span></span>

<span data-ttu-id="957c5-105">`dotnet nuget delete` - サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="957c5-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="957c5-106">構文</span><span class="sxs-lookup"><span data-stu-id="957c5-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="957c5-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="957c5-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="957c5-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="957c5-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="957c5-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="957c5-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="957c5-110">説明</span><span class="sxs-lookup"><span data-stu-id="957c5-110">Description</span></span>

<span data-ttu-id="957c5-111">`dotnet nuget delete` コマンドは、サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="957c5-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="957c5-112">[nuget.org](https://www.nuget.org/) の場合、この操作ではパッケージを一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="957c5-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="957c5-113">引数</span><span class="sxs-lookup"><span data-stu-id="957c5-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="957c5-114">削除するパッケージの名前または ID です。</span><span class="sxs-lookup"><span data-stu-id="957c5-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="957c5-115">削除するパッケージのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="957c5-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="957c5-116">オプション</span><span class="sxs-lookup"><span data-stu-id="957c5-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="957c5-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="957c5-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="957c5-118">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="957c5-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="957c5-119">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="957c5-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="957c5-120">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="957c5-120">The API key for the server.</span></span>

<span data-ttu-id="957c5-121">`--no-service-endpoint` ソース URL に "api/v2/package" を追加しません。</span><span class="sxs-lookup"><span data-stu-id="957c5-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="957c5-122">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="957c5-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="957c5-123">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="957c5-123">Specifies the server URL.</span></span> <span data-ttu-id="957c5-124">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="957c5-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="957c5-125">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="957c5-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="957c5-126">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="957c5-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="957c5-127">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="957c5-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="957c5-128">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="957c5-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="957c5-129">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="957c5-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="957c5-130">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="957c5-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="957c5-131">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="957c5-131">Specifies the server URL.</span></span> <span data-ttu-id="957c5-132">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="957c5-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="957c5-133">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="957c5-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="957c5-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="957c5-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="957c5-135">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="957c5-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="957c5-136">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="957c5-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="957c5-137">サーバーの API キーです。</span><span class="sxs-lookup"><span data-stu-id="957c5-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="957c5-138">ユーザーに入力や確認のメッセージ画面を表示しません。</span><span class="sxs-lookup"><span data-stu-id="957c5-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="957c5-139">サーバー URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="957c5-139">Specifies the server URL.</span></span> <span data-ttu-id="957c5-140">nuget.org でサポートされている URL には、`http://www.nuget.org`、`http://www.nuget.org/api/v3`、および `http://www.nuget.org/api/v2/package` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="957c5-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="957c5-141">プライベート フィードの場合、ホスト名を置き換えます (`%hostname%/api/v3` など)。</span><span class="sxs-lookup"><span data-stu-id="957c5-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="957c5-142">使用例</span><span class="sxs-lookup"><span data-stu-id="957c5-142">Examples</span></span>

<span data-ttu-id="957c5-143">`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="957c5-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="957c5-144">ユーザーに資格情報やその他の入力を求めずに、`Microsoft.AspNetCore.Mvc` パッケージのバージョン 1.0 を削除します。</span><span class="sxs-lookup"><span data-stu-id="957c5-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
