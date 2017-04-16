---
title: "GDI+ でのカーディナル スプライン | Microsoft Docs"
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
  - "カーディナル スプライン"
  - "GDI+, カーディナル スプライン"
  - "スプライン, カーディナル"
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# GDI+ でのカーディナル スプライン
カーディナル スプラインとは、大きな曲線を形成するために接合された個別の曲線の集まりのことです。  スプラインは、複数の点の配列とテンション パラメーターによって指定されます。  カーディナル スプラインは、配列内の各点を滑らかに通過します。不連続な傾きの変化や曲線のテンションの急激な変化はありません。  点のセットおよびセット内の各点を通過するカーディナル スプラインを次の図に示します。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.png "Aboutgdip02\_art09")  
  
## 物理的なスプラインと数学的なスプライン  
 物理的なスプラインは、木などの柔軟な材料で作られた薄い板です。  数学的なスプラインが実用化されるまで、デザイナーは物理的なスプラインを使用して曲線を作図していました。  デザイナーは、紙の上にスプラインを置き、指定した点のセット上でスプラインを固定します。  次に、デザイナーはスプラインに沿ってペンまたは鉛筆で曲線を作図します。  物理的なスプラインの特性に応じて、指定した点のセットからさまざまな曲線を作成できます。  たとえば、曲げに対する抵抗力が強いスプラインと非常に柔軟なスプラインでは、作成される曲線は異なります。  
  
 数学的なスプラインの数式は柔軟な棒の特性に基づいているため、数学的なスプラインで作成される曲線は、従来の物理的なスプラインで作成される曲線に類似しています。  物理的なスプラインでは、指定した点のセットからテンションに応じてさまざまな曲線が作成されます。同様に、数学的なスプラインでは、指定した点のセットからテンション パラメーターの値に応じてさまざまな曲線が作成されます。  同じ点のセットを通過する 4 つのカーディナル スプラインを次の図に示します。  各スプラインのテンションが示されています。  テンションの値 0 は無限大の物理的テンションに相当し、曲線は点の間の最短距離 \(直線\) を通過するように強制されます。  テンションの値 1 は物理的テンションがない状態に相当し、スプラインは曲げの合計が最小になるパスを通過できます。  テンションの値が 1 より大きい場合、曲線は圧縮されたばねと同様に長いパスを通過するように強制されます。  
  
 ![カーディナル スプライン](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.png "Aboutgdip02\_art10")  
  
 上記の図の 4 つのスプラインでは、開始点における接線はすべて同じです。  接線は、開始点と曲線上の次の点を結ぶ直線です。  同様に、終了点における接線は、終了点と曲線上の前の点を結ぶ直線です。  
  
 カーディナル スプラインを描画するには、<xref:System.Drawing.Graphics> クラスのインスタンス、<xref:System.Drawing.Pen>、および <xref:System.Drawing.Point> オブジェクトの配列が必要です。<xref:System.Drawing.Graphics> クラスのインスタンスはスプラインを描画する <xref:System.Drawing.Graphics.DrawCurve%2A> メソッドを提供し、<xref:System.Drawing.Pen> は線幅や色などのスプラインの属性を格納します。  <xref:System.Drawing.Point> オブジェクト配列は曲線が通過する複数の点を格納します。   `myPointArray` 内の点を通過するカーディナル スプラインを描画する方法を次のコード例に示します。  3 番目のパラメーターはテンションです。  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## 参照  
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [曲線の作成と描画](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)