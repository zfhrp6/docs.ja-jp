---
title: GDI+ での楕円および円弧
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 6835127d03f984bda8a95cf5b9ca9798122de804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ellipses-and-arcs-in-gdi"></a><span data-ttu-id="cfbbb-102">GDI+ での楕円および円弧</span><span class="sxs-lookup"><span data-stu-id="cfbbb-102">Ellipses and Arcs in GDI+</span></span>
<span data-ttu-id="cfbbb-103">楕円と円弧を使用して簡単に描画することができます、<xref:System.Drawing.Graphics.DrawEllipse%2A>と<xref:System.Drawing.Graphics.DrawArc%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-103">You can easily draw ellipses and arcs using the <xref:System.Drawing.Graphics.DrawEllipse%2A> and <xref:System.Drawing.Graphics.DrawArc%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="drawing-an-ellipse"></a><span data-ttu-id="cfbbb-104">楕円を描画</span><span class="sxs-lookup"><span data-stu-id="cfbbb-104">Drawing an Ellipse</span></span>  
 <span data-ttu-id="cfbbb-105">楕円を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-105">To draw an ellipse, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="cfbbb-106"><xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、省略記号を表示するために使用する線の色、幅などの属性を格納します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-106">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the ellipse.</span></span> <span data-ttu-id="cfbbb-107"><xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-107">The <xref:System.Drawing.Pen> object is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="cfbbb-108">残りの引数が渡される、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドは、楕円の外接する四角形を指定します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-108">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method specify the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="cfbbb-109">次の図は、その外接する四角形と楕円を描画します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-109">The following illustration shows an ellipse along with its bounding rectangle.</span></span>  
  
 <span data-ttu-id="cfbbb-110">![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span><span class="sxs-lookup"><span data-stu-id="cfbbb-110">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")</span></span>  
  
 <span data-ttu-id="cfbbb-111">楕円を描画する次の例外接する四角形が 80、40 の高さとの左上隅の幅 (100, 50)。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-111">The following example draws an ellipse; the bounding rectangle has a width of 80, a height of 40, and an upper-left corner of (100, 50):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <span data-ttu-id="cfbbb-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-112"><xref:System.Drawing.Graphics.DrawEllipse%2A> is an overloaded method of the <xref:System.Drawing.Graphics> class, so there are several ways you can supply it with arguments.</span></span> <span data-ttu-id="cfbbb-113">たとえば、構成することができます、<xref:System.Drawing.Rectangle>を渡すと、<xref:System.Drawing.Rectangle>を<xref:System.Drawing.Graphics.DrawEllipse%2A>引数としてメソッド。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-113">For example, you can construct a <xref:System.Drawing.Rectangle> and pass the <xref:System.Drawing.Rectangle> to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method as an argument:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a><span data-ttu-id="cfbbb-114">円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-114">Drawing an Arc</span></span>  
 <span data-ttu-id="cfbbb-115">円弧は、楕円の一部です。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-115">An arc is a portion of an ellipse.</span></span> <span data-ttu-id="cfbbb-116">円弧を描くを呼び出す、<xref:System.Drawing.Graphics.DrawArc%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-116">To draw an arc, you call the <xref:System.Drawing.Graphics.DrawArc%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="cfbbb-117">パラメーター、<xref:System.Drawing.Graphics.DrawArc%2A>メソッドのパラメーターと同じでは、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドの点を除いて、<xref:System.Drawing.Graphics.DrawArc%2A>開始角度および掃引角度が必要です。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-117">The parameters of the <xref:System.Drawing.Graphics.DrawArc%2A> method are the same as the parameters of the <xref:System.Drawing.Graphics.DrawEllipse%2A> method, except that <xref:System.Drawing.Graphics.DrawArc%2A> requires a starting angle and sweep angle.</span></span> <span data-ttu-id="cfbbb-118">次の例では、30 度の開始角度および掃引角度が 180 度の円弧を描画します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-118">The following example draws an arc with a starting angle of 30 degrees and a sweep angle of 180 degrees:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 <span data-ttu-id="cfbbb-119">次の図は、円弧、楕円、および外接する四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="cfbbb-119">The following illustration shows the arc, the ellipse, and the bounding rectangle.</span></span>  
  
 <span data-ttu-id="cfbbb-120">![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span><span class="sxs-lookup"><span data-stu-id="cfbbb-120">![Ellipses and arcs](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbbb-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfbbb-121">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="cfbbb-122">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="cfbbb-122">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="cfbbb-123">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="cfbbb-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="cfbbb-124">方法: ペンを作成する</span><span class="sxs-lookup"><span data-stu-id="cfbbb-124">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="cfbbb-125">方法: 形状のアウトラインを描画する</span><span class="sxs-lookup"><span data-stu-id="cfbbb-125">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
