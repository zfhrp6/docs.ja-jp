---
title: 'チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 230d2c6843f9ae80126d9d0a2c949982aae24c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する
このチュートリアルで、SQL Server データベースからデータを取得およびそのデータを表示、<xref:System.Windows.Controls.DataGrid>コントロール。 LINQ を使用して、エンティティ クラスから指定されたデータを取得するクエリを記述するのにと、データを表すエンティティ クラスを作成するのにには、ADO.NET Entity Framework を使用します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]。  
  
-   SQL Server または SQL Server Express が付属している、AdventureWorks サンプル データベースがあるの実行中のインスタンスへのアクセス。 AdventureWorks データベースをダウンロードすることができます、 [GitHub](https://github.com/Microsoft/sql-server-samples/releases)です。  
  
### <a name="to-create-entity-classes"></a>エンティティ クラスを作成するには  
  
1.  Visual Basic または C# の場合で新しい WPF アプリケーション プロジェクトを作成し、名前`DataGridSQLExample`です。  
  
2.  ソリューション エクスプ ローラーでプロジェクトを右クリックし、**追加**、し、**新しい項目の**します。  
  
     [新しい項目の追加] ダイアログ ボックスが表示されます。  
  
3.  インストールされたテンプレート ペインで選択**データ**、テンプレートの一覧で選択および**ADO.NET エンティティ データ モデル**l です。  
  
     ![ADO.NET エンティティ データ モデルを選択して](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  ファイルの名前を付けます`AdventureWorksModel.edmx` をクリックし、**追加**です。  
  
     Entity Data Model ウィザードが表示されます。  
  
5.  モデルのコンテンツの選択 画面で、次のように選択します。**データベースから生成** をクリックし、**次**です。  
  
     ![データベース オプションから生成 を選択](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  データ接続の選択 画面で、AdventureWorksLT2008 データベースへの接続を提供します。 詳細については、次を参照してください。[を選択して、データ接続 ダイアログ ボックス](http://go.microsoft.com/fwlink/?LinkId=160190)です。  
  
     ![データベースへの接続を提供](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  名があるかどうかを確認`AdventureWorksLT2008Entities`ことと、**エンティティ接続設定を付けて App.Config に保存** チェック ボックスを選択して、をクリックして**次**です。  
  
8.  データベース オブジェクトの選択 画面で、テーブル ノードを展開し、選択、**製品**と**ProductCategory**テーブル。  
  
     テーブルのすべてのエンティティ クラスを生成することができます。ただし、この例でのみデータを取得する 2 つのテーブルからです。  
  
     ![テーブルからの Product および ProductCategory の選択](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. **[完了]** をクリックします。  
  
     エンティティ デザイナーで、Product および ProductCategory エンティティが表示されます。  
  
     ![Product および ProductCategory エンティティ モデル](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>取得して、データの表示  
  
1.  MainWindow.xaml ファイルを開きます。  
  
2.  設定、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを<xref:System.Windows.Window>450 にします。  
  
3.  XAML エディターで、次のコードを追加<xref:System.Windows.Controls.DataGrid>タグの間、`<Grid>`と`</Grid>`タグを追加する、<xref:System.Windows.Controls.DataGrid>という`dataGrid1`です。  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![DataGrid のあるウィンドウ](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  <xref:System.Windows.Window> を選択します。  
  
5.  イベント ハンドラーを作成する [プロパティ] ウィンドウまたは XAML エディターを使用して、<xref:System.Windows.Window>という`Window_Loaded`の<xref:System.Windows.FrameworkElement.Loaded>イベント。 詳細については、次を参照してください。[する方法: 単純なイベント ハンドラーを作成する](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480)です。  
  
     次は、MainWindow.xaml の XAML を示します。  
  
    > [!NOTE]
    >  Visual Basic で MainWindow.xaml の最初の行を使用している場合は置き換えます`x:Class="DataGridSQLExample.MainWindow"`で`x:Class="MainWindow"`です。  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  分離コード ファイル (MainWindow.xaml.vb または MainWindow.xaml.cs) を開き、<xref:System.Windows.Window>です。  
  
7.  結合されたテーブルから特定の値を取得および設定するには、次のコードを追加、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.DataGrid>クエリの結果にします。  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  例を実行します。  
  
     参照する必要があります、<xref:System.Windows.Controls.DataGrid>データを表示します。  
  
     ![SQL データベースからデータがある DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>次の手順  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.DataGrid>  
 [方法は i: どこから始めたら WPF アプリケーションで Entity Framework としますか。](http://go.microsoft.com/fwlink/?LinkId=159868)
