---
title: Windows における .NET Core の前提条件
description: Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。
author: JRAlexander
ms.author: johalex
ms.date: 04/24/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 6f2ba8540a38f8e30d3d968f5e2c891c850053aa
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="604f5-103">Windows における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="604f5-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="604f5-104">この記事では、Windows で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="604f5-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="604f5-105">後述のサポート対象 OS のバージョンと依存関係は、Windows で .NET Core アプリを開発する次の 3 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="604f5-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="604f5-106">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="604f5-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="604f5-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="604f5-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="604f5-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="604f5-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="604f5-109">.NET Core がサポートされている Windows バージョン</span><span class="sxs-lookup"><span data-stu-id="604f5-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="604f5-110">.NET Core は、次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="604f5-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="604f5-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="604f5-111">Windows 7 SP1</span></span>
* <span data-ttu-id="604f5-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="604f5-112">Windows 8.1</span></span>
* <span data-ttu-id="604f5-113">Windows 10 Anniversary Update (バージョン 1607) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="604f5-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="604f5-114">Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="604f5-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="604f5-115">Windows Server 2012 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="604f5-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="604f5-116">Windows Server 2012 R2 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="604f5-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="604f5-117">Windows Server 2016 (フル サーバー、Server Core または Nano Server)</span><span class="sxs-lookup"><span data-stu-id="604f5-117">Windows Server 2016 (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="604f5-118">.NET Core 2.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="604f5-118">See [.NET Core 2.x - Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems.</span></span>

<span data-ttu-id="604f5-119">.NET Core 1.x がサポートされるオペレーティング システムの完全なリストは、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="604f5-119">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems.</span></span>

## <a name="net-core-dependencies"></a><span data-ttu-id="604f5-120">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="604f5-120">.NET Core dependencies</span></span>

<span data-ttu-id="604f5-121">.NET Core 1.1 以前のバージョンを Windows 10 と Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="604f5-121">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="604f5-122">この依存関係は、.NET Core インストーラーにより自動でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="604f5-122">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="604f5-123">次の場合には、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685) を手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="604f5-123">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="604f5-124">[インストーラー スクリプト](./tools/dotnet-install-script.md)を使用して .NET Core をインストールする。</span><span class="sxs-lookup"><span data-stu-id="604f5-124">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="604f5-125">自己完結型の .NET Core アプリケーションを展開する。</span><span class="sxs-lookup"><span data-stu-id="604f5-125">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="604f5-126">ソースから製品をビルドする。</span><span class="sxs-lookup"><span data-stu-id="604f5-126">Building the product from source.</span></span>
* <span data-ttu-id="604f5-127">*.zip* ファイルを使用して .NET Core をインストールする。</span><span class="sxs-lookup"><span data-stu-id="604f5-127">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="604f5-128">これにはビルド/CI/CD サーバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="604f5-128">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="604f5-129">*Windows 8.1 以前のバージョン、または Windows Server 2012 R2 以前のバージョンの場合:* Windows のインストールが最新であることと、Windows Update からインストールできる [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) が含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="604f5-129">*For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:* Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) which can be installed through Windows Update.</span></span> <span data-ttu-id="604f5-130">この更新プログラムがインストールされていない場合は、.NET Core アプリケーションを起動するときに、次のようなエラーが表示されます。`The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="604f5-130">If you don't have this update installed, you'll see an error when you launch a .NET Core application like the following: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="604f5-131">Visual Studio 2017 の前提条件</span><span class="sxs-lookup"><span data-stu-id="604f5-131">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="604f5-132">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="604f5-132">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="604f5-133">[Visual Studio 2017](#visual-studio-2017) では、Windows 上に .NET Core アプリ用の統合開発環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="604f5-133">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="604f5-134">Visual Studio 2017 での変更の詳細については、[リリース ノート](/visualstudio/releasenotes/vs2017-relnotes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="604f5-134">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="604f5-135">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="604f5-135">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="604f5-136">Visual Studio 2017 で .NET Core 2.x アプリを開発するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="604f5-136">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="604f5-137">(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 バージョン 15.3.0 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="604f5-137">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="604f5-139">**.NET Core クロスプラットフォームの開発**ツールセットがインストールされると、Visual Studio 2017 で .NET Core 1.x が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="604f5-139">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="604f5-140">Visual Studio 2017 で .NET Core 2.x がサポートされるように、.NET Core 2.x SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="604f5-140">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="604f5-141">[.NET Core 2.x SDK](https://www.microsoft.com/net/download/core) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="604f5-141">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="604f5-142">次の手順を使用して、既存または新規の .NET Core 1.x プロジェクトを .NET Core 2.x に再ターゲットします。</span><span class="sxs-lookup"><span data-stu-id="604f5-142">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="604f5-143">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="604f5-143">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="604f5-144">**[ターゲット フレームワーク]** 選択メニューで、値を **[.NET Core 2.0]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="604f5-144">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![[ターゲット フレームワーク] メニュー項目で [.NET Core 2.0] が選択された Visual Studio 2017 のアプリケーション プロジェクト プロパティのスクリーンショット](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="604f5-146">.NET Core 2.x SDK がインストールされると、Visual Studio 2017 は .NET Core SDK 2.x を既定で使用し、次のアクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="604f5-146">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="604f5-147">既存の .NET Core 1.x プロジェクトを開き、ビルドし、実行する。</span><span class="sxs-lookup"><span data-stu-id="604f5-147">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="604f5-148">.NET Core 1.x プロジェクトを .NET Core 2.x、ビルド、および実行に再ターゲット。</span><span class="sxs-lookup"><span data-stu-id="604f5-148">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="604f5-149">.NET Core 2.x の新しいプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="604f5-149">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="604f5-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="604f5-150">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="604f5-151">Visual Studio で .NET Core 1.x アプリを開発するには、(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 RTM (バージョン 15.0.26228.4) 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="604f5-151">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="604f5-153">.NET Core 1.x の開発に Visual Studio 2015 を使用することはできますが、次の理由からお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="604f5-153">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="604f5-154">.NET Core Tooling は、サポートされていないプレビュー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="604f5-154">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="604f5-155">プロジェクトは、非推奨の project.json ベースです。</span><span class="sxs-lookup"><span data-stu-id="604f5-155">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="604f5-156">プロジェクト形式の変更の詳細については、[変更点の概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="604f5-156">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="604f5-157">お使いの Visual Studio 2017 バージョンを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="604f5-157">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="604f5-158">**[ヘルプ]** メニューの **[About Microsoft Visual Studio]** (Microsoft Visual Studio のバージョン情報) を選択します。</span><span class="sxs-lookup"><span data-stu-id="604f5-158">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="604f5-159">**[Microsoft Visual Studio のバージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="604f5-159">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="604f5-160">.NET Core 2.1 Preview 1 アプリの場合は、Visual Studio 2017 バージョン 15.6 Preview 6 以降です。</span><span class="sxs-lookup"><span data-stu-id="604f5-160">For .NET Core 2.1 Preview 1 apps, Visual Studio 2017 version 15.6 Preview 6 or higher.</span></span>
>   * <span data-ttu-id="604f5-161">.NET Core 2.0 アプリの場合は、Visual Studio 2017 バージョン 15.3 以降です。</span><span class="sxs-lookup"><span data-stu-id="604f5-161">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="604f5-162">.NET Core 1.x アプリの場合は、Visual Studio 2017 バージョン 15.0 以降です。</span><span class="sxs-lookup"><span data-stu-id="604f5-162">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
