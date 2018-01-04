---
title: "方法 : カーディナル スプラインを描画する"
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
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64661bbdcb267e2f2ce33b8a8db2ab2aac9a86f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-cardinal-splines"></a><span data-ttu-id="37ad2-102">方法 : カーディナル スプラインを描画する</span><span class="sxs-lookup"><span data-stu-id="37ad2-102">How to: Draw Cardinal Splines</span></span>
<span data-ttu-id="37ad2-103">カーディナル スプラインとは、指定された一連のポイントをスムーズに通過する曲線です。</span><span class="sxs-lookup"><span data-stu-id="37ad2-103">A cardinal spline is a curve that passes smoothly through a given set of points.</span></span> <span data-ttu-id="37ad2-104">カーディナル スプラインを描画するには、作成、<xref:System.Drawing.Graphics>オブジェクトおよびへのポインターの配列のアドレスを渡す、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="37ad2-104">To draw a cardinal spline, create a <xref:System.Drawing.Graphics> object and pass the address of an array of points to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span>  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a><span data-ttu-id="37ad2-105">ベル型のカーディナル スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-105">Drawing a Bell-Shaped Cardinal Spline</span></span>  
  
-   <span data-ttu-id="37ad2-106">次の例では、5 つの指定した点をベル型のカーディナル スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-106">The following example draws a bell-shaped cardinal spline that passes through five designated points.</span></span> <span data-ttu-id="37ad2-107">次の図は、曲線、5 つの点を示します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-107">The following illustration shows the curve and five points.</span></span>  
  
     <span data-ttu-id="37ad2-108">![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span><span class="sxs-lookup"><span data-stu-id="37ad2-108">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a><span data-ttu-id="37ad2-109">閉じたカーディナル スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-109">Drawing a Closed Cardinal Spline</span></span>  
  
-   <span data-ttu-id="37ad2-110">使用して、<xref:System.Drawing.Graphics.DrawClosedCurve%2A>のメソッド、<xref:System.Drawing.Graphics>閉じたカーディナル スプラインを描画するクラス。</span><span class="sxs-lookup"><span data-stu-id="37ad2-110">Use the <xref:System.Drawing.Graphics.DrawClosedCurve%2A> method of the <xref:System.Drawing.Graphics> class to draw a closed cardinal spline.</span></span> <span data-ttu-id="37ad2-111">閉じたカーディナル スプライン曲線配列の最後の点までで、配列の最初のポイントを使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-111">In a closed cardinal spline, the curve continues through the last point in the array and connects with the first point in the array.</span></span> <span data-ttu-id="37ad2-112">次の例では、6 つの指定した点を通過した閉じたカーディナル スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-112">The following example draws a closed cardinal spline that passes through six designated points.</span></span> <span data-ttu-id="37ad2-113">次の図は、6 個のポイントと共に閉じたスプラインを示します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-113">The following illustration shows the closed spline along with the six points.</span></span>  
  
 <span data-ttu-id="37ad2-114">![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span><span class="sxs-lookup"><span data-stu-id="37ad2-114">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a><span data-ttu-id="37ad2-115">カーディナル スプラインの変更</span><span class="sxs-lookup"><span data-stu-id="37ad2-115">Changing the Bend of a Cardinal Spline</span></span>  
  
-   <span data-ttu-id="37ad2-116">カーディナル スプラインをテンションの引数を渡すことによって曲がる方法を変更する、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="37ad2-116">Change the way a cardinal spline bends by passing a tension argument to the <xref:System.Drawing.Graphics.DrawCurve%2A> method.</span></span> <span data-ttu-id="37ad2-117">次の例では、同じ点のセットを通過する 3 つのカーディナル スプラインを描画します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-117">The following example draws three cardinal splines that pass through the same set of points.</span></span> <span data-ttu-id="37ad2-118">次の図では、次の 3 つスプラインそのテンション値とを示します。</span><span class="sxs-lookup"><span data-stu-id="37ad2-118">The following illustration shows the three splines along with their tension values.</span></span> <span data-ttu-id="37ad2-119">テンションが 0 の場合に、そのポイントが直線で接続されていることを注意してください。</span><span class="sxs-lookup"><span data-stu-id="37ad2-119">Note that when the tension is 0, the points are connected by straight lines.</span></span>  
  
 <span data-ttu-id="37ad2-120">![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span><span class="sxs-lookup"><span data-stu-id="37ad2-120">![Cardinal Spline](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37ad2-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="37ad2-121">Compiling the Code</span></span>  
 <span data-ttu-id="37ad2-122">前の例は、Windows フォームで使用する用に設計され、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーターである、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="37ad2-122">The preceding examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ad2-123">参照</span><span class="sxs-lookup"><span data-stu-id="37ad2-123">See Also</span></span>  
 [<span data-ttu-id="37ad2-124">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="37ad2-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="37ad2-125">曲線の作成と描画</span><span class="sxs-lookup"><span data-stu-id="37ad2-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
