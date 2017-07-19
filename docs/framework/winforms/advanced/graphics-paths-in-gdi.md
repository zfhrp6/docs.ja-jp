---
title: "GDI+ でのグラフィックス パス | Microsoft Docs"
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
  - "描画, パス"
  - "GDI+, 描画 (パスを)"
  - "グラフィックス, パス"
  - "パス, 描画"
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# GDI+ でのグラフィックス パス
パスは、直線、四角形、および単純な曲線を組み合わせて作成されます。  ピクチャの描画に最も適した基本的なビルド ブロックとして次の図形を使用できることは、「[ベクター グラフィックスの概要](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md)」で既に説明しました。  
  
-   線  
  
-   四角形  
  
-   楕円  
  
-   円弧  
  
-   多角形  
  
-   カーディナル スプライン  
  
-   ベジエ スプライン  
  
 GDI\+ の <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトを使用すると、複数のビルド ブロックから成るシーケンスを 1 つの単位として定義できます。  こうすると、直線、四角形、多角形、および曲線から成るシーケンス全体を <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawPath%2A> メソッドへの 1 回の呼び出しで描画できます。  直線、円弧、ベジエ スプライン、およびカーディナル スプラインを組み合わせて作成したパスを次の図に示します。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.png "Aboutgdip02\_art14")  
  
## パスの使用  
 The <xref:System.Drawing.Drawing2D.GraphicsPath> クラスには、描画される項目のシーケンスを作成するためのメソッドとして、<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> \(カーディナル スプライン用\)、および <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A> が用意されています。  これらの各メソッドはオーバーロードされています。つまり、各メソッドが複数の異なるパラメーター リストをサポートします。  たとえば、ある <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> メソッドは 4 個の整数を受け取り、別の <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> メソッドは 2 個の <xref:System.Drawing.Point> オブジェクトを受け取ります。  
  
 直線、四角形、およびベジエ スプラインをパスに追加するメソッドには、1 回の呼び出しで複数の項目をパスに追加するコンパニオン メソッドである <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>、<xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>、および <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A> があります。  また、<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> メソッドと <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> メソッドには、閉じた曲線または扇形をパスに追加するコンパニオン メソッド <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> と <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A> があります。  
  
 パスを描画するには、<xref:System.Drawing.Graphics> オブジェクト、<xref:System.Drawing.Pen> オブジェクト、および <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトは <xref:System.Drawing.Graphics.DrawPath%2A> メソッドを提供し、<xref:System.Drawing.Pen> オブジェクトはパスの描画に使用される線の幅や色などの属性を格納します。  <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトは、パスを構成する直線と曲線のシーケンスを格納します。  <xref:System.Drawing.Pen> オブジェクトと <xref:System.Drawing.Drawing2D.GraphicsPath> オブジェクトは、引数として <xref:System.Drawing.Graphics.DrawPath%2A> メソッドに渡されます。  直線、楕円、およびベジエ スプラインで構成されるパスを描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 このパスを次の図に示します。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.png "Aboutgdip02\_art15")  
  
 直線、四角形、および曲線をパスに追加する以外に、パスを別のパスに追加することもできます。  こうすると、既存のパスを組み合わせて、大きい複雑なパスを作成できます。  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 上記以外に、文字列と扇形の 2 種類の項目をパスに追加できます。  扇形は、楕円の内部にある一部分です。  円弧、カーディナル スプライン、文字列、および扇形からパスを作成する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 このパスを次の図に示します。  パスは連続している必要はありません。円弧、カーディナル スプライン、文字列、および扇形は分離されています。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.png "Aboutgdip02\_Art16")  
  
## 参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)