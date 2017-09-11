---
title: "概要 (WPF) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF, getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 83c9c6fc754bcee3bb3a893ca21be21d169226cf
ms.contentlocale: ja-jp
ms.lasthandoff: 05/02/2017

---
# <a name="getting-started-wpf"></a><span data-ttu-id="5afc4-102">概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="5afc4-102">Getting Started (WPF)</span></span>
<span data-ttu-id="5afc4-103">Windows Presentation Foundation (WPF) は、デスクトップ クライアント アプリケーションを作成する UI フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="5afc4-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="5afc4-104">WPF の開発プラットフォームは、アプリケーション モデル、リソース、コントロール、グラフィックス、レイアウト、データ バインディング、ドキュメント、セキュリティなどのさまざまなアプリケーション開発機能の一式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5afc4-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="5afc4-105">WPF は .NET Framework のサブセットであるため、以前 ASP.NET や Windows フォームを使用して .NET Framework でアプリケーションを構築したことがあれば、プログラミングには馴染みがあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="5afc4-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="5afc4-106">WPF は、Extensible Application Markup Language (XAML) を使用して、アプリケーションのプログラミング用に、宣言型モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="5afc4-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="5afc4-107">このセクションには、WPF の紹介のトピックと、WPF の使用を開始するトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="5afc4-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="5afc4-108">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="5afc4-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5afc4-109">すぐに使用を開始したい</span><span class="sxs-lookup"><span data-stu-id="5afc4-109">I want to jump right in…</span></span>|[<span data-ttu-id="5afc4-110">チュートリアル: 初めての WPF デスクトップ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="5afc4-110">Walkthrough: My First WPF Desktop Application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="5afc4-111">アプリケーションの UI のデザイン方法</span><span class="sxs-lookup"><span data-stu-id="5afc4-111">How do I design the application UI?</span></span>|[<span data-ttu-id="5afc4-112">Visual Studio で XAML をデザインする</span><span class="sxs-lookup"><span data-stu-id="5afc4-112">Designing XAML in Visual Studio</span></span>](http://msdn.microsoft.com/library/288e2415-9fcf-408e-bc35-9848315e14fd)|  
|<span data-ttu-id="5afc4-113">.NET の初心者向け</span><span class="sxs-lookup"><span data-stu-id="5afc4-113">New to .NET?</span></span>|<span data-ttu-id="5afc4-114">[.NET Framework の概要](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5afc4-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="5afc4-115">.NET Framework アプリケーションの基本事項</span><span class="sxs-lookup"><span data-stu-id="5afc4-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="5afc4-116">[Visual C# と Visual Basic の概要](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="5afc4-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="5afc4-117">WPF の詳細な説明...</span><span class="sxs-lookup"><span data-stu-id="5afc4-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="5afc4-118">Visual Studio 2015 での WPF の概要</span><span class="sxs-lookup"><span data-stu-id="5afc4-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="5afc4-119">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="5afc4-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="5afc4-120">コントロール</span><span class="sxs-lookup"><span data-stu-id="5afc4-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="5afc4-121">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="5afc4-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="5afc4-122">Windows フォームの開発者向け</span><span class="sxs-lookup"><span data-stu-id="5afc4-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="5afc4-123">Windows フォーム コントロールおよび同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="5afc4-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="5afc4-124">WPF と Windows フォームの相互運用性</span><span class="sxs-lookup"><span data-stu-id="5afc4-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5afc4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="5afc4-125">See Also</span></span>  
 <span data-ttu-id="5afc4-126">[クラス ライブラリ (WPF)](../../../../docs/framework/wpf/class-library-wpf.md) </span><span class="sxs-lookup"><span data-stu-id="5afc4-126">[Class Library](../../../../docs/framework/wpf/class-library-wpf.md) </span></span>  
<span data-ttu-id="5afc4-127"> [アプリケーション開発](../../../../docs/framework/wpf/app-development/index.md) </span><span class="sxs-lookup"><span data-stu-id="5afc4-127"> [Application Development](../../../../docs/framework/wpf/app-development/index.md) </span></span>  
<span data-ttu-id="5afc4-128"> [.NET Framework デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=187437)</span><span class="sxs-lookup"><span data-stu-id="5afc4-128"> [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=187437)</span></span>
