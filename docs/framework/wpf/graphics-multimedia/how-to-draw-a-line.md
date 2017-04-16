---
title: "方法 : 線を描画する | Microsoft Docs"
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
  - "描画, 線"
  - "グラフィックス [WPF], 線"
  - "線, 描画"
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 線を描画する
この例では、<xref:System.Windows.Shapes.Line> 要素を使用して線を描画する方法を示します。  
  
 線を描画するには、<xref:System.Windows.Shapes.Line> 要素を作成します。  その要素の <xref:System.Windows.Shapes.Line.X1%2A> プロパティと <xref:System.Windows.Shapes.Line.Y1%2A> プロパティを使用して線の始点を設定し、<xref:System.Windows.Shapes.Line.X2%2A> プロパティと <xref:System.Windows.Shapes.Line.Y2%2A> プロパティを使用して終点を設定します。  ストロークのない線は表示されないため、最後に <xref:System.Windows.Shapes.Shape.Stroke%2A> と <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> を設定します。  
  
 線には内部領域がないので、線の <xref:System.Windows.Shapes.Shape.Fill%2A> 要素を設定しても効果はありません。  
  
 <xref:System.Windows.Controls.Canvas> 要素の内側に 3 本の線を描画する例を次に示します。  
  
## 使用例  
 [!code-xml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Line>   
 [Shape 要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)