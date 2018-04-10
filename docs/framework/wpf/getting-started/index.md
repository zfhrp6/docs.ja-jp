---
title: 概要 (WPF)
ms.custom: ''
ms.date: 01/26/2018
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eded6de5de269e7b49a87da31590267a5350f161
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="getting-started-wpf"></a><span data-ttu-id="e2fd9-102">概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2fd9-102">Getting Started (WPF)</span></span>
<span data-ttu-id="e2fd9-103">Windows Presentation Foundation (WPF) は、デスクトップ クライアント アプリケーションを作成する UI フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="e2fd9-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="e2fd9-104">WPF の開発プラットフォームは、アプリケーション モデル、リソース、コントロール、グラフィックス、レイアウト、データ バインディング、ドキュメント、セキュリティなどのさまざまなアプリケーション開発機能の一式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e2fd9-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="e2fd9-105">WPF は .NET Framework のサブセットであるため、以前 ASP.NET や Windows フォームを使用して .NET Framework でアプリケーションを構築したことがあれば、プログラミングには馴染みがあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="e2fd9-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="e2fd9-106">WPF は、Extensible Application Markup Language (XAML) を使用して、アプリケーションのプログラミング用に、宣言型モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="e2fd9-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="e2fd9-107">このセクションには、WPF の紹介のトピックと、WPF の使用を開始するトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="e2fd9-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="e2fd9-108">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="e2fd9-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2fd9-109">すぐに使用を開始したい</span><span class="sxs-lookup"><span data-stu-id="e2fd9-109">I want to jump right in…</span></span>|[<span data-ttu-id="e2fd9-110">チュートリアル: 初めての WPF デスクトップ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e2fd9-110">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="e2fd9-111">アプリケーションの UI のデザイン方法</span><span class="sxs-lookup"><span data-stu-id="e2fd9-111">How do I design the application UI?</span></span>|[<span data-ttu-id="e2fd9-112">Visual Studio で XAML をデザインする</span><span class="sxs-lookup"><span data-stu-id="e2fd9-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="e2fd9-113">.NET の初心者向け</span><span class="sxs-lookup"><span data-stu-id="e2fd9-113">New to .NET?</span></span>|<span data-ttu-id="e2fd9-114">[.NET Framework の概要](https://msdn.microsoft.com/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e2fd9-114">[Overview of the .NET Framework](https://msdn.microsoft.com/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="e2fd9-115">.NET Framework アプリケーションの基本事項</span><span class="sxs-lookup"><span data-stu-id="e2fd9-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="e2fd9-116">[Visual C# と Visual Basic の概要](https://msdn.microsoft.com/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e2fd9-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="e2fd9-117">WPF の詳細な説明...</span><span class="sxs-lookup"><span data-stu-id="e2fd9-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="e2fd9-118">Visual Studio での WPF の概要</span><span class="sxs-lookup"><span data-stu-id="e2fd9-118">Introduction to WPF in Visual Studio</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="e2fd9-119">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="e2fd9-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="e2fd9-120">コントロール</span><span class="sxs-lookup"><span data-stu-id="e2fd9-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="e2fd9-121">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="e2fd9-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="e2fd9-122">Windows フォームの開発者向け</span><span class="sxs-lookup"><span data-stu-id="e2fd9-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="e2fd9-123">Windows フォーム コントロールおよび同等の WPF コントロール</span><span class="sxs-lookup"><span data-stu-id="e2fd9-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="e2fd9-124">WPF と Windows フォームの相互運用性</span><span class="sxs-lookup"><span data-stu-id="e2fd9-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="e2fd9-125">参照</span><span class="sxs-lookup"><span data-stu-id="e2fd9-125">See Also</span></span>  
 [<span data-ttu-id="e2fd9-126">クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="e2fd9-126">Class Library</span></span>](../../../../docs/framework/wpf/class-library-wpf.md)  
 [<span data-ttu-id="e2fd9-127">アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="e2fd9-127">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
 [<span data-ttu-id="e2fd9-128">.NET Framework デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="e2fd9-128">.NET Framework Developer Center</span></span>](https://www.microsoft.com/net)
