---
title: "方法 : 背景として使用するイメージの縦横比を保持する | Microsoft Docs"
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
  - "縦横比 (背景イメージの), 保持"
  - "背景イメージ, 保持 (縦横比を)"
  - "ブラシ, 保持 (背景イメージの縦横比を)"
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 背景として使用するイメージの縦横比を保持する
この例では、イメージの[縦横比](GTMT)を保持するために <xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを使用する方法について説明します。  
  
 既定では、<xref:System.Windows.Media.ImageBrush> を使用して領域を塗りつぶすと、出力領域が完全に塗りつぶされるようにコンテンツが引き伸ばされます。  出力領域とイメージの[縦横比](GTMT)が異なる場合は、この引き伸ばしによってイメージがゆがめられます。  
  
 <xref:System.Windows.Media.ImageBrush> がそのイメージの縦横比を保持するようにするには、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティを <xref:System.Windows.Media.Stretch> または <xref:System.Windows.Media.Stretch> に設定します。  
  
## 使用例  
 次の例では、2 つの <xref:System.Windows.Media.ImageBrush> オブジェクトを使用して、2 つの四角形を塗りつぶしています。  これらの四角形は 300 × 150 [ピクセル](GTMT)で、どちらも 300 × 300 ピクセルのイメージを保持しています。  最初のブラシの <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは <xref:System.Windows.Media.Stretch> に設定され、2 番目のブラシの <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは <xref:System.Windows.Media.Stretch> に設定されています。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 <xref:System.Windows.Media.TileBrush.Stretch%2A> を <xref:System.Windows.Media.Stretch> に設定した最初のブラシの出力を次の図に示します。  
  
 ![Uniform 拡大を使用した ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.png "graphicsmm\_ImageBrushUniformStretch")  
  
 <xref:System.Windows.Media.TileBrush.Stretch%2A> を <xref:System.Windows.Media.Stretch> に設定した 2 番目のブラシの出力を次の図に示します。  
  
 ![UniformToFill 拡大を使用した ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.png "graphicsmm\_ImageBrushUniformToFillStretch")  
  
 <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは、他の <xref:System.Windows.Media.TileBrush> オブジェクト、つまり <xref:System.Windows.Media.DrawingBrush> と <xref:System.Windows.Media.VisualBrush> に対してもまったく同じように動作することに注意してください。  <xref:System.Windows.Media.ImageBrush> およびその他の <xref:System.Windows.Media.TileBrush> オブジェクトの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
 また、<xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティは、<xref:System.Windows.Media.TileBrush> コンテンツを出力領域に合わせて引き伸ばす方法を指定するように見えますが、実際には基本タイルを塗りつぶすように <xref:System.Windows.Media.TileBrush> コンテンツを引き伸ばす方法を指定することにも注意してください。  詳細については、<xref:System.Windows.Media.TileBrush> を参照してください。  
  
 このコード例は、<xref:System.Windows.Media.ImageBrush> クラスのトピックで示されているコード例の一部分です。  サンプル全体については、[ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.TileBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)