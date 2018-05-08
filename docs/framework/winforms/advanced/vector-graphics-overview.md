---
title: ベクター グラフィックスの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: 31fec6d0d3769251d21783b4657d00b06431e942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="vector-graphics-overview"></a>ベクター グラフィックスの概要
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 座標系上線、四角形、およびその他の図形を描画します。 さまざまな座標システムから選択できますが、既定座標系では、左上隅の原点は、x 軸が右と下向き y 軸 をポイントします。 既定の座標システムでメジャーの単位は、ピクセルです。  
  
## <a name="the-building-blocks-of-gdi"></a>GDI + の構成要素  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 コンピューター モニターでは、ドット ピクチャ要素 (ピクセル) と呼ばれる四角形の配列をその表示を作成します。 1 つのモニターから、画面に表示されるピクセルの数が異なり、ユーザーが個々 のモニターに表示されるピクセルの数がある程度を構成する通常ことができます。  
  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 使用すると[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]線、四角形、または曲線を描画するには、描画される項目に関する特定のキー情報を提供します。 たとえば、2 つの点を提供することにより、行を指定でき、ポイント、高さ、幅を提供し、四角形を指定することができます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ディスプレイ ドライバー ソフトウェアは、線、四角形、または曲線の表示にするピクセルをオンにするかを決定すると連携して動作します。 次の図は、(4, 2) のポイントからポイント (12, 8) に線を表示するのになっている (ピクセル) を示します。  
  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 時間の経過と共に特定基本的なビルディング ブロックが証明された、最も有用である 2 次元の画像を作成するためです。 これらのビルド ブロックでサポートされている[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]は、次の一覧で指定します。  
  
-   線  
  
-   四角形  
  
-   省略記号ボタン  
  
-   円弧  
  
-   多角形  
  
-   カーディナル スプライン  
  
-   ベジエ スプライン  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>グラフィックス オブジェクトを使用した描画メソッド  
 <xref:System.Drawing.Graphics>クラス[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、前の一覧の項目を描画するための次のメソッドを提供: <xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawRectangle%2A>、 <xref:System.Drawing.Graphics.DrawEllipse%2A>、 <xref:System.Drawing.Graphics.DrawPolygon%2A>、 <xref:System.Drawing.Graphics.DrawArc%2A>、 <xref:System.Drawing.Graphics.DrawCurve%2A> (用カーディナル スプライン)、および<xref:System.Drawing.Graphics.DrawBezier%2A>. これらの各メソッドはオーバー ロードです。つまり、各メソッドは、いくつかの異なるパラメーター リストをサポートします。 たとえば、1 つバリエーションの 1 つの<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと別のバリエーションの中に、4 つの整数、<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと 2 つ<xref:System.Drawing.Point>オブジェクト。  
  
 線、四角形、およびベジエ スプラインを描画するためのメソッドが 1 回の呼び出しで複数の項目を描画する複数形のコンパニオン メソッドがある: <xref:System.Drawing.Graphics.DrawLines%2A>、 <xref:System.Drawing.Graphics.DrawRectangles%2A>、および<xref:System.Drawing.Graphics.DrawBeziers%2A>です。 また、<xref:System.Drawing.Graphics.DrawCurve%2A>メソッドには、コンパニオン メソッド<xref:System.Drawing.Graphics.DrawClosedCurve%2A>終了、開始する曲線の終点を接続することで、曲線ポイントします。  
  
 すべての描画メソッドの<xref:System.Drawing.Graphics>クラスと連携して動作する<xref:System.Drawing.Pen>オブジェクト。 何を描画するには、少なくとも 2 つのオブジェクトを作成する必要があります。<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。 <xref:System.Drawing.Pen>オブジェクトは線の幅と描画される項目の色などの属性を格納します。 <xref:System.Drawing.Pen>オブジェクトが描画メソッドに引数の 1 つとして渡されます。 たとえば、1 つバリエーションの 1 つの<xref:System.Drawing.Graphics.DrawLine%2A>メソッドは受信、<xref:System.Drawing.Pen>オブジェクトと幅が 100 で 50 の高さの左上隅の四角形を描画する次の例に示すように 4 つの整数 (20, 10)。  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)
