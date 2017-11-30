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
ms.openlocfilehash: f79ae387b123527b3795a2e12a68bd153b308f81
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="install-the-net-framework-on-windows-xp-and-windows-server-2003"></a><span data-ttu-id="f7ef9-104">.NET Framework をインストールする Windows XP および Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="f7ef9-104">Install the .NET Framework on Windows XP and Windows Server 2003</span></span>

> [!NOTE]
> <span data-ttu-id="f7ef9-105">Microsoft では、Windows XP のサポートを終了しました。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-105">Windows XP is no longer supported by Microsoft.</span></span> <span data-ttu-id="f7ef9-106">サポートされており、.NET Framework の最新バージョンが含まれている Windows 10 にアップグレードすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-106">We recommend you upgrade to Windows 10, which is supported and includes the latest version of the .NET Framework.</span></span> <span data-ttu-id="f7ef9-107">このドキュメントは、役に立つトラブルシューティング ガイドという目的でのみ提供されています。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-107">This document is provided solely as a helpful troubleshooting guide.</span></span>

<span data-ttu-id="f7ef9-108">Windows で多くのアプリケーションを実行するには、.NET Framework が必要です。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-108">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="f7ef9-109">次の手順を使用すると、インストールします。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-109">You can use the following instructions to install it.</span></span> <span data-ttu-id="f7ef9-110">アプリケーションを実行しようとし、コンピューターに次のダイアログ ボックスを表示した後に、このページに到着したが可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-110">You may have arrived on this page after trying to run an application and seeing the following dialog on your machine.</span></span>

![このアプリケーションを開始できませんでした。](./media/this-application-could-not-be-started.png)

<span data-ttu-id="f7ef9-112">これらの手順では必要がある .NET Framework のバージョンをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-112">These instructions will help you install the .NET Framework versions you need.</span></span> <span data-ttu-id="f7ef9-113">[.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47)最新のバージョンであります。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-113">The [.NET Framework 4.7.1](https://www.microsoft.com/en-us/download/details.aspx?id=56115&desc=dotnet47) is the latest version.</span></span> <span data-ttu-id="f7ef9-114">Windows XP および Windows Server 2003 ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-114">It is not supported on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="f7ef9-115">付属しています、 [Windows 10 に収まる作成者 Update](https://www.microsoft.com/software-download/windows10)と[Windows Server 2016 バージョン 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)です。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-115">It is included with the [Windows 10 Fall Creators Update](https://www.microsoft.com/software-download/windows10) and [Windows Server 2016 Version 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709).</span></span>

## <a name="net-framework-403"></a><span data-ttu-id="f7ef9-116">.NET Framework 4.0.3</span><span class="sxs-lookup"><span data-stu-id="f7ef9-116">.NET Framework 4.0.3</span></span>

<span data-ttu-id="f7ef9-117">[.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) Windows XP および Windows Server 2003 で最新サポートされている .NET Framework バージョンです。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-117">The [.NET Framework 4.0.3](http://go.microsoft.com/fwlink/?LinkID=213834) is the latest supported .NET Framework version on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="f7ef9-118">.NET Framework 4.0.3 をインストールするには、先に [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-118">The .NET Framework 4.0.3 requires that the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834) is installed first.</span></span> <span data-ttu-id="f7ef9-119">Microsoft では、これらのバージョンの .NET Framework のサポートを終了しています。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-119">Both of these .NET Framework versions are no longer supported by Microsoft.</span></span>

## <a name="net-framework-4"></a><span data-ttu-id="f7ef9-120">.NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="f7ef9-120">.NET Framework 4</span></span>

<span data-ttu-id="f7ef9-121">Windows XP には [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-121">You can install the [.NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span> <span data-ttu-id="f7ef9-122">Microsoft では、このバージョンのサポートを終了しています。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-122">It's no longer supported by Microsoft.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="f7ef9-123">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f7ef9-123">.NET Framework 3.5</span></span>

<span data-ttu-id="f7ef9-124">Windows XP には [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-124">You can install the [.NET Framework 3.5](http://go.microsoft.com/fwlink/?LinkID=213834&dotnetdocs) on Windows XP.</span></span>

<span data-ttu-id="f7ef9-125">.NET Framework 3.5 は、.NET Framework 1.0 から 3.5 用に構築されたアプリケーションを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-125">The .NET Framework 3.5 can be used to run applications built for .NET Framework 1.0 through 3.5.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7ef9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7ef9-126">See also</span></span>

<span data-ttu-id="f7ef9-127">[.NET Framework をダウンロードします。](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="f7ef9-127">[Download the .NET Framework](https://www.microsoft.com/net/download/framework?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="f7ef9-128">[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="f7ef9-128">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="f7ef9-129">開発者にとっての .NET Framework をインストールします。</span><span class="sxs-lookup"><span data-stu-id="f7ef9-129">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
