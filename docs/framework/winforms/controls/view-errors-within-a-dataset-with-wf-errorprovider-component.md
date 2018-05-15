---
title: '方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
ms.openlocfilehash: f00d874f2a4afcea3498a64fe946a93c83eb7b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="54652-102">方法 : Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する</span><span class="sxs-lookup"><span data-stu-id="54652-102">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="54652-103">Windows フォームを使用することができます<xref:System.Windows.Forms.ErrorProvider>データセットまたはその他のデータ ソース内で列エラーを表示するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="54652-103">You can use the Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to view column errors within a dataset or other data source.</span></span> <span data-ttu-id="54652-104"><xref:System.Windows.Forms.ErrorProvider>フォームのデータのエラーを表示するコンポーネントであるがないコントロールに直接関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="54652-104">For an <xref:System.Windows.Forms.ErrorProvider> component to display data errors on a form, it does not have to be directly associated with a control.</span></span> <span data-ttu-id="54652-105">データ ソースにバインドされていると、同じデータ ソースにバインドされている任意のコントロールの横にエラー アイコンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="54652-105">Once it is bound to a data source, it can display an error icon next to any control that is bound to the same data source.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54652-106">エラー プロバイダーを変更する場合<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>と<xref:System.Windows.Forms.ErrorProvider.DataMember%2A>実行時にプロパティを使用してください、<xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A>競合を回避する方法です。</span><span class="sxs-lookup"><span data-stu-id="54652-106">If you change the error provider's <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> and <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> properties at run time, you should use the <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> method to avoid conflicts.</span></span>  
  
### <a name="to-display-data-errors"></a><span data-ttu-id="54652-107">データ エラーを表示するには</span><span class="sxs-lookup"><span data-stu-id="54652-107">To display data errors</span></span>  
  
1.  <span data-ttu-id="54652-108">コンポーネントをデータ テーブル内の特定の列にバインドします。</span><span class="sxs-lookup"><span data-stu-id="54652-108">Bind the component to a specific column within a data table.</span></span>  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2.  <span data-ttu-id="54652-109">設定、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティ フォームをします。</span><span class="sxs-lookup"><span data-stu-id="54652-109">Set the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property to the form.</span></span>  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  <span data-ttu-id="54652-110">列のエラーを含む行を現在のレコードの位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="54652-110">Set the position of the current record to a row that contains a column error.</span></span>  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="54652-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="54652-111">See Also</span></span>  
 [<span data-ttu-id="54652-112">ErrorProvider コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="54652-112">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="54652-113">方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="54652-113">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
