---
title: Windows 10 への .NET Framework のインストール
description: Windows 10 または Windows Server 2016 に .NET Framework をインストールする方法について説明します。
author: rlander
ms.author: mairaw
ms.date: 04/10/2018
ms.custom: updateeachrelease
ms.openlocfilehash: cf374f9d1fd7e343e5eba868d3f686784428a2d0
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270449"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a><span data-ttu-id="2df88-103">Windows 10 と Windows Server 2016 に .NET Framework をインストールする</span><span class="sxs-lookup"><span data-stu-id="2df88-103">Install the .NET Framework on Windows 10 and Windows Server 2016</span></span>

<span data-ttu-id="2df88-104">.NET Framework は、Windows でさまざまなアプリケーションを実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="2df88-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="2df88-105">この記事の指示は、必要なバージョンの .NET Framework をインストールする際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2df88-105">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="2df88-106">最新版は [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) です。</span><span class="sxs-lookup"><span data-stu-id="2df88-106">The [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) is the latest available version.</span></span>

<span data-ttu-id="2df88-107">このページをご覧になっている理由は、アプリケーションを実行しようとして次のようなダイアログがコンピューターに表示されたからではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="2df88-107">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![このアプリケーションを開始できませんでした。](./media/this-application-could-not-be-started.png)

## <a name="net-framework-472"></a><span data-ttu-id="2df88-109">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="2df88-109">.NET Framework 4.7.2</span></span>

<span data-ttu-id="2df88-110">.NET Framework 4.7.2 は次の Windows に付属しています。</span><span class="sxs-lookup"><span data-stu-id="2df88-110">The .NET Framework 4.7.2 is included with:</span></span>

* [<span data-ttu-id="2df88-111">Windows 10 April 2018 Update</span><span class="sxs-lookup"><span data-stu-id="2df88-111">Windows 10 April 2018 Update</span></span>](https://www.microsoft.com/software-download/windows10)

> [!div class="button"]
[<span data-ttu-id="2df88-112">.NET Framework 4.7.2 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="2df88-112">Download .NET Framework 4.7.2</span></span>](https://www.microsoft.com/net/download/thank-you/net472?utm_source=ms-docs&utm_medium=referral)

<span data-ttu-id="2df88-113">[.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) は、.NET Framework 4.0 から 4.7.1 用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2df88-113">The [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) can be used to run applications built for the .NET Framework 4.0 through 4.7.1.</span></span>

<span data-ttu-id="2df88-114">[.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) は次の Windows にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="2df88-114">You can install the [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) on:</span></span>

* <span data-ttu-id="2df88-115">Windows 10 Fall Creators Update (バージョン 1709)</span><span class="sxs-lookup"><span data-stu-id="2df88-115">Windows 10 Fall Creators Update (version 1709)</span></span>
* <span data-ttu-id="2df88-116">Windows 10 Creators Update (バージョン 1703)</span><span class="sxs-lookup"><span data-stu-id="2df88-116">Windows 10 Creators Update (version 1703)</span></span>
* <span data-ttu-id="2df88-117">Windows 10 Anniversary Update (バージョン 1607)</span><span class="sxs-lookup"><span data-stu-id="2df88-117">Windows 10 Anniversary Update (version 1607)</span></span>
* <span data-ttu-id="2df88-118">Windows Server、バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="2df88-118">Windows Server, version 1709</span></span>
* <span data-ttu-id="2df88-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="2df88-119">Windows Server 2016</span></span>

<span data-ttu-id="2df88-120">.NET Framework 4.7.2 はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2df88-120">The .NET Framework 4.7.2 is not supported on:</span></span>

* <span data-ttu-id="2df88-121">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="2df88-121">Windows 10 1507</span></span>
* <span data-ttu-id="2df88-122">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="2df88-122">Windows 10 1511</span></span>

<span data-ttu-id="2df88-123">Windows 10 1507 または 1511 を使用しているとき、.NET Framework 4.7.2 をインストールする場合、それらより新しい Windows 10 バージョンに先にアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2df88-123">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.7.2, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-462"></a><span data-ttu-id="2df88-124">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2df88-124">.NET Framework 4.6.2</span></span>

<span data-ttu-id="2df88-125">[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) は Windows 10 1507 と 1511 でサポートされている最も新しい .NET Framework バージョンです。</span><span class="sxs-lookup"><span data-stu-id="2df88-125">The [.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="2df88-126">.NET Framework 4.6.2 は、.NET Framework 4.0 から 4.6.2 用に構築されたアプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2df88-126">The .NET Framework 4.6.2 supports apps built for the .NET Framework 4.0 through 4.6.2.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="2df88-127">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="2df88-127">.NET Framework 3.5</span></span>

<span data-ttu-id="2df88-128">手順に従って [.NET Framework 3.5 を Windows 10 に](dotnet-35-windows-10.md)インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="2df88-128">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="2df88-129">.NET Framework 3.5 は、.NET Framework 1.0 から 3.5 用に構築されたアプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2df88-129">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="2df88-130">追加情報</span><span class="sxs-lookup"><span data-stu-id="2df88-130">Additional information</span></span>

<span data-ttu-id="2df88-131">.NET Framework 4.x バージョンは、前のバージョンのインプレース更新です。</span><span class="sxs-lookup"><span data-stu-id="2df88-131">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="2df88-132">これは次のことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2df88-132">That means the following:</span></span>

- <span data-ttu-id="2df88-133">お使いのコンピューターにインストールできる .NET Framework 4.x バージョンは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="2df88-133">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="2df88-134">以降のバージョンが既にインストールされている場合、前のバージョンの .NET Framework をコンピューターにインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2df88-134">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="2df88-135">.NET Framework 4.x バージョンは、4.0 からそのバージョンまでの .NET Framework 用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2df88-135">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="2df88-136">たとえば、.NET Framework 4.7 は、.NET Framework 4.0 から 4.7 用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2df88-136">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="2df88-137">最新版 (.NET Framework 4.7.2) は、4.0 以降のすべての .NET Framework バージョンで構築されたアプリケーションの実行に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2df88-137">The latest version (the .NET Framework 4.7.2) can be used to run applications built with all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="2df88-138">ダウンロード可能な .NET Framework バージョンの一覧は、[.NET ダウンロード](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) ページでご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2df88-138">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="2df88-139">ヘルプ</span><span class="sxs-lookup"><span data-stu-id="2df88-139">Help</span></span>

<span data-ttu-id="2df88-140">正しいバージョンの .NET Framework をインストールできない場合、[Microsoft にお問い合わせください](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help)。</span><span class="sxs-lookup"><span data-stu-id="2df88-140">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="2df88-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="2df88-141">See also</span></span>

<span data-ttu-id="2df88-142">[.NET ダウンロード](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="2df88-142">[.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="2df88-143">[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="2df88-143">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="2df88-144">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="2df88-144">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
