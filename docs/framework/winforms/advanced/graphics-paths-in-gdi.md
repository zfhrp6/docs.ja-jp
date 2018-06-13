---
title: GDI+ でのグラフィックス パス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523889"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="58fdd-102">GDI+ でのグラフィックス パス</span><span class="sxs-lookup"><span data-stu-id="58fdd-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="58fdd-103">パスは、線、四角形、および単純な曲線を組み合わせることで形成されます。</span><span class="sxs-lookup"><span data-stu-id="58fdd-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="58fdd-104">メッセージの取り消し、[ベクター グラフィックスの概要](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)基本的な構成要素は次の図を描画するため、最も役に立つことが証明されたこと。</span><span class="sxs-lookup"><span data-stu-id="58fdd-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="58fdd-105">線</span><span class="sxs-lookup"><span data-stu-id="58fdd-105">Lines</span></span>  
  
-   <span data-ttu-id="58fdd-106">四角形</span><span class="sxs-lookup"><span data-stu-id="58fdd-106">Rectangles</span></span>  
  
-   <span data-ttu-id="58fdd-107">省略記号ボタン</span><span class="sxs-lookup"><span data-stu-id="58fdd-107">Ellipses</span></span>  
  
-   <span data-ttu-id="58fdd-108">円弧</span><span class="sxs-lookup"><span data-stu-id="58fdd-108">Arcs</span></span>  
  
-   <span data-ttu-id="58fdd-109">多角形</span><span class="sxs-lookup"><span data-stu-id="58fdd-109">Polygons</span></span>  
  
-   <span data-ttu-id="58fdd-110">カーディナル スプライン</span><span class="sxs-lookup"><span data-stu-id="58fdd-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="58fdd-111">ベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="58fdd-111">Bézier splines</span></span>  
  
 <span data-ttu-id="58fdd-112">GDI + での<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトでは、1 つの単位にこれらの構成要素のシーケンスを収集することができます。</span><span class="sxs-lookup"><span data-stu-id="58fdd-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="58fdd-113">1 回の呼び出しで、線、四角形を多角形、および曲線のシーケンス全体を描画し、ことができます、<xref:System.Drawing.Graphics.DrawPath%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="58fdd-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="58fdd-114">次の図は、行、円弧をベジエ スプラインを通過するカーディナル スプラインを組み合わせることによって作成されるパスを示します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="58fdd-115">![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="58fdd-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="58fdd-116">パスを使用します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-116">Using a Path</span></span>  
 <span data-ttu-id="58fdd-117"><xref:System.Drawing.Drawing2D.GraphicsPath>クラスが描画される項目のシーケンスを作成するための次のメソッドを提供: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (用カーディナル スプライン)、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>です。</span><span class="sxs-lookup"><span data-stu-id="58fdd-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="58fdd-118">これらの各メソッドはオーバー ロードです。つまり、各メソッドは、いくつかの異なるパラメーター リストをサポートします。</span><span class="sxs-lookup"><span data-stu-id="58fdd-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="58fdd-119">たとえば、1 つバリエーションの 1 つの<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドは、4 つの整数と別のバリエーションを受信、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドは、2 つ受け取ります<xref:System.Drawing.Point>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="58fdd-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="58fdd-120">線、四角形、およびベジエ スプラインをパスに追加するためのメソッドを 1 つの呼び出しパスにいくつかの項目を追加する複数形のコンパニオン メソッドがある: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>です。</span><span class="sxs-lookup"><span data-stu-id="58fdd-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="58fdd-121">また、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>メソッドがあるコンパニオン メソッド<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>パスに閉じた曲線または円グラフを追加します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="58fdd-122">パスの描画、する必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Pen>オブジェクト、および<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="58fdd-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="58fdd-123"><xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawPath%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、パスを表示するために使用する線の色、幅などの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="58fdd-124"><xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは、直線と曲線のパスを構成するのシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="58fdd-125"><xref:System.Drawing.Pen>オブジェクトおよび<xref:System.Drawing.Drawing2D.GraphicsPath>への引数として渡されるオブジェクト、<xref:System.Drawing.Graphics.DrawPath%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="58fdd-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="58fdd-126">次の例では、パスは、行、楕円、およびベジエ スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="58fdd-127">次の図は、パスを示します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="58fdd-128">![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="58fdd-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="58fdd-129">にパスを線、四角形、および曲線を追加するだけでなく、パスにパスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="58fdd-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="58fdd-130">これにより、大規模で複雑なパスを形成する既存のパスを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="58fdd-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="58fdd-131">パスに追加できる他の 2 つの項目がある: 文字列と扇形です。</span><span class="sxs-lookup"><span data-stu-id="58fdd-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="58fdd-132">円、楕円の内部の一部です。</span><span class="sxs-lookup"><span data-stu-id="58fdd-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="58fdd-133">次の例では、円弧、通過するカーディナル スプライン、文字列、および、円グラフからパスを作成します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="58fdd-134">次の図は、パスを示します。</span><span class="sxs-lookup"><span data-stu-id="58fdd-134">The following illustration shows the path.</span></span> <span data-ttu-id="58fdd-135">接続されている; パスがないことに注意してください。弧をカーディナル スプライン、文字列、および円グラフが区切られます。</span><span class="sxs-lookup"><span data-stu-id="58fdd-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="58fdd-136">![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="58fdd-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fdd-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="58fdd-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="58fdd-138">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="58fdd-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="58fdd-139">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="58fdd-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="58fdd-140">パスの作成および描画</span><span class="sxs-lookup"><span data-stu-id="58fdd-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
