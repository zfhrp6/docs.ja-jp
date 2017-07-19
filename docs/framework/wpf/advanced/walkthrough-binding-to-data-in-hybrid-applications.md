---
title: "チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング | Microsoft Docs"
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
  - "データ バインディング [WPF 相互運用性]"
  - "ハイブリッド アプリケーション [WPF 相互運用性]"
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# チュートリアル : ハイブリッド アプリケーションでのデータへのバインディング
データ ソースのコントロールへのバインディングは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]と [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のどちらを使用しているかに関係なく、ユーザーが基になるデータにアクセスできるようにするために不可欠です。  このチュートリアルでは、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールと [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの両方を含むハイブリッド アプリケーションでデータ バインディングを使用する方法を示します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   プロジェクトの作成。  
  
-   データ テンプレートの定義。  
  
-   フォーム レイアウトの指定。  
  
-   データ バインディングの指定。  
  
-   相互運用を使用したデータの表示。  
  
-   プロジェクトへのデータ ソースの追加。  
  
-   データ ソースへのバインディング。  
  
 このチュートリアルで示すタスクの完全なコード一覧については、[ハイブリッド アプリケーションでのデータ バインディングのサンプル](http://go.microsoft.com/fwlink/?LinkID=159983)を参照してください。  
  
 終了すると、ハイブリッド アプリケーションのデータ バインディング機能を理解できるようになります。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Microsoft SQL Server で実行されている Northwind サンプル データベースへのアクセス。  
  
## プロジェクトの作成  
  
#### プロジェクトを作成し、設定するには  
  
1.  `WPFWithWFAndDatabinding` という名前の WPF アプリケーション プロジェクトを作成します。  
  
2.  ソリューション エクスプローラーで、次のアセンブリへの参照を追加します。  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]で MainWindow.xaml を開きます。  
  
4.  <xref:System.Windows.Window> 要素に、次の [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名前空間の割り当てを追加します。  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <xref:System.Windows.FrameworkElement.Name%2A> プロパティを割り当てて、既定の <xref:System.Windows.Controls.Grid> 要素に `mainGrid` という名前を付けます。  
  
     [!code-xml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## データ テンプレートの定義  
 顧客のマスター一覧が <xref:System.Windows.Controls.ListBox> コントロールに表示されます。  <xref:System.Windows.Controls.ListBox> コントロールのビジュアル ツリーを制御する `ListItemsTemplate` という名前の <xref:System.Windows.DataTemplate> オブジェクトを定義するコード例を次に示します。  この <xref:System.Windows.DataTemplate> は、<xref:System.Windows.Controls.ListBox> コントロールの <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> プロパティに割り当てられます。  
  
#### データ テンプレートを定義するには  
  
-   次の XAML を <xref:System.Windows.Controls.Grid> 要素の宣言にコピーします。  
  
     [!code-xml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## フォーム レイアウトの指定  
 フォームのレイアウトは、3 つの行と 3 つの列を持つグリッドで定義されます。  <xref:System.Windows.Controls.Label> コントロールで、Customers テーブル内の各列が識別されます。  
  
#### グリッド レイアウトを設定するには  
  
-   次の XAML を <xref:System.Windows.Controls.Grid> 要素の宣言にコピーします。  
  
     [!code-xml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### ラベル コントロールを設定するには  
  
-   次の XAML を <xref:System.Windows.Controls.Grid> 要素の宣言にコピーします。  
  
     [!code-xml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## データ バインディングの指定  
 顧客のマスター一覧が <xref:System.Windows.Controls.ListBox> コントロールに表示されます。  結合された `ListItemsTemplate` によって、<xref:System.Windows.Controls.TextBlock> コントロールがデータベースの `ContactName` フィールドにバインドされます。  
  
 各顧客レコードの詳細がいくつかの <xref:System.Windows.Controls.TextBox> コントロールに表示されます。  
  
#### データ バインディングを指定するには  
  
-   次の XAML を <xref:System.Windows.Controls.Grid> 要素の宣言にコピーします。  
  
     <xref:System.Windows.Data.Binding> クラスによって、<xref:System.Windows.Controls.TextBox> コントロールがデータベースの適切なフィールドにバインドされます。  
  
     [!code-xml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## 相互運用を使用したデータの表示  
 選択した顧客に対応する注文が、`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView?displayProperty=fullName> コントロールに表示されます。  `dataGridView1` コントロールは、分離コード ファイルのデータ ソースにバインドされています。  <xref:System.Windows.Forms.Integration.WindowsFormsHost> コントロールは、この [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] コントロールの親です。  
  
#### DataGridView コントロールにデータを表示するには  
  
-   次の XAML を <xref:System.Windows.Controls.Grid> 要素の宣言にコピーします。  
  
     [!code-xml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## プロジェクトへのデータ ソースの追加  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を使用すると、データ ソースをプロジェクトに簡単に追加できます。  この手順では、厳密に型指定されたデータ セットをプロジェクトに追加します。  選択されたテーブルごとのテーブル アダプターなどの他のサポート クラスもいくつか追加されます。  
  
#### データ ソースを追加するには  
  
1.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
2.  **データ ソース構成ウィザード**で、データセットを使用して、Northwind データベースへの接続を作成します。  詳細については、「[方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)」を参照してください。  
  
3.  データソース構成ウィザードからメッセージが表示されたら、接続文字列を `NorthwindConnectionString` として保存します。  
  
4.  データベース オブジェクトの選択を求められた場合は、`Customers` テーブルと `Orders` テーブルを選択し、生成されたデータセットに  `NorthwindDataSet` という名前を付けます。  
  
## データ ソースへのバインディング  
 <xref:System.Windows.Forms.BindingSource?displayProperty=fullName> コンポーネントは、アプリケーションのデータ ソースの統一されたインターフェイスを提供します。  データ ソースへのバインディングは、分離コード ファイルで実装されます。  
  
#### データ ソースにバインドするには  
  
1.  MainWindow.xaml.vb または MainWindow.xaml.cs という名前の分離コード ファイルを開きます。  
  
2.  次のコードを `MainWindow` クラス定義にコピーします。  
  
     このコードでは、<xref:System.Windows.Forms.BindingSource> コンポーネントと、データベースに接続する関連付けられたヘルパー クラスが宣言されます。  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  コンストラクターに次のコードをコピーします。  
  
     このコードでは、<xref:System.Windows.Forms.BindingSource> コンポーネントが作成および初期化されます。  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  MainWindow.xaml を開きます。  
  
5.  デザイン ビューまたは XAML ビューで、<xref:System.Windows.Window> 要素を選択します。  
  
6.  プロパティ ウィンドウの **\[イベント\]** タブをクリックします。  
  
7.  <xref:System.Windows.FrameworkElement.Loaded> イベントをダブルクリックします。  
  
8.  <xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーに次のコードをコピーします。  
  
     このコードでは、<xref:System.Windows.Forms.BindingSource> コンポーネントがデータ コンテキストとして割り当てられ、`Customers` および `Orders` アダプター オブジェクトが設定されます。  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. 次のコードを `MainWindow` クラス定義にコピーします。  
  
     このメソッドは <xref:System.Windows.Data.CollectionView.CurrentChanged> イベントを処理し、データ バインディングの現在の項目を更新します。  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. F5 キーを押してアプリケーションをビルドし、実行します。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [ハイブリッド アプリケーションでのデータ バインディングのサンプル](http://go.microsoft.com/fwlink/?LinkID=159983)   
 [チュートリアル: WPF での Windows フォーム複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [チュートリアル: Windows フォームでの WPF 複合コントロールのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)