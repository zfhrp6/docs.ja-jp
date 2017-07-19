---
title: "チュートリアル: Windows フォームでの WPF 複合コントロールのホスト | Microsoft Docs"
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
  - "ホスト (Windows フォームの WPF コンテンツを)"
ms.assetid: 0ac41286-4c1b-4b17-9196-d985cb844ce1
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# チュートリアル: Windows フォームでの WPF 複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコードに多大な手間と時間をかけた場合は、コードを最初から記述し直すよりも、既存の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] アプリケーションを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で拡張する方が効率的となることもあります。  一般的なシナリオとしては、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] アプリケーション内に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用して実装したコントロールを埋め込む場合が挙げられます。  WPF コントロールのカスタマイズ方法の詳細については、「[コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)」を参照してください。  
  
 このチュートリアルでは、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] アプリケーションで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールをホストしてデータ エントリを実行するアプリケーションについて段階的に説明します。  複合コントロールは DLL にパッケージ化されています。  この一般的な手順は、さらに複雑なアプリケーションやコントロールに拡張できます。  このチュートリアルは、外観および機能が「[チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)」の例とほぼ同じになるように設計されています。  主な違いは、ホストする側とされる側が逆であることです。  
  
 チュートリアルは、2 つのセクションに分かれています。  最初のセクションでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールの実装について簡単に説明します。  2 番目のセクションでは、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] アプリケーションで複合コントロールをホストし、コントロールからイベントを受け取って、コントロールのプロパティの一部にアクセスする方法について詳しく説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   WPF 複合コントロールを実装する。  
  
-   Windows フォーム ホスト アプリケーションを実装する。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[Windows フォームでの WPF 複合コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159996)を参照してください。  
  
## 必要条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## WPF 複合コントロールの実装  
 この例で使用される [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールは、ユーザーの名前と住所を受け取る単純なデータ入力フォームです。  ユーザーが 2 つのボタンのいずれかをクリックして入力操作が終了したことを示すと、コントロールは入力情報をホストに返すカスタム イベントを発生させます。  レンダリングされたコントロールを次の図に示します。  
  
 ![単純な WPF コントロール](../../../../docs/framework/wpf/advanced/media/avaloncontrol.png "AvalonControl")  
WPF 複合コントロール  
  
### プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を起動して、**\[新しいプロジェクト\]** ダイアログ ボックスを開きます。  
  
2.  Visual C\# および Windows のカテゴリで、**\[WPF ユーザー コントロール ライブラリ\]** テンプレートを選択します。  
  
3.  新しいプロジェクトに `MyControls` という名前を付けます。  
  
4.  配置場所としては、`WindowsFormsHostingWpfControl` など、わかりやすい名前を付けた最上位フォルダーを指定します。  このフォルダーには後でホスト アプリケーションも配置します。  
  
5.  **\[OK\]** をクリックして、プロジェクトを作成します。  既定のプロジェクトには、`UserControl1` という名前の 1 つのコントロールが含まれます。  
  
6.  ソリューション エクスプローラーで、`UserControl1` の名前を `MyControl1` に変更します。  
  
 プロジェクトは、次のシステム DLL を参照している必要があります。  これらの DLL のいずれかが既定で含まれていない場合は、プロジェクトに追加します。  
  
-   PresentationCore  
  
-   PresentationFramework  
  
-   システム  
  
-   WindowsBase  
  
### ユーザー インターフェイスの作成  
 複合コントロールの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して実装されます。  複合コントロールの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は 5 つの <xref:System.Windows.Controls.TextBox> 要素で構成されています。  各 <xref:System.Windows.Controls.TextBox> 要素には、ラベルとして使用される <xref:System.Windows.Controls.TextBlock> 要素が関連付けられています。  下部には **\[OK\]** および **\[Cancel\]** という 2 つの <xref:System.Windows.Controls.Button> 要素があります。  ユーザーがいずれかのボタンをクリックすると、コントロールは情報をホストに返すカスタム イベントを発生させます。  
  
#### 基本的なレイアウト  
 <xref:System.Windows.Controls.Grid> 要素には、さまざまな [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素が格納されます。  <xref:System.Windows.Controls.Grid> を使用して、HTML で `Table` 要素を使用する場合とほとんど同じ方法で、複合コントロールのコンテンツを配置できます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には <xref:System.Windows.Documents.Table> 要素もありますが、<xref:System.Windows.Controls.Grid> の方が軽量で、単純なレイアウト タスクに適しています。  
  
 次の XAML に基本的なレイアウトを示します。  この XAML では、<xref:System.Windows.Controls.Grid> 要素に列および行の数を指定することにより、コントロールの全体的な構造を定義しています。  
  
 MyControl1.xaml で、既存の XAML を次の XAML で置き換えます。  
  
 [!code-xml[WindowsFormsHostingWpfControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#101)]  
[!code-xml[WindowsFormsHostingWpfControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#102)]  
  
#### TextBlock 要素および TextBox 要素のグリッドへの追加  
 グリッドに [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を配置するには、その要素の <xref:System.Windows.Controls.Grid.RowProperty> および <xref:System.Windows.Controls.Grid.ColumnProperty> 属性に適切な行番号と列番号を設定します。  行と列の番号付けは 0 から始まる点に注意してください。  <xref:System.Windows.Controls.Grid.ColumnSpanProperty> 属性を設定することによって、1 つの要素を複数の列にまたがって表示することができます。  <xref:System.Windows.Controls.Grid> 要素の詳細については、「[グリッド要素を作成する](../../../../docs/framework/wpf/controls/how-to-create-a-grid-element.md)」を参照してください。  
  
 次の XAML では、複合コントロールの <xref:System.Windows.Controls.TextBox> 要素および <xref:System.Windows.Controls.TextBlock> 要素に、要素をグリッドに適切に配置するための <xref:System.Windows.Controls.Grid.RowProperty> 属性および <xref:System.Windows.Controls.Grid.ColumnProperty> 属性を設定しています。  
  
 MyControl1.xaml で、次の XAML を <xref:System.Windows.Controls.Grid> 要素内に追加します。  
  
 [!code-xml[WindowsFormsHostingWpfControl#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#103)]  
  
#### UI 要素のスタイル設定  
 データ入力フォームの多くの要素は、外観が似ています。つまり、それらの要素ではいくつかのプロパティの設定が同一になります。  前の XAML では、各要素の属性を個別に設定するのではなく、<xref:System.Windows.Style> 要素を使用して、複数の要素のクラスの標準プロパティ設定を定義しています。  この方法では、コントロールの複雑さが軽減され、1 つのスタイル属性を使用して複数の要素の外観を変更できます。  
  
 <xref:System.Windows.Style> 要素は <xref:System.Windows.Controls.Grid> 要素の <xref:System.Windows.FrameworkElement.Resources%2A> プロパティに格納されるため、コントロール内のすべての要素で使用できます。  スタイルに名前が付いている場合は、そのスタイルの名前に設定された <xref:System.Windows.Style> 要素を追加することによって、要素にそのスタイルを適用します。  名前が付いていないスタイルは、要素の既定のスタイルになります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のスタイルの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
 複合コントロールの <xref:System.Windows.Style> 要素を次の XAML に示します。  スタイルが要素にどのように適用されるかについては、前の XAML を参照してください。  たとえば、最後の <xref:System.Windows.Controls.TextBlock> 要素には `inlineText` スタイルが適用され、最後の <xref:System.Windows.Controls.TextBox> 要素は既定のスタイルを使用します。  
  
 MyControl1.xaml で、次の XAML を <xref:System.Windows.Controls.Grid> の開始要素の直後に追加します。  
  
 [!code-xml[WindowsFormsHostingWpfControl#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#104)]  
  
#### \[OK\] および \[Cancel\] ボタンの追加  
 複合コントロール上の最後の要素は、<xref:System.Windows.Controls.Grid> の最後の行の最初の 2 つの列を専有する **\[OK\]** および **\[Cancel\]** の <xref:System.Windows.Controls.Button> 要素です。  これらの要素は、共通のイベント ハンドラーである `ButtonClicked`、および前の XAML で定義された既定の <xref:System.Windows.Controls.Button> スタイルを使用します。  
  
 MyControl1.xaml で、次の XAML を最後の <xref:System.Windows.Controls.TextBox> 要素の後に追加します。  複合コントロールの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 部分はこれで完成です。  
  
 [!code-xml[WindowsFormsHostingWpfControl#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml#105)]  
  
### 分離コード ファイルの実装  
 分離コード ファイル MyControl1.xaml.cs は、3 つの基本的なタスクを実装します。  
  
1.  ユーザーがボタンのいずれかをクリックしたときに発生するイベントを処理します。  
  
2.  <xref:System.Windows.Controls.TextBox> 要素からデータを取得し、そのデータをカスタム イベント引数オブジェクトにパッケージ化します。  
  
3.  ユーザーが操作を終了したことをホストに通知し、入力データをホストに渡すカスタム `OnButtonClick` イベントを発生させます。  
  
 コントロールは、外観を変更するための色とフォントのプロパティもいくつか公開します。  [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールをホストするために使用される <xref:System.Windows.Forms.Integration.WindowsFormsHost> クラスとは異なり、<xref:System.Windows.Forms.Integration.ElementHost> クラスはコントロールの <xref:System.Windows.Controls.Panel.Background%2A> プロパティのみを公開します。  このコード例と「[チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)」で説明した例の類似性を保持するために、このコントロールでは残りのプロパティを直接公開します。  
  
#### 分離コード ファイルの基本構造  
 分離コード ファイルは、`MyControl1` および `MyControlEventArgs` という 2 つのクラスを格納する単一の名前空間である `MyControls` で構成されています。  
  
```  
  
namespace MyControls  
{  
  public partial class MyControl1 : Grid  
  {  
    //...  
  }  
  public class MyControlEventArgs : EventArgs  
  {  
    //...  
  }  
}  
  
```  
  
 最初のクラスである `MyControl1` は、MyControl1.xaml で定義された [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の機能を実装するコードを格納する部分クラスです。  MyControl1.xaml が解析されると、その [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は同じ部分クラスに変換され、2 つの部分クラスがマージされて、コンパイルされたコントロールを形成します。  このため、分離コード ファイル内のクラス名は、MyControl1.xaml に割り当てられたクラス名と一致する必要があり、コントロールのルート要素から継承する必要があります。  2 番目のクラスである `MyControlEventArgs` はホストにデータを返送するために使用されるイベント引数クラスです。  
  
 MyControl1.xaml.cs を開きます。  次の名前に合わせて既存のクラス宣言を変更し、<xref:System.Windows.Controls.Grid> を継承します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#21)]  
  
#### コントロールの初期化  
 このコードでは、次の基本タスクを実装します。  
  
-   プライベート イベントである `OnButtonClick`、およびそのイベントに関連付けられたデリゲートである `MyControlEventHandler` を宣言します。  
  
-   ユーザーのデータを格納する複数のプライベート グローバル変数を作成します。  このデータは、対応するプロパティを通じて公開されます。  
  
-   コントロールの <xref:System.Windows.FrameworkElement.Loaded> イベントのハンドラー `Init` を実装します。  このハンドラーは、グローバル変数に MyControl1.xaml で定義された値を割り当てることによって、グローバル変数を初期化します。  初期化するには、一般的な <xref:System.Windows.Controls.TextBlock> の要素である `nameLabel` に割り当てられた <xref:System.Windows.FrameworkElement.Name%2A> を使用して、この要素のプロパティの設定にアクセスします。  
  
 既存のコンストラクターを削除し、次のコードを `MyControl1` クラスに追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#11)]  
  
#### ボタンのクリック イベントの処理  
 ユーザーは、**\[OK\]** ボタンまたは **\[Cancel\]** ボタンをクリックすることにより、データ入力タスクを完了したことを示します。  これらのボタンは両方とも、同じ <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーである `ButtonClicked` を使用します。  これらのボタンにはそれぞれ `btnOK` または `btnCancel` という名前が付けられています。これにより、ハンドラーが `sender` 引数の値を調べることによって、どちらのボタンがクリックされたかを判断することができます。  ハンドラーは次の処理を行います。  
  
-   <xref:System.Windows.Controls.TextBox> 要素からのデータを格納する `MyControlEventArgs` オブジェクトを作成します。  
  
-   ユーザーが \[Cancel\] ボタンをクリックした場合に、`MyControlEventArgs` オブジェクトの `IsOK` プロパティを `false` に設定します。  
  
-   ユーザーが操作を終了したことをホストに示す `OnButtonClick` イベントを発生させ、収集したデータを渡します。  
  
 次のコードを、`MyControl1` クラスの `Init` メソッドの後に追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#12)]  
  
#### プロパティの作成  
 クラスの残りの部分では単純に、前に説明したグローバル変数に対応するプロパティを公開します。  プロパティが変更されると、set アクセサーが対応する要素のプロパティを変更し、基になるグローバル変数を更新することによって、コントロールの外観を変更します。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#13)]  
  
#### ホストへのデータの返送  
 ファイルの最後のコンポーネントは、収集されたデータをホストに返送するために使用される `MyControlEventArgs` クラスです。  
  
 `MyControls` 名前空間に次のコードを追加します。  この実装は簡単なので、これ以上の説明はしません。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/MyControls/Page1.xaml.cs#14)]  
  
 ソリューションをビルドします。  ビルドでは、MyControls.dll という名前の DLL が生成されます。  
  
<a name="winforms_host_section"></a>   
## Windows フォーム ホスト アプリケーションの実装  
 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ホスト アプリケーションは <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトを使用して [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールをホストします。  アプリケーションは、`OnButtonClick` イベントを処理して、複合コントロールからデータを受け取ります。  アプリケーションには、コントロールの外観を変更するために使用できるオプションのボタンのセットもあります。  次の図は、アプリケーションを示しています。  
  
 ![Avalon コントロールをホストする Windows フォーム](../../../../docs/framework/wpf/advanced/media/wfhost.png "WFHost")  
Windows フォーム アプリケーションでホストされる WPF 複合コントロール  
  
### プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] を起動して、**\[新しいプロジェクト\]** ダイアログ ボックスを開きます。  
  
2.  Visual C\# および Windows のカテゴリで、**\[Windows フォーム アプリケーション\]** テンプレートを選択します。  
  
3.  新しいプロジェクトに `WFHost` という名前を付けます。  
  
4.  配置場所としては、MyControls プロジェクトの配置先と同じ最上位フォルダーを指定します。  
  
5.  **\[OK\]** をクリックして、プロジェクトを作成します。  
  
 `MyControl1` および他のアセンブリを含む DLL への参照も追加する必要があります。  
  
1.  ソリューション エクスプローラーで、プロジェクト名を右クリックし、**\[参照の追加\]** を選択します。  
  
2.  **\[参照\]** タブをクリックし、MyControls.dll を格納しているフォルダーを参照します。  このチュートリアルの場合は、MyControls\\bin\\Debug フォルダーです。  
  
3.  MyControls.dll を選択し、**\[OK\]** をクリックします。  
  
4.  次のアセンブリへの参照を追加します。  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   System.Xaml  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
### アプリケーションのユーザー インターフェイスの実装  
 Windows フォーム アプリケーションの UI には、WPF 複合コントロールと対話するためのいくつかのコントロールが含まれています。  
  
1.  Windows フォーム デザイナーで、Form1 を開きます。  
  
2.  コントロールを配置するためにフォームを拡げます。  
  
3.  フォームの右上隅に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールを保持するための <xref:System.Windows.Forms.Panel?displayProperty=fullName> コントロールを追加します。  
  
4.  次の <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> コントロールをフォームに追加します。  
  
    |名前|テキスト|  
    |--------|----------|  
    |groupBox1|\[背景色\]|  
    |groupBox2|前景色|  
    |groupBox3|Font Size|  
    |groupBox4|フォント ファミリ|  
    |groupBox5|フォント スタイル|  
    |groupBox6|フォントの太さ|  
    |groupBox7|コントロールからのデータ|  
  
5.  次の <xref:System.Windows.Forms.RadioButton?displayProperty=fullName> コントロールを <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> コントロールに追加します。  
  
    |GroupBox|名前|テキスト|  
    |--------------|--------|----------|  
    |groupBox1|radioBackgroundOriginal|元|  
    |groupBox1|radioBackgroundLightGreen|ライトグリーン|  
    |groupBox1|radioBackgroundLightSalmon|ライトサーモン|  
    |groupBox2|radioForegroundOriginal|元|  
    |groupBox2|radioForegroundRed|赤|  
    |groupBox2|radioForegroundYellow|黄|  
    |groupBox3|radioSizeOriginal|元|  
    |groupBox3|radioSizeTen|10|  
    |groupBox3|radioSizeTwelve|12|  
    |groupBox4|radioFamilyOriginal|元|  
    |groupBox4|radioFamilyTimes|Times New Roman|  
    |groupBox4|radioFamilyWingDings|WingDings|  
    |groupBox5|radioStyleOriginal|Normal|  
    |groupBox5|radioStyleItalic|イタリック体|  
    |groupBox6|radioWeightOriginal|元|  
    |groupBox6|radioWeightBold|\[太字\]|  
  
6.  次の <xref:System.Windows.Forms.Label?displayProperty=fullName> コントロールを最後の <xref:System.Windows.Forms.GroupBox?displayProperty=fullName> に追加します。  これらのコントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールから返されたデータを表示します。  
  
    |GroupBox|名前|テキスト|  
    |--------------|--------|----------|  
    |groupBox7|lblName|名前:|  
    |groupBox7|lblAddress|番地:|  
    |groupBox7|lblCity|市区町村:|  
    |groupBox7|lblState|都道府県:|  
    |groupBox7|lblZip|郵便番号:|  
  
### フォームの初期化  
 通常は、フォームの <xref:System.Windows.Forms.Form.Load> イベント ハンドラー内にホスティング コードを実装します。  次のコードは、サンプルの <xref:System.Windows.Forms.Form.Load> イベント ハンドラー、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールの <xref:System.Windows.FrameworkElement.Loaded> イベントのハンドラー、および後で使用するいくつかのグローバル変数の宣言を示します。  
  
 Windows フォーム デザイナーで、フォームをダブルクリックして <xref:System.Windows.Forms.Form.Load> イベント ハンドラーを作成します。  Form1.cs の先頭に、次の `using` ステートメントを追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#10)]  
  
 既存の `Form1` クラスの内容を次のコードで置き換えます。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#2)]  
  
 前のコードの `Form1_Load` メソッドは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールをホストするための一般的な手順を示します。  
  
1.  新しい <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトを作成します。  
  
2.  コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle?displayProperty=fullName> に設定します。  
  
3.  <xref:System.Windows.Forms.Integration.ElementHost> コントロールを <xref:System.Windows.Forms.Panel> コントロールの <xref:System.Windows.Forms.Control.Controls%2A> コレクションに追加します。  
  
4.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールのインスタンスを作成します。  
  
5.  <xref:System.Windows.Forms.Integration.ElementHost> コントロールの <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> プロパティにコントロールを割り当てることによって、フォーム上で複合コントロールをホストします。  
  
 `Form1_Load` メソッドの残りの 2 行は、2 つのコントロール イベントにハンドラーをアタッチします。  
  
-   `OnButtonClick` は、ユーザーが **\[OK\]** または **\[Cancel\]** ボタンをクリックしたときに複合コントロールが発生させるカスタム イベントです。  このイベントを処理して、ユーザーの応答を取得し、ユーザーが指定したデータをすべて収集します。  
  
-   <xref:System.Windows.FrameworkElement.Loaded> は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールが完全に読み込まれたときにこのコントロールが発生させる標準のイベントです。  ここでこのイベントを使用するのは、この例ではコントロールからのプロパティを使用して複数のグローバル変数を初期化する必要があるからです。  フォームの <xref:System.Windows.Forms.Form.Load> イベントが発生した時点では、コントロールは完全には読み込まれておらず、これらの値はまだ `null` に設定されています。  これらのプロパティにアクセスするには、コントロールの <xref:System.Windows.FrameworkElement.Loaded> イベントが発生するまで待つ必要があります。  
  
 前のコードでは、<xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーが示されています。  `OnButtonClick` ハンドラーについては次のセクションで説明します。  
  
### OnButtonClick の処理  
 `OnButtonClick` イベントは、ユーザーが \[OK\] または \[Cancel\] ボタンをクリックしたときに発生します。  
  
 イベント ハンドラーは、イベント引数の `IsOK` フィールドをチェックして、どちらのボタンがクリックされたかを判断します。  `lbl`*data* 変数は、前に説明した <xref:System.Windows.Forms.Label> コントロールに対応します。  ユーザーが **\[OK\]** ボタンをクリックすると、コントロールの <xref:System.Windows.Controls.TextBox> コントロールからのデータは、対応する <xref:System.Windows.Forms.Label> コントロールに割り当てられます。  ユーザーが **\[Cancel\]** ボタンをクリックした場合、<xref:System.Windows.Forms.Label.Text%2A> の値は既定の文字列に設定されます。  
  
 次のボタン クリック イベント ハンドラー コードを `Form1` クラスに追加します。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#3)]  
  
 アプリケーションをビルドして実行します。  WPF 複合コントロールに任意のテキストを追加し、**\[OK\]** をクリックします。  そのテキストがラベルに表示されます。  この時点で、オプション ボタンの処理用にコードは追加されていません。  
  
### コントロールの外観の変更  
 フォームの <xref:System.Windows.Forms.RadioButton> コントロールを使用すると、ユーザーは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 複合コントロールの前景と背景の色、および複数のフォント プロパティを変更できます。  背景色は <xref:System.Windows.Forms.Integration.ElementHost> オブジェクトによって公開されます。  残りのプロパティは、コントロールのカスタム プロパティとして公開されます。  
  
 フォーム上の各 <xref:System.Windows.Forms.RadioButton> コントロールをダブルクリックして <xref:System.Windows.Forms.RadioButton.CheckedChanged> イベント ハンドラーを作成します。  <xref:System.Windows.Forms.RadioButton.CheckedChanged> イベント ハンドラーを次のコードで置き換えます。  
  
 [!code-csharp[WindowsFormsHostingWpfControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsFormsHostingWpfControl/CSharp/WFHost/Form1.cs#4)]  
  
 アプリケーションをビルドして実行します。  別のオプション ボタンをクリックして、WPF 複合コントロール上の影響を確認します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの 3D WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)