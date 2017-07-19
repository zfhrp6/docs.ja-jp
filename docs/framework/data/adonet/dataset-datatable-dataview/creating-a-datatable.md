---
title: "DataTable の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable の作成
<xref:System.Data.DataTable> は 1 つのインメモリ リレーショナル データのテーブルを表します。DataTable は単独で作成および使用することも、他の .NET Framework オブジェクトから <xref:System.Data.DataSet> のメンバーとして使用することもできます。  
  
 **DataTable** オブジェクトは、適切な **DataTable** コンストラクターを使用することにより作成できます。  このオブジェクトを **DataSet** に追加するには、**Add** メソッドを使用して、**DataTable** オブジェクトの **Tables** コレクションにオブジェクトを追加します。  
  
 **DataSet** の内部で **DataTable** オブジェクトを作成する場合は、**DataAdapter** オブジェクトの **Fill** メソッドまたは **FillSchema** メソッドを使用できます。また、定義済みまたは推論による XML スキーマで、**DataSet** の **ReadXml**、**ReadXmlSchema**、または **InferXmlSchema** の各メソッドを使用して作成することもできます。  **DataTable** を 1 つの **DataSet** の **Tables** コレクションのメンバーとして追加した後で、その **DataTable** を他の **DataSet** のテーブルのコレクションに追加することはできません。  
  
 最初に作成した時点では、**DataTable** にはスキーマ \(構造\) がありません。  テーブルのスキーマを定義するには、<xref:System.Data.DataColumn> オブジェクトを作成し、テーブルの **Columns** コレクションに追加する必要があります。  テーブルの主キー列を定義したり、**Constraint** オブジェクトを作成してテーブルの **Constraints** コレクションに追加したりすることもできます。  **DataTable** のスキーマを定義した後で、**DataRow** オブジェクトをテーブルの **Rows** コレクションに追加することにより、データ行をテーブルに追加できます。  
  
 **DataTable** を作成するときに <xref:System.Data.DataTable.TableName%2A> プロパティの値を指定する必要はありません。このプロパティは、後から指定することも、空のままにしておくこともできます。  ただし、**TableName** 値のないテーブルを **DataSet** に追加した場合、そのテーブルの名前は既定のテーブル名 Table*N* になります。この既定名は Table0 に相当する "Table" から始まり、連続する番号が割り当てられていきます。  
  
> [!NOTE]
>  **TableName** 値を指定するときには、"Table*N*" の命名規則を使用しないことをお勧めします。これは、指定した名前が **DataSet** に既に存在する既定のテーブル名と競合しないようにするためです。  指定した名前が既に存在する場合は、例外がスローされます。  
  
 **DataTable** オブジェクトのインスタンスを作成し、"Customers" という名前を割り当てる例を次に示します。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 **DataTable** のインスタンスを作成し、**DataSet** の **Tables** コレクションに追加する例を次に示します。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## 参照  
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataTableCollection>   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [DataAdapter からの DataSet の読み込み](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)