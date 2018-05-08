---
title: 'パフォーマンスの最適化 : オブジェクトの動作'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 2e1f56dec87de7a22aa8a0bfefe84222d74ba085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-object-behavior"></a>パフォーマンスの最適化 : オブジェクトの動作
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] オブジェクトに固有の動作を理解することは、機能とパフォーマンスのバランスを見極めるうえで役に立ちます。  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>オブジェクトのイベント ハンドラーを削除しないとオブジェクトが維持される可能性がある  
 オブジェクトがそのイベントに渡すデリゲートは、事実上そのオブジェクトへの参照です。 このため、イベント ハンドラーによってオブジェクトが本来より長く維持される可能性があります。 オブジェクトのイベントをリッスンするように登録されているオブジェクトのクリーンアップを実行するときには、オブジェクトを解放する前にそのデリゲートを削除することが重要です。 不要なオブジェクトが残っていると、アプリケーションのメモリ使用量が増加します。 これは、オブジェクトが論理ツリーやビジュアル ツリーのルートである場合には特に重要になります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって導入される弱いイベント リスナー パターンは、ソースとリスナーのオブジェクト有効期間の関係の追跡が困難な場合に役に立ちます。 一部の既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベントはこのパターンを使用します。 カスタム イベントを持つオブジェクトを実装する場合に、このパターンが役に立つこともあります。 詳細については、「[弱いイベント パターン](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)」を参照してください。  
  
 CLR プロファイラーや作業セット ビューアーなど、特定のプロセスのメモリ使用量に関する情報を入手できるツールもいくつかあります。 CLR プロファイラーには、割り当てられた型のヒストグラム、割り当てグラフと呼び出しグラフ、さまざまなジェネレーションのガベージ コレクションとその結果のマネージ ヒープの状態を示す時系列、メソッドごとの割り当てとアセンブリの読み込みを示す呼び出しツリーなど、非常に便利な割り当てプロファイルのビューがいくつか含まれています。 詳細については、「[.NET Framework デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=117435)」を参照してください。  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>依存関係プロパティと依存関係オブジェクト  
 一般の依存関係プロパティへのアクセス、<xref:System.Windows.DependencyObject>にアクセスするよりも遅くなりますが、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティです。 プロパティ値の設定には多少のパフォーマンス オーバーヘッドがありますが、値の取得は、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティから取得する場合と同じくらい高速です。 この小さなパフォーマンス オーバーヘッドがある代わりに、依存関係プロパティでは、データ バインディング、アニメーション、継承、スタイル設定などの堅牢な機能がサポートされています。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty の最適化  
 アプリケーションで依存関係プロパティを定義するときには注意が必要です。 場合、<xref:System.Windows.DependencyProperty>への影響しか表示されないその他のメタデータ オプションではなく、メタデータの種類のオプションなど<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、そのメタデータをオーバーライドすることでようマークする必要があります。 プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
 すべてのプロパティ変更が実際に測定、配置、描画に影響するわけではない場合は、測定、配置、描画の各パスを、プロパティ変更ハンドラーによって手動で無効にした方が効率的な場合もあります。 たとえば、設定した制限値より値が大きい場合にのみ背景を再描画する場合は、 設定した制限値を値が超えていた場合にのみプロパティ変更ハンドラーで描画を無効にします。  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>DependencyProperty を継承可能にするとパフォーマンスへの負荷が発生する  
 既定では、登録した依存関係プロパティは継承不可になります。 ただし、プロパティはどれでも明示的に継承可能にすることができます。 この機能は便利ですが、プロパティを継承可能にすると、プロパティの無効化の時間が増加して、パフォーマンスに影響します。  
  
### <a name="use-registerclasshandler-carefully"></a>RegisterClassHandler は慎重に使用する  
 呼び出し中に<xref:System.Windows.EventManager.RegisterClassHandler%2A>使用する、インスタンスの状態を保存することが重要すべてのインスタンスでは、パフォーマンスの問題が発生することで、ハンドラーが呼び出されることに注意してください。 のみを使用して<xref:System.Windows.EventManager.RegisterClassHandler%2A>ときに、アプリケーションでは、インスタンスの状態を保存することが必要です。  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>DependencyProperty の既定値は登録時に設定する  
 作成するときに、<xref:System.Windows.DependencyProperty>へのパラメーターとして渡される既定のメタデータを使用して設定すると、既定値を必要とする、<xref:System.Windows.DependencyProperty.Register%2A>のメソッド、<xref:System.Windows.DependencyProperty>です。 コンストラクターや要素の各インスタンスでプロパティ値を設定するのではなく、この方法を使用するようにしてください。  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Register を使用して PropertyMetadata の値を設定する  
 作成するときに、 <xref:System.Windows.DependencyProperty>、設定のオプションがある、<xref:System.Windows.PropertyMetadata>いずれかを使用して、<xref:System.Windows.DependencyProperty.Register%2A>または<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドです。 オブジェクトが、静的コンス トラクターを呼び出す<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>、この最適なソリューションではないと、パフォーマンスに影響します。 最適なパフォーマンスを設定、<xref:System.Windows.PropertyMetadata>への呼び出し中に<xref:System.Windows.DependencyProperty.Register%2A>です。  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable オブジェクト  
 A<xref:System.Windows.Freezable>を 2 つの状態を持つオブジェクトの特別な種類: 固定おらず、固定されています。 可能な場合は常にオブジェクトを固定するようにすると、アプリケーションのパフォーマンスが向上し、作業セットを縮小できます。 詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 各<xref:System.Windows.Freezable>が、<xref:System.Windows.Freezable.Changed>変更されるたびに発生するイベントです。 ただし、変更通知はアプリケーションのパフォーマンスに影響を与えます。  
  
 各の次の例を検討してください<xref:System.Windows.Shapes.Rectangle>同じ<xref:System.Windows.Media.Brush>オブジェクト。  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のイベント ハンドラーを提供、<xref:System.Windows.Media.SolidColorBrush>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントが無効にするために、<xref:System.Windows.Shapes.Rectangle>オブジェクトの<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティです。 たびにこの例では、<xref:System.Windows.Media.SolidColorBrush>が起動がその<xref:System.Windows.Freezable.Changed>イベントごとにコールバック関数を呼び出す必要は<xref:System.Windows.Shapes.Rectangle>— 蓄積されるこれらのコールバック関数の呼び出しの大幅なパフォーマンス ペナルティを適用します。 さらに、この時点でハンドラーを追加または削除すると、アプリケーションでリスト全体を検査しなければならなくなるため、パフォーマンスに大きく影響します。 アプリケーションのシナリオは決して変化している場合、 <xref:System.Windows.Media.SolidColorBrush>、維持するためのコストを支払う<xref:System.Windows.Freezable.Changed>イベント ハンドラーが不必要にします。  
  
 固定すること、<xref:System.Windows.Freezable>変更通知を維持することにリソースを展開する必要がなくなったため、パフォーマンスを向上させることができます。 次の表は、単純なのサイズを示します<xref:System.Windows.Media.SolidColorBrush>ときにその<xref:System.Windows.Freezable.IsFrozen%2A>プロパティに設定されている`true`にない場合に比べて、します。 これは 1 つのブラシを適用することを前提としています、 <xref:System.Windows.Shapes.Shape.Fill%2A> 10 プロパティ<xref:System.Windows.Shapes.Rectangle>オブジェクト。  
  
|**状態**|**Size**|  
|---------------|--------------|  
|固定されています。 <xref:System.Windows.Media.SolidColorBrush>|212 バイト|  
|固定されていません。 <xref:System.Windows.Media.SolidColorBrush>|972 バイト|  
  
 この概念の例を次のコード サンプルに示します。  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>固定されていない Freezable の Changed ハンドラーによってオブジェクトが維持される可能性がある  
 オブジェクトに渡すデリゲート、<xref:System.Windows.Freezable>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントは、そのオブジェクトへの参照では実質的にします。 したがって、<xref:System.Windows.Freezable.Changed>イベント ハンドラーが維持オブジェクト予想以上に長くします。 リッスンするように登録されているオブジェクトのクリーンアップを実行するときに、<xref:System.Windows.Freezable>オブジェクトの<xref:System.Windows.Freezable.Changed>イベントがオブジェクトを解放する前にそのデリゲートを削除するために不可欠です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] フック<xref:System.Windows.Freezable.Changed>イベント内部でします。 実行するすべての依存関係プロパティなど、<xref:System.Windows.Freezable>値がリッスンするよう<xref:System.Windows.Freezable.Changed>イベントに自動的にします。 <xref:System.Windows.Shapes.Shape.Fill%2A>プロパティを<xref:System.Windows.Media.Brush>、この概念を説明します。  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 代入時に`myBrush`に`myRectangle.Fill`を指す委任、<xref:System.Windows.Shapes.Rectangle>オブジェクトに追加されます、<xref:System.Windows.Media.SolidColorBrush>オブジェクトの<xref:System.Windows.Freezable.Changed>イベント。 このため、次のコードを使用しても、`myRect` は実際にはガベージ コレクションの対象にはなりません。  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 ここでは`myBrush`も保持し`myRectangle`アライブはコールバックを起動したときに、その<xref:System.Windows.Freezable.Changed>イベント。 割り当てることに注意してください`myBrush`を<xref:System.Windows.Shapes.Shape.Fill%2A>プロパティの新しい<xref:System.Windows.Shapes.Rectangle>を別のイベント ハンドラーを単純に追加されます`myBrush`です。  
  
 削除するのには、これらの種類のオブジェクトをクリーンアップすることをお勧め、<xref:System.Windows.Media.Brush>から、<xref:System.Windows.Shapes.Shape.Fill%2A>順番を削除するには、プロパティ、<xref:System.Windows.Freezable.Changed>イベント ハンドラー。  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>ユーザー インターフェイスの仮想化  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] バリエーションも提供、<xref:System.Windows.Controls.StackPanel>自動的に「は、仮想化」のデータ バインドされた子コンテンツ要素。 ここで、"仮想化" は、どの項目を画面に表示するかに基づいて、オブジェクトのサブセットを多数のデータ項目から生成する手法を指します。 特定の時間に画面に UI 要素が少ししか表示されていない場合に多数の UI 要素を生成すると、メモリおよびプロセッサの両方に負荷がかかります。 <xref:System.Windows.Controls.VirtualizingStackPanel> (によって提供される機能を通じて<xref:System.Windows.Controls.VirtualizingPanel>) 表示されている項目を計算し、連携、<xref:System.Windows.Controls.ItemContainerGenerator>から、 <xref:System.Windows.Controls.ItemsControl> (など<xref:System.Windows.Controls.ListBox>または<xref:System.Windows.Controls.ListView>) のみ表示される項目の要素を作成します。  
  
 パフォーマンスの最適化の一環として、これらの項目のビジュアル オブジェクトは、画面に表示される場合にのみ生成または維持されます。 既にコントロールの表示可能領域にないビジュアル オブジェクトは削除される可能性があります。 これをデータの仮想化と混同しないようにしてください。データの仮想化では、すべてのデータ オブジェクトがローカル コレクションに存在するのではなく、データ オブジェクトが必要に応じてストリームされます。  
  
 次の表は、追加して、5000 のレンダリングの経過時間を示します<xref:System.Windows.Controls.TextBlock>要素を<xref:System.Windows.Controls.StackPanel>と<xref:System.Windows.Controls.VirtualizingStackPanel>です。 このシナリオでは、測定値を表すテキスト文字列をアタッチするまでの時間、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、 <xref:System.Windows.Controls.ItemsControl> panel 要素が、テキスト文字列を表示するときにオブジェクト。  
  
|**ホスト パネル**|**レンダリング時間 (ミリ秒)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [アプリケーション パフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [[テキスト]](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [パフォーマンスに関するその他の推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
