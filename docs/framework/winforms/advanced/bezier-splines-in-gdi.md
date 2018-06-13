---
title: B&#233;ベジエ スプライン GDI + で
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517574"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;ベジエ スプライン GDI + で
ベジエ スプラインは、4 つのポイントで指定された曲線: 次の 2 つの終点 (p1 と p2) と 2 つの制御ポイント (c1 と c2)。 曲線では、p1 で開始され、p2 で終了します。 コントロール ポイントを曲線が通過しませんが、管理ポイントが磁石、特定の方向に曲線をプルし、曲線曲がる方法に影響を与えるとして機能します。 次の図は、およびそのエンドポイントとの制御点のベジエ曲線を示します。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 曲線では、p1 で開始し、制御ポイント c1 に向かって移動します。 P1 における曲線接線は、c1 を p1 から描画される直線です。 エンドポイント p2 における接線は、c2 から p2 に描画される直線です。  
  
## <a name="drawing-bzier-splines"></a>ベジエ スプラインを描画します。  
 ベジエ スプラインを描画する必要がありますのインスタンス、<xref:System.Drawing.Graphics>クラスおよび<xref:System.Drawing.Pen>です。 インスタンス、<xref:System.Drawing.Graphics>クラスを提供、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッド、および<xref:System.Drawing.Pen>曲線を表示するために使用する線の色、幅などの属性を格納します。 <xref:System.Drawing.Pen>への引数の 1 つとして渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッドです。 残りの引数が渡される、<xref:System.Drawing.Graphics.DrawBezier%2A>メソッドは、エンドポイントとの制御点。 次の例は、開始位置 (0, 0) のベジエ スプラインを描画コントロール ポイント (40, 20) と (80、150)、および終了位置 (100, 10)。  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 次の図は、曲線、コントロール ポイント、および 2 つの接線を示します。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 ベジエ スプラインは、自動車の業界でデザインもともとサンピエール ベジエによって開発されました。 さまざまな種類のコンピューター支援設計で利用できることがわかっていますので、フォントの輪郭の定義にも使用されます。 ベジエ スプラインことで得られるさまざまな図形を次の図のうち一部を示しています。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [方法: ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
