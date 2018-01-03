---
title: "Load メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e6c6ce0b722d901e38b728a710e3c49848fb918a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="the-load-method"></a>Load メソッド
<xref:System.Data.DataTable.Load%2A> メソッドを使用して、データ ソースの行を <xref:System.Data.DataTable> に読み込むことができます。 これは最も単純な形式で、単一のパラメーターを受け取っているオーバー ロードされたメソッド、 **DataReader**です。 このフォームで、単に読み込む、 **DataTable**行を含むです。 必要に応じて、指定することができます、 **LoadOption**にデータを追加する方法を制御するパラメーター、 **DataTable**です。  
  
 **LoadOption**パラメーターがの場合に特に便利ですが、 **DataTable**既に行のデータを含む、データと組み合わせられるため、データ ソースからどのように受信データがについて説明しますテーブルの既存の。 たとえば、 **PreserveCurrentValues** (既定値) を指定する行としてマークされている場合**Added**で、 **DataTable**、**元**値列または各列に設定されている一致する行の内容、データ ソースからです。 **現在**値は、行が追加されたときに割り当てられた値を保持し、 **RowState**の行に設定されます**Changed**です。  
  
 <xref:System.Data.LoadOption> 列挙値の簡単な説明を次の表に示します。  
  
|LoadOption の値|説明|  
|----------------------|-----------------|  
|**OverwriteRow**|受信した行が同じである場合**PrimaryKey**既に行と値、 **DataTable**、**元**と**現在**それぞれの値列は、受信した行の値に置き換えられます、 **RowState**プロパティに設定されている**Unchanged**です。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**を使用して追加、 **RowState**値**Unchanged**です。<br /><br /> このオプションが有効の内容を更新、 **DataTable**データ ソースの内容と一致するようにします。|  
|**PreserveCurrentValues (既定値)**|受信した行が同じである場合**PrimaryKey**既に行と値、 **DataTable**、**元**受信する行、および、の内容に値が設定されている**現在**値は変更されません。<br /><br /> 場合、 **RowState**は**Added**または**Modified**に設定されている**Modified**です。<br /><br /> 場合、 **RowState**が**Deleted**、そのまま**Deleted**です。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**追加されると、および**RowState**に設定されている**Unchanged**です。|  
|**UpdateCurrentValues**|受信した行が同じである場合**PrimaryKey**に既に存在する行と値、 **DataTable**、**現在**値をコピー、**元**値、および**現在**値は、受信した行の内容に設定されます。<br /><br /> 場合、 **RowState**で、 **DataTable**が**Added**、 **RowState**まま**Added**です。 としてマークされた行**Modified**または**Deleted**、 **RowState**は**Modified**です。<br /><br /> 行に既に存在しないデータ ソースから、 **DataTable**追加されると、および**RowState**に設定されている**Added**です。|  
  
 次のサンプルは、**ロード**に従業員の誕生日の一覧を表示するメソッド、 **Northwind**データベース。  
  
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
  
## <a name="see-also"></a>参照  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
