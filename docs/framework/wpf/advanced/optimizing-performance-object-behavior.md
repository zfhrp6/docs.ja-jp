---
title: "パフォーマンスの最適化 : オブジェクトの動作 | Microsoft Docs"
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
  - "依存関係プロパティ, パフォーマンス"
  - "イベント ハンドラー [WPF]"
  - "Freezable オブジェクト, パフォーマンス"
  - "オブジェクト パフォーマンスに関する留意事項"
  - "ユーザー インターフェイスの仮想化"
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# パフォーマンスの最適化 : オブジェクトの動作
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトに固有の動作を理解することは、機能とパフォーマンスのバランスを見極めるうえで役に立ちます。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Not_Removing_Event_Handlers"></a>   
## オブジェクトのイベント ハンドラーを削除しないとオブジェクトが維持される可能性がある  
 オブジェクトがそのイベントに渡すデリゲートは、事実上そのオブジェクトへの参照です。  このため、イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。  オブジェクトのイベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。  不要なオブジェクトが残っていると、アプリケーションのメモリ使用量が増加します。  これは、オブジェクトが[論理ツリー](GTMT)や[ビジュアル ツリー](GTMT)のルートである場合には特に重要になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって導入される弱いイベント リスナー パターンは、ソースとリスナーのオブジェクト有効期間の関係の追跡が困難な場合に役に立ちます。  一部の既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントはこのパターンを使用します。  カスタム イベントを持つオブジェクトを実装する場合に、このパターンが役に立つこともあります。  詳細については、「[弱いイベント パターン](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)」を参照してください。  
  
 CLR プロファイラーや作業セット ビューアーなど、特定のプロセスのメモリ使用量に関する情報を入手できるツールもいくつかあります。  CLR プロファイラーには、割り当てられた型のヒストグラム、割り当てグラフと呼び出しグラフ、さまざまなジェネレーションのガベージ コレクションとその結果のマネージ ヒープの状態を示す時系列、メソッドごとの割り当てとアセンブリの読み込みを示す呼び出しツリーなど、非常に便利な割り当てプロファイルのビューがいくつか含まれています。  詳細については、[.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=117435) を参照してください。  
  
<a name="DPs_and_Objects"></a>   
## 依存関係プロパティと依存関係オブジェクト  
 一般に、<xref:System.Windows.DependencyObject> の[依存関係プロパティ](GTMT)へのアクセスが [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティへのアクセスに比べて遅いということはありません。  プロパティ値の設定には多少のパフォーマンス オーバーヘッドがありますが、値の取得は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティから取得する場合と同じくらい高速です。  この小さなパフォーマンス オーバーヘッドがある代わりに、[依存関係プロパティ](GTMT)では、データ バインディング、アニメーション、継承、スタイル設定などの堅牢な機能がサポートされています。  詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
### DependencyProperty の最適化  
 アプリケーションで[依存関係プロパティ](GTMT)を定義するときには注意が必要です。  定義する <xref:System.Windows.DependencyProperty> が描画型のメタデータ オプションにしか影響しない場合 \(<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> などのその他のメタデータ オプションには影響しない場合\) は、メタデータをオーバーライドしてそのようにマークする必要があります。  プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
 すべてのプロパティ変更が実際に測定、配置、および描画に影響するわけではない場合は、測定、配置、および描画の各パスを、プロパティ変更ハンドラーによって手動で無効にした方が効率的な場合もあります。  たとえば、設定した制限値より値が大きい場合にのみ背景を再描画する場合は、  設定した制限値を値が超えていた場合にのみプロパティ変更ハンドラーで描画を無効にします。  
  
### DependencyProperty を継承可能にするとパフォーマンスへの負荷が発生する  
 既定では、登録した[依存関係プロパティ](GTMT)は継承不可になります。  ただし、プロパティはどれでも明示的に継承可能にすることができます。  この機能は便利ですが、プロパティを継承可能にすると、プロパティの無効化の時間が増加して、パフォーマンスに影響します。  
  
### RegisterClassHandler は慎重に使用する  
 <xref:System.Windows.EventManager.RegisterClassHandler%2A> を呼び出すと、インスタンスの状態を保存することができます。ただし、このハンドラーはすべてのインスタンスで呼び出されるということを認識しておく必要があります。これはパフォーマンス上問題になる可能性があります。  <xref:System.Windows.EventManager.RegisterClassHandler%2A> を使用するのは、アプリケーションでインスタンスの状態を保存する必要がある場合だけにしてください。  
  
### DependencyProperty の既定値は登録時に設定する  
 既定値を必要とする <xref:System.Windows.DependencyProperty> を作成するときには、<xref:System.Windows.DependencyProperty> の <xref:System.Windows.DependencyProperty.Register%2A> メソッドにパラメーターとして渡される既定のメタデータを使用してその値を設定します。  コンストラクターや要素の各インスタンスでプロパティ値を設定するのではなく、この方法を使用するようにしてください。  
  
### Register を使用して PropertyMetadata の値を設定する  
 <xref:System.Windows.DependencyProperty> を作成する場合、<xref:System.Windows.PropertyMetadata> を設定するには、<xref:System.Windows.DependencyProperty.Register%2A> メソッドを使用する方法と <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> メソッドを使用する方法があります。  オブジェクトの静的コンストラクターで <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> を呼び出すこともできますが、これは最適な解決方法とは言えず、パフォーマンスに影響します。  最適なパフォーマンスを得るためには、<xref:System.Windows.DependencyProperty.Register%2A> の呼び出しの際に <xref:System.Windows.PropertyMetadata> を設定します。  
  
<a name="Freezable_Objects"></a>   
## Freezable オブジェクト  
 <xref:System.Windows.Freezable> は、非フリーズとフリーズの 2 つの状態を持つ特殊な型のオブジェクトです。  可能な場合は常にオブジェクトを固定するようにすると、アプリケーションのパフォーマンスが向上し、作業セットを縮小できます。  詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 各 <xref:System.Windows.Freezable> には、オブジェクトが変更されるたびに発生する <xref:System.Windows.Freezable.Changed> イベントがあります。  ただし、変更通知はアプリケーションのパフォーマンスに影響を与えます。  
  
 たとえば、次の例では、各 <xref:System.Windows.Shapes.Rectangle> が同じ <xref:System.Windows.Media.Brush> オブジェクトを使用しています。  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、<xref:System.Windows.Media.SolidColorBrush> オブジェクトの <xref:System.Windows.Freezable.Changed> イベントに対するイベント ハンドラーが既定で用意されており、それを使用して <xref:System.Windows.Shapes.Rectangle> オブジェクトの <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを無効にすることができます。  この場合、<xref:System.Windows.Media.SolidColorBrush> では、<xref:System.Windows.Freezable.Changed> イベントを発生させる必要が生じるたびに、各 <xref:System.Windows.Shapes.Rectangle> のコールバック関数を呼び出す必要があります。このコールバック関数の呼び出しが積み重なると、パフォーマンスが大幅に低下します。  さらに、この時点でハンドラーを追加または削除すると、アプリケーションでリスト全体を検査しなければならなくなるため、パフォーマンスに大きく影響します。  アプリケーションのシナリオで <xref:System.Windows.Media.SolidColorBrush> が変更されることがない場合は、<xref:System.Windows.Freezable.Changed> イベント ハンドラーの維持に無駄な負荷を費やすことになります。  
  
 <xref:System.Windows.Freezable> を固定すると、変更通知の維持にリソースを費やす必要がなくなるため、パフォーマンスが向上します。  次の表は、単純な <xref:System.Windows.Media.SolidColorBrush> について、<xref:System.Windows.Freezable.IsFrozen%2A> プロパティを `true` に設定した場合とそうでない場合のサイズの比較を示しています。  ここでは、10 の <xref:System.Windows.Shapes.Rectangle> オブジェクトの <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティに 1 つのブラシを適用する場合を想定しています。  
  
|**状態**|**サイズ**|  
|------------|-------------|  
|固定された <xref:System.Windows.Media.SolidColorBrush>|212 バイト|  
|固定されていない <xref:System.Windows.Media.SolidColorBrush>|972 バイト|  
  
 この概念の例を次のコード サンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### 固定されていない Freezable の Changed ハンドラーによってオブジェクトが維持される可能性がある  
 <xref:System.Windows.Freezable> オブジェクトの <xref:System.Windows.Freezable.Changed> イベントにオブジェクトが渡すデリゲートは、事実上そのオブジェクトへの参照です。  このため、<xref:System.Windows.Freezable.Changed> イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。  <xref:System.Windows.Freezable> オブジェクトの <xref:System.Windows.Freezable.Changed> イベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Freezable.Changed> イベントが内部でもフックされます。  たとえば、<xref:System.Windows.Freezable> を値として受け取るすべての[依存関係プロパティ](GTMT)は、自動的に <xref:System.Windows.Freezable.Changed> イベントをリッスンします。  この概念の例として、<xref:System.Windows.Media.Brush> を受け取る <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティを次に示します。  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 `myRectangle.Fill` に `myBrush` を割り当てると、その <xref:System.Windows.Shapes.Rectangle> オブジェクトを指すデリゲートが <xref:System.Windows.Media.SolidColorBrush> オブジェクトの <xref:System.Windows.Freezable.Changed> イベントに追加されます。  このため、次のコードを使用しても、`myRect` は実際にはガベージ コレクションの対象にはなりません。  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 この場合、`myBrush` は `myRectangle` を引き続き維持し、それを <xref:System.Windows.Freezable.Changed> イベントを発生させるときにコールバックします。  `myBrush` を新しい <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> プロパティに割り当てても、`myBrush` にイベント ハンドラーがさらに追加されるだけです。  
  
 この種のオブジェクトをクリーンアップするための推奨される方法としては、<xref:System.Windows.Shapes.Shape.Fill%2A> プロパティから <xref:System.Windows.Media.Brush> を削除します。これにより、<xref:System.Windows.Freezable.Changed> イベント ハンドラーも削除されます。  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## ユーザー インターフェイスの仮想化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] もデータ バインド子コンテンツを自動的に "仮想化する" <xref:System.Windows.Controls.StackPanel> 要素のバリエーションを提供します。  ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、オブジェクトのサブセットを多数のデータ項目から生成する手法を指します。  特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。  <xref:System.Windows.Controls.VirtualizingStackPanel> は、<xref:System.Windows.Controls.VirtualizingPanel> で提供される機能を通じて、表示される項目を計算し、<xref:System.Windows.Controls.ItemsControl> \(<xref:System.Windows.Controls.ListBox> や <xref:System.Windows.Controls.ListView> など\) の <xref:System.Windows.Controls.ItemContainerGenerator> と共に機能することで、表示される項目に対応する要素だけを作成します。  
  
 パフォーマンスの最適化の一環として、これらの項目のビジュアル オブジェクトは、画面に表示される場合にのみ生成または維持されます。  既にコントロールの表示可能領域にないビジュアル オブジェクトは削除される可能性があります。  これをデータの仮想化と混同しないようにしてください。データの仮想化では、すべてのデータ オブジェクトがローカル コレクションに存在するのではなく、データ オブジェクトが必要に応じてストリームされます。  
  
 次の表は、5000 の <xref:System.Windows.Controls.TextBlock> 要素を <xref:System.Windows.Controls.StackPanel> と <xref:System.Windows.Controls.VirtualizingStackPanel> に追加して描画した場合の経過時間を示しています。  このシナリオの測定値は、テキスト文字列を <xref:System.Windows.Controls.ItemsControl> オブジェクトの <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティに割り当ててから、パネル要素にそのテキスト文字列が表示されるまでの時間を表します。  
  
|**ホスト パネル**|**レンダリング時間 \(ミリ秒\)**|  
|-----------------|--------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## 参照  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)