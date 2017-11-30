---
title: ".NET Framework を使用したクライアント アプリケーションの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daf09f94b4c0854365274773f8c426cc07e8c6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="32744-102">.NET Framework を使用したクライアント アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="32744-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="32744-103">ユーザーのコンピューターやデバイスでローカルに動作する .NET Framework で、Windows ベースのアプリケーションを開発する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="32744-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="32744-104">このセクションには、Windows Presentation Foundation (WPF) または Windows Forms を使用して Windows ベースのアプリケーションを作成する方法について説明しているトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="32744-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="32744-105">ただし、.NET Framework を使用して Web アプリケーションを作成したり、コンピューターやデバイス向けのクライアント アプリケーションを作成したりして、Windows ストアおよび Windows Phone ストアで公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="32744-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="32744-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="32744-106">In This Section</span></span>  
 [<span data-ttu-id="32744-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="32744-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="32744-108">WPF を使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="32744-109">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="32744-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="32744-110">Windows フォームを使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="32744-111">共通クライアント技術</span><span class="sxs-lookup"><span data-stu-id="32744-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="32744-112">クライアント アプリケーションを開発する場合に使用できる、その他の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32744-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="32744-113">Related Sections</span></span>  
 [<span data-ttu-id="32744-114">Windows ストア アプリ</span><span class="sxs-lookup"><span data-stu-id="32744-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="32744-115">Windows ストアを介してユーザーが利用できるアプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="32744-116">ストア アプリ用 .NET</span><span class="sxs-lookup"><span data-stu-id="32744-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="32744-117">Windows コンピューターとデバイスに展開できるストア アプリ用 .NET Framework のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="32744-118">[Windows Phone Silverlight 用の .NET API](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="32744-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="32744-119">Windows Phone Silverlight を使用したアプリを構築するために利用できる .NET Framework API の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="32744-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="32744-120">複数のプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="32744-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="32744-121">複数の種類のクライアント アプリを対象にするために .NET Framework を使用できるさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="32744-122">ASP.NET Web サイト入門</span><span class="sxs-lookup"><span data-stu-id="32744-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="32744-123">ASP.NET を使用して Web アプリを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32744-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32744-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="32744-124">See Also</span></span>  
 [<span data-ttu-id="32744-125">ポータブル クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="32744-125">Portable Class Library</span></span>](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)  
 [<span data-ttu-id="32744-126">概要</span><span class="sxs-lookup"><span data-stu-id="32744-126">Overview</span></span>](../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="32744-127">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="32744-127">Development Guide</span></span>](../../docs/framework/development-guide.md)  
 [<span data-ttu-id="32744-128">方法: Windows デスクトップ アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="32744-128">How to: Create a Windows Desktop Application</span></span>](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148)  
 [<span data-ttu-id="32744-129">Windows サービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="32744-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)
