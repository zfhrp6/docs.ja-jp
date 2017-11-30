---
title: "方法: Windows フォーム DataGrid コントロールにマスター/詳細形式の一覧を作成"
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
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63cb647e2ed6dcbc97fab15db3166b55c52f635a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="0f75b-102">方法 : Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する</span><span class="sxs-lookup"><span data-stu-id="0f75b-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="0f75b-103"><xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="0f75b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="0f75b-104">詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f75b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="0f75b-105">場合、<xref:System.Data.DataSet>は一連の関連テーブルの 2 つ使用できます<xref:System.Windows.Forms.DataGrid>マスター/詳細形式でデータを表示するコントロール。</span><span class="sxs-lookup"><span data-stu-id="0f75b-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="0f75b-106">1 つ<xref:System.Windows.Forms.DataGrid>マスター グリッドに指定し、詳細グリッドに、もう一方を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f75b-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="0f75b-107">マスターの一覧にエントリを選択すると、詳細の一覧ですべての関連する子エントリのとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f75b-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="0f75b-108">たとえば場合、 <xref:System.Data.DataSet> Customers テーブルと関連の Orders テーブルを含むマスター グリッドに Customers テーブルと Orders テーブルに、詳細グリッドを指定するとします。</span><span class="sxs-lookup"><span data-stu-id="0f75b-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="0f75b-109">マスター グリッドから、顧客がオンの場合、すべての注文を Orders テーブル内でその顧客に関連付けられているの詳細グリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f75b-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="0f75b-110">マスター/詳細関係をコードから設定するには</span><span class="sxs-lookup"><span data-stu-id="0f75b-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="0f75b-111">新しい 2 つ作成<xref:System.Windows.Forms.DataGrid>を制御し、それらのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="0f75b-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="0f75b-112">データセットにテーブルを追加します。</span><span class="sxs-lookup"><span data-stu-id="0f75b-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="0f75b-113">型の変数を宣言<xref:System.Data.DataRelation>を作成するリレーションシップを表します。</span><span class="sxs-lookup"><span data-stu-id="0f75b-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="0f75b-114">リレーションシップの名前を指定して、テーブル、列、および 2 つのテーブルを関連付ける項目を指定することによって、リレーションシップのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0f75b-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="0f75b-115">リレーションシップを追加、<xref:System.Data.DataSet>オブジェクトの<xref:System.Data.DataSet.Relations%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="0f75b-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="0f75b-116">使用して、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>のメソッド、<xref:System.Windows.Forms.DataGrid>のグリッドの各バインドに、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="0f75b-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="0f75b-117">次の例は、Customers と Orders テーブル間で以前に生成されたマスター/詳細関係を設定する方法を示します<xref:System.Data.DataSet>(`ds`)。</span><span class="sxs-lookup"><span data-stu-id="0f75b-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f75b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f75b-118">See Also</span></span>  
 [<span data-ttu-id="0f75b-119">DataGrid コントロール</span><span class="sxs-lookup"><span data-stu-id="0f75b-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="0f75b-120">DataGrid コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="0f75b-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="0f75b-121">方法: データ ソースに Windows フォーム DataGrid コントロールをバインドする</span><span class="sxs-lookup"><span data-stu-id="0f75b-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
