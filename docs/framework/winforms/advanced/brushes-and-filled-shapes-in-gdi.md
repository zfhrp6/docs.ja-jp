---
title: GDI+ でのブラシと塗りつぶされた図形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 9475518a5f0422e0eac1ec521088071bb4d1c885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519000"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ でのブラシと塗りつぶされた図形
四角形や楕円など、閉じた図形は、概要と、内部で構成されます。 ペンを使用して、アウトラインが描画され、内部はブラシと塗りつぶされます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 閉じた図形の内部を塗りつぶすときのいくつかのブラシ クラスを提供します。 <xref:System.Drawing.SolidBrush>、 <xref:System.Drawing.Drawing2D.HatchBrush>、 <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、および<xref:System.Drawing.Drawing2D.PathGradientBrush>です。 継承するすべてのクラス、<xref:System.Drawing.Brush>クラスです。 次の図は、四角形とソリッド ブラシ、ハッチ ブラシを使用して塗りつぶした楕円を示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>ソリッド ブラシ  
 閉じた図形を塗りつぶす必要がありますのインスタンス、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Brush>です。 インスタンス、<xref:System.Drawing.Graphics>クラスなど、メソッドを提供<xref:System.Drawing.Graphics.FillRectangle%2A>と<xref:System.Drawing.Graphics.FillEllipse%2A>、および<xref:System.Drawing.Brush>の色やパターンなど、塗りつぶしの属性を格納します。 <xref:System.Drawing.Brush> Fill メソッドに引数の 1 つとして渡されます。 次のコード例では、楕円を純色の赤に設定する方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  前の例では、ブラシが型で<xref:System.Drawing.SolidBrush>から継承される<xref:System.Drawing.Brush>です。  
  
## <a name="hatch-brushes"></a>ハッチ ブラシ  
 ハッチ ブラシを使用して図形を塗りつぶすときは、前景の色、背景色と陰影のスタイルを指定します。 前景色、陰影の色であります。  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 50 以上の陰影のスタイル; は、します。次の図に示すように 3 つのスタイルが<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>、 <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>、および<xref:System.Drawing.Drawing2D.HatchStyle.Cross>です。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>テクスチャ ブラシ  
 テクスチャ ブラシを使用して、ビットマップに格納されているパターンで図形を塗りつぶすことができます。 たとえば、次の図は、というディスク ファイルに格納されている`MyTexture.bmp`です。  
  
 ![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 次のコード例に格納されている画像の繰り返しで、省略記号を入力する方法を示しています。`MyTexture.bmp`です。  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 次の図は、塗りつぶされた楕円を示します。  
  
 ![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>グラデーション ブラシ  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] グラデーション ブラシの 2 種類の説明: 線形とパス。 線形グラデーション ブラシを使用して、図形を塗りつぶす色が徐々 に水平、垂直方向には、図形間で移動すると、または対角線方向に変化することができます。 次のコード例では、楕円の左端から右端に移動すると、青から緑色に変化する水平グラデーション ブラシで楕円を塗りつぶす方法を示します。  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 次の図は、塗りつぶされた楕円を示します。  
  
 ![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 端に図形の中心から移動すると、色を変更するのには、パス グラデーション ブラシを構成できます。  
  
 ![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 パス グラデーション ブラシは非常に柔軟なです。 グラデーション ブラシ、次の図は徐々 に中央の赤からに変更の頂点で 3 つの異なる色の三角形の塗りつぶしに使用します。  
  
 ![図形の入力](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: Windows フォームに塗りつぶした四角形を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [方法: Windows フォームに塗りつぶした楕円を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
