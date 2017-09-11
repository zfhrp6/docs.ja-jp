---
title: "Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール"
ms.date: 05/26/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework 3.5, installing on Windows 8
- Windows 8, installing .NET Framework 3.5
ms.assetid: 3eab3eb4-4573-42ac-98f8-36fb2c22c7d5
caps.latest.revision: 69
author: mairaw
ms.author: mairaw
ms.translationtype: HT
ms.sourcegitcommit: 93f77dd5c3ca61935ae98ddef15f9c5cf7644bbb
ms.openlocfilehash: e9c8dcfacff689761d9ec891db8a1a4756acece0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/23/2017

---

# <a name="install-the-net-framework-35-on-windows-8-windows-81-and-windows-10"></a><span data-ttu-id="0cf2d-102">Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール</span><span class="sxs-lookup"><span data-stu-id="0cf2d-102">Install the .NET Framework 3.5 on Windows 8, Windows 8.1, and Windows 10</span></span>

<span data-ttu-id="0cf2d-103">.NET Framework は、Windows 上で実行されている多数のアプリケーションに不可欠な部分であり、それらのアプリケーションが稼働するための共通の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-103">The .NET Framework is an integral part of many apps running on Windows and provides common functionality for those apps to run.</span></span> <span data-ttu-id="0cf2d-104">開発者に対し、.NET Framework はアプリケーションを作成するための一貫したプログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-104">For developers, the .NET Framework provides a consistent programming model for building apps.</span></span> <span data-ttu-id="0cf2d-105">Windows オペレーティング システムを使用している場合は、.NET Framework がコンピューターに既にインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-105">If you're using the Windows operating system, the .NET Framework may already be installed on your computer.</span></span> <span data-ttu-id="0cf2d-106">具体的には、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には [!INCLUDE[win8](../../../includes/win8-md.md)]が組み込まれており、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] には [!INCLUDE[win81](../../../includes/win81-md.md)] が組み込まれており、Windows 10 には [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-106">Specifically, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is included with [!INCLUDE[win8](../../../includes/win8-md.md)], the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] is included with [!INCLUDE[win81](../../../includes/win81-md.md)], and the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] is included with Windows 10.</span></span>  
  
<span data-ttu-id="0cf2d-107">ただし、.NET Framework 3.5 は [!INCLUDE[win8](../../../includes/win8-md.md)]、[!INCLUDE[win81](../../../includes/win81-md.md)]、または Windows 10 と一緒に自動的にインストールされません。これに依存するアプリケーションを実行するには、.NET Framework 3.5 を別途有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-107">The .NET Framework 3.5, however, is not automatically installed with [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], or Windows 10, and must be separately enabled to run apps that depend on it.</span></span> <span data-ttu-id="0cf2d-108">これは、3 つの方法のいずれかで呼び出される、Windows Update を使用して行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-108">This must happen through Windows Update, which is invoked in one of three ways.</span></span> <span data-ttu-id="0cf2d-109">以下の方法はすべて、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-109">All of these require an Internet connection:</span></span>  
  
- [<span data-ttu-id="0cf2d-110">必要に応じて .NET Framework 3.5 をインストールする</span><span class="sxs-lookup"><span data-stu-id="0cf2d-110">Install the .NET Framework 3.5 on Demand</span></span>](#OnDemand)  
  
- [<span data-ttu-id="0cf2d-111">コントロール パネルで .NET Framework 3.5 を有効にする</span><span class="sxs-lookup"><span data-stu-id="0cf2d-111">Enable the .NET Framework 3.5 in Control Panel</span></span>](#ControlPanel)  
  
- <span data-ttu-id="0cf2d-112">[.NET Framework 3.5 インストーラーをダウンロードする](http://www.microsoft.com/en-us/download/details.aspx?id=21) (注: これは .NET Framework を直接ダウンロードするのでなく、Windows Update を呼び出すインストーラーです)。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-112">[Download the .NET Framework 3.5 installer](http://www.microsoft.com/en-us/download/details.aspx?id=21) (Note: This does not download the .NET Framework directly; it is an installer that invokes Windows Update.)</span></span>  
  
<span data-ttu-id="0cf2d-113">インストール中にエラー 0x800f0906、0x800f0907、または 0x800f081f が発生することがあります。その場合は、「[.NET Framework 3.5 インストール エラー: 0x800f0906、0x800f0907、または 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-113">During installation, you may encounter error 0x800f0906, 0x800f0907, or 0x800f081f, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09).</span></span> <span data-ttu-id="0cf2d-114">なお、これらのエラーは、 [セキュリティ更新プログラム 3005628](https://support.microsoft.com/kb/3005628)をインストールすれば解決することがあります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-114">Note that these are possibly resolved by installing [security update 3005628](https://support.microsoft.com/kb/3005628).</span></span>  
  
<span data-ttu-id="0cf2d-115">前述の方法がいずれも失敗した場合、またはインターネット接続がない場合は、Windows のインストール メディアを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-115">If any of the above methods fail or if you do not have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="0cf2d-116">詳細については、 [.NET Framework 3.5 のインストール エラーに関する記事](https://support.microsoft.com/en-us/kb/2734782)に記載されているエラー 0x800f0906 用の方法 3 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-116">For details, see Method 3 for error 0x800f0906 in the [.NET Framework 3.5 installation error article](https://support.microsoft.com/en-us/kb/2734782).</span></span> <span data-ttu-id="0cf2d-117">インストール メディアがいない場合は、「[Windows 8.1 用のインストール メディアを作成する](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-117">If you don't have installation media, see [Create Installation media for Windows 8.1](http://windows.microsoft.com/en-US/windows-8/create-reset-refresh-media?woldogcb=0).</span></span>  
  
<span data-ttu-id="0cf2d-118">**重要なメモ:**</span><span class="sxs-lookup"><span data-stu-id="0cf2d-118">**Important notes:**</span></span>
  
- <span data-ttu-id="0cf2d-119">通常は、コンピューターからすべてのバージョンの .NET Framework をアンインストールしないでください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-119">In general, don't uninstall any versions of the .NET Framework from your computer.</span></span> <span data-ttu-id="0cf2d-120">アプリごとに異なるバージョンのフレームワークに依存していることがあり、.NET Framework の複数のバージョンが 1 台のコンピューターに共存することができます。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-120">Different apps depend on different versions of the framework, and multiple versions of the .NET Framework can coexist on a single computer at the same time.</span></span>  
  
- <span data-ttu-id="0cf2d-121">.NET Framework 3.5 は、バージョン 2.0 および 3.0 用にビルドされたアプリでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-121">The .NET Framework 3.5 is also used by apps built for versions 2.0 and 3.0.</span></span>  
  
- <span data-ttu-id="0cf2d-122">.NET Framework 3.5 をインストールする前に Windows の言語パックをインストールすると、.NET Framework 3.5 のインストールが失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-122">Installing a Windows language pack before installing the .NET Framework 3.5 may cause the .NET Framework 3.5 installation to fail.</span></span> <span data-ttu-id="0cf2d-123">Windows の言語パックをインストールする前に .NET Framework 3.5 をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-123">Install the .NET Framework 3.5 before installing any Windows language packs.</span></span>  
  
- <span data-ttu-id="0cf2d-124">Windows CardSpace は [!INCLUDE[win8](../../../includes/win8-md.md)]の .NET Framework 3.5 では使用できません。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-124">Windows CardSpace is not available with the .NET Framework 3.5 on [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span>  
  
- <span data-ttu-id="0cf2d-125">.NET Framework 3.5 のインストール方法については複雑であるため、残念ながら Windows Update とは独立して実行可能なスタンドアロン インストーラーを個別に提供することはできません。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-125">Because of complications around how the .NET Framework 3.5 must be installed, it's unfortunately not possible to provide a separate, standalone installer that can run independently of Windows Update.</span></span> <span data-ttu-id="0cf2d-126">その他の方法がすべて失敗した場合は、前述したインストール メディアを使用してください。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-126">If all other methods fail, you must resort to installation media as described earlier.</span></span>  
  
<a name="OnDemand"></a>   
## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="0cf2d-127">必要に応じて .NET Framework 3.5 をインストールする</span><span class="sxs-lookup"><span data-stu-id="0cf2d-127">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="0cf2d-128">アプリに .NET Framework 3.5 が必要でも、コンピューター上でこのバージョンが有効化されていることを検出できない場合、インストール中またはアプリの初回起動時に次のメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-128">If an app requires the .NET Framework 3.5 but doesn't find that version enabled on your computer, it displays the following message box, either during installation or when you run the app for the first time.</span></span> <span data-ttu-id="0cf2d-129">.NET Framework 3.5 を有効にするには、このメッセージ ボックスの **[Install this feature]** (この機能のインストール) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-129">In the message box, choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="0cf2d-130">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-130">This option requires an Internet connection.</span></span>  
  
<span data-ttu-id="0cf2d-131">![Windows 8 に 3.5 をインストールするためのダイアログ ボックス](../../../docs/framework/deployment/media/installdialog.png "installdialog")</span><span class="sxs-lookup"><span data-stu-id="0cf2d-131">![Dialog box for 3.5 install on Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")</span></span>  
  
<a name="ControlPanel"></a>   
## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="0cf2d-132">コントロール パネルで .NET Framework 3.5 を有効にする</span><span class="sxs-lookup"><span data-stu-id="0cf2d-132">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="0cf2d-133">コントロール パネルを使用して .NET Framework 3.5 を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-133">You can enable the .NET Framework 3.5 through Control Panel.</span></span> <span data-ttu-id="0cf2d-134">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-134">This option requires an Internet connection.</span></span>  
  
1. <span data-ttu-id="0cf2d-135">キーボードの Windows キー ![Windows ロゴ](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") を押します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-135">Press the Windows key ![Windows logo](../../../docs/framework/get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo") on your keyboard.</span></span> <span data-ttu-id="0cf2d-136">「Windows の機能」と入力して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-136">Type "Windows Features" and press Enter.</span></span> <span data-ttu-id="0cf2d-137">**[Windows の機能の有効化または無効化]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-137">This brings up the **Turn Windows features on or off** dialog box.</span></span> <span data-ttu-id="0cf2d-138">あるいは、[コントロール パネル] を開き、**[プログラム]** の項目をクリックし、**[プログラムと機能]** で **[Windows の機能の有効化または無効化]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-138">Alternately, open Control Panel, click on the **Programs** items, and then select **Turn Windows features on or off** under **Programs and Features**.</span></span>  
  
2. <span data-ttu-id="0cf2d-139">**[.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)]** チェック ボックスをオンにして **[OK]** を選択し、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-139">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>  
  
<span data-ttu-id="0cf2d-140">WCF スクリプトおよびハンドラー マッピングの機能を必要とする開発者でない限り、**Windows Communication Foundation (WCF) HTTP アクティブ化**用に子項目を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0cf2d-140">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP activation** unless you're a developer who requires WCF script and handler mapping functionality.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0cf2d-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf2d-141">See also</span></span>

[<span data-ttu-id="0cf2d-142">インストール ガイド</span><span class="sxs-lookup"><span data-stu-id="0cf2d-142">Installation Guide</span></span>](../../../docs/framework/get-started/index.md)

