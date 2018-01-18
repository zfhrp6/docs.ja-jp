---
title: "Windows XP への .NET Framework のインストール"
description: "Windows XP に .NET Framework をインストールする方法について説明します。"
author: rlander
ms.author: mairaw
keywords: ".Net Framework, インストール"
ms.date: 08/03/2017
ms.topic: article
ms.prod: .net-framework
ms.devlang: dotnet
ms.workload: dotnet
ms.openlocfilehash: 83def2091cf1fdc7d3d359c98aa3116a009d465d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="install-the-net-framework-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="d2f6a-104">Windows XP と Windows Server 2003 に .NET Framework をインストールする</span><span class="sxs-lookup"><span data-stu-id="d2f6a-104">Install the .NET Framework on Windows XP and Windows Server 2003</span></span>

> [!NOTE]
> <span data-ttu-id="d2f6a-105">Microsoft では、Windows XP のサポートを終了しました。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-105">Windows XP is no longer supported by Microsoft.</span></span> <span data-ttu-id="d2f6a-106">サポート対象の Windows 10 にアップグレードすることをお勧めします。Windows 10 には最新バージョンの .NET Framework が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-106">We recommend you upgrade to Windows 10, which is supported and includes the latest version of the .NET Framework.</span></span> <span data-ttu-id="d2f6a-107">このドキュメントは、役に立つトラブルシューティング ガイドという目的でのみ提供されています。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-107">This document is provided solely as a helpful troubleshooting guide.</span></span>

<span data-ttu-id="d2f6a-108">.NET Framework は、Windows でさまざまなアプリケーションを実行するために必要です。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-108">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="d2f6a-109">次の手順を使用してインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-109">You can use the following instructions to install it.</span></span> <span data-ttu-id="d2f6a-110">このページをご覧になっている理由は、アプリケーションを実行しようとして次のようなダイアログがコンピューターに表示されたからではないでしょうか。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-110">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![このアプリケーションを開始できませんでした。](./media/this-application-could-not-be-started.png)

<span data-ttu-id="d2f6a-112">これらの手順は、必要な .NET Framework バージョンをインストールする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-112">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="d2f6a-113">[.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) が最新バージョンです。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-113">The [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) is the latest version.</span></span> <span data-ttu-id="d2f6a-114">Windows XP と Windows Server 2003 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-114">It is not supported on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="d2f6a-115">[Windows 10 Fall Creators Update](https://www.microsoft.com/software-download/windows10) と [Windows Server 2016 Version 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-115">It is included with the [Windows 10 Fall Creators Update](https://www.microsoft.com/software-download/windows10) and [Windows Server 2016 Version 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709).</span></span>

## <a name="net-framework-403"></a><span data-ttu-id="d2f6a-116">.NET Framework 4.0.3</span><span class="sxs-lookup"><span data-stu-id="d2f6a-116">.NET Framework 4.0.3</span></span>

<span data-ttu-id="d2f6a-117">[.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) は Windows XP と Windows Server 2003 でサポートされている最も新しい .NET Framework バージョンです。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-117">The [.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) is the latest supported .NET Framework version on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="d2f6a-118">.NET Framework 4.0.3 をインストールするには、先に [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-118">The .NET Framework 4.0.3 requires that the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) is installed first.</span></span> <span data-ttu-id="d2f6a-119">Microsoft では、これらのバージョンの .NET Framework のサポートを終了しています。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-119">Both of these .NET Framework versions are no longer supported by Microsoft.</span></span>

## <a name="net-framework-4"></a><span data-ttu-id="d2f6a-120">.NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="d2f6a-120">.NET Framework 4</span></span>

<span data-ttu-id="d2f6a-121">Windows XP には [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-121">You can install the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span> <span data-ttu-id="d2f6a-122">Microsoft では、このバージョンのサポートを終了しています。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-122">It's no longer supported by Microsoft.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="d2f6a-123">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="d2f6a-123">.NET Framework 3.5</span></span>

<span data-ttu-id="d2f6a-124">Windows XP には [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-124">You can install the [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span>

<span data-ttu-id="d2f6a-125">.NET Framework 3.5 は、.NET Framework 1.0 から 3.5 用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2f6a-125">The .NET Framework 3.5 can be used to run applications built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2f6a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2f6a-126">See also</span></span>

<span data-ttu-id="d2f6a-127">[.NET Framework のダウンロード](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="d2f6a-127">[Download the .NET Framework](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="d2f6a-128">[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="d2f6a-128">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="d2f6a-129">開発者向けの .NET Framework のインストール</span><span class="sxs-lookup"><span data-stu-id="d2f6a-129">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
