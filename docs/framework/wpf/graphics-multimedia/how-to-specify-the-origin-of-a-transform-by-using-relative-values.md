---
title: "方法 : 変換の原点を相対値で指定する | Microsoft Docs"
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
  - "グラフィックス, 原点 (変換の)"
  - "原点 (変換の)"
  - "変換, 原点"
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 変換の原点を相対値で指定する
この例では、相対値を使用して、<xref:System.Windows.FrameworkElement> に適用する <xref:System.Windows.UIElement.RenderTransform%2A> の原点を指定する方法を示します。  
  
 <xref:System.Windows.UIElement.RenderTransform%2A> プロパティを使用して <xref:System.Windows.FrameworkElement> を回転、拡大縮小、または[傾斜](GTMT)させる場合、既定の設定では、要素の左上隅に変換が適用されます。  要素の中心を基準にして回転、拡大縮小、または傾斜させる場合は、変換の中心を要素の中心に設定することで補正できます。  ただし、この方法を使用するには、要素のサイズがわかっている必要があります。  さらに簡単に変換を要素の中心に適用するには、変換自体で中心の値を設定する代わりに、要素の <xref:System.Windows.UIElement.RenderTransformOrigin%2A> プロパティを \(0.5, 0.5\) に設定します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.RotateTransform> を使用して、<xref:System.Windows.Controls.Button> を時計回りに 45°回転します。  この例では中心を指定しないため、ボタンはその左上隅の点 \(0, 0\) を中心として回転します。  <xref:System.Windows.Media.RotateTransform> は、<xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用されます。  
  
 この例の変換結果を次の図に示します。  
  
 ![RenderTransform を使用して変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm\_RenderTransformWithDefaultCenter")  
RenderTransform プロパティを使用して時計回りに 45°回転  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 次の例でも <xref:System.Windows.Media.RotateTransform> を使用して <xref:System.Windows.Controls.Button> を時計回りに 45°回転していますが、この例ではボタンの <xref:System.Windows.UIElement.RenderTransformOrigin%2A> を \(0.5, 0.5\) に設定しています。  その結果、回転はボタンの左上隅ではなく中心に適用されます。  
  
 この例の変換結果を次の図に示します。  
  
 ![中心の周りで変換されたボタン](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm\_RenderTransformRelativeCenter")  
RenderTransformOrigin を \(0.5, 0.5\) に設定した RenderTransform プロパティを使用して時計回りに 45°回転  
  
 [!code-xml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <xref:System.Windows.FrameworkElement> オブジェクトの変換の詳細については、「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Transform>   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)