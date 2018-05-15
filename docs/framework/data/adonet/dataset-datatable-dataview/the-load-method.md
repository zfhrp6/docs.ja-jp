---
title: Load メソッド
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 04defffc724875e691fd7b87331c28e6b6c0cd28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="the-load-method"></a><span data-ttu-id="fecd6-102">Load メソッド</span><span class="sxs-lookup"><span data-stu-id="fecd6-102">The Load Method</span></span>
<span data-ttu-id="fecd6-103"><xref:System.Data.DataTable.Load%2A> メソッドを使用して、データ ソースの行を <xref:System.Data.DataTable> に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fecd6-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="fecd6-104">これは最も単純な形式で、単一のパラメーターを受け取っているオーバー ロードされたメソッド、 **DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="fecd6-105">このフォームで、単に読み込む、 **DataTable**行を含むです。</span><span class="sxs-lookup"><span data-stu-id="fecd6-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="fecd6-106">必要に応じて、指定することができます、 **LoadOption**にデータを追加する方法を制御するパラメーター、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="fecd6-107">**LoadOption**パラメーターがの場合に特に便利ですが、 **DataTable**既に行のデータを含む、データと組み合わせられるため、データ ソースからどのように受信データがについて説明しますテーブルの既存の。</span><span class="sxs-lookup"><span data-stu-id="fecd6-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="fecd6-108">たとえば、 **PreserveCurrentValues** (既定値) を指定する行としてマークされている場合**Added**で、 **DataTable**、**元**値列または各列に設定されている一致する行の内容、データ ソースからです。</span><span class="sxs-lookup"><span data-stu-id="fecd6-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="fecd6-109">**現在**値は、行が追加されたときに割り当てられた値を保持し、 **RowState**の行に設定されます**Changed**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="fecd6-110"><xref:System.Data.LoadOption> 列挙値の簡単な説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fecd6-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="fecd6-111">LoadOption の値</span><span class="sxs-lookup"><span data-stu-id="fecd6-111">LoadOption value</span></span>|<span data-ttu-id="fecd6-112">説明</span><span class="sxs-lookup"><span data-stu-id="fecd6-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="fecd6-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="fecd6-113">**OverwriteRow**</span></span>|<span data-ttu-id="fecd6-114">受信した行が同じである場合**PrimaryKey**既に行と値、 **DataTable**、**元**と**現在**それぞれの値列は、受信した行の値に置き換えられます、 **RowState**プロパティに設定されている**Unchanged**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="fecd6-115">行に既に存在しないデータ ソースから、 **DataTable**を使用して追加、 **RowState**値**Unchanged**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="fecd6-116">このオプションが有効の内容を更新、 **DataTable**データ ソースの内容と一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="fecd6-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="fecd6-117">**PreserveCurrentValues (既定値)**</span><span class="sxs-lookup"><span data-stu-id="fecd6-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="fecd6-118">受信した行が同じである場合**PrimaryKey**既に行と値、 **DataTable**、**元**受信する行、および、の内容に値が設定されている**現在**値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="fecd6-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="fecd6-119">場合、 **RowState**は**Added**または**Modified**に設定されている**Modified**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="fecd6-120">場合、 **RowState**が**Deleted**、そのまま**Deleted**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="fecd6-121">行に既に存在しないデータ ソースから、 **DataTable**追加されると、および**RowState**に設定されている**Unchanged**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="fecd6-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="fecd6-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="fecd6-123">受信した行が同じである場合**PrimaryKey**に既に存在する行と値、 **DataTable**、**現在**値をコピー、**元**値、および**現在**値は、受信した行の内容に設定されます。</span><span class="sxs-lookup"><span data-stu-id="fecd6-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="fecd6-124">場合、 **RowState**で、 **DataTable**が**Added**、 **RowState**まま**Added**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="fecd6-125">としてマークされた行**Modified**または**Deleted**、 **RowState**は**Modified**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="fecd6-126">行に既に存在しないデータ ソースから、 **DataTable**追加されると、および**RowState**に設定されている**Added**です。</span><span class="sxs-lookup"><span data-stu-id="fecd6-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="fecd6-127">次のサンプルは、**ロード**に従業員の誕生日の一覧を表示するメソッド、 **Northwind**データベース。</span><span class="sxs-lookup"><span data-stu-id="fecd6-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="fecd6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="fecd6-128">See Also</span></span>  
 [<span data-ttu-id="fecd6-129">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="fecd6-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="fecd6-130">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="fecd6-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
