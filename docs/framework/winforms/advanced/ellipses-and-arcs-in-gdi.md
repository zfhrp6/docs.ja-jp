---
title: "GDI+ での楕円および円弧 | Microsoft Docs"
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
  - "円弧"
  - "描画, 円弧"
  - "描画, 楕円"
  - "楕円"
  - "GDI+, 円弧"
  - "GDI+, 楕円"
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# GDI+ での楕円および円弧
<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドおよび <xref:System.Drawing.Graphics.DrawArc%2A> メソッドを使用すると、楕円と円弧を簡単に描画できます。  
  
## 楕円の描画  
 楕円を描画するには、<xref:System.Drawing.Graphics> オブジェクトと <xref:System.Drawing.Pen> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトには <xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドが用意されており、<xref:System.Drawing.Pen> オブジェクトには楕円の描画に使用する線の幅や色などの属性が格納されます。  <xref:System.Drawing.Pen> オブジェクトは、引数の 1 つとして <xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドに渡されます。  <xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドに渡される他の引数は、楕円に外接する四角形を指定します。  楕円とその楕円に外接する四角形を次の図に示します。  
  
 ![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.png "Aboutgdip02\_art05")  
  
 楕円を描画する例を次に示します。外接する四角形は、幅 80、高さ 40、左上隅 \(100, 50\) です。  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> は <xref:System.Drawing.Graphics> クラスのオーバーロードされたメソッドであるため、いくつかの方法でこのメソッドの引数を指定できます。  たとえば、<xref:System.Drawing.Rectangle> を構築して、その <xref:System.Drawing.Rectangle> を引数として <xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドに渡すことができます。  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## 円弧の描画  
 円弧は、楕円の一部です。  円弧を描画するには、<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawArc%2A> メソッドを呼び出します。  <xref:System.Drawing.Graphics.DrawArc%2A> メソッドのパラメーターは、<xref:System.Drawing.Graphics.DrawEllipse%2A> メソッドのパラメーターと基本的に同じです。ただし、<xref:System.Drawing.Graphics.DrawArc%2A> では開始角度とスイープ角度が必要です。  開始角度 30°、スイープ角度 180°の円弧を描画する例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 円弧、楕円、および外接する四角形を次の図に示します。  
  
 ![楕円と円弧](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.png "Aboutgdip02\_art06")  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [方法 : ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)   
 [方法 : 形状のアウトラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)