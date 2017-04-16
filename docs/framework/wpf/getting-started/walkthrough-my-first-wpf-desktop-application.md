---
title: "チュートリアル: WPF の概要 | Microsoft Docs"
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
  - "はじめに, WPF"
  - "WPF, はじめに"
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: 71
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 68
---
# チュートリアル: WPF の概要
<a name="introduction"></a> このチュートリアルでは、ほとんどの [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションに共通の要素を含む [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの開発の概要について説明します。このような共通の要素には、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] マークアップ、分離コード、アプリケーション定義、コントロール、レイアウト、データ バインディング、スタイルなどがあります。  
  
 このチュートリアルでは、次の手順に従って、簡単な [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを作成していきます。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を定義して、アプリケーションの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の外観を設計します。  
  
-   アプリケーションの動作を構築するコードを記述します。  
  
-   アプリケーション定義を作成して、アプリケーションを管理します。  
  
-   コントロールの追加およびレイアウトの作成を行い、アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を構成します。  
  
-   アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 全体で一貫性のある外観を作成するためのスタイルを作成します。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をデータにバインドして、データから [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を設定し、データと [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の同期を維持します。  
  
 このチュートリアルの最後には、ユーザーが選択した個人の経費報告書を表示できる、スタンドアロンの [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] アプリケーションが完成します。  このアプリケーションは、ブラウザー スタイルのウィンドウでホストされる複数の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ページから構成されます。  
  
 このチュートリアルの構築に使用するサンプル コードは、[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] と [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] の両方が用意されています。[WPF アプリケーションの構築の概要](http://go.microsoft.com/fwlink/?LinkID=160008)に関する記述を参照してください。  
  
<a name="Requirements"></a>   
## 必要条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]  
  
 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のインストールの詳細については、「[Visual Studio のインストール](../Topic/Install%20Visual%20Studio%202015.md)」を参照してください。  
  
<a name="Create_The_Application_Code_Files"></a>   
## アプリケーション プロジェクトの作成  
 このセクションでは、アプリケーション定義、2 つのページ、および 1 つのイメージが含まれるアプリケーション インフラストラクチャを作成します。  
  
1.  Visual Basic または Visual C\# で `ExpenseIt` という名前の新しい WPF アプリケーション プロジェクトを作成します。  詳細については、「[方法 : 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)」を参照してください。  
  
    > [!NOTE]
    >  このチュートリアルでは、.NET Framework 4 で使用できる <xref:System.Windows.Controls.DataGrid> コントロールを使用します。  プロジェクトで .NET Framework 4 を対象としてください。  詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
2.  Application.xaml \(Visual Basic\) または App.xaml \(C\#\) を開きます。  
  
     この [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションとすべてのアプリケーション リソースを定義します。また、このファイルは、アプリケーションの起動時に自動的に表示する [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を指定するためにも使用されます。この例では、MainWindow.xaml を指定しています。  
  
     Visual Basic では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は次のようになります。  
  
     [!code-xml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     C\# では、次のようになります。  
  
     [!code-xml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3.  MainWindow.xaml を開きます。  
  
     この [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルは、アプリケーションのメイン ウィンドウであり、ページで作成されたコンテンツを表示します。  <xref:System.Windows.Window> クラスは、ウィンドウのプロパティ \(タイトル、サイズ、アイコンなど\) を定義し、イベント \(ウィンドウを閉じたり非表示にしたりするなど\) を処理します。  
  
4.  <xref:System.Windows.Window> 要素を <xref:System.Windows.Navigation.NavigationWindow> に変更します。  
  
     このアプリケーションでは、ユーザー操作に応じてさまざまなコンテンツに移動します。  そのため、メインの <xref:System.Windows.Window> を <xref:System.Windows.Navigation.NavigationWindow> に変更する必要があります。  <xref:System.Windows.Navigation.NavigationWindow> は、<xref:System.Windows.Window> のすべてのプロパティを継承します。  XAML ファイル内の <xref:System.Windows.Navigation.NavigationWindow> 要素は、<xref:System.Windows.Navigation.NavigationWindow> クラスのインスタンスを作成します。  詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
5.  <xref:System.Windows.Navigation.NavigationWindow> 要素の次のプロパティを変更します。  
  
    -   <xref:System.Windows.Window.Title%2A> プロパティを "ExpenseIt" に設定します。  
  
    -   <xref:System.Windows.FrameworkElement.Width%2A> プロパティを 500 ピクセルに設定します。  
  
    -   <xref:System.Windows.FrameworkElement.Height%2A> プロパティを 350 ピクセルに設定します。  
  
    -   <xref:System.Windows.Navigation.NavigationWindow> タグの間の <xref:System.Windows.Controls.Grid> 要素を削除します。  
  
     Visual Basic では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は次のようになります。  
  
     [!code-xml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     C\# では、次のようになります。  
  
     [!code-xml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6.  MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。  
  
     このファイルは、MainWindow.xaml で宣言されたイベントを処理するコードを含む分離コード ファイルです。  このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。  
  
7.  C\# を使用している場合は、`MainWindow` クラスが <xref:System.Windows.Navigation.NavigationWindow> から派生するように変更します。  
  
     Visual Basic では、XAML でウィンドウを変更すると自動的にこの処理が行われます。  
  
     コードは、次のようになります。  
  
     [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
     [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
<a name="add_files_to_the_application"></a>   
## アプリケーションへのファイルの追加  
 このセクションでは、2 つのページと 1 つのイメージをアプリケーションに追加します。  
  
1.  `ExpenseItHome.xaml` というプロジェクトに、新しいページ \(WPF\) を追加します。  詳細については、「[方法 : 新しい項目を WPF プロジェクトに追加する](http://msdn.microsoft.com/ja-jp/17e6b238-fc32-4385-98ef-2f66ca09d9ad)」を参照してください。  
  
     このページは、アプリケーションの起動時に最初に表示されるページです。  ここに個人の一覧が表示され、ユーザーは経費報告書の表示対象となる個人を選択できます。  
  
2.  ExpenseItHome.xaml を開きます。  
  
3.  <xref:System.Windows.Controls.Page.Title%2A> を "ExpenseIt \- Home" に設定します。  
  
     Visual Basic では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は次のようになります。  
  
     [!code-xml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     C\# では、次のようになります。  
  
     [!code-xml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4.  MainWindow.xaml を開きます。  
  
5.  <xref:System.Windows.Navigation.NavigationWindow> の <xref:System.Windows.Navigation.NavigationWindow.Source%2A> プロパティを "ExpenseItHome.xaml" に設定します。  
  
     これにより、ExpenseItHome.xaml は、アプリケーションの起動時に最初に表示されるページに設定されます。  Visual Basic では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は次のようになります。  
  
     [!code-xml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     C\# では、次のようになります。  
  
     [!code-xml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6.  `ExpenseReportPage.xaml` というプロジェクトに、新しいページ \(WPF\) を追加します。  
  
     このページには、ExpenseItHome.xaml で選択された個人の経費報告書が表示されます。  
  
7.  ExpenseReportPage.xaml を開きます。  
  
8.  <xref:System.Windows.Controls.Page.Title%2A> を "ExpenseIt \- View Expense" に設定します。  
  
     Visual Basic では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は次のようになります。  
  
     [!code-xml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     C\# では、次のようになります。  
  
     [!code-xml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. ExpenseItHome.xaml.vb と ExpenseReportPage.xaml.vb を開くか、または ExpenseItHome.xaml.cs と ExpenseReportPage.xaml.cs を開きます。  
  
     新しいページ ファイルを作成すると、分離コード ファイルが自動的に作成されます。  これらの分離コード ファイルでは、ユーザー入力に応答するためのロジックを処理します。  
  
     コードは、次のようになります。  
  
     [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
     [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
     [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
     [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. watermark.png という名前のイメージをプロジェクトに追加します。  独自のイメージを作成することも、サンプル コードからファイルをコピーすることもできます。  詳細については、「[NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/ja-jp/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)」を参照してください。  
  
<a name="Build_The_Application"></a>   
## アプリケーションのビルドと実行  
 このセクションでは、アプリケーションをビルドして実行します。  
  
1.  F5 キーを押すか、**\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックして、アプリケーションをビルドして実行します。  
  
     次の図は、<xref:System.Windows.Navigation.NavigationWindow> ボタンのあるアプリケーションを示しています。  
  
     ![ExpenseIt のサンプルのスクリーンショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2.  アプリケーションを閉じて [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] に戻ります。  
  
<a name="Add_Layout"></a>   
## レイアウトの作成  
 レイアウトは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素の配置を整えるほか、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のサイズが変更された場合に各要素のサイズと位置を管理します。  通常、レイアウトを作成するには、次のレイアウト コントロールのいずれかを使用します。  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 これらの各レイアウト コントロールは、その子要素に対して特別な種類のレイアウトをサポートします。  ExpenseIt のページはサイズの変更が可能で、各ページの要素は縦にも横にも他の要素と揃えられています。  したがって、このアプリケーションにとっては <xref:System.Windows.Controls.Grid> が最適なレイアウト要素です。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Panel> 要素の詳細については、「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」を参照してください。  レイアウトの詳細については、「[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)」を参照してください。  
  
 このセクションでは、ExpenseItHome.xaml の <xref:System.Windows.Controls.Grid> に列と行の定義を追加して、10 ピクセルのマージンを持つ 3 行 1 列のテーブルを作成します。  
  
1.  ExpenseItHome.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.Grid> 要素の <xref:System.Windows.FrameworkElement.Margin%2A> プロパティを "10,0,10,10" に設定します。"10,0,10,10" の各値は、左、上、右、下のマージンに対応しています。  
  
3.  <xref:System.Windows.Controls.Grid> タグの間に次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を追加し、行と列の定義を作成します。  
  
     [!code-xml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     2 つの行の <xref:System.Windows.Controls.RowDefinition.Height%2A> は <xref:System.Windows.GridLength.Auto%2A> に設定されます。これは、行のサイズがその行に含まれるコンテンツに基づいて設定されることを意味します。  既定では、<xref:System.Windows.Controls.RowDefinition.Height%2A> は <xref:System.Windows.GridUnitType> サイズ値です。つまり、行は、使用可能なスペースの加重比率で示されます。  たとえば、2 つの行それぞれの高さが "\*" の場合、各行の高さは、使用可能なスペースの半分です。  
  
     <xref:System.Windows.Controls.Grid> は、次の XAML のようになります。  
  
     [!code-xml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
<a name="Add_Controls"></a>   
## コントロールの追加  
 このセクションでは、ホーム ページの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新して個人の一覧を表示します。ユーザーは、この一覧から選択して、特定の個人の経費報告書を表示できます。  コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。  詳細については、「[コントロール](../../../../docs/framework/wpf/controls/index.md)」を参照してください。  
  
 この [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を作成するために、ExpenseItHome.xaml に次の要素を追加します。  
  
-   <xref:System.Windows.Controls.ListBox> \(個人の一覧を表示します\)。  
  
-   <xref:System.Windows.Controls.Label> \(一覧のヘッダーとして使用します\)。  
  
-   <xref:System.Windows.Controls.Button> \(クリック時に、一覧で選択された個人の経費報告書を表示します\)。  
  
 各コントロールは、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=fullName> 添付プロパティを設定することで、<xref:System.Windows.Controls.Grid> の行に配置されます。  添付プロパティの詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
1.  ExpenseItHome.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.Grid> タグの間に次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を追加します。  
  
     [!code-xml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3.  アプリケーションをビルドして実行します。  
  
 次の図は、このセクションの XAML で作成されたコントロールを示しています。  
  
 ![ExpenseIt のサンプルのスクリーンショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
<a name="Add_an_Image"></a>   
## イメージとタイトルの追加  
 このセクションでは、ホーム ページの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新して、イメージとページ タイトルを表示します。  
  
1.  ExpenseItHome.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> に、<xref:System.Windows.Controls.ColumnDefinition.Width%2A> が 230 ピクセルで固定された新しい列を追加します。  
  
     [!code-xml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3.  <xref:System.Windows.Controls.Grid.RowDefinitions%2A> に新しい行を追加します。  
  
     [!code-xml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4.  <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=fullName> を 1 に設定して、コントロールを 2 列目に移動します。  <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=fullName> を 1 増加して、各コントロールを 1 行下へ移動します。  
  
     [!code-xml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5.  <xref:System.Windows.Controls.Grid> の <xref:System.Windows.Controls.Panel.Background%2A> を watermark.png イメージ ファイルに設定します。  
  
     [!code-xml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6.  <xref:System.Windows.Controls.Border> の前に、ページのタイトルになる "View Expense Report" というコンテンツが指定された <xref:System.Windows.Controls.Label> を追加します。  
  
     [!code-xml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7.  アプリケーションをビルドして実行します。  
  
 次の図は、このセクションの結果を示しています。  
  
 ![ExpenseIt のサンプルのスクリーンショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
<a name="Add_Code_to_Process_Events"></a>   
## イベントを処理するコードの追加  
  
1.  ExpenseItHome.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.Button> 要素に <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーを追加します。  詳細については、「[方法 : 単純なイベント ハンドラーを作成する](http://msdn.microsoft.com/ja-jp/b1456e07-9dec-4354-99cf-18666b64f480)」を参照してください。  
  
     [!code-xml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3.  ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs を開きます。  
  
4.  <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーに次のコードを追加します。これにより、ウィンドウが ExpenseReportPage.xaml ファイルに移動します。  
  
     [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
     [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
<a name="Create_the_UI_for_Pane2"></a>   
## ExpenseReportPage の UI の作成  
 ExpenseReportPage.xaml には、ExpenseItHome.xaml で選択した個人の経費報告書が表示されます。  このセクションでは、コントロールを追加して、ExpenseReportPage.xaml の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を作成します。  また、さまざまな [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素の背景と塗りつぶしの色も追加します。  
  
1.  ExpenseReportPage.xaml を開きます。  
  
2.  <xref:System.Windows.Controls.Grid> タグの間に次の XAML を追加します。  
  
     この UI は、<xref:System.Windows.Controls.DataGrid> で表示されるレポート データ以外は、ExpenseItHome.xaml で作成した UI に似ています。  
  
     [!code-xml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3.  アプリケーションをビルドして実行します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Controls.DataGrid> が見つからないか存在しないエラーが発生した場合は、プロジェクトで .NET Framework 4 を対象としてください。  詳細については、「[方法: .NET Framework のバージョンをターゲットにする](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)」を参照してください。  
  
4.  **\[View\]** をクリックします。  
  
     経費報告書のページが表示されます。  
  
 ExpenseReportPage.xaml に追加された [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を次の図に示します。  "戻る" ナビゲーション ボタンが有効になっていることに注意してください。  
  
 ![ExpenseIt のサンプルのスクリーンショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
<a name="Add_Code_to_Style_a_Control"></a>   
## コントロールのスタイル設定  
 多くの場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] では、要素の種類が同じであれば、外観もすべて同じになります。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] では、複数の要素間で外観を再利用できるように、スタイルが使用されます。  スタイルの再利用性により、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の作成と管理が簡略化されます。  スタイルの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  このセクションでは、これまでの手順で定義した要素ごとの属性をスタイルに置き換えます。  
  
1.  Application.xaml または App.xaml を開きます。  
  
2.  <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> タグの間に次の XAML を追加します。  
  
     [!code-xml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     この [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、次のスタイルが追加されます。  
  
    -   `headerTextStyle`: ページ タイトルの <xref:System.Windows.Controls.Label> を書式設定します。  
  
    -   `labelStyle`: <xref:System.Windows.Controls.Label> コントロールを書式設定します。  
  
    -   `columnHeaderStyle`: <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> を書式設定します。  
  
    -   `listHeaderStyle`: 一覧のヘッダーの <xref:System.Windows.Controls.Border> コントロールを書式設定します。  
  
    -   `listHeaderTextStyle`: 一覧のヘッダーの <xref:System.Windows.Controls.Label> を書式設定します。  
  
    -   `buttonStyle`: ExpenseItHome.xaml の <xref:System.Windows.Controls.Button> を書式設定します。  
  
     スタイルは、<xref:System.Windows.Application.Resources%2A?displayProperty=fullName> プロパティ要素のリソースであり、子でもあります。  ここでは、スタイルはアプリケーション内のすべての要素に適用されます。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションでリソースを使用する例については、「[アプリケーション リソースを使用する](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)」を参照してください。  
  
3.  ExpenseItHome.xaml を開きます。  
  
4.  <xref:System.Windows.Controls.Grid> 要素間のすべての内容を次の XAML に置き換えます。  
  
     [!code-xml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、スタイルを適用することにより、削除されて置き換えられます。  たとえば、`headerTextStyle` は、"View Expense Report" という <xref:System.Windows.Controls.Label> に適用されます。  
  
5.  ExpenseReportPage.xaml を開きます。  
  
6.  <xref:System.Windows.Controls.Grid> 要素間のすべての内容を次の XAML に置き換えます。  
  
     [!code-xml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     これにより、<xref:System.Windows.Controls.Label> 要素と <xref:System.Windows.Controls.Border> 要素にスタイルが追加されます。  
  
7.  アプリケーションをビルドして実行します。  
  
     このセクションで [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を追加した後も、アプリケーションの外観はスタイルによる更新の前と変わりません。  
  
<a name="Bind_Data_to_a_Control"></a>   
## コントロールへのデータのバインド  
 このセクションでは、さまざまなコントロールにバインドされる [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] データを作成します。  
  
1.  ExpenseItHome.xaml を開きます。  
  
2.  開始の <xref:System.Windows.Controls.Grid> 要素の後に、各個人のデータを含む <xref:System.Windows.Data.XmlDataProvider> を作成する次の XAML を追加します。  
  
     データは <xref:System.Windows.Controls.Grid> リソースとして作成されます。  通常、これはファイルとして読み込まれますが、わかりやすくするために、データをインラインで追加しています。  
  
     [!code-xml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3.  <xref:System.Windows.Controls.Grid> リソースでは、次の <xref:System.Windows.DataTemplate> を追加します。これにより、<xref:System.Windows.Controls.ListBox> にデータを表示する方法が定義されます。  データ テンプレートの詳細については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。  
  
     [!code-xml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4.  既存の <xref:System.Windows.Controls.ListBox> を次の XAML に置き換えます。  
  
     [!code-xml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     この XAML は、<xref:System.Windows.Controls.ListBox> の <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティをデータ ソースにバインドし、データ テンプレートを <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> として適用します。  
  
<a name="Connect_Data_to_Controls"></a>   
## コントロールへのデータの接続  
 このセクションでは、ExpenseItHome.xaml ページ上の個人の一覧で選択されている現在の項目を取得し、その参照を `ExpenseReportPage` のコンストラクターに渡してインスタンス化するコードを作成します。  `ExpenseReportPage` は、渡された項目を使用してデータ コンテキストを設定します。この項目が、ExpenseReportPage.xaml で定義されたコントロールのバインド先になります。  
  
1.  ExpenseReportPage.xaml.vb または ExpenseReportPage.xaml.cs を開きます。  
  
2.  オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。  
  
     [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
     [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3.  ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs を開きます。  
  
4.  選択した個人の経費報告書データを渡す新しいコンストラクターを呼び出すように <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーを変更します。  
  
     [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
     [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
<a name="Add_Style_to_Data"></a>   
## データ テンプレートを使用したデータのスタイル設定  
 このセクションでは、データ テンプレートを使用して、データ バインド リスト内の各項目の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新します。  
  
1.  ExpenseReportPage.xaml を開きます。  
  
2.  "Name" および "Department" の <xref:System.Windows.Controls.Label> 要素の内容を適切なデータ ソース プロパティにバインドします。  データ バインディングの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
     [!code-xml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3.  <xref:System.Windows.Controls.Grid> 要素を開いたら、経費報告書データの表示方法を定義する、次のデータ テンプレートを追加します。  
  
     [!code-xml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4.  経費報告書データを表示する <xref:System.Windows.Controls.DataGrid> 列にテンプレートを適用します。  
  
     [!code-xml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5.  アプリケーションをビルドして実行します。  
  
6.  個人を選択し、\[**View**\] をクリックします。  
  
 次の図は、コントロール、レイアウト、スタイル、データ バインド、およびデータ テンプレートが適用された ExpenseIt アプリケーションの両方のページを示しています。  
  
 ![ExpenseIt のサンプルのスクリーンショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
<a name="Best_Practices"></a>   
## ベスト プラクティス  
 このサンプルでは、WPF の特定の機能を示します。そのため、アプリケーション開発のベスト プラクティスに従っていません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] と [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] のアプリケーション開発ベスト プラクティスの包括的な説明については、適宜、次のトピックを参照してください。  
  
-   ユーザー補助 \- 「[ユーザー補助のベスト プラクティス](../../../../docs/framework/ui-automation/accessibility-best-practices.md)」  
  
-   セキュリティ \- 「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」  
  
-   ローカリゼーション \- 「[WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)」  
  
-   パフォーマンス \- 「[WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)」  
  
<a name="Whats_Next"></a>   
## 次の内容  
 ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] を使用して [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を自由に作成する多くの方法を学習しました。  データ バインドされた [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] アプリケーションの基本的なビルド ブロックについて幅広く説明してきました。  このトピックですべてを網羅したわけではありませんが、このトピックに示した方法以外にも独自の方法を発見できる可能性があります。  
  
 WPF アーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。  
  
-   [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
  
 アプリケーションの作成の詳細については、次のトピックを参照してください。  
  
-   [アプリケーション開発](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [コントロール](../../../../docs/framework/wpf/controls/index.md)  
  
-   [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## 参照  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [スタイルおよびテンプレート](../../../../docs/framework/wpf/controls/styles-and-templates.md)