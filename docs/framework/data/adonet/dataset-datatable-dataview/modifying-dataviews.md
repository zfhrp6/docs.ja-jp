---
title: "DataView の変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataView の変更
<xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。  基になるテーブルのデータを **DataView** で変更できるかどうかは、**DataView** の 3 つのブール値プロパティで制御されます。  この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。  これらのプロパティの既定値は **true** です。  
  
 **AllowNew** が **true** の場合は、**DataView** の <xref:System.Data.DataView.AddNew%2A> メソッドを使用して <xref:System.Data.DataRowView> を新規に作成できます。  **DataRowView** の <xref:System.Data.DataRowView.EndEdit%2A> メソッドが呼び出されるまでは、新規に作成された行は基になる <xref:System.Data.DataTable> に追加されません。  **DataRowView** の <xref:System.Data.DataRowView.CancelEdit%2A> メソッドが呼び出されると、新規に作成された行は破棄されます。  一度に編集できるのは、1 つの **DataRowView** だけです。  保留中の行がある場合は、**DataRowView** の **AddNew** メソッドまたは **BeginEdit** メソッドを呼び出すと、保留中の行に対して **EndEdit** が暗黙的に呼び出されます。  **EndEdit** が呼び出されると、基になる **DataTable** に対して変更が適用されます。適用された変更をコミットするには **DataTable**、**DataSet**、または **DataRow** の各オブジェクトの **AcceptChanges** メソッドを使用し、拒否するにはこれらのオブジェクトの **RejectChanges** メソッドを使用します。  **AllowNew** が **false** の場合は、**DataRowView** の **AddNew** メソッドを呼び出すと例外がスローされます。  
  
 **AllowEdit** が **true** の場合は、**DataRowView** を使用すると **DataRow** の内容を変更できます。  基になる行の変更内容を確定するには **DataRowView.EndEdit** を使用し、変更内容を取り消すには **DataRowView.CancelEdit** を使用します。  一度に編集できるのは 1 行だけです。  保留中の行がある場合は、**DataRowView** の **AddNew** メソッドまたは **BeginEdit** メソッドを呼び出すと、保留中の行に対して **EndEdit** が暗黙的に呼び出されます。  **EndEdit** が呼び出されると、基になる **DataRow** の **Current** 行バージョンに対して変更が適用されます。適用された変更をコミットするには **DataTable**、**DataSet**、または **DataRow** の各オブジェクトの **AcceptChanges** メソッドを使用し、拒否するにはこれらのオブジェクトの **RejectChanges** メソッドを使用します。  **AllowEdit** が **false** の場合は、**DataView** の値を変更しようとすると例外がスローされます。  
  
 既存の **DataRowView** の編集中でも、まだ確定されていない変更に関して、基になる **DataTable** のイベントが発生する場合があります。  **DataRowView** に対して **EndEdit** と **CancelEdit** のどちらが呼び出されているかに関係なく、基になる **DataRow** に対して **EndEdit** を呼び出すと、確定されていない変更が適用され、**CancelEdit** を呼び出すと、確定されていない変更が取り消されます。  
  
 **AllowDelete** が **true** の場合は、**DataView** オブジェクトまたは **DataRowView** オブジェクトの **Delete** メソッドを使用して **DataView** の行を削除できます。DataView の行を削除すると、基になる **DataTable** から行が削除されます。  後でこの削除操作をコミットするには **AcceptChanges** を使用し、拒否するには **RejectChanges** を使用します。  **AllowDelete** が **false** の場合は、**DataView** または **DataRowView** の **Delete** メソッドを呼び出すと例外がスローされます。  
  
 次のコード サンプルは、**DataView** を使用して行を削除する機能を無効にし、**DataView** を使用して基になるテーブルに新しい行を追加します。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## 参照  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 <xref:System.Data.DataRowView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)