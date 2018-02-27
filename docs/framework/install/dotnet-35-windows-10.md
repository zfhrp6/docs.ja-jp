---
title: "Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール"
description: "Windows 10、Windows 8.1、および Windows 8 に .NET Framework 3.5 をインストールする方法について説明します"
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="b9f22-103">Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール</span><span class="sxs-lookup"><span data-stu-id="b9f22-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="b9f22-104">Windows 10、Windows 8.1、および Windows 8 上でアプリケーションを実行するために、.NET Framework 3.5 が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9f22-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="b9f22-105">また、さらに古いバージョンの Windows にもこれらの手順を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9f22-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="b9f22-106">必要に応じて .NET Framework 3.5 をインストールする</span><span class="sxs-lookup"><span data-stu-id="b9f22-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="b9f22-107">.NET Framework 3.5 が必要なアプリケーションを実行しようとすると、次の構成ダイアログが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="b9f22-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="b9f22-108">.NET Framework 3.5 を有効にするには、**[この機能をインストールする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b9f22-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="b9f22-109">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9f22-109">This option requires an Internet connection.</span></span>

![.NET Framework のインストール ダイアログ](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="b9f22-111">コントロール パネルで .NET Framework 3.5 を有効にする</span><span class="sxs-lookup"><span data-stu-id="b9f22-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="b9f22-112">Windows のコントロール パネルを使用して .NET Framework 3.5 を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="b9f22-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="b9f22-113">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="b9f22-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="b9f22-114">キーボードの Windows キー ![Windows ロゴ](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) を押し、「Windows の機能」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b9f22-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="b9f22-115">**[Windows 機能の有効化または無効化]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9f22-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="b9f22-116">**[.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)]** チェック ボックスをオンにして **[OK]** を選択し、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b9f22-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![コントロール パネルを使用した .NET のインストール](./media/dotnet-control-panel.png)

   <span data-ttu-id="b9f22-118">Windows Communication Foundation (WCF) 機能が必要な開発者またはサーバー管理者でない限り、**[Windows Communication Foundation HTTP アクティブ化]** および **[Windows Communication Foundation 非 HTTP アクティブ化]**の子項目を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b9f22-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="b9f22-119">.NET Framework 3.5 のインストールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b9f22-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="b9f22-120">インストール中にエラー 0x800f0906、0x800f0907、0x800f081f、0x800F0922 が発生することがあります。その場合は、「[.NET Framework 3.5 インストール エラー: 0x800f0906、0x800f0907、または 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09)」を参照し、問題の解決方法をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="b9f22-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="b9f22-121">前の記事で紹介した方法がいずれも失敗した場合、またはインターネット接続がない場合は、Windows のインストール メディアを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9f22-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="b9f22-122">詳細については、「[Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism)」 (展開イメージのサービスと管理 (DISM) を利用して .NET Framework 3.5 を展開する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9f22-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="b9f22-123">インストール メディアがない場合は、「[Windows 用のインストール メディアを作成する](https://support.microsoft.com/help/15088/windows-create-installation-media)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9f22-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
