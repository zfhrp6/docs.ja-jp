---
title: "DataRelation の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataRelation の追加
複数の <xref:System.Data.DataTable> オブジェクトを含む <xref:System.Data.DataSet> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。  
  
 **DataRelation** の作成に必要な引数は、作成する **DataRelation** の名前、およびそのリレーションシップで親子の列となる列への 1 つ以上の <xref:System.Data.DataColumn> 参照の配列です。  **DataRelation** の作成後、DataRelation を使用してテーブル間の移動および値の取得を行うことができます。  
  
 <xref:System.Data.DataSet> への **DataRelation** の追加は、既定では <xref:System.Data.UniqueConstraint> が親テーブルに、<xref:System.Data.ForeignKeyConstraint> が子テーブルに追加されます。  上記の既定の制約の詳細については、「[DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)」を参照してください。  
  
 <xref:System.Data.DataSet> にある 2 つの <xref:System.Data.DataTable> オブジェクトを使用して、**DataRelation** を作成するコード サンプルを次に示します。  各 <xref:System.Data.DataTable> には、2 つの <xref:System.Data.DataTable> オブジェクト間のリンクとなる **CustID** という名前の列があります。  例では、単一の **DataRelation** が <xref:System.Data.DataSet> の **Relations** コレクションに追加されます。  例にある最初の引数には、作成する **DataRelation** の名前を指定します。  2 番目の引数によって親の **DataColumn** が、3 番目の引数によって子の **DataColumn** が設定されます。  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 **DataRelation** には、**入れ子になった**プロパティもあります。**true** に設定すると、<xref:System.Data.DataSet.WriteXml%2A> を使用して XML 要素として書き込むときに、親テーブルの関連付けられた行の中で子テーブルの行が入れ子になります。  詳細については、「[DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。  
  
## 参照  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)