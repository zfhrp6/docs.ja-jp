---
title: Windows における .NET Core の前提条件
description: Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="prerequisites-for-net-core-on-windows"></a><span data-ttu-id="6d4cc-103">Windows における .NET Core の前提条件</span><span class="sxs-lookup"><span data-stu-id="6d4cc-103">Prerequisites for .NET Core on Windows</span></span>

<span data-ttu-id="6d4cc-104">この記事では、Windows で .NET Core アプリケーションを開発するために必要な依存関係を示します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-104">This article shows the dependencies needed to develop .NET Core applications on Windows.</span></span> <span data-ttu-id="6d4cc-105">後述のサポート対象 OS のバージョンと依存関係は、Windows で .NET Core アプリを開発する次の 3 つの方法に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on Windows:</span></span>

* [<span data-ttu-id="6d4cc-106">コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-106">Command line</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="6d4cc-107">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6d4cc-107">Visual Studio 2017</span></span>](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [<span data-ttu-id="6d4cc-108">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6d4cc-108">Visual Studio Code</span></span>](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a><span data-ttu-id="6d4cc-109">.NET Core がサポートされている Windows バージョン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-109">.NET Core supported Windows versions</span></span>

<span data-ttu-id="6d4cc-110">.NET Core は、次のバージョンでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-110">.NET Core is supported on the following versions of:</span></span>

* <span data-ttu-id="6d4cc-111">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="6d4cc-111">Windows 7 SP1</span></span>
* <span data-ttu-id="6d4cc-112">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6d4cc-112">Windows 8.1</span></span>
* <span data-ttu-id="6d4cc-113">Windows 10 Anniversary Update (バージョン 1607) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-113">Windows 10 Anniversary Update (version 1607) or later versions</span></span>
* <span data-ttu-id="6d4cc-114">Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="6d4cc-114">Windows Server 2008 R2 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="6d4cc-115">Windows Server 2012 SP1 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="6d4cc-115">Windows Server 2012 SP1 (Full Server or Server Core)</span></span>
* <span data-ttu-id="6d4cc-116">Windows Server 2012 R2 (フル サーバーまたは Server Core)</span><span class="sxs-lookup"><span data-stu-id="6d4cc-116">Windows Server 2012 R2 (Full Server or Server Core)</span></span>
* <span data-ttu-id="6d4cc-117">Windows Server 2016 以降のバージョン (フル サーバー、Server Core、または Nano Server)</span><span class="sxs-lookup"><span data-stu-id="6d4cc-117">Windows Server 2016 or later versions (Full Server, Server Core, or Nano Server)</span></span>

<span data-ttu-id="6d4cc-118">次の記事では、.NET Core がサポートされたオペレーティング システム (バージョンごと) の完全な一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-118">The following articles have a complete list of .NET Core supported operating systems per version:</span></span>

* [<span data-ttu-id="6d4cc-119">.NET Core 2.1 - サポートされている OS バージョン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-119">.NET Core 2.1 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [<span data-ttu-id="6d4cc-120">.NET Core 2.0 - サポートされている OS バージョン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-120">.NET Core 2.0 - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [<span data-ttu-id="6d4cc-121">.NET Core 1.x - サポートされている OS バージョン</span><span class="sxs-lookup"><span data-stu-id="6d4cc-121">.NET Core 1.x - Supported OS Versions</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a><span data-ttu-id="6d4cc-122">.NET Core の依存関係</span><span class="sxs-lookup"><span data-stu-id="6d4cc-122">.NET Core dependencies</span></span>

<span data-ttu-id="6d4cc-123">.NET Core 1.1 以前のバージョンを Windows 10 と Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-123">.NET Core 1.1 and earlier versions require the Visual C++ Redistributable when running on Windows versions earlier than Windows 10 and Windows Server 2016.</span></span> <span data-ttu-id="6d4cc-124">この依存関係は、.NET Core インストーラーにより自動でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-124">This dependency is automatically installed by the .NET Core installer.</span></span>

<span data-ttu-id="6d4cc-125">次の場合には、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685) を手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-125">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) must be manually installed when:</span></span>

* <span data-ttu-id="6d4cc-126">[インストーラー スクリプト](./tools/dotnet-install-script.md)を使用して .NET Core をインストールする。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-126">Installing .NET Core with the [installer script](./tools/dotnet-install-script.md).</span></span>
* <span data-ttu-id="6d4cc-127">自己完結型の .NET Core アプリケーションを展開する。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-127">Deploying a self-contained .NET Core application.</span></span>
* <span data-ttu-id="6d4cc-128">ソースから製品をビルドする。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-128">Building the product from source.</span></span>
* <span data-ttu-id="6d4cc-129">*.zip* ファイルを使用して .NET Core をインストールする。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-129">Installing .NET Core via a *.zip* file.</span></span> <span data-ttu-id="6d4cc-130">これにはビルド/CI/CD サーバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-130">This can include build/CI/CD servers.</span></span>

> [!NOTE]
> <span data-ttu-id="6d4cc-131">**Windows 8.1 以前のバージョン、または Windows Server 2012 R2 以前のバージョンの場合:**</span><span class="sxs-lookup"><span data-stu-id="6d4cc-131">**For Windows 8.1 and earlier versions, or Windows Server 2012 R2 and earlier versions:**</span></span>
>
> <span data-ttu-id="6d4cc-132">Windows のインストールが最新であり、Windows Update から修正プログラム [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows) をインストールしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-132">Make sure that your Windows installation is up-to-date and includes [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), which can be installed through Windows Update.</span></span> <span data-ttu-id="6d4cc-133">この更新プログラムがインストールされていない場合は、.NET Core アプリケーションを起動するときに、次のようなエラーが表示されます。`The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span><span class="sxs-lookup"><span data-stu-id="6d4cc-133">If you don't have this update installed, you'll see an error like the following when you launch a .NET Core application: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`</span></span>
>
> <span data-ttu-id="6d4cc-134">**Windows 7 または Windows Server 2008 R2 の場合:**</span><span class="sxs-lookup"><span data-stu-id="6d4cc-134">**For Windows 7 or Windows Server 2008 R2:**</span></span>
>
> <span data-ttu-id="6d4cc-135">KB2999226 に加え、[KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) もインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-135">In addition to KB2999226, make sure you also have [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) installed.</span></span> <span data-ttu-id="6d4cc-136">この更新プログラムがインストールされていない場合は、.NET Core アプリケーションを起動するときに、次のようなエラーが表示されます。`The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`</span><span class="sxs-lookup"><span data-stu-id="6d4cc-136">If you don't have this update installed, you'll see an error similar to the following when you launch a .NET Core application: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.</span></span>

## <a name="prerequisites-with-visual-studio-2017"></a><span data-ttu-id="6d4cc-137">Visual Studio 2017 の前提条件</span><span class="sxs-lookup"><span data-stu-id="6d4cc-137">Prerequisites with Visual Studio 2017</span></span>

<span data-ttu-id="6d4cc-138">.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-138">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="6d4cc-139">[Visual Studio 2017](#visual-studio-2017) では、Windows 上に .NET Core アプリ用の統合開発環境が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-139">[Visual Studio 2017](#visual-studio-2017) provides an integrated development environment for .NET Core apps on Windows.</span></span>

<span data-ttu-id="6d4cc-140">Visual Studio 2017 での変更の詳細については、[リリース ノート](/visualstudio/releasenotes/vs2017-relnotes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-140">You can read more about the changes in Visual Studio 2017 in the [release notes](/visualstudio/releasenotes/vs2017-relnotes).</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="6d4cc-141">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="6d4cc-141">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="6d4cc-142">Visual Studio 2017 で .NET Core 2.x アプリを開発するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-142">To develop .NET Core 2.x apps in Visual Studio 2017:</span></span>

 1. <span data-ttu-id="6d4cc-143">(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 バージョン 15.3.0 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-143">[Download and install Visual Studio 2017 version 15.3.0 or higher](/visualstudio/install/install-visual-studio) with the **.NET Core cross-platform development** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs-15-3-workloads.jpg)

<span data-ttu-id="6d4cc-145">**.NET Core クロスプラットフォームの開発**ツールセットがインストールされると、Visual Studio 2017 で .NET Core 1.x が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-145">After the **.NET Core cross-platform development** toolset is installed, Visual Studio 2017 uses .NET Core 1.x by default.</span></span> <span data-ttu-id="6d4cc-146">Visual Studio 2017 で .NET Core 2.x がサポートされるように、.NET Core 2.x SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-146">Install the .NET Core 2.x SDK to get .NET Core 2.x support in Visual Studio 2017.</span></span>

 2. <span data-ttu-id="6d4cc-147">[.NET Core 2.x SDK](https://www.microsoft.com/net/download/core) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-147">Install the [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).</span></span>
 3. <span data-ttu-id="6d4cc-148">次の手順を使用して、既存または新規の .NET Core 1.x プロジェクトを .NET Core 2.x に再ターゲットします。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-148">Retarget existing or new .NET Core 1.x projects to .NET Core 2.x using the following instructions:</span></span>
    * <span data-ttu-id="6d4cc-149">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-149">On the **Project** menu, Choose **Properties**.</span></span>
    * <span data-ttu-id="6d4cc-150">**[ターゲット フレームワーク]** 選択メニューで、値を **[.NET Core 2.0]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-150">In the **Target framework** selection menu, set the value to **.NET Core 2.0**.</span></span>

![[ターゲット フレームワーク] メニュー項目で [.NET Core 2.0] が選択された Visual Studio 2017 のアプリケーション プロジェクト プロパティのスクリーンショット](./media/windows-prerequisites/Targeting-dotnetCore2.png)

<span data-ttu-id="6d4cc-152">.NET Core 2.x SDK がインストールされると、Visual Studio 2017 は .NET Core SDK 2.x を既定で使用し、次のアクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-152">Once the .NET Core 2.x SDK is installed, Visual Studio 2017 uses the .NET Core SDK 2.x by default, and supports the following actions:</span></span>

* <span data-ttu-id="6d4cc-153">既存の .NET Core 1.x プロジェクトを開き、ビルドし、実行する。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-153">Open, build, and run existing .NET Core 1.x projects.</span></span>
* <span data-ttu-id="6d4cc-154">.NET Core 1.x プロジェクトを .NET Core 2.x、ビルド、および実行に再ターゲット。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-154">Retarget .NET Core 1.x projects to .NET Core 2.x, build, and run.</span></span>
* <span data-ttu-id="6d4cc-155">.NET Core 2.x の新しいプロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-155">Create new .NET Core 2.x projects.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d4cc-156">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d4cc-156">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="6d4cc-157">Visual Studio で .NET Core 1.x アプリを開発するには、(**[その他のツールセット]** セクションで) **[.NET Core クロスプラットフォームの開発]** ワークロードを選択して、[Visual Studio 2017 RTM (バージョン 15.0.26228.4) 以降をダウンロードしてインストール](/visualstudio/install/install-visual-studio)します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-157">To develop .NET Core 1.x apps in Visual Studio, [download and install Visual Studio 2017 RTM (version 15.0.26228.4) or higher](/visualstudio/install/install-visual-studio) with the **".NET Core cross-platform development"** workload (in the **Other Toolsets** section) selected.</span></span>

![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> <span data-ttu-id="6d4cc-159">.NET Core 1.x の開発に Visual Studio 2015 を使用することはできますが、次の理由からお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-159">It's possible to use Visual Studio 2015 for .NET Core 1.x development, but it's not recommended for the following reasons:</span></span>
  > * <span data-ttu-id="6d4cc-160">.NET Core Tooling は、サポートされていないプレビュー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-160">The .NET Core tooling is a preview version, which is not supported.</span></span>
  > * <span data-ttu-id="6d4cc-161">プロジェクトは、非推奨の project.json ベースです。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-161">The projects are project.json-based, which is deprecated.</span></span>
>
> <span data-ttu-id="6d4cc-162">プロジェクト形式の変更の詳細については、[変更点の概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-162">For more information about the project format changes, see [High-level overview of changes](./tools/cli-msbuild-architecture.md).</span></span>
---

> [!TIP]
> <span data-ttu-id="6d4cc-163">お使いの Visual Studio 2017 バージョンを確認するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-163">To verify your Visual Studio 2017 version:</span></span>
>
> * <span data-ttu-id="6d4cc-164">**[ヘルプ]** メニューの **[About Microsoft Visual Studio]** (Microsoft Visual Studio のバージョン情報) を選択します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-164">On the **Help** menu, choose **About Microsoft Visual Studio**.</span></span>
> * <span data-ttu-id="6d4cc-165">**[Microsoft Visual Studio のバージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-165">In the **About Microsoft Visual Studio** dialog, verify the version number.</span></span>
>   * <span data-ttu-id="6d4cc-166">.NET Core 2.1 RC アプリの場合は、Visual Studio 2017 バージョン 15.7 以降です。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-166">For .NET Core 2.1 RC apps, Visual Studio 2017 version 15.7 or higher.</span></span>
>   * <span data-ttu-id="6d4cc-167">.NET Core 2.0 アプリの場合は、Visual Studio 2017 バージョン 15.3 以降です。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-167">For .NET Core 2.0 apps, Visual Studio 2017 version 15.3 or higher.</span></span>
>   * <span data-ttu-id="6d4cc-168">.NET Core 1.x アプリの場合は、Visual Studio 2017 バージョン 15.0 以降です。</span><span class="sxs-lookup"><span data-stu-id="6d4cc-168">For .NET Core 1.x apps, Visual Studio 2017 version 15.0 or higher.</span></span>
