---
title: GDI+ での開いた曲線と閉じた曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527149"
---
# <a name="open-and-closed-curves-in-gdi"></a>GDI+ での開いた曲線と閉じた曲線
次の図に、2 つの曲線: 1 つが開いて、もう 1 つが終了します。  
  
 ![開いた曲線と閉じた曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>曲線の管理インターフェイス  
 閉じた曲線では、内部があるし、ブラシを使用して入力することができます。 <xref:System.Drawing.Graphics>クラス内で[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]閉じた図形と曲線を塗りつぶすときの次のメソッドを提供します。 <xref:System.Drawing.Graphics.FillRectangle%2A>、 <xref:System.Drawing.Graphics.FillEllipse%2A>、 <xref:System.Drawing.Graphics.FillPie%2A>、 <xref:System.Drawing.Graphics.FillPolygon%2A>、 <xref:System.Drawing.Graphics.FillClosedCurve%2A>、 <xref:System.Drawing.Graphics.FillPath%2A>、と<xref:System.Drawing.Graphics.FillRegion%2A>です。 これらのメソッドのいずれかを呼び出すたびに、特定のブラシの種類のいずれかを渡す必要があります (<xref:System.Drawing.SolidBrush>、 <xref:System.Drawing.Drawing2D.HatchBrush>、 <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、または<xref:System.Drawing.Drawing2D.PathGradientBrush>) を引数として。  
  
 <xref:System.Drawing.Graphics.FillPie%2A>メソッドは、対応する、<xref:System.Drawing.Graphics.DrawArc%2A>メソッドです。 同様、<xref:System.Drawing.Graphics.DrawArc%2A>メソッドは、楕円の輪郭の部分を描画、<xref:System.Drawing.Graphics.FillPie%2A>メソッドは、楕円の内部の一部を入力します。 次の例では、円弧を描画し、対応する部分楕円の内部を塗りつぶします。  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 次の図は、円弧と塗りつぶされた円グラフを示します。  
  
 ![開いた曲線と閉じた曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A>メソッドは、対応する、<xref:System.Drawing.Graphics.DrawClosedCurve%2A>メソッドです。 両方のメソッドは、自動的に開始点、終点を接続することで、曲線を閉じます。 次の例を通過する曲線の描画 (0, 0)、(60, 20)、および (40、50)。 接続することで、曲線が自動的に閉じられますし、(40、50) 開始ポイント (0, 0) にし、内部が純色で塗りつぶされます。  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A>メソッドは、パスの別の部分の内部を塗りつぶします。 場合は、閉じた曲線または図形、パスの一部を形成しません、<xref:System.Drawing.Graphics.FillPath%2A>メソッドでは、入力する前に、パスの部分を自動的に閉じます。 次の例を描画し、円弧、通過するカーディナル スプライン、文字列、および、円グラフで構成されるパスを入力します。  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 次の図は、および塗りつぶしの純使用せずに、パスを示します。 文字列内のテキストが記載されている、ですが、格納されていないによって、<xref:System.Drawing.Graphics.DrawPath%2A>メソッドです。 <xref:System.Drawing.Graphics.FillPath%2A>文字列内の文字の内部を描画するメソッド。  
  
 ![パス内の文字列](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
