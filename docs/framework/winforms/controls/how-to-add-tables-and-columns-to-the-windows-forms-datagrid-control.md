---
title: "方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する | Microsoft Docs"
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
  - "列 [Windows フォーム], 追加 (DataGrid コントロールに)"
  - "DataGrid コントロール [Windows フォーム], 追加 (テーブルと列を)"
  - "テーブル [Windows フォーム], 追加 (DataGrid コントロールに)"
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロールのデータをテーブルおよび列に表示するには、**DataGridTableStyle** オブジェクトを作成して **GridTableStylesCollection** オブジェクトに追加します。GridTableStylesCollection オブジェクトには、<xref:System.Windows.Forms.DataGrid> コントロールの **TableStyles** プロパティを使用してアクセスできます。  各テーブル スタイルは、**DataGridTableStyle** オブジェクトの **MappingName** プロパティで指定されたデータ テーブルの内容を表示します。  既定では、列スタイルが指定されていないテーブル スタイルには、そのデータ テーブル内のすべての列が表示されます。  **GridColumnStylesCollection** オブジェクトに **DataGridColumnStyle** オブジェクトを追加することにより、テーブルから表示する列を制限できます。GridColumnStylesCollection オブジェクトには、各 **DataGridTableStyle** オブジェクトの **GridColumnStyles** プロパティを通してアクセスできます。  
  
### プログラムで DataGrid にテーブルおよび列を追加するには  
  
1.  データをテーブルに表示するには、まず <xref:System.Windows.Forms.DataGrid> コントロールをデータセットにバインドする必要があります。  詳細については、「[方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)」を参照してください。  
  
    > [!CAUTION]
    >  列スタイルをプログラムで指定する場合は、**DataGridTableStyle** オブジェクトを **GridTableStylesCollection** オブジェクトに追加する前に、必ず **DataGridColumnStyle** オブジェクトを作成して **GridColumnStylesCollection** オブジェクトに追加します。  空の **DataGridTableStyle** オブジェクトをコレクションに追加すると、**DataGridColumnStyle** オブジェクトが自動的に生成されます。  その結果、重複した **MappingName** 値で新しい **DataGridColumnStyle** オブジェクトを **GridColumnStylesCollection** オブジェクトに追加しようとすると、例外が発生します。  
  
2.  新しいテーブル スタイルを宣言し、そのマップ名を設定します。  
  
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
  
3.  新しい列スタイルを宣言し、そのマップ名とその他のプロパティを設定します。  
  
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
  
4.  **GridColumnStylesCollection** オブジェクトの **Add** メソッドを呼び出して、列をテーブル スタイルに追加します。  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  **GridTableStylesCollection** オブジェクトの **Add** メソッドを呼び出して、テーブル スタイルをデータ グリッドに追加します。  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## 参照  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)