---
title: DataViews の管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: c292c9f7827e86d48f2006c05f6012ad95da1485
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="managing-dataviews"></a><span data-ttu-id="45c7c-102">DataViews の管理</span><span class="sxs-lookup"><span data-stu-id="45c7c-102">Managing DataViews</span></span>
<span data-ttu-id="45c7c-103"><xref:System.Data.DataViewManager> のすべてのテーブルのビュー設定を管理するには、<xref:System.Data.DataView> を使用します。</span><span class="sxs-lookup"><span data-stu-id="45c7c-103">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="45c7c-104">グリッドなど、リレーションシップをナビゲートする複数のテーブルにバインドするコントロールがある場合、 **DataViewManager**最適です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-104">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="45c7c-105">**DataViewManager**のコレクションを格納<xref:System.Data.DataViewSetting>内のテーブルのビュー設定に使用されるオブジェクト、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-105">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="45c7c-106"><xref:System.Data.DataViewSettingCollection> 1 つ含む<xref:System.Data.DataViewSetting>内の各テーブルのオブジェクト、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-106">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="45c7c-107">既定値を設定することができます**ApplyDefaultSort**、**並べ替え**、 **RowFilter**、および**RowStateFilter**によって参照されているテーブルのプロパティ使用してその**DataViewSetting**です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-107">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="45c7c-108">参照することができます、 **DataViewSetting**名前または序数参照は、その特定のテーブル オブジェクトへの参照を渡すことによって、特定のテーブルにします。</span><span class="sxs-lookup"><span data-stu-id="45c7c-108">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="45c7c-109">コレクションにアクセスすることができます**DataViewSetting**内のオブジェクト、 **DataViewManager**を使用して、 **DataViewSettings**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45c7c-109">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="45c7c-110">次のコード例がいっぱいになった、**データセット**SQL Server と**Northwind**データベース テーブル**顧客**、 **Orders**、および**Order Details**、テーブル間のリレーションシップを作成、使用して、 **DataViewManager**を既定値を設定する**DataView**設定、およびバインド、 **DataGrid**を**DataViewManager**です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-110">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="45c7c-111">例では、既定値を設定する**DataView**のすべてのテーブルの設定、**データセット**テーブルの主キーを並べ替える (**ApplyDefaultSort**  =  **true**)、後の並べ替え順序を変更し、**顧客**で並べ替えを行うテーブル**CompanyName**です。</span><span class="sxs-lookup"><span data-stu-id="45c7c-111">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="45c7c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="45c7c-112">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataViewManager>  
 <xref:System.Data.DataViewSetting>  
 <xref:System.Data.DataViewSettingCollection>  
 [<span data-ttu-id="45c7c-113">DataViews</span><span class="sxs-lookup"><span data-stu-id="45c7c-113">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="45c7c-114">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="45c7c-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
