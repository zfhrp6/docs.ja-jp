---
title: "チュートリアル: WPF での Windows フォーム コントロールの配置"
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
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480d61f6ca2aa67e0de48030655a6368c70554f4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>チュートリアル: WPF での Windows フォーム コントロールの配置
このチュートリアルで使用する方法[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を整列するレイアウト機能[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ハイブリッド アプリケーションでのコントロールです。  
  
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
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WPF サンプルでの Windows フォーム コントロールの配置](http://go.microsoft.com/fwlink/?LinkID=159971)です。  
  
 理解する必要が完了したら、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]レイアウトの機能で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションです。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`WpfLayoutHostingWf`です。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  MainWindow.xaml をダブルクリックして、XAML ビューで開きます。  
  
4.  <xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間のマッピング。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <xref:System.Windows.Controls.Grid>要素セット、<xref:System.Windows.Controls.Grid.ShowGridLines%2A>プロパティを`true`5 つの行および 3 つの列を定義します。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>既定のレイアウト設定の使用  
 既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は、ホスト型のレイアウトで処理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
#### <a name="to-use-default-layout-settings"></a>既定のレイアウト設定を使用するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType>コントロールに表示され、<xref:System.Windows.Controls.Canvas>です。 ホストされるコントロールは、その内容に基づいてサイズでは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素のサイズは、ホストされるコントロールに対応します。  
  
## <a name="sizing-to-content"></a>コンテンツに合わせたサイズの変更  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の内容を正しく表示するため、ホストされるコントロールがサイズを調整することを確認します。  
  
#### <a name="to-size-to-content"></a>コンテンツに合わせてサイズ変更するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 2 つの新しいボタン コントロールのフォント サイズを大きく、長いテキスト文字列が正しく表示するサイズは、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストされるコントロールに合わせて要素のサイズが変更されます。  
  
## <a name="using-absolute-positioning"></a>絶対配置の使用  
 絶対配置を使用する配置、<xref:System.Windows.Forms.Integration.WindowsFormsHost>任意の場所で、ユーザー インターフェイス (UI) 要素です。  
  
#### <a name="to-use-absolute-positioning"></a>絶対配置を使用するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>のグリッド セルの上にあるから 20 ピクセル、左端から 20 ピクセル要素が配置されます。  
  
## <a name="specifying-size-explicitly"></a>サイズの明示的な指定  
 サイズを指定することができます、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を使用して、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティです。  
  
#### <a name="to-specify-size-explicitly"></a>サイズを明示的に指定するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素はこれが既定のレイアウトの設定よりも小さい 70 ピクセル、高さ、幅 50 ピクセルのサイズに設定します。 内容、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールがそれに応じて再配置します。  
  
## <a name="setting-layout-properties"></a>レイアウト プロパティの設定  
 常のプロパティを使用してホストされるコントロールにレイアウトに関連するプロパティを設定、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 ホストされているコントロールで直接レイアウト プロパティを設定すると、予期しない結果になります。  
  
 ホストされるコントロールのレイアウトに関連するプロパティを設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も何も起こりません。  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>ホストされているコントロールでプロパティを設定した場合の結果を確認するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  ソリューション エクスプ ローラーで、MainWindow.xaml をダブルクリックします。 vb または MainWindow.xaml.cs コード エディターで開きます。  
  
3.  次のコードをコピー、`MainWindow`クラス定義です。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
5.  クリックして、 **Click me**ボタンをクリックします。 `button1_Click`イベント ハンドラーの設定、<xref:System.Windows.Forms.Control.Top%2A>と<xref:System.Windows.Forms.Control.Left%2A>ホストされるコントロールのプロパティです。 これにより、ホストされるコントロール内の位置を変更する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 ホストは同じ画面領域を維持しますが、ホストされているコントロールはクリップされます。 代わりに、ホストされるコントロールの入力は常に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
## <a name="understanding-z-order-limitations"></a>z オーダーの制限の理解  
 既定では、表示されている<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素は常に他の上に描画[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、および、z オーダーで影響を受けません。 Z オーダーを有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。  
  
#### <a name="to-see-the-default-z-order-behavior"></a>既定の z オーダーの動作を確認するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>ラベル要素上で要素を描画します。  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a>IsRedirected が true の場合に z オーダーの動作を確認するには  
  
1.  前の z オーダーの例を次の XAML に置き換えます。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     F5 キーを押してアプリケーションをビルドし、実行します。 経由で、label 要素が描画された、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
## <a name="docking"></a>ドッキング  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をサポートしている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ドッキングします。 設定、<xref:System.Windows.Controls.DockPanel.Dock%2A>添付プロパティでホストされるコントロールをドッキングするのには、<xref:System.Windows.Controls.DockPanel>要素。  
  
#### <a name="to-dock-a-hosted-control"></a>ホストされているコントロールをドッキングするには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>の右側に要素がドッキングされている、<xref:System.Windows.Controls.DockPanel>要素。  
  
## <a name="setting-visibility"></a>可視性の設定  
 ことができます、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]非表示を制御したり、設定して折りたたむこと、<xref:System.Windows.UIElement.Visibility%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。 コントロールを非表示にすると、そのコントロールは表示されませんが、レイアウト空間は使用されます。 コントロールを折りたたむと、そのコントロールは表示されず、レイアウト空間も使用されません。  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>ホストされているコントロールの可視性を設定するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
4.  をクリックして、**を非表示 をクリックします。**を作成するボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素を非表示します。  
  
5.  をクリックして、**を折りたたみます**を非表示にするにはボタン、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素をレイアウトから完全です。 ときに、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールが折りたたまれている、周囲の要素がその領域を占有するように再配置します。  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>伸縮しないコントロールのホスト  
 いくつか[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールのサイズが固定されているし、レイアウトで使用可能なスペースを埋めます伸縮しませんしないでください。 たとえば、<xref:System.Windows.Forms.MonthCalendar>コントロールでは、固定された間隔で 1 か月が表示されます。  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>伸縮しないコントロールをホストするには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がグリッド行の中央に配置が、空き領域の塗りつぶしに拡張されていません。 ウィンドウが十分な大きさの場合、ホストによって表示される 2 つ以上の月を参照してください可能性があります<xref:System.Windows.Forms.MonthCalendar>コントロールが、これらが、行の中央に配置します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウト エンジンの中心が空き領域の塗りつぶしのサイズが変更できない要素。  
  
## <a name="scaling"></a>スケーリング  
 異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、ほとんど[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールにスケーラブルな継続的にはできません。 既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素可能な場合は、ホストされるコントロールのスケールを設定します。  本格的なスケーリングを有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>既定の動作を使用してホストされているコントロールをスケーリングするには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールとその周りの要素は、0.5 倍でスケーリングされます。 ただし、ホストされているコントロールのフォントはスケーリングされません。  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a>IsRedirected を true に設定してホストされているコントロールをスケーリングするには  
  
1.  前述のスケーリングの例を、次の XAML に書き換えます。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロール、その周りの要素、ホストされているコントロールのフォントは 0.5 倍でスケーリングされます。  
  
## <a name="rotating"></a>回転  
 異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールでは回転をサポートしていません。 既定では、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素が他の回転させません[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]回転変換を適用するときの要素。 180 度を発生させます以外の値を回転、<xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>イベント。  任意の角度に回転を有効にするには設定、<xref:System.Windows.Interop.HwndHost.IsRedirected%2A>のプロパティ、<xref:System.Windows.Forms.Integration.WindowsFormsHost>を true に、<xref:System.Windows.Interop.HwndHost.CompositionMode%2A>プロパティを<xref:System.Windows.Interop.CompositionMode.Full>または<xref:System.Windows.Interop.CompositionMode.OutputOnly>です。  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>ハイブリッド アプリケーションでの回転の効果を確認するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールは回転しませんが、その周りの要素は 180 度の角度で回転します。 要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a>IsRedirected が true の場合に、ハイブリッド アプリケーションで回転の効果を確認するには  
  
1.  前述の回転の例を、次の XAML に書き換えます。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 ホストされているコントロールが回転します。  なお、<xref:System.Windows.Media.RotateTransform.Angle%2A>プロパティは、任意の値に設定することができます。 要素を表示するためにウィンドウのサイズを変更する必要がある場合があります。  
  
## <a name="setting-padding-and-margins"></a>パディングとマージンの設定  
 パディングと余白の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトは、埋め込みと余白のような[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]します。 設定するだけ、<xref:System.Windows.Controls.Control.Padding%2A>と<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素。  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>ホストされているコントロールのパディングとマージンを設定するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  F5 キーを押してアプリケーションをビルドし、実行します。 パディングと余白の設定が適用されるホストに[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]で、適用される同じ方法でコントロール[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]です。  
  
## <a name="using-dynamic-layout-containers"></a>動的レイアウト コンテナーの使用  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]2 つの動的レイアウト コンテナーを提供<xref:System.Windows.Forms.FlowLayoutPanel>と<xref:System.Windows.Forms.TableLayoutPanel>です。 これらのコンテナーを使用することもできます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]レイアウトです。  
  
#### <a name="to-use-a-dynamic-layout-container"></a>動的レイアウト コンテナーを使用するには  
  
1.  次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素。  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードをクラス定義にコピーします。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  呼び出しを追加、`InitializeFlowLayoutPanel`コンス トラクターのメソッドです。  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  F5 キーを押してアプリケーションをビルドし、実行します。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の設定、 <xref:System.Windows.Controls.DockPanel>、および<xref:System.Windows.Forms.FlowLayoutPanel>、既定では、その子コントロールを配置<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WindowsFormsHost 要素のレイアウトに関する考慮事項](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [WPF のサンプルでのフォーム コントロールのウィンドウの配置](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
