---
title: "GDI+ での開いた曲線と閉じた曲線 | Microsoft Docs"
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
  - "曲線"
  - "曲線, 描画"
  - "曲線, 塗りつぶし"
  - "GDI+, 曲線"
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ での開いた曲線と閉じた曲線
開いた曲線と閉じた曲線を次の図に示します。  
  
 ![開いた曲線と閉じた曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.png "Aboutgdip02\_art24")  
  
## 曲線の管理インターフェイス  
 閉じた曲線には内部があるため、ブラシを使用して塗りつぶすことができます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の <xref:System.Drawing.Graphics> クラスには、閉じた図形および曲線を塗りつぶすためのメソッドとして、<xref:System.Drawing.Graphics.FillRectangle%2A>、<xref:System.Drawing.Graphics.FillEllipse%2A>、<xref:System.Drawing.Graphics.FillPie%2A>、<xref:System.Drawing.Graphics.FillPolygon%2A>、<xref:System.Drawing.Graphics.FillClosedCurve%2A>、<xref:System.Drawing.Graphics.FillPath%2A>、および <xref:System.Drawing.Graphics.FillRegion%2A> が用意されています。  これらのメソッドの 1 つを呼び出す場合は、特定のブラシ型 \(<xref:System.Drawing.SolidBrush>、<xref:System.Drawing.Drawing2D.HatchBrush>、<xref:System.Drawing.TextureBrush>、<xref:System.Drawing.Drawing2D.LinearGradientBrush>、または <xref:System.Drawing.Drawing2D.PathGradientBrush>\) の 1 つを引数として渡す必要があります。  
  
 <xref:System.Drawing.Graphics.FillPie%2A> メソッドは、<xref:System.Drawing.Graphics.DrawArc%2A> メソッドのコンパニオン メソッドです。  <xref:System.Drawing.Graphics.DrawArc%2A> メソッドが楕円のアウトラインの一部を描画するのと同様に、<xref:System.Drawing.Graphics.FillPie%2A> メソッドは楕円の内部の一部を塗りつぶします。  円弧を描画し、その円弧に対応する楕円の内部の一部を塗りつぶす例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 円弧と塗りつぶされた扇形を次の図に示します。  
  
 ![開いた曲線と閉じた曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.png "Aboutgdip02\_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> メソッドは、<xref:System.Drawing.Graphics.DrawClosedCurve%2A> メソッドのコンパニオン メソッドです。  この 2 つのメソッドは、終了点と開始点を連結することによって曲線を自動的に閉じます。  \(0, 0\)、\(60, 20\)、および \(40, 50\) を通過する曲線を描画する例を次に示します。  次に、\(40, 50\) と開始点 \(0, 0\) を連結することによって曲線を自動的に閉じ、内部を純色で塗りつぶします。  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> メソッドは、1 つのパスの各部分の内部を塗りつぶします。  パスの 1 つの部分が閉じた曲線または図形を形成していない場合、<xref:System.Drawing.Graphics.FillPath%2A> メソッドは、塗りつぶす前にパスのその部分を自動的に閉じます。  円弧、カーディナル スプライン、文字列、および扇形で構成されるパスを描画し、その内部を塗りつぶす例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 純色で塗りつぶしたパスと、塗りつぶしていないパスを次の図に示します。  <xref:System.Drawing.Graphics.DrawPath%2A> メソッドによって文字列内のテキストのアウトラインは描画されていますが、内部は塗りつぶされていません。  文字列の文字の内部を塗りつぶすのは、<xref:System.Drawing.Graphics.FillPath%2A> メソッドです。  
  
 ![パスの文字列](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.png "Aboutgdip02\_art26")  
  
## 参照  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 <xref:System.Drawing.Point?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [パスの作成および描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)