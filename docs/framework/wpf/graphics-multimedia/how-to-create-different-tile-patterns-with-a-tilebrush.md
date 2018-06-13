---
title: '方法 : TileBrush を使用してさまざまなタイル パターンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: 01004c66a8bd820f05e6e1f6c77a9fe7d30bca46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559602"
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a><span data-ttu-id="f2008-102">方法 : TileBrush を使用してさまざまなタイル パターンを作成する</span><span class="sxs-lookup"><span data-stu-id="f2008-102">How to: Create Different Tile Patterns with a TileBrush</span></span>
<span data-ttu-id="f2008-103">この例を使用する方法を示しています、<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、<xref:System.Windows.Media.TileBrush>パターンを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2008-103">This example shows how to use the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.TileBrush> to create a pattern.</span></span>  
  
 <span data-ttu-id="f2008-104"><xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティを使用すると、指定方法のコンテンツ、<xref:System.Windows.Media.TileBrush>が繰り返されますが、出力領域に並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="f2008-104">The <xref:System.Windows.Media.TileBrush.TileMode%2A> property enables you to specify how the content of a <xref:System.Windows.Media.TileBrush> is repeated, that is, tiled to fill an output area.</span></span> <span data-ttu-id="f2008-105">設定するパターンを作成する、<xref:System.Windows.Media.TileBrush.TileMode%2A>に<xref:System.Windows.Media.TileMode.Tile>、 <xref:System.Windows.Media.TileMode.FlipX>、 <xref:System.Windows.Media.TileMode.FlipY>、または<xref:System.Windows.Media.TileMode.FlipXY>です。</span><span class="sxs-lookup"><span data-stu-id="f2008-105">To create a pattern, you set the <xref:System.Windows.Media.TileBrush.TileMode%2A> to <xref:System.Windows.Media.TileMode.Tile>, <xref:System.Windows.Media.TileMode.FlipX>, <xref:System.Windows.Media.TileMode.FlipY>, or <xref:System.Windows.Media.TileMode.FlipXY>.</span></span> <span data-ttu-id="f2008-106">設定する必要があります、<xref:System.Windows.Media.TileBrush.Viewport%2A>の<xref:System.Windows.Media.TileBrush>; 描画している領域よりも小さくなるよう以外の場合、1 つのタイルのみに関係なく、生成されたを<xref:System.Windows.Media.TileBrush.TileMode%2A>設定を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f2008-106">You must also set the <xref:System.Windows.Media.TileBrush.Viewport%2A> of the <xref:System.Windows.Media.TileBrush> so that it is smaller than the area that you are painting; otherwise, only a single tile is produced, regardless which <xref:System.Windows.Media.TileBrush.TileMode%2A> setting you use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2008-107">例</span><span class="sxs-lookup"><span data-stu-id="f2008-107">Example</span></span>  
 <span data-ttu-id="f2008-108">次の例では、5 つが作成されます<xref:System.Windows.Media.DrawingBrush>オブジェクトでは、異なる<xref:System.Windows.Media.TileBrush.TileMode%2A>を設定して、それらを 5 つの四角形の描画に使用します。</span><span class="sxs-lookup"><span data-stu-id="f2008-108">The following example creates five <xref:System.Windows.Media.DrawingBrush> objects, gives them each a different <xref:System.Windows.Media.TileBrush.TileMode%2A> setting, and uses them to paint five rectangles.</span></span> <span data-ttu-id="f2008-109">この例を使用しますが、<xref:System.Windows.Media.DrawingBrush>を示すためにクラス<xref:System.Windows.Media.TileBrush.TileMode%2A>の動作、<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティのすべての動作は同じです、<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.VisualBrush>と<xref:System.Windows.Media.DrawingBrush>です。</span><span class="sxs-lookup"><span data-stu-id="f2008-109">Although this example uses the <xref:System.Windows.Media.DrawingBrush> class to demonstrate <xref:System.Windows.Media.TileBrush.TileMode%2A> behavior, the <xref:System.Windows.Media.TileBrush.TileMode%2A> property works identically for all the <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.VisualBrush>, and <xref:System.Windows.Media.DrawingBrush>.</span></span>  
  
 <span data-ttu-id="f2008-110">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2008-110">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="f2008-111">![出力例を並べて表示された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span><span class="sxs-lookup"><span data-stu-id="f2008-111">![TileBrush tiling example output](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")</span></span>  
<span data-ttu-id="f2008-112">TileMode プロパティを使用して作成されたタイル パターン</span><span class="sxs-lookup"><span data-stu-id="f2008-112">Tile patterns created with the TileMode property</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f2008-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2008-113">See Also</span></span>  
 [<span data-ttu-id="f2008-114">TileBrush のタイル サイズを設定する</span><span class="sxs-lookup"><span data-stu-id="f2008-114">Set the Tile Size for a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [<span data-ttu-id="f2008-115">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="f2008-115">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
