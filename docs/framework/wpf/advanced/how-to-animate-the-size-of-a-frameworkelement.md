---
title: '方法 : FrameworkElement のサイズをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: 148e3d592e129984bd2f7ac062340c5169e48d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543986"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a><span data-ttu-id="e78c4-102">方法 : FrameworkElement のサイズをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="e78c4-102">How to: Animate the Size of a FrameworkElement</span></span>
<span data-ttu-id="e78c4-103">サイズをアニメーション化する、 <xref:System.Windows.FrameworkElement>、アニメーション化することができますか、その<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティまたはを使用して、アニメーション<xref:System.Windows.Media.ScaleTransform>です。</span><span class="sxs-lookup"><span data-stu-id="e78c4-103">To animate the size of a <xref:System.Windows.FrameworkElement>, you can either animate its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties or use an animated <xref:System.Windows.Media.ScaleTransform>.</span></span>  
  
 <span data-ttu-id="e78c4-104">次の例では、これら 2 つの方法を使用して 2 つのボタンのサイズをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="e78c4-104">In the following example animates the size of two buttons using these two approaches.</span></span> <span data-ttu-id="e78c4-105">アニメーション化により 1 つのボタンがサイズ変更、<xref:System.Windows.FrameworkElement.Width%2A>プロパティと別のアニメーションでサイズを変更、<xref:System.Windows.Media.ScaleTransform>に適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e78c4-105">One button is resized by animating its <xref:System.Windows.FrameworkElement.Width%2A> property and another is resized by animating a <xref:System.Windows.Media.ScaleTransform> applied to its <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="e78c4-106">各ボタンには、いくつかのテキストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e78c4-106">Each button contains some text.</span></span> <span data-ttu-id="e78c4-107">最初に、両方のボタンで、同じテキストが表示されますが、2 番目のボタンのテキストになりますがゆがんで表示されるように、ボタンのサイズが変更されます。</span><span class="sxs-lookup"><span data-stu-id="e78c4-107">Initially, the text appears the same in both buttons, but as the buttons are resized, the text in the second button becomes distorted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e78c4-108">例</span><span class="sxs-lookup"><span data-stu-id="e78c4-108">Example</span></span>  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 <span data-ttu-id="e78c4-109">要素を変換する場合は、全体の要素とその内容が変換されます。</span><span class="sxs-lookup"><span data-stu-id="e78c4-109">When you transform an element, the entire element and its contents are transformed.</span></span> <span data-ttu-id="e78c4-110">場合の最初のボタンのように、要素のサイズを直接変更するときに、そのサイズと位置がその親要素のサイズに依存しない限り、要素の内容はサイズ変更されません。</span><span class="sxs-lookup"><span data-stu-id="e78c4-110">When you directly alter the size of an element, as in the case of the first button, the element's contents are not resized unless their size and position depend on the size of their parent element.</span></span>  
  
 <span data-ttu-id="e78c4-111">要素のサイズをアニメーション化するアニメーションの変換を適用することでその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティをアニメーションより優れたパフォーマンスを提供するその<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>を直接ため、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティでは、レイアウト パスは発生しません。</span><span class="sxs-lookup"><span data-stu-id="e78c4-111">Animating the size of an element by applying an animated transform to its <xref:System.Windows.UIElement.RenderTransform%2A> property provides better performance than animated its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> directly, because the <xref:System.Windows.UIElement.RenderTransform%2A> property does not trigger a layout pass.</span></span>  
  
 <span data-ttu-id="e78c4-112">プロパティをアニメーション化の詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="e78c4-112">For more information about animating properties, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="e78c4-113">変換の詳細については、次を参照してください。、[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="e78c4-113">For more information about transforms, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>
