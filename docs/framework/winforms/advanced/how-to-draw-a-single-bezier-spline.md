---
title: "方法 : 1 本のベジエ スプラインを描画する | Microsoft Docs"
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
  - "ベジエ スプライン, 描画"
  - "描画, ベジエ スプライン"
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : 1 本のベジエ スプラインを描画する
ベジエ スプラインは、開始点、2 つの制御点、および終了点の 4 つの点によって定義されます。  
  
## 使用例  
 開始点が \(10, 100\) で終了点が \(200, 100\) のベジエ スプラインを描画する例を次に示します。  制御点は \(100, 10\) および \(150, 150\) です。  
  
 生成されたベジエ スプラインとその開始点、制御点、および終了点を、次の図に示します。  また、この図では、スプラインの外側の枠である、4 つの点を直線で結んで形成される多角形も示しています。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Graphics.DrawBezier%2A>   
 [GDI\+ でのベジエ スプライン](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [方法 : 一連のベジエ スプラインを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)