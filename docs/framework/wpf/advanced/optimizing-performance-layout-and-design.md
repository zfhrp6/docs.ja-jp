---
title: "パフォーマンスの最適化 : レイアウトとデザイン | Microsoft Docs"
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
  - "デザインの考慮事項"
  - "レイアウト パス"
  - "レイアウト, 最適化 (パフォーマンスを)"
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# パフォーマンスの最適化 : レイアウトとデザイン
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの設計によっては、レイアウトの計算やオブジェクト参照の検証で不要なオーバーヘッドが発生して、パフォーマンスに影響が及ぶことがあります。  オブジェクトの作成 \(特に起動時の作成\) はアプリケーションのパフォーマンス特性に影響する可能性があります。  
  
 このトピックでは、このようなパフォーマンスに関する推奨事項について説明します。  
  
## \[レイアウト\]  
 "レイアウト パス" という用語は、<xref:System.Windows.Controls.Panel> 派生オブジェクトの子のコレクションのメンバーを測定および配置して、それらを画面上に描画するプロセスを表します。  レイアウト パスは数学的に増大するプロセスで、コレクション内の子の数が多くなれば、必要な計算の数も多くなります。  たとえば、コレクション内の子 <xref:System.Windows.UIElement> オブジェクトがその位置を変更するたびに、レイアウト システムによる新しいパスがトリガーされる可能性があります。  オブジェクトの特性とレイアウトの動作の間には密接な関係があるため、レイアウト システムを呼び出すことができるイベントの種類を把握することが重要です。  レイアウト パスの不要な呼び出しをできるだけ減らすことで、アプリケーションのパフォーマンスを向上させることができます。  
  
 レイアウト システムは、コレクションの子メンバーごとに、測定パスと配置パスという 2 つのパスを実行します。  各子オブジェクトは、それぞれ固有のレイアウト動作を提供するために、<xref:System.Windows.UIElement.Measure%2A> メソッドと <xref:System.Windows.UIElement.Arrange%2A> メソッドの独自のオーバーライドされた実装を提供します。  簡単に言うと、レイアウトは、要素のサイズ測定、配置、および画面上への描画を繰り返す再帰的なシステムです。  
  
-   子 <xref:System.Windows.UIElement> オブジェクトは、最初にそのコア プロパティを測定して、レイアウト プロセスを開始します。  
  
-   オブジェクトのサイズに関連する <xref:System.Windows.FrameworkElement> プロパティ \(<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> など\) が評価されます。  
  
-   <xref:System.Windows.Controls.DockPanel> の <xref:System.Windows.Controls.DockPanel.Dock%2A> プロパティや <xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.Controls.StackPanel.Orientation%2A> プロパティなど、<xref:System.Windows.Controls.Panel> 固有のロジックが適用されます。  
  
-   すべての子オブジェクトが測定された後、コンテンツが配置されます。  
  
-   子オブジェクトのコレクションが画面に描画されます。  
  
 以下のアクションが発生すると、再びレイアウト パス プロセスが呼び出されます。  
  
-   子オブジェクトがコレクションに追加された場合。  
  
-   子オブジェクトに <xref:System.Windows.FrameworkElement.LayoutTransform%2A> が適用された場合。  
  
-   子オブジェクトに対して <xref:System.Windows.UIElement.UpdateLayout%2A> メソッドが呼び出された場合。  
  
-   測定パスや配置パスに影響を与えるものとしてメタデータでマークされている[依存関係プロパティ](GTMT)の値が変更された場合。  
  
### 可能な場合は最も効率的なパネルを使用する  
 使用する <xref:System.Windows.Controls.Panel> 派生要素のレイアウト動作はレイアウト プロセスの複雑さに直接影響します。  たとえば、<xref:System.Windows.Controls.Grid> コントロールや <xref:System.Windows.Controls.StackPanel> コントロールには <xref:System.Windows.Controls.Canvas> コントロールよりはるかに多くの機能が用意されていますが、  その代償として、パフォーマンスへの負荷も高くなります。  <xref:System.Windows.Controls.Grid> コントロールに用意されている機能が必要ない場合は、<xref:System.Windows.Controls.Canvas> やカスタム パネルなど、パフォーマンスへの負荷が低いコントロールを代わりに使用するようにしてください。  
  
 詳細については、「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」を参照してください。  
  
### RenderTransform は置き換えずに更新する  
 <xref:System.Windows.UIElement.RenderTransform%2A> プロパティの値として、<xref:System.Windows.Media.Transform> を置き換えずに更新できる場合があります。  アニメーションを含むシナリオでは特にこれが当てはまります。  既存の <xref:System.Windows.Media.Transform> を更新すると、不要なレイアウト計算が開始されるのを防ぐことができます。  
  
### ツリーはトップダウンで作成する  
 [論理ツリー](GTMT)のノードが追加または削除されると、ノードの親とそのすべての子でプロパティの無効化が行われます。  このため、常にトップダウンの作成パターンに従って、検証済みのノードで無駄に無効化が行われないようにする必要があります。  ツリーをトップダウンで作成した場合とボトムアップで作成した場合の実行速度の違いを次の表に示します。このツリーには 150 のレベルがあり、各レベルに <xref:System.Windows.Controls.TextBlock> と <xref:System.Windows.Controls.DockPanel> が 1 つずつ含まれています。  
  
|**動作**|**ツリーの作成 \(ミリ秒\)**|**レンダリング — ツリーの作成を含む \(ミリ秒\)**|  
|------------|------------------------|------------------------------------|  
|ボトムアップ|366|454|  
|トップダウン|11|96|  
  
 ツリーをトップダウンで作成する方法を次のコード例に示します。  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 論理ツリーの詳細については、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」を参照してください。  
  
## 参照  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)