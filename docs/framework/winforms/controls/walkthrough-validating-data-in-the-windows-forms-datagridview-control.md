---
title: "チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査 | Microsoft Docs"
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
  - "データ [Windows フォーム], 検証"
  - "データ グリッド, 検証 (データを)"
  - "データの妥当性検査, Windows フォーム"
  - "DataGridView コントロール [Windows フォーム], データの妥当性検査"
  - "検証 (データを), Windows フォーム"
  - "チュートリアル [Windows フォーム], DataGridView コントロール"
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査
データ入力機能をユーザーに表示する場合、フォームに入力されたデータの妥当性検査を行うことが必要になる場合があります。  <xref:System.Windows.Forms.DataGridView> クラスには、データがデータ ストアにコミットされる前に妥当性検査を実行できる便利な手段が用意されています。  現在のセルが変更されたときに <xref:System.Windows.Forms.DataGridView> で発生する <xref:System.Windows.Forms.DataGridView.CellValidating> イベントを処理することで、データの妥当性検査を行うことができます。  
  
 このチュートリアルでは、Northwind サンプル データベースの `Customers` テーブルから行を取得し、<xref:System.Windows.Forms.DataGridView> コントロールに表示します。  ユーザーが `CompanyName` 列のセルを編集し、そのセルから離れようとすると、<xref:System.Windows.Forms.DataGridView.CellValidating> イベント ハンドラーは新しい会社名文字列が空でないかどうかを確認し、新しい値が空の文字列の場合、<xref:System.Windows.Forms.DataGridView> は空でない文字列が入力されるまで、ユーザーのカーソルがそのセルから移動できないようにします。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : Windows フォーム DataGridView コントロールのデータを検証する](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
## フォームの作成  
  
#### DataGridView に入力されたデータの妥当性検査を行うには  
  
1.  <xref:System.Windows.Forms.Form> から派生し、<xref:System.Windows.Forms.DataGridView> コントロールおよび <xref:System.Windows.Forms.BindingSource> コンポーネントを含むクラスを作成します。  
  
     次のコード例は、基本的な初期化処理を行い、`Main` メソッドを含みます。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  フォームのクラス定義に、データベースへの接続の詳細を処理するメソッドを実装します。  
  
     このコード例では、データが入力された <xref:System.Data.DataTable> オブジェクトを返す  `GetData`  メソッドを使用します。  `connectionString` 変数には、使用するデータベースに適した値を設定してください。  
  
    > [!IMPORTANT]
    >  接続文字列内にパスワードなどの機密情報を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  <xref:System.Windows.Forms.DataGridView> と <xref:System.Windows.Forms.BindingSource> の初期化、およびデータ バインディングの設定を行うために、フォームの <xref:System.Windows.Forms.Form.Load> イベントのハンドラーを実装します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CellValidating> イベントおよび <xref:System.Windows.Forms.DataGridView.CellEndEdit> イベントのハンドラーを実装します。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating> イベント ハンドラーでは、`CompanyName` 列のセルの値が空であるかどうかを調べます。  セルの値が妥当性検査に合格しなかった場合は、<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=fullName> クラスの <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを `true` に設定します。  これにより、<xref:System.Windows.Forms.DataGridView> コントロールはカーソルがそのセルから移動することを禁止します。  その行の <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> プロパティに説明文字列を設定します。  これにより、エラー アイコンと、エラー テキストを含むツールヒントが表示されます。  <xref:System.Windows.Forms.DataGridView.CellEndEdit> イベント ハンドラーでは、行の <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> プロパティに空の文字列を設定します。  <xref:System.Windows.Forms.DataGridView.CellEndEdit> イベントは、セルの編集モードが終了した場合にのみ発生します。そのためには、セルが妥当性検査に合格することが必要です。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     <xref:System.Windows.Forms.DataGridView> に、`Customers` テーブルからのデータが入力されて表示されます。  `CompanyName` 列内のセルをダブルクリックすると、値を編集できます。  すべての文字を削除してから、Tab キーを押してそのセルから離れようとすると、<xref:System.Windows.Forms.DataGridView> によって阻止されます。  空でない文字列をセルに入力すると、<xref:System.Windows.Forms.DataGridView> コントロールはセルから離れることを許可します。  
  
## 次の手順  
 このアプリケーションでは、<xref:System.Windows.Forms.DataGridView> コントロールの機能について基本を理解できます。  次のような方法を使用すると、<xref:System.Windows.Forms.DataGridView> コントロールの外観および動作をカスタマイズできます。  
  
-   輪郭およびヘッダー スタイルを変更します。  詳細については、「[方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力の許可または制限。  詳細については、「[方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)」および「[方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   ユーザー入力に対するデータベース関連エラーの検査。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)」を参照してください。  
  
-   仮想モードを使用した大量のデータの処理。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
-   セルの外観をカスタマイズします。  詳細については、「[方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)」および「[方法 : Windows フォーム DataGridView コントロールのフォントと色のスタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータを検証する](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)