---
title: '方法: B のシーケンスを描画&#233;ベジエ スプライン'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 8439e08109630b9a59c8e0359aa4d18e5241412c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521408"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="9ccfe-102">方法: B のシーケンスを描画&#233;ベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="9ccfe-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="9ccfe-103">使用することができます、<xref:System.Drawing.Graphics.DrawBeziers%2A>のメソッド、<xref:System.Drawing.Graphics>のシーケンスを描画するクラスがベジエ スプラインを接続します。</span><span class="sxs-lookup"><span data-stu-id="9ccfe-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ccfe-104">例</span><span class="sxs-lookup"><span data-stu-id="9ccfe-104">Example</span></span>  
 <span data-ttu-id="9ccfe-105">次の例では、接続された 2 つのベジエ スプラインから成る曲線を描画します。</span><span class="sxs-lookup"><span data-stu-id="9ccfe-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="9ccfe-106">最初のベジエ スプラインのエンドポイントは、2 番目のベジエ スプラインの開始点です。</span><span class="sxs-lookup"><span data-stu-id="9ccfe-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="9ccfe-107">次の図では、接続されたスプライン 7 つの点とを示します。</span><span class="sxs-lookup"><span data-stu-id="9ccfe-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="9ccfe-108">![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="9ccfe-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ccfe-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9ccfe-109">Compiling the Code</span></span>  
 <span data-ttu-id="9ccfe-110">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="9ccfe-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccfe-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ccfe-111">See Also</span></span>  
 [<span data-ttu-id="9ccfe-112">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="9ccfe-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="9ccfe-113">GDI+ でのベジエ スプライン</span><span class="sxs-lookup"><span data-stu-id="9ccfe-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="9ccfe-114">曲線の作成と描画</span><span class="sxs-lookup"><span data-stu-id="9ccfe-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
