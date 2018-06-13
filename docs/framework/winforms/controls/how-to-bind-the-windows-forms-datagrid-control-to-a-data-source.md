---
title: '方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 62f61eb2d294baf007b0b3f749f3cf6b7f4857c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530303"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="b0d22-102">方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="b0d22-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
>  <span data-ttu-id="b0d22-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="b0d22-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b0d22-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0d22-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b0d22-105">Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは具体的には、データ ソースから情報を表示するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b0d22-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="b0d22-106">実行時に呼び出すことによって、コントロールをバインドする、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b0d22-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="b0d22-107">さまざまなデータ ソースからデータを表示できますが、最も一般的なソース、データセットとデータのビューです。</span><span class="sxs-lookup"><span data-stu-id="b0d22-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="b0d22-108">DataGrid コントロールをプログラムでデータ バインドする</span><span class="sxs-lookup"><span data-stu-id="b0d22-108">To data-bind the DataGrid control programmatically</span></span>  
  
1.  <span data-ttu-id="b0d22-109">データセットを読み込むコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="b0d22-110">データ ソースが、データセットまたはデータセットのテーブルに基づいたデータ ビューの場合は、データセットへのデータ、フォームにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="b0d22-111">実際に使用するコードは、データセットがデータを取得する場所によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b0d22-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="b0d22-112">データセットは、データベースから直接登録されているが、通常を呼び出した場合、`Fill`という名前のデータセットに読み込まれる次の例のように、データ アダプターの`DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="b0d22-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="b0d22-113">場合は、データセットは、XML Web サービスから指定されている、通常、コードでサービスのインスタンスを作成し、データセットを返すメソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="b0d22-114">XML Web サービスからのデータセットをマージするには、ローカルのデータセットにします。</span><span class="sxs-lookup"><span data-stu-id="b0d22-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="b0d22-115">次の例と呼ばれる XML Web サービスのインスタンスを作成する方法を示しています`CategoriesService`を呼び出してその`GetCategories`メソッド、およびローカルのデータセットに結果のデータセットと呼ばれるマージ`DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="b0d22-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2.  <span data-ttu-id="b0d22-116">呼び出す、<xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド、データ ソースとデータ メンバーを渡します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="b0d22-117">データ メンバーを明示的に渡す必要がない場合は、空の文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d22-118">最初に、グリッドをバインドする場合は、コントロールを設定することができます<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="b0d22-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="b0d22-119">ただし、これらを設定したら、これらのプロパティをリセットできません。</span><span class="sxs-lookup"><span data-stu-id="b0d22-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="b0d22-120">そのため、お勧め必ず使用すること、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b0d22-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="b0d22-121">次の例は、プログラムによってという名前のデータセット内の Customers テーブルにバインドする方法を示しています`DsCustomers1`:。</span><span class="sxs-lookup"><span data-stu-id="b0d22-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="b0d22-122">Customers テーブルがデータセット内の唯一のテーブルの場合は、でしたまたはグリッドを連結するこの方法。</span><span class="sxs-lookup"><span data-stu-id="b0d22-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  <span data-ttu-id="b0d22-123">(省略可能)グリッドに適切なテーブルのスタイルおよび列のスタイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="b0d22-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="b0d22-124">テーブルのスタイルがない場合、テーブルが表示されますが、最低限の書式とすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b0d22-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d22-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0d22-125">See Also</span></span>  
 [<span data-ttu-id="b0d22-126">DataGrid コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="b0d22-126">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="b0d22-127">方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="b0d22-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="b0d22-128">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="b0d22-128">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="b0d22-129">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="b0d22-129">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
