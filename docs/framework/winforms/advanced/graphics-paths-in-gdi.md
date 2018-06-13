---
title: GDI+ でのグラフィックス パス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523889"
---
# <a name="graphics-paths-in-gdi"></a>GDI+ でのグラフィックス パス
パスは、線、四角形、および単純な曲線を組み合わせることで形成されます。 メッセージの取り消し、[ベクター グラフィックスの概要](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)基本的な構成要素は次の図を描画するため、最も役に立つことが証明されたこと。  
  
-   線  
  
-   四角形  
  
-   省略記号ボタン  
  
-   円弧  
  
-   多角形  
  
-   カーディナル スプライン  
  
-   ベジエ スプライン  
  
 GDI + での<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトでは、1 つの単位にこれらの構成要素のシーケンスを収集することができます。 1 回の呼び出しで、線、四角形を多角形、および曲線のシーケンス全体を描画し、ことができます、<xref:System.Drawing.Graphics.DrawPath%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。 次の図は、行、円弧をベジエ スプラインを通過するカーディナル スプラインを組み合わせることによって作成されるパスを示します。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>パスを使用します。  
 <xref:System.Drawing.Drawing2D.GraphicsPath>クラスが描画される項目のシーケンスを作成するための次のメソッドを提供: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (用カーディナル スプライン)、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>です。 これらの各メソッドはオーバー ロードです。つまり、各メソッドは、いくつかの異なるパラメーター リストをサポートします。 たとえば、1 つバリエーションの 1 つの<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドは、4 つの整数と別のバリエーションを受信、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>メソッドは、2 つ受け取ります<xref:System.Drawing.Point>オブジェクト。  
  
 線、四角形、およびベジエ スプラインをパスに追加するためのメソッドを 1 つの呼び出しパスにいくつかの項目を追加する複数形のコンパニオン メソッドがある: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>、 <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>、および<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>です。 また、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>メソッドがあるコンパニオン メソッド<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>と<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>パスに閉じた曲線または円グラフを追加します。  
  
 パスの描画、する必要があります、<xref:System.Drawing.Graphics>オブジェクト、<xref:System.Drawing.Pen>オブジェクト、および<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawPath%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、パスを表示するために使用する線の色、幅などの属性を格納します。 <xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトは、直線と曲線のパスを構成するのシーケンスを格納します。 <xref:System.Drawing.Pen>オブジェクトおよび<xref:System.Drawing.Drawing2D.GraphicsPath>への引数として渡されるオブジェクト、<xref:System.Drawing.Graphics.DrawPath%2A>メソッドです。 次の例では、パスは、行、楕円、およびベジエ スプラインを描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 次の図は、パスを示します。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 にパスを線、四角形、および曲線を追加するだけでなく、パスにパスを追加できます。 これにより、大規模で複雑なパスを形成する既存のパスを結合することができます。  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 パスに追加できる他の 2 つの項目がある: 文字列と扇形です。 円、楕円の内部の一部です。 次の例では、円弧、通過するカーディナル スプライン、文字列、および、円グラフからパスを作成します。  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 次の図は、パスを示します。 接続されている; パスがないことに注意してください。弧をカーディナル スプライン、文字列、および円グラフが区切られます。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
