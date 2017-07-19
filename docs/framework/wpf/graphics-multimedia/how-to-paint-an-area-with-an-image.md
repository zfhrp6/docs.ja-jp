---
title: "方法 : イメージで領域を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, イメージによる塗りつぶし"
  - "イメージ, 塗りつぶし"
  - "描画, イメージを使用"
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : イメージで領域を塗りつぶす
この例では、<xref:System.Windows.Media.ImageBrush> クラスを使用してイメージで領域を塗りつぶす方法を示します。  <xref:System.Windows.Media.ImageBrush> を使用した場合、その <xref:System.Windows.Media.ImageBrush.ImageSource%2A> プロパティで指定した単一のイメージが表示されます。  
  
## 使用例  
 <xref:System.Windows.Media.ImageBrush> を使用して、ボタンの <xref:System.Windows.Controls.Control.Background%2A> を塗りつぶす例を次に示します。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 既定では、<xref:System.Windows.Media.ImageBrush> はイメージを引き伸ばして、描画する領域を完全に塗りつぶします。  前の例のようにイメージを引き伸ばしてボタンを塗りつぶすと、イメージにゆがみが生じることがあります。  この動作を制御するには、<xref:System.Windows.Media.TileBrush> の <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを <xref:System.Windows.Media.Stretch> または <xref:System.Windows.Media.Stretch> に設定します。これにより、ブラシはイメージの[縦横比](GTMT)を維持します。  
  
 <xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.TileBrush.Viewport%2A> および <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティを設定すると、繰り返しのパターンを作成できます。  イメージから作成したパターンを使用して、ボタンを塗りつぶす方法を次の例に示します。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 <xref:System.Windows.Media.ImageBrush> クラスの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
 このコード例は、<xref:System.Windows.Media.ImageBrush> クラスのトピックで示されているコード例の一部分です。  サンプル全体については、[ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。  
  
## 参照  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)