---
title: "行の検索"
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9ede2dbf0718a4ca1d8025af3ce60c256afc867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="finding-rows"></a>行の検索
<xref:System.Data.DataView.Find%2A> の <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。 値が検索の大文字小文字の区別、**検索**と**FindRows**メソッドはによって決定されます、 **CaseSensitive** 、基になるプロパティ<xref:System.Data.DataTable>です。 検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。  
  
 **検索**メソッドのインデックスを持つ整数を返します、<xref:System.Data.DataRowView>検索条件に一致します。 複数の行には、検索条件、一致した最初のインデックスのみが一致する場合**DataRowView**が返されます。 一致が見つからない場合**検索**-1 を返します。  
  
 複数の行に一致する検索結果を返すを使用して、 **FindRows**メソッドです。 **FindRows**同様の機能、**検索**メソッドを返します点を除いて、 **DataRowView**配列内のすべての一致する行を参照する、 **DataView**です。 一致が見つからない場合、 **DataRowView**配列は空になります。  
  
 使用する、**検索**または**FindRows**並べ替え順を指定する必要がありますメソッドで設定するか注文**ApplyDefaultSort**に**true**またはを使用して、**並べ替え**プロパティです。 並べ替え順序が指定されないと、例外がスローされます。  
  
 **検索**と**FindRows**メソッドがの長さが並べ替え順序で列の数と一致する入力として値の配列を取得します。 1 つの列に基づく並べ替えの場合は、1 つの値を渡します。 複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。 複数の列で並べ替えには、オブジェクトの配列内の値と一致するがで指定された列の順序に注意してください、**並べ替え**のプロパティ、 **DataView**です。  
  
 次のコード例は、**検索**メソッドに対して呼び出されると、 **DataView** 1 つの列の並べ替え順序を持つ。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 場合、**並べ替え**プロパティが複数の列を指定します、によって指定された順序で各列に対して検索値を持つオブジェクトの配列を渡す必要があります、**並べ替え**プロパティは、次のコード例に示すようにします。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
