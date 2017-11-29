---
title: "方法 : FrameworkElement のサイズをアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="657ad-102">方法 : FrameworkElement のサイズをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="657ad-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="657ad-103">サイズをアニメーション化する、 <xref:System.Windows.FrameworkElement>、アニメーション化することができますか、その<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティまたはを使用して、アニメーション<xref:System.Windows.Media.ScaleTransform>です。</span><span class="sxs-lookup"><span data-stu-id="657ad-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="657ad-104">次の例では、これら 2 つの方法を使用して 2 つのボタンのサイズをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="657ad-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="657ad-105">アニメーション化により 1 つのボタンがサイズ変更、<xref:System.Windows.FrameworkElement.Width%2A>プロパティと別のアニメーションでサイズを変更、<xref:System.Windows.Media.ScaleTransform>に適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="657ad-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="657ad-106">各ボタンには、いくつかのテキストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="657ad-106">Each button contains some text.</span></span> <span data-ttu-id="657ad-107">最初に、両方のボタンで、同じテキストが表示されますが、2 番目のボタンのテキストになりますがゆがんで表示されるように、ボタンのサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="657ad-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="657ad-108">例</span><span class="sxs-lookup"><span data-stu-id="657ad-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="657ad-109">要素を変換する場合は、全体の要素とその内容が変換されます。</span><span class="sxs-lookup"><span data-stu-id="657ad-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="657ad-110">場合の最初のボタンのように、要素のサイズを直接変更するときに、そのサイズと位置がその親要素のサイズに依存しない限り、要素の内容はサイズ変更されません。</span><span class="sxs-lookup"><span data-stu-id="657ad-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="657ad-111">要素のサイズをアニメーション化するアニメーションの変換を適用することでその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティをアニメーションより優れたパフォーマンスを提供するその<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>を直接ため、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティでは、レイアウト パスは発生しません。</span><span class="sxs-lookup"><span data-stu-id="657ad-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="657ad-112">プロパティをアニメーション化の詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="657ad-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="657ad-113">変換の詳細については、次を参照してください。、[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="657ad-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
