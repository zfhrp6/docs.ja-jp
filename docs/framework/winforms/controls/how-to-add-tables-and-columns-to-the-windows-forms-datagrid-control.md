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
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="e21e2-102">方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する</span><span class="sxs-lookup"><span data-stu-id="e21e2-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="e21e2-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="e21e2-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e21e2-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e21e2-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e21e2-105">Windows フォームでデータを表示することができます<xref:System.Windows.Forms.DataGrid>テーブルおよび列を作成してコントロール**DataGridTableStyle**オブジェクトとに追加すること、 **GridTableStylesCollection**オブジェクトは使用してアクセス、<xref:System.Windows.Forms.DataGrid>コントロールの**TableStyles**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e21e2-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="e21e2-106">各テーブルのスタイルで指定されたは、どのようなデータ テーブルの内容を表示する、 **DataGridTableStyle**オブジェクトの**MappingName**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="e21e2-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="e21e2-107">テーブル スタイルが指定されていない列のスタイルでは既定では、そのデータ テーブル内のすべての列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e21e2-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="e21e2-108">追加することによって表示される、テーブルから列を制限する**DataGridColumnStyle**オブジェクトを**GridColumnStylesCollection**からアクセスできるオブジェクト、 **GridColumnStyles**の各プロパティ**DataGridTableStyle**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e21e2-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="e21e2-109">データ グリッドに、テーブルと列をプログラムで追加するには</span><span class="sxs-lookup"><span data-stu-id="e21e2-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="e21e2-110">テーブルにデータを表示するためにする必要がありますまずバインド、<xref:System.Windows.Forms.DataGrid>データセットを制御します。</span><span class="sxs-lookup"><span data-stu-id="e21e2-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="e21e2-111">詳細については、次を参照してください。[する方法: Windows フォーム DataGrid コントロールをデータ ソースにバインド](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)です。</span><span class="sxs-lookup"><span data-stu-id="e21e2-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="e21e2-112">列のスタイルをプログラムで指定する場合は常に作成する**DataGridColumnStyle**オブジェクトに追加して、 **GridColumnStylesCollection**追加する前にオブジェクト**DataGridTableStyle**オブジェクトを**GridTableStylesCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e21e2-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="e21e2-113">空の追加と**DataGridTableStyle** 、コレクションにオブジェクトを**DataGridColumnStyle**オブジェクトが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e21e2-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="e21e2-114">新規追加しようとする場合に、例外がスローされますその結果、 **DataGridColumnStyle**オブジェクトが複製によって**MappingName**値を**GridColumnStylesCollection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e21e2-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="e21e2-115">新しいテーブルのスタイルを宣言し、そのマップ名を設定します。</span><span class="sxs-lookup"><span data-stu-id="e21e2-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="e21e2-116">新しい列のスタイルを宣言し、そのマップ名やその他のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e21e2-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="e21e2-117">呼び出す、**追加**のメソッド、 **GridColumnStylesCollection**テーブルのスタイルに列を追加するオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e21e2-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="e21e2-118">呼び出す、**追加**のメソッド、 **GridTableStylesCollection**データ グリッドにテーブルのスタイルを追加するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e21e2-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e21e2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="e21e2-119">See Also</span></span>  
 [<span data-ttu-id="e21e2-120">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="e21e2-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="e21e2-121">方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする</span><span class="sxs-lookup"><span data-stu-id="e21e2-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
