---
title: "方法 : ビデオを使用して領域を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, 塗りつぶし (ビデオによる)"
  - "塗りつぶし (ビデオによる)"
  - "ビデオ, 塗りつぶし"
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : ビデオを使用して領域を塗りつぶす
この例では、メディアを使用して領域を塗りつぶす方法を示します。  メディアを使用して領域を塗りつぶす 1 つの方法は、<xref:System.Windows.Controls.MediaElement> と共に <xref:System.Windows.Media.VisualBrush> を使用することです。  <xref:System.Windows.Controls.MediaElement> を使用してメディアを読み込んで再生した後、そのメディアを使用して <xref:System.Windows.Media.VisualBrush> の <xref:System.Windows.Media.VisualBrush.Visual%2A> プロパティを設定します。  その後は、<xref:System.Windows.Media.VisualBrush> を使用して、読み込んだメディアを使用して領域を塗りつぶすことができます。  
  
## 使用例  
 <xref:System.Windows.Controls.MediaElement> と <xref:System.Windows.Media.VisualBrush> を使用して、<xref:System.Windows.Controls.TextBlock> コントロールの <xref:System.Windows.Controls.TextBlock.Foreground%2A> をビデオで塗りつぶす例を次に示します。  この例では、音が出ないように、<xref:System.Windows.Controls.MediaElement> の <xref:System.Windows.Controls.MediaElement.IsMuted%2A> プロパティを `true` に設定しています。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## 使用例  
 <xref:System.Windows.Media.VisualBrush> は <xref:System.Windows.Media.TileBrush> クラスを継承するため、並べて表示するモードをいくつか備えています。  <xref:System.Windows.Media.VisualBrush> の <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティを <xref:System.Windows.Media.TileMode> に設定し、その <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティを塗りつぶす領域より小さい値に設定することで、並べて表示するパターンを作成できます。  
  
 次の例は前の例と同じものですが、<xref:System.Windows.Media.VisualBrush> がビデオからパターンを生成するところが異なっています。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 メディア ファイルなどのコンテンツ ファイルをアプリケーションに追加する方法については、「[WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。  メディア ファイルを追加するときは、リソース ファイルとしてではなく、コンテンツ ファイルとして追加する必要があります。  
  
## 参照  
 <xref:System.Windows.Media.VisualBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [TileBrush の概要](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)   
 [マルチメディアの概要](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)