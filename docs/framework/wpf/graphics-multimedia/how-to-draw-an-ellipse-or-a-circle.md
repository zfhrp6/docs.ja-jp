---
title: "方法 : 楕円または円を描画する | Microsoft Docs"
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
  - "円, 描画"
  - "描画 (円を)"
  - "描画 (楕円を)"
  - "楕円, 描画"
  - "グラフィックス, 描画 (円を)"
  - "グラフィックス, 描画 (楕円を)"
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 楕円または円を描画する
この例では、<xref:System.Windows.Shapes.Ellipse> 要素を使用して楕円および円を描画する方法を示します。  楕円を描画するには、<xref:System.Windows.Shapes.Ellipse> 要素を作成して <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> を指定します。  楕円の内部を塗りつぶすために使用する <xref:System.Windows.Media.Brush> を指定するには、<xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを使用します。  楕円のアウトラインを塗りつぶすために使用する <xref:System.Windows.Media.Brush> を指定するには、<xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティを使用します。  <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> プロパティは、楕円のアウトラインの太さを指定します。  
  
 円を描画するには、<xref:System.Windows.Shapes.Ellipse> 要素の <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> を同じ値にします。  
  
 次の例では、<xref:System.Windows.Controls.Canvas> 内に 4 つの <xref:System.Windows.Shapes.Ellipse> 要素を描画します。  
  
## 使用例  
 [!code-xml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 この例では <xref:System.Windows.Controls.Canvas> を使用して楕円を組み込みますが、テキスト以外のコンテンツをサポートする任意の <xref:System.Windows.Controls.Panel> や <xref:System.Windows.Controls.Control> でも、楕円要素 \(および他のすべての図形要素\) を使用できます。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Ellipse>   
 <xref:System.Windows.Shapes.Shape>   
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)