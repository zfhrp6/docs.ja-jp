---
title: "方法 : TileBrush の水平方向および垂直方向の配置を設定する | Microsoft Docs"
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
  - "エイリアスの使用, TileBrush"
  - "水平方向の配置 (TileBrush の)"
  - "TileBrush, 配置"
  - "垂直方向の配置 (TileBrush の)"
ms.assetid: 65ae89bd-9246-4c9e-bde4-2fb991d4060d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : TileBrush の水平方向および垂直方向の配置を設定する
この例では、タイル内にあるコンテンツの水平方向の配置と垂直方向の配置を制御する方法を示します。  <xref:System.Windows.Media.TileBrush> の水平方向および垂直方向の配置を制御するには、その <xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティと <xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティを使用します。  
  
 次のいずれかの条件に当てはまる場合は、<xref:System.Windows.Media.TileBrush> の <xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティと <xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティが使用されます。  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティが <xref:System.Windows.Media.Stretch> または <xref:System.Windows.Media.Stretch> で、<xref:System.Windows.Media.TileBrush.Viewbox%2A> および <xref:System.Windows.Media.TileBrush.Viewport%2A> の[縦横比](GTMT)が異なる場合。  
  
-   <xref:System.Windows.Media.TileBrush.Stretch%2A> プロパティが <xref:System.Windows.Media.Stretch> で、<xref:System.Windows.Media.TileBrush.Viewbox%2A> および <xref:System.Windows.Media.TileBrush.Viewport%2A> のサイズが異なる場合。  
  
## 使用例  
 <xref:System.Windows.Media.TileBrush> の一種である <xref:System.Windows.Media.DrawingBrush> のコンテンツをタイルの左上隅に配置する例を次に示します。  コンテンツの配置のため、この例では、<xref:System.Windows.Media.DrawingBrush> の <xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティを <xref:System.Windows.Media.AlignmentX>、<xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティを <xref:System.Windows.Media.AlignmentY> に設定しています。  この例を実行すると、次の出力が生成されます。  
  
 ![左上に配置された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletopleft.png "graphicsmm\_TileBrushAlignmentExampleTopLeft")  
コンテンツを左上隅に配置した TileBrush  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmentinline)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティを <xref:System.Windows.Media.AlignmentX>、<xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティを <xref:System.Windows.Media.AlignmentY> に設定して、<xref:System.Windows.Media.DrawingBrush> のコンテンツをタイルの右下隅に配置します。  この例の出力は、次のようになります。  
  
 ![右下に配置された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomright.png "graphicsmm\_TileBrushAlignmentExampleBottomRight")  
コンテンツを右下隅に配置した TileBrush  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティを <xref:System.Windows.Media.AlignmentX>、<xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティを <xref:System.Windows.Media.AlignmentY> に設定して、<xref:System.Windows.Media.DrawingBrush> のコンテンツをタイルの左上隅に配置します。  さらに、<xref:System.Windows.Media.DrawingBrush> の <xref:System.Windows.Media.TileBrush.Viewport%2A> および <xref:System.Windows.Media.TileBrush.TileMode%2A> を設定して、タイル パターンを生成します。  この例の出力は、次のようになります。  
  
 ![左上に並べて配置された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexampletoplefttiled.png "graphicsmm\_TileBrushAlignmentExampleTopLeftTiled")  
基本タイルの左上部分にコンテンツを配置したタイル パターン  
  
 この図では、コンテンツがどのように配置されるかを確認できるように、基本タイルを強調表示しています。  <xref:System.Windows.Media.DrawingBrush> のコンテンツが基本タイルの水平方向を完全に埋めているため、<xref:System.Windows.Media.TileBrush.AlignmentX%2A> の設定は影響を及ぼさないことに注意してください。  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushtopleftalignmenttiledinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushtopleftalignmenttiledinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushTopLeftAlignmentTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushtopleftalignmenttiledinline)]  
  
## 使用例  
 最後の例では、<xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティを <xref:System.Windows.Media.AlignmentX>、<xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティを <xref:System.Windows.Media.AlignmentY> に設定して、並べて表示された <xref:System.Windows.Media.DrawingBrush> のコンテンツを基本タイルの右下に配置します。  この例の出力は、次のようになります。  
  
 ![右下に並べて配置された TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-tilebrushalignmentexamplebottomrighttiled.png "graphicsmm\_TileBrushAlignmentExampleBottomRightTiled")  
基本タイルの右下部分にコンテンツを配置したタイル パターン  
  
 ここでも、<xref:System.Windows.Media.DrawingBrush> のコンテンツが基本タイルの水平方向を完全に埋めているため、<xref:System.Windows.Media.TileBrush.AlignmentX%2A> の設定は影響を及ぼしません。  
  
 [!code-csharp[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/TileBrushAlignmentExample.cs#tilebrushbottomrightalignmentinline)]
 [!code-vb[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushOverviewExamples_snip/visualbasic/tilebrushalignmentexample.vb#tilebrushbottomrightalignmentinline)]
 [!code-xml[brushoverviewexamples_snip#TileBrushBottomRightAlignmentInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/TileBrushAlignmentExample.xaml#tilebrushbottomrightalignmentinline)]  
  
 ここでは、<xref:System.Windows.Media.DrawingBrush> オブジェクトを例に取って <xref:System.Windows.Media.TileBrush.AlignmentX%2A> プロパティと <xref:System.Windows.Media.TileBrush.AlignmentY%2A> プロパティの使用方法を示しています。  これらのプロパティは、<xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.VisualBrush> のすべてのタイル ブラシでまったく同じように動作します。  タイル ブラシの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.DrawingBrush>   
 <xref:System.Windows.Media.ImageBrush>   
 <xref:System.Windows.Media.VisualBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)