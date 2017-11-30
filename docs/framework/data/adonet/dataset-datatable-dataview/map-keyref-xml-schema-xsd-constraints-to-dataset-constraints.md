---
title: "XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ca72292bd2c43fec6f3833d521ddb83c01c32c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
**Keyref**要素では、ドキュメント内の要素間のリンクを確立することができます。 これは、リレーショナル データベースの外部キーのリレーションシップと同様です。 スキーマを指定する場合、 **keyref**要素で、要素がのテーブル内の列に対応する外部キー制約にスキーマの割り当て処理中に変換された、<xref:System.Data.DataSet>です。 既定では、 **keyref**要素に、リレーションも生成されます、 **ParentTable**、 **ChildTable**、 **ParentColumn**、および**ChildColumn**リレーションに指定されたプロパティ。  
  
 次の表にアウトライン、 **msdata**属性で指定することができます、 **keyref**要素。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|場合**ConstraintOnly ="true"**で指定された、 **keyref**スキーマ内の要素、制約は作成されますが、リレーションシップは作成されません。 この属性が指定されていない場合 (またはに設定されている**False**)、制約とリレーションシップの両方に作成されます、**データセット**です。|  
|**msdata:ConstraintName**|場合、 **ConstraintName**属性を指定すると、その値は、制約の名前として使用します。 それ以外の場合、**名前**の属性、 **keyref**スキーマ内の要素に制約名を提供する、**データセット**です。|  
|**msdata:UpdateRule**|場合、 **UpdateRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **UpdateRule**制約プロパティに、 **データセット**です。 それ以外の場合、 **UpdateRule**プロパティに設定されている**Cascade**です。|  
|**msdata:DeleteRule**|場合、 **DeleteRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **DeleteRule**制約プロパティに、 **データセット**です。 それ以外の場合、 **DeleteRule**プロパティに設定されている**Cascade**です。|  
|**msdata:AcceptRejectRule**|場合、 **AcceptRejectRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **AcceptRejectRule**制約プロパティに、 **データセット**です。 それ以外の場合、 **AcceptRejectRule**プロパティに設定されている**None**です。|  
  
 次の例に示すスキーマが含まれています、**キー**と**keyref**間のリレーションシップ、 **OrderNumber**の子要素、**順序**要素および**OrderNo**の子要素、 **OrderDetail**要素。  
  
 例では、 **OrderNumber**の子要素、 **OrderDetail**要素を指す、 **OrderNo**のキーの子要素、**順序**要素。  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 結果は次の XML スキーマ定義言語 (XSD) スキーマの割り当て処理**データセット**2 つのテーブルで。  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 さらに、**データセット**は次の制約を定義します。  
  
-   Unique 制約、**順序**テーブル。  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   間のリレーションシップ、**順序**と**OrderDetail**テーブル。 **入れ子になった**プロパティに設定されている**False**スキーマの 2 つの要素が入れ子になっていないためです。  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   外部キー制約、 **OrderDetail**テーブル。  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>関連項目  
 [制約の DataSet 制約への XML スキーマ (XSD) 制約のマッピング](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
