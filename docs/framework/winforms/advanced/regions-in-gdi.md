---
title: "GDI+ での領域 | Microsoft Docs"
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
  - "描画, 領域"
  - "GDI+, 領域"
  - "領域"
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# GDI+ での領域
領域は、出力デバイスのディスプレイ範囲の一部です。  単純な領域 \(単一の四角形\) と複雑な領域 \(複数の多角形と閉じた曲線の組み合わせ\) があります。  四角形から構築された領域とパスから構築された領域を次の図に示します。  
  
 ![領域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.png "AboutGdip02\_Art27")  
  
## 領域の使用  
 領域は、クリッピングとヒット テストに使用されることがよくあります。  クリッピングでは、ディスプレイ範囲の特定の領域 \(通常は更新が必要な部分\) だけに描画を制限します。  ヒット テストでは、マウス ボタンが押されたときにカーソルが画面上の特定の領域内にあるかどうかを判断します。  
  
 四角形またはパスから領域を構築できます。  既存の領域を組み合わせて複雑な領域を作成することもできます。  <xref:System.Drawing.Region> クラスでは、領域を組み合わせるためのメソッドとして、<xref:System.Drawing.Region.Intersect%2A>、<xref:System.Drawing.Region.Union%2A>、<xref:System.Drawing.Region.Xor%2A>、<xref:System.Drawing.Region.Exclude%2A>、および <xref:System.Drawing.Region.Complement%2A> が用意されています。  
  
 2 つの領域の積集合は、両方の領域に属しているすべての点の集合です。  和集合は、いずれか一方または両方の領域に属しているすべての点の集合です。  1 つの領域の補集合は、その領域に属していないすべての点の集合です。  上記の図にある 2 つの領域の積集合と和集合を次の図に示します。  
  
 ![領域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02\_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A> メソッドは、2 つの領域に対して適用され、いずれか一方の領域にだけ属しているすべての点を含む領域を生成します。  <xref:System.Drawing.Region.Exclude%2A> メソッドは、2 つの領域に対して適用され、1 番目の領域には属しているが 2 番目の領域には属していないすべての点を含む領域を生成します。  このトピックの最初に示した 2 つの領域に対して <xref:System.Drawing.Region.Xor%2A> メソッドと <xref:System.Drawing.Region.Exclude%2A> メソッドを適用して生成された領域を次の図に示します。  
  
 ![領域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02\_Art29")  
  
 領域を塗りつぶすには、<xref:System.Drawing.Graphics> オブジェクト、<xref:System.Drawing.Brush> オブジェクト、および <xref:System.Drawing.Region> オブジェクトが必要です。  <xref:System.Drawing.Graphics> オブジェクトには <xref:System.Drawing.Graphics.FillRegion%2A> メソッドが用意されており、<xref:System.Drawing.Brush> オブジェクトには色やパターンなど、塗りつぶしの属性が格納されます。  純色で領域を塗りつぶす例を次に示します。  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## 参照  
 <xref:System.Drawing.Region?displayProperty=fullName>   
 [直線、曲線、および図形](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [領域の使用](../../../../docs/framework/winforms/advanced/using-regions.md)