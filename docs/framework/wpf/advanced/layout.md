---
title: "レイアウト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントロール [WPF], レイアウト システム"
  - "レイアウト システム [WPF]"
  - "WPF レイアウト システム"
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# レイアウト
ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のレイアウト システムについて説明します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でユーザー インターフェイスを作成するには、レイアウトの計算が行われる方法とタイミングを理解することが重要です。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [要素の境界ボックス](#LayoutSystem_BoundingBox)  
  
-   [レイアウト システム](#LayoutSystem_Overview)  
  
-   [子のサイズ測定と配置](#LayoutSystem_Measure_Arrange)  
  
-   [パネル要素とカスタム レイアウトの動作](#LayoutSystem_PanelsCustom)  
  
-   [レイアウト パフォーマンスに関する留意事項](#LayoutSystem_Performance)  
  
-   [サブピクセル レンダリングとレイアウトの丸め](#LayoutSystem_LayoutRounding)  
  
-   [次の内容](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## 要素の境界ボックス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのレイアウトについて考えるときは、すべての要素を囲む境界ボックスを理解することが重要です。  レイアウト システムで処理される各 <xref:System.Windows.FrameworkElement> は、レイアウトに組み込まれる四角形として考えることができます。  要素のレイアウト割り当て \(スロット\) の境界を返す <xref:System.Windows.Controls.Primitives.LayoutInformation> クラスが公開されています。  四角形のサイズは、使用可能な画面スペース、制約のサイズ、余白やパディングなどのレイアウト固有のプロパティ、および親 <xref:System.Windows.Controls.Panel> 要素の個々の動作を計算して決定されます。  このデータを処理して、レイアウト システムは特定の <xref:System.Windows.Controls.Panel> のすべての子の位置を計算できます。  親要素で定義されたサイズ設定特性 \(<xref:System.Windows.Controls.Border> など\) は、その子に影響するという点に注意することが重要です。  
  
 次の図は、単純な配置を表しています。  
  
 ![一般的なグリッド、重ね合わせる境界ボックスなし。](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 このレイアウトは、次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して実現できます。  
  
 [!code-xml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 1 つの <xref:System.Windows.Controls.TextBlock> 要素が <xref:System.Windows.Controls.Grid> 内にホストされています。  テキストは配置先の列の左上隅だけを占めていますが、実際にはそれよりもかなり大きいスペースが <xref:System.Windows.Controls.TextBlock> に割り当てられています。  <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> メソッドを使用して、任意の <xref:System.Windows.FrameworkElement> の境界ボックスを取得できます。  次の図は、<xref:System.Windows.Controls.TextBlock> 要素の境界ボックスを示しています。  
  
 ![TextBlock の境界ボックスが表示されます。](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 黄色い四角形で示すように、<xref:System.Windows.Controls.TextBlock> 要素には、実際には外観よりかなり大きいスペースが割り当てられています。  <xref:System.Windows.Controls.Grid> に要素が追加されると、この割り当ては、追加された要素の型やサイズに応じて縮小または拡張されます。  
  
 <xref:System.Windows.Controls.TextBlock> のレイアウト スロットは、<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> メソッドを使用して、<xref:System.Windows.Shapes.Path> に変換されます。  この方法は、要素の境界ボックスを表示する場合に便利です。  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## レイアウト システム  
 簡単に言うと、レイアウトは、要素のサイズ測定、配置、および描画を繰り返す再帰的なシステムです。  具体的には、レイアウトとは、<xref:System.Windows.Controls.Panel> 要素の <xref:System.Windows.Controls.Panel.Children%2A> コレクションのメンバーを測定し位置を決定するプロセスを表します。  レイアウトは、負荷の高いプロセスです。  <xref:System.Windows.Controls.Panel.Children%2A> コレクションが大きくなるにつれ、実行が必要な計算の数も多くなります。  コレクションを所有する <xref:System.Windows.Controls.Panel> 要素で定義されるレイアウト動作のために、複雑になる場合もあります。  <xref:System.Windows.Controls.Canvas> などの比較的単純な <xref:System.Windows.Controls.Panel> では、<xref:System.Windows.Controls.Grid> などのより複雑な <xref:System.Windows.Controls.Panel> に比べて、大幅に優れたパフォーマンスを実現できます。  
  
 子 <xref:System.Windows.UIElement> の位置が変更されるたびに、レイアウト システムによって新しいパスがトリガーされる可能性があります。  したがって、不要な呼び出しによってアプリケーションのパフォーマンスが低下する可能性があるので、レイアウト システムを呼び出す可能性があるイベントを理解しておくことが重要です。  次に示すのは、レイアウト システムが呼び出されたときに発生するプロセスです。  
  
1.  子 <xref:System.Windows.UIElement> は、最初にそのコア プロパティを測定して、レイアウト プロセスを開始します。  
  
2.  <xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> など、<xref:System.Windows.FrameworkElement> で定義されるサイズ設定プロパティが評価されます。  
  
3.  <xref:System.Windows.Controls.Dock> 方向やスタック <xref:System.Windows.Controls.StackPanel.Orientation%2A> など、<xref:System.Windows.Controls.Panel> 固有のロジックが適用されます。  
  
4.  すべての子が測定された後、コンテンツが配置されます。  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> コレクションが画面に描画されます。  
  
6.  <xref:System.Windows.Controls.Panel.Children%2A> がコレクションに追加された場合、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> が適用された場合、または <xref:System.Windows.UIElement.UpdateLayout%2A> メソッドが呼び出された場合は、プロセスが再度呼び出されます。  
  
 このプロセス、およびプロセスが呼び出される方法については、以降のセクションで詳しく定義します。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## 子のサイズ測定と配置  
 レイアウト システムは、<xref:System.Windows.Controls.Panel.Children%2A> コレクションのメンバーごとに、測定パスと配置パスという 2 つのパスを実行します。  各子 <xref:System.Windows.Controls.Panel> では、それぞれ固有のレイアウト動作を実現するために、独自の <xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドと <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドが用意されています。  
  
 測定パスの実行中に、<xref:System.Windows.Controls.Panel.Children%2A> コレクションの各メンバーが評価されます。  このプロセスは、<xref:System.Windows.UIElement.Measure%2A> メソッドの呼び出しで開始されます。  このメソッドは、親 <xref:System.Windows.Controls.Panel> 要素の実装内で呼び出され、レイアウトを実行するために明示的に呼び出す必要はありません。  
  
 最初に、<xref:System.Windows.UIElement.Clip%2A>、<xref:System.Windows.UIElement.Visibility%2A> などの <xref:System.Windows.UIElement> のネイティブ サイズ プロパティが評価されます。  これにより、<xref:System.Windows.FrameworkElement.MeasureCore%2A> に渡される `constraintSize` という値が生成されます。  
  
 次に、<xref:System.Windows.FrameworkElement> で定義されたフレームワーク プロパティが処理され、`constraintSize` の値に反映されます。  これらのプロパティは、一般に、<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.FrameworkElement.Style%2A> など、基になる <xref:System.Windows.UIElement> のサイズ特性を表しています。  これらの各プロパティにより、要素の表示に必要な領域が変更されることがあります。  続いて、<xref:System.Windows.FrameworkElement.MeasureOverride%2A> が `constraintSize` と共にパラメーターとして呼び出されます。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkElement.Height%2A> および <xref:System.Windows.FrameworkElement.Width%2A> と <xref:System.Windows.FrameworkElement.ActualHeight%2A> および <xref:System.Windows.FrameworkElement.ActualWidth%2A> の各プロパティには違いがあります。  たとえば、<xref:System.Windows.FrameworkElement.ActualHeight%2A> プロパティは、他の高さの入力やレイアウト システムを基に計算された値です。  この値は、実際の描画パスに基づいて、レイアウト システム自体によって設定されるため、入力変更の基準となる <xref:System.Windows.FrameworkElement.Height%2A> などのプロパティの設定値よりも少し遅れることがあります。  
>   
>  <xref:System.Windows.FrameworkElement.ActualHeight%2A> は計算値であるため、レイアウト システムによるさまざまな操作の結果として、複数または追加の変更がレポートされる可能性があることに注意してください。  子要素、親要素による制約などに必要な測度空間をレイアウト システムが計算している場合があります。  
  
 測定パスの最終的な目標は、子の <xref:System.Windows.UIElement.DesiredSize%2A> が決定されることです。これは、<xref:System.Windows.FrameworkElement.MeasureCore%2A> の呼び出し時に行われます。  この <xref:System.Windows.UIElement.DesiredSize%2A> 値は、<xref:System.Windows.UIElement.Measure%2A> に格納され、コンテンツの配置パスで使用されます。  
  
 配置パスは、<xref:System.Windows.UIElement.Arrange%2A> メソッドの呼び出しで開始されます。  配置パスでは、親 <xref:System.Windows.Controls.Panel> 要素から、子の境界を表す四角形が生成されます。  この値は、<xref:System.Windows.FrameworkElement.ArrangeCore%2A> メソッドに渡されて処理されます。  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> メソッドは子の <xref:System.Windows.UIElement.DesiredSize%2A> を評価し、その要素の表示サイズに影響を与える余白が他にあるかどうかを評価します。  <xref:System.Windows.FrameworkElement.ArrangeCore%2A> が `arrangeSize` を生成し、<xref:System.Windows.Controls.Panel> の <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドにパラメーターとして渡されます。  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> が子の `finalSize` を生成します。  最後に、<xref:System.Windows.FrameworkElement.ArrangeCore%2A> メソッドが余白や配置などのオフセット プロパティの最終的な評価を行い、レイアウト スロット内に子を配置します。  子は、割り当てられた領域全体を占める必要はなく、実際に、全体を占めないことも珍しくありません。  次に、制御が親 <xref:System.Windows.Controls.Panel> に戻されて、レイアウト プロセスが完了します。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## パネル要素とカスタム レイアウトの動作  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、<xref:System.Windows.Controls.Panel> から派生した要素のグループが含まれています。  これらの <xref:System.Windows.Controls.Panel> 要素により、多くの複雑なレイアウトができます。  たとえば、要素のスタックは <xref:System.Windows.Controls.StackPanel> 要素を使用して簡単に実現できますが、<xref:System.Windows.Controls.Canvas> を使用すると、より複雑で流動性の高いレイアウトを実現できます。  
  
 次の表に、使用可能なレイアウトの <xref:System.Windows.Controls.Panel> 要素をまとめています。  
  
|パネル名|Description|  
|----------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|<xref:System.Windows.Controls.Canvas> 領域に対する座標により子要素を明示的に配置できる領域を定義します。|  
|<xref:System.Windows.Controls.DockPanel>|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|列と行で構成される柔軟なグリッド領域を定義します。|  
|<xref:System.Windows.Controls.StackPanel>|単一行に子要素を整列します。行は水平方向または垂直方向にできます。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|子データ コレクションを仮想化する <xref:System.Windows.Controls.Panel> 要素のフレームワークを提供します。  これは抽象クラスです。|  
|<xref:System.Windows.Controls.WrapPanel>|左から右へ順に子要素を配置し、ボックスの端で改行してコンテンツを次の行に送ります。  後続の配置は、<xref:System.Windows.Controls.WrapPanel.Orientation%2A> プロパティの値に応じて、上から下または右から左に向かって行われます。|  
  
 アプリケーションで必要なレイアウトが、定義されたどの <xref:System.Windows.Controls.Panel> 要素を使用しても実現できない場合は、<xref:System.Windows.Controls.Panel> からの継承と、<xref:System.Windows.FrameworkElement.MeasureOverride%2A> メソッドおよび <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> メソッドのオーバーライドにより、カスタムのレイアウト動作を実現できます。  例については、[カスタム放射状パネルのサンプル](http://go.microsoft.com/fwlink/?LinkID=159982)を参照してください。  
  
<a name="LayoutSystem_Performance"></a>   
## レイアウト パフォーマンスに関する留意事項  
 レイアウトは、再帰プロセスです。  <xref:System.Windows.Controls.Panel.Children%2A> コレクション内の各子要素は、レイアウト システムの各呼び出しによって処理されます。  そのため、レイアウト システムのトリガーは、できるだけ避ける必要があります。  次に示す考慮事項は、より優れたパフォーマンスを実現するうえで役に立ちます。  
  
-   プロパティ値をどのように変更するとレイアウト システムの再帰的な更新が実行されるかに注意します。  
  
     依存関係プロパティの値によってレイアウト システムが初期化される可能性がある場合、そのプロパティはパブリック フラグでマークされます。  <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> および <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> は、どのプロパティ値の変更によってレイアウト システムの再帰的な更新が実行されるかを判断する手掛かりになります。  一般的に、要素の境界ボックスのサイズに影響を与える可能性があるプロパティでは、<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> フラグが true に設定されている必要があります。  詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
-   可能な場合は、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> の代わりに <xref:System.Windows.UIElement.RenderTransform%2A> を使用します。  
  
     <xref:System.Windows.FrameworkElement.LayoutTransform%2A> は、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] のコンテンツに影響を与えるための非常に便利な手段です。  ただし、変換の結果を他の要素の配置に影響させる必要がない場合は、代わりに <xref:System.Windows.UIElement.RenderTransform%2A> を使用することをお勧めします。<xref:System.Windows.UIElement.RenderTransform%2A> はレイアウト システムを呼び出さないためです。  <xref:System.Windows.FrameworkElement.LayoutTransform%2A> はその変換を適用し、再帰的なレイアウトの更新を強制的に実行して、影響を受ける要素の新しい配置に反映させます。  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> の不要な呼び出しは避けてください。  
  
     この <xref:System.Windows.UIElement.UpdateLayout%2A> メソッドは、再帰的なレイアウトの更新を強制的に実行しますが、多くの場合は必要ありません。  全面的な更新が必要でない限り、このメソッドの呼び出しはレイアウト システムに任せてください。  
  
-   大きい <xref:System.Windows.Controls.Panel.Children%2A> コレクションで作業する場合は、通常の <xref:System.Windows.Controls.StackPanel> の代わりに、<xref:System.Windows.Controls.VirtualizingStackPanel> の使用をお勧めします。  
  
     子コレクションを仮想化することで、<xref:System.Windows.Controls.VirtualizingStackPanel> は、現在、親の [ViewPort](GTMT) 内に存在するオブジェクトのみをメモリ内に維持します。  その結果、パフォーマンスは多くのシナリオで大幅に向上します。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## サブピクセル レンダリングとレイアウトの丸め  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のグラフィックス システムでは、解像度およびデバイスに依存しないようにするために、デバイスに依存しない単位が使用されます。  デバイスに依存しない各ピクセルは、システムの [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] 設定に従って自動的にスケーリングされます。  これにより、さまざまな [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 設定で [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションが適切にスケーリングされ、アプリケーションが自動的に [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] に対応するようになります。  
  
 ただし、この [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] に依存しない方法では、アンチエイリアシングによる端の描画にむらが生じる可能性があります。  このような不鮮明な表示 \(半透明のエッジ\) は、端がデバイス ピクセル間ではなく、1 つのデバイス ピクセル内に位置するときに発生する場合があります。  レイアウト システムでは、このような場合の調整方法として、レイアウトの丸めが用意されています。  レイアウトの丸めでは、レイアウト パスの実行中に整数以外のピクセル値が見つかった場合、レイアウト システムによって丸め処理が行われます。  
  
 レイアウトの丸めは既定では無効になっています。  レイアウトの丸めを有効にするには、<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> プロパティを <xref:System.Windows.FrameworkElement> のいずれかで `true` に設定します。  これは依存関係プロパティであるため、値はビジュアル ツリー内のすべての子に反映されます。  UI 全体でレイアウトの丸めを有効にするには、ルート コンテナーで <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> を `true` に設定します。  例については、「<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>」を参照してください。  
  
<a name="LayoutSystem_whatsnext"></a>   
## 次の内容  
 要素の測定および配置方法を理解することが、レイアウトを理解する第一歩です。  使用可能な <xref:System.Windows.Controls.Panel> 要素の詳細については、「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」を参照してください。  レイアウトに影響する可能性がある各配置プロパティをさらに詳しく理解するには、「[配置、余白、パディングの概要](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)」を参照してください。  カスタム <xref:System.Windows.Controls.Panel> 要素の例については、[カスタム放射状パネルのサンプル](http://go.microsoft.com/fwlink/?LinkID=159982)を参照してください。  軽量アプリケーションにすべての要素を取り入れる準備ができている場合は、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.UIElement>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [配置、余白、パディングの概要](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)