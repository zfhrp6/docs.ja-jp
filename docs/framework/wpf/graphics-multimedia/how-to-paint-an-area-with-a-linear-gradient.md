---
title: "方法 : 線形グラデーションを使用して領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec4ec2fc7ba99081eaafa6803d20c99bebc6c2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="6c96f-102">方法 : 線形グラデーションを使用して領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="6c96f-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="6c96f-103">この例を使用する方法を示しています、<xref:System.Windows.Media.LinearGradientBrush>線形グラデーションで領域を塗りつぶすクラス。</span><span class="sxs-lookup"><span data-stu-id="6c96f-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="6c96f-104">次の例で、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>赤青の淡い緑から黄色から遷移対角線方向の線形グラデーションで塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="6c96f-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c96f-105">例</span><span class="sxs-lookup"><span data-stu-id="6c96f-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="6c96f-106">次の図は、前述の例で作成したグラデーションを示します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="6c96f-107">![対角線方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="6c96f-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="6c96f-108">水平方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0,0.5) に (1,0.5) とします。</span><span class="sxs-lookup"><span data-stu-id="6c96f-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="6c96f-109">次の例で、<xref:System.Windows.Shapes.Rectangle>が水平方向の線形グラデーションを使用して描画します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="6c96f-110">次の図は、前述の例で作成したグラデーションを示します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="6c96f-111">![水平方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="6c96f-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="6c96f-112">垂直方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0.5,0) に (0.5,1) とします。</span><span class="sxs-lookup"><span data-stu-id="6c96f-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="6c96f-113">次の例で、<xref:System.Windows.Shapes.Rectangle>が垂直方向の線形グラデーションを使用して描画します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="6c96f-114">次の図は、前述の例で作成したグラデーションを示します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="6c96f-115">![垂直方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="6c96f-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c96f-116">このトピックの例では、始点と終点を設定するための既定の座標系を使用します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="6c96f-117">既定の座標システムは境界ボックスに対する相対: 0%、境界ボックスの場合は 0、1 は、境界ボックスの 100% を示します。</span><span class="sxs-lookup"><span data-stu-id="6c96f-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="6c96f-118">この座標系を変更するには設定して、<xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティ値を<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="6c96f-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c96f-119">絶対座標系は、境界ボックスに相対しません。</span><span class="sxs-lookup"><span data-stu-id="6c96f-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="6c96f-120">値は、ローカル空間に直接変換されます。</span><span class="sxs-lookup"><span data-stu-id="6c96f-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="6c96f-121">その他の例では、次を参照してください。[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。</span><span class="sxs-lookup"><span data-stu-id="6c96f-121">For additional examples, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="6c96f-122">グラデーションおよびその他の種類のブラシの詳細については、次を参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="6c96f-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
