---
title: "方法 : オブジェクトを回転させる | Microsoft Docs"
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
  - "グラフィックス, 回転 (オブジェクトを)"
  - "回転 (オブジェクトを)"
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : オブジェクトを回転させる
この例では、オブジェクトを回転させる方法を示します。  この例では、最初に <xref:System.Windows.Media.RotateTransform> を作成した後、その <xref:System.Windows.Media.RotateTransform.Angle%2A> を度で指定します。  
  
 次の例では、<xref:System.Windows.Shapes.Polyline> オブジェクトを、左上隅を中心に 45°回転します。  
  
## 使用例  
 [!code-xml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform> の <xref:System.Windows.Media.RotateTransform.CenterX%2A> プロパティと <xref:System.Windows.Media.RotateTransform.CenterY%2A> プロパティは、オブジェクトを回転させる中心点を指定します。  この中心点は、変換する要素の座標空間で表します。  既定では、回転は \(0,0\) に適用されます。これは変換対象のオブジェクトの左上隅です。  
  
 次の例では、<xref:System.Windows.Shapes.Polyline> オブジェクトを、点 \(25,50\) を中心にして時計回りに 45°回転します。  
  
 [!code-xml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 次の図は、2 つのオブジェクトに <xref:System.Windows.Media.Transform> を適用した結果を示しています。  
  
 ![中心点が異なる 45 度の回転](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.png "wcpsdk\_graphicsmm\_rotatetransform45degrees")  
異なる中心点を軸に 45°回転させた 2 つのオブジェクト  
  
 前の例での <xref:System.Windows.Shapes.Polyline> は <xref:System.Windows.UIElement> です。  <xref:System.Windows.UIElement> の <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに <xref:System.Windows.Media.Transform> を適用するときは、<xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティを使用して、その要素に適用するすべての <xref:System.Windows.Media.Transform> の原点を指定できます。  <xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティは相対座標を使用するので、要素のサイズがわからなくても、要素の中心に変換を適用できます。  詳細および例については、「[変換の原点を相対値で指定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)」を参照してください。  
  
 サンプル全体については、[2\-D 変換のサンプル](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)