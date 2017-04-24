---
title: "グラフィックスとマルチメディア | Microsoft Docs"
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
  - "アニメーション, 機能"
  - "グラフィックス機能"
  - "メディア, 機能"
  - "サウンド効果"
  - "遷移効果"
  - "ビデオ効果"
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# グラフィックスとマルチメディア
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、マルチメディア、ベクター グラフィックス、アニメーション、およびコンテンツ構成のサポートが提供されるので、開発者はユーザーの関心を引くユーザー インターフェイスやコンテンツを簡単に開発できます。  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して、ベクター グラフィックスまたは複雑なアニメーションを作成し、メディアをアプリケーションに統合することができます。  
  
 ここでは、アプリケーションにグラフィックス、遷移効果、サウンド、およびビデオを追加できるようにする [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス、アニメーション、およびメディア機能について説明します。  
  
> [!NOTE]
>  Windows サービスで WPF 型を使用することは避けることを強くお勧めします。  Windows サービスで WPF 型を使用しようとした場合、サービスが期待どおりに動作しないことがあります。  
  
   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## WPF 4 のグラフィックスとマルチメディアの新機能  
 グラフィックスとアニメーションに関するいくつかの変更点があります。  
  
-   レイアウトの丸め  
  
     オブジェクトの一方の端が 1 つのピクセル デバイスに位置する場合、DPI に依存しないグラフィック システムでは、不鮮明な表示 \(半透明のエッジ\) などのレンダリング アイテムを作成できます。  以前のバージョンの WPF には、このような場合の処理に役立つピクセル スナップが含まれています。  Silverlight 2 では、レイアウトの丸めが導入されたことで、端がピクセル境界全体に位置するように、要素を移動する別の方法が利用できます。  WPF では今回、<xref:System.Windows.FrameworkElement> にアタッチされた <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> プロパティで、レイアウトの丸めがサポートされました。  
  
-   キャッシュ済みコンポジション  
  
     新しい <xref:System.Windows.Media.BitmapCache> クラスと <xref:System.Windows.Media.BitmapCacheBrush> クラスを使用すると、ビジュアル ツリーの複雑な部分をビットマップとしてキャッシュすることで、描画時間を大幅に短縮できます。  このビットマップに対しては、マウス クリックなどのユーザー入力ができるため、その他の要素上にブラシのように描画することができます。  
  
-   Pixel Shader 3 のサポート  
  
     WPF 4 は、WPF 3.5 SP1 で導入された <xref:System.Windows.Media.Effects.ShaderEffect> のサポートを基に、アプリケーションで Pixel Shader \(PS\) Version 3.0 を使用したエフェクトを記述できるようにします。  PS 3.0 のシェーダー モデルは、サポートされているハードウェア上でより多くのエフェクトを使用できるという点で、PS 2.0 より洗練されています。  
  
-   イージング関数  
  
     イージング関数を使用すると、アニメーションの動きを詳細に制御できるため、アニメーションが魅力的になります。  たとえば、<xref:System.Windows.Media.Animation.ElasticEase> をアニメーションに適用すると、アニメーションに弾むような動作を加えることができます。  イージングの種類の詳細については、<xref:System.Windows.Media.Animation> 名前空間のドキュメントを参照してください。  
  
<a name="graphics_and_rendering"></a>   
## グラフィックスおよび描画  
 WPF では、高品質 2D グラフィックスがサポートされます。  ブラシ、ジオメトリ、イメージ、変換などの機能が用意されています。  詳細については、「[グラフィックス](../../../../docs/framework/wpf/graphics-multimedia/graphics.md)」を参照してください。  グラフィック要素の描画は、<xref:System.Windows.Media.Visual> クラスに基づいています。  画面のビジュアル オブジェクトの構造は、ビジュアル ツリーによって表されます。  詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
### 2\-D 図形  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、次の図に示すような四角形や楕円などの、一般的に使用されるベクター描画の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 図形のライブラリが用意されています。  
  
 ![楕円と四角形](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.png "WPFIntroFigure4")  
  
 これらの固有の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 図形は単なる図形ではなく、キーボード入力やマウス入力を含む最も一般的なコントロールで得られる機能の多くを実装するプログラミング可能な要素です。  次の例は、<xref:System.Windows.Shapes.Ellipse> 要素をクリックすることによって発生した <xref:System.Windows.UIElement.MouseUp> イベントの処理方法を示しています。  
  
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
  
 上記の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップおよび分離コードの出力を次の図に示します。  
  
 !["you clicked the ellipse&#33;" というテキストを含むウィンドウ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 詳細については、「[WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)」を参照してください。  入門用のサンプルについては、[Shape 要素のサンプル](http://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
### 2\-D ジオメトリ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で提供される [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 図形では不十分な場合は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] でのジオメトリおよびパスのサポートを利用して独自の図形を作成します。  ジオメトリを使用して図形を描画ブラシとして作成し、他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素をクリップする方法を次の図に示します。  
  
 ![パスのさまざまな使用](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.png "WPFIntroFigure5")  
  
 詳細については、「[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)」を参照してください。  入門用のサンプルについては、[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)を参照してください。  
  
### 2\-D 効果  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、さまざまな効果を作成するために使用できる [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] クラスのライブラリが用意されています。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] レンダリング機能を使用すると、グラデーション、ビットマップ、描画、およびビデオを持つ [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を塗りつぶすことができます。また、回転、拡大縮小、および[傾斜](GTMT)を使用して要素を操作できます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ブラシを使用して得られる多くの効果の例を次の図に示します。  
  
 ![さまざまなブラシの図](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.png "WPFIntroFigure6")  
  
 詳細については、「[WPF のブラシの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md)」を参照してください。  入門用のサンプルについては、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  
  
<a name="rendering"></a>   
## 3\-D レンダリング  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、さらに人目を引くレイアウト、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、およびデータの視覚化を実現するために [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] グラフィックス サポートと統合された一連の [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] レンダリング機能が用意されています。  たとえば、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、次の図に示すように [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 図形のサーフェイスに [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] イメージを描画できます。  
  
 ![Visual3D サンプルのスクリーンショット](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 詳細については、「[3\-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)」を参照してください。  入門用のサンプルについては、[3\-D ソリッドのサンプル](http://go.microsoft.com/fwlink/?LinkID=159964)を参照してください。  
  
<a name="animation"></a>   
## アニメーション  
 アニメーションを使用すると、コントロールおよび要素の拡張、振動、回転、およびフェード効果を実現できます。また、人の関心を引くページの遷移なども作成できます。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではほとんどのプロパティをアニメーション化できるため、ほとんどの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] オブジェクトをアニメーション化できるだけでなく、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用して作成するカスタム オブジェクトをアニメーション化することもできます。  
  
 ![アニメーション キューブのイメージ](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  その他の入門用のサンプルについては、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)を参照してください。  
  
<a name="media"></a>   
## メディア  
 イメージ、ビデオ、およびオーディオは、情報およびユーザー エクスペリエンスを伝えるメディア リッチな手段です。  
  
### \[イメージ\]  
 アイコン、背景、およびアニメーションのパーツを含むイメージは、ほとんどのアプリケーションの中核です。  イメージは頻繁に使用する必要があるため、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ではさまざまな方法でイメージを処理できます。  その方法の一例を次の図に示します。  
  
 ![スタイル サンプル スクリーンショット](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro\_EventTriggers")  
  
 詳細については、「[イメージングの概要](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)」を参照してください。  
  
### ビデオとオーディオ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のグラフィックス機能の主要な特性は、ビデオやオーディオを含むマルチメディアの処理をネイティブにサポートすることです。  次の例は、アプリケーションにメディア プレーヤーを挿入する方法を示しています。  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <xref:System.Windows.Controls.MediaElement> はビデオとオーディオの両方を再生でき、カスタム [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を簡単に作成できる拡張性を備えています。  
  
 詳細については、「[マルチメディアの概要](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media>   
 <xref:System.Windows.Media.Animation>   
 <xref:System.Windows.Media.Media3D>   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [WPF での図形と基本描画の概要](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [3\-D Graphics](http://msdn.microsoft.com/ja-jp/565c1f3c-235b-47de-b05b-3b53ed63f1b8)   
 [Multimedia](http://msdn.microsoft.com/ja-jp/44a8dcd0-80cb-4db0-a222-87cde68c2fac)