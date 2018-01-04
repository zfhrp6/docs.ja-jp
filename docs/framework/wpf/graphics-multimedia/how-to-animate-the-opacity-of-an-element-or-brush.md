---
title: "方法 : 要素またはブラシの不透明度をアニメーション化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3b750e6ee21c8347d3896ec290f0ff564cc0a2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="bf9b0-102">方法 : 要素またはブラシの不透明度をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="bf9b0-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="bf9b0-103">フレームワーク要素がフェードインおよびフェードアウトするために、アニメーション化できますその<xref:System.Windows.UIElement.Opacity%2A>またはプロパティをアニメーション化することができます、<xref:System.Windows.Media.Brush.Opacity%2A>のプロパティ、 <xref:System.Windows.Media.Brush> (またはブラシ) ペイントするために使用します。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="bf9b0-104">でき、要素の不透明度をアニメーション化してその子のフェードインおよびフェードアウトが要素のどの部分がフェードインはより慎重に選択する要素の描画に使用するブラシをアニメーション化することができます。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="bf9b0-105">たとえば、ボタンの背景の描画に使用されるブラシの不透明度をアニメーション化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="bf9b0-106">これにより、ビュー、そのテキストを完全に不透明なままのフェードインおよびフェードアウトするボタンの背景が原因です。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf9b0-107">アニメーション化する、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.Brush>アニメーションを超えるパフォーマンス上の利点を提供、<xref:System.Windows.UIElement.Opacity%2A>要素のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="bf9b0-108">次の例では、2 つのボタンをアニメーション化してフェードインおよびフェードアウトします。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="bf9b0-109">最初の不透明度<xref:System.Windows.Controls.Button>とアニメーション`1.0`に`0.0`経由で、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 秒間です。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="bf9b0-110">、2 番目のボタンがアニメーション化もが描画に使用される、SolidColorBrush の不透明度その<xref:System.Windows.Controls.Control.Background%2A>全体のボタンの不透明度ではなくアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="bf9b0-111">この例を実行すると、最初のボタン完全にフェードインおよびフェードアウト、2 番目のボタンの背景のみがフェードインおよびフェードアウト中にします。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="bf9b0-112">テキストと境界線は、完全に不透明のままになります。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf9b0-113">例</span><span class="sxs-lookup"><span data-stu-id="bf9b0-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="bf9b0-114">コードは、この例から省略されています。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-114">Code has been omitted from this example.</span></span> <span data-ttu-id="bf9b0-115">完全なサンプルでは、不透明度をアニメーション化する方法も示しています、<xref:System.Windows.Media.Color>内で、<xref:System.Windows.Media.LinearGradientBrush>です。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="bf9b0-116">サンプル全体については、次を参照してください。、[要素のサンプルの不透明度をアニメーション化](http://go.microsoft.com/fwlink/?LinkID=159968)です。</span><span class="sxs-lookup"><span data-stu-id="bf9b0-116">For the full sample, see the [Animating the Opacity of an Element Sample](http://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
