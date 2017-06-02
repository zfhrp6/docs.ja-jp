---
title: "イメージングの概要 | Microsoft Docs"
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
  - "変換 (イメージを)"
  - "トリミング (イメージを)"
  - "デコード (イメージ形式を)"
  - "表示 (イメージを)"
  - "エンコード (イメージ形式を)"
  - "形式のデコード (イメージ)"
  - "形式のエンコード (イメージ)"
  - "イメージ メタデータ"
  - "イメージ, イメージングの概要"
  - "イメージング API"
  - "メタデータ, イメージ"
  - "イメージによる塗りつぶし"
  - "回転 (イメージを)"
  - "引き伸ばし (イメージの)"
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# イメージングの概要
ここでは、[!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]の概要を説明します。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]を使用すると、イメージの表示、変換、および書式設定を行うことができます。  
  
   
  
<a name="_wpfImaging"></a>   
## WPF イメージング コンポーネント  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]では、[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 内のイメージング機能が大幅に強化されています。  ビットマップの表示や一般的なコントロール上でのイメージの使用などのイメージング機能は、以前は [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] または [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] ライブラリに依存していました。  これらの [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] では、基本的なイメージング機能は提供されていますが、コーデック拡張機能のサポートや忠実性の高いイメージのサポートなどの機能は含まれていません。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]は、[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] および [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] の欠点を克服し、アプリケーション内でイメージを表示および使用するための新しい [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] のセットを提供するために設計されています。  
  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]の [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]、マネージ コンポーネント、およびアンマネージ コンポーネントにアクセスするには、2 つの方法があります。  アンマネージ コンポーネントは、次の機能を提供します。  
  
-   新しいイメージ形式または専用のイメージ形式の拡張モデル。  
  
-   [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)]、[!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)]、アイコン \(.ico\) などのネイティブ イメージ形式に対するパフォーマンスとセキュリティの向上。  
  
-   1 チャネルあたり 8 ビット \(1 ピクセルあたり 32 ビット\) までの高いビット深度のイメージ データの保存。  
  
-   非破壊のイメージ スケーリング、トリミング、および回転。  
  
-   簡略化された色の管理。  
  
-   ファイル内の専用のメタデータのサポート。  
  
-   マネージ コンポーネントでは、アンマネージ インフラストラクチャを利用して、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、アニメーション、グラフィックスなどのその他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の機能とイメージとのシームレスな統合を提供します。  マネージ コンポーネントには、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーション内の新しいイメージ形式の自動認識を可能にする、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] のイメージング コーデック拡張モデルによる利点もあります。  
  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]のマネージ [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の大部分は <xref:System.Windows.Media.Imaging?displayProperty=fullName> 名前空間にありますが、<xref:System.Windows.Media.ImageBrush> や <xref:System.Windows.Media.ImageDrawing> などのいくつかの重要な種類は <xref:System.Windows.Media?displayProperty=fullName> 名前空間にあり、<xref:System.Windows.Controls.Image> は <xref:System.Windows.Controls?displayProperty=fullName> 名前空間にあります。  
  
 ここでは、マネージ コンポーネントに関する追加情報を提供します。  アンマネージ [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] の詳細については、「[Unmanaged WPF Imaging Component](_wic_lh)」を参照してください。  
  
<a name="_imageformats"></a>   
## WPF イメージ形式  
 コーデックは特定のメディア形式をデコードまたはエンコードするために使用されます。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] には、[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]、[!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]、[!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]、[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]、[!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]、[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]、および ICON のイメージ形式のコーデックが含まれます。  これらのコーデックにより、アプリケーションでは、それぞれのイメージ形式のデコードと、ICON を除く各イメージ形式のエンコードを実行できるようになります。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> はイメージのデコードとエンコードに使用される重要なクラスです。  これは [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] パイプラインの基本的なビルド ブロックであり、単一の一定なピクセル セットを特定のサイズおよび解像度で表します。  <xref:System.Windows.Media.Imaging.BitmapSource> は複数のフレーム イメージの個別のフレームとしたり、<xref:System.Windows.Media.Imaging.BitmapSource> で実行される変換の結果にしたりできます。  これは <xref:System.Windows.Media.Imaging.BitmapFrame> などの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] イメージングで使用される主なクラスの多くの親です。  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> は、イメージ形式の実際のビットマップ データを格納するために使用されます。  [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] や [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] などの形式は 1 イメージあたり複数のフレームをサポートしますが、多くのイメージ形式は単一の <xref:System.Windows.Media.Imaging.BitmapFrame> のみをサポートします。  フレームは、デコーダーによって入力データとして使用され、イメージ ファイルを作成するためにエンコーダーに渡されます。  
  
 <xref:System.Windows.Media.Imaging.BitmapFrame> がどのように <xref:System.Windows.Media.Imaging.BitmapSource> から作成され、[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] イメージに追加されるかを次の例に示します。  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### イメージ形式のデコード  
 イメージ デコードとは、イメージ形式をシステムで使用できるイメージ データに変換することです。  その後、イメージ データは、表示、処理、または別の形式にエンコードするために使用できます。  デコーダーは、イメージ形式に基づいて選択されます。  特定のデコーダーが指定されない限り、コーデックの選択は自動的に行われます。  「[WPF でのイメージの表示](#_displayingimages)」セクションで、自動デコードの例を示します。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]の アンマネージ インターフェイスを使用して開発され、システムに登録されたカスタム形式デコーダーは、自動的にデコーダーの選択に追加されます。  これによって、カスタム形式を自動的に [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで表示できるようになります。  
  
 ビットマップ デコータを使用して [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 形式のイメージをデコードする例を次に示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### イメージ形式のエンコード  
 イメージ エンコードとは、イメージ データを特定のイメージ形式に変換することです。  その後、エンコードされたイメージ データは、新しいイメージ ファイルを作成するために使用できます。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]は、前に説明したイメージ形式のそれぞれに対するエンコーダーを提供します。  
  
 エンコーダーを使用して新しく作成されるビットマップ イメージを保存する例を次に示します。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## WPF でのイメージの表示  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションでイメージを表示するにはいくつかの方法があります。  イメージは、<xref:System.Windows.Controls.Image> コントロールを使用して表示したり、<xref:System.Windows.Media.ImageBrush> を使用してビジュアル上に描画したり、<xref:System.Windows.Media.ImageDrawing> を使用して描画したりできます。  
  
### イメージ コントロールの使用  
 <xref:System.Windows.Controls.Image> は、フレームワーク要素であり、アプリケーション内のイメージを表示する主な方法です。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.Controls.Image> を属性構文とプロパティ構文の 2 つの方法で使用できます。  属性構文とプロパティ タグ構文の両方を使用して、幅が 200 ピクセルのイメージをレンダリングする方法を次の例に示します。  属性およびプロパティの構文については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 多くの例で、イメージ ファイルの参照に <xref:System.Windows.Media.Imaging.BitmapImage> オブジェクトを使用しています。  <xref:System.Windows.Media.Imaging.BitmapImage> は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 読み込み用に最適化された専用の <xref:System.Windows.Media.Imaging.BitmapSource> で、イメージを <xref:System.Windows.Controls.Image> コントロールの <xref:System.Windows.Controls.Image.Source%2A> として簡単に表示できる方法です。  
  
 コードを使用して幅が 200 ピクセルのイメージをレンダリングする方法を次の例に示します。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> は、複数のプロパティでの初期化を最適化するために <xref:System.ComponentModel.ISupportInitialize> インターフェイスを実装しています。  プロパティを変更できるのは、オブジェクトの初期化時だけです。  <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> を呼び出して初期化が開始されたことを通知し、<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> を呼び出して初期化が完了したことを通知します。  初期化されると、プロパティの変更は無視されます。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### イメージの回転、変換、およびトリミング  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用すると、ユーザーは、<xref:System.Windows.Media.Imaging.BitmapImage> のプロパティを使用して、または <xref:System.Windows.Media.Imaging.CroppedBitmap> や <xref:System.Windows.Media.Imaging.FormatConvertedBitmap> などの追加 <xref:System.Windows.Media.Imaging.BitmapSource> オブジェクトを使用して、イメージを変換できます。  これらのイメージの変換では、イメージのスケーリングまたは回転、イメージのピクセル形式の変更、またはイメージのトリミングを行うことができます。  
  
 イメージの回転は、<xref:System.Windows.Media.Imaging.BitmapImage> の <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> プロパティを使用して実行されます。  回転は、90°単位でのみ可能です。  次の例では、イメージが 90°回転されます。  
  
 [!code-xml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 グレースケールなどの別のピクセル形式へのイメージの変換は、<xref:System.Windows.Media.Imaging.FormatConvertedBitmap> を使用して行われます。  次の例では、イメージが <xref:System.Windows.Media.PixelFormats.Gray4%2A> に変換されます。  
  
 [!code-xml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 イメージをトリミングするには、<xref:System.Windows.Controls.Image> または <xref:System.Windows.Media.Imaging.CroppedBitmap> の <xref:System.Windows.UIElement.Clip%2A> プロパティを使用できます。  通常、イメージの一部を表示するだけの場合は、<xref:System.Windows.UIElement.Clip%2A> を使用する必要があります。  トリミングされたイメージをエンコードして保存する必要がある場合は、<xref:System.Windows.Media.Imaging.CroppedBitmap> を使用する必要があります。  次の例では、イメージが <xref:System.Windows.Media.EllipseGeometry> を使用している Clip プロパティを使用してトリミングされます。  
  
 [!code-xml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### イメージの引き伸ばし  
 <xref:System.Windows.Controls.Image.Stretch%2A> プロパティは、コンテナーを塗りつぶすためにイメージを引き伸ばす方法を制御します。  <xref:System.Windows.Controls.Image.Stretch%2A> プロパティは、<xref:System.Windows.Media.Stretch> 列挙体によって定義された次の値を受け入れます。  
  
-   <xref:System.Windows.Media.Stretch> : イメージは出力領域を塗りつぶすために引き伸ばされません。  イメージが出力領域よりも大きい場合は、そのイメージは出力領域に描画され、領域に収まらない部分がトリミングされます。  
  
-   <xref:System.Windows.Media.Stretch> : イメージは出力領域に合わせてスケーリングされます。  イメージの高さと幅は別々にスケーリングされるため、イメージの元の縦横比が維持されない場合があります。  つまり、出力コンテナーを完全に塗りつぶすために、イメージがいびつになることがあります。  
  
-   <xref:System.Windows.Media.Stretch> : イメージは、出力領域内に完全に収まるようにスケーリングされます。  イメージの縦横比は維持されます。  
  
-   <xref:System.Windows.Media.Stretch> : イメージは、イメージの元の縦横比を維持しながら、出力領域を完全に塗りつぶすようにスケーリングされます。  
  
 利用可能な各 <xref:System.Windows.Media.Stretch> 列挙体を <xref:System.Windows.Controls.Image> に適用する例を次に示します。  
  
 次のイメージはこの例の出力結果を表示したものであり、異なる <xref:System.Windows.Controls.Image.Stretch%2A> 設定をイメージに適用した場合の効果を示しています。  
  
 ![別の TileBrush Stretch 設定](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.png "img\_mmgraphics\_stretchenum")  
さまざまな Stretch 設定  
  
 [!code-xml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### イメージによる塗りつぶし  
 イメージは、<xref:System.Windows.Media.Brush> を使用して塗りつぶすことによってもアプリケーション内に表示できます。  ブラシを使用すると、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] オブジェクトに、純色やパターンとイメージの複雑なセットなどを適用できます。  イメージで塗りつぶすには、<xref:System.Windows.Media.ImageBrush> を使用します。  <xref:System.Windows.Media.ImageBrush> は、ビットマップ イメージとしてコンテンツを定義する <xref:System.Windows.Media.TileBrush> の一種です。  <xref:System.Windows.Media.ImageBrush> を使用した場合、その <xref:System.Windows.Media.ImageBrush.ImageSource%2A> プロパティで指定した単一のイメージが表示されます。  イメージをどのように伸縮、配置、および並べて表示するかを制御できるため、ゆがみを防ぎ、パターンやその他の効果を適用できます。  <xref:System.Windows.Media.ImageBrush> で適用できるいくつかの効果を次の図に示します。  
  
 ![ImageBrush の出力例](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
イメージ ブラシは、図形、コントロール、テキストなどの塗りつぶしを行うことができます。  
  
 <xref:System.Windows.Media.ImageBrush> を使用してイメージによってボタンの背景を塗りつぶす方法を次の例に示します。  
  
 [!code-xml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 <xref:System.Windows.Media.ImageBrush> とイメージの描画の詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
<a name="_metadata"></a>   
## イメージ メタデータ  
 一部のイメージ ファイルには、コンテンツまたはファイルの特性を表すメタデータが含まれています。  たとえば、ほとんどのデジタル カメラでは、イメージをキャプチャするために使用されたカメラの型とモデルに関するメタデータを含むイメージが作成されます。  各イメージ形式ではそれぞれ異なる方法でメタデータを処理しますが、[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]では、各サポート対象のイメージ形式のメタデータを保存および取得するための統一された方法が提供されます。  
  
 メタデータへのアクセスは <xref:System.Windows.Media.Imaging.BitmapSource> オブジェクトの <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> プロパティによって提供されます。  <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> は、イメージに含まれるすべてのメタデータを格納する <xref:System.Windows.Media.Imaging.BitmapMetadata> オブジェクトを返します。  このデータは、1 つのメタデータ スキーマまたはさまざまなスキーマの組み合わせにすることができます。  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]は、[!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)]、tEXt \(PNG Textual Data\)、[!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]、[!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)]、[!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)] などのイメージ メタデータ スキーマをサポートします。  
  
 メタデータの読み取りのプロセスを簡略化するために、<xref:System.Windows.Media.Imaging.BitmapMetadata> は、<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>、<xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>、<xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A> などの簡単にアクセスできるいくつかの名前付きプロパティを提供します。  これらの名前付きプロパティの多くはメタデータを書き込むためにも使用できます。  メタデータ クエリ リーダーによって、メタデータを読み取るための追加サポートが行われます。  <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> メソッドは、*"\/app1\/exif\/"* などの文字列クエリを提供することによって、メタデータ クエリ リーダーを取得するために使用されます。  次の例では、<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> は *"\/Text\/Description"* の場所に格納されているテキストを取得するために使用されます。  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 メタデータを書き込むには、メタデータ クエリ ライターが使用されます。  <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> はクエリ ライターを取得し、必要な値を設定します。  次の例では、<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> は *"\/Text\/Description"* の場所に格納されているテキストを書き込むために使用されます。  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## コーデック拡張機能  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]のコア機能は、新しいイメージ コーデックの拡張モデルです。  これらのアンマネージ インターフェイスを使用すると、コーデック開発者は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで新しいイメージ形式を自動的に使用できるように、コーデックを [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] に統合できます。  
  
 拡張 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] のサンプルについては、[Win32 サンプル コーデック](http://go.microsoft.com/fwlink/?LinkID=160052)を参照してください。  このサンプルでは、カスタム イメージ形式のデコーダーおよびエンコーダーを作成する方法を示します。  
  
> [!NOTE]
>  コーデックには、システムで認識するために、デジタル署名を行う必要があります。  
  
## 参照  
 <xref:System.Windows.Media.Imaging.BitmapSource>   
 <xref:System.Windows.Media.Imaging.BitmapImage>   
 <xref:System.Windows.Controls.Image>   
 <xref:System.Windows.Media.Imaging.BitmapMetadata>   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Win32 サンプル コーデック](http://go.microsoft.com/fwlink/?LinkID=160052)