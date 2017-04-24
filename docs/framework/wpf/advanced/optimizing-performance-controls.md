---
title: "パフォーマンスの最適化 : コントロール | Microsoft Docs"
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
  - "コンテナーのリサイクル"
  - "コントロール [WPF], 向上 (パフォーマンスを)"
  - "ユーザー インターフェイスの仮想化"
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# パフォーマンスの最適化 : コントロール
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、大半の Windows アプリケーションで使用される一般的なユーザー インターフェイス \(UI: User Interface\) コンポーネントが多数含まれています。  このトピックでは、UI のパフォーマンスを向上させる方法について説明します。  
  
   
  
<a name="Displaying"></a>   
## 大容量のデータ セットの表示  
 アプリケーションで項目リストを表示するには、<xref:System.Windows.Controls.ListView> や <xref:System.Windows.Controls.ComboBox> などの WPF コントロールが使用されます。  表示するリストが大きい場合、アプリケーションのパフォーマンスに影響する可能性があります。  これは、標準的なレイアウト システムでは、リスト コントロールに関連付けられた項目ごとにレイアウト コンテナーを作成した後、コンテナーのレイアウト サイズと位置を計算するためです。  通常、すべての項目を同時に表示する必要はありません。その代わりに項目のサブセットが表示され、ユーザーはリストをスクロールすることで、すべての項目を確認します。  このような場合は、UI の*仮想化*が役に立ちます。これは、項目に対する項目コンテナーの生成と関連するレイアウトの計算を、項目が表示されるまで遅らせることを意味します。  
  
 UI の仮想化は、リスト コントロールにとって重要な処理です。  UI の仮想化とデータの仮想化を混同しないでください。  UI の仮想化では、表示される項目だけをメモリに格納しますが、データのバインディングがある場合はデータ構造体のすべてがメモリに格納されます。  これに対し、データの仮想化では、画面上に表示されているデータ項目だけがメモリに格納されます。  
  
 既定では、UI の仮想化は、<xref:System.Windows.Controls.ListView> コントロールと <xref:System.Windows.Controls.ListBox> コントロールで、それぞれのリスト項目がデータにバインドされる場合は有効になっています。  <xref:System.Windows.Controls.TreeView> の仮想化は、<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> 添付プロパティを `true` に設定することで有効にできます。  <xref:System.Windows.Controls.ItemsControl> から派生するカスタム コントロール、または <xref:System.Windows.Controls.StackPanel> クラスを使用する既存のコントロール \(<xref:System.Windows.Controls.ComboBox> など\) で UI の仮想化を有効にする場合は、<xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> を <xref:System.Windows.Controls.VirtualizingStackPanel> に設定し、<xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> を`true` に設定します。  ただし、これらのコントロールに対する UI の仮想化は、仮想化を実現せずに無効にできます。  UI の仮想化を無効にする条件を一覧で示します。  
  
-   項目コンテナーが <xref:System.Windows.Controls.ItemsControl> に直接的に追加される。  たとえば、アプリケーションで <xref:System.Windows.Controls.ListBoxItem> オブジェクトが <xref:System.Windows.Controls.ListBox> に明示的に追加される場合、<xref:System.Windows.Controls.ListBox> は <xref:System.Windows.Controls.ListBoxItem> オブジェクトを仮想化しません。  
  
-   <xref:System.Windows.Controls.ItemsControl> に含まれる項目コンテナーの種類が異なる。  たとえば、<xref:System.Windows.Controls.Separator> オブジェクトを使用する <xref:System.Windows.Controls.Menu> では、項目のリサイクルを実装できません。これは、<xref:System.Windows.Controls.Menu> には、<xref:System.Windows.Controls.Separator> 型のオブジェクトと <xref:System.Windows.Controls.MenuItem> 型のオブジェクトが含まれるからです。  
  
-   <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> を `false` に設定する。  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> を `false` に設定する。  
  
 コンテナー項目を仮想化する際の重要な考慮事項は項目が属する項目コンテナーに関連付けられた追加の状態情報の有無です。  その場合は、追加状態を保存する必要があります。  たとえば、<xref:System.Windows.Controls.Expander> コントロールに含まれる項目で、<xref:System.Windows.Controls.Expander.IsExpanded%2A> 状態が、項目自体ではなく、項目コンテナーにバインドされている場合があります。  このコンテナーが新しい項目に対して再利用される場合、新しい項目には <xref:System.Windows.Controls.Expander.IsExpanded%2A> の現在の値が使用されます。  さらに、古い項目は、正しい <xref:System.Windows.Controls.Expander.IsExpanded%2A> 値を失います。  
  
 現時点では、データの仮想化のサポートが組み込まれている WPF コントロールはありません。  
  
<a name="Container"></a>   
## コンテナーのリサイクル  
 .NET Framework 3.5 SP1 で、<xref:System.Windows.Controls.ItemsControl> から継承するコントロール用として追加された UI の仮想化に対する最適化は*コンテナーのリサイクル*です。コンテナーのリサイクルによってスクロールのパフォーマンスも向上します。  UI の仮想化を使用する <xref:System.Windows.Controls.ItemsControl> が設定されると、項目をスクロールして表示するたびに項目コンテナーが作成され、項目をスクロールして非表示にするたびに項目コンテナーが破棄されます。  *コンテナーのリサイクル*では、異なるデータ項目用の既存の項目コンテナーをコントロールが再利用できるので、ユーザーが <xref:System.Windows.Controls.ItemsControl> をスクロールするたびに項目コンテナーの作成と破棄が常に行われることはありません。  <xref:System.Windows.Controls.VirtualizationMode> に <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> の添付プロパティを設定することにより項目のリサイクルを有効にすることができます。  
  
 仮想化をサポートするすべての <xref:System.Windows.Controls.ItemsControl> で、コンテナーのリサイクルを使用できます。  <xref:System.Windows.Controls.ListBox> でコンテナーのリサイクルを有効にする方法の例については、「[ListBox のスクロール速度を向上させる](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)」を参照してください。  
  
<a name="Supporting"></a>   
## 双方向仮想化のサポート  
 <xref:System.Windows.Controls.VirtualizingStackPanel> には、水平または垂直のいずれかの方向での UI の仮想化のサポートが組み込まれています。  コントロールに対して双方向の仮想化を使用する場合は、<xref:System.Windows.Controls.VirtualizingStackPanel> クラスを拡張するカスタム パネルを実装する必要があります。  <xref:System.Windows.Controls.VirtualizingStackPanel> クラスは、<xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>、<xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> などの仮想メソッドを公開します。これらの仮想メソッドを使用して、リストの表示部分の変更を検出し、変更に応じた処理を実行できます。  
  
<a name="Optimizing"></a>   
## テンプレートの最適化  
 ビジュアル ツリーには、アプリケーションのすべてのビジュアル要素が含まれます。  直接的に作成されたオブジェクトに加え、テンプレートの拡張によって追加されたオブジェクトも含まれます。  たとえば、<xref:System.Windows.Controls.Button> を作成すると、ビジュアル ツリーには、<xref:Microsoft.Windows.Themes.ClassicBorderDecorator> オブジェクトと <xref:System.Windows.Controls.ContentPresenter> オブジェクトも取得されます。  コントロール テンプレートを最適化していない場合、必要のない余分なオブジェクトがビジュアル ツリーの中に多数作成される可能性があります。  ビジュアル ツリーの詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
<a name="Deferred"></a>   
## 遅延スクロール  
 既定では、ユーザーがスクロールバーのつまみをドラッグすると、コンテンツ ビューが連続的に更新されます。  コントロールのスクロールが遅い場合は、遅延スクロールの使用を検討してください。  遅延スクロールでは、コンテンツは、ユーザーがつまみを離したときにのみ更新されます。  
  
 遅延スクロールを実装するには、<xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> プロパティを `true` に設定します。  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> は添付プロパティであり、<xref:System.Windows.Controls.ScrollViewer> と、コントロール テンプレート内に <xref:System.Windows.Controls.ScrollViewer> が含まれているすべてのコントロールに設定できます。  
  
<a name="Controls"></a>   
## パフォーマンス機能を実装するコントロール  
 次の表は、データを表示するための一般的なコントロールと、各コントロールのパフォーマンス機能に対するサポートを示しています。  これらの機能を有効にする方法については、前のセクションを参照してください。  
  
|Control|仮想化|コンテナーのリサイクル|遅延スクロール|  
|-------------|---------|-----------------|-------------|  
|<xref:System.Windows.Controls.ComboBox>|有効にできます。|有効にできます。|有効にできます。|  
|<xref:System.Windows.Controls.ContextMenu>|有効にできます。|有効にできます。|有効にできます。|  
|<xref:System.Windows.Controls.DocumentViewer>|使用できません。|使用できません。|有効にできます。|  
|<xref:System.Windows.Controls.ListBox>|既定値|有効にできます。|有効にできます。|  
|<xref:System.Windows.Controls.ListView>|既定値|有効にできます。|有効にできます。|  
|<xref:System.Windows.Controls.TreeView>|有効にできます。|有効にできます。|有効にできます。|  
|<xref:System.Windows.Controls.ToolBar>|使用できません。|使用できません。|有効にできます。|  
  
> [!NOTE]
>  <xref:System.Windows.Controls.TreeView> に対する仮想化とコンテナーのリサイクルを有効にする方法の例については、「[TreeView のパフォーマンスを改善する](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)」を参照してください。  
  
## 参照  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [コントロール](../../../../docs/framework/wpf/controls/index.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)