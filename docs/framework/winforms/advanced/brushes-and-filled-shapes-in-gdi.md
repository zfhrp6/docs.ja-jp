---
title: "GDI+ でのブラシと塗りつぶされた図形 | Microsoft Docs"
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
  - "ブラシ, GDI+"
  - "ブラシ, グラデーション"
  - "塗りつぶされた図形, GDI+"
  - "GDI+, ブラシ"
  - "GDI+, 塗りつぶされた図形"
  - "グラデーション ブラシ"
  - "形状, GDI+"
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ でのブラシと塗りつぶされた図形
四角形や楕円などの閉じた図形は、アウトラインと内部から構成されます。  アウトラインはペンを使用して描画され、内部はブラシを使用して塗りつぶされます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、閉じた図形の内部を塗りつぶすためのブラシ クラスとして、<xref:System.Drawing.SolidBrush>、<xref:System.Drawing.Drawing2D.HatchBrush>、<xref:System.Drawing.TextureBrush>、<xref:System.Drawing.Drawing2D.LinearGradientBrush> 、および <xref:System.Drawing.Drawing2D.PathGradientBrush> が用意されています。  これらのクラスはすべて、<xref:System.Drawing.Brush> クラスを継承します。  ソリッド ブラシを使用して塗りつぶされた四角形と、ハッチ ブラシを使用して塗りつぶされた楕円を次の図に示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.png "Aboutgdip02\_art17")  
  
## ソリッド ブラシ  
 閉じた図形を塗りつぶすには、<xref:System.Drawing.Graphics> クラスのインスタンスと <xref:System.Drawing.Brush> オブジェクトが必要です。  <xref:System.Drawing.Graphics> クラスのインスタンスには、<xref:System.Drawing.Graphics.FillRectangle%2A> や <xref:System.Drawing.Graphics.FillEllipse%2A> などのメソッドが用意されています。<xref:System.Drawing.Brush> は、色やパターンなどの塗りつぶし属性を格納します。  <xref:System.Drawing.Brush> は、引数の 1 つとして塗りつぶしメソッドに渡されます。  楕円を純色の赤で塗りつぶす方法を次のコード例に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  上記の例のブラシは <xref:System.Drawing.SolidBrush> 型で、<xref:System.Drawing.Brush> から継承されています。  
  
## ハッチ ブラシ  
 ハッチ ブラシを使用して図形を塗りつぶす場合は、前景色、背景色、およびハッチ スタイルを指定します。  前景色はハッチングの色です。  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、50 種類を超えるハッチ スタイルが用意されています。<xref:System.Drawing.Drawing2D.HatchStyle>、<xref:System.Drawing.Drawing2D.HatchStyle>、および <xref:System.Drawing.Drawing2D.HatchStyle> の 3 つのスタイルを次の図に示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.png "Aboutgdip02\_art18")  
  
## テクスチャ ブラシ  
 テクスチャ ブラシを使用すると、ビットマップに格納されているパターンを使用して図形を塗りつぶすことができます。  たとえば、`MyTexture.bmp` という名前のディスク ファイルに、次のピクチャが格納されているとします。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.png "Aboutgdip02\_Art19")  
  
 `MyTexture.bmp` に格納されているピクチャを繰り返して楕円を塗りつぶすコード例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 塗りつぶされた楕円を次の図に示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.png "AboutGdip02\_Art20")  
  
## グラデーション ブラシ  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、線形とパスの 2 種類のグラデーション ブラシが用意されています。  線形グラデーション ブラシを使用すると、図形内を横方向、縦方向、または対角線方向に移動するのに応じて色を段階的に変化させながら図形を塗りつぶすことができます。  楕円の左端から右端へ移動するのに応じて、青から緑へ変化する横方向のグラデーション ブラシを使用して楕円を塗りつぶすコード例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 塗りつぶされた楕円を次の図に示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.png "AboutGdip02\_Art21")  
  
 パス グラデーション ブラシは、図形の中央から外縁に向かって移動するのに応じて色が変化するように設定できます。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.png "AboutGdip02\_Art22")  
  
 パス グラデーション ブラシは、柔軟性の高いブラシです。  グラデーション ブラシを使用して、中央の赤から頂点の 3 つの異なる色へ色が段階的に変化するように三角形を塗りつぶす例を次の図に示します。  
  
 ![塗りつぶされた図形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.png "AboutGdip02\_Art23")  
  
## 参照  
 <xref:System.Drawing.SolidBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=fullName>   
 <xref:System.Drawing.TextureBrush?displayProperty=fullName>   
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : Windows フォームに塗りつぶした四角形を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)   
 [方法 : Windows フォームに塗りつぶした楕円を描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)