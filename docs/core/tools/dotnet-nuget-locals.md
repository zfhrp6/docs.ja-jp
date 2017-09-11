---
title: "dotnet-nuget-locals コマンド - .NET Core CLI"
description: "dotnet-nuget-locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。"
keywords: "dotnet-nuget-locals, CLI, CLI コマンド, .NET Core"
author: karann-msft
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8440229e-317e-4dc1-9463-cba5fdb12c3b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2c9ea7b3b7c61b347cb7c56254773290f04a0cd6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-nuget-locals"></a><span data-ttu-id="6d305-104">dotnet-nuget locals</span><span class="sxs-lookup"><span data-stu-id="6d305-104">dotnet-nuget locals</span></span>

## <a name="name"></a><span data-ttu-id="6d305-105">名前</span><span class="sxs-lookup"><span data-stu-id="6d305-105">Name</span></span>

<span data-ttu-id="6d305-106">`dotnet-nuget locals` - ローカル NuGet リソースをクリアまたはリストします。</span><span class="sxs-lookup"><span data-stu-id="6d305-106">`dotnet-nuget locals` - Clears or lists local NuGet resources.</span></span> 

## <a name="synopsis"></a><span data-ttu-id="6d305-107">構文</span><span class="sxs-lookup"><span data-stu-id="6d305-107">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="6d305-108">説明</span><span class="sxs-lookup"><span data-stu-id="6d305-108">Description</span></span>

<span data-ttu-id="6d305-109">`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6d305-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="6d305-110">引数</span><span class="sxs-lookup"><span data-stu-id="6d305-110">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="6d305-111">次のいずれかの値です。</span><span class="sxs-lookup"><span data-stu-id="6d305-111">One of the following values:</span></span>

`all`

<span data-ttu-id="6d305-112">指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d305-112">Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>

`http-cache`

<span data-ttu-id="6d305-113">指定した操作を HTTP 要求キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d305-113">Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="6d305-114">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6d305-114">The other cache locations are not affected.</span></span>

`global-packages`

<span data-ttu-id="6d305-115">指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d305-115">Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="6d305-116">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6d305-116">The other cache locations are not affected.</span></span>

`temp`

<span data-ttu-id="6d305-117">指定した操作を一時キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d305-117">Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="6d305-118">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6d305-118">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="6d305-119">オプション</span><span class="sxs-lookup"><span data-stu-id="6d305-119">Options</span></span>

`-h|--help`

<span data-ttu-id="6d305-120">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6d305-120">Prints out a short help for the command.</span></span>  

`-c|--clear`

<span data-ttu-id="6d305-121">クリア オプションは、指定されたキャッシュの種類でクリア操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6d305-121">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="6d305-122">キャッシュ ディレクトリの内容は、再帰的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="6d305-122">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="6d305-123">実行中のユーザー/グループには、キャッシュ ディレクトリ内のファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="6d305-123">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="6d305-124">アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d305-124">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="6d305-125">一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d305-125">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="6d305-126">コマンドライン出力を強制的に英語にします。</span><span class="sxs-lookup"><span data-stu-id="6d305-126">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="6d305-127">例</span><span class="sxs-lookup"><span data-stu-id="6d305-127">Examples</span></span>

<span data-ttu-id="6d305-128">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="6d305-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="6d305-129">ローカルの HTTP キャッシュ ディレクトリのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="6d305-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="6d305-130">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) からすべてのファイルをクリアします。</span><span class="sxs-lookup"><span data-stu-id="6d305-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="6d305-131">ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6d305-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="6d305-132">ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6d305-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="6d305-133">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6d305-133">Troubleshooting</span></span>

<span data-ttu-id="6d305-134">`dotnet nuget locals` コマンドを使うときの一般的な問題やエラーについては、「[Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d305-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>

