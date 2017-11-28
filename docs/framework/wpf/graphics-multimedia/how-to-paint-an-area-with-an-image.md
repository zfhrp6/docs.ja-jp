---
title: "方法 : イメージで領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3edbe30347580bb4f9677d7fb98d3b4fd8b92cff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-an-image"></a>方法 : イメージで領域を塗りつぶす
この例を使用する方法を示しています、<xref:System.Windows.Media.ImageBrush>イメージで領域を塗りつぶすクラス。 <xref:System.Windows.Media.ImageBrush>で指定された 1 つのイメージが表示されます、<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティです。  
  
## <a name="example"></a>例  
 次の例の描画、<xref:System.Windows.Controls.Control.Background%2A>のボタンを使用して、<xref:System.Windows.Media.ImageBrush>です。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 既定では、<xref:System.Windows.Media.ImageBrush>を完全に描画している領域を埋めるには、そのイメージを拡大します。 前の例のようにイメージを引き伸ばしてボタンを塗りつぶすと、イメージにゆがみが生じることがあります。 設定してこの動作を制御することができます、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティ<xref:System.Windows.Media.TileBrush>に<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>、それが原因で、イメージの縦横比を維持するブラシ。  
  
 設定した場合、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、 <xref:System.Windows.Media.ImageBrush>、繰り返しパターンを作成することができます。 次の例は、イメージから作成したパターンを使用してボタンを塗りつぶします。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 詳細については、<xref:System.Windows.Media.ImageBrush>クラスを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
 このコード例は提供されている長い例の一部である、<xref:System.Windows.Media.ImageBrush>クラスです。 サンプル全体については、次を参照してください。 [ImageBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160005)です。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
