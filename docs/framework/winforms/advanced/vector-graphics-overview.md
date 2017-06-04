---
title: "ベクター グラフィックスの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "座標系"
  - "グラフィックス, ベクター グラフィックス"
  - "包括 (描画時に両側の端点を)"
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# ベクター グラフィックスの概要
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、直線や四角形などの図形を座標系内で描画します。  さまざまな座標系を選択できますが、既定の座標系は原点が左上隅、x 軸が右向き、y 軸が下向きの座標系です。  既定の座標系での単位はピクセルです。  
  
## GDI\+ のビルド ブロック  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art01.png "AboutGdip02\_Art01")  
  
 コンピューターのモニターでは、画素 \(ピクセル\) と呼ばれるドットから構成される四角形の配列上に表示が生成されます。  画面上に表示されるピクセルの数はモニターごとに異なります。通常、それぞれのモニターに表示されるピクセルの数は、一定の範囲内でユーザーが設定できます。  
  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art02.png "AboutGdip02\_Art02")  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して直線、四角形、または曲線を描画する場合は、項目を描画するために基本的な情報を指定します。  たとえば、2 点を定義すると直線を指定でき、1 点、高さ、および幅を定義すると四角形を指定できます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] とディスプレイ ドライバー ソフトウェアによって、直線、四角形、または曲線を表示するためにどのピクセルをオンにするかが決定されます。  点 \(4, 2\) から点 \(12, 8\) まで直線を表示するためにオンにされているピクセルを次の図に示します。  
  
 ![ベクター グラフィックス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art03.png "AboutGdip02\_Art03")  
  
 2 次元ピクチャの作成に最も適した基本的なビルド ブロックとして、いくつかの図形を使用できることが実証されています。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] によってすべてサポートされる、これらのビルド ブロックを次に示します。  
  
-   線  
  
-   四角形  
  
-   楕円  
  
-   円弧  
  
-   多角形  
  
-   カーディナル スプライン  
  
-   ベジエ スプライン  
  
## グラフィックス オブジェクトを使用した描画方法  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の <xref:System.Drawing.Graphics> クラスは、上記の項目を描画するためのメソッドとして、<xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawRectangle%2A>、<xref:System.Drawing.Graphics.DrawEllipse%2A>、<xref:System.Drawing.Graphics.DrawPolygon%2A>、<xref:System.Drawing.Graphics.DrawArc%2A>、<xref:System.Drawing.Graphics.DrawCurve%2A> \(カーディナル スプライン用\)、および <xref:System.Drawing.Graphics.DrawBezier%2A> を提供します。  これらの各メソッドはオーバーロードされています。つまり、各メソッドが複数の異なるパラメーター リストをサポートします。  たとえば、ある <xref:System.Drawing.Graphics.DrawLine%2A> メソッドは <xref:System.Drawing.Pen> オブジェクトと 4 個の整数を受け取り、別の <xref:System.Drawing.Graphics.DrawLine%2A> メソッドは <xref:System.Drawing.Pen> オブジェクトと 2 個の <xref:System.Drawing.Point> オブジェクトを受け取ります。  
  
 直線、四角形、およびベジエ スプラインを描画するためのメソッドには、1 回の呼び出しで複数の項目を描画するコンパニオン メソッドである <xref:System.Drawing.Graphics.DrawLines%2A>、<xref:System.Drawing.Graphics.DrawRectangles%2A>、および <xref:System.Drawing.Graphics.DrawBeziers%2A> があります。  また、<xref:System.Drawing.Graphics.DrawCurve%2A> メソッドにも、曲線の終了点と開始点を連結することによって曲線を閉じるコンパニオン メソッド <xref:System.Drawing.Graphics.DrawClosedCurve%2A> があります。  
  
 <xref:System.Drawing.Graphics> クラスのすべての描画メソッドは、<xref:System.Drawing.Pen> オブジェクトと共に機能します。  図形を描画するためには、少なくとも <xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトの 2 つのオブジェクトを作成する必要があります。  <xref:System.Drawing.Pen> オブジェクトには、描画される項目の属性として、線の幅や色などが格納されます。  <xref:System.Drawing.Pen> オブジェクトは、引数の 1 つとして描画メソッドに渡されます。  たとえば、ある <xref:System.Drawing.Graphics.DrawLine%2A> メソッドは、次の例に示すように <xref:System.Drawing.Pen> オブジェクトと 4 個の整数を受け取ります。このメソッドは、幅 100、高さ 50、左上隅 \(20, 10\) の四角形を描画します。  
  
 [!code-csharp[LinesCurvesAndShapes#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)