---
title: グラフィックスとマルチメディア
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 74375c468170d58cfa79031ab0030477c29bd445
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566633"
---
# <a name="graphics-and-multimedia"></a>グラフィックスとマルチメディア
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] マルチ メディア、ベクター グラフィックス、アニメーション、およびコンテンツの構成、簡単に興味深いユーザー インターフェイスとコンテンツを構築する開発者向けのサポートを提供します。 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して、ベクター グラフィックスや複雑なアニメーションを作成し、メディアをアプリケーションに統合できます。  
  
 このトピックでは、アプリケーションにグラフィックス、画面切り替え効果、サウンド、ビデオを追加できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス、アニメーション、メディア機能を紹介します。  
  
> [!NOTE]
>  Windows サービスで WPF 型を使用するのは避けることを強くお勧めします。 Windows サービスで WPF 型を使用しようとした場合、サービスが期待どおりに動作しないことがあります。   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 のグラフィックスとマルチメディアの新機能  
 グラフィックスとアニメーションに関するいくつかの変更点があります。  
  
-   レイアウトの丸め  
  
     オブジェクトの端が 1 ピクセル デバイスの中間に位置する場合、DPI に依存しないグラフィックス システムでは、端がぼやけたり半透明になったりするなどのレンダリング アーティファクトが発生することがあります。 以前のバージョンの WPF には、このような場合の処理に役立つピクセル スナップが含まれていました。 Silverlight 2 では、端がピクセル境界全体に位置するように要素を移動する別の方法としてレイアウトの丸めが導入されました。 WPF では、レイアウトの丸め処理を行う、<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>添付プロパティを<xref:System.Windows.FrameworkElement>です。  
  
-   キャッシュ済みコンポジション  
  
     新しいを使用して<xref:System.Windows.Media.BitmapCache>と<xref:System.Windows.Media.BitmapCacheBrush>クラス、複雑なビットマップとしてビジュアル ツリーの一部をキャッシュし、レンダリング時間を大幅に向上します。 ビットマップは、マウス クリックなどのユーザー入力に引き続き応答し、その他の要素上にブラシのように描画できます。  
  
-   Pixel Shader 3 のサポート  
  
     WPF 4 がの上に構築、<xref:System.Windows.Media.Effects.ShaderEffect>サポートできるため、ピクセル シェーダー (PS) バージョン 3.0 を使用して、効果を作成するアプリケーションで WPF 3.5 SP1 で導入されました。 PS 3.0 のシェーダー モデルは PS 2.0 より洗練されており、サポートされているハードウェア上でより多くのエフェクトを使用できます。  
  
-   イージング関数  
  
     イージング関数を使用してアニメーションを強化し、アニメーションの動作をより細かく制御できます。 たとえば、適用することができます、<xref:System.Windows.Media.Animation.ElasticEase>アニメーションのアニメーションばね式の動作を提供します。 詳細については、イージングの型を参照してください、<xref:System.Windows.Media.Animation>名前空間。  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a>グラフィックスとレンダリング  
 WPF では、高品質な 2-D グラフィックがサポートされます。 ブラシ、ジオメトリ、イメージ、図形、変換などの機能が用意されています。 詳しくは、「[グラフィックス](../../../../docs/framework/wpf/graphics-multimedia/graphics.md)」をご覧ください。 グラフィック要素のレンダリングがに基づいて、<xref:System.Windows.Media.Visual>クラスです。 画面のビジュアル オブジェクトの構造は、ビジュアル ツリーで表されます。 詳しくは、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。  
  
### <a name="2-d-shapes"></a>2-D 図形  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、次の図に示す四角形や楕円のような、一般的に使用されるベクター描画の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 図形のライブラリが用意されています。  
  
 ![楕円と四角形](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 これらの固有の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 図形は単なる図形ではなく、一般的なコントロールに期待されるキーボード入力やマウス入力などの機能の多くを実装するプログラミング可能な要素です。 次の例は、処理する方法を示しています、<xref:System.Windows.UIElement.MouseUp>をクリックすると発生するイベント、<xref:System.Windows.Shapes.Ellipse>要素。  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  x:Class="Window1" >  
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />  
</Window>  
```  
  
```csharp  
public partial class Window1  : Window  
{  
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)  
    {  
        MessageBox.Show("You clicked the ellipse!");  
    }  
}  
```  
  
```vb  
Partial Public Class Window1  
    Inherits Window  
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)  
        MessageBox.Show("You clicked the ellipse!")  
    End Sub  
End Class  
```  
  
 上記の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップとコードビハインドの出力を次の図に示します。  
  
 !["you clicked the ellipse&#33;" というテキストを含むウィンドウ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 詳しくは、「 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)」をご覧ください。 入門用のサンプルについては、「[Shape 要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)」をご覧ください。  
  
### <a name="2-d-geometries"></a>2-D ジオメトリ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で提供される [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 図形では不十分な場合は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のジオメトリとパスのサポートを利用して独自に作成できます。 ジオメトリを使用して図形を描画ブラシとして作成し、他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素をクリップする方法を次の図に示します。  
  
 ![パスのさまざまな使用方法](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 詳しくは、「[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)」をご覧ください。 入門用のサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」をご覧ください。  
  
### <a name="2-d-effects"></a>2-D 効果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、さまざまな効果の作成に使用できる [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] クラスのライブラリが用意されています。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] レンダリング機能を使用すると、グラデーション、ビットマップ、描画、ビデオを持つ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を塗りつぶすことができます。また、回転、拡大縮小、傾斜を使用してそれらの要素を操作できます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ブラシを使用して実現できる多くの効果の例を次の図に示します。  
  
 ![さまざまなブラシの図](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 詳しくは、「 [WPF のブラシの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)」をご覧ください。 入門用のサンプルについては、「[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)」をご覧ください。  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a>3-D レンダリング  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、さらに魅力的なレイアウト、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、データの視覚化を実現するために [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] グラフィックス サポートと統合された一連の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] レンダリング機能が用意されています。 たとえば、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、次の図に示すように [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] イメージを [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 図形のサーフェイスにレンダリングできます。  
  
 ![Visual3D サンプルのスクリーンショット](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 詳しくは、「 [3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)」をご覧ください。 入門用のサンプルについては、「[3-D ソリッドのサンプル](http://go.microsoft.com/fwlink/?LinkID=159964)」をご覧ください。  
  
<a name="animation"></a>   
## <a name="animation"></a>アニメーション  
 アニメーションを使用すると、コントロールや要素を拡大、振動、回転、フェードさせることができ、魅力的なページ遷移なども作成できです。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではほとんどのプロパティをアニメーション化できるため、ほとんどの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] オブジェクトをアニメーション化できるだけでなく、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して作成するカスタム オブジェクトをアニメーション化することもできます。  
  
 ![アニメーション キューブのイメージ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。 入門用のサンプルについては、「[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)」をご覧ください。  
  
<a name="media"></a>   
## <a name="media"></a>メディア  
 イメージ、ビデオ、オーディオは、情報とユーザー エクスペリエンスを伝えるメディア リッチな手段です。  
  
### <a name="images"></a>イメージ  
 アイコン、背景、アニメーションのパーツを含むイメージは、ほとんどのアプリケーションの中核です。 イメージは頻繁に使用する必要があるため、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではさまざまな方法でイメージを処理する機能を公開しています。 その方法の 1 つを次の図に示します。  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
 詳しくは、「 [イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」をご覧ください。  
  
### <a name="video-and-audio"></a>ビデオとオーディオ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のグラフィックス機能の中核となる機能は、ビデオやオーディオを含むマルチメディアの処理をネイティブにサポートすることです。 次の例では、メディア プレーヤーをアプリケーションに挿入する方法を示しています。  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> オーディオとビデオを再生できるは、カスタムの簡単な作成を許可するのに十分な拡張[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]です。  
  
 詳しくは、「[マルチメディアの概要](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [アニメーションおよびタイミング](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [3-D グラフィックス](http://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [マルチメディア](http://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
