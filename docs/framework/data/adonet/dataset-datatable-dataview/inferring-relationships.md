---
title: "リレーションシップの推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 79f79c1dbc74b98cff10de81c2bd7bd32d7d286b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-relationships"></a>リレーションシップの推論
テーブルとして推論される要素に、同じくテーブルとして推論される子の要素が含まれている場合には、2 つのテーブル間に <xref:System.Data.DataRelation> が作成されます。 新しい列の名前を持つ**ParentTableName_Id**親要素に対して作成されたテーブルと子要素に対して作成されたテーブルの両方に追加されます。 **ColumnMapping**この id 列のプロパティ設定されます**MappingType.Hidden**です。 列は、親テーブルの自動インクリメントの主キーになりに使用される、 **DataRelation** 2 つのテーブルです。 追加される id 列のデータ型になります**System.Int32**、これは他のすべての推論された列のデータ型とは異なり**System.String**です。 A<xref:System.Data.ForeignKeyConstraint>で**DeleteRule** = **Cascade**親と子の両方のテーブルに新しい列を使用して作成されます。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスが 2 つのテーブルに生成されます: **Element1**と**ChildElement1**です。  
  
 **Element1**テーブルが 2 つの列になります: **Element1_Id**と**ChildElement2**です。 **ColumnMapping**のプロパティ、 **Element1_Id**列に設定されます**MappingType.Hidden**です。 **ColumnMapping**のプロパティ、 **ChildElement2**列に設定されます**MappingType.Element**です。 **Element1_Id**としての主キー列が設定されます、 **Element1**テーブル。  
  
 **ChildElement1**テーブルは 3 つの列になります: **attr1**、 **attr2**と**Element1_Id**です。 **ColumnMapping**プロパティを**attr1**と**attr2**列を設定すること**MappingType.Attribute**です。 **ColumnMapping**のプロパティ、 **Element1_Id**列に設定されます**MappingType.Hidden**です。  
  
 A **DataRelation**と**ForeignKeyConstraint**を使用して作成されます、 **Element1_Id**両方のテーブルの列です。  
  
 **データセット:** DocumentElement  
  
 **Table:** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table:** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation:** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable:** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **入れ子になった:**は True。  
  
 **ForeignKeyConstraint:** Element1_ChildElement1  
  
 **列:** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable:** ChildElement1  
  
 **DeleteRule:** Cascade  
  
 **AcceptRejectRule:**なし  
  
## <a name="see-also"></a>参照  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
