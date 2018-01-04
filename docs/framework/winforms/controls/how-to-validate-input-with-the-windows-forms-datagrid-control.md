---
title: "方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88cdc7914c301af0f0f244f935b986fb78ec775e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="7b0a6-102">方法 : Windows フォームの DataGrid コントロールを使用して入力データを検証する</span><span class="sxs-lookup"><span data-stu-id="7b0a6-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="7b0a6-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7b0a6-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="7b0a6-105">入力の検証の 2 種類がある Windows フォームの使用可能な<xref:System.Windows.Forms.DataGrid>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="7b0a6-106">ユーザーがセル、たとえば、整数型に文字列のないデータ型の値を入力する場合、新しい値が無効ですが、古い値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="7b0a6-107">この種類の入力の検証は自動的に行われ、カスタマイズすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-107">This kind of input validation is done automatically and cannot be customized.</span></span>  
  
 <span data-ttu-id="7b0a6-108">データすべて 0 の値より大きいか等しい 1、または不適切な文字列にする必要があるフィールドに例を拒否するのには、入力の検証の他の種類を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="7b0a6-109">これは、データセット内のイベント ハンドラーを記述して、<xref:System.Data.DataTable.ColumnChanging>または<xref:System.Data.DataTable.RowChanging>イベント。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="7b0a6-110">使用して次の例、<xref:System.Data.DataTable.ColumnChanging>イベント不正な値が"Product"列を具体的には許可されていないためです。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="7b0a6-111">使用する場合があります、<xref:System.Data.DataTable.RowChanging>確認「終了日」列の値が同じ行の「開始日」の列より後のイベントです。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>  
  
### <a name="to-validate-user-input"></a><span data-ttu-id="7b0a6-112">ユーザー入力を検証するには</span><span class="sxs-lookup"><span data-stu-id="7b0a6-112">To validate user input</span></span>  
  
1.  <span data-ttu-id="7b0a6-113">処理するコードを記述、<xref:System.Data.DataTable.ColumnChanging>適切なテーブルのイベントです。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="7b0a6-114">不適切な入力が検出されると、呼び出し、<xref:System.Data.DataRow.SetColumnError%2A>のメソッド、<xref:System.Data.DataRow>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>  
  
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
  
2.  <span data-ttu-id="7b0a6-115">イベント ハンドラーをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-115">Connect the event handler to the event.</span></span>  
  
     <span data-ttu-id="7b0a6-116">フォームのコード内で、次の場所<xref:System.Windows.Forms.Form.Load>イベントまたはそのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="7b0a6-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b0a6-117">参照</span><span class="sxs-lookup"><span data-stu-id="7b0a6-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [<span data-ttu-id="7b0a6-118">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="7b0a6-118">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
