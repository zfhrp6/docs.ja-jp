---
title: ".NET Framework および特別なリリース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c79326634a24ddcc9aed71fca018c69c36c94db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="the-net-framework-and-out-of-band-releases"></a><span data-ttu-id="3dbb5-102">.NET Framework および特別なリリース</span><span class="sxs-lookup"><span data-stu-id="3dbb5-102">The .NET Framework and Out-of-Band Releases</span></span>
<span data-ttu-id="3dbb5-103">.NET Framework は、従来のデスクトップ アプリや Web アプリに加えて、Windows Phone や Windows ストア アプリなど、さまざまなプラットフォームに対応し、コードを最大限に再利用できるように発展しています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-103">The .NET Framework is evolving to accommodate different platforms such as Windows Phone and Windows Store apps as well as traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="3dbb5-104">通常の .NET Framework のリリースに加えて、クロスプラットフォームでの開発の強化や新機能の導入を目的として、新しい機能をアウトオブバンド (OOB) リリースによって提供しています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-104">In addition to our regular .NET Framework releases, we release new features out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span> <span data-ttu-id="3dbb5-105">ここでは、.NET Framework および OOB リリースの将来の方向性について説明します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-105">This topic discusses the future direction of the .NET Framework and its OOB releases.</span></span>  
  
## <a name="advantages-of-oob-releases"></a><span data-ttu-id="3dbb5-106">OOB リリースの長所</span><span class="sxs-lookup"><span data-stu-id="3dbb5-106">Advantages of OOB releases</span></span>  
 <span data-ttu-id="3dbb5-107">新しいコンポーネントやコンポーネントに対する更新プログラムをアウトオブバンドで提供することにより、Microsoft では .NET Framework の更新プログラムをより頻繁に提供できます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-107">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to the .NET Framework.</span></span> <span data-ttu-id="3dbb5-108">また、カスタマーからのフィードバックにすばやく収集して対応できます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-108">In addition, we can gather and respond to customer feedback more quickly.</span></span>  
  
 <span data-ttu-id="3dbb5-109">独自のアプリで OOB 機能を使用する場合、OOB アセンブリはアプリのパッケージで配置されるため、ユーザーはアプリを実行するために最新バージョンの .NET Framework をインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-109">When you use an OOB feature in your app, your users do not have to install the latest version of the .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>  
  
## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="3dbb5-110">OOB パッケージの配布方法</span><span class="sxs-lookup"><span data-stu-id="3dbb5-110">How OOB packages are distributed</span></span>  
<span data-ttu-id="3dbb5-111">共通言語ランタイム (CLR) のコア コンポーネントの OOB リリースは、.NET 用パッケージ マネージャーである [NuGet](https://www.nuget.org/) を通じて配布されます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-111">OOB releases for core common language runtime (CLR) components are delivered through the [NuGet](https://www.nuget.org/), which is a package manager for .NET.</span></span> <span data-ttu-id="3dbb5-112">NuGet によって、Visual Studio のソリューション エクスプローラーから簡単に、.NET Framework プロジェクトを参照したり、ライブラリを追加したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-112">NuGet enables you to browse and add libraries to your .NET Framework projects easily from the Solution Explorer in Visual Studio.</span></span> <span data-ttu-id="3dbb5-113">NuGet は、Visual Studio 2012 以降のすべてのエディションに付属しています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-113">NuGet is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="3dbb5-114">NuGet がインストールされているかどうかを確認するには、Visual Studio の **[ツール]** メニューの **[ライブラリ パッケージ マネージャー]** を検索します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-114">To see if NuGet is installed, look for **Library Package Manager** on the Visual Studio **Tools** menu.</span></span> <span data-ttu-id="3dbb5-115">インストールされていない場合:</span><span class="sxs-lookup"><span data-stu-id="3dbb5-115">If it’s not installed:</span></span>  
  
1.  <span data-ttu-id="3dbb5-116">Visual Studio のメニュー バーで、**[ツール]**、**[拡張機能と更新プログラム]** を選択します (Visual Studio 2010 では、**[拡張機能マネージャー]** を選択します)。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-116">On the Visual Studio menu bar, choose **Tools**, **Extensions and Updates** (in Visual Studio 2010, choose **Extension Manager**).</span></span>  
  
     <span data-ttu-id="3dbb5-117">**[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-117">The **Extensions and Updates** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="3dbb5-118">**[オンライン]**、**[NuGet パッケージ マネージャー]** を選択し、**[ダウンロード]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-118">Choose **Online**, **NuGet Package Manager**, and then choose **Download**.</span></span>  
  
3.  <span data-ttu-id="3dbb5-119">ダウンロードが完了したら、Visual Studio を再起動します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-119">After the download completes, restart Visual Studio.</span></span>  
  
 <span data-ttu-id="3dbb5-120">詳細なインストール方法については、NuGet Docs Web サイトの「[Installing NuGet](http://docs.nuget.org/docs/start-here/installing-nuget)」(Nuget のインストール) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-120">For detailed installation instructions, see [Installing NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) on the NuGet Docs website.</span></span> <span data-ttu-id="3dbb5-121">NuGet の詳細については、[NuGet のドキュメント](http://docs.nuget.org/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-121">For more information about NuGet, see the [NuGet documentation](http://docs.nuget.org/).</span></span>  
  
## <a name="using-a-nuget-oob-package"></a><span data-ttu-id="3dbb5-122">NuGet OOB パッケージの使用</span><span class="sxs-lookup"><span data-stu-id="3dbb5-122">Using a NuGet OOB package</span></span>  
 <span data-ttu-id="3dbb5-123">NuGet をインストールした後、Visual Studio のソリューション エクスプローラーを使用して NuGet パッケージの表示や、NuGet パッケージへの参照の追加を行うことができます:</span><span class="sxs-lookup"><span data-stu-id="3dbb5-123">After you install NuGet, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>  
  
1.  <span data-ttu-id="3dbb5-124">Visual Studio でプロジェクトのショートカット メニューを開き、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-124">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="3dbb5-125">(このオプションは、**[プロジェクト]** メニューからも使用できます。)</span><span class="sxs-lookup"><span data-stu-id="3dbb5-125">(This option is also available from the **Project** menu.)</span></span>  
  
2.  <span data-ttu-id="3dbb5-126">左ペインで、**[オンライン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-126">In the left pane, choose **Online**.</span></span>  
  
3.  <span data-ttu-id="3dbb5-127">プレリリースのパッケージを使用する場合は、中央のペインのドロップダウン リスト ボックスで **[安定版パッケージのみ]** の代わりに **[リリース前のパッケージを含める]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-127">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>  
  
4.  <span data-ttu-id="3dbb5-128">右ペインで、**[検索]** ボックスを使用して使用するパッケージを検索します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-128">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="3dbb5-129">Microsoft の一部のパッケージは、Microsoft .NET Framework のロゴで識別され、すべて発行者は Microsoft となっています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-129">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>  
  
 <span data-ttu-id="3dbb5-130">![NuGet パッケージ マネージャー](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span><span class="sxs-lookup"><span data-stu-id="3dbb5-130">![NuGet Package Manager](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span></span>  
  
 <span data-ttu-id="3dbb5-131">OOB パッケージを使用するアプリケーションを配置する場合は、前述のとおり、OOB のアセンブリは、アプリのパッケージに付属しています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-131">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>  
  
## <a name="types-of-oob-releases"></a><span data-ttu-id="3dbb5-132">OOB のリリースの種類</span><span class="sxs-lookup"><span data-stu-id="3dbb5-132">Types of OOB releases</span></span>  
 <span data-ttu-id="3dbb5-133">通常、OOB パッケージには、1 つ以上のプレリリース バージョンと 1 つの安定したバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-133">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="3dbb5-134">プレリリースに含まれるライセンスでは通常、再配布は許可されませんが、パッケージを試用して、フィードバックを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-134">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="3dbb5-135">フィードバックはパッケージに対する更新プログラムに組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-135">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="3dbb5-136">最終リリースは NuGet を使って安定したパッケージとして配布され、アプリと共に NuGet パッケージを再配布できるライセンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-136">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="3dbb5-137">安定したパッケージは Microsoft によってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-137">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="3dbb5-138">Microsoft では、IntelliSense のサポートや、ブログの投稿、フォーラムでの回答などの別の種類のドキュメントを、すべてのパッケージについて提供します。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-138">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="3dbb5-139">また、すべてのパッケージではありませんが、一部のパッケージについてはソース コードも利用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-139">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="3dbb5-140">新しいパッケージや更新パッケージに関するお知らせについては、「[.NET Framework ブログ](http://blogs.msdn.com/b/dotnet/)」を受信登録できます。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-140">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](http://blogs.msdn.com/b/dotnet/).</span></span>  
  
 <span data-ttu-id="3dbb5-141">リリース前のパッケージと安定版パッケージの両方を検索するには、NuGet パッケージ マネージャーで **[リリース前のパッケージを含める]** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-141">To find both prerelease and stable packages, choose **Include Prerelease** in the NuGet Package Manager.</span></span>  
  
 <span data-ttu-id="3dbb5-142">安定版パッケージのリリースについて通知を受ける場合は、[the .NET Framework のフィード](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)を受信登録してください。</span><span class="sxs-lookup"><span data-stu-id="3dbb5-142">If you want to be notified of stable package releases, subscribe to the [the .NET Framework feed](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dbb5-143">参照</span><span class="sxs-lookup"><span data-stu-id="3dbb5-143">See Also</span></span>  
 [<span data-ttu-id="3dbb5-144">はじめに</span><span class="sxs-lookup"><span data-stu-id="3dbb5-144">Getting Started</span></span>](../../../docs/framework/get-started/index.md)
