---
title: GDI+ での多角形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525848"
---
# <a name="polygons-in-gdi"></a>GDI+ での多角形
多角形は、次の 3 つまたは複数の辺に閉じた形状です。 たとえば、三角形は、次の 3 つの辺の多角形、四角形は、4 辺の多角形および五角形は、5 つの辺の多角形です。 次の図は、いくつかの多角形を示します。  
  
 ![多角形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>多角形の描画  
 多角形を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Pen>オブジェクト、および配列の<xref:System.Drawing.Point>(または<xref:System.Drawing.PointF>) オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawPolygon%2A>メソッドです。 <xref:System.Drawing.Pen>オブジェクトは、多角形の配列およびを表示するために使用する線の色、幅などの属性を格納<xref:System.Drawing.Point>オブジェクトは、直線で接続するポイントを格納します。 <xref:System.Drawing.Pen>オブジェクトの配列および<xref:System.Drawing.Point>オブジェクトへの引数として渡される、<xref:System.Drawing.Graphics.DrawPolygon%2A>メソッドです。 次の例では、3 つの辺の多角形を描画します。 内の 3 つだけのポイントがあることに注意してください`myPointArray`: (0, 0)、(50, 30)、および (30、60)。 <xref:System.Drawing.Graphics.DrawPolygon%2A>メソッドから行を描画して、多角形を自動的に閉じる (30、60) 開始ポイント (0, 0) に戻ります。  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 次の図は、多角形を示します。  
  
 ![多角形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
