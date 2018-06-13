---
title: マルチメディアの概要
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 7a986125cff1ff4812528212fa3aee7689af1f16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566432"
---
# <a name="multimedia-overview"></a>マルチメディアの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のマルチメディア機能を使用してアプリケーションにオーディオとビデオを統合することで、ユーザー エクスペリエンスを向上させることできます。 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のマルチメディア機能の概要を説明します。  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>メディア API  
 <xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>クラスを使用するオーディオまたはビデオ コンテンツを表示します。 これらのクラスは、対話式またはクロックで制御できます。 これらのクラスは、メディアを再生するために [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 のコントロールで使用できます。 どちらのクラスを使用するかは、シナリオによって決まります。  
  
 <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.UIElement>でサポートされている、[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)あり、多くのコントロールのコンテンツとして使用することができます。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でコードとして使用することもできます。 <xref:System.Windows.Media.MediaPlayer>、その一方で、は用に設計された<xref:System.Windows.Media.Drawing>オブジェクトおよびレイアウトをサポートしません。 使用して読み込まれたメディア、<xref:System.Windows.Media.MediaPlayer>でのみ表示できますを使用して、<xref:System.Windows.Media.VideoDrawing>またはと直接やり取りすることによって、<xref:System.Windows.Media.DrawingContext>です。 <xref:System.Windows.Media.MediaPlayer> XAML では使用できません。  
  
 描画オブジェクトと描画コンテキストの詳細については、「[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」を参照してください。  
  
> [!NOTE]
>  アプリケーションでメディアを配布するときに、プロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>メディア再生モード  
  
> [!NOTE]
>  両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>のようなメンバーが存在します。 このセクションのリンクを参照してください、<xref:System.Windows.Controls.MediaElement>クラス メンバーです。 メンバーがリンクされて、特に明記されていない限り、<xref:System.Windows.Controls.MediaElement>クラスも含まれて、<xref:System.Windows.Media.MediaPlayer>クラスです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でのメディアの再生を理解するには、メディアを再生できる複数のモードを理解しておく必要があります。 両方<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.MediaPlayer>、独立したモードとクロック モードの 2 つの別のメディア モードで使用できます。 メディアのモードはによって決定されます、<xref:System.Windows.Controls.MediaElement.Clock%2A>プロパティです。 ときに<xref:System.Windows.Controls.MediaElement.Clock%2A>は`null`、独立したモードでは、メディア オブジェクト。 ときに、<xref:System.Windows.Controls.MediaElement.Clock%2A>はクロック モードでは、null 以外の場合、メディア オブジェクト。 既定では、メディア オブジェクトは Independent モードになっています。  
  
### <a name="independent-mode"></a>Independent モード  
 Independent モードでは、メディア コンテンツがメディアの再生を行います。 Independent モードには、次のオプションがあります。  
  
-   メディアの<xref:System.Uri>直接指定することができます。  
  
-   メディアの再生を直接制御できます。  
  
-   メディアの<xref:System.Windows.Controls.MediaElement.Position%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティを変更できます。  
  
 いずれかの設定によってメディアが読み込まれる、<xref:System.Windows.Controls.MediaElement>オブジェクトの<xref:System.Windows.Controls.MediaElement.Source%2A>プロパティまたは呼び出すことによって、<xref:System.Windows.Media.MediaPlayer>オブジェクトの<xref:System.Windows.Media.MediaPlayer.Open%2A>メソッドです。  
  
 Independent モードでメディアの再生を制御するには、メディア オブジェクトの制御メソッドを使用できます。 コントロールに使用できる方法は<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>です。 <xref:System.Windows.Controls.MediaElement>、これらのメソッドを使用して対話型のコントロールは使用可能な場合に、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>に設定されている<xref:System.Windows.Controls.MediaState.Manual>です。 メディア オブジェクトが Clock モードの場合、これらのメソッドは使用できません。  
  
 Independent モードの例については、「[MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)」を参照してください。  
  
### <a name="clock-mode"></a>Clock モード  
 クロック モードで、<xref:System.Windows.Media.MediaTimeline>ドライブ メディアを再生します。 Clock モードには次の特徴があります。  
  
-   メディアの<xref:System.Uri>がを通じて間接的に設定されて、<xref:System.Windows.Media.MediaTimeline>です。  
  
-   メディアの再生は、クロックによって制御できます。 メディア オブジェクトの制御メソッドは使用できません。  
  
-   設定によってメディアが読み込まれる、<xref:System.Windows.Media.MediaTimeline>オブジェクトの<xref:System.Windows.Media.MediaTimeline.Source%2A>タイムラインから時計を作成し、メディア オブジェクトへのクロックの割り当てのプロパティです。 メディアがこのように読み込まれるもときに、<xref:System.Windows.Media.MediaTimeline>内、<xref:System.Windows.Media.Animation.Storyboard>ターゲット、<xref:System.Windows.Controls.MediaElement>です。  
  
 クロック モードでのメディア再生を制御する、<xref:System.Windows.Media.Animation.ClockController>制御メソッドを使用する必要があります。 A<xref:System.Windows.Media.Animation.ClockController>から取得した、<xref:System.Windows.Media.Animation.ClockController>のプロパティ、<xref:System.Windows.Media.MediaClock>です。 いずれかのコントロールのメソッドを使用しようとする場合、<xref:System.Windows.Controls.MediaElement>または<xref:System.Windows.Media.MediaPlayer>クロック モードで、オブジェクト、<xref:System.InvalidOperationException>がスローされます。  
  
 クロックとタイムラインの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 Clock モードの例については、「[ストーリーボードを使用して MediaElement を制御する](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)」を参照してください。  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement クラス  
 追加するだけでは、メディアをアプリケーションに追加する、<xref:System.Windows.Controls.MediaElement>コントロールを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]アプリケーションを提供して、<xref:System.Uri>たいメディアにします。 [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 でサポートされているすべてのメディアが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でもサポートされます。 次の例は、単純な使用量、<xref:System.Windows.Controls.MediaElement>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 このサンプルでは、メディアは、読み込まれるとすぐに自動的に再生されます。 メディアの再生が終了すると、メディアが閉じられ、すべてのメディア リソースが解放されます (ビデオ メモリを含みます)。 これは、既定の動作、<xref:System.Windows.Controls.MediaElement>オブジェクトし、によって制御されます、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティです。  
  
### <a name="controlling-a-mediaelement"></a>MediaElement の制御  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティの動作を制御する、<xref:System.Windows.Controls.MediaElement>とき<xref:System.Windows.FrameworkElement.IsLoaded%2A>は`true`または`false`、それぞれします。 <xref:System.Windows.Controls.MediaState>メディア再生の動作に影響を与えるプロパティが設定されます。 たとえば、既定値<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Play>と既定<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Close>します。 つまり、このとすぐに、<xref:System.Windows.Controls.MediaElement>が読み込まれて、プリロールが完了すると、メディアの再生が開始されるとします。 再生が完了すると、メディアが閉じられ、すべてのメディア リソースが解放されます。  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>と<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>プロパティがメディアの再生を制御する唯一の方法ではありません。 クロック モードで、クロックを制御できます、<xref:System.Windows.Controls.MediaElement>対話型コントロール メソッドが制御できると、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 <xref:System.Windows.Controls.MediaElement> 次の優先順位を評価することによって、このコントロールでの競合を処理します。  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>。 メディアがアンロードされているときに有効です。 これにより、既定では、すべてのメディア リソースを解放する場合でも、<xref:System.Windows.Media.MediaClock>に関連付けられている、<xref:System.Windows.Controls.MediaElement>です。  
  
2.  <xref:System.Windows.Media.MediaClock>。 メディアが含まれている場合、<xref:System.Windows.Controls.MediaElement.Clock%2A>です。 メディアが読み込まれる場合、<xref:System.Windows.Media.MediaClock>限り有効になります、<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 クロック モードでは、アンロード動作より常に優先、<xref:System.Windows.Controls.MediaElement>です。  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>。 メディアが読み込まれているときに有効です。  
  
4.  対話型の制御メソッド。 配置時に<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>は<xref:System.Windows.Controls.MediaState.Manual>します。 コントロールに使用できる方法は<xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、 <xref:System.Windows.Controls.MediaElement.Close%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>です。  
  
### <a name="displaying-a-mediaelement"></a>MediaElement の表示  
 表示する、<xref:System.Windows.Controls.MediaElement>コンテンツをレンダリングする必要があります、これがその<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>プロパティは、コンテンツが読み込まれるまでをゼロに設定します。 オーディオのみのコンテンツでは、これらのプロパティは常に 0 です。 ビデオのコンテンツで 1 回、<xref:System.Windows.Controls.MediaElement.MediaOpened>イベントが発生した、<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>読み込まれたメディアのサイズをレポートには。 つまり、メディアが読み込まれるまで、<xref:System.Windows.Controls.MediaElement>内のすべての物理領域を消費しません、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]しない限り、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティが設定されます。  
  
 両方を設定、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティと、メディアに指定された領域に合わせて拡大を<xref:System.Windows.Controls.MediaElement>です。 か、メディアの元の縦横比を保持するために、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>プロパティは、セットが、両方を指定してください。 両方を設定、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティが望ましいことができない可能性がある要素の固定サイズで表示するメディアになります。  
  
 要素のサイズが固定されることを避けるために、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、メディアをプリロールすることができます。 これは、設定で、<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>いずれかに<xref:System.Windows.Controls.MediaState.Play>または<xref:System.Windows.Controls.MediaState.Pause>です。 <xref:System.Windows.Controls.MediaState.Pause>状態にある場合、メディアはプリロールされし、最初のフレームが表示されます。 <xref:System.Windows.Controls.MediaState.Play>状態にある場合、メディアはプリロールされ、再生が開始します。  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer クラス  
 該当します。、<xref:System.Windows.Controls.MediaElement>クラスは、フレームワーク要素、<xref:System.Windows.Media.MediaPlayer>クラスで使用するものでは<xref:System.Windows.Media.Drawing>オブジェクト。 パフォーマンス上の利点を取得するためにフレームワーク レベルの機能を犠牲にする必要がある場合または描画オブジェクトで使用<xref:System.Windows.Freezable>機能します。 <xref:System.Windows.Media.MediaPlayer> アプリケーションでメディア コンテンツを提供するときにこれらの機能を利用できます。 同様に<xref:System.Windows.Controls.MediaElement>、<xref:System.Windows.Media.MediaPlayer>独立で使用できるまたは時刻のモードはありませんが、<xref:System.Windows.Controls.MediaElement>オブジェクトのアンロードし、読み込み状態。 これは再生コントロールの複雑さを軽減、<xref:System.Windows.Media.MediaPlayer>です。  
  
### <a name="controlling-mediaplayer"></a>Media Player の制御  
 <xref:System.Windows.Media.MediaPlayer>はステートレスであるメディア再生を制御する方法は 2 つです。  
  
1.  対話型の制御メソッド。 独立したモードのときにインプレース (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A>プロパティ)。  
  
2.  <xref:System.Windows.Media.MediaClock>。 メディアが含まれている場合、<xref:System.Windows.Media.MediaPlayer.Clock%2A>です。  
  
### <a name="displaying-a-mediaplayer"></a>MediaPlayer の表示  
 技術的には、<xref:System.Windows.Media.MediaPlayer>物理的に表したものがあるないので、表示されることはできません。 ただしでメディアを表示する使用する、<xref:System.Windows.Media.Drawing>を使用して、<xref:System.Windows.Media.VideoDrawing>クラスです。 次の例での使用、<xref:System.Windows.Media.VideoDrawing>メディアを表示します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 参照してください、[描画オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)の詳細については<xref:System.Windows.Media.Drawing>オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media.DrawingGroup>  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
