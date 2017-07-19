---
title: "チュートリアル: WPF での Windows フォーム コントロールの配置 | Microsoft Docs"
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
  - "配置 (コントロールを)"
  - "ハイブリッド アプリケーション [WPF 相互運用性]"
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# チュートリアル: WPF での Windows フォーム コントロールの配置
このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト機能を使用して、ハイブリッド アプリケーションで [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを配置する方法を示します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   既定のレイアウト設定の使用。  
  
-   コンテンツに合わせたサイズの変更。  
  
-   絶対配置の使用。  
  
-   サイズの明示的な指定。  
  
-   レイアウト プロパティの設定。  
  
-   z オーダーの制限の理解。  
  
-   ドッキング。  
  
-   可視性の設定。  
  
-   伸縮しないコントロールのホスト。  
  
-   スケーリング。  
  
-   回転。  
  
-   パディングとマージンの設定。  
  
-   動的レイアウト コンテナーの使用。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[WPF での Windows フォーム コントロールの配置のサンプル](http://go.microsoft.com/fwlink/?LinkID=159971)を参照してください。  
  
 終了すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションにおける [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] レイアウトの機能を理解できます。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## プロジェクトの作成  
  
#### プロジェクトを作成し、設定するには  
  
1.  `WpfLayoutHostingWf` という名前の WPF アプリケーション プロジェクトを作成します。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  MainWindow.xaml をダブルクリックして、XAML ビューで開きます。  
  
4.  <xref:System.Windows.Window> 要素に、次の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 名前空間の割り当てを追加します。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <xref:System.Windows.Controls.Grid> 要素で、<xref:System.Windows.Controls.Grid.ShowGridLines%2A> プロパティを `true` に設定し、5 つの行と 3 つの列を定義します。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## 既定のレイアウト設定の使用  
 既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素が、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのレイアウトを処理します。  
  
#### 既定のレイアウト設定を使用するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=fullName> コントロールが <xref:System.Windows.Controls.Canvas> に表示されます。  ホストされているコントロールはそのコンテンツに基づいてサイズ設定され、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はホストされているコントロールが収まるようにサイズ変更されます。  
  
## コンテンツに合わせたサイズの変更  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を使用すると、ホストされているコントロールのサイズは、そのコンテンツが正しく表示されるように変更されます。  
  
#### コンテンツに合わせてサイズ変更するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  長くなったテキスト文字列および大きくなったフォント サイズが正しく表示されるように 2 つの新しいボタン コントロールのサイズが変更され、ホストされているコントロールが収まるように <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のサイズが変更されます。  
  
## 絶対配置の使用  
 絶対配置を使用して、ユーザー インターフェイス \(UI\) の任意の場所に <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を配置できます。  
  
#### 絶対配置を使用するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、グリッド セルの上辺から 20 ピクセル、左辺から 20 ピクセルの位置に配置されます。  
  
## サイズの明示的な指定  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のサイズは、<xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティを使用して指定できます。  
  
#### サイズを明示的に指定するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、既定のレイアウト設定よりも小さい、幅 50 ピクセル、高さ 70 ピクセルに設定されます。  それに合わせて、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールのコンテンツが再配置されます。  
  
## レイアウト プロパティの設定  
 ホストされているコントロールにレイアウト関連のプロパティを設定する場合は、常に <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素のプロパティを使用します。  ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でホストされているコントロールにレイアウト関連プロパティを設定しても無効です。  
  
#### ホストされているコントロールでプロパティを設定した場合の結果を確認するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  ソリューション エクスプローラーで、MainWindow.xaml.  vb または MainWindow.xaml.cs をダブルクリックして、コード エディターで開きます。  
  
3.  次のコードを `MainWindow` クラス定義にコピーします。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
5.  \[Click me\] ボタンをクリックします。  `button1_Click` イベント ハンドラーは、ホストされているコントロールで <xref:System.Windows.Forms.Control.Top%2A> プロパティと <xref:System.Windows.Forms.Control.Left%2A> プロパティを設定します。  これにより、ホストされているコントロールは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素内で再配置されます。  ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。  代わりに、ホストされているコントロールは、常に <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素全体を占めます。  
  
## z オーダーの制限の理解  
 既定では<xref:System.Windows.Forms.Integration.WindowsFormsHost> の可視要素は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の他の要素の上に常に描画されz オーダーには影響しません。  18 Z 命令を有効にするには<xref:System.Windows.Interop.CompositionMode.Full> または <xref:System.Windows.Interop.CompositionMode.OutputOnly> と <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> のプロパティを調整できるように <xref:System.Windows.Forms.Integration.WindowsFormsHost> の <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> のプロパティを設定します。  
  
#### 既定の z オーダーの動作を確認するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素がラベル要素の上に描画されます。  
  
#### IsRedirected に該当する場合は z オーダーの動作を確認するには  
  
1.  次の XAML に前の z オーダーの例を次のコードに置き換えます。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     F5 キーを押してアプリケーションをビルドし、実行します。  label 要素は <xref:System.Windows.Forms.Integration.WindowsFormsHost> の要素の上に描画されます。  
  
## ドッキング  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のドッキングをサポートします。  ホストされているコントロールを <xref:System.Windows.Controls.DockPanel> 要素にドッキングするように、<xref:System.Windows.Controls.DockPanel.Dock%2A> 添付プロパティを設定します。  
  
#### ホストされているコントロールをドッキングするには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素が <xref:System.Windows.Controls.DockPanel> 要素の右側にドッキングされます。  
  
## 可視性の設定  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールを非表示にしたり、折りたたむには、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素で <xref:System.Windows.UIElement.Visibility%2A> プロパティを設定します。  コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。  コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。  
  
#### ホストされているコントロールの可視性を設定するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を非表示にするには、\[Click to make invisible\] ボタンをクリックします。  
  
5.  レイアウト全体から <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を非表示にする場合は、\[Click to collapse\] ボタンをクリックします。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールが折りたたまれ、周りの要素が再配置されて、そのスペースが使用されます。  
  
## 伸縮しないコントロールのホスト  
 一部の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは、サイズが固定され、レイアウト内の使用可能なスペースに合わせて伸縮しません。  たとえば、<xref:System.Windows.Forms.MonthCalendar> コントロールでは、固定されたスペースに月が表示されます。  
  
#### 伸縮しないコントロールをホストするには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素はグリッド行で中央揃えになりますが、使用可能なスペースに合わせて伸縮されることはありません。  ウィンドウが十分に大きい場合は、ホストされている <xref:System.Windows.Forms.MonthCalendar> コントロールによって 2 か月以上の月が表示される場合もありますが、これらは行内で中央揃えになります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウト エンジンは、使用可能なスペースに合わせたサイズ変更ができない要素を中央揃えにします。  
  
## スケーリング  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素と異なり、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは継続的にスケーリングすることはできません。  既定では<xref:System.Windows.Forms.Integration.WindowsFormsHost> の要素は可能であればホストされているコントロールをスケーリングします。  完全なスケーリングを有効にするには<xref:System.Windows.Interop.CompositionMode.Full> または <xref:System.Windows.Interop.CompositionMode.OutputOnly> と <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> のプロパティを調整できるように <xref:System.Windows.Forms.Integration.WindowsFormsHost> の <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> のプロパティを設定します。  
  
#### ホストされているコントロールを既定の動作を使用してスケーリングするには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  ホストされているコントロールとその周りの要素は、ファクター 0.5 でスケーリングされますが、  ホストされているコントロールのフォントはスケーリングされません。  
  
#### ホストされているコントロールを IsRedirected を true に設定してスケーリングするには  
  
1.  次の XAML にスケーリング前の例のに置き換えます。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  ホストされているコントロールその周りの要素とホストされているコントロールのフォントはファクター 0.5 でスケーリングされます。  
  
## 回転  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素とは異なり、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールは回転をサポートしません。  既定では<xref:System.Windows.Forms.Integration.WindowsFormsHost> の要素は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の他の要素と回転変換が適用されても。  回転値が 180 度の場合を除き、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> イベントが発生します。  への回転の角度を有効にするには<xref:System.Windows.Interop.CompositionMode.Full> または <xref:System.Windows.Interop.CompositionMode.OutputOnly> と <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> のプロパティを調整できるように <xref:System.Windows.Forms.Integration.WindowsFormsHost> の <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> のプロパティを設定します。  
  
#### ハイブリッド アプリケーションでの回転の結果を確認するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。  要素を表示するためにウィンドウのサイズを変更することが必要になる場合があります。  
  
#### IsRedirected に該当する場合はハイブリッド アプリケーションで回転の効果を確認します。  
  
1.  次の XAML に前の回転の例を次のコードに置き換えます。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  ホストされているコントロールは回転します。  <xref:System.Windows.Media.RotateTransform.Angle%2A> のプロパティを任意の値に設定できることに注意してください。  要素を表示するためにウィンドウのサイズを変更することが必要になる場合があります。  
  
## パディングとマージンの設定  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトのパディングとマージンは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のパディングとマージンに似ています。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素で <xref:System.Windows.Controls.Control.Padding%2A> プロパティと <xref:System.Windows.FrameworkElement.Margin%2A> プロパティを設定するだけです。  
  
#### ホストされているコントロールのパディングとマージンを設定するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。  パディングとマージンの設定が、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で適用される場合と同じように、ホストされている [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールに適用されます。  
  
## 動的レイアウト コンテナーの使用  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]は、2 つの動的レイアウト コンテナー、<xref:System.Windows.Forms.FlowLayoutPanel> と <xref:System.Windows.Forms.TableLayoutPanel> を提供します。  これらのコンテナーは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトで使用することもできます。  
  
#### 動的レイアウト コンテナーを使用するには  
  
1.  次の XAML を <xref:System.Windows.Controls.Grid> 要素にコピーします。  
  
     [!code-xml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  コンストラクターに `InitializeFlowLayoutPanel` メソッドの呼び出しを追加します。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は <xref:System.Windows.Controls.DockPanel> 全体を占め、<xref:System.Windows.Forms.FlowLayoutPanel> はその子コントロールを既定の <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> に配置します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [WPF での Windows フォーム コントロールの配置のサンプル](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)