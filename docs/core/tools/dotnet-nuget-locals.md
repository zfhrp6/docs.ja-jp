---
title: "dotnet nuget locals コマンド - .NET Core CLI"
description: "dotnet nuget locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。"
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9c8df8e457a9883b86abd0505c0c682d849bc7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="d0989-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d0989-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d0989-104">name</span><span class="sxs-lookup"><span data-stu-id="d0989-104">Name</span></span>

<span data-ttu-id="d0989-105">`dotnet nuget locals` - ローカル NuGet リソースをクリアまたはリストします。</span><span class="sxs-lookup"><span data-stu-id="d0989-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d0989-106">構文</span><span class="sxs-lookup"><span data-stu-id="d0989-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="d0989-107">説明</span><span class="sxs-lookup"><span data-stu-id="d0989-107">Description</span></span>

<span data-ttu-id="d0989-108">`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d0989-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="d0989-109">引数</span><span class="sxs-lookup"><span data-stu-id="d0989-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="d0989-110">次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="d0989-110">One of the following values:</span></span>

* <span data-ttu-id="d0989-111">`all` - 指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0989-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="d0989-112">`http-cache` - 指定した操作を HTTP 要求キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0989-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="d0989-113">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0989-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="d0989-114">`global-packages` - 指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0989-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="d0989-115">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0989-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="d0989-116">`temp` - 指定した操作を一時キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0989-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="d0989-117">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="d0989-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="d0989-118">オプション</span><span class="sxs-lookup"><span data-stu-id="d0989-118">Options</span></span>

`-h|--help`

<span data-ttu-id="d0989-119">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="d0989-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="d0989-120">クリア オプションは、指定されたキャッシュの種類でクリア操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0989-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="d0989-121">キャッシュ ディレクトリの内容は、再帰的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="d0989-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="d0989-122">実行中のユーザー/グループには、キャッシュ ディレクトリ内のファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d0989-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="d0989-123">アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d0989-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="d0989-124">一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d0989-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="d0989-125">コマンドライン出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="d0989-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="d0989-126">使用例</span><span class="sxs-lookup"><span data-stu-id="d0989-126">Examples</span></span>

<span data-ttu-id="d0989-127">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d0989-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="d0989-128">ローカルの HTTP キャッシュ ディレクトリのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d0989-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="d0989-129">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) からすべてのファイルをクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0989-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="d0989-130">ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0989-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="d0989-131">ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="d0989-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="d0989-132">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d0989-132">Troubleshooting</span></span>

<span data-ttu-id="d0989-133">`dotnet nuget locals` コマンドを使うときの一般的な問題やエラーについては、「[Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d0989-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>