---
title: "ScrollViewer の概要 | Microsoft Docs"
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
  - "コントロール, ScrollViewer"
  - "ScrollViewer コントロール, ScrollViewer コントロールの概要"
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# ScrollViewer の概要
ユーザー インターフェイスのコンテンツは、コンピューターの画面の表示領域より大きいことがよくあります。  <xref:System.Windows.Controls.ScrollViewer> コントロールには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションのコンテンツのスクロールを可能にする便利な方法が用意されています。  このトピックでは、<xref:System.Windows.Controls.ScrollViewer> 要素について説明し、使用例をいくつか示します。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [ScrollViewer コントロール](#what_is_a_scrollviewer_element)  
  
-   [物理スクロールと論理スクロール](#scrollviewer_physical_vs_logical)  
  
-   [ScrollViewer 要素の定義と使用](#scrollviewer_markup_syntax_and_sample)  
  
-   [ScrollViewer へのスタイルの適用](#scrollviewer_styling_scrollviewer)  
  
-   [ドキュメントの改ページ処理](#scrollviewer_scroll_vs_paginate)  
  
-   [Related Topics](#seeAlsoToggle)  
  
<a name="what_is_a_scrollviewer_element"></a>   
## ScrollViewer コントロール  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでのスクロールを可能にする定義済み要素には、<xref:System.Windows.Controls.Primitives.ScrollBar> と <xref:System.Windows.Controls.ScrollViewer> の 2 つがあります。  <xref:System.Windows.Controls.ScrollViewer> コントロールは、スクロール可能領域に他の表示要素を表示するために、水平および垂直の <xref:System.Windows.Controls.Primitives.ScrollBar> 要素とコンテンツ コンテナー \(<xref:System.Windows.Controls.Panel> 要素など\) をカプセル化します。  コンテンツのスクロール用に <xref:System.Windows.Controls.Primitives.ScrollBar> 要素を使用するには、カスタム オブジェクトを作成する必要があります。  一方、<xref:System.Windows.Controls.ScrollViewer> 要素は <xref:System.Windows.Controls.Primitives.ScrollBar> の機能をカプセル化する複合コントロールなので、単独で使用することができます。  
  
 <xref:System.Windows.Controls.ScrollViewer> コントロールは、マウスとキーボードの両方のコマンドに応答し、あらかじめ設定されているインクリメントでコンテンツをスクロールする多くのメソッドが定義されています。  <xref:System.Windows.Controls.ScrollViewer> の状態変化を検出するには、<xref:System.Windows.Controls.ScrollViewer.ScrollChanged> イベントを使用できます。  
  
 <xref:System.Windows.Controls.ScrollViewer> が持つことのできる子は 1 つだけです。通常は、要素の <xref:System.Windows.Controls.Panel.Children%2A> コレクションをホストできる <xref:System.Windows.Controls.Panel> 要素を使用します。  <xref:System.Windows.Controls.ContentPresenter.Content%2A> プロパティは、<xref:System.Windows.Controls.ScrollViewer> の唯一の子を定義します。  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## 物理スクロールと論理スクロール  
 物理スクロールは、あらかじめ定められた物理インクリメント \(通常は、ピクセル数で宣言された値\) で内容をスクロールするために使用されます。  論理スクロールは、論理ツリーの次の項目にスクロールするために使用されます。  物理スクロールは、ほとんどの <xref:System.Windows.Controls.Panel> 要素の既定のスクロール動作です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、両方の種類のスクロールをサポートしています。  
  
#### IScrollInfo インターフェイス  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> インターフェイスは、<xref:System.Windows.Controls.ScrollViewer> または派生コントロール内のメインのスクロール領域を表します。  このインターフェイスではスクロールのプロパティとメソッドが定義されており、物理インクリメントではなく論理単位でのスクロールを必要とする <xref:System.Windows.Controls.Panel> 要素によって実装できます。  <xref:System.Windows.Controls.Primitives.IScrollInfo> のインスタンスを派生 <xref:System.Windows.Controls.Panel> にキャストし、そのスクロール メソッドを使用すると、ピクセル インクリメントではなく、子コレクション内の次の論理単位にスクロールする場合に役立ちます。  既定では、<xref:System.Windows.Controls.ScrollViewer> コントロールは物理単位でのスクロールをサポートします。  
  
 <xref:System.Windows.Controls.StackPanel> と <xref:System.Windows.Controls.VirtualizingStackPanel> はどちらも <xref:System.Windows.Controls.Primitives.IScrollInfo> を実装し、論理スクロールをネイティブでサポートします。  論理スクロールをネイティブでサポートするレイアウト コントロールでも、ホスト <xref:System.Windows.Controls.Panel> 要素を <xref:System.Windows.Controls.ScrollViewer> 内にラップし、<xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> プロパティを `false` に設定することで、物理スクロールを実現できます。  
  
 <xref:System.Windows.Controls.Primitives.IScrollInfo> のインスタンスを <xref:System.Windows.Controls.StackPanel> にキャストして、インターフェイスによって定義されているコンテンツ スクロール メソッド \(<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> および <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>\) を使用する方法を次のコード例に示します。  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## ScrollViewer 要素の定義と使用  
 いくつかのテキストと四角形を含むウィンドウに <xref:System.Windows.Controls.ScrollViewer> を作成する例を次に示します。  <xref:System.Windows.Controls.Primitives.ScrollBar> 要素は必要な場合にのみ表示されます。  ウィンドウのサイズを変更すると、<xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> プロパティと <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> プロパティの値の更新に応じて、<xref:System.Windows.Controls.Primitives.ScrollBar> 要素が表示されたり表示されなくなったりします。  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## ScrollViewer へのスタイルの適用  
 Windows Presentation Foundation の他のコントロールと同様に、<xref:System.Windows.Controls.ScrollViewer> にもスタイルを設定でき、コントロールの既定のレンダリング動作を変更できます。  コントロールのスタイル設定の詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## ドキュメントの改ページ処理  
 ドキュメント コンテンツの場合は、スクロールの代わりに、改ページ処理をサポートするドキュメント コンテナーを選択できます。  <xref:System.Windows.Documents.FlowDocument> は、<xref:System.Windows.Controls.FlowDocumentPageViewer> など、複数ページにわたるコンテンツの改ページをサポートする表示コントロールでホストされるように設計されたドキュメント用です。このような表示コントロールでは、スクロールの必要がありません。  <xref:System.Windows.Controls.DocumentViewer> は、<xref:System.Windows.Documents.FixedDocument> コンテンツを表示するためのソリューションを提供し、従来のスクロールを使用して、表示領域の外部にあるコンテンツを表示します。  
  
 ドキュメント形式と表示オプションの詳細については、「[WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.ScrollViewer>   
 <xref:System.Windows.Controls.Primitives.ScrollBar>   
 <xref:System.Windows.Controls.Primitives.IScrollInfo>   
 [Create a Scroll Viewer](http://msdn.microsoft.com/ja-jp/c8e46af7-b417-441b-aa30-791cbdbd43ef)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [ScrollBar のスタイルとテンプレート](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)   
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)