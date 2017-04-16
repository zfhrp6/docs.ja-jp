---
title: "チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成 | Microsoft Docs"
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
  - "データ [Windows フォーム], 表示 (データ ソースにバインドせずに)"
  - "データ [Windows フォーム], バインドされていない"
  - "DataGridView コントロール [Windows フォーム], 表示 (データ ソースにバインドせずにデータを)"
  - "DataGridView コントロール [Windows フォーム], バインドされていないデータ"
  - "チュートリアル [Windows フォーム], DataGridView コントロール"
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成
データベースから取得したものではないデータを表形式で表示しなければならない場合はよくあります。  たとえば、文字列の 2 次元配列の内容を表示する場合などです。  <xref:System.Windows.Forms.DataGridView> クラスは、データ ソースにバインドせずにデータを表示するための、簡単で高度にカスタマイズ可能な手段となります。  このチュートリアルでは、<xref:System.Windows.Forms.DataGridView> コントロールのデータを手動で作成し、行の追加と削除を非バインド モードで管理する方法を示します。  既定では、ユーザーが新しい行を追加できます。  行の追加を防ぐには、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティを `false` に設定します。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : 連結されていない Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)」を参照してください。  
  
## フォームの作成  
  
#### バインドされていない DataGridView コントロールを使用するには  
  
1.  <xref:System.Windows.Forms.Form> から派生したクラスを作成し、次の変数宣言と `Main` メソッドを含めます。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  フォームのクラス定義の中に、フォームのレイアウトをセットアップするための `SetupLayout` メソッドを実装します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  <xref:System.Windows.Forms.DataGridView> の列とプロパティをセットアップするための `SetupDataGridView` メソッドを作成します。  
  
     このメソッドでは、まず <xref:System.Windows.Forms.DataGridView> コントロールをフォームの <xref:System.Windows.Forms.Control.Controls%2A> コレクションに追加します。  次に、<xref:System.Windows.Forms.DataGridView.ColumnCount%2A> プロパティを使用して、表示する列の数を設定します。  さらに、列ヘッダーの既定のスタイルを設定するために、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> プロパティによって返される <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>、および <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> プロパティを設定します。  
  
     レイアウトと外観に関するプロパティを設定したら、次は列名を割り当てます。  このメソッドが終了すると、<xref:System.Windows.Forms.DataGridView> コントロールにデータを追加できる状態になります。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  <xref:System.Windows.Forms.DataGridView> コントロールに行を追加するための `PopulateDataGridView` メソッドを作成します。  
  
     各行は、歌とその関連情報を表しています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  ユーティリティ メソッドを定義したら、次はイベント ハンドラーを追加します。  
  
     **\[Add\]** ボタンと **\[Delete\]** ボタンの <xref:System.Windows.Forms.Control.Click> イベント、フォームの <xref:System.Windows.Forms.Form.Load> イベント、さらに <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントを処理します。  
  
     **\[Add\]** ボタンの <xref:System.Windows.Forms.Control.Click> イベントが発生したときは、新しい空の行を <xref:System.Windows.Forms.DataGridView> に追加します。  
  
     **\[Delete\]** ボタンの <xref:System.Windows.Forms.Control.Click> イベントが発生したときは、選択中の行が新規レコード用の行 \(ユーザーが新しい行を追加するときに使用\) でない限り、選択中の行を削除します。  この行は、必ず <xref:System.Windows.Forms.DataGridView> コントロールの最後の行になります。  
  
     フォームの <xref:System.Windows.Forms.Form.Load> イベントが発生したときは、`SetupLayout`、`SetupDataGridView`、`PopulateDataGridView` というユーティリティ メソッドを呼び出します。  
  
     <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントが発生したときは、`Date` 列の各セルを長い形式の日付に書式設定します \(セルの値が解析できない場合を除く\)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     `PopulateDataGridView` 内で指定した歌の一覧を含む <xref:System.Windows.Forms.DataGridView> コントロールが表示されます。  **\[Add Row\]** ボタンをクリックすると新しい行を追加でき、**\[Delete Row\]** ボタンをクリックすると選択中の行を削除できます。  このバインドされていない <xref:System.Windows.Forms.DataGridView> コントロールはそれ自体がデータ ストアであり、このデータは <xref:System.Data.DataSet> や配列などの外部ソースに依存していません。  
  
## 次の手順  
 このアプリケーションでは、<xref:System.Windows.Forms.DataGridView> コントロールの機能について基本を理解できます。  次のような方法を使用すると、<xref:System.Windows.Forms.DataGridView> コントロールの外観および動作をカスタマイズできます。  
  
-   輪郭およびヘッダー スタイルを変更します。  詳細については、「[方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力の許可または制限。  詳細については、「[方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)」および「[方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   ユーザー入力に対するデータベース関連エラーの検査。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)」を参照してください。  
  
-   仮想モードを使用した大量のデータの処理。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
-   セルの外観をカスタマイズします。  詳細については、「[方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)」および「[方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : 連結されていない Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)