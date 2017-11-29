---
title: "方法 : UIElement を透明または半透明にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec35ae2e064acf78d1165f64ce8c9e34b153299d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a><span data-ttu-id="855c9-102">方法 : UIElement を透明または半透明にする</span><span class="sxs-lookup"><span data-stu-id="855c9-102">How to: Make a UIElement Transparent or Semi-Transparent</span></span>
<span data-ttu-id="855c9-103">この例では、作成、<xref:System.Windows.UIElement>透明または半透明です。</span><span class="sxs-lookup"><span data-stu-id="855c9-103">This example shows how to make a <xref:System.Windows.UIElement> transparent or semi-transparent.</span></span> <span data-ttu-id="855c9-104">設定する要素を透明または半透明にその<xref:System.Windows.UIElement.Opacity%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="855c9-104">To make an element transparent or semi-transparent, you set its <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="855c9-105">値`0.0`要素は完全に透明で、値の中に、`1.0`要素を完全に不透明になります。</span><span class="sxs-lookup"><span data-stu-id="855c9-105">A value of `0.0` makes the element completely transparent, while a value of `1.0` makes the element completely opaque.</span></span> <span data-ttu-id="855c9-106">値`0.5`により要素 50% 不透明で、やなどです。</span><span class="sxs-lookup"><span data-stu-id="855c9-106">A value of `0.5` makes the element 50% opaque, and so on.</span></span> <span data-ttu-id="855c9-107">要素の<xref:System.Windows.UIElement.Opacity%2A>に設定されている`1.0`既定です。</span><span class="sxs-lookup"><span data-stu-id="855c9-107">An element's <xref:System.Windows.UIElement.Opacity%2A> is set to `1.0` by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="855c9-108">例</span><span class="sxs-lookup"><span data-stu-id="855c9-108">Example</span></span>  
 <span data-ttu-id="855c9-109">次の例のセット、<xref:System.Windows.UIElement.Opacity%2A>するボタンの`0.25`、作成とその内容 (この場合、ボタンのテキスト) を 25% 不透明です。</span><span class="sxs-lookup"><span data-stu-id="855c9-109">The following example sets the <xref:System.Windows.UIElement.Opacity%2A> of a button to `0.25`, making it and its contents (in this case, the button's text) 25% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 <span data-ttu-id="855c9-110">要素の内容が自分<xref:System.Windows.UIElement.Opacity%2A>、それらの値の設定を含む要素が乗算<xref:System.Windows.UIElement.Opacity%2A>です。</span><span class="sxs-lookup"><span data-stu-id="855c9-110">If an element's contents have their own <xref:System.Windows.UIElement.Opacity%2A> settings, those values are multiplied against the containing elements <xref:System.Windows.UIElement.Opacity%2A>.</span></span>  
  
 <span data-ttu-id="855c9-111">次の例では、ボタンの<xref:System.Windows.UIElement.Opacity%2A>に`0.25`、および<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Image> をクリックしてに含まれているコントロール`0.5`です。</span><span class="sxs-lookup"><span data-stu-id="855c9-111">The following example sets a button's <xref:System.Windows.UIElement.Opacity%2A> to `0.25`, and the <xref:System.Windows.UIElement.Opacity%2A> of an <xref:System.Windows.Controls.Image> control contained with in the button to `0.5`.</span></span> <span data-ttu-id="855c9-112">その結果、イメージが 12.5% 不透明度が表示されます: 0.125 = 0.25 * 0.5 です。</span><span class="sxs-lookup"><span data-stu-id="855c9-112">As a result, the image appears 12.5% opaque: 0.25 * 0.5 = 0.125.</span></span>  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 <span data-ttu-id="855c9-113">要素の不透明度を制御する別の方法がの不透明度を設定するには、<xref:System.Windows.Media.Brush>要素を描画します。</span><span class="sxs-lookup"><span data-stu-id="855c9-113">Another way to control the opacity of an element is to set the opacity of the <xref:System.Windows.Media.Brush> that paints the element.</span></span> <span data-ttu-id="855c9-114">この方法が選択的に、要素の各部分の不透明度を変更することができ、使用する要素の場合よりパフォーマンス上の利点を提供<xref:System.Windows.UIElement.Opacity%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="855c9-114">This approach enables you to selectively alter the opacity of portions of an element, and provides performance benefits over using the element's <xref:System.Windows.UIElement.Opacity%2A> property.</span></span> <span data-ttu-id="855c9-115">次の例のセット、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>ボタンの描画に使用される<xref:System.Windows.Controls.Control.Background%2A>に設定されている`0.25`です。</span><span class="sxs-lookup"><span data-stu-id="855c9-115">The following example sets the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush> used to paint the button's <xref:System.Windows.Controls.Control.Background%2A> is set to `0.25`.</span></span> <span data-ttu-id="855c9-116">その結果、ブラシの背景が 25% 不透明で残ります内容 (ボタンのテキスト) 100% の不透明度。</span><span class="sxs-lookup"><span data-stu-id="855c9-116">As a result, the brush's background is 25% opaque, but its contents (the button's text) remain 100% opaque.</span></span>  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 <span data-ttu-id="855c9-117">ブラシ内の個々 の色の不透明度を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="855c9-117">You may also control the opacity of individual colors within a brush.</span></span> <span data-ttu-id="855c9-118">詳細については、色、ブラシを参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="855c9-118">For more information about colors and brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span> <span data-ttu-id="855c9-119">要素の不透明度をアニメーション化する方法を示す例は、次を参照してください。[要素またはブラシの不透明度をアニメーション化](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)です。</span><span class="sxs-lookup"><span data-stu-id="855c9-119">For an example showing how to animate an element's opacity, see [Animate the Opacity of an Element or Brush](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).</span></span>
