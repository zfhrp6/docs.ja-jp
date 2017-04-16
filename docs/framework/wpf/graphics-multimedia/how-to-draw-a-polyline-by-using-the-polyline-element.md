---
title: "方法 : ポリライン要素を使用してポリラインを描画する | Microsoft Docs"
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
  - "連結した線"
  - "描画, ポリライン"
  - "グラフィックス [WPF], ポリライン"
  - "線, 接続 ("ポリライン" を参照)"
  - "ポリライン, 描画"
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ポリライン要素を使用してポリラインを描画する
この例では、<xref:System.Windows.Shapes.Polyline> 要素を使用して、接続された一連の線であるポリラインを描画する方法を示します。  
  
 ポリラインを描画するには、<xref:System.Windows.Shapes.Polyline> 要素を作成し、その <xref:System.Windows.Shapes.Polyline.Points%2A> プロパティを使用して図形の頂点を指定します。  最後に、<xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティと <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> プロパティを使用して、ポリライン アウトラインを描きます。ストロークのない線は表示されません。  
  
> [!NOTE]
>  <xref:System.Windows.Shapes.Polyline> 要素は閉じた図形でないため、意図的に図形のアウトラインを閉じた場合でも、<xref:System.Windows.Shapes.Shape.Fill%2A> プロパティは無効です。  閉じた図形を <xref:System.Windows.Shapes.Shape.Fill%2A> で作成するには、<xref:System.Windows.Shapes.Polygon> 要素を使用します。  
  
 <xref:System.Windows.Controls.Canvas> 内に、2 つの <xref:System.Windows.Shapes.Polyline> 要素を描画する例を次に示します。  
  
## 使用例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、頂点を表す有効な構文は、コンマ区切りの x 座標と y 座標のペアをスペースで区切ったリストです。  
  
 [!code-xml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 この例では <xref:System.Windows.Controls.Canvas> を使用してポリラインを組み込みますが、テキスト以外のコンテンツをサポートする任意の <xref:System.Windows.Controls.Panel> や <xref:System.Windows.Controls.Control> でも、ポリライン要素 \(および他のすべての図形要素\) を使用できます。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Shapes.Polygon>   
 <xref:System.Windows.Shapes.Shape>   
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)