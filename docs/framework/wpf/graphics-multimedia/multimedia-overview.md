---
title: "マルチメディアの概要 | Microsoft Docs"
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
  - "メディア"
  - "マルチメディア"
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用すると、オーディオおよびビデオをアプリケーションに統合し、ユーザー エクスペリエンスを向上させることができます。ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="mediaapi"></a>   
## メディア API  
 <xref:System.Windows.Controls.MediaElement> クラスと <xref:System.Windows.Media.MediaPlayer> クラスは、オーディオ コンテンツまたはビデオ コンテンツの表示に使用されます。  これらのクラスは対話型またはクロックでの制御に対応しています。  これらのクラスは、[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 コントロールでメディアを再生するために使用できます。シナリオに応じてクラスを使い分けてください。  
  
 <xref:System.Windows.Controls.MediaElement> は、[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)によってサポートされる <xref:System.Windows.UIElement> で、多数のコントロールのコンテンツとして使用できます。  また、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] およびコードで使用できます。一方、<xref:System.Windows.Media.MediaPlayer> は、<xref:System.Windows.Media.Drawing> オブジェクト向けに設計されており、レイアウト サポートはありません。  <xref:System.Windows.Media.MediaPlayer> を使用して読み込まれたメディアは、<xref:System.Windows.Media.VideoDrawing> を使用するか、<xref:System.Windows.Media.DrawingContext> と直接対話することによってのみ再生できます。  <xref:System.Windows.Media.MediaPlayer> は、XAML では使用できません。  
  
 描画オブジェクトおよび描画コンテキストの詳細については、「[Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
>  アプリケーションでメディアを配布する場合、メディア ファイルをプロジェクト リソースとして使用することはできません。  代わりにプロジェクト ファイルでメディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>   
## メディアの再生モード  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement> および <xref:System.Windows.Media.MediaPlayer> には、同様のメンバーが含まれています。  このセクション内のリンクは、<xref:System.Windows.Controls.MediaElement> クラス メンバーを参照しています。  特に記載のない限り、<xref:System.Windows.Controls.MediaElement> クラス内にリンクされているメンバーは、<xref:System.Windows.Media.MediaPlayer> クラス内にもあります。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生可能な異なるモードについて理解している必要があります。  <xref:System.Windows.Controls.MediaElement> および <xref:System.Windows.Media.MediaPlayer> は、独立モードとクロック モードの 2 つのメディア モードで使用できます。  メディア モードは、<xref:System.Windows.Controls.MediaElement.Clock%2A> プロパティによって決定されます。  <xref:System.Windows.Controls.MediaElement.Clock%2A> が `null` の場合、メディア オブジェクトは独立モードです。  <xref:System.Windows.Controls.MediaElement.Clock%2A> が null 以外の場合、メディア オブジェクトはクロック モードです。  既定では、メディア オブジェクトは独立モードです。  
  
### 独立モード  
 独立モードでは、メディア コンテンツによってメディアの再生が実行されます。  独立モードは次のオプションを有効にします。  
  
-   メディアの <xref:System.Uri> を直接指定することができます。  
  
-   メディアの再生を直接制御できます。  
  
-   メディアの <xref:System.Windows.Controls.MediaElement.Position%2A> プロパティと <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> プロパティを変更できます。  
  
 メディアは、<xref:System.Windows.Controls.MediaElement> オブジェクトの <xref:System.Windows.Controls.MediaElement.Source%2A> プロパティを設定すること、または <xref:System.Windows.Media.MediaPlayer> オブジェクトの <xref:System.Windows.Media.MediaPlayer.Open%2A> メソッドを呼び出すことのいずれかによって読み込まれます。  
  
 独立モードでメディアの再生を制御するために、メディア オブジェクトのコントロール メソッドを使用することはできません。  使用可能なコントロール メソッドは、<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A>、<xref:System.Windows.Controls.MediaElement.Stop%2A> です。  <xref:System.Windows.Controls.MediaElement> では、これらのメソッドを使用して対話的に制御できるのは、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState> に設定されている場合です。  メディア オブジェクトがクロック モードの場合、これらのメソッドは使用できません。  
  
 独立モードの使用例については、「[MediaElement \(再生、一時停止、停止、ボリューム、および速度\) を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### クロック モード  
 クロック モードでは、<xref:System.Windows.Media.MediaTimeline> によって、メディアの再生が実行されます。  クロック モードには次の特徴があります。  
  
-   メディアの <xref:System.Uri> は、<xref:System.Windows.Media.MediaTimeline> を通じて間接的に設定されます。  
  
-   メディアの再生をクロックで制御できます。  メディア オブジェクトのコントロール メソッドは使用できません。  
  
-   メディアは、<xref:System.Windows.Media.MediaTimeline> オブジェクトの <xref:System.Windows.Media.MediaTimeline.Source%2A> プロパティを設定すること、タイムラインからクロックを作成すること、およびメディア オブジェクトにクロックを割り当てることによって読み込まれます。  <xref:System.Windows.Media.Animation.Storyboard> 内の <xref:System.Windows.Media.MediaTimeline> が <xref:System.Windows.Controls.MediaElement> をターゲットとする場合にも、メディアはこの方法によって読み込まれます。  
  
 クロック モードでメディアの再生を制御するには、<xref:System.Windows.Media.Animation.ClockController> コントロール メソッドを使用する必要があります。  <xref:System.Windows.Media.Animation.ClockController> は、<xref:System.Windows.Media.MediaClock> の <xref:System.Windows.Media.Animation.ClockController> プロパティから取得します。  クロック モードで <xref:System.Windows.Controls.MediaElement> オブジェクトまたは <xref:System.Windows.Media.MediaPlayer> オブジェクトのいずれかのコントロール メソッドを使用しようとすると、<xref:System.InvalidOperationException> がスローされます。  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 クロック モードの使用例については、「[ストーリーボードを使用して MediaElement を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>   
## MediaElement クラス  
 アプリケーションへのメディアの追加は、アプリケーションの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に <xref:System.Windows.Controls.MediaElement> コントロールを追加し、含めるメディアに <xref:System.Uri> を提供するというように簡単に行うことができます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 でサポートされているすべての種類のメディアがサポートされています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で、<xref:System.Windows.Controls.MediaElement> を簡単に使用する例を次に示します。  
  
 [!code-xml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。  再生が終わると、メディアは閉じられ、すべてのメディア リソース \(ビデオ メモリを含む\) は解放されます。  これは、<xref:System.Windows.Controls.MediaElement> オブジェクトの既定の動作で、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティと <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> プロパティによって制御されます。  
  
### MediaElement の制御  
 <xref:System.Windows.FrameworkElement.IsLoaded%2A> が `true` または `false` のとき、それぞれ、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティと <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> プロパティは、<xref:System.Windows.Controls.MediaElement> の動作を制御します。  プロパティで設定される <xref:System.Windows.Controls.MediaState> は、メディアの再生動作に影響します。  たとえば、既定の <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> は <xref:System.Windows.Controls.MediaState> で、既定の <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> は <xref:System.Windows.Controls.MediaState> です。  したがって、<xref:System.Windows.Controls.MediaElement> が読み込まれ、[プリロール](GTMT)が完了するとすぐにメディアは再生を始めます。  再生が終わるとメディアは閉じられ、すべてのメディア リソースは解放されます。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> プロパティと <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> プロパティ以外にも、メディアの再生を制御する方法があります。  クロック モードでは、クロックによって <xref:System.Windows.Controls.MediaElement> を制御できるほか、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState> の場合は、コントロール メソッドで対話的に制御できます。  <xref:System.Windows.Controls.MediaElement> は、制御に対するこのような競合を、次の優先順位によって解決します。  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  メディアがアンロードされた場合。  すべてのメディア リソースが、既定で解放されます。<xref:System.Windows.Media.MediaClock> が <xref:System.Windows.Controls.MediaElement> に関連付けられているときでも同様です。  
  
2.  <xref:System.Windows.Media.MediaClock>.  メディアに <xref:System.Windows.Controls.MediaElement.Clock%2A> が含まれている場合に有効になります。  メディアがアンロードされた場合、<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> が <xref:System.Windows.Controls.MediaState> である限り、<xref:System.Windows.Media.MediaClock> が有効になります。  クロック モードは、<xref:System.Windows.Controls.MediaElement> が読み込まれたときの動作を常にオーバーライドします。  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>.  メディアが読み込まれた場合。  
  
4.  対話型コントロール メソッド。  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> が <xref:System.Windows.Controls.MediaState> の場合。  使用可能なコントロール メソッドは、<xref:System.Windows.Controls.MediaElement.Play%2A>、<xref:System.Windows.Controls.MediaElement.Pause%2A>、<xref:System.Windows.Controls.MediaElement.Close%2A>、<xref:System.Windows.Controls.MediaElement.Stop%2A> です。  
  
### MediaElement の表示  
 <xref:System.Windows.Controls.MediaElement> を表示するには、描画されるコンテンツが必要で、コンテンツが読み込まれるまでは、その <xref:System.Windows.FrameworkElement.ActualWidth%2A> プロパティと <xref:System.Windows.FrameworkElement.ActualHeight%2A> プロパティは 0 に設定されます。  オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。  ビデオ コンテンツでは、<xref:System.Windows.Controls.MediaElement.MediaOpened> イベントが発生すると、<xref:System.Windows.FrameworkElement.ActualWidth%2A> と <xref:System.Windows.FrameworkElement.ActualHeight%2A> は読み込まれたメディアのサイズを報告します。  したがって、メディアが読み込まれるまでは、<xref:System.Windows.FrameworkElement.Width%2A> プロパティまたは <xref:System.Windows.FrameworkElement.Height%2A> プロパティが設定されていない限り、<xref:System.Windows.Controls.MediaElement> は [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 内の物理的なスペースを占めません。  
  
 <xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティの両方を設定すると、メディアは、<xref:System.Windows.Controls.MediaElement> に提供された領域に合うように引き伸ばされます。  メディアの元の[縦横比](GTMT)を維持するには、<xref:System.Windows.FrameworkElement.Width%2A> プロパティまたは <xref:System.Windows.FrameworkElement.Height%2A> プロパティのいずれか一方のみを設定する必要があります。  <xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティの両方を設定すると、メディアが要素の固定サイズに含まれ、望ましくない場合もあります。  
  
 固定サイズの要素を含まないようにするため、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアを[プリロール](GTMT)することができます。  これを行うには、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> を <xref:System.Windows.Controls.MediaState> または <xref:System.Windows.Controls.MediaState> のいずれかに設定します。  <xref:System.Windows.Controls.MediaState> 状態では、メディアはプリロールされ、最初のフレームが表示されます。  <xref:System.Windows.Controls.MediaState> 状態では、メディアは[プリロール](GTMT)され、再生が始まります。  
  
<a name="mediaplayer"></a>   
## MediaPlayer クラス  
 <xref:System.Windows.Controls.MediaElement> クラスはフレームワーク要素ですが、<xref:System.Windows.Media.MediaPlayer> クラスは <xref:System.Windows.Media.Drawing> オブジェクトで使用するために設計されています。  Drawing オブジェクトは、パフォーマンス上の利点を得るためにフレームワーク レベルの機能を犠牲にしてもかまわない場合や、<xref:System.Windows.Freezable> 機能が必要な場合に使用されます。  <xref:System.Windows.Media.MediaPlayer> を使用すると、メディア コンテンツをアプリケーションに提供すると共に、これらの機能を利用できます。  <xref:System.Windows.Controls.MediaElement> と同様に、<xref:System.Windows.Media.MediaPlayer> は、独立モードまたはクロック モードで使用できますが、<xref:System.Windows.Controls.MediaElement> オブジェクトのアンロードされた状態および読み込まれた状態はありません。  これにより、<xref:System.Windows.Media.MediaPlayer> の再生制御の複雑さが軽減されています。  
  
### MediaPlayer の制御  
 <xref:System.Windows.Media.MediaPlayer> はステートレスであるため、メディアの再生を制御するには 2 つの方法しかありません。  
  
1.  対話型コントロール メソッド。  独立モード \(`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> プロパティ\) の場合。  
  
2.  <xref:System.Windows.Media.MediaClock>.  メディアに <xref:System.Windows.Media.MediaPlayer.Clock%2A> が含まれている場合に有効になります。  
  
### MediaPlayer の表示  
 技術的に、<xref:System.Windows.Media.MediaPlayer> は、物理的な形式を持たないため表示することはできません。  ただし、<xref:System.Windows.Media.VideoDrawing> クラスを使用して、<xref:System.Windows.Media.Drawing> でメディアを提供するために使用することはできます。  <xref:System.Windows.Media.VideoDrawing> を使用してメディアを表示する例を次に示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <xref:System.Windows.Media.Drawing> オブジェクトの詳細については、「[Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.DrawingGroup>   
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)