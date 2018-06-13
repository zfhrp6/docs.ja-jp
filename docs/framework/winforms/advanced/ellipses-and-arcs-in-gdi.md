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
ms.locfileid: "33522110"
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+ での楕円および円弧
楕円と円弧を使用して簡単に描画することができます、<xref:System.Drawing.Graphics.DrawEllipse%2A>と<xref:System.Drawing.Graphics.DrawArc%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。  
  
## <a name="drawing-an-ellipse"></a>楕円を描画  
 楕円を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、省略記号を表示するために使用する線の色、幅などの属性を格納します。 <xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドです。 残りの引数が渡される、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドは、楕円の外接する四角形を指定します。 次の図は、その外接する四角形と楕円を描画します。  
  
 ![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 楕円を描画する次の例外接する四角形が 80、40 の高さとの左上隅の幅 (100, 50)。  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。 たとえば、構成することができます、<xref:System.Drawing.Rectangle>を渡すと、<xref:System.Drawing.Rectangle>を<xref:System.Drawing.Graphics.DrawEllipse%2A>引数としてメソッド。  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>円弧を描画します。  
 円弧は、楕円の一部です。 円弧を描くを呼び出す、<xref:System.Drawing.Graphics.DrawArc%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。 パラメーター、<xref:System.Drawing.Graphics.DrawArc%2A>メソッドのパラメーターと同じでは、<xref:System.Drawing.Graphics.DrawEllipse%2A>メソッドの点を除いて、<xref:System.Drawing.Graphics.DrawArc%2A>開始角度および掃引角度が必要です。 次の例では、30 度の開始角度および掃引角度が 180 度の円弧を描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 次の図は、円弧、楕円、および外接する四角形を示します。  
  
 ![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [方法: ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [方法: 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
