---
title: "方法 : 描画を使用して領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1db788ae0fabdfd27cf215bfcf466c41df19c637
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="d5061-102">方法 : 描画を使用して領域を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="d5061-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="d5061-103">この例では、描画を使用して領域を塗りつぶす方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5061-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="d5061-104">描画を使用して領域を塗りつぶすには、使用する、<xref:System.Windows.Media.DrawingBrush>と 1 つまたは複数<xref:System.Windows.Media.Drawing>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d5061-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="d5061-105">次の例では、 <xref:System.Windows.Media.DrawingBrush> 2 つの楕円の描画を使用してオブジェクトの描画にします。</span><span class="sxs-lookup"><span data-stu-id="d5061-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5061-106">例</span><span class="sxs-lookup"><span data-stu-id="d5061-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="d5061-107">この例の出力を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="d5061-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="d5061-108">![DrawingBrush からの出力](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="d5061-108">![Output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="d5061-109">(上の理由から」に記載の図形の中心が白[複合図形の塗りつぶしを制御](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md))。</span><span class="sxs-lookup"><span data-stu-id="d5061-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="d5061-110">設定して、<xref:System.Windows.Media.DrawingBrush>オブジェクトの<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティ、繰り返しパターンを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d5061-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="d5061-111">2 つの楕円の描画から作成されるパターンで、オブジェクトを塗りつぶす例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5061-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="d5061-112">次の図は、並べて表示<xref:System.Windows.Media.DrawingBrush>出力します。</span><span class="sxs-lookup"><span data-stu-id="d5061-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="d5061-113">![並べて表示された DrawingBrush の出力](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="d5061-113">![Tiled output from a DrawingBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="d5061-114">詳細については、描画ブラシを参照してください。[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5061-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="d5061-115">詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください、[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5061-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>
