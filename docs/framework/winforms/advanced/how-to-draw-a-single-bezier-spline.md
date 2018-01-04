---
title: "方法: 描画単一 B &#233; ベジエ スプライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d2eaf570190f85ca084e5a5ab5d1bee1be56871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="f3b59-102">方法: 描画単一 B &#233; ベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="f3b59-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="f3b59-103">ベジエ スプラインを 4 つの点によって定義されます: 開始時点、2 つの制御ポイント、およびエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="f3b59-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b59-104">例</span><span class="sxs-lookup"><span data-stu-id="f3b59-104">Example</span></span>  
 <span data-ttu-id="f3b59-105">次の例では、(10, 100) の始点と終点 (200, 100) のベジエ スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="f3b59-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="f3b59-106">コントロールは (100, 10) と (150、150) をポイントします。</span><span class="sxs-lookup"><span data-stu-id="f3b59-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="f3b59-107">次の図は、その始点、コントロール ポイント、およびエンドポイントと共に結果として得られるベジエ スプラインを示します。</span><span class="sxs-lookup"><span data-stu-id="f3b59-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="f3b59-108">図には、直線で 4 つのポイントを接続することで形成される多角形スプラインの凸包です。</span><span class="sxs-lookup"><span data-stu-id="f3b59-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="f3b59-109">![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="f3b59-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3b59-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f3b59-110">Compiling the Code</span></span>  
 <span data-ttu-id="f3b59-111">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="f3b59-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b59-112">参照</span><span class="sxs-lookup"><span data-stu-id="f3b59-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [<span data-ttu-id="f3b59-113">GDI+ でのベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="f3b59-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="f3b59-114">方法: 一連のベジエ スプラインを描画する</span><span class="sxs-lookup"><span data-stu-id="f3b59-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
