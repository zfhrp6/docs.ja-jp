---
title: "WPF グラフィックス レンダリングの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfb9a546ca33b848fbbcbd114951eddc5b000663
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-graphics-rendering-overview"></a>WPF グラフィックス レンダリングの概要
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のビジュアル層の概要について説明します。 ロールに焦点を当てています、<xref:System.Windows.Media.Visual>でのサポートを表示するためのクラス、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]モデル。  
  
  
<a name="role_of_visual_object"></a>   
## <a name="role-of-the-visual-object"></a>ビジュアル オブジェクトの役割  
 <xref:System.Windows.Media.Visual>クラスは、元の基本抽象化すべて<xref:System.Windows.FrameworkElement>オブジェクトが派生します。 また、このクラスは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で新しいコントロールを作成するためのエントリ ポイントとしても機能し、多くの点で Win32 アプリケーション モデルのウィンドウ ハンドル (HWND) と考えることができます。  
  
 <xref:System.Windows.Media.Visual>オブジェクトは、コア[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プライマリ ロールがあるレンダリング サポートを提供するオブジェクト。 などのユーザー インターフェイス コントロール<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.TextBox>から派生して、<xref:System.Windows.Media.Visual>クラス、およびその表示データを保持するに使用します。 <xref:System.Windows.Media.Visual>オブジェクトのサポートを提供します。  
  
-   出力表示: ビジュアルの、シリアル化された永続的な描画内容をレンダリングします。  
  
-   変換: は、ビジュアルで変換を実行します。  
  
-   クリッピング: ビジュアルのクリッピング領域をサポートします。  
  
-   ヒット テスト: 座標またはジオメトリがビジュアルの境界内に含まれているかどうかを判断します。  
  
-   境界ボックスの計算: ビジュアルの四角形領域を決定します。  
  
 ただし、<xref:System.Windows.Media.Visual>オブジェクトが非表示機能のサポートをなど含まれません。  
  
-   イベント処理  
  
-   レイアウト  
  
-   スタイル  
  
-   データ バインディング  
  
-   グローバリゼーション  
  
 <xref:System.Windows.Media.Visual>子クラスを派生する必要があります、パブリックの抽象クラスとして公開されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で公開されるビジュアル オブジェクトの階層構造を次の図に示します。  
  
 ![Visual オブジェクトから派生したクラスのダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visualclass01.png "VisualClass01")  
Visual クラスの階層構造  
  
### <a name="drawingvisual-class"></a>DrawingVisual クラス  
 <xref:System.Windows.Media.DrawingVisual>は、軽量な図形、画像、またはテキストを表示するために使用されるクラスを描画します。 このクラスが軽量と見なされる理由は、レイアウトやイベントの処理を行わないため、実行時のパフォーマンスが向上するからです。 そのため、背景やクリップ アートの描画に適しています。 <xref:System.Windows.Media.DrawingVisual>カスタム ビジュアル オブジェクトの作成に使用できます。 詳しくは、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」をご覧ください。  
  
### <a name="viewport3dvisual-class"></a>Viewport3DVisual クラス  
 <xref:System.Windows.Media.Media3D.Viewport3DVisual> 2D 間の橋渡し<xref:System.Windows.Media.Visual>と<xref:System.Windows.Media.Media3D.Visual3D>オブジェクト。 <xref:System.Windows.Media.Media3D.Visual3D>クラスは、3 D のすべてのビジュアル要素の基本クラスです。 <xref:System.Windows.Media.Media3D.Viewport3DVisual>を定義することが必要です、<xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A>値と<xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A>値。 カメラを使用するとシーンを表示できます。 ビューポートは、投影が 2D サーフェイス上にマップされる場所を設定します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の 3D について詳しくは、「[3-D グラフィックスの概要](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)」をご覧ください。  
  
### <a name="containervisual-class"></a>ContainerVisual クラス  
 <xref:System.Windows.Media.ContainerVisual>クラスはコンテナーとしてのコレクションの使用は<xref:System.Windows.Media.Visual>オブジェクト。 <xref:System.Windows.Media.DrawingVisual>から派生したクラス、<xref:System.Windows.Media.ContainerVisual>ビジュアル オブジェクトのコレクションを含めることができるクラスです。  
  
### <a name="drawing-content-in-visual-objects"></a>ビジュアル オブジェクトの描画コンテンツ  
 A<xref:System.Windows.Media.Visual>オブジェクトとしてレンダリング データを格納する、**ベクター グラフィックス命令リスト**です。 命令リスト内の各項目は、グラフィックス データと関連リソースの低レベル セットを、シリアル化された形式で表します。 描画コンテンツを格納できるレンダリング データには、次の 4 つの種類があります。  
  
|描画コンテンツの種類|説明|  
|--------------------------|-----------------|  
|ベクター グラフィックス|ベクター グラフィックス データ、および関連<xref:System.Windows.Media.Brush>と<xref:System.Windows.Media.Pen>情報。|  
|イメージ|によって定義される領域内のイメージを表す、<xref:System.Windows.Rect>です。|  
|グリフ|レンダリングする描画を表す、 <xref:System.Windows.Media.GlyphRun>、これは、指定したフォント リソースからのグリフのシーケンス。 テキストはこれによって表示されます。|  
|ビデオ|ビデオをレンダリングする描画を表します。|  
  
 <xref:System.Windows.Media.DrawingContext>を設定することができます、 <xref:System.Windows.Media.Visual> visual のコンテンツを持つ。 使用すると、<xref:System.Windows.Media.DrawingContext>一連のグラフィックス システムで後で使用されるレンダリング データを格納する実際には、オブジェクトの描画がコマンド以外の場合はリアルタイムで画面に描画されません。  
  
 作成するときに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]など、制御、 <xref:System.Windows.Controls.Button>、レンダリング データ自体を描画するため、コントロールを暗黙的に生成します。 たとえば、設定、<xref:System.Windows.Controls.ContentControl.Content%2A>のプロパティ、<xref:System.Windows.Controls.Button>グリフの表示形式を格納するコントロールします。  
  
 A<xref:System.Windows.Media.Visual>として 1 つまたは複数のコンテンツについて説明<xref:System.Windows.Media.Drawing>に含まれるオブジェクト、<xref:System.Windows.Media.DrawingGroup>です。 A<xref:System.Windows.Media.DrawingGroup>不透明マスク、変換、ビットマップ効果、およびその内容に適用されているその他の操作についても説明します。 <xref:System.Windows.Media.DrawingGroup>操作は、コンテンツが表示されるときに、次の順序で適用されます: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>、 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>、 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>、 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>、 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>、し<xref:System.Windows.Media.DrawingGroup.Transform%2A>です。  
  
 次の図に順序を<xref:System.Windows.Media.DrawingGroup>レンダリング シーケンス中の操作が適用されます。  
  
 ![操作の DrawingGroup 順序](../../../../docs/framework/wpf/graphics-multimedia/media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
DrawingGroup の操作の順序  
  
 詳しくは、「[Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)」をご覧ください。  
  
#### <a name="drawing-content-at-the-visual-layer"></a>ビジュアル層での描画コンテンツ  
 決して直接インスタンス化する、 <xref:System.Windows.Media.DrawingContext>; など、特定のメソッドから描画コンテキストを取得すること、ただし、<xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>です。 次の例では取得、<xref:System.Windows.Media.DrawingContext>から、<xref:System.Windows.Media.DrawingVisual>四角形の描画を使用しています。  
  
 [!code-csharp[drawingvisualsample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>ビジュアル層で描画コンテンツを列挙する  
 その他の使用方法だけでなく<xref:System.Windows.Media.Drawing>オブジェクトは、の内容を列挙するため、オブジェクト モデルを提供するも、<xref:System.Windows.Media.Visual>です。  
  
> [!NOTE]
>  ビジュアルの内容を列挙しているときに取得する<xref:System.Windows.Media.Drawing>オブジェクト、および、基になる表現ではありませんレンダー データ ベクトル グラフィックス命令リストとして。  
  
 次の例では、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>を取得する方法、<xref:System.Windows.Media.DrawingGroup>の値、<xref:System.Windows.Media.Visual>およびそれを列挙します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>   
## <a name="how-visual-objects-are-used-to-build-controls"></a>ビジュアル オブジェクトを使用してコントロールをビルドする方法  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のオブジェクトの多くは、他のビジュアル オブジェクトで構成されています。そのため、それらのオブジェクトには、子孫オブジェクトのさまざまな階層を格納することができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のユーザー インターフェイス要素 (コントロールなど) の多くは、さまざまな種類のレンダリング要素を表す、複数のビジュアル オブジェクトで構成されています。 たとえば、<xref:System.Windows.Controls.Button>コントロールなど、他のオブジェクトの数を含めることができます<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>、 <xref:System.Windows.Controls.ContentPresenter>、および<xref:System.Windows.Controls.TextBlock>です。  
  
 次のコードは、<xref:System.Windows.Controls.Button>マークアップで定義されています。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 既定値を構成するビジュアル オブジェクトを列挙したかどうか<xref:System.Windows.Controls.Button>コントロール、下図のビジュアル オブジェクトの階層に見つかります。  
  
 ![ビジュアル ツリー階層のダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview03.gif "VisualLayerOverview03")  
ビジュアル ツリー階層のダイアグラム  
  
 <xref:System.Windows.Controls.Button>コントロールに含まれる、<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>要素が、含まれています、<xref:System.Windows.Controls.ContentPresenter>要素。 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>要素は、罫線および背景を描画するため、<xref:System.Windows.Controls.Button>です。 <xref:System.Windows.Controls.ContentPresenter>の内容を表示するため、要素は、<xref:System.Windows.Controls.Button>です。 テキストを表示するためここでは、<xref:System.Windows.Controls.ContentPresenter>要素が含まれています、<xref:System.Windows.Controls.TextBlock>要素。 ファクトを<xref:System.Windows.Controls.Button>コントロール、<xref:System.Windows.Controls.ContentPresenter>など、他の要素で、コンテンツを表すことが意味、<xref:System.Windows.Controls.Image>またはジオメトリなど、<xref:System.Windows.Media.EllipseGeometry>です。  
  
### <a name="control-templates"></a>コントロール テンプレート  
 コントロールのコントロールの階層に拡張するキーは、<xref:System.Windows.Controls.ControlTemplate>です。 コントロール テンプレートは、コントロールの既定のビジュアル階層を指定します。 コントロールを明示的に参照すると、コントロールのビジュアル階層が暗黙的に参照されます。 コントロール テンプレートの既定値をオーバーライドして、コントロールの外観をカスタマイズすることもできます。 背景色の値を変更するなど、<xref:System.Windows.Controls.Button>純色の値ではなく線形グラデーションの色値が使用できるようにします。 詳しくは、「[ボタンのスタイルとテンプレート](../../../../docs/framework/wpf/controls/button-styles-and-templates.md)」をご覧ください。  
  
 ユーザー インターフェイス要素のような<xref:System.Windows.Controls.Button>コントロールをいくつかのベクトル グラフィックス命令リストを含むコントロールの全体を表示の定義について説明します。 次のコードは、<xref:System.Windows.Controls.Button>マークアップで定義されています。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 ビジュアル オブジェクトを列挙するグラフィックスおよびベクター グラフィックス命令のリストを構成する場合、<xref:System.Windows.Controls.Button>コントロール、下図のオブジェクトの階層に見つかります。  
  
 ![ビジュアル ツリーおよび描画データのダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview04.png "VisualLayerOverview04")  
ビジュアル ツリーおよび描画データのダイアグラム  
  
 <xref:System.Windows.Controls.Button>コントロールに含まれる、<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>要素が、含まれています、<xref:System.Windows.Controls.ContentPresenter>要素。 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>要素は、境界線とボタンの背景を構成する、独立したすべてのグラフィック要素を描画するために行います。 <xref:System.Windows.Controls.ContentPresenter>の内容を表示するため、要素は、<xref:System.Windows.Controls.Button>です。 イメージを表示するためここでは、<xref:System.Windows.Controls.ContentPresenter>要素が含まれています、<xref:System.Windows.Controls.Image>要素。  
  
 ビジュアル オブジェクトとベクター グラフィックス命令リストの階層については、次の点に注意する必要があります。  
  
-   階層内の順序は、描画情報のレンダリング順序を表します。 子要素は、ルート ビジュアル要素を起点として、左から右、上から下に走査されます。 要素に子ビジュアル要素がある場合、子ビジュアル要素は要素の兄弟よりも先に走査されます。  
  
-   階層では、非リーフ ノード要素など<xref:System.Windows.Controls.ContentPresenter>、子要素を格納するために使用: 命令の一覧が含まれていません。  
  
-   ビジュアル要素にベクター グラフィックス命令リストとビジュアル子の両方が含まれている場合は、ビジュアル子オブジェクトが描画される前に、親ビジュアル要素の命令リストがレンダリングされます。  
  
-   ベクター グラフィックス命令リスト内の項目は、左から右の順にレンダリングされます。  
  
<a name="visual_tree"></a>   
## <a name="visual-tree"></a>ビジュアル ツリー  
 ビジュアル ツリーには、アプリケーションのユーザー インターフェイスで使用されるすべてのビジュアル要素が含まれます。 ビジュアル要素には永続化された描画情報が含まれているので、ビジュアル ツリーは、ディスプレイ デバイスへの出力を構成するのに必要なレンダリング情報をすべて含んだ、シーン グラフであると考えることができます。 このツリーは、コードかマークアップかを問わず、アプリケーションで直接作成されたすべてのビジュアル要素を累積したものです。 ビジュアル ツリーには、コントロールやデータ オブジェクトなど、要素のテンプレート拡張によって作成されたビジュアル要素もすべて含まれます。  
  
 次のコードは、<xref:System.Windows.Controls.StackPanel>マークアップで定義します。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 構成するビジュアル オブジェクトを列挙したかどうか、<xref:System.Windows.Controls.StackPanel>例では、マークアップ内の要素、下図のビジュアル オブジェクトの階層に見つかります。  
  
 ![ビジュアル ツリー階層のダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview05.gif "VisualLayerOverview05")  
ビジュアル ツリー階層のダイアグラム  
  
### <a name="rendering-order"></a>レンダリング順序  
 ビジュアル ツリーは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のビジュアル オブジェクトと描画オブジェクトの表示順序を決定します。 走査の順序は、ビジュアル ツリーの最上位ノードであるルート ビジュアルから始まります。 次に、ルート ビジュアルの子が左から右に走査されます。 ビジュアルの子が存在する場合、子はビジュアルの兄弟よりも先に走査されます。 つまり、子ビジュアルの内容は、そのビジュアル自体の内容よりも前面に表示されます。  
  
 ![ビジュアル ツリー描画順序のダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview06.gif "VisualLayerOverview06")  
ビジュアル ツリー描画順序のダイアグラム  
  
### <a name="root-visual"></a>ルート ビジュアル  
 **ルート ビジュアル**は、ビジュアル ツリー階層内の最上位の要素です。 ルート visual の基本クラスでは、ほとんどのアプリケーションではいずれかの<xref:System.Windows.Window>または<xref:System.Windows.Navigation.NavigationWindow>です。 ただし、ビジュアル オブジェクトを Win32 アプリケーションでホストする場合は、Win32 ウィンドウにホストする最上位のビジュアルがルート ビジュアルになります。 詳しくは、「[チュートリアル: Win32 アプリケーションでのビジュアル オブジェクトのホスト](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)」をご覧ください。  
  
### <a name="relationship-to-the-logical-tree"></a>論理ツリーとの関係  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の論理ツリーは、実行時のアプリケーションの要素を表します。 このツリーを直接操作することはありませんが、アプリケーションのこのビューは、プロパティの継承やイベントのルーティングを理解する上で役立ちます。 ビジュアル ツリーとは異なり、論理ツリーは、非ビジュアルのデータ オブジェクトなど<xref:System.Windows.Documents.ListItem>です。 多くの場合、論理ツリーはアプリケーションのマークアップ定義にほぼ一致します。 次のコードは、<xref:System.Windows.Controls.DockPanel>マークアップで定義します。  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 構成する論理オブジェクトを列挙したかどうか、<xref:System.Windows.Controls.DockPanel>要素マークアップの例では、次に示すよう論理オブジェクトの階層に見つかります。  
  
 ![ツリー ダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/tree1-wcp.gif "Tree1_wcp")  
論理ツリーのダイアグラム  
  
 ビジュアル ツリーと論理ツリーはどちらも、現在のアプリケーション要素セットと同期し、要素の追加、削除、または変更をすべて反映します。 ただし、これらのツリーが表すアプリケーションのビューはそれぞれ異なるものです。 ビジュアル ツリーとは異なり、論理ツリーでは、コントロールの<xref:System.Windows.Controls.ContentPresenter>要素。 つまり、同じオブジェクト セットについて見ても、論理ツリーとビジュアルツリーの間に 1 対 1 の対応関係はありません。 実際には、呼び出し、 **LogicalTreeHelper**オブジェクトの<xref:System.Windows.LogicalTreeHelper.GetChildren%2A>メソッドおよび**VisualTreeHelper**オブジェクトの<xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>結果の違いをパラメーターとして、同じ要素を使用してメソッド.  
  
 論理ツリーについて詳しくは、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」をご覧ください。  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>XamlPad を使用したビジュアル ツリーの表示  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ツールである XamlPad は、現在定義されている [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] コンテンツに対応するビジュアル ツリーを表示、探索するために使用できます。 ビジュアル ツリーを表示するには、メニュー バーの **[Show Visual Tree]** (ビジュアル ツリーを表示) ボタンをクリックします。 次の図は、XamlPad の **[Visual Tree Explorer]** (ビジュアル ツリー エクスプローラー) パネルに表示されたビジュアル ツリー ノードで、[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] コンテンツを展開した様子を示したものです。  
  
 ![XamlPad のビジュアル ツリー エクスプ ローラー パネル](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview08.png "VisualLayerOverview08")  
XamlPad のビジュアル ツリー エクスプローラー パネル  
  
 通知方法、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.TextBox>、および<xref:System.Windows.Controls.Button>各コントロールが別のビジュアル オブジェクトの階層を表示、**ビジュアル ツリー エクスプ ローラー** XamlPad のパネルです。 これは、ため[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールがある、<xref:System.Windows.Controls.ControlTemplate>そのコントロールのビジュアル ツリーを格納しています。 コントロールを明示的に参照すると、コントロールのビジュアル階層が暗黙的に参照されます。  
  
### <a name="profiling-visual-performance"></a>ビジュアル パフォーマンスのプロファイリング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] にはパフォーマンス プロファイリング ツールのセットがあります。アプリケーションの実行時動作を分析したり、適用できるパフォーマンス最適化の種類を決定したりできます。 Visual Profiler ツールでは、パフォーマンス データをアプリケーションのビジュアル ツリーに直接マップすることにより、それらのデータを多彩なグラフィカル ビューで表示できます。 このスクリーンショットでは、Visual Profiler の **[CPU 使用率]** セクションに、オブジェクトの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サービスの使用率が詳しく表示されています (レンダリングやレイアウトなど)。  
  
 ![Visual Profiler 表示出力](../../../../docs/framework/wpf/graphics-multimedia/media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Visual Profiler 表示出力  
  
<a name="visual_rendering_behavior"></a>   
## <a name="visual-rendering-behavior"></a>ビジュアル レンダリング動作  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ビジュアル オブジェクトのレンダリング動作に影響を及ぼす機能が導入されています。保持モード グラフィックス、ベクター グラフィックス、およびデバイス非依存グラフィックスです。  
  
### <a name="retained-mode-graphics"></a>保持モード グラフィックス  
 ビジュアル オブジェクトの役割を理解するためには、**イミディエイト モード**のグラフィックス システムと**保持モード**のグラフィックス システムの違いについて理解することが重要です。 GDI または GDI+ に基づく標準的な Win32 アプリケーションでは、イミディエイト モードのグラフィックス システムが使用されます。 これは、ウィンドウのサイズ変更やオブジェクトの外観変更などといったアクションによって無効化されたクライアント領域の部分を、アプリケーションが再描画するということを意味します。  
  
 ![Win32 レンダリング シーケンスのダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview01.png "VisualLayerOverview01")  
Win32 レンダリング シーケンスのダイアグラム  
  
 これに対し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、保持モード システムが使用されます。 これは、外観を持つアプリケーション オブジェクト側で、シリアル化された一連の描画データが定義されるということを意味します。 描画データが定義された後は、アプリケーション オブジェクトをレンダリングするためのすべての再描画要求に、システム側が対応します。 実行時であっても、アプリケーション オブジェクトを変更したり作成した場合の描画要求への対応は、システムに任せることができます。 保持モードのグラフィックス システムでは、描画情報が常にシリアル化された状態でアプリケーションに保持されますが、レンダリングはシステムによって実行されます。これが、保持モードのグラフィックス システムの長所です。 次の図は、アプリケーションでの描画要求が [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって処理される様子を示したものです。  
  
 ![WPF レンダリング シーケンスのダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/visuallayeroverview02.png "VisualLayerOverview02")  
WPF レンダリング シーケンスのダイアグラム  
  
#### <a name="intelligent-redrawing"></a>インテリジェントな再描画  
 保持モード グラフィックスを使用することの最も大きな利点の 1 つは、アプリケーション内のどの項目を再描画するのかを、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が効率的に最適化できることです。 さまざまな不透明度が適用された複雑なシーンがある場合でも、通常、再描画を最適化するために特殊な目的のコードを記述する必要はありません。 これに対し、Win32 プログラミングでは、更新領域内の再描画量を最小化してアプリケーションを最適化するために、多大な労力が費やされることもあります。 Win32 アプリケーションで再描画を最適化するための複雑な作業の例については、「[Redrawing in the Update Region](https://msdn.microsoft.com/library/dd162909.aspx)」(更新領域での再描画) をご覧ください。  
  
### <a name="vector-graphics"></a>ベクター グラフィックス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、がレンダリング データ形式として**ベクタ グラフィックス**が使用されます。 スケーラブル ベクター グラフィックス (SVG)、Windows メタファイル (.wmf)、TrueType フォントなどのベクター グラフィックスは、レンダリング データを格納し、それを命令リストとして伝達します。命令リストには、グラフィックス プリミティブを使用してイメージを再作成するための方法が記述されます。 たとえば、TrueType フォントは、ピクセル配列ではなく、直線、曲線、およびコマンドのセットで表されるアウトライン フォントです。 ベクター グラフィックスの主な利点の 1 つは、任意のサイズや解像度に拡大縮小できることです。  
  
 ビットマップ グラフィックスは、ベクター グラフィックスとは異なり、特定の解像度で事前にレンダリングされた、ピクセル単位のイメージ表現としてレンダリング データを格納します。 ビットマップ グラフィックス形式とベクター グラフィックス形式の主な違いの 1 つは、元のソース イメージへの忠実性です。 たとえば、ソース イメージのサイズを変更した場合、ビットマップ グラフィックス システムではイメージが伸縮されますが、ベクタ グラフィックス システムでは、イメージが拡大縮小されるため、イメージの忠実性が維持されます。  
  
 次の図は、ソース イメージが 300% に拡大された場合の例です。 ソース イメージをビットマップ グラフィックス イメージとして拡大したイメージには、ゆがみが生じています。ベクター グラフィックス イメージとして拡大縮小した場合、こうしたゆがみは生じません。  
  
 ![ラスターおよびベクター グラフィックスの違い](../../../../docs/framework/wpf/graphics-multimedia/media/vectorgraphics01.png "VectorGraphics01")  
ラスター グラフィックスとベクター グラフィックスの違い  
  
 次のマークアップを示しています 2<xref:System.Windows.Shapes.Path>定義されている要素です。 2 番目の要素を使用して、 <xref:System.Windows.Media.ScaleTransform> 300% して最初の要素の描画の命令のサイズを変更します。 注意して図面の指示、<xref:System.Windows.Shapes.Path>要素は変更されません。  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>解像度とデバイス非依存グラフィックスについて  
 画面上のテキストやグラフィックスのサイズを決定するシステム要素は、2 つあります。解像度と DPI です。 解像度は、画面に表示されるピクセルの数を表します。 解像度が高くなると、ピクセルが小さくなり、グラフィックスとテキストがより滑らかに表示されます。 モニターの解像度が 1024 x 768 に設定されている場合、解像度を 1600 x 1200 に変更すると、表示されるグラフィックスがより小さくなります。  
  
 もう 1 つのシステム設定である DPI は、画面上の 1 インチのサイズをピクセル単位で表したものです。 ほとんどの [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] システムは 96 DPI であり、これは、画面上の 1 インチが 96 ピクセルであることを意味します。 DPI の設定を上げると、画面上の 1 インチが長くなり、設定を下げると、画面上の 1 インチが短くなります。 そのため、ほとんどのシステムでは、画面上の 1 インチと実際の 1 インチが同じサイズにはなりません。 DPI を大きくすると、画面上の 1 インチのサイズが大きくなるため、DPI 対応のグラフィックスとテキストは大きくなります。 DPI を大きくすると、特に高解像度の場合にはテキストが読みやすくなります。  
  
 ただし、すべてのアプリケーションが DPI に対応しているわけではありません。一部のアプリケーションでは、主要な測定単位としてハードウェア ピクセルが使用されているため、システム DPI を変更しても影響がありません。 また、フォント サイズに DPI 対応の単位を使用している場合でも、それ以外の項目にはすべてピクセルを使用するアプリケーションが数多く存在します。 これらのアプリケーションで DPI を過度に小さくしたり、大きくしたりした場合、アプリケーションのテキストはシステムの DPI 設定に従って拡大縮小されますが、アプリケーションの UI は拡大縮小されないため、レイアウトの問題が発生する可能性があります。 この問題は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用して開発されたアプリケーションでは発生しません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、ハードウェア ピクセルの代わりに、デバイス非依存のピクセルを主要測定単位として用いた、自動拡大縮小機能がサポートされています。つまり、アプリケーション開発者が手を加えなくても、グラフィックスとテキストが適切に拡大縮小されます。 次の図は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のテキストとグラフィックスが、さまざまな DPI でどのように表示されるかを示したものです。  
  
 ![異なる DPI 設定のグラフィックスとテキスト](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
異なる DPI 設定のグラフィックスとテキスト  
  
<a name="visualtreehelper_class"></a>   
## <a name="visualtreehelper-class"></a>VisualTreeHelper クラス  
 <xref:System.Windows.Media.VisualTreeHelper>クラスは、visual オブジェクト レベル、高性能なカスタム コントロールの開発など、非常に特定のシナリオで役に立ちますはプログラミングの低レベルの機能を提供する静的ヘルパー クラス。 ほとんどの場合、高レベル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]framework などのオブジェクト、<xref:System.Windows.Controls.Canvas>と<xref:System.Windows.Controls.TextBlock>柔軟性と使いやすさを提供します。  
  
### <a name="hit-testing"></a>ヒット テスト  
 <xref:System.Windows.Media.VisualTreeHelper>ヒット既定値は、テストのサポートをヒットしたときに、ビジュアル オブジェクトに対するテストがニーズを満たしていないために、クラスがメソッドを提供します。 使用することができます、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>内のメソッド、 <xref:System.Windows.Media.VisualTreeHelper> geometry 型またはポイント座標の値がコントロールのグラフィック要素など、特定のオブジェクトの境界内にあるかどうかを決めるクラスをします。 たとえば、ヒット テストを使用して、オブジェクトの四角形領域内でのマウス クリックが円のジオメトリ内にあるかどうかを確認することもできます。また、ヒット テストの既定の実装をオーバーライドして、独自のカスタム ヒット テスト計算を実行することもできます。  
  
 ヒット テストについて詳しくは、「[ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)」をご覧ください。  
  
### <a name="enumerating-the-visual-tree"></a>ビジュアル ツリーを列挙する  
 <xref:System.Windows.Media.VisualTreeHelper>クラスのビジュアル ツリーのメンバーを列挙するための機能を提供します。 親を取得する、<xref:System.Windows.Media.VisualTreeHelper.GetParent%2A>メソッドです。 子、または、ビジュアル オブジェクトの直系の子孫を取得する、<xref:System.Windows.Media.VisualTreeHelper.GetChild%2A>メソッドです。 このメソッドは、子を返します<xref:System.Windows.Media.Visual>指定したインデックス位置の親です。  
  
 次の例に示すのは、ビジュアル オブジェクトのすべての子孫を列挙する方法です。これは、ビジュアル オブジェクト階層のすべての描画情報をシリアル化する必要がある場合に使用できる手法です。  
  
 [!code-csharp[VisualsOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 ほとんどの場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの要素を表すのには、論理ツリーの方が役立ちます。 論理ツリーを直接変更することはありませんが、アプリケーションのこのビューは、プロパティの継承やイベントのルーティングを理解する上で役立ちます。 ビジュアル ツリーとは異なり、論理ツリーは、非ビジュアルのデータ オブジェクトなど<xref:System.Windows.Documents.ListItem>です。 論理ツリーについて詳しくは、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」をご覧ください。  
  
 <xref:System.Windows.Media.VisualTreeHelper>クラスはビジュアル オブジェクトの外接する四角形を返すためのメソッドを提供します。 呼び出すことによってビジュアル オブジェクトの外接する四角形を返すことができます<xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>です。 呼び出して visual オブジェクト自体を含め、ビジュアル オブジェクトのすべての子孫の外接する四角形を返すことができます<xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>です。 次のコードは、ビジュアル オブジェクトとそのすべての子孫の四角形領域を計算する方法を示したものです。  
  
 [!code-csharp[VisualsOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 <xref:System.Windows.Media.DrawingVisual>  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [ビジュアル層でのヒット テスト](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [チュートリアル : Win32 アプリケーションでのビジュアル オブジェクトのホスト](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
