---
title: "チュートリアル: WPF での Windows フォーム複合コントロールのホスト"
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
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9f9a63d9fced326d20013b1f306d1fe0b7721dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a>チュートリアル: WPF での Windows フォーム複合コントロールのホスト
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、アプリケーションの作成に適した環境を提供します。 ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コード、だということには、少なくともを再利用すると効率的では、そのコードの一部、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションではなく最初から書き換えをします。 最も一般的なシナリオは、既存のある場合[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]コントロール。 場合によっては、するがありますいないでもこれらのコントロールのソース コードへのアクセス。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]このようなコントロールをホストするため、簡単な手順を提供する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 たとえば、使用することができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、特殊なをホストしているときに、プログラミングのほとんどの<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 このチュートリアル手順を説明してアプリケーションをホストする、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]複合コントロールでのデータ入力を実行する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 複合コントロールは DLL にパッケージ化されています。 この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。 このチュートリアルは、外観と機能をほぼ同一である[チュートリアル: Windows フォームで WPF 複合コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)です。 主な違いは、ホストする側とされる側が逆であることです。  
  
 このチュートリアルは、2 つのセクションに分かれています。 最初のセクションの実装をについて簡単に説明する、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]複合コントロール。 2 番目のセクションで詳しく複合コントロールをホストする方法について説明します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、コントロールからイベントを受け取るし、コントロールのプロパティの一部にアクセスします。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォームの複合コントロールを実装します。  
  
-   WPF のホスト アプリケーションを実装します。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WPF サンプルでは、Windows フォームの複合コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=159999)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
## <a name="implementing-the-windows-forms-composite-control"></a>Windows フォームの複合コントロールを実装します。  
 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]この例で使用される複合コントロールは、単純なデータ エントリ フォーム。 このフォームは、ユーザーの名前とアドレスを受け取りし、カスタム イベントを使用してホストにその情報を返します。 次の図はレンダリングされたコントロールを示しています。  
  
 ![単純な Windows フォーム コントロールの](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")  
Windows フォームの複合コントロール  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  起動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、開き、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  [ウィンドウ] カテゴリの選択、 **Windows フォーム コントロール ライブラリ**テンプレート。  
  
3.  新しいプロジェクトに `MyControls` という名前を付けます。  
  
4.  場所についてを指定して、簡単に名前付きのトップレベルのフォルダーなど`WpfHostingWindowsFormsControl`です。 このフォルダーには後でホスト アプリケーションも配置します。  
  
5.  をクリックして**OK**プロジェクトを作成します。 既定のプロジェクトには、という名前の 1 つのコントロールが含まれています。`UserControl1`です。  
  
6.  ソリューション エクスプ ローラーで、名前を変更`UserControl1`に`MyControl1`です。  
  
 プロジェクトは、以下のシステム DLL を参照している必要があります。 既定で含まれていないこれらの Dll のいずれかの場合は、プロジェクトに追加します。  
  
-   システム  
  
-   System.Data  
  
-   System.Drawing  
  
-   System.Windows.Forms  
  
-   System.Xml  
  
### <a name="adding-controls-to-the-form"></a>フォームへのコントロールの追加  
 フォームにコントロールを追加します。  
  
-   開いている`MyControl1`デザイナーでします。  
  
 5 個追加<xref:System.Windows.Forms.Label>コントロールとそれに対応する<xref:System.Windows.Forms.TextBox>コントロール、サイズ設定およびフォームで、前の図のように配置されます。 この例で、<xref:System.Windows.Forms.TextBox>コントロールの名前が付けられます。  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 2 つ追加<xref:System.Windows.Forms.Button>ラベル コントロール**OK**と**キャンセル**です。 ボタン名は、例では、`btnOK`と`btnCancel`、それぞれします。  
  
### <a name="implementing-the-supporting-code"></a>サポート コードの実装  
 コード ビューで、フォームを開きます。 コントロールがそのホストにカスタムを発生させることによって、収集したデータを返します`OnButtonClick`イベント。 データは、イベント引数オブジェクトに含まれます。 次のコードは、イベントおよびデリゲートの宣言を示しています。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 `MyControlEventArgs`クラスには、ホストに返される情報が含まれています。  
  
 フォームに次のクラスを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 ユーザーがクリックしたとき、 **[ok]**または**キャンセル**ボタン、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを作成、`MyControlEventArgs`データを格納しているオブジェクトを生成し、`OnButtonClick`イベント。 2 つのハンドラーの唯一の違いは、イベント引数の`IsOK`プロパティです。 このプロパティは、ホストがクリックしてされたボタンを決定できます。 設定されている`true`の**[ok]**ボタン、および`false`の**キャンセル**ボタンをクリックします。 次のコードは、次の 2 つのボタン ハンドラーを示しています。  
  
 `MyControl1` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a>アセンブリに厳密な名前を付けると、アセンブリのビルド  
 このアセンブリによって参照されていること、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、厳密な名前を持つ必要があります。 厳密な名前を作成するに Sn.exe のキー ファイルを作成し、プロジェクトに追加します。  
  
1.  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のコマンド プロンプトを開きます。 これを行うには、をクリックして、**開始**メニューをクリックして**すべてプログラム/Microsoft Visual Studio 2010 または Visual Studio Tools と Visual Studio コマンド プロンプト**です。 これは、カスタマイズされた環境変数とコンソール ウィンドウを起動します。  
  
2.  コマンド プロンプトを使用して、`cd`コマンドをプロジェクト フォルダーに移動します。  
  
3.  次のコマンドを実行して MyControls.snk をという名前のキー ファイルを生成します。  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  キー ファイルをプロジェクトに含める、ソリューション エクスプ ローラーでプロジェクト名を右クリックし、をクリックして**プロパティ**です。 プロジェクト デザイナーで、をクリックして、**署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンし、キー ファイルを参照します。  
  
5.  ソリューションをビルドします。 ビルドでは、MyControls.dll という名前の DLL が生成されます。  
  
## <a name="implementing-the-wpf-host-application"></a>WPF のホスト アプリケーションの実装  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホスト アプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールをホストに`MyControl1`です。 アプリケーションのハンドル、`OnButtonClick`コントロールからデータを受信するイベントです。 さらから、コントロールのプロパティの一部を変更するためのオプション ボタンのコレクション、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 次の図は、完成したアプリケーションを示します。  
  
 ![WPF ページに埋め込まれたコントロール](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")  
完全なアプリケーションでは、コントロールを表示する WPF アプリケーションに埋め込まれています。  
  
### <a name="creating-the-project"></a>プロジェクトの作成  
 プロジェクトを開始するには  
  
1.  開いている[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]を選択して**新しいプロジェクト**です。  
  
2.  [ウィンドウ] カテゴリの選択、 **WPF アプリケーション**テンプレート。
  
3.  新しいプロジェクトに `WpfHost` という名前を付けます。  
  
4.  配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。  
  
5.  をクリックして**OK**プロジェクトを作成します。  
  
 含む DLL への参照を追加する必要があります`MyControl1`およびその他のアセンブリ。  
  
1.  ソリューション エクスプ ローラーでプロジェクト名を右クリックし **参照の追加**です。  
  
2.  クリックして、**参照**タブをクリックし、MyControls.dll を含まれているフォルダーを参照します。 このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。  
  
3.  MyControls.dll を選択し、クリックして**OK**です。  
  
4.  WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。  
  
### <a name="implementing-the-basic-layout"></a>基本的なレイアウトを実装します。  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] MainWindow.xaml で、ホストのアプリケーションを実装します。 このファイルを含む[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]レイアウトを定義しをホストするマークアップを[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]コントロール。 アプリケーションは、3 つの領域に分かれています。  
  
-   **コントロール プロパティ**パネルで、ホストされるコントロールのさまざまなプロパティを変更に使用できるオプション ボタンのコレクションを格納します。  
  
-   **コントロールからのデータ**パネルで、いくつか示します<xref:System.Windows.Controls.TextBlock>ホストされるコントロールからデータを表示する要素が返されます。  
  
-   ホストされるコントロール自体です。  
  
 次の XAML では、基本的なレイアウトが表示されます。 必要なマークアップをホストに`MyControl1`はからこの例では、省略されたものの、後で説明されています。  
  
 次の MainWindow.xaml で XAML に置き換えます。 Visual Basic を使用している場合にクラスを変更`x:Class="MainWindow"`です。  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 最初の<xref:System.Windows.Controls.StackPanel>要素には、複数のセットが含まれています。<xref:System.Windows.Controls.RadioButton>ホストされるコントロールのさまざまな既定のプロパティを変更することができるようにするコントロール。 後に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、どのホスト`MyControl1`です。 最終的な<xref:System.Windows.Controls.StackPanel>要素では、いくつか含まれています<xref:System.Windows.Controls.TextBlock>ホストされるコントロールによって返されるデータを表示する要素。 要素の順序と<xref:System.Windows.Controls.DockPanel.Dock%2A>と<xref:System.Windows.FrameworkElement.Height%2A>属性の設定は、ギャップや歪みなしで、ウィンドウにホストされるコントロールを埋め込みます。  
  
#### <a name="hosting-the-control"></a>コントロールをホストしています。  
 次の編集したバージョン以前の XAML のについて重点的に必要な要素をホストに`MyControl1`です。  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 `xmlns`名前空間のマッピング属性への参照を作成する、`MyControls`ホストされるコントロールを含む名前空間です。 このマッピングを使用すると、表す`MyControl1`で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として`<mcl:MyControl1>`です。  
  
 XAML での 2 つの要素は、ホスティングを処理します。  
  
-   `WindowsFormsHost`表す、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストに使用すると要素、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]内の制御、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
-   `mcl:MyControl1`、を表す`MyControl1`、に追加、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子のコレクション。 その結果、この[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]の一部としてコントロールを表示、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウ、およびするが、アプリケーションからコントロールと通信できます。  
  
### <a name="implementing-the-code-behind-file"></a>分離コード ファイルの実装  
 MainWindow.xaml.vb または MainWindow.xaml.cs で、分離コード ファイルには、機能を実装する手順のコードが含まれています、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]前のセクションで説明します。 主要なタスクは次のとおりです。  
  
-   イベント ハンドラーをアタッチする`MyControl1`の`OnButtonClick`イベント。  
  
-   さまざまなプロパティを変更する`MyControl1`オプション ボタンのコレクションを設定する方法に基づきます。  
  
-   コントロールによって収集されたデータを表示します。  
  
#### <a name="initializing-the-application"></a>アプリケーションの初期化  
 ウィンドウのイベント ハンドラーの初期化コードが含まれている<xref:System.Windows.FrameworkElement.Loaded>イベントをコントロールのイベント ハンドラーをアタッチおよび`OnButtonClick`イベント。  
  
 MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードを追加、`MainWindow`クラスです。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以前に追加された説明`MyControl1`を<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子要素のコレクションをキャストすること、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>への参照を取得する`MyControl1`です。 イベント ハンドラーをアタッチする、その参照を使用することができますし、`OnButtonClick`です。  
  
 コントロール自体への参照を提供するだけでなく<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、アプリケーションから操作できるは、コントロールのプロパティの数を表示します。 初期化コードは、後で使用するアプリケーションでのグローバル変数をプライベートにそれらの値を割り当てます。  
  
 内の型を簡単にアクセスできるように、 `MyControls` DLL、次の追加`Imports`または`using`ステートメント ファイルの先頭にします。  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a>OnButtonClick イベントの処理  
 `MyControl1`発生させる、`OnButtonClick`イベント、ユーザーがコントロールのボタンのいずれかをクリックします。  
  
 `MainWindow` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 テキスト ボックス内のデータがパック、`MyControlEventArgs`オブジェクト。 ユーザーがクリックした場合、 **OK**ボタン、イベント ハンドラーは、データを抽出し、下のパネルの表示`MyControl1`です。  
  
#### <a name="modifying-the-controls-properties"></a>コントロールのプロパティを変更します。  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がいくつかのホストされるコントロールの既定のプロパティを公開します。 その結果、アプリケーションのスタイルをより厳密に一致するようにコントロールの外観を変更できます。 左側のパネルでオプション ボタンのセットには、いくつかの色とフォントのプロパティを変更するユーザーが有効にします。 ボタンの各セットのハンドラーがある、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントでは、ユーザーのオプション ボタンの選択肢を検出し、コントロールに対応するプロパティを変更します。  
  
 `MainWindow` クラスに次のコードを追加します。  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 アプリケーションをビルドして実行します。 Windows フォームの複合コントロールのいくつかのテキストを追加し、クリックして**OK**です。 そのテキストがラベルに表示されます。 コントロールへの影響を表示する別のオプション ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [チュートリアル: WPF での Windows フォーム コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
