---
title: "チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "データ エントリ, エラー処理"
  - "データ グリッド, エラー処理"
  - "DataGridView コントロール [Windows フォーム], エラー処理"
  - "エラー処理, データ エントリ"
  - "エラー処理, DataGridView コントロール"
  - "チュートリアル [Windows フォーム], DataGridView コントロール"
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理
データ入力アプリケーションでは、基になるデータ ストアのエラーを処理する機能が必須です。  Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールは、データ ストアが制約違反またはビジネス ルール違反を検出したときに発生する <xref:System.Windows.Forms.DataGridView.DataError> イベントを公開することで、これを簡単に実現しています。  
  
 このチュートリアルでは、Northwind サンプル データベースの `Customers` テーブルから行を取得し、<xref:System.Windows.Forms.DataGridView> コントロールに表示します。  新規行または編集された既存行の中で重複する `CustomerID` 値が検出されたときは、<xref:System.Windows.Forms.DataGridView.DataError> イベントが発生するので、この例外について説明する <xref:System.Windows.Forms.MessageBox> を表示することでイベントを処理します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーを処理する](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
## フォームの作成  
  
#### DataGridView コントロール内のデータ入力エラーを処理するには  
  
1.  <xref:System.Windows.Forms.Form> から派生し、<xref:System.Windows.Forms.DataGridView> コントロールおよび <xref:System.Windows.Forms.BindingSource> コンポーネントを含むクラスを作成します。  
  
     次のコード例は、基本的な初期化処理を行い、`Main` メソッドを含みます。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  フォームのクラス定義に、データベースへの接続の詳細を処理するメソッドを実装します。  
  
     このコード例では、データが入力された <xref:System.Data.DataTable> オブジェクトを返す  `GetData`  メソッドを使用します。  `connectionString` 変数には、使用するデータベースに適した値を設定してください。  
  
    > [!IMPORTANT]
    >  接続文字列内にパスワードなどの機密情報を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  <xref:System.Windows.Forms.DataGridView> と <xref:System.Windows.Forms.BindingSource> の初期化、およびデータ バインディングの設定を行うために、フォームの <xref:System.Windows.Forms.Form.Load> イベントのハンドラーを実装します。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  <xref:System.Windows.Forms.DataGridView> の <xref:System.Windows.Forms.DataGridView.DataError> イベントを処理します。  
  
     エラーのコンテキストがコミット操作である場合は、エラーを <xref:System.Windows.Forms.MessageBox> に表示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     <xref:System.Windows.Forms.DataGridView> コントロールに Customers テーブルのデータが読み込まれることを確認します。  `CustomerID` に重複する値を入力して編集内容をコミットすると、セルの値が自動的に元に戻り、データ入力エラーを示す <xref:System.Windows.Forms.MessageBox> が表示されます。  
  
## 次の手順  
 このアプリケーションでは、<xref:System.Windows.Forms.DataGridView> コントロールの機能について基本を理解できます。  次のような方法を使用すると、<xref:System.Windows.Forms.DataGridView> コントロールの外観および動作をカスタマイズできます。  
  
-   輪郭およびヘッダー スタイルを変更します。  詳細については、「[方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力の許可または制限。  詳細については、「[方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)」および「[方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力を検証します。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   仮想モードを使用した大量のデータの処理。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
-   セルの外観をカスタマイズします。  詳細については、「[方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)」および「[方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーを処理する](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)