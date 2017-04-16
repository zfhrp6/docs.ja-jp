---
title: "方法 : 一連のベジエ スプラインを描画する | Microsoft Docs"
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
  - "ベジエ スプライン, 描画シーケンス"
  - "スプライン, 描画 (ベジエ)"
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 一連のベジエ スプラインを描画する
<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawBeziers%2A> メソッドを使用すると、連結された一連のベジエ スプラインを描画できます。  
  
## 使用例  
 2 つのベジエ スプラインを結んだ 1 つの曲線を描画する例を次に示します。  1 番目のベジエ スプラインの終了点は 2 番目のベジエ スプラインの開始点です。  
  
 結合されたスプラインとその 7 つの点を次の図に示します。  
  
 ![ベジエ スプライン](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [GDI\+ でのベジエ スプライン](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)   
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)