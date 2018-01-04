---
title: "方法 : 楕円の円弧を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e11f3e0035c00bbc280b658c0931d57c37524f93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="c373f-102">方法 : 楕円の円弧を作成する</span><span class="sxs-lookup"><span data-stu-id="c373f-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="c373f-103">この例では、楕円の円弧を描画する方法を示します。楕円の円弧を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.ArcSegment>クラスです。</span><span class="sxs-lookup"><span data-stu-id="c373f-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c373f-104">例</span><span class="sxs-lookup"><span data-stu-id="c373f-104">Example</span></span>  
 <span data-ttu-id="c373f-105">次の例では、楕円の円弧は (10,100) から (200, 100) に描画されます。</span><span class="sxs-lookup"><span data-stu-id="c373f-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="c373f-106">円弧が、 <xref:System.Windows.Media.ArcSegment.Size%2A> 100 で 50 のデバイスに依存しないピクセル単位の<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>45 度、<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>の設定`true`、および<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>の<xref:System.Windows.Media.SweepDirection.Counterclockwise>します。</span><span class="sxs-lookup"><span data-stu-id="c373f-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="c373f-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="c373f-107">[xaml]</span></span>  
  
 <span data-ttu-id="c373f-108">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]パスを記述する属性の構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c373f-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="c373f-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="c373f-109">[xaml]</span></span>  
  
 <span data-ttu-id="c373f-110">(この属性の構文が実際に作成するメモ、 <xref:System.Windows.Media.StreamGeometry>、軽量バージョンの<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="c373f-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="c373f-111">詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。)</span><span class="sxs-lookup"><span data-stu-id="c373f-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="c373f-112">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、明示的に object タグを使用して、楕円の円弧を描画することもできます。</span><span class="sxs-lookup"><span data-stu-id="c373f-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="c373f-113">次は、前と同じ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。</span><span class="sxs-lookup"><span data-stu-id="c373f-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="c373f-114">この例は、さらに大きなサンプルの一部です。</span><span class="sxs-lookup"><span data-stu-id="c373f-114">This example is part of a larger sample.</span></span> <span data-ttu-id="c373f-115">サンプル全体については、次を参照してください。、[ジオメトリ サンプル](http://go.microsoft.com/fwlink/?LinkID=159989)です。</span><span class="sxs-lookup"><span data-stu-id="c373f-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c373f-116">参照</span><span class="sxs-lookup"><span data-stu-id="c373f-116">See Also</span></span>  
 [<span data-ttu-id="c373f-117">2 次ベジエ曲線を作成する</span><span class="sxs-lookup"><span data-stu-id="c373f-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="c373f-118">3 次ベジエ曲線を作成する</span><span class="sxs-lookup"><span data-stu-id="c373f-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
