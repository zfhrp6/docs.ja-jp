---
title: '方法 : デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
ms.openlocfilehash: 4b29a3040415cce8fad27abf9bf46aa3d3e14b4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>方法 : デザイナーを使って Windows フォーム DataGrid コントロールにテーブルと列を追加する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームでデータを表示することができます<xref:System.Windows.Forms.DataGrid>テーブルおよび列を作成してコントロール<xref:System.Windows.Forms.DataGridTableStyle>オブジェクトとに追加すること、<xref:System.Windows.Forms.GridTableStylesCollection>からアクセスできるオブジェクト、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティです。 各テーブルのスタイルで指定されたは、どのようなデータ テーブルの内容を表示する、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridTableStyle>です。 列スタイルを指定せず、テーブルのスタイルでは既定では、そのデータ テーブル内のすべての列が表示されます。 追加することによって表示される、テーブルから列を制限することができます<xref:System.Windows.Forms.DataGridColumnStyle>オブジェクトを<xref:System.Windows.Forms.GridColumnStylesCollection>、を通じてアクセスされますが、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>の各プロパティ<xref:System.Windows.Forms.DataGridTableStyle>です。  
  
 次の手順が必要な**Windows アプリケーション**を含むフォームを使用してプロジェクト、<xref:System.Windows.Forms.DataGrid>コントロール。 このようなプロジェクトを設定する方法については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。 既定で[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>コントロールに含まれていない、**ツールボックス**です。 追加の詳細については、次を参照してください。[する方法: ツールボックス アイテムの追加](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>デザイナーで、DataGrid コントロールにテーブルを追加するには  
  
1.  テーブルにデータを表示するためにする必要がありますまずバインド、<xref:System.Windows.Forms.DataGrid>データセットを制御します。 詳細については、次を参照してください。[する方法: Windows フォーム DataGrid コントロールをバインドするデータ ソース デザイナーを使用して、](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)です。  
  
2.  選択、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティ ウィンドウでプロパティの省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横にこのプロパティを表示、 **DataGridTableStyle コレクション エディター**です。  
  
3.  コレクション エディターで、**追加**テーブル スタイルを挿入します。  
  
4.  をクリックして**OK**コレクション エディターを閉じてから開き、次に省略記号ボタンをクリックする、<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティです。  
  
     コレクション エディターを開くと、コントロールにバインドされているすべてのデータ テーブルは、のドロップダウン リストに表示されます、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>テーブル スタイルのプロパティです。  
  
5.  **メンバー**ボックス コレクション エディターのテーブルのスタイルをクリックします。  
  
6.  **プロパティ**コレクション エディターでは、select のボックス、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>を表示するテーブルの値。  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>デザイナーで、DataGrid コントロールに列を追加するには  
  
1.  **メンバー**のボックス、 **DataGridTableStyle コレクション エディター**、適切なテーブルのスタイルを選択します。 **プロパティ**コレクション エディターでは、select のボックス、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>コレクション、省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を表示するプロパティの横に、 **DataGridColumnStyle コレクション エディター**です。  
  
2.  コレクション エディターで、**追加**を列のスタイルを挿入または横に、下矢印をクリックする**追加**列の種類を指定します。  
  
     ドロップダウン ボックスで、いずれかを選択できます、<xref:System.Windows.Forms.DataGridTextBoxColumn>または<xref:System.Windows.Forms.DataGridBoolColumn>型です。  
  
3.  閉じるには、[ok] をクリックして、 **DataGridColumnStyle コレクション エディター**、横にある省略記号ボタンをクリックすると、再度開くと、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティです。  
  
     コレクション エディターを開くと、バインドされたデータ テーブル内のデータ列は、のドロップダウン リストに表示されます、<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>列スタイルのプロパティです。  
  
4.  **メンバー**ボックス コレクション エディターの列のスタイルをクリックします。  
  
5.  **プロパティ**コレクション エディターでは、select のボックス、<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>を表示する列の値。  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
