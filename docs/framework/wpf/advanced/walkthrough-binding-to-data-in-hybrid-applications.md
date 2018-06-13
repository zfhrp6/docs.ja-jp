---
title: 'チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: fe8826a390abd370361b84f99540b8dacbdedc5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549280"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング
使用しているかどうかをコントロールにデータ ソースのバインドは、基になるデータへのアクセス権を持つユーザーを提供するために不可欠な[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 このチュートリアルでは、両方を格納するハイブリッド アプリケーションのデータ バインディングを使用するどの[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   データ テンプレートを定義します。  
  
-   フォームのレイアウトを指定します。  
  
-   データ バインディングを指定します。  
  
-   相互運用を使用してデータを表示しています。  
  
-   プロジェクトへのデータ ソースを追加します。  
  
-   データ ソースにバインドします。  
  
 このチュートリアルでタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルでのデータ バインディング](http://go.microsoft.com/fwlink/?LinkID=159983)です。  
  
 完了したら、ハイブリッド アプリケーションでのデータ バインディング機能について理解があります。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。  
  
-   Microsoft SQL Server で実行されている、Northwind サンプル データベースへのアクセス。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
  
#### <a name="to-create-and-set-up-the-project"></a>プロジェクトを作成し、設定するには  
  
1.  という名前の WPF アプリケーション プロジェクトを作成する`WPFWithWFAndDatabinding`です。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml を開き、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。  
  
4.  <xref:System.Windows.Window>要素では、次の追加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間マッピング。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  既定値の名前を付けます<xref:System.Windows.Controls.Grid>要素`mainGrid`を割り当てることによって、<xref:System.Windows.FrameworkElement.Name%2A>プロパティです。  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a>データ テンプレートの定義  
 顧客のマスター一覧に表示されます、<xref:System.Windows.Controls.ListBox>コントロール。 次のコード例を定義、<xref:System.Windows.DataTemplate>という名前のオブジェクト`ListItemsTemplate`のビジュアル ツリーを制御する、<xref:System.Windows.Controls.ListBox>コントロール。 これは、<xref:System.Windows.DataTemplate>に割り当てられている、<xref:System.Windows.Controls.ListBox>コントロールの<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティです。  
  
#### <a name="to-define-the-data-template"></a>データ テンプレートを定義するには  
  
-   次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a>フォーム レイアウトの指定  
 フォームのレイアウトは、次の 3 つの行と 3 つの列を含むグリッドによって定義されます。 <xref:System.Windows.Controls.Label> コントロールは、Customers テーブル内の各列の識別に提供されます。  
  
#### <a name="to-set-up-the-grid-layout"></a>グリッド レイアウトを設定するには  
  
-   次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a>ラベル コントロールを設定するには  
  
-   次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a>データ バインディングの指定  
 顧客のマスター一覧に表示されます、<xref:System.Windows.Controls.ListBox>コントロール。 アタッチされた`ListItemsTemplate`バインド、<xref:System.Windows.Controls.TextBlock>コントロールを`ContactName`データベースからフィールドです。  
  
 各顧客レコードの詳細は、いくつか表示されます<xref:System.Windows.Controls.TextBox>コントロール。  
  
#### <a name="to-specify-data-bindings"></a>データ バインディングを指定するには  
  
-   次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。  
  
     <xref:System.Windows.Data.Binding>クラスのバインド、<xref:System.Windows.Controls.TextBox>データベース内の該当フィールドへのコントロールです。  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a>相互運用を使用してデータを表示します。  
 選択した顧客に対応する注文が表示される、<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>という名前のコントロール`dataGridView1`です。 `dataGridView1`分離コード ファイル内のデータ ソースにコントロールをバインドします。 A<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールの親では、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロール。  
  
#### <a name="to-display-data-in-the-datagridview-control"></a>DataGridView コントロールにデータを表示するには  
  
-   次の XAML をコピー、<xref:System.Windows.Controls.Grid>要素の宣言。  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a>データ ソースをプロジェクトに追加します。  
 Visual Studio プロジェクトにデータ ソースを簡単に追加できます。 このプロシージャは、プロジェクトに厳密に型指定されたデータ セットを追加します。 いくつか他のサポートなどのクラスを選択したテーブルの各テーブルのアダプターも追加されます。  
  
#### <a name="to-add-the-data-source"></a>データ ソースを追加するには  
  
1.  **データ**メニューの **新しいデータ ソースの追加**です。  
  
2.  **データ ソース構成ウィザード**データセットを使用して、Northwind データベースへの接続を作成します。 詳細については、次を参照してください。[する方法: データベース内のデータへの接続](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)です。  
  
3.  によってメッセージが表示されたら、**データ ソース構成ウィザード**、接続文字列として保存`NorthwindConnectionString`です。  
  
4.  データベース オブジェクトの選択画面が表示されたら、選択、`Customers`と`Orders`テーブル、および生成されたデータ セットの名前`NorthwindDataSet`です。  
  
## <a name="binding-to-the-data-source"></a>データ ソースにバインドします。  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>コンポーネントは、アプリケーションのデータ ソースの統一されたインターフェイスを提供します。 データ ソースへのバインディングは、分離コード ファイルに実装されます。  
  
#### <a name="to-bind-to-the-data-source"></a>データ ソースにバインドするには  
  
1.  MainWindow.xaml.vb または MainWindow.xaml.cs の名前は、分離コード ファイルを開きます。  
  
2.  次のコードをコピー、`MainWindow`クラス定義です。  
  
     このコードで宣言、<xref:System.Windows.Forms.BindingSource>コンポーネントとデータベースへの接続を関連付けられているヘルパー クラス。  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  コンス トラクターに次のコードをコピーします。  
  
     このコードを作成して、初期化、<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  MainWindow.xaml を開きます。  
  
5.  [デザイン] ビューまたは XAML ビューで、選択、<xref:System.Windows.Window>要素。  
  
6.  [プロパティ] ウィンドウ、**イベント**タブです。  
  
7.  ダブルクリックして、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
8.  次のコードをコピー、<xref:System.Windows.FrameworkElement.Loaded>イベント ハンドラー。  
  
     このコードに割り当てます、<xref:System.Windows.Forms.BindingSource>データ コンテキストとしてコンポーネントに入力し、`Customers`と`Orders`アダプター オブジェクト。  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. 次のコードをコピー、`MainWindow`クラス定義です。  
  
     このメソッドは、処理、<xref:System.Windows.Data.CollectionView.CurrentChanged>イベントとデータ バインディングの現在の項目を更新します。  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [ハイブリッド アプリケーションのサンプルでのデータ バインディング](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
