---
title: "方法 : カーディナル スプラインを描画する | Microsoft Docs"
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
  - "カーディナル スプライン, 描画"
  - "描画, カーディナル スプライン"
  - "グラフィックス, カーディナル スプライン"
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : カーディナル スプラインを描画する
カーディナル スプラインとは、指定された一連の点を滑らかに結ぶ曲線のことです。  カーディナル スプラインを描画するには、<xref:System.Drawing.Graphics> オブジェクトを作成し、点の配列のアドレスを <xref:System.Drawing.Graphics.DrawCurve%2A> メソッドに渡します。  
  
### 鐘型のカーディナル スプラインの描画  
  
-   指定した 5 つの点を結ぶ鐘型のカーディナル スプラインを描画する例を次に示します。  この曲線と 5 つの点を次の図に示します。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### 閉じたカーディナル スプラインの描画  
  
-   閉じたカーディナル スプラインを描画するには、<xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawClosedCurve%2A> メソッドを使用します。  閉じたカーディナル スプラインの場合、曲線は配列内の最後の点と、配列内の最初の点を結びます。  指定された 6 つの点を結ぶ、閉じたカーディナル スプラインを描画する例を次に示します。  この閉じたスプラインと 6 つの点を次の図に示します。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### カーディナル スプラインの歪曲度の変更  
  
-   カーディナル スプラインの歪曲度を変更するには、<xref:System.Drawing.Graphics.DrawCurve%2A> メソッドにテンション引数を渡します。  一連の同じ点を結ぶ 3 つのカーディナル スプラインを描画する例を次に示します。  この 3 つのスプラインとそのテンション値を次の図に示します。  テンションが 0 の場合、各点は直線で結ばれます。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)