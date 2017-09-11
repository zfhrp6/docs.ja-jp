---
title: ".NET Framework を使用したクライアント アプリケーションの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
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
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: aba9547bcd96b9e8038bc973aa9ef971bb82f698
ms.openlocfilehash: 891c783429c069d7c807a9c31aff45d02f518eee
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="developing-client-applications-with-the-net-framework"></a><span data-ttu-id="395f5-102">.NET Framework を使用したクライアント アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="395f5-102">Developing Client Applications with the .NET Framework</span></span>
<span data-ttu-id="395f5-103">ユーザーのコンピューターやデバイスでローカルに動作する .NET Framework で、Windows ベースのアプリケーションを開発する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="395f5-103">There are multiple ways to develop Windows-based applications with the .NET framework that run locally on users' computers or devices.</span></span> <span data-ttu-id="395f5-104">このセクションには、Windows Presentation Foundation (WPF) または Windows Forms を使用して Windows ベースのアプリケーションを作成する方法について説明しているトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="395f5-104">This section contains topics that describe how to create Windows-based applications by using Windows Presentation Foundation (WPF) or by using Windows Forms.</span></span> <span data-ttu-id="395f5-105">ただし、.NET Framework を使用して Web アプリケーションを作成したり、コンピューターやデバイス向けのクライアント アプリケーションを作成したりして、Windows ストアおよび Windows Phone ストアで公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="395f5-105">However, you can also create web applications using the .NET Framework, and client applications for computers or devices that you make available through the Windows Store or Windows Phone Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="395f5-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="395f5-106">In This Section</span></span>  
 [<span data-ttu-id="395f5-107">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="395f5-107">Windows Presentation Foundation</span></span>](../../docs/framework/wpf/index.md)  
 <span data-ttu-id="395f5-108">WPF を使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-108">Provides information about developing applications by using WPF.</span></span>  
  
 [<span data-ttu-id="395f5-109">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="395f5-109">Windows Forms</span></span>](../../docs/framework/winforms/index.md)  
 <span data-ttu-id="395f5-110">Windows フォームを使用したアプリケーション開発の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-110">Provides information about developing applications by using Windows Forms.</span></span>  
  
 [<span data-ttu-id="395f5-111">共通クライアント技術</span><span class="sxs-lookup"><span data-stu-id="395f5-111">Common Client Technologies</span></span>](../../docs/framework/common-client-technologies/index.md)  
 <span data-ttu-id="395f5-112">クライアント アプリケーションを開発する場合に使用できる、その他の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-112">Provides information about additional technologies that can be used when developing client applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="395f5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="395f5-113">Related Sections</span></span>  
 [<span data-ttu-id="395f5-114">Windows ストア アプリ</span><span class="sxs-lookup"><span data-stu-id="395f5-114">Windows Store apps</span></span>](http://msdn.microsoft.com/windows/apps/)  
 <span data-ttu-id="395f5-115">Windows ストアを介してユーザーが利用できるアプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-115">Describes how to create apps that you can make available to users through the Windows Store</span></span>  
  
 [<span data-ttu-id="395f5-116">ストア アプリ用 .NET</span><span class="sxs-lookup"><span data-stu-id="395f5-116">.NET for Store apps</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 <span data-ttu-id="395f5-117">Windows コンピューターとデバイスに展開できるストア アプリ用 .NET Framework のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-117">Describes the .NET Framework support for Store apps, which can be deployed to Windows computers and devices.</span></span>  
  
 <span data-ttu-id="395f5-118">[Windows Phone Silverlight 用の .NET API](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="395f5-118">[.NET API for Windows Phone Silverlight](http://msdn.microsoft.com/library/windows/apps/xaml/jj207211\(v=vs.105\).aspx)</span></span>  
 <span data-ttu-id="395f5-119">Windows Phone Silverlight を使用したアプリを構築するために利用できる .NET Framework API の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="395f5-119">List the .NET Framework APIs you can use for building apps with Windows Phone Silverlight</span></span>  
  
 [<span data-ttu-id="395f5-120">複数のプラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="395f5-120">Developing for Multiple Platforms</span></span>](../../docs/standard/cross-platform/index.md)  
 <span data-ttu-id="395f5-121">複数の種類のクライアント アプリを対象にするために .NET Framework を使用できるさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-121">Describes the different methods you can use the .NET Framework to target multiple client app types.</span></span>  
  
 [<span data-ttu-id="395f5-122">ASP.NET Web サイト入門</span><span class="sxs-lookup"><span data-stu-id="395f5-122">Get Started with ASP.NET Web Sites</span></span>](http://www.asp.net/get-started/websites)  
 <span data-ttu-id="395f5-123">ASP.NET を使用して Web アプリを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="395f5-123">Describes the ways you can develop web apps using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395f5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="395f5-124">See Also</span></span>  
 <span data-ttu-id="395f5-125">[ポータブル クラス ライブラリ](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) </span><span class="sxs-lookup"><span data-stu-id="395f5-125">[Portable Class Library](../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) </span></span>  
 <span data-ttu-id="395f5-126">[概要](../../docs/framework/get-started/overview.md) </span><span class="sxs-lookup"><span data-stu-id="395f5-126">[Overview](../../docs/framework/get-started/overview.md) </span></span>  
 <span data-ttu-id="395f5-127">[開発ガイド](../../docs/framework/development-guide.md) </span><span class="sxs-lookup"><span data-stu-id="395f5-127">[Development Guide](../../docs/framework/development-guide.md) </span></span>  
 <span data-ttu-id="395f5-128">[方法: Windows デスクトップ アプリケーションの作成](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148) </span><span class="sxs-lookup"><span data-stu-id="395f5-128">[How to: Create a Windows Desktop Application](http://msdn.microsoft.com/library/47021403-eaca-4c34-946a-a26c42a64148) </span></span>  
 [<span data-ttu-id="395f5-129">Windows サービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="395f5-129">Windows Service Applications</span></span>](../../docs/framework/windows-services/index.md)

