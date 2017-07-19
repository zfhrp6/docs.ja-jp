---
title: "方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする | Microsoft Docs"
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
  - "列 [Windows フォーム], 削除 (データ グリッド内で)"
  - "列 [Windows フォーム], 非表示"
  - "データ グリッド, 削除 (列を)"
  - "データ グリッド, 非表示 (列を)"
  - "DataGrid コントロール [Windows フォーム], 削除 (列を)"
  - "DataGrid コントロール [Windows フォーム], 非表示 (列を)"
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridTableStyle> クラスのメンバーである <xref:System.Windows.Forms.GridColumnStylesCollection> オブジェクトと <xref:System.Windows.Forms.DataGridColumnStyle> オブジェクトのプロパティおよびメソッドを使用して、Windows フォーム <xref:System.Windows.Forms.DataGrid> コントロールの列をプログラムで削除したり非表示にしたりできます。  
  
 削除した列や非表示にした列は、グリッドが連結されているデータ ソースに引き続き含まれていて、プログラムでアクセスできます。  単にデータ グリッドに表示されないだけです。  
  
> [!NOTE]
>  アプリケーションがデータの特定の列にアクセスせず、それらの列をデータ グリッドに表示する必要がないのであれば、通常はそれらの列をデータ ソースに含める必要性はありません。  
  
### プログラムで DataGrid から列を削除するには  
  
1.  フォームの宣言領域で、<xref:System.Windows.Forms.DataGridTableStyle> クラスの新しいインスタンスを宣言します。  
  
2.  <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=fullName> プロパティに、スタイルを適用するデータ ソース内のテーブルを設定します。  次の例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName> プロパティを使用しています。このプロパティは既に設定されていると仮定しています。  
  
3.  データ グリッドのテーブル スタイル コレクションに新しい <xref:System.Windows.Forms.DataGridTableStyle> オブジェクトを追加します。  
  
4.  削除する列の列インデックスを指定して、<xref:System.Windows.Forms.DataGrid> の <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> コレクションの <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> メソッドを呼び出します。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### プログラムで DataGrid の列を非表示にするには  
  
1.  フォームの宣言領域で、<xref:System.Windows.Forms.DataGridTableStyle> クラスの新しいインスタンスを宣言します。  
  
2.  <xref:System.Windows.Forms.DataGridTableStyle> の <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> プロパティに、スタイルを適用するデータ ソース内のテーブルを設定します。  次のコード例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName> プロパティを使用しています。このプロパティは既に設定されていると仮定しています。  
  
3.  データ グリッドのテーブル スタイル コレクションに新しい <xref:System.Windows.Forms.DataGridTableStyle> オブジェクトを追加します。  
  
4.  非表示にする列の列インデックスを指定して `Width`  プロパティを 0 に設定すると、列が非表示になります。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## 参照  
 [方法 : Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)   
 [方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)