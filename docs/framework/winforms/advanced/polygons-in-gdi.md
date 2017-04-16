---
title: "GDI+ での多角形 | Microsoft Docs"
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
  - "描画, 多角形"
  - "GDI+, 多角形"
  - "多角形"
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# GDI+ での多角形
多角形は、3 つ以上の辺を持つ閉じた図形です。  たとえば、三角形、四角形、五角形は、それぞれ 3 辺、4 辺、5 辺を持つ多角形です。  いくつかの多角形を次の図に示します。  
  
 ![多角形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.png "Aboutgdip02\_art07")  
  
## 多角形の描画  
 多角形を描画するには、<xref:System.Drawing.Graphics> オブジェクト、<xref:System.Drawing.Pen> オブジェクト、および <xref:System.Drawing.Point> \(または <xref:System.Drawing.PointF>\) オブジェクト配列が必要です。  <xref:System.Drawing.Graphics> オブジェクトには、<xref:System.Drawing.Graphics.DrawPolygon%2A> メソッドが用意されています。  <xref:System.Drawing.Pen> オブジェクトは多角形の描画に使用される線の幅や色などの属性を格納し、<xref:System.Drawing.Point> オブジェクト配列は直線で連結される複数の点を格納します。  <xref:System.Drawing.Pen> オブジェクトと <xref:System.Drawing.Point> オブジェクト配列は、引数として <xref:System.Drawing.Graphics.DrawPolygon%2A> メソッドに渡されます。  3 辺を持つ多角形を描画する例を次に示します。   `myPointArray` の点は、\(0, 0\)、\(50, 30\)、および \(30, 60\) の 3 点だけです。  <xref:System.Drawing.Graphics.DrawPolygon%2A> メソッドは、\(30, 60\) から開始点 \(0, 0\) に戻る直線を描画することにより、多角形を自動的に閉じます。  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 この多角形を次の図に示します。  
  
 ![多角形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.png "Aboutgdip02\_art08")  
  
## 参照  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Pen?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [方法 : ペンを作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)