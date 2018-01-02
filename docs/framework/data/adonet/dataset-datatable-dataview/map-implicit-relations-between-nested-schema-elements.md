---
title: "入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0ad26637ec8cd3e9ea555a20810805cf6eb1444e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
XML スキーマ言語定義 (XSD) スキーマでは、複数の複合型を入れ子にして指定できます。 この場合、割り当て処理には既定の割り当てが適用されます。その際、<xref:System.Data.DataSet> に作成される内容を次に示します。  
  
-   複合型 (親および子) それぞれに対して 1 つのテーブル。  
  
-   追加主キーに対して 1 列テーブルの定義がという名前の親に unique 制約が存在しない場合*TableName*_id のデータ型、 *TableName*親テーブルの名前を指定します。  
  
-   主キーとして追加される列を識別する、親テーブルに主キー制約 (設定して、 **IsPrimaryKey**プロパティを**True**)。 制約が制約を名前付き*#* 場所 *#*  1、2、3 というようにします。 たとえば、最初の制約の既定の名前は Constraint1 となります。  
  
-   子テーブルの外部キー制約により、追加された列が親テーブルの主キーを参照する外部キーとして認識されます。 制約名が*ParentTable_ChildTable*場所*ParentTable* 、親テーブルの名前を指定し、 *ChildTable*子テーブルの名前を指定します。  
  
-   その結果、親テーブルと子テーブル間のデータが関連付けられます。  
  
 次の例では、スキーマ、 **OrderDetail**の子要素は、**順序**です。  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XML スキーマの割り当て処理では、次の作成、**データセット**:  
  
-   **順序**と**OrderDetail**テーブル。  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Unique 制約、**順序**テーブル。 なお、 **IsPrimaryKey**プロパティに設定されている**True**です。  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   外部キー制約、 **OrderDetail**テーブル。  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   間のリレーションシップ、**順序**と**OrderDetail**テーブル。 **入れ子になった**このリレーションシップのプロパティに設定されて**True**ため、**順序**と**OrderDetail**スキーマ内の要素が入れ子になった.  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>参照  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
