---
title: '方法 : TileBrush のタイル サイズを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 16f0a4b3a5c9b9075126ba6d8f19d65169f70921
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561749"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>方法 : TileBrush のタイル サイズを設定する
この例のタイルのサイズを設定する方法を示しています、<xref:System.Windows.Media.TileBrush>です。 既定では、<xref:System.Windows.Media.TileBrush>完全に領域に描画している 1 つのタイルが生成されます。 この動作をオーバーライドするには、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティです。  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティ、タイルのサイズを指定、<xref:System.Windows.Media.TileBrush>です。 既定では、値、<xref:System.Windows.Media.TileBrush.Viewport%2A>塗りつぶされている領域のサイズに対する相対パス プロパティです。 させる、 <xref:System.Windows.Media.TileBrush.Viewport%2A> 、絶対のタイルのサイズを指定するプロパティを設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.ImageBrush>の型<xref:System.Windows.Media.TileBrush>タイルを含む四角形を描画します。 例では、各タイルを出力領域 (四角形) の 50% x 50% に設定します。 その結果、四角形は、イメージの 4 つの投影で塗りつぶされます。  
  
 次の図は、この例で生成される出力を示しています。
  
 ![イメージ ブラシを並べて表示する例](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 次の例では、作成、 <xref:System.Windows.Media.ImageBrush>、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>に`0,0,25,25`とその<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>に<xref:System.Windows.Media.BrushMappingMode.Absolute>、し、別の四角形の描画に使用します。 その結果、ブラシは、幅が 25 ピクセル、高さが 25 ピクセルのタイルを生成します。  
  
 次の図は、この例で生成される出力を示しています。  
  
 ![0,0,0.25,0.25 の Viewport を使用したタイル表示の TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 上記の例は、大規模なサンプルの一部です。 サンプル全体については、次を参照してください。 [ImageBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160005)です。  
  
 この例を使用しますが、<xref:System.Windows.Media.ImageBrush>クラス、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティが、他の動作は同じです<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>です。 詳細については<xref:System.Windows.Media.ImageBrush>と、その他の<xref:System.Windows.Media.TileBrush>、オブジェクトを参照してください[イメージ、図形、およびビジュアルの描画](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.TileBrush>  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush を使用してさまざまなタイル パターンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)
