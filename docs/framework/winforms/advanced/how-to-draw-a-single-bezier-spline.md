---
title: '方法: 1 つの B を描画&#233;ベジエ スプライン'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 9e91b63275c37fc0cdde5721fddd114e1bf2264e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521337"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>方法: 1 つの B を描画&#233;ベジエ スプライン
ベジエ スプラインを 4 つの点によって定義されます: 開始時点、2 つの制御ポイント、およびエンドポイント。  
  
## <a name="example"></a>例  
 次の例では、(10, 100) の始点と終点 (200, 100) のベジエ スプラインを描画します。 コントロールは (100, 10) と (150、150) をポイントします。  
  
 次の図は、その始点、コントロール ポイント、およびエンドポイントと共に結果として得られるベジエ スプラインを示します。 図には、直線で 4 つのポイントを接続することで形成される多角形スプラインの凸包です。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [GDI+ でのベジエ スプライン](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [方法: 一連のベジエ スプラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
