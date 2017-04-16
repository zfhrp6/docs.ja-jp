---
title: "方法 : 要素をスケーリングする | Microsoft Docs"
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
  - "クラス, ScaleTransform"
  - "グラフィックス, スケーリング (要素を)"
  - "ScaleTransform クラス"
  - "スケーリング, 要素"
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 要素をスケーリングする
<xref:System.Windows.Media.ScaleTransform> を使用して要素をスケーリングする方法を次の例に示します。  
  
 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> および <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> プロパティを使用して、指定するファクターごとに要素のサイズを変更します。  たとえば、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A> の値が 1.5 である場合、要素は元の幅の 150% に引き伸ばされます。  <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> の値が 0.5 である場合、要素の高さは 50% 縮められます。  
  
 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> および <xref:System.Windows.Media.ScaleTransform.CenterY%2A> プロパティを使用して、スケール操作の中心となる点を指定します。  既定では、<xref:System.Windows.Media.ScaleTransform> は中心点 \(0,0\) に配置されます。これは四角形の左上隅に相当します。  <xref:System.Windows.Media.Transform> を適用すると、オブジェクトが存在する座標空間が変更されるため、これには要素を移動する効果、および要素を大きく表示する効果もあります。  
  
 次のコード例では、<xref:System.Windows.Media.ScaleTransform> を使用して、縦横 50 サイズの <xref:System.Windows.Shapes.Rectangle> を 2 倍にします。  <xref:System.Windows.Media.ScaleTransform> には、<xref:System.Windows.Media.ScaleTransform.CenterX%2A> と <xref:System.Windows.Media.ScaleTransform.CenterY%2A> の両方に対して値 0 \(既定値\) があります。  
  
## 使用例  
 [!code-xml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常、<xref:System.Windows.Media.ScaleTransform.CenterX%2A> および <xref:System.Windows.Media.ScaleTransform.CenterY%2A> をスケーリングされるオブジェクトの中心に設定します \(<xref:System.Windows.FrameworkElement.Width%2A>\/2、<xref:System.Windows.FrameworkElement.Height%2A>\/2\)。  
  
 サイズが 2 倍にされている別の <xref:System.Windows.Shapes.Rectangle> の例を次に示します。ただし、この <xref:System.Windows.Media.ScaleTransform> には、<xref:System.Windows.Media.ScaleTransform.CenterX%2A> と <xref:System.Windows.Media.ScaleTransform.CenterY%2A> の両方に対して、四角形の中心に対応する値 25 があります。  
  
 [!code-xml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 2 つの <xref:System.Windows.Media.ScaleTransform> の操作の違いを次の図に示します。  点線は、スケーリング前の四角形のサイズと位置を示します。  
  
 ![中心点が異なる 2 倍のスケール](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.png "wcpsdk\_graphicsmm\_scalecenter")  
ScaleX 値と ScaleY 値が同じであっても中心が異なる 2 つの ScaleTransform 操作  
  
 サンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)