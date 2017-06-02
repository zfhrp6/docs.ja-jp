---
title: "DataRelation の移動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataRelation の移動
<xref:System.Data.DataRelation> の主な機能の 1 つは、<xref:System.Data.DataSet> の 1 つの <xref:System.Data.DataTable> から別の <xref:System.Data.DataTable> を移動できることです。  この参照により、関連付けられた **DataTable** から単一の **DataRow** を指定すると、1 つの **DataTable** 内の関連する <xref:System.Data.DataRow> オブジェクトをすべて取得できます。  たとえば、顧客のテーブルとオーダーのテーブル間に **DataRelation** を確立すると、**GetChildRows** を使用して特定の顧客行のオーダー行をすべて取得できます。  
  
 **DataSet** の **Customers** テーブルと **Orders** テーブル間の **DataRelation** を作成し、各顧客のすべてのオーダーを返すコード サンプルを次に示します。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 上記の例に基づいて、4 つのテーブルを相互に関連付け、そのテーブルのリレーションシップ間を移動する例を次に示します。  上記の例に示すように、**CustomerID** は **Customers** テーブルを **Orders** テーブルに関連付けます。  **Customers** テーブルにある各顧客に対しては、**Orders** テーブルにあるすべての子の行が確定され、該当する顧客のオーダー数とその **OrderID** の値が返されます。  
  
 展開された例では、**OrderDetails** テーブルおよび **Products** テーブルからも値が返されます。  各顧客のオーダーに対しては、オーダーされた製品および数量を示すために、**OrderID** を使用して **Orders** テーブルが **OrderDetails** テーブルに関連付けられます。  **OrderDetails** テーブルに含まれているのは、オーダーされた製品の **ProductID** だけであるため、**ProductID** を使用して、**OrderDetails** を **Products** に関連付けて **ProductName** を返します。  このリレーションでは、**Products** テーブルが親となり、**Order Details** テーブルが子となります。  その結果、**OrderDetails** テーブルを順次処理すると、**GetParentRow** が呼び出され、関連付けられた **ProductName** の値を取得します。  
  
 **DataRelation** が **Customers** テーブルと **Orders** テーブルに対して作成された場合には、**createConstraints** フラグには値が指定されません \(既定値は **true**\)。  これは、**Orders** テーブルにあるすべての行に対して親の **Customers** テーブルにある **CustomerID** の値が設定されているためです。  **Orders** テーブルに、**Customers** テーブルに存在しない **CustomerID** が存在する場合、<xref:System.Data.ForeignKeyConstraint> は例外をスローします。  
  
 親の列に含まれていない値が子の列に含まれる場合、**DataRelation** の追加時に **createConstraints** フラグが **false** に設定されます。  例では、**Orders** テーブルと **OrderDetails** テーブル間の **DataRelation** に対して、**createConstraints** フラグが **false** に設定されています。  このため、このアプリケーションでは **OrderDetails** テーブルからすべてのレコードを返し、実行時に例外を生成せずに **Orders** テーブルからレコードのサブセットだけを返すことができます。  展開された例では、次の形式で出力が生成されます。  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 **Orders** テーブルのレコードのサブセットだけと共に、**OrderDetails** テーブルと **Products** テーブルからの値が返された場合に展開された例を次のコード サンプルに示します。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## 参照  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)