---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する | Microsoft Docs"
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
  - "セル, 設定 (スタイルを)"
  - "データ [Windows フォーム], 設定 (形式を)"
  - "データ形式"
  - "DataGridView コントロール [Windows フォーム], セル スタイル"
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する
<xref:System.Windows.Forms.DataGridView> コントロールを使用すると、コントロール全体、特定の列、行ヘッダーと列ヘッダー、および交互の行の既定のセル スタイルおよびセル データ形式を指定して、帳簿のような体裁にできます。  コントロール全体に設定されている既定のスタイルは、列および交互の行に設定した既定のスタイルによってオーバーライドされます。  また、個々の行およびセルに対してコードで設定したスタイルにより、既定のスタイルがオーバーライドされます。  
  
 セル スタイルの詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  交互の行のスタイルを設定する方法については、「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> プロパティを使用して、コントロールに追加するすべての行のスタイルを設定することもできます。  行テンプレートの詳細については、「[方法 : 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロール内のすべてのセルに既定のスタイルを設定するには  
  
1.  デザイナーで <xref:System.Windows.Forms.DataGridView> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> プロパティ、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> プロパティ、または <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  **\[CellStyle ビルダー\]** ダイアログ ボックスが表示されます。  
  
3.  プロパティを設定してスタイルを定義し、**プレビュー** ペインで選択内容を確認します。  
  
> [!NOTE]
>  visual スタイルが有効になっている場合は、行ヘッダーおよび列ヘッダー \(<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A> を除く\) のスタイルは現在のテーマによって自動的に設定され、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> プロパティと <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> プロパティの値がオーバーライドされます。  
>   
>  デザイナーを使用して、選択した複数の <xref:System.Windows.Forms.DataGridView> コントロールのセル スタイルを設定できます。ただし、コントロール間で、変更するセル スタイルのプロパティ値が同じである場合に限ります。  変更するプロパティの値がいずれかのセル スタイルで異なる場合、**\[CellStyle ビルダー\]** ダイアログ ボックスの **\[プロパティ\]** ウィンドウは空白になります。  
  
### 個々の列のセルに既定のスタイルを設定するには  
  
1.  デザイナーで <xref:System.Windows.Forms.DataGridView> コントロールを右クリックし、**\[列の編集\]** をクリックします。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[列のプロパティ\]** グリッドで、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  **\[CellStyle ビルダー\]** ダイアログ ボックスが表示されます。  
  
4.  プロパティを設定してスタイルを定義し、**プレビュー** ペインで選択内容を確認します。  
  
### セル内のデータを書式設定するには  
  
1.  上記の手順のいずれかを使用して、既定のセル スタイル プロパティに関連する **\[CellStyle ビルダー\]** ダイアログ ボックスを表示します。  
  
2.  **\[CellStyle ビルダー\]** ダイアログ ボックスで、<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  **\[書式文字列のダイアログ\]** ダイアログ ボックスが表示されます。  
  
3.  書式の種類を選択し、その詳細設定 \(小数点以下の表示桁数など\) を変更します。変更内容は **\[サンプル\]** ボックスで確認します。  
  
4.  null 値を格納している可能性があるデータ ソースに <xref:System.Windows.Forms.DataGridView> コントロールをバインドする場合は、**\[Null 値\]** ボックスに値を指定します。  ここで指定した値は、セルの値が null 参照 \(Visual Basic では `Nothing`\) または <xref:System.DBNull.Value?displayProperty=fullName> と等しい場合に表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)