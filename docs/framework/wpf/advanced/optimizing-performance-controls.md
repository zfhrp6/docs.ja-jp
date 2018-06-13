---
title: 'パフォーマンスの最適化 : コントロール'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 9e4ceee26263a1d047aeda0881b955070de4326d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549264"
---
# <a name="optimizing-performance-controls"></a>パフォーマンスの最適化 : コントロール
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、大半の Windows アプリケーションで使用される一般的なユーザー インターフェイス (UI: User Interface) コンポーネントが多数含まれています。 このトピックでは、UI のパフォーマンスを向上させる方法について説明します。  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>大容量のデータ セットの表示  
 などの WPF コントロール、<xref:System.Windows.Controls.ListView>と<xref:System.Windows.Controls.ComboBox>アプリケーションにアイテムの一覧を表示するために使用します。 表示するリストが大きい場合、アプリケーションのパフォーマンスに影響する可能性があります。 これは、標準的なレイアウト システムでは、リスト コントロールに関連付けられた項目ごとにレイアウト コンテナーを作成した後、コンテナーのレイアウト サイズと位置を計算するためです。 通常、すべての項目を同時に表示する必要はありません。その代わりに項目のサブセットが表示され、ユーザーはリストをスクロールすることで、すべての項目を確認します。 このような場合は、UI の*仮想化*が役に立ちます。これは、項目に対する項目コンテナーの生成、および関連するレイアウトの計算を、項目が表示されるまで遅らせることを意味します。  
  
 UI の仮想化は、リスト コントロールにとって重要な処理です。 UI の仮想化とデータの仮想化を混同しないでください。 UI の仮想化では、表示される項目だけをメモリに格納しますが、データのバインディングがある場合はデータ構造体のすべてがメモリに格納されます。 これに対し、データの仮想化では、画面上に表示されているデータ項目だけがメモリに格納されます。  
  
 既定では、UI の仮想化が有効になって、<xref:System.Windows.Controls.ListView>と<xref:System.Windows.Controls.ListBox>リスト項目がデータにバインドされる場合を制御します。 <xref:System.Windows.Controls.TreeView> 設定して、仮想化を有効にすることができます、 <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing`添付プロパティ`true`です。 派生するカスタム コントロールの UI 仮想化を有効にするかどうかは<xref:System.Windows.Controls.ItemsControl>または既存の項目のコントロールを使用する、<xref:System.Windows.Controls.StackPanel>クラスなど<xref:System.Windows.Controls.ComboBox>、設定することができます、<xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A>に<xref:System.Windows.Controls.VirtualizingStackPanel>設定と<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A>に`true`. 残念ながら、これらのコントロールに対する UI の仮想化を知らずに無効にすることがあります。 UI の仮想化が無効になる条件を一覧で示します。  
  
-   項目コンテナーは直接に追加された、<xref:System.Windows.Controls.ItemsControl>です。 たとえば、アプリケーションが明示的に追加<xref:System.Windows.Controls.ListBoxItem>オブジェクトを<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ListBox>は仮想化できません、<xref:System.Windows.Controls.ListBoxItem>オブジェクト。  
  
-   内のコンテナーの項目、<xref:System.Windows.Controls.ItemsControl>型が異なります。 たとえば、<xref:System.Windows.Controls.Menu>を使用して<xref:System.Windows.Controls.Separator>オブジェクトがために、項目が再利用を実装することはできません、<xref:System.Windows.Controls.Menu>型のオブジェクトが含まれます<xref:System.Windows.Controls.Separator>と<xref:System.Windows.Controls.MenuItem>です。  
  
-   設定<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A>に`false`です。  
  
-   設定<!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>-->`IsVirtualizing`に`false`です。  
  
 コンテナー項目を仮想化する際の重要な考慮事項は項目が属する項目コンテナーに関連付けられた追加の状態情報があるかどうかです。 その場合は、追加状態を保存する必要があります。 たとえばに含まれている項目があります、<xref:System.Windows.Controls.Expander>コントロールと<xref:System.Windows.Controls.Expander.IsExpanded%2A>状態を連結すると、アイテムのコンテナーおよびアイテム自体にありません。 コンテナーが、新しい項目の現在の値の再利用された日時<xref:System.Windows.Controls.Expander.IsExpanded%2A>新しい項目のために使用します。 さらに、古い項目は、正しい失った<xref:System.Windows.Controls.Expander.IsExpanded%2A>値。  
  
 現時点では、データの仮想化のサポートが組み込まれている WPF コントロールはありません。  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>コンテナーのリサイクル  
 UI 仮想化コントロールから継承するは、.NET Framework 3.5 SP1 で追加するよう最適化<xref:System.Windows.Controls.ItemsControl>は*コンテナーのリサイクル、* でもスクロールのパフォーマンスが向上することができます。  ときに、<xref:System.Windows.Controls.ItemsControl>を使用して UI 仮想化が設定されると、表示されるまでスクロールし、スクロール ビューから外れている各項目の項目コンテナーを破棄する各アイテムについて、項目コンテナーが作成されます。 *コンテナー リサイクル*コントロールが項目コンテナーがない常に作成され、ユーザーがスクロール破棄できるように、別のデータ項目の既存の項目コンテナーを再利用できるように、<xref:System.Windows.Controls.ItemsControl>です。 項目を設定してリサイクルを有効にすることができます、<xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A>添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling>です。  
  
 どの<xref:System.Windows.Controls.ItemsControl>をサポートする仮想化は、コンテナーのリサイクルを使用できます。  [リサイクル] コンテナーを有効にする方法の例については、<xref:System.Windows.Controls.ListBox>を参照してください[ListBox のスクロールのパフォーマンスを向上させる](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)です。  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>双方向仮想化のサポート  
 <xref:System.Windows.Controls.VirtualizingStackPanel> 水平方向または垂直方向には、一方向に UI 仮想化の組み込みサポートを提供しています。 コントロールの双方向の仮想化を使用する場合は、拡張するカスタム パネルを実装する必要があります、<xref:System.Windows.Controls.VirtualizingStackPanel>クラスです。 <xref:System.Windows.Controls.VirtualizingStackPanel>クラスなどの仮想メソッドを公開<xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>、 <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>、 <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>、および<xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>です。これらの仮想メソッドを使用すると、一覧の表示領域の変更を検出し、それに応じて処理できます。  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>テンプレートの最適化  
 ビジュアル ツリーには、アプリケーションのすべてのビジュアル要素が含まれます。  直接的に作成されたオブジェクトに加え、テンプレートの拡張によって追加されたオブジェクトも含まれます。  たとえば、作成、 <xref:System.Windows.Controls.Button>、取得することも<xref:Microsoft.Windows.Themes.ClassicBorderDecorator>と<xref:System.Windows.Controls.ContentPresenter>ビジュアル ツリー内のオブジェクト。  コントロール テンプレートを最適化していない場合、必要のない余分なオブジェクトがビジュアル ツリーの中に多数作成される可能性があります。   ビジュアル ツリーの詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>遅延スクロール  
 既定では、ユーザーがスクロールバーのつまみをドラッグすると、コンテンツ ビューが連続的に更新されます。  コントロールのスクロールが遅い場合は、遅延スクロールの使用をご検討ください。  遅延スクロールでは、コンテンツは、ユーザーがつまみを離したときにのみ更新されます。  
  
 スクロールの遅延を実装するのには、設定、<xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>プロパティを`true`です。  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 添付プロパティは、に対して設定できる<xref:System.Windows.Controls.ScrollViewer>とを持つすべての制御、<xref:System.Windows.Controls.ScrollViewer>コントロール テンプレートにします。  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>パフォーマンス機能を実装するコントロール  
 次の表は、データを表示するための一般的なコントロールと、各コントロールのパフォーマンス機能に対するサポートを示しています。  これらの機能を有効にする方法については、前のセクションを参照してください。  
  
|コントロール|仮想化|コンテナーのリサイクル|遅延スクロール|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|有効にできます|有効にできます|有効にできます|  
|<xref:System.Windows.Controls.ContextMenu>|有効にできます|有効にできます|有効にできます|  
|<xref:System.Windows.Controls.DocumentViewer>|使用できません|使用できません|有効にできます|  
|<xref:System.Windows.Controls.ListBox>|既定値|有効にできます|有効にできます|  
|<xref:System.Windows.Controls.ListView>|既定値|有効にできます|有効にできます|  
|<xref:System.Windows.Controls.TreeView>|有効にできます|有効にできます|有効にできます|  
|<xref:System.Windows.Controls.ToolBar>|使用できません|使用できません|有効にできます|  
  
> [!NOTE]
>  仮想化し、[リサイクル] コンテナーを有効にする方法の例については、<xref:System.Windows.Controls.TreeView>を参照してください[TreeView のパフォーマンスを向上させる](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)です。  
  
## <a name="see-also"></a>関連項目  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
