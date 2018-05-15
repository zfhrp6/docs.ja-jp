---
title: '方法 : 四角形を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 100f1a8062628e892e9a71b988bb2a8754ea6bad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="cc823-102">方法 : 四角形を描画する</span><span class="sxs-lookup"><span data-stu-id="cc823-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="cc823-103">この例を使用して、四角形を描画する方法を示しています、<xref:System.Windows.Shapes.Rectangle>要素。</span><span class="sxs-lookup"><span data-stu-id="cc823-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="cc823-104">四角形を描画するには、作成、<xref:System.Windows.Shapes.Rectangle>要素を指定し、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>です。</span><span class="sxs-lookup"><span data-stu-id="cc823-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="cc823-105">四角形の内部を描画するには、次のように設定します。 その<xref:System.Windows.Shapes.Shape.Fill%2A>です。</span><span class="sxs-lookup"><span data-stu-id="cc823-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="cc823-106">四角形にアウトラインを与えるを使用してその<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cc823-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="cc823-107">角の丸い四角形を提供する、省略可能な指定<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cc823-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="cc823-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティ設定を四角形の角を丸めるに使用される楕円の x 軸と y 軸半径。</span><span class="sxs-lookup"><span data-stu-id="cc823-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="cc823-109">次の例では、次の 2 つ<xref:System.Windows.Shapes.Rectangle>で要素が描画、<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="cc823-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cc823-110">最初の四角形は、<xref:System.Windows.Media.Brushes.Blue%2A>内部です。</span><span class="sxs-lookup"><span data-stu-id="cc823-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="cc823-111">2 つ目の四角形、 <xref:System.Windows.Media.Brushes.Blue%2A> 、内部、<xref:System.Windows.Media.Brushes.Black%2A>アウトライン、および角の丸いです。</span><span class="sxs-lookup"><span data-stu-id="cc823-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc823-112">例</span><span class="sxs-lookup"><span data-stu-id="cc823-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="cc823-113">この例を使用しますが、<xref:System.Windows.Controls.Canvas>を四角形を含むで使用できる長方形要素 (およびその他のすべての図形要素) いずれかの<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc823-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="cc823-114">実際、四角形は特にの部分の背景を提供するのに役立ちます<xref:System.Windows.Controls.Grid>パネルです。</span><span class="sxs-lookup"><span data-stu-id="cc823-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="cc823-115">例については、次を参照してください。、[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc823-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="cc823-116">この例より大きなサンプルの一部サンプル全体については、次を参照してください。[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)です。</span><span class="sxs-lookup"><span data-stu-id="cc823-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc823-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc823-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="cc823-118">図形要素のサンプル</span><span class="sxs-lookup"><span data-stu-id="cc823-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="cc823-119">WPF での図形と基本描画の概要</span><span class="sxs-lookup"><span data-stu-id="cc823-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="cc823-120">テーブルの概要</span><span class="sxs-lookup"><span data-stu-id="cc823-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
