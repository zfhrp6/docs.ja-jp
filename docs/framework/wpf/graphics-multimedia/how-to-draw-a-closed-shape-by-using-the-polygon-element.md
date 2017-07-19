---
title: "方法 : 多角形要素を使用して、閉じた図形を描画する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "閉じた図形, 描画 (Polygon 要素で)"
  - "描画, 閉じた図形 (Polygon 要素で)"
  - "グラフィックス, Polygon 要素"
  - "Polygon 要素"
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 多角形要素を使用して、閉じた図形を描画する
この例では、<xref:System.Windows.Shapes.Polygon> 要素を使用して閉じた図形を描画する方法を示します。  閉じた図形を描画するには、<xref:System.Windows.Shapes.Polygon> 要素を作成し、その <xref:System.Windows.Shapes.Polygon.Points%2A> プロパティを使用して図形の各頂点を指定します。  最初と最後の点を結ぶ線が自動的に描画されます。  最後に、<xref:System.Windows.Shapes.Shape.Fill%2A>、<xref:System.Windows.Shapes.Shape.Stroke%2A>、またはその両方を指定します。  
  
## 使用例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、頂点を表す有効な構文は、コンマ区切りの x 座標と y 座標のペアをスペースで区切ったリストです。  
  
 [!code-xml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 この例では <xref:System.Windows.Controls.Canvas> を使用して多角形を組み込みますが、テキスト以外のコンテンツをサポートする任意の <xref:System.Windows.Controls.Panel> や <xref:System.Windows.Controls.Control> でも、多角形要素 \(および他のすべての図形要素\) を使用できます。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。