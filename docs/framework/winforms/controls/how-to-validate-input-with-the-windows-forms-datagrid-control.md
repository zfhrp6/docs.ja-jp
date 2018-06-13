---
title: '方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: a01cb90b7cba596dafa56963dcf9c489deb3e21a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535894"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 入力の検証の 2 種類がある Windows フォームの使用可能な<xref:System.Windows.Forms.DataGrid>コントロール。 ユーザーがセル、たとえば、整数型に文字列のないデータ型の値を入力する場合、新しい値が無効ですが、古い値に置き換えられます。 この種類の入力の検証は自動的に行われ、カスタマイズすることはできません。  
  
 データすべて 0 の値より大きいか等しい 1、または不適切な文字列にする必要があるフィールドに例を拒否するのには、入力の検証の他の種類を使用できます。 これは、データセット内のイベント ハンドラーを記述して、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>イベント。 使用して次の例、<xref:System.Data.DataTable.ColumnChanging>イベント不正な値が"Product"列を具体的には許可されていないためです。 使用する場合があります、<xref:System.Data.DataTable.RowChanging>確認「終了日」列の値が同じ行の「開始日」の列より後のイベントです。  
  
### <a name="to-validate-user-input"></a>ユーザー入力を検証するには  
  
1.  処理するコードを記述、<xref:System.Data.DataTable.ColumnChanging>適切なテーブルのイベントです。 不適切な入力が検出されると、呼び出し、<xref:System.Data.DataRow.SetColumnError%2A>のメソッド、<xref:System.Data.DataRow>オブジェクト。  
  
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
  
2.  イベント ハンドラーをイベントに接続します。  
  
     フォームのコード内で、次の場所<xref:System.Windows.Forms.Form.Load>イベントまたはそのコンス トラクターです。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
