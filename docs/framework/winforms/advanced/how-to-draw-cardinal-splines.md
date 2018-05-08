---
title: '方法 : カーディナル スプラインを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 3ad06eb28e1d8e6b5d5f4a77e545f174d8a68d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-cardinal-splines"></a>方法 : カーディナル スプラインを描画する
カーディナル スプラインとは、指定された一連のポイントをスムーズに通過する曲線です。 カーディナル スプラインを描画するには、作成、<xref:System.Drawing.Graphics>オブジェクトおよびへのポインターの配列のアドレスを渡す、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドです。  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>ベル型のカーディナル スプラインを描画します。  
  
-   次の例では、5 つの指定した点をベル型のカーディナル スプラインを描画します。 次の図は、曲線、5 つの点を示します。  
  
     ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>閉じたカーディナル スプラインを描画します。  
  
-   使用して、<xref:System.Drawing.Graphics.DrawClosedCurve%2A>のメソッド、<xref:System.Drawing.Graphics>閉じたカーディナル スプラインを描画するクラス。 閉じたカーディナル スプライン曲線配列の最後の点までで、配列の最初のポイントを使用して接続します。 次の例では、6 つの指定した点を通過した閉じたカーディナル スプラインを描画します。 次の図は、6 個のポイントと共に閉じたスプラインを示します。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>カーディナル スプラインの変更  
  
-   カーディナル スプラインをテンションの引数を渡すことによって曲がる方法を変更する、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドです。 次の例では、同じ点のセットを通過する 3 つのカーディナル スプラインを描画します。 次の図では、次の 3 つスプラインそのテンション値とを示します。 テンションが 0 の場合に、そのポイントが直線で接続されていることを注意してください。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用する用に設計され、必要な<xref:System.Windows.Forms.PaintEventArgs>`e`はのパラメーターである、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。  
  
## <a name="see-also"></a>関連項目  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
