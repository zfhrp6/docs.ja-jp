---
title: "DataSet の内容のコピー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d8f9eac80d7a6679e7b3717446e79caf54a5fed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="copying-dataset-contents"></a>DataSet の内容のコピー
コピーを作成することができます、 <xref:System.Data.DataSet> 、元のデータに影響を与えずにデータを操作したり、作業できるようにからのデータのサブセットを**データセット**です。 コピーするときに、**データセット**、することができます。  
  
-   正確なコピーを作成、**データセット**(スキーマ、データ、行状態情報、および行のバージョンなど)。  
  
-   作成、**データセット**、既存のスキーマを格納している**データセット**、変更された行だけです。 変更されているすべての行を返すか、特定の指定**DataRowState**です。 行の状態の詳細については、次を参照してください。[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
-   スキーマ、またはリレーショナル構造のコピー、**データセット**任意の行をコピーすることがなくのみです。 行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。  
  
 正確なコピーを作成する、**データセット**スキーマとデータの両方が含まれている、使用して、<xref:System.Data.DataSet.Copy%2A>のメソッド、**データセット**です。 次のコード例の正確なコピーを作成する方法を示しています、**データセット**です。  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 コピーを作成する、**データセット**スキーマとのみ、データを表すが含まれる**Added**、 **Modified**、または**Deleted**行を使用して、<xref:System.Data.DataSet.GetChanges%2A>のメソッド、**データセット**です。 使用することも**GetChanges**を渡すことによって指定された行の状態を持つ行だけを返す、 **DataRowState**値の呼び出し時に**GetChanges**です。 次のコード例に渡す方法を示しています、 **DataRowState**を呼び出すときに**GetChanges**です。  
  
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
  
 コピーを作成する、**データセット**スキーマのみを含む、使用して、<xref:System.Data.DataSet.Clone%2A>のメソッド、**データセット**です。 複製されたに既存の行を追加することもできます。**データセット**を使用して、 **ImportRow**のメソッド、 **DataTable**です。 **ImportRow**データ、行の状態、および行のバージョン情報を指定したテーブルに追加します。 列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。  
  
 次のコード例は、の複製を作成、**データセット**し、元の行を追加し、**データセット**を**顧客**テーブルに、**データセット**顧客の複製で、 **CountryRegion**列に値"Germany"です。  
  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
