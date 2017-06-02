---
title: "方法 : 要素を傾斜させる | Microsoft Docs"
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
  - "クラス, SkewTransform"
  - "グラフィックス, 傾斜 (要素を)"
  - "傾斜 (要素を)"
  - "SkewTransform クラス"
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 要素を傾斜させる
この例では、<xref:System.Windows.Media.SkewTransform> を使用して要素を傾斜させる方法を示します。  [傾斜](GTMT)とは、座標空間を不均等に伸縮させた変形のことで、シアとも呼ばれます。  <xref:System.Windows.Media.SkewTransform> の代表的な用途の 1 つとして、[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] オブジェクトでの [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 深度のシミュレートが挙げられます。  
  
 <xref:System.Windows.Media.SkewTransform.CenterX%2A> プロパティおよび <xref:System.Windows.Media.SkewTransform.CenterY%2A> プロパティを使用して、<xref:System.Windows.Media.SkewTransform> の中心点を指定します。  
  
 <xref:System.Windows.Media.SkewTransform.AngleX%2A> プロパティおよび <xref:System.Windows.Media.SkewTransform.AngleY%2A> プロパティを使用して x 軸と y 軸の傾斜角度を指定し、これらの軸に沿って現在の座標系を傾斜させます。  
  
 傾斜変形の結果を予測するには、<xref:System.Windows.Media.SkewTransform.AngleX%2A> によって、x 軸の値が元の座標系に対して相対的に傾斜すると考えます。  つまり、<xref:System.Windows.Media.SkewTransform.AngleX%2A> が 30 の場合、y 軸が原点を中心に 30°回転し、x の値がその原点から 30°傾斜します。  同様に、<xref:System.Windows.Media.SkewTransform.AngleY%2A> を 30 にすると、図形の y 値が原点から 30°傾斜します。  座標系を x 方向または y 方向に 30°変換 \(移動\) した場合とは効果が異なる点に注意してください。  
  
 <xref:System.Windows.Shapes.Rectangle> に対して \(0,0\) を中心点とした水平方向 45°の傾斜を適用する例を次に示します。  
  
## 使用例  
 [!code-xml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 <xref:System.Windows.Shapes.Rectangle> に対し、\(25,25\) を中心点として水平方向 45°の傾斜を適用する例を次に示します。  
  
 [!code-xml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 <xref:System.Windows.Shapes.Rectangle> に対し、\(25,25\) を中心点として垂直方向 45°の傾斜を適用する例を次に示します。  
  
 [!code-xml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 この例で使用されている各種の傾斜を次の図に示します。  
  
 ![SkewTransform の例](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.png "img\_wcpsdk\_graphicsmm\_skewtransformexample")  
3 種類の SkewTransform の例を示した図  
  
 サンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.SkewTransform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)