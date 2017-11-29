---
title: "方法 : 2 次ベジエ曲線を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8320889f931e4482091b15bd9295c77a36d6d1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="e0688-102">方法 : 2 次ベジエ曲線を作成する</span><span class="sxs-lookup"><span data-stu-id="e0688-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="e0688-103">この例では、2 次ベジエ曲線を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0688-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="e0688-104">2 次ベジエ曲線を作成するには、使用、 <xref:System.Windows.Media.PathGeometry>、 <xref:System.Windows.Media.PathFigure>、および<xref:System.Windows.Media.QuadraticBezierSegment>クラスです。</span><span class="sxs-lookup"><span data-stu-id="e0688-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0688-105">例</span><span class="sxs-lookup"><span data-stu-id="e0688-105">Example</span></span>  
 <span data-ttu-id="e0688-106">次の例では、2 次ベジエ曲線は (10,100) から (300, 100) に描画されます。</span><span class="sxs-lookup"><span data-stu-id="e0688-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="e0688-107">曲線は、コントロール ポイント (200, 200)。</span><span class="sxs-lookup"><span data-stu-id="e0688-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="e0688-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e0688-108">[xaml]</span></span>  
  
 <span data-ttu-id="e0688-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]パスを記述する属性の構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e0688-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="e0688-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="e0688-110">[xaml]</span></span>  
  
 <span data-ttu-id="e0688-111">(この属性の構文が実際に作成するメモ、 <xref:System.Windows.Media.StreamGeometry>、軽量バージョンの<xref:System.Windows.Media.PathGeometry>です。</span><span class="sxs-lookup"><span data-stu-id="e0688-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="e0688-112">詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。)</span><span class="sxs-lookup"><span data-stu-id="e0688-112">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="e0688-113">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、オブジェクト要素の構文を使用して、2 次ベジエ曲線を描画することもできます。</span><span class="sxs-lookup"><span data-stu-id="e0688-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="e0688-114">次の例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="e0688-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="e0688-115">この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0688-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0688-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0688-116">See Also</span></span>  
 [<span data-ttu-id="e0688-117">楕円の円弧を作成する</span><span class="sxs-lookup"><span data-stu-id="e0688-117">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="e0688-118">3 次ベジエ曲線を作成する</span><span class="sxs-lookup"><span data-stu-id="e0688-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
