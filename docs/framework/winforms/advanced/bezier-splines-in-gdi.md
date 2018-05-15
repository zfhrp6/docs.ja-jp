---
title: B&#233;ベジエ スプライン GDI + で
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="fa959-102">B&#233;ベジエ スプライン GDI + で</span><span class="sxs-lookup"><span data-stu-id="fa959-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="fa959-103">ベジエ スプラインは、4 つのポイントで指定された曲線: 次の 2 つの終点 (p1 と p2) と 2 つの制御ポイント (c1 と c2)。</span><span class="sxs-lookup"><span data-stu-id="fa959-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="fa959-104">曲線では、p1 で開始され、p2 で終了します。</span><span class="sxs-lookup"><span data-stu-id="fa959-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="fa959-105">コントロール ポイントを曲線が通過しませんが、管理ポイントが磁石、特定の方向に曲線をプルし、曲線曲がる方法に影響を与えるとして機能します。</span><span class="sxs-lookup"><span data-stu-id="fa959-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="fa959-106">次の図は、およびそのエンドポイントとの制御点のベジエ曲線を示します。</span><span class="sxs-lookup"><span data-stu-id="fa959-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="fa959-107">![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="fa959-107">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="fa959-108">曲線では、p1 で開始し、制御ポイント c1 に向かって移動します。</span><span class="sxs-lookup"><span data-stu-id="fa959-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="fa959-109">P1 における曲線接線は、c1 を p1 から描画される直線です。</span><span class="sxs-lookup"><span data-stu-id="fa959-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="fa959-110">エンドポイント p2 における接線は、c2 から p2 に描画される直線です。</span><span class="sxs-lookup"><span data-stu-id="fa959-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="fa959-111">ベジエ スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="fa959-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="fa959-112">ベジエ スプラインを描画する必要がありますのインスタンス、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Pen>です。</span><span class="sxs-lookup"><span data-stu-id="fa959-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="fa959-113">インスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッド、および<xref:System.Drawing.Pen>曲線を表示するために使用する線の色、幅などの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="fa959-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="fa959-114"><xref:System.Drawing.Pen>への引数の 1 つとして渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fa959-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="fa959-115">残りの引数が渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッドは、エンドポイントとの制御点。</span><span class="sxs-lookup"><span data-stu-id="fa959-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="fa959-116">次の例は、開始位置 (0, 0) のベジエ スプラインを描画コントロール ポイント (40, 20) と (80、150)、および終了位置 (100, 10)。</span><span class="sxs-lookup"><span data-stu-id="fa959-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="fa959-117">次の図は、曲線、コントロール ポイント、および 2 つの接線を示します。</span><span class="sxs-lookup"><span data-stu-id="fa959-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="fa959-118">![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="fa959-118">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="fa959-119">ベジエ スプラインは、自動車の業界でデザインもともとサンピエール ベジエによって開発されました。</span><span class="sxs-lookup"><span data-stu-id="fa959-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="fa959-120">さまざまな種類のコンピューター支援設計で利用できることがわかっていますので、フォントの輪郭の定義にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fa959-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="fa959-121">ベジエ スプラインことで得られるさまざまな図形を次の図のうち一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="fa959-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fa959-122">![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="fa959-122">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa959-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa959-123">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="fa959-124">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="fa959-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="fa959-125">曲線の作成と描画</span><span class="sxs-lookup"><span data-stu-id="fa959-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [<span data-ttu-id="fa959-126">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="fa959-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="fa959-127">方法: ペンを作成する</span><span class="sxs-lookup"><span data-stu-id="fa959-127">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
