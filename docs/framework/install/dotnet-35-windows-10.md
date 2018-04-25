---
title: Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール
description: Windows 10、Windows 8.1、および Windows 8 に .NET Framework 3.5 をインストールする方法について説明します
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: 09c4f81da76bb6608c3e579c442cf686ffab1688
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="f4300-103">Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール</span><span class="sxs-lookup"><span data-stu-id="f4300-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="f4300-104">Windows 10、Windows 8.1、および Windows 8 上でアプリケーションを実行するために、.NET Framework 3.5 が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f4300-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="f4300-105">また、さらに古いバージョンの Windows にもこれらの手順を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f4300-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="f4300-106">必要に応じて .NET Framework 3.5 をインストールする</span><span class="sxs-lookup"><span data-stu-id="f4300-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="f4300-107">.NET Framework 3.5 が必要なアプリケーションを実行しようとすると、次の構成ダイアログが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f4300-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="f4300-108">.NET Framework 3.5 を有効にするには、**[この機能をインストールする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4300-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="f4300-109">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4300-109">This option requires an Internet connection.</span></span>

![.NET Framework のインストール ダイアログ](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a><span data-ttu-id="f4300-111">このポップアップが表示される理由</span><span class="sxs-lookup"><span data-stu-id="f4300-111">Why am I getting this pop-up?</span></span>

<span data-ttu-id="f4300-112">.NET Framework は、Microsoft によって作成されており、アプリケーションの実行環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="f4300-112">The .NET Framework is created by Microsoft and provides an environment for running applications.</span></span> <span data-ttu-id="f4300-113">異なるバージョンを利用できます。</span><span class="sxs-lookup"><span data-stu-id="f4300-113">There are different versions available.</span></span> <span data-ttu-id="f4300-114">多くの企業は .NET Framework を使用して実行するようにアプリを開発しており、それらのアプリでは特定のバージョンが対象になっています。</span><span class="sxs-lookup"><span data-stu-id="f4300-114">Many companies develop their apps to run using the .NET Framework, and these apps target a specific version.</span></span> <span data-ttu-id="f4300-115">このポップアップが表示される場合は、実行しようとしているアプリケーションでは .NET Framework バージョン 3.5 が必要ですが、そのバージョンがシステムにインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="f4300-115">If you see this pop-up, you're trying to run an application that requires the .NET Framework version 3.5, but that version is not installed on your system.</span></span>

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="f4300-116">コントロール パネルで .NET Framework 3.5 を有効にする</span><span class="sxs-lookup"><span data-stu-id="f4300-116">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="f4300-117">Windows のコントロール パネルを使用して .NET Framework 3.5 を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="f4300-117">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="f4300-118">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4300-118">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="f4300-119">キーボードの Windows キー ![Windows ロゴ](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) を押し、「Windows の機能」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f4300-119">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="f4300-120">**[Windows 機能の有効化または無効化]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4300-120">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="f4300-121">**[.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)]** チェック ボックスをオンにして **[OK]** を選択し、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f4300-121">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![コントロール パネルを使用した .NET のインストール](./media/dotnet-control-panel.png)

   <span data-ttu-id="f4300-123">Windows Communication Foundation (WCF) 機能が必要な開発者またはサーバー管理者でない限り、**[Windows Communication Foundation HTTP アクティブ化]** および **[Windows Communication Foundation 非 HTTP アクティブ化]** の子項目を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f4300-123">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="f4300-124">.NET Framework 3.5 のインストールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f4300-124">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="f4300-125">インストール中にエラー 0x800f0906、0x800f0907、0x800f081f、0x800F0922 が発生することがあります。その場合は、「[.NET Framework 3.5 インストール エラー: 0x800f0906、0x800f0907、または 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)」を参照し、問題の解決方法をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="f4300-125">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="f4300-126">インストールの問題をまだ解決できない場合、またはインターネット接続がない場合は、Windows のインストール メディアを使ってインストールしてみることができます。</span><span class="sxs-lookup"><span data-stu-id="f4300-126">If you still can't resolve your installation issue or you don't have an Internet connection, you can try installing it using your Windows installation media.</span></span> <span data-ttu-id="f4300-127">詳細については、「[Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism)」 (展開イメージのサービスと管理 (DISM) を利用して .NET Framework 3.5 を展開する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4300-127">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="f4300-128">インストール メディアがない場合は、「[Windows 用のインストール メディアを作成する](https://support.microsoft.com/help/15088/windows-create-installation-media)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4300-128">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
