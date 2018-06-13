---
title: パネルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 65f5fa9eeffdeb6e7bc869d159b4b33d75fd7570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558240"
---
# <a name="panels-overview"></a>パネルの概要
<xref:System.Windows.Controls.Panel> 要素は要素の描画を制御するコンポーネント、そのサイズとディメンション、それらの位置およびその子コンテンツの配置。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は多数の定義済み<xref:System.Windows.Controls.Panel>要素だけでなくカスタムを作成する機能<xref:System.Windows.Controls.Panel>要素。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [パネル クラス](#Panels_view_from_10000_feet)  
  
-   [パネルの要素の一般的なメンバー](#Panels_declared_members)  
  
-   [派生パネル要素](#Panels_derived_elements)  
  
-   [ユーザー インターフェイス パネル](#Panels_main_UI_elements)  
  
-   [入れ子になったパネル要素](#Panels_nested_panel_elements)  
  
-   [カスタム パネル要素](#Panels_custom_panel_elements)  
  
-   [ローカライズ/グローバリゼーション サポート](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>パネル クラス  
 <xref:System.Windows.Controls.Panel> レイアウトを提供するすべての要素をサポートする基本クラスは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。 派生<xref:System.Windows.Controls.Panel>要素内の要素を配置したりを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]とコード。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、多くの複雑なレイアウトを可能にする派生パネル実装の総合的なスイートが含まれます。 これらの派生クラスは、標準 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] シナリオのほとんどを可能にするプロパティとメソッドを公開します。 開発者は、ニーズを満たす子の並べ替え動作はオーバーライドすることで新しいレイアウトを作成することを見つけることができない、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>と<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドです。 カスタム レイアウト動作の詳細については、「[カスタム パネル要素](#Panels_custom_panel_elements)」を参照してください。  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>パネルの一般的なメンバー  
 すべて<xref:System.Windows.Controls.Panel>要素によって定義されたプロパティを配置してサイズ変更、ベースをサポートする<xref:System.Windows.FrameworkElement>など、 <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、および<xref:System.Windows.FrameworkElement.LayoutTransform%2A>です。 によって定義されたプロパティの配置の詳細については<xref:System.Windows.FrameworkElement>を参照してください[アラインメント、余白、および概要のパディング](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)です。  
  
 <xref:System.Windows.Controls.Panel> 重要な意味を理解すると、レイアウトを使用して、追加のプロパティを公開します。 <xref:System.Windows.Controls.Panel.Background%2A>プロパティを使用してを持つ派生パネル要素の境界間の領域を埋める、<xref:System.Windows.Media.Brush>です。 <xref:System.Windows.Controls.Panel.Children%2A> 要素の子コレクションを表しますを<xref:System.Windows.Controls.Panel>で構成されます。 <xref:System.Windows.Controls.Panel.InternalChildren%2A> 内容を表す、<xref:System.Windows.Controls.Panel.Children%2A>コレクションとデータ バインディングによって生成されたこれらのメンバーです。 どちらも、<xref:System.Windows.Controls.UIElementCollection>親内でホストされている子要素の<xref:System.Windows.Controls.Panel>します。  
  
 パネルの公開も、<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>添付、派生階層化順序を実現するために使用できるプロパティ<xref:System.Windows.Controls.Panel>です。 パネルのメンバー<xref:System.Windows.Controls.Panel.Children%2A>高いを持つコレクション<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>、下の前に値が表示される<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>値。 これは、パネルのように<xref:System.Windows.Controls.Canvas>と<xref:System.Windows.Controls.Grid>これを使用して同じ座標空間を共有する子。  
  
 <xref:System.Windows.Controls.Panel> 定義、<xref:System.Windows.Controls.Panel.OnRender%2A>の既定のプレゼンテーションの動作をオーバーライドするために使用するメソッド、<xref:System.Windows.Controls.Panel>です。  
  
#### <a name="attached-properties"></a>アタッチされるプロパティ  
 派生パネル要素は、添付プロパティを広く活用しています。 添付プロパティは、従来の [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティ "ラッパー" を持たない特殊な形式の依存関係プロパティです。 添付プロパティは、下記の例に見られるとおり、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内に特殊な構文を持ちます。  
  
 添付プロパティの目的の 1 つは、親要素によって実際に定義されたプロパティの一意の値を子要素が格納できるようにすることです。 この機能の応用方法の 1 つは、子要素から親要素に [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] でどのように表示したいかを通知させることであり、これはアプリケーション レイアウトに非常に役立ちます。 詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>派生パネル要素  
 多くのオブジェクトから派生して<xref:System.Windows.Controls.Panel>、ルート レイアウト プロバイダーとして使用するものではそれらのすべてが、します。 6 つのパネルが定義されているクラスがある (<xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、および<xref:System.Windows.Controls.WrapPanel>) アプリケーションの作成専用に設計[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。  
  
 次の表に各パネル要素でカプセル化されているそれぞれの特殊機能を示します。  
  
|要素名|UI パネル?|説明|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|[はい]|内部では、子要素に対する相対座標で明示的に配置できる領域を定義、<xref:System.Windows.Controls.Canvas>領域。|  
|<xref:System.Windows.Controls.DockPanel>|[はい]|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|[はい]|列と行で構成されている柔軟なグリッド領域を定義します。 子要素、<xref:System.Windows.Controls.Grid>を使用して正確に配置することができます、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティです。|  
|<xref:System.Windows.Controls.StackPanel>|[はい]|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|×|内のタブ ボタンのレイアウトを処理する<xref:System.Windows.Controls.TabControl>です。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|×|内のコンテンツを整列、<xref:System.Windows.Controls.ToolBar>コントロール。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|×|<xref:System.Windows.Controls.Primitives.UniformGrid> すべてのセルと同じサイズで、グリッド内の子を配置に使用されます。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|×|子コレクションを "仮想化" できるパネルに基本クラスを提供します。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|[はい]|水平方向または垂直方向の単一行でコンテンツを整列し、仮想化します。|  
|<xref:System.Windows.Controls.WrapPanel>|[はい]|<xref:System.Windows.Controls.WrapPanel> 順番の位置の子要素は左から右、互換性に影響するコンテンツを含むボックスの端にある次の行にします。 後続の処理順番に上から下または右から左の値に応じて、<xref:System.Windows.Controls.WrapPanel.Orientation%2A>プロパティです。|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>ユーザー インターフェイス パネル  
 6 つのパネル クラスでは使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サポートするために最適化されている[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]シナリオ: <xref:System.Windows.Controls.Canvas>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、 <xref:System.Windows.Controls.StackPanel>、 <xref:System.Windows.Controls.VirtualizingStackPanel>、および<xref:System.Windows.Controls.WrapPanel>です。 これらのパネル要素は使いやすく、用途が広く、ほとんどのアプリケーションに対する拡張性があります。  
  
 派生した各<xref:System.Windows.Controls.Panel>要素がサイズ制約を異なる方法で扱われます。 理解する方法、<xref:System.Windows.Controls.Panel>ハンドル制約水平または垂直方向のいずれかで行うことができますレイアウト予測しやすくします。  
  
|**パネル名**|**x 方向**|**y 方向**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.DockPanel>|制約あり。|制約あり。|  
|<xref:System.Windows.Controls.StackPanel> (縦方向)|制約あり。|コンテンツに対する制約あり。|  
|<xref:System.Windows.Controls.StackPanel> (横方向)|コンテンツに対する制約あり。|制約あり。|  
|<xref:System.Windows.Controls.Grid>|制約あり。|場合を除き、制約がある場所<xref:System.Windows.GridUnitType.Auto>行と列に適用|  
|<xref:System.Windows.Controls.WrapPanel>|コンテンツに対する制約あり。|コンテンツに対する制約あり。|  
  
 これらの各要素の詳細な説明と使用例を次に示します。  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Canvas  
 <xref:System.Windows.Controls.Canvas>要素は、絶対に従ってコンテンツを配置できるように*x -* と*y*座標。 要素は一意の場所に描画できます。または、要素が同じ座標を占める場合、マークアップに表示される順序が要素の描画順序を決定します。  
  
 <xref:System.Windows.Controls.Canvas> いずれかの最も柔軟なレイアウトのサポートを提供<xref:System.Windows.Controls.Panel>です。 高さと幅のプロパティを使用して、キャンバスの領域を定義し、内の要素が親の領域と相対的に絶対座標を割り当てられている<xref:System.Windows.Controls.Canvas>です。 アタッチされる 4 つのプロパティ、 <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType>と<xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>、内のオブジェクト配置の詳細に制御する、<xref:System.Windows.Controls.Canvas>開発者は、画面上に正確に要素を配置したりできるようにします。  
  
#### <a name="cliptobounds-within-a-canvas"></a>キャンバス内の ClipToBounds  
 <xref:System.Windows.Controls.Canvas> 子要素を独自に定義された外にある座標であっても、画面の任意の位置に配置できる<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>です。 さらに、<xref:System.Windows.Controls.Canvas>その子のサイズの影響を受けません。 その結果、可能であれば、親の外接する四角形の外側には、その他の要素範囲を超えて描画する子要素の<xref:System.Windows.Controls.Canvas>します。 既定の動作、 <xref:System.Windows.Controls.Canvas> 、子供が親の境界外に描画するのには、<xref:System.Windows.Controls.Canvas>です。 この動作が、望ましくない場合、<xref:System.Windows.UIElement.ClipToBounds%2A>プロパティに設定することができます`true`です。 これにより、<xref:System.Windows.Controls.Canvas>独自のサイズにクリップします。 <xref:System.Windows.Controls.Canvas> 子供の境界外に描画するのには、のみのレイアウト要素です。  
  
 この動作は、[Width のプロパティの比較のサンプル](http://go.microsoft.com/fwlink/?LinkID=160050)に図示されています。  
  
#### <a name="defining-and-using-a-canvas"></a>キャンバスの定義と使用  
 A<xref:System.Windows.Controls.Canvas>を使用するだけでインスタンス化できます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。 次の例を使用する方法を示します<xref:System.Windows.Controls.Canvas>絶対にコンテンツを配置します。 このコードでは、100 ピクセルの四角形を 3 つ生成します。 最初の四角形は赤色で、左上 (*x, y*) の位置が (0, 0) に指定されます。 2 番目の四角形は緑色で、左上の位置は (100, 100) となり、最初の四角形の右下になります。 3 番目の四角形は青色で、左上の位置は (50, 50) となるため、最初の四角形の右下の象限および 2 番目の四角形の左上の象限を囲む状態になります。 3 番目の四角形が最後にレイアウトされるため、他の 2 つの四角形の上に重なっているように見えます。つまり、重複している部分は 3 番目の四角形の色とみなされます。  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なキャンバス要素: ](../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel>要素を使用して、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティをコンテナーの端にコンテンツを配置する子コンテンツの要素で設定します。 ときに<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>に設定されている<xref:System.Windows.Controls.Dock.Top>または<xref:System.Windows.Controls.Dock.Bottom>、子要素の上または他の下に位置します。 ときに<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>に設定されている<xref:System.Windows.Controls.Dock.Left>または<xref:System.Windows.Controls.Dock.Right>、互いの右または左に子要素を配置します。 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>プロパティの子として追加された最後の要素の位置を決定する、<xref:System.Windows.Controls.DockPanel>です。  
  
 使用することができます<xref:System.Windows.Controls.DockPanel>一連のボタンなどの関連するコントロールのグループを配置します。 または、これを使用して、[!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)] に見られるのと同様の "ウィンドウ形式の" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を作成できます。  
  
#### <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 場合、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>プロパティが指定されていない<xref:System.Windows.Controls.DockPanel>そのコンテンツへのサイズ。 サイズは、子要素のサイズに合うように、増減させることができます。 ただし、これらのプロパティが指定され、次の指定した子要素のスペースが不要になった<xref:System.Windows.Controls.DockPanel>その子要素またはそれ以降の子要素は表示されませんし、後続の子要素を測定することはありません。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 既定では、最後の子、<xref:System.Windows.Controls.DockPanel>要素は"fill"残り、未割り当ての領域。 この動作が必要でない場合は、設定、<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>プロパティを`false`です。  
  
#### <a name="defining-and-using-a-dockpanel"></a>DockPanel の定義と使用  
 次の例では、スペースを使用してパーティション分割する方法、<xref:System.Windows.Controls.DockPanel>です。 5 つ<xref:System.Windows.Controls.Border>要素は、親の子として追加<xref:System.Windows.Controls.DockPanel>です。 別の配置プロパティを使用して各、<xref:System.Windows.Controls.DockPanel>パーティション領域にします。 最後の要素が、残っている未割り当て領域の "塗り潰し" を実行します。  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な DockPanel シナリオ: ](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>グリッド  
 <xref:System.Windows.Controls.Grid>要素が絶対位置指定および表形式のデータ コントロールの機能をマージします。 A<xref:System.Windows.Controls.Grid>位置とスタイルの要素を簡単にできます。 <xref:System.Windows.Controls.Grid> 柔軟な行と列グループを定義することができ、でも複数の間でのサイズ変更情報を共有するメカニズムを備えています<xref:System.Windows.Controls.Grid>要素。  
  
#### <a name="how-is-grid-different-from-table"></a>グリッドとテーブルを区別する方法  
 <xref:System.Windows.Documents.Table> および<xref:System.Windows.Controls.Grid>各はさまざまなシナリオに最適なはいくつかの一般的な機能を共有します。 A<xref:System.Windows.Documents.Table>フロー コンテンツ内で使用するために設計されていますが (を参照してください[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)フロー コンテンツの詳細については)。 グリッドは、フォーム内で最適に使用される (基本的に任意の場所以外のフロー コンテンツ)。 内で、 <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Table>サポート フロー コンテンツの動作などの改ページ、列の折り返し、およびコンテンツの選択中に、<xref:System.Windows.Controls.Grid>しません。 A<xref:System.Windows.Controls.Grid>一方は最適以外で使用される、<xref:System.Windows.Documents.FlowDocument>さまざまな理由<xref:System.Windows.Controls.Grid>行と列のインデックスに基づいて要素を追加<xref:System.Windows.Documents.Table>しません。 <xref:System.Windows.Controls.Grid>要素により、1 つの「セル」内に存在する 1 つ以上の要素を許可する子コンテンツの重ね順 <xref:System.Windows.Documents.Table> 重ね順をサポートしていません。 子要素、 <xref:System.Windows.Controls.Grid> 「セル」境界外部の領域と相対的絶対位置に配置できます。 <xref:System.Windows.Documents.Table> この機能はサポートしません。 最後に、<xref:System.Windows.Controls.Grid>より軽量は、<xref:System.Windows.Documents.Table>です。  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>列と行のサイズ変更動作  
 内で定義されている行と列、<xref:System.Windows.Controls.Grid>活用できる<xref:System.Windows.GridUnitType.Star>残りの領域を比例的に配布するためにサイズ変更します。 ときに<xref:System.Windows.GridUnitType.Star>高さまたは幅行または列、列または行に残りの空き領域の加重比率が受信するを選択しています。 これは、対照的に<xref:System.Windows.GridUnitType.Auto>領域の行または列内のコンテンツのサイズに基づいて均等に配布します。 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用する場合、この値は `*` または `2*` と表現されます。 最初のケースでは、行または列は使用可能なスペース領域を 1 回受け取り、2 番目のケースでは 2 回受け取ることになります。 領域を比例的に配布するには、この手法を組み合わせることによって、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>の値`Stretch`画面領域の割合で、パーティション レイアウト領域を行うことができます。 <xref:System.Windows.Controls.Grid> この方法で領域を配布することができますのみのレイアウト パネルです。  
  
#### <a name="defining-and-using-a-grid"></a>グリッドの定義と使用  
 次の例に、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] スタート メニューで使用可能な [ファイル名を指定して実行] ダイアログ ボックスに見られるのと同様の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を構築する方法を示します。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的なグリッド要素: ](../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 A<xref:System.Windows.Controls.StackPanel>すると、指定した方向に要素を「積み重ねる」ことができます。 既定のスタック方向は、縦です。 <xref:System.Windows.Controls.StackPanel.Orientation%2A>コンテンツ フローを制御するプロパティを使用できます。  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel と DockPanel  
 <xref:System.Windows.Controls.DockPanel>できますも「スタック」子要素、<xref:System.Windows.Controls.DockPanel>と<xref:System.Windows.Controls.StackPanel>いくつかの使用シナリオに似ていますの結果が得られない。 たとえば、子要素の順序に影響する可能性、サイズ、<xref:System.Windows.Controls.DockPanel>ではなく、<xref:System.Windows.Controls.StackPanel>です。 これは、ため<xref:System.Windows.Controls.StackPanel>でスタックの方向にメジャー<xref:System.Double.PositiveInfinity>であるのに対し<xref:System.Windows.Controls.DockPanel>のみ利用可能なサイズを測定します。  
  
 この主な相違点を次の例に示します。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 このイメージにはレンダリング動作の違いが見られます。  
  
 ![スクリーン ショット: StackPanel スクリーン ショットとします。DockPanel スクリーン ショット](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>StackPanel の定義と使用  
 次の例で使用する方法、<xref:System.Windows.Controls.StackPanel>垂直方向に配置されているボタンのセットを作成します。 横方向の配置の設定、<xref:System.Windows.Controls.StackPanel.Orientation%2A>プロパティを<xref:System.Windows.Controls.Orientation.Horizontal>です。  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な StackPanel 要素: ](../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] バリエーションも提供、<xref:System.Windows.Controls.StackPanel>自動的に「は、仮想化」のデータ バインドされた子コンテンツ要素。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、要素のサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel> (によって提供される機能を通じて<xref:System.Windows.Controls.VirtualizingPanel>) 表示されている項目を計算し、連携、<xref:System.Windows.Controls.ItemContainerGenerator>から、 <xref:System.Windows.Controls.ItemsControl> (など<xref:System.Windows.Controls.ListBox>または<xref:System.Windows.Controls.ListView>) のみ表示される項目の要素を作成します。  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel>などホスト コントロールのアイテムとして要素が自動的に設定、<xref:System.Windows.Controls.ListBox>です。 バインドのコレクションをデータをホストしているときにコンテンツが自動的に仮想化の境界内にコンテンツがある限り、<xref:System.Windows.Controls.ScrollViewer>です。 これにより、多くの子項目をホストする際のパフォーマンスが大幅に向上します。  
  
 次のマークアップを使用する方法を示しています、<xref:System.Windows.Controls.VirtualizingStackPanel>項目ホストとして。 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>に添付プロパティを設定する必要があります`true`が発生する仮想化のためには、(既定)。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel> 子要素を左から右、次の行、親コンテナーの端に達したときに重大なコンテンツの位置が順次配置に使用されます。 コンテンツは水平方向または垂直方向に設定できます。 <xref:System.Windows.Controls.WrapPanel> 単純なをフローさせるために役立ちます[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]シナリオです。 また、子要素すべてに均等なサイズを適用する際にも使用できます。  
  
 次の例で作成する方法、<xref:System.Windows.Controls.WrapPanel>を表示する<xref:System.Windows.Controls.Button>コンテナーの端に到達したときをラップするコントロール。  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![代表的な WrapPanel 要素: ](../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>入れ子になったパネル要素  
 <xref:System.Windows.Controls.Panel> 要素は、複雑なレイアウトを生成するために互いに入れ子にすることができます。 これは、ことができますの際に役立つ状況 1<xref:System.Windows.Controls.Panel>の一部に最適です、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の他の部分のニーズを満たしていない可能性がありますが、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。  
  
 アプリケーションがサポートできる入れ子の量に決められた制限はありませんが、一般的に、目的のレイアウトに必要なパネルのみを使用するようアプリケーションを制限することをお勧めします。 多くの場合、<xref:System.Windows.Controls.Grid>要素は入れ子になったパネル レイアウト コンテナーとして、柔軟性のための代わりに使用できます。 これにより、ツリーから不要な要素が排除され、アプリケーションのパフォーマンスが向上します。  
  
 次の例で作成する方法、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の利用が入れ子になっている<xref:System.Windows.Controls.Panel>要素を特定のレイアウトを実現するためにします。 この特定のケースで、<xref:System.Windows.Controls.DockPanel>要素を使用して提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]構造、および入れ子になった<xref:System.Windows.Controls.StackPanel>要素、 <xref:System.Windows.Controls.Grid>、および<xref:System.Windows.Controls.Canvas>親に正確に含まれる子要素を配置するために使用<xref:System.Windows.Controls.DockPanel>です。  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 コンパイルされたアプリケーションは、これと同様の新しい [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を生成します。  
  
 ![入れ子になったパネルを利用する UI: ](../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>カスタム パネル要素  
 中に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]柔軟なレイアウト コントロール、カスタム レイアウトの動作をオーバーライドすることによっても実行できますの配列を提供、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>と<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドです。 このオーバーライド メソッド内で新しい配置動作を定義することにより、カスタムのサイズ変更と配置が実行されます。  
  
 同様に、カスタム レイアウトの動作に基づいて派生クラス (など<xref:System.Windows.Controls.Canvas>または<xref:System.Windows.Controls.Grid>) をオーバーライドして定義することができます、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>と<xref:System.Windows.FrameworkElement.MeasureOverride%2A>メソッドです。  
  
 次のマークアップがカスタムを作成する方法を示します<xref:System.Windows.Controls.Panel>要素。 この新しい<xref:System.Windows.Controls.Panel>として定義されている`PlotPanel`、ハード コーディングされたを使用して子要素の位置をサポートしている*x -* と*y*座標。 この例では、 <xref:System.Windows.Shapes.Rectangle> (表示されない) 要素はプロット時点 50 (*x*)、50 (*y*)。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 より複雑なカスタム パネルの実装を確認するには、[カスタム コンテンツ折り返しパネルの作成のサンプル](http://go.microsoft.com/fwlink/?LinkID=159979)を参照してください。  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>ローカライズ/グローバリゼーション サポート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、ローカライズ可能な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の作成を支援する多数の機能をサポートしています。  
  
 パネルのすべての要素をネイティブ サポート、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティを動的に再設定、ユーザーのロケールまたは言語設定に基づいて、コンテンツをフローするために使用できます。 詳細については、「<xref:System.Windows.FrameworkElement.FlowDirection%2A>」を参照してください。  
  
 <xref:System.Windows.Window.SizeToContent%2A>プロパティは、アプリケーション開発者ができるようにするメカニズムを備えています。 ローカライズのニーズを予測する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 使用して、<xref:System.Windows.SizeToContent.WidthAndHeight>親は、このプロパティの値<xref:System.Windows.Window>常にサイズを動的にコンテンツを合わせるし、人為的な高さまたは幅の制限による制約を受けない。  
  
 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid>、および<xref:System.Windows.Controls.StackPanel>のすべての適切な選択肢は、ローカライズ可能な[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 <xref:System.Windows.Controls.Canvas> 適切な選択ではありません、ただし、配置コンテンツ、絶対にローカライズするは困難になります。  
  
 ローカライズ可能な [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] を備えた [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法の詳細については、「[自動レイアウトの使用の概要](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 初めての WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [WPF レイアウト ギャラリー サンプル](http://go.microsoft.com/fwlink/?LinkID=160054)  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
 [WPF Controls Gallery Sample](http://go.microsoft.com/fwlink/?LinkID=160053)  
 [配置、余白、パディングの概要](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [カスタム コンテンツの折り返しパネル サンプルを作成します。](http://go.microsoft.com/fwlink/?LinkID=159979)  
 [添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [自動レイアウトの使用の概要](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
