---
title: "方法 : 直線または線分の終点のキャップを変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グラフィックス, 形状キャップ"
  - "Shape 要素, キャップ"
  - "Shape 要素, 終点"
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 直線または線分の終点のキャップを変更する
この例では、開いた <xref:System.Windows.Shapes.Shape> 要素の始点または終点の形状を変更する方法を示します。  開いた <xref:System.Windows.Shapes.Shape> の始点のキャップを変更するには、<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A> プロパティを使用します。  開いた <xref:System.Windows.Shapes.Shape> の終点のキャップを変更するには、<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A> プロパティを使用します。  使用できる線キャップを確認するには、<xref:System.Windows.Media.PenLineCap> 列挙体を参照してください。  
  
> [!NOTE]
>  このプロパティは、<xref:System.Windows.Shapes.Line>、<xref:System.Windows.Shapes.Polyline>、または開いた <xref:System.Windows.Shapes.Path> 要素などの開いた図形に対してのみ適用されます。  
  
 次の例では、4 つの <xref:System.Windows.Shapes.Polyline> 要素を描画し、それぞれの端に異なる形状のセットを使用します。  
  
## 使用例  
 [!code-xml[drawingwithshapeelements#ShapeLineCaps1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[図形要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Polyline>   
 <xref:System.Windows.Media.PenLineCap>