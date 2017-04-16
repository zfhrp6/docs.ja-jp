---
title: "DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable
<xref:System.Data.DataSet> は、テーブル、リレーションシップ、および制約のコレクションで構成されます。  ADO.NET では、**DataSet** 内のテーブルを表すために <xref:System.Data.DataTable> オブジェクトを使用します。  **DataTable** は、1 つのメモリ内のリレーショナル データ テーブルを表します。このテーブルのデータは、そのデータが存在する .NET ベース アプリケーションのローカル データですが、**DataAdapter** を使用して Microsoft SQL Server などのデータ ソースから読み込むこともできます。詳細については、「[DataAdapter からの DataSet の読み込み](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)」を参照してください。  
  
 **DataTable** クラスは、.NET Framework クラス ライブラリ内の **System.Data** 名前空間のメンバーです。  **DataTable** は、単独でも **DataSet** のメンバーとしても作成および使用できます。また、**DataTable** オブジェクトは、<xref:System.Data.DataView> などの他の .NET Framework オブジェクトからも使用できます。  **DataSet** 内のテーブルのコレクションには、**DataSet** オブジェクトの **Tables** プロパティを使用してアクセスします。  
  
 テーブルのスキーマ \(構造\) は、列と制約で表されます。  **DataTable** のスキーマは、<xref:System.Data.DataColumn>、<xref:System.Data.ForeignKeyConstraint>、<xref:System.Data.UniqueConstraint> の各オブジェクトを使用して定義します。  テーブルの列は、データ ソースの列に割り当てたり、式で算出された値を格納したり、格納されている値を自動的にインクリメントしたり、主キー値を格納したりできます。  
  
 **DataTable** には、スキーマだけでなく、データを格納して順序付けるための行も必要です。  <xref:System.Data.DataRow> クラスは、テーブルに格納される実際のデータを表します。  **DataRow** およびそのプロパティとメソッドを使用して、テーブル内のデータを取得、評価、および操作できます。  行内のデータがアクセスされて変更されたときは、**DataRow** オブジェクトは、変更後の現在の状態と変更前の状態を維持します。  
  
 テーブル間で 1 つ以上の列を関連付け、テーブル間の親子のリレーションシップを作成できます。  **DataTable** オブジェクト間のリレーションシップを作成するには、<xref:System.Data.DataRelation> を使用します。  **DataRelation** オブジェクトを使用すると、特定の行に関連付けられた子の行または親の行を返すことができます。  詳細については、「[DataRelation の追加](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)」を参照してください。  
  
## このセクションの内容  
 [DataTable の作成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 **DataTable** を作成して **DataSet** に追加する方法について説明します。  
  
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 **DataColumn** オブジェクトと制約の作成および使用について説明します。  
  
 [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 テーブル内のデータを追加、変更、および削除する方法について説明します。  **DataTable** イベントを使用してテーブル内のデータが変更されたかどうかを確認する方法について説明します。  
  
 [DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 列値が変更された場合や行が追加または削除された場合のイベントなど、**DataTable** で使用できるイベントについて説明します。  
  
## 関連項目  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 ADO.NET のアーキテクチャとコンポーネントについて説明し、ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。  
  
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 テーブル間のリレーションシップを作成する方法も含め、ADO.NET の **DataSet** について説明します。  
  
 [Constraint クラス](frlrfSystemDataConstraintClassTopic)  
 **Constraint** オブジェクトの参照情報を提供します。  
  
 [DataColumn クラス](frlrfSystemDataDataColumnClassTopic)  
 **DataColumn** オブジェクトの参照情報を提供します。  
  
 [DataSet クラス](frlrfSystemDataDataSetClassTopic)  
 **DataSet** オブジェクトの参照情報を提供します。  
  
 [DataTable クラス](frlrfSystemDataDataTableClassTopic)  
 **DataTable** オブジェクトの参照情報を提供します。  
  
 [クラス ライブラリの概要](../../../../../docs/standard/class-library-overview.md)  
 **System** 名前空間やその下位レベルの名前空間 **System.Data** を含む .NET Framework クラス ライブラリの概要について説明します。  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)