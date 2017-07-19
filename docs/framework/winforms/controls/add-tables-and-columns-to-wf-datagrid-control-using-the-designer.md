---
title: "方法 : デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列 [Windows フォーム], 追加 (DataGrid コントロールに)"
  - "DataGrid コントロール [Windows フォーム], 追加 (テーブルと列を)"
  - "テーブル [Windows フォーム], 追加 (DataGrid コントロールに)"
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロールのデータをテーブルおよび列に表示するには、<xref:System.Windows.Forms.DataGridTableStyle> オブジェクトを作成して <xref:System.Windows.Forms.GridTableStylesCollection> オブジェクトに追加します。GridTableStylesCollection オブジェクトには、<xref:System.Windows.Forms.DataGrid> コントロールの <xref:System.Windows.Forms.DataGrid.TableStyles%2A> プロパティを使用してアクセスできます。  各テーブル スタイルは、<xref:System.Windows.Forms.DataGridTableStyle> の <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> プロパティで指定されたデータ テーブルの内容を表示します。  既定では、列スタイルが指定されていないテーブル スタイルには、そのデータ テーブル内のすべての列が表示されます。  テーブルから表示される列を制限するには、<xref:System.Windows.Forms.DataGridColumnStyle> オブジェクトを <xref:System.Windows.Forms.GridColumnStylesCollection> に追加します。<xref:System.Windows.Forms.GridColumnStylesCollection> にアクセスするには、各 <xref:System.Windows.Forms.DataGridTableStyle> の <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> プロパティを使用します。  
  
 次の手順では、<xref:System.Windows.Forms.DataGrid> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、既定で <xref:System.Windows.Forms.DataGrid> コントロールは**ツールボックス**に含まれていません。  コントロールの追加の詳細については、「[How to: Add Items to the Toolbox](http://msdn.microsoft.com/ja-jp/458e119e-17fe-450b-b889-e31c128bd7e0)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーで DataGrid コントロールにテーブルを追加するには  
  
1.  データをテーブルに表示するには、まず <xref:System.Windows.Forms.DataGrid> コントロールをデータセットにバインドする必要があります。  詳細については、「[方法 : デザイナーを使ってデータ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)」を参照してください。  
  
2.  \[プロパティ\] ウィンドウで <xref:System.Windows.Forms.DataGrid> コントロールの <xref:System.Windows.Forms.DataGrid.TableStyles%2A> プロパティを選択し、プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして **DataGridTableStyle コレクション エディター**を表示します。  
  
3.  コレクション エディターで、**\[追加\]** をクリックしてテーブル スタイルを挿入します。  
  
4.  **\[OK\]** をクリックしてコレクション エディターを閉じ、<xref:System.Windows.Forms.DataGrid.TableStyles%2A> プロパティの省略記号ボタンをクリックして再び開きます。  
  
     コレクション エディターを再び開くと、コントロールに連結されているデータ テーブルが、テーブル スタイルの <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> プロパティのドロップダウン リストに表示されます。  
  
5.  コレクション エディターの **\[メンバー\]** ボックスで、テーブル スタイルをクリックします。  
  
6.  コレクション エディターの **\[プロパティ\]** ボックスで、表示するテーブルの <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 値を選択します。  
  
### デザイナーで DataGrid コントロールに列を追加するには  
  
1.  **DataGridTableStyle** コレクション エディターの **\[メンバー\]** ボックスで、適切なテーブル スタイルを選択します。  コレクション エディターの **\[プロパティ\]** ボックスで <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> コレクションを選択し、プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして **DataGridColumnStyle コレクション エディター**を開きます。  
  
2.  コレクション エディターで、**\[追加\]** をクリックして列スタイルを挿入するか、**\[追加\]** の横にある下向きの矢印をクリックして列の種類を指定します。  
  
     ドロップダウン リストからは、<xref:System.Windows.Forms.DataGridTextBoxColumn> または <xref:System.Windows.Forms.DataGridBoolColumn> を選択できます。  
  
3.  \[OK\] をクリックして **DataGridColumnStyle コレクション エディター**を閉じ、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> プロパティの省略記号ボタンをクリックして再び開きます。  
  
     コレクション エディターを再び開くと、連結されているテーブル内のデータ列が、列スタイルの <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> プロパティのドロップダウン リストに表示されます。  
  
4.  コレクション エディターの **\[メンバー\]** ボックスで、列スタイルをクリックします。  
  
5.  コレクション エディターの **\[プロパティ\]** ボックスで、表示する列の <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> 値を選択します。  
  
## 参照  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)