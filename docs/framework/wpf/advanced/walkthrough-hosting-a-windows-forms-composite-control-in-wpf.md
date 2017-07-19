---
title: "チュートリアル: WPF での Windows フォーム複合コントロールのホスト | Microsoft Docs"
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
  - "複合コントロール, ホスト (WPF で)"
  - "ホスト (Windows フォーム コントロールを WPF で)"
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# チュートリアル: WPF での Windows フォーム複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。  ただし、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]のコードに多くの投資を行った場合は、コードを最初から記述し直すよりも、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのコードの少なくとも一部を再利用する方が効率的です。  最も一般的なシナリオは、既存の [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールがある場合です。  場合によっては、これらのコントロールのソース コードにアクセスできないことがあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、そのようなコントロールを [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでホストするための簡単な手順が用意されています。  たとえば、特殊な <xref:System.Windows.Forms.DataGridView> コントロールをホストしながら、ほとんどのプログラミングには [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用できます。  
  
 このチュートリアルでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合コントロールをホストしてデータ エントリを実行するアプリケーションについて段階的に説明します。  複合コントロールは DLL にパッケージ化されています。  この一般的な手順は、さらに複雑なアプリケーションやコントロールに拡張できます。  このチュートリアルは、外観および機能が「[チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)」の例とほぼ同じになるように設計されています。  主な違いは、ホストする側とされる側が逆であることです。  
  
 チュートリアルは、2 つのセクションに分かれています。  最初のセクションでは、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合コントロールの実装について簡単に説明します。  2 番目のセクションでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションで複合コントロールをホストし、コントロールからイベントを受け取って、コントロールのプロパティの一部にアクセスする方法について詳しく説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム複合コントロールの実装  
  
-   WPF ホスト アプリケーションの実装  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[WPF での Windows フォーム複合コントロールのホストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159999)を参照してください。  
  
## 必要条件  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## Windows フォーム複合コントロールの実装  
 この例で使用する [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 複合コントロールは、単純なデータ入力フォームです。  このフォームは、ユーザーの名前と住所を受け取った後、カスタム イベントを使用してその情報をホストに返します。  レンダリングされたコントロールを次の図に示します。  
  
 ![シンプルな Windows フォーム コントロール](../../../../docs/framework/wpf/advanced/media/wfcontrol.png "WFControl")  
Windows フォーム複合コントロール  
  
### プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を起動して、**\[新しいプロジェクト\]** ダイアログ ボックスを開きます。  
  
2.  ウィンドウのカテゴリで、**\[Windows フォーム コントロール ライブラリ\]** テンプレートを選択します。  
  
3.  新しいプロジェクトに `MyControls` という名前を付けます。  
  
4.  配置場所としては、`WpfHostingWindowsFormsControl` など、わかりやすい名前を付けた最上位フォルダーを指定します。  このフォルダーには後でホスト アプリケーションも配置します。  
  
5.  **\[OK\]** をクリックして、プロジェクトを作成します。  既定のプロジェクトには、`UserControl1` という名前の 1 つのコントロールが含まれます。  
  
6.  ソリューション エクスプローラーで、`UserControl1` の名前を `MyControl1` に変更します。  
  
 プロジェクトは、次のシステム DLL を参照している必要があります。  これらの DLL のいずれかが既定で含まれていない場合は、プロジェクトに追加します。  
  
-   システム  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### フォームへのコントロールの追加  
 フォームにコントロールを追加するには、次の操作を実行します。  
  
-   デザイナーで `MyControl1` を開きます。  
  
 5 つの <xref:System.Windows.Forms.Label> コントロールとそれに対応する <xref:System.Windows.Forms.TextBox> コントロールを、前の図と同じようなサイズと位置関係で、フォーム上に追加します。  この例では、<xref:System.Windows.Forms.TextBox> コントロールには次のような名前を付けます。  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 **OK** と **Cancel** というラベルを付けた 2 つの <xref:System.Windows.Forms.Button> コントロールを追加します。  この例では、ボタンの名前はそれぞれ `btnOK` と `btnCancel` です。  
  
### サポート コードの実装  
 コード ビューでフォームを開きます。  コントロールは、カスタム `OnButtonClick` イベントを発生させることで、収集したデータをホストに返します。  データは、イベント引数オブジェクトに格納されています。  次のコードは、イベントとデリゲートの宣言を示しています。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs` クラスには、ホストに返される情報が格納されます。  
  
 次のクラスをフォームに追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 ユーザーが \[OK\] ボタンまたは \[Cancel\] ボタンをクリックすると、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーはデータを格納した `MyControlEventArgs` オブジェクトを作成し、`OnButtonClick` イベントを発生させます。  2 つのハンドラーの違いは、イベント引数の `IsOK` プロパティだけです。  このプロパティにより、ホストはどちらのボタンがクリックされたのかを判別できます。  \[OK\] ボタンの場合は `true` が設定され、\[Cancel\] ボタンの場合は `false` が設定されます。  次のコード例は、2 つのボタン ハンドラーを示しています。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### アセンブリへの厳密な名前の設定とアセンブリのビルド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションからこのアセンブリを参照するには、アセンブリに厳密な名前を付ける必要があります。  厳密な名前を作成するには、Sn.exe でキー ファイルを作成し、それをプロジェクトに追加します。  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のコマンド プロンプトを開きます。  この操作を行うには、**\[スタート\]** ボタンをクリックし、**\[すべてのプログラム\]**、\[Microsoft Visual Studio 2010\]、\[Visual Studio ツール\] の順にポイントして、\[Visual Studio コマンド プロンプト\] をクリックします。  カスタマイズされた環境変数でコンソール ウィンドウが起動されます。  
  
2.  コマンド プロンプトで、`cd` コマンドを使用してプロジェクト フォルダーに移動します。  
  
3.  次のコマンドを実行し、MyControls.snk という名前のキー ファイルを生成します。  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  キー ファイルをプロジェクトに組み込むには、ソリューション エクスプローラーでプロジェクト名を右クリックし、**\[プロパティ\]** をクリックします。  プロジェクト デザイナーで、**\[署名\]** タブをクリックし、**\[アセンブリの署名\]** チェック ボックスをオンにして、キー ファイルを参照します。  
  
5.  ソリューションをビルドします。  ビルドでは、MyControls.dll という名前の DLL が生成されます。  
  
## WPF ホスト アプリケーションの実装  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ホスト アプリケーションは、<xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールを使用して `MyControl1` をホストします。  アプリケーションは、`OnButtonClick` イベントを処理して、コントロールからデータを受け取ります。  また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションからコントロールの一部のプロパティを変更できるオプション ボタンのコレクションもあります。  最終的なアプリケーションを次の図に示します。  
  
 ![WPF ページに埋め込まれたコントロール](../../../../docs/framework/wpf/advanced/media/avalonhost.png "AvalonHost")  
WPF アプリケーションに埋め込まれたコントロールが表示されている完成したアプリケーション  
  
### プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] を開き、\[新しいプロジェクト\] を選択します。  
  
2.  ウィンドウのカテゴリで、**\[WPF アプリケーション\]** テンプレートを選択します。  
  
3.  新しいプロジェクトに `WpfHost` という名前を付けます。  
  
4.  配置場所としては、MyControls プロジェクトの配置先と同じ最上位フォルダーを指定します。  
  
5.  **\[OK\]** をクリックして、プロジェクトを作成します。  
  
 `MyControl1` および他のアセンブリを含む DLL への参照も追加する必要があります。  
  
1.  ソリューション エクスプローラーで、プロジェクト名を右クリックし、**\[参照の追加\]** を選択します。  
  
2.  **\[参照\]** タブをクリックし、MyControls.dll を格納しているフォルダーを参照します。  このチュートリアルの場合は、MyControls\\bin\\Debug フォルダーです。  
  
3.  MyControls.dll を選択し、**\[OK\]** をクリックします。  
  
4.  WindowsFormsIntegration.dll という名前の WindowsFormsIntegration アセンブリに参照を追加します。  
  
### 基本レイアウトの実装  
 ホスト アプリケーションの[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] は、MainWindow.xaml で実装されます。  このファイルは、レイアウトを定義する [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] マークアップを含み、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールをホストします。  アプリケーションは次の 3 つの領域に分かれています。  
  
-   \[Control Properties\] パネルには、ホストされるコントロールのさまざまなプロパティの変更に使用できるオプション ボタンのコレクションが含まれます。  
  
-   \[Data from Control\] パネルには、ホストされるコントロールから返されるデータを表示する <xref:System.Windows.Controls.TextBlock> 要素が含まれます。  
  
-   ホストされるコントロール自体。  
  
 基本的なレイアウトを次の XAML に示します。  `MyControl1` をホストするために必要なマークアップはこの例では省略されていますが、これについては後で説明します。  
  
 MainWindow.xaml 内の XAML を次のコードに置き換えます。  Visual Basic を使用している場合は、クラスを `x:Class="MainWindow"` に変更します。  
  
 [!code-xml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 最初の <xref:System.Windows.Controls.StackPanel> 要素には、ホストされるコントロールのさまざまな既定のプロパティを変更できる一連の <xref:System.Windows.Controls.RadioButton> コントロールが含まれます。  その後にある <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、`MyControl1` をホストします。  最後の <xref:System.Windows.Controls.StackPanel> 要素には、ホストされるコントロールから返されるデータを表示する <xref:System.Windows.Controls.TextBlock> 要素が含まれます。  要素の順序、および <xref:System.Windows.Controls.DockPanel.Dock%2A> 属性と <xref:System.Windows.FrameworkElement.Height%2A> 属性の設定により、すきまやゆがみがないように、ホストされるコントロールがウィンドウに埋め込まれます。  
  
#### コントロールのホスト  
 次のコードは前の XAML を編集したものですが、ここでは `MyControl1` をホストするために必要な要素に焦点を当てます。  
  
 [!code-xml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns` 名前空間の割り当ての属性により、ホストされるコントロールを格納する `MyControls` 名前空間への参照が作成されます。  この割り当てにより、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で `MyControl1` を `<mcl:MyControl1>` として表すことができます。  
  
 XAML に含まれる次の 2 つの要素がホストを処理します。  
  
-   `WindowsFormsHost` は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでの [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールのホストを可能にする <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素を表します。  
  
-   `MyControl1` を表す `mcl:MyControl1` は、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の子コレクションに追加されます。  結果として、この [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] コントロールは [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ウィンドウの一部としてレンダリングされ、アプリケーションからコントロールと通信できます。  
  
### 分離コード ファイルの実装  
 分離コード ファイル MainWindow.xaml.vb または MainWindow.xaml.cs には、前のセクションで説明した [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の機能を実装する手順コードが含まれます。  主要なタスクは次のとおりです。  
  
-   `MyControl1` の `OnButtonClick` イベントへのイベント ハンドラーのアタッチ。  
  
-   一連のオプション ボタンの設定に基づく、`MyControl1` のさまざまなプロパティの変更。  
  
-   コントロールによって収集されたデータの表示。  
  
#### アプリケーションの初期化  
 初期化コードは、ウィンドウの <xref:System.Windows.FrameworkElement.Loaded> イベントのイベント ハンドラーに含まれ、イベント ハンドラーをコントロールの `OnButtonClick` イベントにアタッチします。  
  
 MainWindow.xaml.vb または MainWindow.xaml.cs で、`MainWindow` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 前述の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] によって、`MyControl1` が <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の子要素コレクションに追加されているため、<xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素の <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> をキャストして `MyControl1` への参照を取得できます。  その後、その参照を使用して、イベント ハンドラーを `OnButtonClick` にアタッチすることができます。  
  
 コントロール自体への参照を提供するだけでなく、<xref:System.Windows.Forms.Integration.WindowsFormsHost> ではさまざまなコントロールのプロパティも公開されており、アプリケーションからそれを操作できます。  初期化コードは、後でアプリケーションで使用するため、これらの値をプライベート グローバル変数に代入します。  
  
 `MyControls` DLL の種類に簡単にアクセスできるように、次の `Imports` ステートメントまたは `using` ステートメントをファイルの先頭に追加します。  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### OnButtonClick イベントの処理  
 ユーザーがコントロールのボタンのいずれかをクリックすると、`MyControl1` が `OnButtonClick` イベントを発生させます。  
  
 `MainWindow` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 テキスト ボックスのデータは、`MyControlEventArgs` オブジェクトに格納されます。  ユーザーが \[OK\] ボタンをクリックすると、イベント ハンドラーはデータを抽出して、`MyControl1` の下のパネルに表示します。  
  
#### コントロールのプロパティの変更  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 要素は、ホストされるコントロールのいくつかの既定のプロパティを公開します。  これにより、アプリケーションのスタイルにより一致するように、コントロールの外観を変更できます。  左側のパネルにある一連のオプション ボタンを使用すると、色やフォントのプロパティを変更できます。  各ボタン セットには <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントに対するハンドラーがあり、ユーザーによるオプション ボタンの選択を検出して、コントロールの対応するプロパティを変更します。  
  
 `MainWindow` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 アプリケーションをビルドして実行します。  Windows フォーム複合コントロールにテキストを追加して **\[OK\]** をクリックします。  そのテキストがラベルに表示されます。  別のオプション ボタンをクリックして、コントロール上の影響を確認します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)