---
title: "GDI+ でのベジエ スプライン | Microsoft Docs"
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
  - "ベジエ スプライン"
  - "GDI+, ベジエ スプライン"
  - "スプライン, ベジエ"
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# GDI+ でのベジエ スプライン
ベジエ スプラインは、4 つの点、つまり 2 つのエンドポイント \(p1 と p2\) と 2 つの制御点 \(c1 と c2\) によって指定される曲線です。  曲線は p1 で開始され、p2 で終了します。  この曲線は制御点を通過しません。しかし、制御点は磁石のような役割を果たし、曲線を特定の方向に引っ張って曲線の曲がり方を制御します。  ベジエ曲線およびそのエンドポイントと制御点を次の図に示します。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.png "Aboutgdip02\_art11a")  
  
 曲線は p1 で開始され、制御点 c1 に向かって移動します。  p1 における曲線の接線は、p1 と c1 を結ぶ直線です。  エンドポイント p2 における接線は、c2 と p2 を結ぶ直線です。  
  
## ベジエ スプラインの描画  
 ベジエ スプラインを描画するには、<xref:System.Drawing.Graphics> クラスのインスタンスと <xref:System.Drawing.Pen> が必要です。  <xref:System.Drawing.Graphics> クラスのインスタンスは <xref:System.Drawing.Graphics.DrawBezier%2A> メソッドを提供し、<xref:System.Drawing.Pen> は曲線を描画するために使用される線の幅や色などの属性を格納します。  <xref:System.Drawing.Pen> は、引数の 1 つとして <xref:System.Drawing.Graphics.DrawBezier%2A> メソッドに渡されます。  <xref:System.Drawing.Graphics.DrawBezier%2A> メソッドに渡される他の引数は、エンドポイントと制御点です。  開始点 \(0, 0\)、制御点 \(40, 20\) および \(80, 150\)、終了点 \(100, 10\) のベジエ スプラインを描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 曲線、制御点、および 2 つの接線を次の図に示します。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.png "Aboutgdip02\_art12")  
  
 ベジエ スプラインは、自動車業界向けのデザイン用に Pierre Bézier 氏によって開発されました。  それ以降、ベジエ スプラインはコンピューター支援設計のさまざまな用途で利用できることが実証され、フォントのアウトラインの定義にも使用されています。  ベジエ スプラインで作成できるさまざまな図形のいくつかを次の図に示します。  
  
 ![パス](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.png "Aboutgdip02\_art13")  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [方法 : ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)