---
title: "Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール"
description: "Windows 10、Windows 8.1、および Windows 8 に .NET Framework 3.5 をインストールする方法について説明します"
author: rlander
ms.author: mairaw
keywords: ".Net Framework, インストール"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.translationtype: HT
ms.sourcegitcommit: 21c6a1485f3d0c38bde065d6ecc7b07d5e424c1d
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/05/2017

---

# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="5873e-104">Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール</span><span class="sxs-lookup"><span data-stu-id="5873e-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="5873e-105">Windows 10、Windows 8.1、および Windows 8 上でアプリケーションを実行するために、.NET Framework 3.5 が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="5873e-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="5873e-106">また、さらに古いバージョンの Windows にもこれらの手順を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5873e-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="5873e-107">必要に応じて .NET Framework 3.5 をインストールする</span><span class="sxs-lookup"><span data-stu-id="5873e-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="5873e-108">.NET Framework 3.5 が必要なアプリケーションを実行しようとすると、次の構成ダイアログが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="5873e-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="5873e-109">.NET Framework 3.5 を有効にするには、**[この機能をインストールする]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5873e-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="5873e-110">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="5873e-110">This option requires an Internet connection.</span></span>

![.NET Framework のインストール ダイアログ](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="5873e-112">コントロール パネルで .NET Framework 3.5 を有効にする</span><span class="sxs-lookup"><span data-stu-id="5873e-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="5873e-113">Windows のコントロール パネルを使用して .NET Framework 3.5 を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="5873e-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="5873e-114">このオプションを使用するには、インターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="5873e-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="5873e-115">キーボードの Windows キー ![Windows ロゴ](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) を押し、「Windows の機能」と入力して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5873e-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="5873e-116">**[Windows 機能の有効化または無効化]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5873e-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="5873e-117">**[.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)]** チェック ボックスをオンにして **[OK]** を選択し、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="5873e-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![コントロール パネルを使用した .NET のインストール](./media/dotnet-control-panel.png)

   <span data-ttu-id="5873e-119">Windows Communication Foundation (WCF) 機能が必要な開発者またはサーバー管理者でない限り、**[Windows Communication Foundation HTTP アクティブ化]** および **[Windows Communication Foundation 非 HTTP アクティブ化]**の子項目を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5873e-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

