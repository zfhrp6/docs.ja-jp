---
title: GDI+ でのペン、直線、および四角形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 86cc51006361d5628dc12999588520e28e62f166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+ でのペン、直線、および四角形
線を描画する[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]を作成する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトが実際には、描画を実行するメソッドを提供し、<xref:System.Drawing.Pen>オブジェクトは線の色、幅、およびスタイルなどの属性を格納します。  
  
## <a name="drawing-a-line"></a>直線を描画します。  
 線を描画する呼び出し、<xref:System.Drawing.Graphics.DrawLine%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。 <xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドです。 次の例は、(12, 6) のポイントに点 (4, 2) から線を描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。 2 つ構築など、<xref:System.Drawing.Point>オブジェクトやパス、<xref:System.Drawing.Point>オブジェクトへの引数として、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド。  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>ペンを作成します。  
 構築するときに特定の属性を指定することができます、<xref:System.Drawing.Pen>オブジェクト。 たとえば、1 つ`Pen`コンス トラクターでは、色と幅を指定することができます。 次の例は、幅 2 からの青い線を描画 (0, 0) に (60, 30)。  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>破線とライン キャップ  
 <xref:System.Drawing.Pen>オブジェクトもプロパティを公開など<xref:System.Drawing.Pen.DashStyle%2A>行の機能を指定を行えます。 次の例から破線を描画する (100, 50) に (300, 80)。  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 プロパティを使用することができます、<xref:System.Drawing.Pen>以上、多くの行の属性を設定するオブジェクト。 <xref:System.Drawing.Pen.StartCap%2A>と<xref:System.Drawing.Pen.EndCap%2A>プロパティが、線の端の外観を指定以外の場合は、終了は、フラット、正方形、角の丸い、三角形、またはカスタムの形状。 <xref:System.Drawing.Pen.LineJoin%2A>プロパティを使用して、接続されている直線がかどうかマイター (とがった角に参加している)、傾斜、丸め、クリップを指定できます。 次の図は、さまざまな cap と結合のスタイルを使用して行を示します。  
  
 ![行](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>四角形の描画  
 長方形を描画[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]直線の描画に似ています。 四角形を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは線の幅、色などの属性を格納します。 <xref:System.Drawing.Pen>オブジェクトが渡される引数の 1 つとして、<xref:System.Drawing.Graphics.DrawRectangle%2A>メソッドです。 次の例で左上隅を四角形を描画する (100, 50)、80、幅と高さ 40。  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> オーバー ロードされたメソッド、<xref:System.Drawing.Graphics>クラスの引数を指定することがいくつかの方法があるようにします。 たとえば、構成することができます、<xref:System.Drawing.Rectangle>オブジェクトを渡す、<xref:System.Drawing.Rectangle>オブジェクトを<xref:System.Drawing.Graphics.DrawRectangle%2A>引数としてメソッド。  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A<xref:System.Drawing.Rectangle>オブジェクトがメソッドとプロパティを操作すると、四角形に関する情報を収集します。 たとえば、<xref:System.Drawing.Rectangle.Inflate%2A>と<xref:System.Drawing.Rectangle.Offset%2A>メソッドは、四角形の位置とサイズを変更します。 <xref:System.Drawing.Rectangle.IntersectsWith%2A>メソッドに指示するかどうか、四角形他と交差する四角形を指定し、<xref:System.Drawing.Rectangle.Contains%2A>メソッドは、特定の時点が四角形の内側がかどうかを示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [方法: ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [方法: Windows フォームに直線を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [方法: 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
