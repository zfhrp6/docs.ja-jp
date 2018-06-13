---
title: '方法 : ビデオを使用して領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: d2ca0f8b70abf6e895ea275d2a47eb4a6dd4bfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560778"
---
# <a name="how-to-paint-an-area-with-a-video"></a>方法 : ビデオを使用して領域を塗りつぶす
この例では、メディアを使用して領域を塗りつぶす方法を示します。 メディアを使用して領域を描画する方法の 1 つを使用して、<xref:System.Windows.Controls.MediaElement>と共に、<xref:System.Windows.Media.VisualBrush>です。 使用して、<xref:System.Windows.Controls.MediaElement>ロードし、メディアを再生し、設定を使用する、<xref:System.Windows.Media.VisualBrush.Visual%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>です。 使用してできます、<xref:System.Windows.Media.VisualBrush>読み込まれたメディアで領域を塗りつぶすにします。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.VisualBrush>を描画する、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>ビデオ コントロール。 この例では設定、<xref:System.Windows.Controls.MediaElement.IsMuted%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>に`true`サウンドが生成されないようにします。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.VisualBrush>から継承、<xref:System.Windows.Media.TileBrush>クラス、いくつかのタイル モードを提供します。 設定して、<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>に<xref:System.Windows.Media.TileMode.Tile>を設定したり、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティを描画している領域より小さい値には、並べて表示するパターンを作成することができます。  
  
 次の例は点を除いて、前の例と同じ、<xref:System.Windows.Media.VisualBrush>ビデオからパターンが生成されます。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 そのため、アプリケーションが media ファイルなどのコンテンツ ファイルを追加する方法については、次を参照してください。 [WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)です。 メディア ファイルを追加すると、リソース ファイルではなく、コンテンツ ファイルとして追加する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.VisualBrush>  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [TileBrush の概要](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [マルチメディアの概要](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
