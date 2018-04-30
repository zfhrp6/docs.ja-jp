---
title: 'チュートリアル : カスタム アニメーション ボタンの作成'
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
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10d723f8a685d76cc739ac88770aad3e1de982ca
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="a83ad-102">チュートリアル : カスタム アニメーション ボタンの作成</span><span class="sxs-lookup"><span data-stu-id="a83ad-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="a83ad-103">その名前からわかるように、Windows Presentation Foundation (WPF) は顧客の経験の豊富なプレゼンテーションを行うための優れたです。</span><span class="sxs-lookup"><span data-stu-id="a83ad-103">As its name suggests, Windows Presentation Foundation (WPF) is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="a83ad-104">これらのチュートリアルでは、(アニメーションを含む) ボタンの動作と外観をカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a83ad-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="a83ad-105">このカスタマイズを行う、スタイルとテンプレートを使用すると、このカスタム ボタンをアプリケーションで他のボタンに簡単に適用できます。</span><span class="sxs-lookup"><span data-stu-id="a83ad-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="a83ad-106">次の図を作成する場合、カスタマイズされたボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="a83ad-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="a83ad-107">![作成するカスタマイズされたボタン](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="a83ad-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="a83ad-108">ボタンの外観を構成するベクター グラフィックスを使用して作成される[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a83ad-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="a83ad-109"> 強力で拡張可能である点を除いて、HTML に似ています。</span><span class="sxs-lookup"><span data-stu-id="a83ad-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="a83ad-110"> Microsoft Visual Studio またはメモ帳を使用して手動で入力できるまたは Microsoft Expression Blend などのビジュアル デ ザイン ツールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a83ad-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="a83ad-111">Expression Blend は基になるを作成することで機能[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードは、両方のメソッドが、同じグラフィックスを作成するようにします。</span><span class="sxs-lookup"><span data-stu-id="a83ad-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a83ad-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a83ad-112">In This Section</span></span>  
 [<span data-ttu-id="a83ad-113">Microsoft Expression Blend を使用してボタンを作成する</span><span class="sxs-lookup"><span data-stu-id="a83ad-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="a83ad-114">Expression Blend のデザイナーの機能を使用して、カスタム動作を持つボタンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a83ad-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="a83ad-115">XAML を使用したボタンの作成</span><span class="sxs-lookup"><span data-stu-id="a83ad-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="a83ad-116">使用して、カスタム動作を持つボタンを作成する方法を示します[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]および Visual Studio です。</span><span class="sxs-lookup"><span data-stu-id="a83ad-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and Visual Studio.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a83ad-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a83ad-117">Related Sections</span></span>  
 [<span data-ttu-id="a83ad-118">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="a83ad-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="a83ad-119">スタイルとテンプレートを使用して、コントロールの動作と外観を決定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a83ad-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="a83ad-120">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="a83ad-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="a83ad-121">使用してオブジェクトをアニメーション化する方法について説明します、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アニメーションおよびタイミング システムです。</span><span class="sxs-lookup"><span data-stu-id="a83ad-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="a83ad-122">純色およびグラデーションによる塗りつぶしの概要</span><span class="sxs-lookup"><span data-stu-id="a83ad-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="a83ad-123">純色の線形グラデーション放射状グラデーションとペイントするブラシ オブジェクトを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a83ad-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="a83ad-124">ビットマップ効果の概要</span><span class="sxs-lookup"><span data-stu-id="a83ad-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="a83ad-125">サポートされているビットマップ効果について説明します[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]と、それらを適用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a83ad-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
