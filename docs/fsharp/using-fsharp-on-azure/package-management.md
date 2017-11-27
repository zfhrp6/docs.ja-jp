---
title: "Azure の f# でパッケージの管理の使用"
description: "パケットを作成または Nuget を使用して、F# で Azure の依存関係を管理するには"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="da6fc-104">F# の Azure の依存関係のためのパッケージ管理</span><span class="sxs-lookup"><span data-stu-id="da6fc-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="da6fc-105">パッケージ マネージャーを使用する場合は、この Azure 開発用のパッケージを取得することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="da6fc-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="da6fc-106">2 つのオプション[パケットを作成](https://fsprojects.github.io/Paket/)と[NuGet](https://www.nuget.org/)です。</span><span class="sxs-lookup"><span data-stu-id="da6fc-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="da6fc-107">使用するパケットを作成</span><span class="sxs-lookup"><span data-stu-id="da6fc-107">Using Paket</span></span>

<span data-ttu-id="da6fc-108">使用する場合[パケットを作成](https://fsprojects.github.io/Paket/)の依存関係マネージャーとして使用することができます、 `paket.exe` Azure の依存関係を追加するツールです。</span><span class="sxs-lookup"><span data-stu-id="da6fc-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="da6fc-109">例:</span><span class="sxs-lookup"><span data-stu-id="da6fc-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="da6fc-110">または、使用する場合[モノラル](http://www.mono-project.com/)のクロス プラットフォームの .NET 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="da6fc-111">これが追加されます`WindowsAzure.Storage`、現在のディレクトリ内のプロジェクトのパッケージの依存関係のセット、変更、`paket.dependencies`ファイル、およびパッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="da6fc-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="da6fc-112">依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="da6fc-113">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="da6fc-114">次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="da6fc-115">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="da6fc-116">Nuget を使用します。</span><span class="sxs-lookup"><span data-stu-id="da6fc-116">Using Nuget</span></span>

<span data-ttu-id="da6fc-117">使用する場合[NuGet](https://www.nuget.org/)の依存関係マネージャーとして使用することができます、 `nuget.exe` Azure の依存関係を追加するツールです。</span><span class="sxs-lookup"><span data-stu-id="da6fc-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="da6fc-118">例:</span><span class="sxs-lookup"><span data-stu-id="da6fc-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="da6fc-119">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="da6fc-120">これが追加されます`WindowsAzure.Storage`現在のディレクトリ、およびダウンロード パッケージにプロジェクトのパッケージの依存関係のセットにします。</span><span class="sxs-lookup"><span data-stu-id="da6fc-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="da6fc-121">依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="da6fc-122">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="da6fc-123">次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="da6fc-124">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="da6fc-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="da6fc-125">参照元のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="da6fc-125">Referencing Assemblies</span></span>

<span data-ttu-id="da6fc-126">F# スクリプトで、パッケージを使用するのを使用してパッケージに含まれるアセンブリを参照する必要があります、`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="da6fc-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="da6fc-127">例:</span><span class="sxs-lookup"><span data-stu-id="da6fc-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="da6fc-128">ご覧のように、DLL と完全の DLL の名前は必ずしも厳密パッケージ名と同じ相対パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da6fc-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="da6fc-129">Framework のバージョンおよび可能性のあるパッケージのバージョン番号、パスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="da6fc-130">インストールされているすべてのアセンブリを検索するには、Windows のコマンドラインで次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="da6fc-131">または、Unix のシェルでは、何か次のようにします。</span><span class="sxs-lookup"><span data-stu-id="da6fc-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="da6fc-132">これにより、パスにインストールされているアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="da6fc-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="da6fc-133">そこから、フレームワークのバージョンの正しいパスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="da6fc-133">From there, you can select the correct path for your framework version.</span></span>
