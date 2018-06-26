---
title: dotnet nuget locals コマンド - .NET Core CLI
description: dotnet nuget locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696872"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="f958c-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="f958c-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f958c-104">name</span><span class="sxs-lookup"><span data-stu-id="f958c-104">Name</span></span>

<span data-ttu-id="f958c-105">`dotnet nuget locals` - ローカル NuGet リソースをクリアまたはリストします。</span><span class="sxs-lookup"><span data-stu-id="f958c-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f958c-106">構文</span><span class="sxs-lookup"><span data-stu-id="f958c-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f958c-107">説明</span><span class="sxs-lookup"><span data-stu-id="f958c-107">Description</span></span>

<span data-ttu-id="f958c-108">`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="f958c-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="f958c-109">引数</span><span class="sxs-lookup"><span data-stu-id="f958c-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="f958c-110">一覧表示またはクリアするキャッシュの場所。</span><span class="sxs-lookup"><span data-stu-id="f958c-110">The cache location to list or clear.</span></span> <span data-ttu-id="f958c-111">次のいずれかの値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="f958c-111">It accepts one of the following values:</span></span>

* <span data-ttu-id="f958c-112">`all` - 指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f958c-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="f958c-113">`http-cache` - 指定した操作を HTTP 要求キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f958c-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="f958c-114">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f958c-114">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="f958c-115">`global-packages` - 指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f958c-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="f958c-116">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f958c-116">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="f958c-117">`temp` - 指定した操作を一時キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f958c-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="f958c-118">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f958c-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="f958c-119">オプション</span><span class="sxs-lookup"><span data-stu-id="f958c-119">Options</span></span>

`--force-english-output`

<span data-ttu-id="f958c-120">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="f958c-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="f958c-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="f958c-121">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="f958c-122">クリア オプションは、指定されたキャッシュの種類でクリア操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f958c-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="f958c-123">キャッシュ ディレクトリの内容は、再帰的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="f958c-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="f958c-124">実行中のユーザー/グループには、キャッシュ ディレクトリ内のファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="f958c-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="f958c-125">アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f958c-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

`-l|--list`

<span data-ttu-id="f958c-126">一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f958c-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="f958c-127">使用例</span><span class="sxs-lookup"><span data-stu-id="f958c-127">Examples</span></span>

<span data-ttu-id="f958c-128">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="f958c-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="f958c-129">ローカルの HTTP キャッシュ ディレクトリのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="f958c-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="f958c-130">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) からすべてのファイルをクリアします。</span><span class="sxs-lookup"><span data-stu-id="f958c-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="f958c-131">ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="f958c-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="f958c-132">ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="f958c-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="f958c-133">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f958c-133">Troubleshooting</span></span>

<span data-ttu-id="f958c-134">`dotnet nuget locals` コマンドを使うときの一般的な問題やエラーについては、「[Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f958c-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>