---
title: "DataSet の内容のコピー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# DataSet の内容のコピー
<xref:System.Data.DataSet> のコピーを作成すると、元のデータに影響せずにデータを使用したり、**DataSet** のデータのサブセットを使用したりできます。  **DataSet** をコピーすると、次の操作を行うことができます。  
  
-   スキーマ、データ、行状態情報、行バージョンなどの **DataSet** の正確なコピーを作成できます。  
  
-   既存の **DataSet** のスキーマを含み、行だけを変更した **DataSet** を作成できます。  変更されたすべての行を返したり、特定の **DataRowState** を指定したりできます。  行の状態の詳細については、「[行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)」を参照してください。  
  
-   行をコピーせずに、**DataSet** のスキーマ \(リレーショナル構造\) だけをコピーできます。  行は、<xref:System.Data.DataTable.ImportRow%2A> を使用して、既存の <xref:System.Data.DataTable> にインポートできます。  
  
 スキーマとデータを含む **DataSet** の正確なコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.Copy%2A> メソッドを使用します。  **DataSet** の正確なコピーを作成する方法を次のコード サンプルに示します。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 スキーマ、およびデータが **Added**、**Modified**、または **Deleted** である行だけを含む **DataSet** のコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.GetChanges%2A> メソッドを使用します。  また、**GetChanges** の呼び出し時に **DataRowState** の値を渡すことによって、**GetChanges** を使用して特定の行状態の行だけを返すことができます。  **GetChanges** の呼び出し時に **DataRowState** を渡す方法を次のコード サンプルに示します。  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 スキーマだけを含む **DataSet** のコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.Clone%2A> メソッドを使用します。  また、**DataTable** の **ImportRow** メソッドを使用して、複製した **DataSet** に既存の行を追加することもできます。  **ImportRow** メソッドを使用すると、データ、行の状態、および行バージョンの情報が指定したテーブルに追加されます。  列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。  
  
 **DataSet** のクローンを作成し、**CountryRegion** 列の値が "Germany" の顧客に対する **DataSet** のクローン内の **Customers** テーブルに、元の **DataSet** の行を追加するコード サンプルを次に示します。  
  
```vb  
  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## 参照  
 <xref:System.Data.DataSet>   
 <xref:System.Data.DataTable>   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)