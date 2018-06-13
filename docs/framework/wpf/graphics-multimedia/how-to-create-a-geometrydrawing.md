---
title: '方法 : GeometryDrawing を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: 713cecd10bfa62494c50c96cb8cbece69f7e5660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560661"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="46c8d-102">方法 : GeometryDrawing を作成する</span><span class="sxs-lookup"><span data-stu-id="46c8d-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="46c8d-103">この例を作成し、表示する方法を示しています、<xref:System.Windows.Media.GeometryDrawing>です。</span><span class="sxs-lookup"><span data-stu-id="46c8d-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="46c8d-104">A<xref:System.Windows.Media.GeometryDrawing>を関連付けることで作成して、アウトラインの図形を作成することができます、<xref:System.Windows.Media.Pen>と<xref:System.Windows.Media.Brush>で、<xref:System.Windows.Media.Geometry>です。</span><span class="sxs-lookup"><span data-stu-id="46c8d-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="46c8d-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A>図形の構造について説明します、 <xref:System.Windows.Media.GeometryDrawing.Brush%2A> 、図形の塗りつぶしをについて説明し、<xref:System.Windows.Media.GeometryDrawing.Pen%2A>図形の輪郭をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="46c8d-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c8d-106">例</span><span class="sxs-lookup"><span data-stu-id="46c8d-106">Example</span></span>  
 <span data-ttu-id="46c8d-107">次の例では、<xref:System.Windows.Media.GeometryDrawing>図形を表示するためにします。</span><span class="sxs-lookup"><span data-stu-id="46c8d-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="46c8d-108">図形は、<xref:System.Windows.Media.GeometryGroup>と 2 つ<xref:System.Windows.Media.EllipseGeometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="46c8d-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="46c8d-109">図形の内部を描画すると、<xref:System.Windows.Media.LinearGradientBrush>でアウトラインを描画し、 <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>です。</span><span class="sxs-lookup"><span data-stu-id="46c8d-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="46c8d-110"><xref:System.Windows.Media.GeometryDrawing>を使用して、表示、<xref:System.Windows.Media.ImageDrawing>と<xref:System.Windows.Controls.Image>要素。</span><span class="sxs-lookup"><span data-stu-id="46c8d-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="46c8d-111">次の図は、結果として得られる<xref:System.Windows.Media.GeometryDrawing>です。</span><span class="sxs-lookup"><span data-stu-id="46c8d-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="46c8d-112">![楕円 2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="46c8d-112">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="46c8d-113">複雑な図面を作成するには、描画を使用して 1 つの複合に複数の描画オブジェクトを結合できます、<xref:System.Windows.Media.DrawingGroup>です。</span><span class="sxs-lookup"><span data-stu-id="46c8d-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c8d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="46c8d-114">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 [<span data-ttu-id="46c8d-115">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="46c8d-115">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="46c8d-116">ジオメトリの概要</span><span class="sxs-lookup"><span data-stu-id="46c8d-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="46c8d-117">複合描画を作成する</span><span class="sxs-lookup"><span data-stu-id="46c8d-117">Create a Composite Drawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
