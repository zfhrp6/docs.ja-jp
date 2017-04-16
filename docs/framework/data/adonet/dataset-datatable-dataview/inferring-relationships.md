---
title: "リレーションシップの推論 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# リレーションシップの推論
テーブルとして推論される要素に、同じくテーブルとして推論される子の要素が含まれている場合には、2 つのテーブル間に <xref:System.Data.DataRelation> が作成されます。  この場合、**ParentTableName\_Id** という名前の新しい列が、親の要素に対して作成されたテーブルと、子の要素に対して作成されたテーブルの両方に追加されます。  この ID 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。  この列が、親テーブルの自動的にインクリメントされる主キーとなり、2 つのテーブル間の **DataRelation** で使用されます。  推論される他のすべての列のデータ型は **System.String** になりますが、追加される ID 列のデータ型は **System.Int32** になります。  親テーブルおよび子テーブルの両方に追加されたこの新しい列を使用して、**DeleteRule** \= **Cascade** である <xref:System.Data.ForeignKeyConstraint> も作成されます。  
  
 たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、**Element1** および **ChildElement1** という名前の 2 つのテーブルが生成されます。  
  
 **Element1** テーブルには、**Element1\_Id** および **ChildElement2** という名前の 2 つの列があります。  **Element1\_Id** 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。  **ChildElement2** 列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。  **Element1\_Id** 列は、**Element1** テーブルの主キーとして設定されます。  
  
 **ChildElement1** テーブルには、**attr1**、**attr2**、および **Element1\_Id** という名前の 3 つの列があります。  **attr1** 列および **attr2** 列の **ColumnMapping** プロパティは、**MappingType.Attribute** に設定されます。  **Element1\_Id** 列の **ColumnMapping** プロパティは、**MappingType.Hidden** に設定されます。  
  
 2 つのテーブルの **Element1\_Id** 列を使用して、**DataRelation** および **ForeignKeyConstraint** が作成されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|Element1\_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table:** ChildElement1  
  
|attr1|attr2|Element1\_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation:** Element1\_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1\_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1\_Id  
  
 **Nested:** True  
  
 **ForeignKeyConstraint:** Element1\_ChildElement1  
  
 **Column:** Element1\_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:** None  
  
## 参照  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)