---
title: "方法 : TileBrush のタイル サイズを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 484419c05c3d607212ea6d565777cf49cbfdbc19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="84707-102">方法 : TileBrush のタイル サイズを設定する</span><span class="sxs-lookup"><span data-stu-id="84707-102">How to: Set the Tile Size for a TileBrush</span></span>
<span data-ttu-id="84707-103">この例のタイルのサイズを設定する方法を示しています、<xref:System.Windows.Media.TileBrush>です。</span><span class="sxs-lookup"><span data-stu-id="84707-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="84707-104">既定では、<xref:System.Windows.Media.TileBrush>完全に領域に描画している 1 つのタイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="84707-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="84707-105">この動作をオーバーライドするには、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="84707-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>  
  
 <span data-ttu-id="84707-106"><xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティ、タイルのサイズを指定、<xref:System.Windows.Media.TileBrush>です。</span><span class="sxs-lookup"><span data-stu-id="84707-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="84707-107">既定では、値、<xref:System.Windows.Media.TileBrush.Viewport%2A>塗りつぶされている領域のサイズに対する相対パス プロパティです。</span><span class="sxs-lookup"><span data-stu-id="84707-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="84707-108">させる、 <xref:System.Windows.Media.TileBrush.Viewport%2A> 、絶対のタイルのサイズを指定するプロパティを設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>です。</span><span class="sxs-lookup"><span data-stu-id="84707-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84707-109">例</span><span class="sxs-lookup"><span data-stu-id="84707-109">Example</span></span>  
 <span data-ttu-id="84707-110">次の例では、<xref:System.Windows.Media.ImageBrush>の型<xref:System.Windows.Media.TileBrush>タイルを含む四角形を描画します。</span><span class="sxs-lookup"><span data-stu-id="84707-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="84707-111">例では、各タイルを出力領域 (四角形) の 50% x 50% に設定します。</span><span class="sxs-lookup"><span data-stu-id="84707-111">The example sets each tile to  50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="84707-112">その結果、四角形は、イメージの 4 つの投影で塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="84707-112">As a result, the rectangle is painted with four projections of the image.</span></span>  
  
 <span data-ttu-id="84707-113">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="84707-113">The following illustration shows the output that the example produces.</span></span>
  
 <span data-ttu-id="84707-114">![イメージ ブラシを並べて表示する例](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span><span class="sxs-lookup"><span data-stu-id="84707-114">![Example of tiling with an image brush](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 <span data-ttu-id="84707-115">次の例では、作成、 <xref:System.Windows.Media.ImageBrush>、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>に`0,0,25,25`とその<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>に<xref:System.Windows.Media.BrushMappingMode.Absolute>、し、別の四角形の描画に使用します。</span><span class="sxs-lookup"><span data-stu-id="84707-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="84707-116">その結果、ブラシは、幅が 25 ピクセル、高さが 25 ピクセルのタイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="84707-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>  
  
 <span data-ttu-id="84707-117">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="84707-117">The following illustration shows the output that the example produces.</span></span>  
  
 <span data-ttu-id="84707-118">![0,0,0.25,0.25 の Viewport を使用したタイル表示の TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span><span class="sxs-lookup"><span data-stu-id="84707-118">![A tiled TileBrush with a Viewport of 0,0,0.25,0.25](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")</span></span>  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 <span data-ttu-id="84707-119">上記の例は、大規模なサンプルの一部です。</span><span class="sxs-lookup"><span data-stu-id="84707-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="84707-120">サンプル全体については、次を参照してください。 [ImageBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160005)です。</span><span class="sxs-lookup"><span data-stu-id="84707-120">For the complete sample, see [ImageBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160005).</span></span>  
  
 <span data-ttu-id="84707-121">この例を使用しますが、<xref:System.Windows.Media.ImageBrush>クラス、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティが、他の動作は同じです<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>です。</span><span class="sxs-lookup"><span data-stu-id="84707-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="84707-122">詳細については<xref:System.Windows.Media.ImageBrush>と、その他の<xref:System.Windows.Media.TileBrush>、オブジェクトを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。</span><span class="sxs-lookup"><span data-stu-id="84707-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84707-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="84707-123">See Also</span></span>  
 <xref:System.Windows.Media.TileBrush>  
 [<span data-ttu-id="84707-124">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="84707-124">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="84707-125">TileBrush を使用してさまざまなタイル パターンを作成する</span><span class="sxs-lookup"><span data-stu-id="84707-125">Create Different Tile Patterns with a TileBrush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
