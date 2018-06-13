---
title: '方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: fc8161ea29da92f5dcc2e76f956f3fecd6140acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527720"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームでデータを表示することができます<xref:System.Windows.Forms.DataGrid>テーブルおよび列を作成してコントロール**DataGridTableStyle**オブジェクトとに追加すること、 **GridTableStylesCollection**オブジェクトは使用してアクセス、<xref:System.Windows.Forms.DataGrid>コントロールの**TableStyles**プロパティです。 各テーブルのスタイルで指定されたは、どのようなデータ テーブルの内容を表示する、 **DataGridTableStyle**オブジェクトの**MappingName**プロパティです。 テーブル スタイルが指定されていない列のスタイルでは既定では、そのデータ テーブル内のすべての列が表示されます。 追加することによって表示される、テーブルから列を制限する**DataGridColumnStyle**オブジェクトを**GridColumnStylesCollection**からアクセスできるオブジェクト、 **GridColumnStyles**の各プロパティ**DataGridTableStyle**オブジェクト。  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>データ グリッドに、テーブルと列をプログラムで追加するには  
  
1.  テーブルにデータを表示するためにする必要がありますまずバインド、<xref:System.Windows.Forms.DataGrid>データセットを制御します。 詳細については、次を参照してください。[する方法: Windows フォーム DataGrid コントロールをデータ ソースにバインド](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)です。  
  
    > [!CAUTION]
    >  列のスタイルをプログラムで指定する場合は常に作成する**DataGridColumnStyle**オブジェクトに追加して、 **GridColumnStylesCollection**追加する前にオブジェクト**DataGridTableStyle**オブジェクトを**GridTableStylesCollection**オブジェクト。 空の追加と**DataGridTableStyle** 、コレクションにオブジェクトを**DataGridColumnStyle**オブジェクトが自動的に生成されます。 新規追加しようとする場合に、例外がスローされますその結果、 **DataGridColumnStyle**オブジェクトが複製によって**MappingName**値を**GridColumnStylesCollection**オブジェクト。  
  
2.  新しいテーブルのスタイルを宣言し、そのマップ名を設定します。  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  新しい列のスタイルを宣言し、そのマップ名やその他のプロパティを設定します。  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  呼び出す、**追加**のメソッド、 **GridColumnStylesCollection**テーブルのスタイルに列を追加するオブジェクト  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  呼び出す、**追加**のメソッド、 **GridTableStylesCollection**データ グリッドにテーブルのスタイルを追加するオブジェクト。  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
