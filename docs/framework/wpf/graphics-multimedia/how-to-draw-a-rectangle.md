---
title: "方法 : 四角形を描画する | Microsoft Docs"
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
  - "描画, 四角形"
  - "グラフィックス [WPF], 四角形"
  - "四角形, 描画"
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 四角形を描画する
この例では、<xref:System.Windows.Shapes.Rectangle> 要素を使用して四角形を描画する方法を示します。  
  
 四角形を描画するには、<xref:System.Windows.Shapes.Rectangle> 要素を作成し、<xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.Height%2A> を指定します。  四角形の内側を塗りつぶすには、<xref:System.Windows.Shapes.Shape.Fill%2A> を設定します。  四角形のアウトラインを描画するには、<xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティと <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> プロパティを使用します。  
  
 四角形の角を丸くするには、オプションの <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> プロパティと <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> プロパティを指定します。  <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> プロパティと <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> プロパティは、四角形の角に丸みを付けるために使用される楕円の x 軸半径と y 軸半径を設定します。  
  
 次の例では、2 つの <xref:System.Windows.Shapes.Rectangle> 要素が <xref:System.Windows.Controls.Canvas> 内に描画されます。  最初の四角形は、内側が <xref:System.Windows.Media.Brushes.Blue%2A> です。  2 番目の四角形は、内側が <xref:System.Windows.Media.Brushes.Blue%2A>、アウトラインが <xref:System.Windows.Media.Brushes.Black%2A> で角が丸くなります。  
  
## 使用例  
 [!code-xml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 この例では <xref:System.Windows.Controls.Canvas> を使用して四角形を組み込みますが、テキスト以外のコンテンツをサポートする任意の <xref:System.Windows.Controls.Panel> や <xref:System.Windows.Controls.Control> でも、四角形要素 \(および他のすべての図形要素\) を使用できます。  実際、四角形は、<xref:System.Windows.Controls.Grid> パネルの一部へ背景を提供するのに特に役立ちます。  例については、「[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)」を参照してください。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Rectangle>   
 [図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)