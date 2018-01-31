---
title: ".NET Framework を使用した Windows ベースのクライアント アプリケーションの開発"
ms.date: 01/09/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cfc8a0f176e3732e7fe6f088c9973bfbcdaf89a
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="eb364-102">.NET Framework を使用したクライアント アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="eb364-102">Developing client applications with the .NET Framework</span></span>

<span data-ttu-id="eb364-103">.NET Framework で Windows ベースのアプリケーションを開発する方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="eb364-103">There are several ways to develop Windows-based applications with the .NET Framework.</span></span> <span data-ttu-id="eb364-104">次のツールおよびフレームワークのいずれかを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="eb364-104">You can use any of these tools and frameworks:</span></span> 

* [<span data-ttu-id="eb364-105">ユニバーサル Windows プラットフォーム (UWP)</span><span class="sxs-lookup"><span data-stu-id="eb364-105">Universal Windows Platform (UWP)</span></span>](https://developer.microsoft.com/windows/apps)
* [<span data-ttu-id="eb364-106">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="eb364-106">Windows Presentation Foundation (WPF)</span></span>](../../docs/framework/wpf/index.md)
* [<span data-ttu-id="eb364-107">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="eb364-107">Windows Forms</span></span>](../../docs/framework/winforms/index.md)

<span data-ttu-id="eb364-108">このセクションには、Windows Presentation Foundation または Windows Forms を使用して Windows ベースのアプリケーションを作成する方法について説明しているトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="eb364-108">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation or by using Windows Forms.</span></span> <span data-ttu-id="eb364-109">ただし、.NET Framework を使用して Web アプリケーションを作成したり、コンピューターやデバイス向けのクライアント アプリケーションを作成したりして、Microsoft Store で公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="eb364-109">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Microsoft Store.</span></span>
 
## <a name="in-this-section"></a><span data-ttu-id="eb364-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eb364-110">In this section</span></span>

[<span data-ttu-id="eb364-111">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="eb364-111">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
<span data-ttu-id="eb364-112">WPF を使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-112">Provides information about developing applications by using WPF.</span></span>

[<span data-ttu-id="eb364-113">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="eb364-113">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
<span data-ttu-id="eb364-114">Windows フォームを使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-114">Provides information about developing applications by using Windows Forms.</span></span>

[<span data-ttu-id="eb364-115">共通クライアント技術</span><span class="sxs-lookup"><span data-stu-id="eb364-115">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
<span data-ttu-id="eb364-116">クライアント アプリケーションを開発する場合に使用できる、その他の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-116">Provides information about additional technologies that can be used when developing client applications.</span></span>

## <a name="related-sections"></a><span data-ttu-id="eb364-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb364-117">Related sections</span></span>

[<span data-ttu-id="eb364-118">ユニバーサル Windows プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="eb364-118">Universal Windows Platform</span></span>](https://developer.microsoft.com/windows/apps)  
<span data-ttu-id="eb364-119">Microsoft Store を介してユーザーが利用できる Windows 10 用のアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-119">Describes how to create applications for Windows 10 that you can make available to users through the Windows Store.</span></span>

[<span data-ttu-id="eb364-120">UWP アプリ用 .NET</span><span class="sxs-lookup"><span data-stu-id="eb364-120">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)  
<span data-ttu-id="eb364-121">Windows コンピューターとデバイスに展開できるストア アプリ用 .NET Framework のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-121">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>

<span data-ttu-id="eb364-122">[Windows Phone Silverlight 用の .NET API](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="eb364-122">[.NET API for Windows Phone Silverlight](https://docs.microsoft.com/en-us/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>  
<span data-ttu-id="eb364-123">Windows Phone Silverlight を使用したアプリを構築するために利用できる .NET Framework API の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="eb364-123">Lists the .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>
  
[<span data-ttu-id="eb364-124">複数のプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="eb364-124">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
<span data-ttu-id="eb364-125">複数の種類のクライアント アプリを対象にするために .NET Framework を使用できるさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-125">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>

[<span data-ttu-id="eb364-126">ASP.NET Web サイト入門</span><span class="sxs-lookup"><span data-stu-id="eb364-126">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
<span data-ttu-id="eb364-127">ASP.NET を使用して Web アプリを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb364-127">Describes the ways you can develop web apps using ASP.NET.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb364-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb364-128">See also</span></span>

[<span data-ttu-id="eb364-129">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="eb364-129">.NET Standard</span></span>](../../docs/standard/net-standard.md)  
[<span data-ttu-id="eb364-130">概要</span><span class="sxs-lookup"><span data-stu-id="eb364-130">Overview</span></span>](../../docs/framework/get-started/overview.md)  
[<span data-ttu-id="eb364-131">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="eb364-131">Development Guide</span></span>](../../docs/framework/development-guide.md)  
[<span data-ttu-id="eb364-132">Windows サービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="eb364-132">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)  
