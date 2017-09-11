---
title: "Windows における .NET Core の前提条件"
description: "Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。"
keywords: ".NET Core, Windows, 前提条件, 依存関係, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 06/26/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0e414af0edbafed5b7f540eda6de2e5078eac789
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="5893e-104">Windows における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="5893e-104">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="5893e-105">この記事では、.NET Core アプリケーションを Windows コンピューターで展開および実行、ならびに Visual Studio を使用して開発するのに必要となる依存関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="5893e-105">This article shows you what dependencies you need to deploy and run .NET Core applications on Windows machines and develop using Visual Studio.</span></span>

## <a name="supported-windows-versions"></a><span data-ttu-id="5893e-106">サポートされている Windows バージョン</span><span class="sxs-lookup"><span data-stu-id="5893e-106">Supported Windows versions</span></span>

<span data-ttu-id="5893e-107">.NET Core は、Windows の次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5893e-107">.NET Core is supported on the following versions of Windows:</span></span>

* <span data-ttu-id="5893e-108">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="5893e-108">Windows 7 SP1</span></span>
* <span data-ttu-id="5893e-109">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="5893e-109">Windows 8.1</span></span>
* <span data-ttu-id="5893e-110">Windows 10</span><span class="sxs-lookup"><span data-stu-id="5893e-110">Windows 10</span></span>
* <span data-ttu-id="5893e-111">Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="5893e-111">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="5893e-112">Windows Server 2012 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="5893e-112">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="5893e-113">Windows Server 2012 R2 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="5893e-113">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="5893e-114">Windows Server 2016 (フル サーバー、Server Core または Nano Server)</span><span class="sxs-lookup"><span data-stu-id="5893e-114">Windows Server 2016 (Full Server, Server Core or Nano Server)</span></span>

<span data-ttu-id="5893e-115">サポートされるすべてのオペレーティング システムは、[.NET Core のリリース ノート](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)で確認してください。</span><span class="sxs-lookup"><span data-stu-id="5893e-115">See the [.NET Core Release Notes](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) for the full set of supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="5893e-116">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="5893e-116">.NET Core dependencies</span></span>

<span data-ttu-id="5893e-117">.NET Core を Windows 10 および Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="5893e-117">.NET Core requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="5893e-118">この依存関係は、.NET Core インストーラーを使用する場合は自動でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="5893e-118">This dependency is automatically installed for you if you use the .NET Core installer.</span></span> <span data-ttu-id="5893e-119">ただし、.NET Core を[インストーラー スクリプト](./tools/dotnet-install-script.md)でインストールしたか、自己完結型の .NET Core アプリケーションを配置する場合は、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/en-us/download/details.aspx?id=52685) を手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5893e-119">However, you need to manually install the [Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/en-us/download/details.aspx?id=52685) if you are installing .NET Core via the [installer script](./tools/dotnet-install-script.md) or deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="5893e-120"><em>Windows 7 および Windows Server 2008 コンピューターのみ:</em></span><span class="sxs-lookup"><span data-stu-id="5893e-120"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="5893e-121">Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/help/2533623) をインストールしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5893e-121">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="5893e-122">Visual Studio 2017 の前提条件</span><span class="sxs-lookup"><span data-stu-id="5893e-122">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="5893e-123">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5893e-123">You can use any editor of your choice to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="5893e-124">一方、統合開発環境の Windows 上で .NET Core アプリケーションを開発する場合、[Visual Studio 2017](#visual-studio-2017) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5893e-124">However, if you want to develop .NET Core applications on Windows in an integrated development environment, you can use [Visual Studio 2017](#visual-studio-2017).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5893e-125">プレビュー バージョンの .NET Core ツールで Visual Studio 2015 を使用できる場合でも、これらのプロジェクトは *project.json* ベースであるため、推奨されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5893e-125">Even though, it's possible to use Visual Studio 2015 with a preview version of the .NET Core tooling, these projects will be *project.json*-based, which is now deprecated.</span></span> <span data-ttu-id="5893e-126">Visual Studio 2017 では、MSBuild に基づくプロジェクト ファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5893e-126">Visual Studio 2017 uses project files based on MSBuild.</span></span> <span data-ttu-id="5893e-127">この形式変更の詳細については、[変更点の大まかな概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5893e-127">For more information about the format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>

<span data-ttu-id="5893e-128">Visual Studio 2017 を使用して .NET Core アプリを開発する場合は、最新版の Visual Studio をインストールする必要があります。その際、(**[他のツールセット]** セクションで) **プラットフォームに依存しない .NET Core** 開発ツールセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="5893e-128">To use Visual Studio 2017 to develop .NET Core apps, you'll need to have the latest version of Visual Studio installed with the **.NET Core cross-platform development** toolset (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="5893e-129">![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="5893e-129">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>

<span data-ttu-id="5893e-130">Visual Studio 2017 には複数のエディションがあります。</span><span class="sxs-lookup"><span data-stu-id="5893e-130">There are different editions of Visual Studio 2017.</span></span> <span data-ttu-id="5893e-131">[Visual Studio Community 2017](https://www.visualstudio.com/downloads/) を無料でダウンロードして始められます。</span><span class="sxs-lookup"><span data-stu-id="5893e-131">You can download [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) for free to get started.</span></span>  <span data-ttu-id="5893e-132">Visual Studio のインストール プロセスの詳細については、「[Install Visual Studio 2017](/visualstudio/install/install-visual-studio)」(Visual Studio のインストール) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5893e-132">To learn more about the Visual Studio installation process, see [Install Visual Studio 2017](/visualstudio/install/install-visual-studio).</span></span>

<span data-ttu-id="5893e-133">Visual Studio 2017 の最新バージョンを実行していることを確認するには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="5893e-133">To verify that you're running the latest version of Visual Studio 2017, do the following:</span></span>

 * <span data-ttu-id="5893e-134">[**ヘルプ**] メニューの [**About Microsoft Visual Studio**] (Microsoft Visual Studio のバージョン情報) を選択します。</span><span class="sxs-lookup"><span data-stu-id="5893e-134">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
 * <span data-ttu-id="5893e-135">[**Microsoft Visual Studio のバージョン情報**] ダイアログのバージョン番号は、15.0.26228.4 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5893e-135">In the **About Microsoft Visual Studio** dialog, the version number should be 15.0.26228.4 or higher.</span></span>

<span data-ttu-id="5893e-136">Visual Studio 2017 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5893e-136">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>

