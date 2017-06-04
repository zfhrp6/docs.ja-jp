---
title: "方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する | Microsoft Docs"
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
  - "DataGrid コントロール [Windows フォーム], 例"
  - "DataGrid コントロール [Windows フォーム], 検証 (入力を)"
  - "例 [Windows フォーム], DataGrid コントロール"
  - "ユーザー入力, 検証"
  - "検証, ユーザー入力"
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロールで使用できる入力データの検証には 2 種類の方法があります。  ユーザーが適切でないデータ型 \(たとえば整数型のセルに文字列\) を入力した場合、その入力された無効な値は既存の有効な値に置き換えられます。  このような入力データの検証は自動的に行われ、カスタマイズはできません。  
  
 もう一方の入力データの検証は、不適切なデータをすべて拒否する場合に使用できます。たとえば 1 以上の値が必要なフィールドに 0 を入力しようとする場合や、適切でない文字列を入力しようとする場合にそのデータを拒否します。  <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに対してイベント ハンドラーを記述することにより、データセット内で実施できます。  次に示す例では、<xref:System.Data.DataTable.ColumnChanging> イベントを使用しています。"Product" 列では特に不適切な値が許可されないためです。  <xref:System.Data.DataTable.RowChanging> イベントを使用すると、"End Date" 列の値が同一行の "Start Date" 列の値より後であることを確認できます。  
  
### ユーザー入力データを検証するには  
  
1.  適切なテーブルに対して <xref:System.Data.DataTable.ColumnChanging> イベントを処理するコードを記述します。  不適切な入力が検出された場合は、<xref:System.Data.DataRow> オブジェクトの <xref:System.Data.DataRow.SetColumnError%2A> メソッドを呼び出します。  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
             e.Row.SetColumnError(e.Column, "Product cannot be " & _  
             CType(badValue, String))  
          End If  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    //Handle column changing events on the Customers table  
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {  
  
       //Only check for errors in the Product column  
       if (e.Column.ColumnName.Equals("Product")) {  
  
          //Do not allow "Automobile" as a product  
          if (e.ProposedValue.Equals("Automobile")) {  
             object badValue = e.ProposedValue;  
             e.ProposedValue = "Bad Data";  
             e.Row.RowError = "The Product column contains an error";  
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);  
          }  
       }  
    }  
  
    ```  
  
2.  イベントにイベント ハンドラーを接続します。  
  
     フォームの <xref:System.Windows.Forms.Form.Load> イベントまたはコンストラクターに、次のコードを記述します。  
  
    ```vb  
    ' Assumes the grid is bound to a dataset called customersDataSet1  
    ' with a table called Customers.  
    ' Put this code in the form's Load event or its constructor.  
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging  
  
    ```  
  
    ```csharp  
    // Assumes the grid is bound to a dataset called customersDataSet1  
    // with a table called Customers.  
    // Put this code in the form's Load event or its constructor.  
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Data.DataTable.ColumnChanging>   
 <xref:System.Data.DataRow.SetColumnError%2A>   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)