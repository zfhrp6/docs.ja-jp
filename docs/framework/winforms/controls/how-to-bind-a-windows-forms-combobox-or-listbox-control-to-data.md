---
title: '方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする '
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
ms.openlocfilehash: 270ed1c9fab4013df72b715ce8b074d287616713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="41993-102">方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする </span><span class="sxs-lookup"><span data-stu-id="41993-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="41993-103">バインドすることができます、<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>または既存のデータを編集する、データベース内のデータの参照などのタスクを実行するデータを新しいデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="41993-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="41993-104">ComboBox または ListBox コントロールをバインドするには</span><span class="sxs-lookup"><span data-stu-id="41993-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="41993-105">設定、`DataSource`プロパティをデータ ソース オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="41993-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="41993-106">データ ソースには、<xref:System.Windows.Forms.BindingSource>データ、データ テーブル、データ ビュー、データセットにバインドされると、データ マネージャー、配列、または表示を実装するクラス、<xref:System.Collections.IList>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41993-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="41993-107">詳細については、次を参照してください。 [Windows フォームでサポートされるデータ ソース](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="41993-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="41993-108">テーブルにバインドする場合は、設定、`DisplayMember`プロパティをデータ ソース内の列の名前にします。</span><span class="sxs-lookup"><span data-stu-id="41993-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="41993-109">\- または -</span><span class="sxs-lookup"><span data-stu-id="41993-109">\- or -</span></span>  
  
     <span data-ttu-id="41993-110">バインドする場合、<xref:System.Collections.IList>表示のメンバー リスト内の型のパブリック プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="41993-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="41993-111">かどうかは、実装されていないデータ ソースにバインドされている、<xref:System.ComponentModel.IBindingList>インターフェイスなど、 <xref:System.Collections.ArrayList>、データ ソースが更新されたときに、バインドされたコントロールのデータは更新されません。</span><span class="sxs-lookup"><span data-stu-id="41993-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="41993-112">たとえばがある場合、コンボ ボックスにバインド、<xref:System.Collections.ArrayList>にデータが追加されると、 <xref:System.Collections.ArrayList>、コンボ ボックスでこれらの新しい項目は表示されません。</span><span class="sxs-lookup"><span data-stu-id="41993-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="41993-113">ただし、呼び出すことで更新するコンボ ボックスを強制することができます、<xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A>と<xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A>メソッドのインスタンスで、<xref:System.Windows.Forms.BindingContext>コントロールがバインドされるクラスです。</span><span class="sxs-lookup"><span data-stu-id="41993-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41993-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="41993-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="41993-115">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="41993-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="41993-116">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="41993-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="41993-117">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="41993-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
