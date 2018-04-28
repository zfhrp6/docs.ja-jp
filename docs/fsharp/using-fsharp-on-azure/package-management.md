---
title: Azure の f# でパッケージの管理の使用
description: パケットを作成または Nuget を使用して、F# で Azure の依存関係を管理するには
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da6938c6ee29292571f4269c68a9148c13738422
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="2cece-103">F# の Azure の依存関係のためのパッケージ管理</span><span class="sxs-lookup"><span data-stu-id="2cece-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="2cece-104">パッケージ マネージャーを使用する場合は、この Azure 開発用のパッケージを取得することは簡単です。</span><span class="sxs-lookup"><span data-stu-id="2cece-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="2cece-105">2 つのオプション[パケットを作成](https://fsprojects.github.io/Paket/)と[NuGet](https://www.nuget.org/)です。</span><span class="sxs-lookup"><span data-stu-id="2cece-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="2cece-106">使用するパケットを作成</span><span class="sxs-lookup"><span data-stu-id="2cece-106">Using Paket</span></span>

<span data-ttu-id="2cece-107">使用する場合[パケットを作成](https://fsprojects.github.io/Paket/)の依存関係マネージャーとして使用することができます、 `paket.exe` Azure の依存関係を追加するツールです。</span><span class="sxs-lookup"><span data-stu-id="2cece-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="2cece-108">例えば:</span><span class="sxs-lookup"><span data-stu-id="2cece-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="2cece-109">または、使用する場合[モノラル](https://www.mono-project.com/)のクロス プラットフォームの .NET 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="2cece-110">これが追加されます`WindowsAzure.Storage`、現在のディレクトリ内のプロジェクトのパッケージの依存関係のセット、変更、`paket.dependencies`ファイル、およびパッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="2cece-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="2cece-111">依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="2cece-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="2cece-112">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="2cece-113">次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="2cece-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="2cece-114">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="2cece-115">Nuget を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cece-115">Using Nuget</span></span>

<span data-ttu-id="2cece-116">使用する場合[NuGet](https://www.nuget.org/)の依存関係マネージャーとして使用することができます、 `nuget.exe` Azure の依存関係を追加するツールです。</span><span class="sxs-lookup"><span data-stu-id="2cece-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="2cece-117">例えば:</span><span class="sxs-lookup"><span data-stu-id="2cece-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="2cece-118">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="2cece-119">これが追加されます`WindowsAzure.Storage`現在のディレクトリ、およびダウンロード パッケージにプロジェクトのパッケージの依存関係のセットにします。</span><span class="sxs-lookup"><span data-stu-id="2cece-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="2cece-120">依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="2cece-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="2cece-121">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="2cece-122">次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="2cece-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="2cece-123">または、Mono 開発。</span><span class="sxs-lookup"><span data-stu-id="2cece-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="2cece-124">参照元のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="2cece-124">Referencing Assemblies</span></span>

<span data-ttu-id="2cece-125">F# スクリプトで、パッケージを使用するのを使用してパッケージに含まれるアセンブリを参照する必要があります、`#r`ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="2cece-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="2cece-126">例えば:</span><span class="sxs-lookup"><span data-stu-id="2cece-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="2cece-127">ご覧のように、DLL と完全の DLL の名前は必ずしも厳密パッケージ名と同じ相対パスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cece-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="2cece-128">Framework のバージョンおよび可能性のあるパッケージのバージョン番号、パスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2cece-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="2cece-129">インストールされているすべてのアセンブリを検索するには、Windows のコマンドラインで次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cece-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="2cece-130">または、Unix のシェルでは、何か次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2cece-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="2cece-131">これにより、パスにインストールされているアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="2cece-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="2cece-132">そこから、フレームワークのバージョンの正しいパスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="2cece-132">From there, you can select the correct path for your framework version.</span></span>
