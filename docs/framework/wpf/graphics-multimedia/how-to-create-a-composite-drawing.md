---
title: '方法 : 複合描画を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: bb222fff11c81b491c0413f174539ff0005d11b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="4fe1e-102">方法 : 複合描画を作成する</span><span class="sxs-lookup"><span data-stu-id="4fe1e-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="4fe1e-103">この例を使用する方法を示しています、<xref:System.Windows.Media.DrawingGroup>複数を組み合わせることで複雑な図面を作成する<xref:System.Windows.Media.Drawing>に 1 つの複合描画オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe1e-104">例</span><span class="sxs-lookup"><span data-stu-id="4fe1e-104">Example</span></span>  
 <span data-ttu-id="4fe1e-105">次の例では、<xref:System.Windows.Media.DrawingGroup>の描画領域を作成する、<xref:System.Windows.Media.GeometryDrawing>と<xref:System.Windows.Media.ImageDrawing>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="4fe1e-106">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="4fe1e-107">![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="4fe1e-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="4fe1e-108">DrawingGroup を使用して作成される複合描画</span><span class="sxs-lookup"><span data-stu-id="4fe1e-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="4fe1e-109">描画の境界を示しています。 灰色の枠線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="4fe1e-110">使用することができます、<xref:System.Windows.Media.DrawingGroup>を適用する、 <xref:System.Windows.Media.DrawingGroup.Transform%2A>、<xref:System.Windows.Media.DrawingGroup.Opacity%2A>設定、 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、または<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>が含まれている図面にします。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="4fe1e-111"><xref:System.Windows.Media.DrawingGroup>も、 <xref:System.Windows.Media.Drawing>、他の含めることができます<xref:System.Windows.Media.DrawingGroup>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="4fe1e-112">追加を使用する点を除いて、次の例は前の例のような<xref:System.Windows.Media.DrawingGroup>の描いた絵の一部のビットマップ効果と不透明度マスクを適用するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="4fe1e-113">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="4fe1e-114">![複数の描画を含む DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="4fe1e-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="4fe1e-115">描画する複合が複数の DrawingGroup オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4fe1e-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="4fe1e-116">描画の境界を示しています。 灰色の枠線に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="4fe1e-117">詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="4fe1e-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe1e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fe1e-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="4fe1e-119">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="4fe1e-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
