---
title: '方法 : TileBrush を使用してさまざまなタイル パターンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TileBrush [WPF], creating tile patterns
- tile patterns [WPF], creating
- creating [WPF], tile patterns with TileBrush
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
ms.openlocfilehash: 01004c66a8bd820f05e6e1f6c77a9fe7d30bca46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-different-tile-patterns-with-a-tilebrush"></a>方法 : TileBrush を使用してさまざまなタイル パターンを作成する
この例を使用する方法を示しています、<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、<xref:System.Windows.Media.TileBrush>パターンを作成します。  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティを使用すると、指定方法のコンテンツ、<xref:System.Windows.Media.TileBrush>が繰り返されますが、出力領域に並べて表示します。 設定するパターンを作成する、<xref:System.Windows.Media.TileBrush.TileMode%2A>に<xref:System.Windows.Media.TileMode.Tile>、 <xref:System.Windows.Media.TileMode.FlipX>、 <xref:System.Windows.Media.TileMode.FlipY>、または<xref:System.Windows.Media.TileMode.FlipXY>です。 設定する必要があります、<xref:System.Windows.Media.TileBrush.Viewport%2A>の<xref:System.Windows.Media.TileBrush>; 描画している領域よりも小さくなるよう以外の場合、1 つのタイルのみに関係なく、生成されたを<xref:System.Windows.Media.TileBrush.TileMode%2A>設定を使用しています。  
  
## <a name="example"></a>例  
 次の例では、5 つが作成されます<xref:System.Windows.Media.DrawingBrush>オブジェクトでは、異なる<xref:System.Windows.Media.TileBrush.TileMode%2A>を設定して、それらを 5 つの四角形の描画に使用します。 この例を使用しますが、<xref:System.Windows.Media.DrawingBrush>を示すためにクラス<xref:System.Windows.Media.TileBrush.TileMode%2A>の動作、<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティのすべての動作は同じです、<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.VisualBrush>と<xref:System.Windows.Media.DrawingBrush>です。  
  
 次の図は、この例で生成される出力を示しています。  
  
 ![出力例を並べて表示された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm_DrawingBrushTileModeExample")  
TileMode プロパティを使用して作成されたタイル パターン  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## <a name="see-also"></a>関連項目  
 [TileBrush のタイル サイズを設定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
