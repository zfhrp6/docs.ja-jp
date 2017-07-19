---
title: "DataSet への既存の制約の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataSet への既存の制約の追加
**DataAdapter** の **Fill** メソッドは、<xref:System.Data.DataSet> にデータ ソースからのテーブルの列および行だけを格納します。制約は一般にデータ ソースで設定されますが、既定では **Fill** メソッドは **DataSet** にスキーマ情報を追加しません。  データ ソースからの既存の主キー制約情報を **DataSet** に設定するには、**DataAdapter** の **FillSchema** メソッドを呼び出すか、または **Fill** を呼び出す前に **DataAdapter** の **MissingSchemaAction** プロパティを **AddWithKey** に設定します。  これにより、データ ソースの主キー制約が **DataSet** の主キー制約に反映されます。  外部キー制約情報はインクルードされないため、「[DataTable の制約](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)」で示すように明示的に作成する必要があります。  
  
 **DataSet** 内にデータを格納する前にスキーマ情報を追加すると、主キー制約が **DataSet** 内の <xref:System.Data.DataTable> オブジェクトにインクルードされます。  その結果、**DataSet** に対して格納を行う追加の呼び出しを行ったとき、その主キー列情報を使用してデータ ソースから得られた新しい行と各 **DataTable** の現在の行を一致させ、各テーブルの現在のデータをデータ ソースのデータで上書きします。  スキーマ情報がないと、**DataSet** にデータ ソースからの新しい行が付け加えられ、重複行が発生します。  
  
> [!NOTE]
>  データ ソースの列を自動インクリメント列として指定した場合は、**FillSchema** メソッド \(**MissingSchemaAction** を **AddWithKey** に設定した **Fill** メソッド\) が、**AutoIncrement** プロパティを `true` に設定した **DataColumn** を作成します。  ただし、**AutoIncrementStep** 値と **AutoIncrementSeed** 値は明示的に設定する必要があります。  自動インクリメント列の詳細については、「[AutoIncrement 列の作成](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)」を参照してください。  
  
 **FillSchema** の使用や **MissingSchemaAction** の設定を **AddWithKey** にする場合、データ ソースで主キー列情報を確認するための追加の処理が必要になります。  この追加の処理によりパフォーマンスが低下する場合があります。  デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 \(複数の場合もある\) を明示的に指定することをお勧めします。  テーブルに関する主キー情報を明示的に設定する方法については、「[主キーの定義](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)」を参照してください。  
  
 **FillSchema** を使用して **DataSet** にスキーマ情報を追加する方法を次のコード サンプルに示します。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 **Fill** メソッドの **MissingSchemaAction.AddWithKey** プロパティを使用してスキーマ情報を **DataSet** に追加する方法を次のコード サンプルに示します。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## 複数の結果セットの処理  
 **DataAdapter** は、**SelectCommand** から返された複数の結果セットを検出すると **DataSet** に複数のテーブルを作成します。  これらのテーブルには、0 から始まるインクリメンタル既定名 **Table** *N* が割り当てられます。したがって "Table0" ではなく、**Table** から始まります。  テーブル名が **FillSchema** メソッドに引数として渡されると、0 からから始まるインクリメンタル名 **TableName** *N* が割り当てられます。ここでは、"TableName0" ではなく **TableName** から始まります。  
  
> [!NOTE]
>  **OleDbDataAdapter** オブジェクトの **FillSchema** メソッドが複数の結果セットを返すコマンドとして呼び出された場合は、最初の結果セットのスキーマ情報が返されます。  **OleDbDataAdapter** を使用して複数の結果セットのスキーマ情報を返すときは、**Fill** メソッドを呼び出すときに **AddWithKey** に設定した **MissingSchemaAction** を指定してスキーマ情報を取得することをお勧めします。  
  
## 参照  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [DataSets、DataTables、および DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)