---
title: WPF アプリケーションのパフォーマンスの最適化
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2de2d4009cb29c5e9cbdace0d69c220f95a54e1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="8a3ba-102">WPF アプリケーションのパフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="8a3ba-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="8a3ba-103">このセクションの目的は、参照用として[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション開発者が、アプリケーションのパフォーマンスを向上させる方法を探しています。</span><span class="sxs-lookup"><span data-stu-id="8a3ba-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="8a3ba-104">新しい Microsoft .NET Framework には、開発者がいるかどうかと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、おく必要があります最初に自分で両方のプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="8a3ba-104">If you are a developer who is new to the Microsoft .NET Framework and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="8a3ba-105">このセクションでは、両方の実用的な知識を前提としていてが既に実行して、アプリケーションを十分に把握するプログラマにとって書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8a3ba-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a3ba-106">このセクションで提供されるパフォーマンス データがに基づいて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]RAM および ATI Radeon 9700、512 で 2.8 GHz PC で実行されるアプリケーション グラフィックス カードです。</span><span class="sxs-lookup"><span data-stu-id="8a3ba-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a3ba-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8a3ba-107">In This Section</span></span>  
 [<span data-ttu-id="8a3ba-108">アプリケーション パフォーマンスの計画</span><span class="sxs-lookup"><span data-stu-id="8a3ba-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="8a3ba-109">ハードウェアの活用</span><span class="sxs-lookup"><span data-stu-id="8a3ba-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="8a3ba-110">レイアウトとデザイン</span><span class="sxs-lookup"><span data-stu-id="8a3ba-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="8a3ba-111">2D グラフィックスとイメージング</span><span class="sxs-lookup"><span data-stu-id="8a3ba-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="8a3ba-112">オブジェクトの動作</span><span class="sxs-lookup"><span data-stu-id="8a3ba-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="8a3ba-113">アプリケーション リソース</span><span class="sxs-lookup"><span data-stu-id="8a3ba-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 <span data-ttu-id="8a3ba-114">[[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)</span><span class="sxs-lookup"><span data-stu-id="8a3ba-114">[Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)</span></span>  
  
 [<span data-ttu-id="8a3ba-115">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="8a3ba-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="8a3ba-116">コントロール</span><span class="sxs-lookup"><span data-stu-id="8a3ba-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="8a3ba-117">パフォーマンスに関するその他の推奨事項</span><span class="sxs-lookup"><span data-stu-id="8a3ba-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="8a3ba-118">アプリケーションの起動時間</span><span class="sxs-lookup"><span data-stu-id="8a3ba-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="8a3ba-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a3ba-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="8a3ba-120">グラフィックスの描画層</span><span class="sxs-lookup"><span data-stu-id="8a3ba-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="8a3ba-121">WPF グラフィックス レンダリングの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="8a3ba-122">レイアウト</span><span class="sxs-lookup"><span data-stu-id="8a3ba-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="8a3ba-123">WPF のツリー</span><span class="sxs-lookup"><span data-stu-id="8a3ba-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="8a3ba-124">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="8a3ba-125">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="8a3ba-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="8a3ba-126">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="8a3ba-127">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="8a3ba-128">XAML リソース</span><span class="sxs-lookup"><span data-stu-id="8a3ba-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="8a3ba-129">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="8a3ba-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="8a3ba-130">書式設定されたテキストの描画</span><span class="sxs-lookup"><span data-stu-id="8a3ba-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="8a3ba-131">WPF のタイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="8a3ba-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="8a3ba-132">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="8a3ba-133">ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="8a3ba-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="8a3ba-134">アニメーションのヒントとテクニック</span><span class="sxs-lookup"><span data-stu-id="8a3ba-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="8a3ba-135">チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="8a3ba-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
