---
title: "レイアウト"
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
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9a5f33ab22779002e85d7a73b29ae74dac81c26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="layout"></a>レイアウト
このトピックでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] レイアウト システムについて説明します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でユーザー インターフェイスを作成するには、レイアウトの計算が発生するタイミングと方法を理解することが非常に重要です。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [要素の境界ボックス](#LayoutSystem_BoundingBox)  
  
-   [レイアウト システム](#LayoutSystem_Overview)  
  
-   [子の測定と配置](#LayoutSystem_Measure_Arrange)  
  
-   [パネル要素とカスタム レイアウトの動作](#LayoutSystem_PanelsCustom)  
  
-   [レイアウトのパフォーマンスの考慮事項](#LayoutSystem_Performance)  
  
-   [サブピクセル レンダリングとレイアウトの丸め処理](#LayoutSystem_LayoutRounding)  
  
-   [次の内容](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>要素の境界ボックス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でレイアウトについて考えるときは、すべての要素を囲む境界ボックスを理解することが重要です。 各<xref:System.Windows.FrameworkElement>消費レイアウトによってシステムはようなものの四角形レイアウトに挿入されています。 <xref:System.Windows.Controls.Primitives.LayoutInformation>クラスは、要素のレイアウトの割り当て、またはスロットの境界を返します。 四角形のサイズは使用可能な画面スペース、制約、(マージンと埋め込み) などのレイアウトに固有のプロパティと、親の個々 の動作のサイズを計算することによって決まります<xref:System.Windows.Controls.Panel>要素。 このデータを処理するには、レイアウト システムは、特定のすべての子の位置を計算できません<xref:System.Windows.Controls.Panel>です。 などの特性をサイズ変更は、親要素で定義されているかを注意してください、 <xref:System.Windows.Controls.Border>、その子に影響します。  
  
 次の図は、シンプルなレイアウトを示しています。  
  
 ![一般的なグリッド、重ね合わせる境界ボックスなし。](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 このレイアウトは、次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して実現できます。  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 1 つ<xref:System.Windows.Controls.TextBlock>要素が内でホストされている、<xref:System.Windows.Controls.Grid>です。 テキストが最初の列に割り当てられた領域の左上隅のみを入力中に、<xref:System.Windows.Controls.TextBlock>が実際に大きくします。 いずれかの境界ボックス<xref:System.Windows.FrameworkElement>を使用して取得できる、<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>メソッドです。 次の図に、境界ボックス、<xref:System.Windows.Controls.TextBlock>要素。  
  
 ![TextBlock の境界ボックスが表示されます。](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 黄色の四角形に割り当てられた領域に示すように、<xref:System.Windows.Controls.TextBlock>要素は、実際にははるかに上回ることが表示されます。 追加の要素が追加されるにつれて、 <xref:System.Windows.Controls.Grid>、この割り当てを縮小または展開の種類と追加される要素のサイズによって、可能性があります。  
  
 レイアウト スロット、<xref:System.Windows.Controls.TextBlock>に変換される、<xref:System.Windows.Shapes.Path>を使用して、<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>メソッドです。 この方法は、要素の境界ボックスの表示に役立ちます。  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>レイアウト システム  
 簡単に言うと、レイアウトは、要素のサイズ測定、配置、および描画を繰り返す再帰的なシステムです。 具体的にはレイアウトが測定と配置のメンバーのプロセスについて説明します、<xref:System.Windows.Controls.Panel>要素の<xref:System.Windows.Controls.Panel.Children%2A>コレクション。 レイアウトは集中的なプロセスです。 大きいほど、<xref:System.Windows.Controls.Panel.Children%2A>コレクション、行う必要があります計算数は大きくします。 によって定義されたレイアウト動作に基づいて複雑さを導入することも、<xref:System.Windows.Controls.Panel>コレクションを所有する要素。 比較的単純な<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Canvas>より複雑なよりも大幅に優れたパフォーマンスを持つことができます<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Grid>です。  
  
 ごとに子<xref:System.Windows.UIElement>の位置を変更、レイアウト システムによって新しいパスをトリガーする可能性があります。 したがって、不要な呼び出しはアプリケーション パフォーマンスの低下につながる可能性があるため、レイアウト システムを呼び出す可能性があるイベントを理解することが重要です。 以下に、レイアウト システムが呼び出されたときに発生するプロセスについて説明します。  
  
1.  子<xref:System.Windows.UIElement>測定コア プロパティを持つ最初からレイアウト プロセスを開始します。  
  
2.  サイズ設定プロパティで定義されている<xref:System.Windows.FrameworkElement>など、評価は<xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.Height%2A>、および<xref:System.Windows.FrameworkElement.Margin%2A>です。  
  
3.  <xref:System.Windows.Controls.Panel>-など特定のロジックが適用される<xref:System.Windows.Controls.Dock>方向、またはスタック<xref:System.Windows.Controls.StackPanel.Orientation%2A>です。  
  
4.  すべての子が測定された後にコンテンツが配置されます。  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A>コレクションは、画面に描画します。  
  
6.  プロセスに呼び出されるもう一度場合追加<xref:System.Windows.Controls.Panel.Children%2A>、コレクションに追加されます、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>適用すると、または<xref:System.Windows.UIElement.UpdateLayout%2A>メソッドが呼び出されます。  
  
 このプロセスとその呼び出し方法は、次のセクションで詳細に定義します。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>子の測定と配置  
 レイアウト システムの各メンバーに対して 2 つのパスを完了する、<xref:System.Windows.Controls.Panel.Children%2A>コレクション、測定パスと配置パス。 それぞれの子<xref:System.Windows.Controls.Panel>独自<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドは独自の特定のレイアウト動作を実現するためにします。  
  
 各メンバーの測定パス中に、<xref:System.Windows.Controls.Panel.Children%2A>コレクションが評価されます。 呼び出しには、まず、<xref:System.Windows.UIElement.Measure%2A>メソッドです。 親の実装内でこのメソッドが呼び出されます<xref:System.Windows.Controls.Panel>要素、およびレイアウトの発生を明示的に呼び出す必要はありません。  
  
 最初、ネイティブのサイズ プロパティ、<xref:System.Windows.UIElement>など、評価は<xref:System.Windows.UIElement.Clip%2A>と<xref:System.Windows.UIElement.Visibility%2A>です。 これにより、という名前の値が生成されます。`constraintSize`に渡される<xref:System.Windows.FrameworkElement.MeasureCore%2A>です。  
  
 次に、フレームワーク プロパティが定義されている<xref:System.Windows.FrameworkElement>が処理の値に影響する`constraintSize`です。 これらのプロパティ、通常、サイズ変更の特性を記述、基になる<xref:System.Windows.UIElement>などの<xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、および<xref:System.Windows.FrameworkElement.Style%2A>です。 これらの各プロパティは、要素を表示するために必要な領域を変更できます。 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>呼び出された`constraintSize`をパラメーターとして。  
  
> [!NOTE]
>  プロパティの間で違いがある<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>と<xref:System.Windows.FrameworkElement.ActualWidth%2A>です。 たとえば、<xref:System.Windows.FrameworkElement.ActualHeight%2A>プロパティは、その他の高さの入力と、レイアウト システムに基づいて計算される値。 値が実際のレンダリング パスに基づいて、レイアウト システム自体によって設定されている可能性があるためと、プロパティの設定された値の背後にあるなど<xref:System.Windows.FrameworkElement.Height%2A>、入力の変更の基礎にあります。  
>   
>  <xref:System.Windows.FrameworkElement.ActualHeight%2A>注意すべき、計算した値には複数存在する可能性がありますか、増分が報告されている結果が変化してさまざまな操作、レイアウト システムでします。 レイアウト システムが、子要素に必要な測定スペース、親要素による制約などを計算している場合があります。  
  
 測定パスの最終的な目標は、子を決定する、 <xref:System.Windows.UIElement.DesiredSize%2A>、中に発生する、<xref:System.Windows.FrameworkElement.MeasureCore%2A>呼び出します。 <xref:System.Windows.UIElement.DesiredSize%2A>によって値が格納されている<xref:System.Windows.UIElement.Measure%2A>コンテンツの配置パスで使用するためです。  
  
 配置パスがへの呼び出しで始まり、<xref:System.Windows.UIElement.Arrange%2A>メソッドです。 パスでは、配置、親<xref:System.Windows.Controls.Panel>要素が子の境界を表す四角形を生成します。 この値は、<xref:System.Windows.FrameworkElement.ArrangeCore%2A>処理のためのメソッドです。  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>メソッドは、評価、<xref:System.Windows.UIElement.DesiredSize%2A>子のレンダリングされる要素のサイズに影響するその他の余白を評価します。 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>生成、`arrangeSize`に渡される、<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>のメソッド、<xref:System.Windows.Controls.Panel>をパラメーターとして。 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>生成、`finalSize`子。 最後に、<xref:System.Windows.FrameworkElement.ArrangeCore%2A>メソッドが最終的な余白や配置などのオフセットのプロパティの評価し、レイアウト スロット内の子を格納します。 子は割り当てられた領域全体を埋める必要はありません (そうしない場合もよくあります)。 コントロールは、親に返されます<xref:System.Windows.Controls.Panel>レイアウト プロセスが完了するとします。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>パネル要素とカスタム レイアウトの動作  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]派生した要素のグループが含まれています<xref:System.Windows.Controls.Panel>です。 これら<xref:System.Windows.Controls.Panel>要素には、多くの複雑なレイアウトが有効にします。 たとえば、要素をスタックに簡単に実現できますを使用して、<xref:System.Windows.Controls.StackPanel>要素を使用して、複雑なレイアウトと空きフロー レイアウトも有効であるときに、<xref:System.Windows.Controls.Canvas>です。  
  
 次の表に、使用可能なレイアウト<xref:System.Windows.Controls.Panel>要素。  
  
|パネル名|説明|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|内部では、子要素に対する相対座標で明示的に配置できる領域を定義、<xref:System.Windows.Controls.Canvas>領域。|  
|<xref:System.Windows.Controls.DockPanel>|子要素を互いに水平方向または垂直方向に整列する領域を定義します。|  
|<xref:System.Windows.Controls.Grid>|行と列で構成される柔軟性のあるグリッド領域を定義します。|  
|<xref:System.Windows.Controls.StackPanel>|子要素を水平方向または垂直方向の単一行に整列します。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|フレームワークを提供<xref:System.Windows.Controls.Panel>子のデータ コレクションを仮想化する要素。 これは抽象クラスです。|  
|<xref:System.Windows.Controls.WrapPanel>|左から右へ順に子要素を配置し、ボックスの端で改行してコンテンツを次の行へ送ります。 後続の並べ替えが発生した順番に上から下または右から左の値に応じて、<xref:System.Windows.Controls.WrapPanel.Orientation%2A>プロパティです。|  
  
 定義済みのいずれかの方法では不可能なレイアウトを必要とするアプリケーションの<xref:System.Windows.Controls.Panel>要素、カスタム レイアウト動作から継承することで実現できます<xref:System.Windows.Controls.Panel>をオーバーライドして、<xref:System.Windows.FrameworkElement.MeasureOverride%2A>と<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>メソッドです。 例については、「[Custom Radial Panel Sample](http://go.microsoft.com/fwlink/?LinkID=159982)」 (カスタム放射状パネルのサンプル) を参照してください。  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>レイアウトのパフォーマンスの考慮事項  
 レイアウトは再帰的なプロセスです。 内の各子要素、<xref:System.Windows.Controls.Panel.Children%2A>レイアウト システムの各呼び出し中にコレクションが処理を取得します。 そのため、必要ない場合はレイアウト システムをトリガーしないようにしてください。 次の考慮事項は、パフォーマンスを向上させるのに役立ちます。  
  
-   どのプロパティ値の変更がレイアウト システムによる再帰的な更新を強制するかに注意してください。  
  
     レイアウト システムを初期化できる値が設定されている依存関係プロパティは、パブリック フラグでマークされます。 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>および<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>プロパティに関する値が変更されたが、再帰的なを強制的に役立ちますの手がかりをレイアウト システム更新を提供します。 通常、要素の境界ボックスのサイズに影響する可能性があるプロパティがあります、<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>フラグを true に設定します。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
-   可能であれば、使用、<xref:System.Windows.UIElement.RenderTransform%2A>の代わりに、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>です。  
  
     A<xref:System.Windows.FrameworkElement.LayoutTransform%2A>の内容に影響する非常に便利な方法を指定できます、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 ただし、その他の要素の位置に影響する変換の結果がない場合をお勧めを使用する、<xref:System.Windows.UIElement.RenderTransform%2A>代わりに、ため<xref:System.Windows.UIElement.RenderTransform%2A>レイアウト システムは呼び出されません。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>その変換を適用し、新しい要素の位置の影響を受けるために、再帰的なレイアウトの更新を強制します。  
  
-   不要な呼び出しを避けるため<xref:System.Windows.UIElement.UpdateLayout%2A>です。  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A>メソッドは、再帰的なレイアウトの更新を強制し、よく必要はありません。 完全な更新が必要であると確信できる場合を除き、このメソッドの呼び出しはレイアウト システムに任せます。  
  
-   大規模なを使用する場合<xref:System.Windows.Controls.Panel.Children%2A>、コレクションの使用を検討、 <xref:System.Windows.Controls.VirtualizingStackPanel> 、通常ではなく<xref:System.Windows.Controls.StackPanel>です。  
  
     子コレクションを仮想化により、<xref:System.Windows.Controls.VirtualizingStackPanel>は現在、親のビューポート内にあるメモリ内オブジェクトにのみ維持されます。 その結果、ほとんどのシナリオでパフォーマンスが大幅に向上します。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>サブピクセル レンダリングとレイアウトの丸め処理  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グラフィックス システムでは、デバイスに依存しない単位を使用して、解像度とデバイスの独立性を可能にします。 システムのされた各デバイスに依存しないピクセルが自動的に拡大縮小[!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)]設定します。 これにより、異なる [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 設定に対して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに適切なスケーリングを提供し、アプリケーションを自動的に [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 対応にします。  
  
 ただし、この [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 非依存は、アンチエイリアシングのため、不規則なエッジ レンダリングが作成される場合があります。 これらの成果物 (通常はぼやけたエッジや半透明のエッジが見られます) は、エッジの場所がデバイス ピクセルの間ではなく、デバイス ピクセルの中間にある場合に発生します。 レイアウト システムは、レイアウトの丸め処理でこれを調整する方法を提供します。 レイアウトの丸め処理では、レイアウト システムがレイアウト パスの実行中に任意の整数以外のピクセル値を丸めます。  
  
 レイアウトの丸め処理は既定で無効になっています。 レイアウトの丸めを有効にするには設定、<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>プロパティを`true`いずれかで<xref:System.Windows.FrameworkElement>です。 これは依存関係プロパティであるため、値はビジュアル ツリー内のすべての子に反映されます。 レイアウトの UI 全体の丸め処理を有効にするには設定<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>に`true`ルート コンテナーにします。 例については、「<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>」を参照してください。  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>次の内容  
 要素の測定方法と配置方法を理解することが、レイアウトを理解する最初のステップです。 詳細については、使用可能な<xref:System.Windows.Controls.Panel>要素を参照してください[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)です。 レイアウトに影響を与えるさまざまな配置プロパティをより理解するには、「[配置、余白、パディングの概要](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)」を参照してください。 カスタムの例については<xref:System.Windows.Controls.Panel>要素を参照してください[カスタム放射状パネル サンプル](http://go.microsoft.com/fwlink/?LinkID=159982)です。 軽量のアプリケーションにまとめて配置する準備ができたらを参照してください。[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [配置、余白、パディングの概要](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
