---
title: "Windows における .NET Core の前提条件"
description: "Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。"
author: JRAlexander
ms.author: johalex
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 16a72edde39e4857dbdfb400f195deb9975f993c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="722e4-103">Windows における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="722e4-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="722e4-104">この記事では、Windows で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="722e4-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="722e4-105">後述のサポート対象 OS のバージョンと依存関係は、Windows で .NET Core アプリを開発する次の 3 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="722e4-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="722e4-106">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="722e4-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="722e4-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="722e4-107">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads/)
* [<span data-ttu-id="722e4-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="722e4-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="722e4-109">.NET Core がサポートされている Windows バージョン</span><span class="sxs-lookup"><span data-stu-id="722e4-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="722e4-110">.NET Core は、次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="722e4-110">.NET Core is supported on the following versions of :</span></span>

* <span data-ttu-id="722e4-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="722e4-111">Windows 7 SP1</span></span>
* <span data-ttu-id="722e4-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="722e4-112">Windows 8.1</span></span>
* <span data-ttu-id="722e4-113">Windows 10、Windows 10 Anniversary Update (バージョン 1607) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="722e4-113">Windows 10, Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="722e4-114">Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="722e4-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="722e4-115">Windows Server 2012 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="722e4-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="722e4-116">Windows Server 2012 R2 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="722e4-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="722e4-117">Windows Server 2016 (フル サーバー、Server Core または Nano Server)</span><span class="sxs-lookup"><span data-stu-id="722e4-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="722e4-118">.NET Core 2.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="722e4-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="722e4-119">.NET Core 1.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="722e4-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="722e4-120">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="722e4-120">.NET Core dependencies</span></span>

<span data-ttu-id="722e4-121">1.1 およびそれ以前の .NET core は、Windows 10 および Windows Server 2016 より前のバージョンの Windows で実行されている場合、Visual C 再頒布可能が必要です。</span><span class="sxs-lookup"><span data-stu-id="722e4-121">.NET Core 1.1 and earlier requires the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="722e4-122">この依存関係は、.NET Core インストーラーにより自動でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="722e4-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="722e4-123">次の場合には、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685) を手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="722e4-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

   * <span data-ttu-id="722e4-124">[インストーラー スクリプト](./tools/dotnet-install-script.md)を使用して .NET Core をインストールする。</span><span class="sxs-lookup"><span data-stu-id="722e4-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
   * <span data-ttu-id="722e4-125">自己完結型の .NET Core アプリケーションを展開する。</span><span class="sxs-lookup"><span data-stu-id="722e4-125">Deploying a self-contained .NET Core application.</span></span>

> [!NOTE]
> <span data-ttu-id="722e4-126"><em>Windows 7 および Windows Server 2008 コンピューターのみ:</em></span><span class="sxs-lookup"><span data-stu-id="722e4-126"><em>For Windows 7 and Windows Server 2008 machines only:</em></span></span><br>
> <span data-ttu-id="722e4-127">Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/help/2533623) をインストールしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="722e4-127">Make sure that your Windows installation is up-to-date and includes hotfix [KB2533623](https://support.microsoft.com/help/2533623) installed through Windows Update.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="722e4-128">Visual Studio 2017 の前提条件</span><span class="sxs-lookup"><span data-stu-id="722e4-128">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="722e4-129">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="722e4-129">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span>  <span data-ttu-id="722e4-130">[Visual Studio 2017](#visual-studio-2017) では、Windows 上に .NET Core アプリ用の統合開発環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="722e4-130">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="722e4-131">Visual Studio 2017 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="722e4-131">You can read more about the changes in Visual Studio 2017 in the [release notes](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).</span></span>
# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="722e4-132">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="722e4-132">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="722e4-133">Visual Studio 2017 で .NET Core 2.x アプリを開発するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="722e4-133">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="722e4-134">(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 バージョン 15.3.0 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="722e4-134">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="722e4-135">![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="722e4-135">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs-15-3-workloads.jpg)</span></span>

<span data-ttu-id="722e4-136">**.NET Core クロスプラットフォームの開発**ツールセットがインストールされると、Visual Studio 2017 で .NET Core 1.x が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="722e4-136">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="722e4-137">Visual Studio 2017 で .NET Core 2.x がサポートされるように、.NET Core 2.x SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="722e4-137">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="722e4-138">[.NET Core 2.x SDK](https://www.microsoft.com/net/download/core) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="722e4-138">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="722e4-139">次の手順を使用して、既存または新規の .NET Core 1.x プロジェクトを .NET Core 2.x に再ターゲットします。</span><span class="sxs-lookup"><span data-stu-id="722e4-139">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="722e4-140">**[プロジェクト]** メニューの **[プロパティ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="722e4-140">On the **Project** menu, Choose **Properties**.</span></span> 
    * <span data-ttu-id="722e4-141">**[ターゲット フレームワーク]** 選択メニューで、値を **[.NET Core 2.0]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="722e4-141">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![[ターゲット フレームワーク] メニュー項目で [.NET Core 2.0] が選択された Visual Studio 2017 のアプリケーション プロジェクト プロパティのスクリーンショット](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="722e4-143">.NET Core 2.x SDK がインストールされると、Visual Studio 2017 は .NET Core SDK 2.x を既定で使用し、次のアクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="722e4-143">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

  * <span data-ttu-id="722e4-144">既存の .NET Core 1.x プロジェクトを開き、ビルドし、実行する。</span><span class="sxs-lookup"><span data-stu-id="722e4-144">Open, build, and run existing .NET Core 1.x projects.</span></span>
  * <span data-ttu-id="722e4-145">.NET Core 1.x プロジェクトを .NET Core 2.x、ビルド、および実行に再ターゲット。</span><span class="sxs-lookup"><span data-stu-id="722e4-145">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
  * <span data-ttu-id="722e4-146">.NET Core 2.x の新しいプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="722e4-146">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="722e4-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="722e4-147">.NET Core 1.x</span></span>](#tab/netcore1x)
<span data-ttu-id="722e4-148">Visual Studio で .NET Core 1.x アプリを開発するには、(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 RTM (バージョン 15.0.26228.4) 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="722e4-148">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>
<span data-ttu-id="722e4-149">![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)</span><span class="sxs-lookup"><span data-stu-id="722e4-149">![Screenshot of Visual Studio 2017 installation with the ".NET Core cross-platform development" workload selected](./media/windows-prerequisites/vs_workloads.jpg)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="722e4-150">.NET Core 1.x の開発に Visual Studio 2015 を使用することはできますが、次の理由からお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="722e4-150">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="722e4-151">.NET Core Tooling は、サポートされていないプレビュー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="722e4-151">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="722e4-152">プロジェクトは、非推奨の project.json ベースです。</span><span class="sxs-lookup"><span data-stu-id="722e4-152">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="722e4-153">プロジェクト形式の変更の詳細については、[変更点の概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="722e4-153">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

>[!TIP]
  > <span data-ttu-id="722e4-154">お使いの Visual Studio 2017 バージョンを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="722e4-154">To verify your Visual Studio 2017 version:</span></span>
>
     > * <span data-ttu-id="722e4-155">**[ヘルプ]** メニューの **[About Microsoft Visual Studio]** (Microsoft Visual Studio のバージョン情報) を選択します。</span><span class="sxs-lookup"><span data-stu-id="722e4-155">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
     > * <span data-ttu-id="722e4-156">**[Microsoft Visual Studio のバージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="722e4-156">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>     * <span data-ttu-id="722e4-157">.NET Core 2.x アプリの場合は、Visual Studio 2017 バージョン 15.3 (26730.01) 以降です。</span><span class="sxs-lookup"><span data-stu-id="722e4-157">For .NET Core 2.x apps, Visual Studio 2017 version 15.3 (26730.01) or higher.</span></span>
>     * <span data-ttu-id="722e4-158">.NET Core 1.x アプリの場合は、Visual Studio 2017 バージョン 15.0 (26228.04) 以降です。</span><span class="sxs-lookup"><span data-stu-id="722e4-158">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 (26228.04) or higher.</span></span>
