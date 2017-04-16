---
title: "方法 : デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する | Microsoft Docs"
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
  - "色, 適用 (DataGrid コントロールに)"
  - "列 [Windows フォーム], DataGrid コントロール"
  - "DataGrid コントロール [Windows フォーム], 既定のスタイル"
  - "DataGrid コントロール [Windows フォーム], 書式指定"
  - "書式設定 [Windows フォーム]"
  - "テーブル [Windows フォーム], 書式指定 (DataGrid コントロールでの)"
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGrid> コントロールの各部分に異なる色を付けると、コントロールの情報が読みやすく、解釈しやすくなります。  行および列の色を指定できます。  また、行および列の表示\/非表示を切り替えることもできます。  
  
 <xref:System.Windows.Forms.DataGrid> コントロールの書式設定には、3 つの基本的な段階があります。  
  
-   プロパティを設定して、データを表示する既定のスタイルを設定できます。  
  
-   設定したスタイルに基づいて、実行時に特定のテーブルを表示する方法をカスタマイズできます。  
  
-   最後に、データ グリッドに表示する列、および表示する色やその他の書式を変更できます。  
  
 データ グリッドの書式設定の最初の手順として、<xref:System.Windows.Forms.DataGrid> 自体のプロパティを設定できます。  ここで選択した色および書式を基本として、表示するデータ テーブルおよび列に応じた変更を加えることができます。  
  
 次の手順では、<xref:System.Windows.Forms.DataGrid> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] では、既定で <xref:System.Windows.Forms.DataGrid> コントロールは**ツールボックス**に含まれていません。  詳細については、「[How to: Add Items to the Toolbox](http://msdn.microsoft.com/ja-jp/458e119e-17fe-450b-b889-e31c128bd7e0)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### DataGrid コントロールの既定のスタイルを設定するには  
  
1.  <xref:System.Windows.Forms.DataGrid> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、次のプロパティを適切に設定します。  
  
    |プロパティ|Description|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` プロパティは、グリッドの偶数番号の行の色を定義します。  <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> プロパティを異なる色に設定すると、1 行おきにこの新しい色が設定されます \(行 1、3、5 など\)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|グリッドの偶数番号の行 \(行 0、2、4、6 など\) の背景色。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A> プロパティと <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> プロパティはグリッドの行の色を決定しますが、<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> プロパティは行領域の外の領域の色を決定します。この領域は、グリッドが一番下までスクロールされたときや、グリッドに数行しか含まれていない場合にだけ表示されます。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|グリッドの境界線スタイル。<xref:System.Windows.Forms.BorderStyle> 列挙値の 1 つです。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|グリッドのウィンドウ キャプションの背景色。ウィンドウ キャプションは、グリッドのすぐ上に表示されます。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|グリッドの上部のキャプションのフォント。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|グリッドのウィンドウ キャプションの背景色。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|グリッドのテキストの表示に使用されるフォント。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|データ グリッドの行に表示されるデータのフォントの色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|データ グリッドのグリッド線の色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|グリッドのセル間の線のスタイル。<xref:System.Windows.Forms.DataGridLineStyle> 列挙値の 1 つです。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|行ヘッダーと列ヘッダーの背景色。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|列ヘッダーに使用されるフォント。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|グリッドの列ヘッダーの前景色。列ヘッダーのテキストおよびプラス\/マイナス グリフも含まれます。プラス記号 \(\+\)\/マイナス記号 \(\-\) グリフは、複数の関連するテーブルが表示されているときに行を展開するために使用します。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|データ グリッド内のすべてのリンク テキストの色。子テーブル、リレーションシップ名などへのリンクが含まれます。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|子テーブルに表示される親テーブルの行の背景色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|子テーブルに表示される親テーブルの行の前景色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|親テーブルの行にテーブル名と列名が表示されるかどうかを決定します。<xref:System.Windows.Forms.DataGridParentRowsLabelStyle> 列挙型を使用します。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|グリッドの列の既定の幅 \(ピクセル単位\)。  このプロパティは、<xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティと <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティをリセットする前に設定してください。リセットした後で設定しても無効です。これらのプロパティは、別個にリセットするか、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用してリセットします。<br /><br /> このプロパティは、0 未満の値には設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|グリッドの行の高さ \(ピクセル単位\)。  このプロパティは、<xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティと <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティをリセットする前に設定してください。リセットした後で設定しても無効です。これらのプロパティは、別個にリセットするか、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用してリセットします。<br /><br /> このプロパティは、0 未満の値には設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|グリッドの行ヘッダーの幅。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|行またはセルが選択されたときの背景色。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|行またはセルが選択されたときの前景色。|  
  
    > [!NOTE]
    >  コントロールの色をカスタマイズするときには、不適切な色の選択 \(赤と緑など\) によってコントロールがアクセスできなくなる可能性があることに注意してください。  この問題を避けるには、**\[システム カラー\]** パレットに含まれる色を使用します。  
  
     次のプロシージャには、データ テーブルにバインドされた <xref:System.Windows.Forms.DataGrid> コントロールが必要です。  詳細については、「[方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)」を参照してください。  
  
### デザイン時にデータ テーブルのテーブル スタイルと列スタイルを設定するには  
  
1.  フォームで <xref:System.Windows.Forms.DataGrid> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.DataGrid.TableStyles%2A> プロパティを選択し、**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
3.  **\[DataGridTableStyle コレクション エディター\]** ダイアログ ボックスの **\[追加\]** をクリックしてテーブル スタイルをコレクションに追加します。  
  
     **DataGridTableStyle コレクション エディター**では、テーブル スタイルの追加または削除、表示やレイアウトのプロパティの設定、テーブル スタイルのマッピング名の設定をすることができます。  
  
4.  <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> プロパティを各テーブル スタイルのマッピング名に設定します。  
  
     マッピング名を使用して、どのテーブルでどのテーブル スタイルを使用するかを指定します。  
  
5.  **DataGridTableStyle コレクション エディター**で、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> プロパティを選択し、省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
6.  **\[DataGridColumnStyle コレクション エディター\]** ダイアログ ボックスで、作成したテーブル スタイルに列スタイルを追加します。  
  
     **DataGridColumnStyle コレクション エディター**では、列スタイルの追加または削除、表示やレイアウトのプロパティの設定、データ列のマッピング名および書式指定文字列の設定をすることができます。  
  
    > [!NOTE]
    >  書式指定文字列の詳細については、「[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.GridTableStylesCollection>   
 <xref:System.Windows.Forms.GridColumnStylesCollection>   
 <xref:System.Windows.Forms.DataGrid>   
 [方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)