---
title: "行の検索 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 行の検索
<xref:System.Data.DataView> の <xref:System.Data.DataView.Find%2A> メソッドと <xref:System.Data.DataView.FindRows%2A> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。  **Find** メソッドと **FindRows** メソッドによる検索で、値の大文字と小文字が区別されるかどうかは、基になる <xref:System.Data.DataTable> の **CaseSensitive** プロパティによって決まります。  検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。  
  
 **Find** メソッドは、検索条件に一致する <xref:System.Data.DataRowView> のインデックスの整数値を返します。  複数の行が検索条件に一致する場合は、一致した最初の **DataRowView** が返されます。  一致する DataRowView がない場合には、**Find** は \-1 を返します。  
  
 複数の行に一致する検索結果を返すには、**FindRows** メソッドを使用します。  **FindRows** は **Find** メソッドと同様に機能しますが、**DataView** 内で条件に一致するすべての行を参照する **DataRowView** 配列を返す点が **Find** メソッドとは異なります。  一致する行が見つからない場合、**DataRowView** 配列は空になります。  
  
 **Find** メソッドまたは **FindRows** メソッドを使用するには、並べ替え順序を指定する必要があります。並べ替え順序を指定するには、**ApplyDefaultSort** を **true** に設定するか、または **Sort** プロパティを使用します。  並べ替え順序が指定されないと、例外がスローされます。  
  
 **Find** メソッドと **FindRows** メソッドには、並べ替え順序に指定されている列の数と長さが一致する値配列を入力として渡します。  1 つの列に基づく並べ替えの場合は、1 つの値を渡します。  複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。  複数列に基づく並べ替えでは、オブジェクト配列の値の順序が、**DataView** の **Sort** プロパティに指定されている列の順序と一致する必要があります。  
  
 1 列の並べ替え順序が設定されている **DataView** に対して **Find** メソッドを呼び出すコード サンプルを次に示します。  
  
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
  
 **Sort** プロパティで複数の列が指定される場合は、次のコード サンプルに示すように、各列に対応する検索値を **Sort** プロパティで指定されている順序で格納したオブジェクト配列を渡す必要があります。  
  
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
  
## 参照  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)