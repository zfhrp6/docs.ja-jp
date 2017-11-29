---
title: "チュートリアル: 最初 WPF デスクトップ アプリケーション"
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
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9818231a68f5c2ac2a6852f27e4876baa9728e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>チュートリアル: 最初 WPF デスクトップ アプリケーション
このチュートリアルでは、開発の概要については、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]多くに共通要素を含むアプリケーション[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーション:[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップ、分離コード、アプリケーション定義、コントロール、レイアウト、データ バインディング、およびスタイル。 
  
 このチュートリアルで説明する、簡単な開発[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションは、次の手順を使用します。 
  
-   定義する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、アプリケーションの外観をデザインする[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 
  
-   アプリケーションの動作を構築するコードを記述します。 
  
-   アプリケーションを管理するためのアプリケーション定義を作成します。 
  
-   コントロールを追加して、アプリケーションを作成するレイアウトを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 
  
-   アプリケーションの全体で一貫した外観を作成するスタイルを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 
  
-   バインディング、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]両方にデータを設定、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]データとデータを維持するからと[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]同期します。 
  
 スタンドアロンのチュートリアルの目的は、構築した[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]アプリケーションを選択したユーザーの経費報告書を表示することができます。 アプリケーションは、いくつかの構成は[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ブラウザー スタイルのウィンドウでホストされているページ。 
  
 このチュートリアルの構築に使用するサンプル コードは両方の使用可能な[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]と[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]で[Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008)です。 

## <a name="prerequisites"></a>必須コンポーネント  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)] 以降

Visual Studio の最新バージョンのインストールに関する詳細については、次を参照してください。 [Visual Studio インストール](/visualstudio/install/install-visual-studio)です。
  
## <a name="creating-the-application-project"></a>アプリケーション プロジェクトの作成  
 このセクションでは、アプリケーション定義、2 つのページ、および 1 つのイメージが含まれる、アプリケーション インフラストラクチャを作成します。 
  
1. Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`ExpenseIt`です。 詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。 
  
    > [!NOTE]
    >  このチュートリアルでは、 <xref:System.Windows.Controls.DataGrid> .NET Framework 4 で使用可能なコントロールです。 プロジェクトの対象 .NET Framework 4 であることを確認して以降であります。 詳細については、次を参照してください。[する方法: .NET Framework のバージョンを対象に](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)です。 
  
2. Application.xaml (Visual Basic) または App.xaml (C#) を開きます。 
  
     これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルを定義、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションとアプリケーション リソース。 使用することもこのファイルを指定する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]表示は、アプリケーションの起動時に自動的にこの場合、MainWindow.xaml です。 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     C# では、次のようになります。  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. MainWindow.xaml を開きます。 
  
     これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは、アプリケーションのメイン ウィンドウと、ページで作成されたコンテンツが表示されます。 <xref:System.Windows.Window>クラスなど、そのタイトル、サイズ、または、アイコン、ウィンドウのプロパティを定義し、閉じるか、非表示にするなどのイベントを処理します。 
  
4. 変更、<xref:System.Windows.Window>要素を<xref:System.Windows.Navigation.NavigationWindow>です。 
  
     このアプリケーションでは、ユーザー操作に応じて画面がさまざまなコンテンツに移動します。 そのため、メイン<xref:System.Windows.Window>に変更する必要があります、<xref:System.Windows.Navigation.NavigationWindow>です。 <xref:System.Windows.Navigation.NavigationWindow>すべてのプロパティを継承<xref:System.Windows.Window>です。 <xref:System.Windows.Navigation.NavigationWindow> XAML ファイル内の要素のインスタンスを作成する、<xref:System.Windows.Navigation.NavigationWindow>クラスです。 詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。 
  
5. 次のプロパティを変更、<xref:System.Windows.Navigation.NavigationWindow>要素。  
  
    -   設定、<xref:System.Windows.Window.Title%2A>プロパティを"ExpenseIt"です。 
  
    -   設定、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを 500 ピクセルです。 
  
    -   設定、 <xref:System.Windows.FrameworkElement.Height%2A> 350 ピクセル プロパティです。 
  
    -   削除、<xref:System.Windows.Controls.Grid>の間に要素、<xref:System.Windows.Navigation.NavigationWindow>タグ。 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     C# では、次のようになります。  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。 
  
     このファイルは、MainWindow.xaml で宣言されたイベントを処理するコードを含んだ、分離コード ファイルです。 このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。 
  
7. C# を使用している場合は、変更、`MainWindow`から派生するクラス<xref:System.Windows.Navigation.NavigationWindow>です。 
  
     Visual Basic では、XAML でウィンドウを変更すると自動的にこの処理が行われます。 
  
     コードは次のようになります。 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a>ファイルをアプリケーションに追加します。  
 このセクションでは、アプリケーションに 2 つのページと 1 つのイメージを追加します。 
  
1. という名前のプロジェクトに新しいページ (WPF) を追加`ExpenseItHome.xaml`です。 詳細については、次を参照してください。[する方法: WPF プロジェクトに新しい項目の追加](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad)です。 
  
     このページが、アプリケーションの起動時に表示される最初のページになります。 ここに個人の一覧が表示され、ユーザーは経費報告書の表示対象となる個人を選択できます。 
  
2. ExpenseItHome.xaml を開きます。 
  
3. 設定、 <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - ホーム"にします。 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     C# では、次のようになります。  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. MainWindow.xaml を開きます。 
  
5. 設定、<xref:System.Windows.Navigation.NavigationWindow.Source%2A>プロパティを<xref:System.Windows.Navigation.NavigationWindow>"ExpenseItHome.xaml"にします。 
  
     これにより、ExpenseItHome.xaml が、アプリケーションの起動時に最初に開くページになります。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     C# では、次のようになります。  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. という名前のプロジェクトに新しいページ (WPF) を追加`ExpenseReportPage.xaml`です。 
  
     このページには、ExpenseItHome.xaml で選択されたユーザーの経費明細書が表示されます。 
  
7. ExpenseReportPage.xaml を開きます。 
  
8. 設定、 <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - 経費の表示"にします。 
  
     [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     C# では、次のようになります。  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. ExpenseItHome.xaml.vb と ExpenseReportPage.xaml.vb を開くか、または ExpenseItHome.xaml.cs と ExpenseReportPage.xaml.cs を開きます。 
  
     新しいページ ファイルを作成すると、Visual Studio によって分離コード ファイルが自動的に作成されます。 これらの分離コード ファイルでは、ユーザー入力に対応するためのロジックを処理します。 
  
     コードは次のようになります。 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. watermark.png という名前のイメージをプロジェクトに追加します。 独自のイメージを作成することも、サンプル コードからファイルをコピーすることもできます。 詳細については、次を参照してください。 [NIB: 方法: 既存の項目をプロジェクトに追加](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)です。 

## <a name="building-and-running-the-application"></a>ビルドおよびアプリケーションの実行  
 このセクションでは、アプリケーションをビルドして実行します。 
  
1. ビルドおよびキーを押して、f5 キーまたは選択して、アプリケーションを実行する**デバッグの開始**から、**デバッグ**メニュー。 
  
     次の図は、アプリケーションに、<xref:System.Windows.Navigation.NavigationWindow>ボタン。 
  
     ![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
2. 戻るには、アプリケーションを閉じて[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。 
  
## <a name="creating-the-layout"></a>レイアウトの作成  
 レイアウトが順序付けられたを配置する方法を提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素、およびそれらの要素の位置とサイズをまた管理ときに、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のサイズを変更します。 通常、レイアウトを作成するには、次のいずれかのレイアウト コントロールを使用します。  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 これらの各レイアウト コントロールは、その子要素に対する特別な種類のレイアウトをサポートしています。 ExpenseIt のページはサイズの変更が可能で、各ページの要素は縦にも横にも他の要素と揃えられます。 その結果、<xref:System.Windows.Controls.Grid>アプリケーションに最適なレイアウト要素です。 
  
> [!NOTE]
>  詳細については<xref:System.Windows.Controls.Panel>要素を参照してください[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)です。 レイアウトの詳細については、次を参照してください。[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)です。 
  
 セクションで、テーブルを作成する、単一列 3 つの行と 10 ピクセルの余白を含む列と行の定義を追加することによって、 <xref:System.Windows.Controls.Grid> ExpenseItHome.xaml にします。 
  
1. ExpenseItHome.xaml を開きます。 
  
2. 設定、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Controls.Grid>「10,0,10,10」左、上、右および下余白に対応する要素。 
  
3. 次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]間、<xref:System.Windows.Controls.Grid>行と列の定義を作成するタグです。 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <xref:System.Windows.Controls.RowDefinition.Height%2A> 2 つの行に設定されている<xref:System.Windows.GridLength.Auto%2A>行の内容は、基に、行がサイズ調整することを意味します。 既定値<xref:System.Windows.Controls.RowDefinition.Height%2A>は<xref:System.Windows.GridUnitType.Star>サイズ変更は、行が使用可能な領域の加重比率になることを意味します。 たとえば、2 つの行それぞれの高さが "*" の場合、各行の高さは、使用可能なスペースの半分になります。  
  
     <xref:System.Windows.Controls.Grid>は次の XAML のようになります。  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a>コントロールを追加します。  
 このセクションでは、ホーム ページの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]が更新されことから選択できる、選択された人物の経費報告書を表示するユーザーの一覧を表示します。 コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。 詳しくは、「 [コントロール](../../../../docs/framework/wpf/controls/index.md)」をご覧ください。 
  
 これを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseItHome.xaml に、次の要素が追加されます。  
  
-   <xref:System.Windows.Controls.ListBox>(用、ユーザーの一覧)。 
  
-   <xref:System.Windows.Controls.Label>(リストのヘッダーとして)。 
  
-   <xref:System.Windows.Controls.Button>(をクリックして、一覧で選択されているユーザーの経費報告書を表示する)。 
  
 行内の各コントロールが配置される、<xref:System.Windows.Controls.Grid>を設定して、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>添付プロパティ。 添付プロパティの詳細については、次を参照してください。[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)です。 
  
1. ExpenseItHome.xaml を開きます。 
  
2. 次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]間、<xref:System.Windows.Controls.Grid>タグ。 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. アプリケーションをビルドして実行します。 
  
 次の図は、このセクションの XAML で作成されたコントロールを示しています。 
  
 ![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
## <a name="adding-an-image-and-a-title"></a>イメージとタイトルを追加します。  
 このセクションでは、ホーム ページの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]イメージとページ タイトルで更新されます。 
  
1. ExpenseItHome.xaml を開きます。 
  
2. 別の列を追加、<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>固定の<xref:System.Windows.Controls.ColumnDefinition.Width%2A>230 ピクセルのです。 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. 別の行を追加、<xref:System.Windows.Controls.Grid.RowDefinitions%2A>です。 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. 2 番目の列に設定して、コントロールを移動<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>を 1 にします。 下の行を増やすことで各コントロールを移動する、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>を 1 つです。 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. 設定、<xref:System.Windows.Controls.Panel.Background%2A>の<xref:System.Windows.Controls.Grid>watermark.png イメージ ファイルであることにします。 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. 前に、 <xref:System.Windows.Controls.Border>、追加、<xref:System.Windows.Controls.Label>経費レポートの表示 ページのタイトルになるコンテンツを使用します。 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. アプリケーションをビルドして実行します。 
  
 次の図は、このセクションの結果を示しています。 
  
 ![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
## <a name="adding-code-to-handle-events"></a>イベントを処理するコードを追加します。  
  
1. ExpenseItHome.xaml を開きます。 
  
2. 追加、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラーを<xref:System.Windows.Controls.Button>要素。 詳細については、次を参照してください。[する方法: 単純なイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480)です。 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs ファイルを開きます。 
  
4. 次のコードを追加、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 、によって ExpenseReportPage.xaml ファイルに移動するウィンドウのイベント ハンドラー。 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a>ExpenseReportPage の UI の作成  
 ExpenseReportPage.xaml には、ExpenseItHome.xaml で選択した個人の経費報告書が表示されます。 このセクションでは、コントロールを追加し、作成、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml 用です。 ここでは、さまざまな背景の塗りつぶしの色を追加するも[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。 
  
1. ExpenseReportPage.xaml を開きます。 
  
2. <xref:System.Windows.Controls.Grid> タグの間に次の XAML を追加します。 
  
     この UI はで、レポート データが表示される点を除いて、ExpenseItHome.xaml で作成した ui と似ています、<xref:System.Windows.Controls.DataGrid>です。 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. アプリケーションをビルドして実行します。 
  
    > [!NOTE]
    >  エラーを取得する場合、<xref:System.Windows.Controls.DataGrid>が見つかりませんでしたまたは存在しない、プロジェクトの対象 .NET Framework 4 以降であるかどうかを確認します。 詳細については、「[方法: .NET Framework のバージョンをターゲットにする](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。 
  
4. クリックして、**ビュー**ボタンをクリックします。 
  
     経費明細書ページが表示されます。 
  
 次の図は、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml に追加された要素。 [戻る] ナビゲーション ボタンが有効になっていることを確認してください。 
  
 ![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
## <a name="styling-controls"></a>コントロールのスタイル  
 さまざまな要素の外観は、同じ型でのすべての要素の同じ多くの場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] では、複数の要素間で外観を再利用できるように、スタイルが使用されます。 スタイルの再利用が簡略化するのに役立つ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の作成および管理します。 スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。 このセクションでは、これまでの手順で定義した要素ごとの属性を、スタイルに置き換えます。 
  
1. Application.xaml または App.xaml を開きます。 
  
2. 間に次の XAML を追加、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>タグ。  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]次のスタイルを追加します。  
  
    -  `headerTextStyle`: ページ タイトル <xref:System.Windows.Controls.Label>の書式を設定します。 
  
    -  `labelStyle`: <xref:System.Windows.Controls.Label> コントロールの書式を設定します。 
  
    -  `columnHeaderStyle`: <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>の書式を設定します。 
  
    -  `listHeaderStyle`: リスト ヘッダーの <xref:System.Windows.Controls.Border> コントロールの書式を設定します。 
  
    -  `listHeaderTextStyle`: 一覧のヘッダーを書式設定するには<xref:System.Windows.Controls.Label>です。 
  
    -  `buttonStyle`: 書式設定するには<xref:System.Windows.Controls.Button>ExpenseItHome.xaml にします。 
  
     スタイルがリソースとの子であることを確認、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>プロパティ要素。 ここでは、スタイルはアプリケーション内のすべての要素に適用されます。 内のリソースを使用する例については、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーションを参照してください[アプリケーション リソースの使用](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)です。 
  
3. ExpenseItHome.xaml を開きます。 
  
4. 間のすべてのものを置き換える、<xref:System.Windows.Controls.Grid>を次の XAML 要素。 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、これらのスタイルを適用することで、削除されて置き換えられます。 たとえば、 `headerTextStyle` 、支出レポートの表示 に適用される<xref:System.Windows.Controls.Label>です。 
  
5. ExpenseReportPage.xaml を開きます。 
  
6. 間のすべてのものを置き換える、<xref:System.Windows.Controls.Grid>を次の XAML 要素。 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     これにより、スタイルが <xref:System.Windows.Controls.Label> と <xref:System.Windows.Controls.Border> の要素に追加されます。 
  
7. アプリケーションをビルドして実行します。 
  
     追加した後、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]このセクションで、アプリケーションの外観は同じとスタイルを使用して更新される前にします。 
  
## <a name="binding-data-to-a-control"></a>コントロールへのデータ バインディング  
 このセクションで作成、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]さまざまなコントロールにバインドされているデータ。 
  
1. ExpenseItHome.xaml を開きます。 
  
2. 開始後に<xref:System.Windows.Controls.Grid>要素を作成する次の XAML を追加、<xref:System.Windows.Data.XmlDataProvider>個人ごとにデータを格納しています。 
  
     データとして作成、<xref:System.Windows.Controls.Grid>リソース。 通常、これはファイルとして読み込まれますが、説明を簡単にするため、データをインラインで追加します。 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <xref:System.Windows.Controls.Grid>リソース、次の追加<xref:System.Windows.DataTemplate>、データを表示する方法を定義する、<xref:System.Windows.Controls.ListBox>です。 データ テンプレートの詳細については「 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. 既存の置換<xref:System.Windows.Controls.ListBox>次の XAML を使用します。 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     次の XAML バインド、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>データ ソースに、データ テンプレートとして適用されると、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>です。 
  
## <a name="connecting-data-to-controls"></a>コントロールにデータを接続します。  
 このセクションで、ExpenseItHome.xaml ページで、ユーザーの一覧で選択されのコンス トラクターへの参照を渡しますを現在の項目を取得するコードを記述する`ExpenseReportPage`インスタンス化します。 `ExpenseReportPage` は、渡された項目を使用してデータ コンテキストを設定します。この項目が、ExpenseReportPage.xaml で定義されたコントロールのバインド先になります。 
  
1. ExpenseReportPage.xaml.vb または ExpenseReportPage.xaml.cs を開きます。 
  
2. オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs ファイルを開きます。 
  
4. 変更、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>選択したユーザーの経費報告書データを渡す新しいコンス トラクターを呼び出すイベント ハンドラー。 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a>データ テンプレートを使用してデータのスタイル設定  
 このセクションで更新する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]バインドされたリストをデータ テンプレートを使用して、データ内の各項目。 
  
1. ExpenseReportPage.xaml を開きます。 
  
2. 「名前」と"Department"の内容をバインド<xref:System.Windows.Controls.Label>要素を適切なデータ ソースのプロパティです。 データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. オープン後<xref:System.Windows.Controls.Grid>要素、経費報告書データを表示する方法を定義する次のデータ テンプレートを追加します。  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. テンプレートを適用する、<xref:System.Windows.Controls.DataGrid>経費を表示する列がデータを報告します。 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. アプリケーションをビルドして実行します。 
  
6. ユーザーを選択し、クリックして、**ビュー**ボタンをクリックします。 
  
 次の図には、コントロール、レイアウト、スタイル、データ バインディング、データ テンプレートが適用された ExpenseIt アプリケーションの両方のページが示されています。 
  
 ![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
## <a name="best-practices"></a>ベスト プラクティス  
 このサンプルは、WPF の特定の機能を説明するものであり、アプリケーション開発のベスト プラクティスには従っていません。 包括的なカバレッジ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーション開発のベスト プラクティスでは、必要に応じて、次のトピックを参照してください。  
  
-   ユーザー補助 - [ユーザー補助のベスト プラクティス](../../../../docs/framework/ui-automation/accessibility-best-practices.md)  
  
-   セキュリティ -[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)  
  
-   ローカリゼーション - [WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)  
  
-   パフォーマンス - [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
  
## <a name="whats-next"></a>次の内容  
 ユーザーが自由に作成するためのさまざまな手法があるようになりました、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。 データ バインドの基本的な構成要素の広範な理解が[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーションです。 このトピックは決して網羅的なものではありませんが、このトピックの手法を基に、自分で学習を進められるようになったはずです。 
  
 WPF のアーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。  
  
-   [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
  
 アプリケーションの作成の詳細については、次のトピックを参照してください。  
  
-   [アプリケーションの開発](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [コントロール](../../../../docs/framework/wpf/controls/index.md)  
  
-   [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a>関連項目  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [スタイルおよびテンプレート](../../../../docs/framework/wpf/controls/styles-and-templates.md)
