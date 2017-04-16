---
title: "入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
XML スキーマ言語定義 \(XSD\) スキーマでは、複数の複合型を入れ子にして指定できます。  この場合、割り当て処理には既定の割り当てが適用されます。その際、<xref:System.Data.DataSet> に作成される内容を次に示します。  
  
-   複合型 \(親および子\) それぞれに対して 1 つのテーブル。  
  
-   親に UNIQUE 制約がなく、親テーブル名が *TableName* である場合は、*TableName*\_Id という名前の主キー列が、テーブル定義ごとに 1 つ追加されます。  
  
-   親テーブルの主キー制約により、追加された列が主キーとして認識されます \(**IsPrimaryKey** プロパティを **True** に設定することで\)。  制約には、Constraint*\#* \(*\#* は、1、2、3 など\) という名前が付けられます。  たとえば、最初の制約の既定の名前は Constraint1 となります。  
  
-   子テーブルの外部キー制約により、追加された列が親テーブルの主キーを参照する外部キーとして認識されます。  親テーブル名が *ParentTable*、子テーブル名が *ChildTable* の場合には、制約の名前は *ParentTable\_ChildTable* となります。  
  
-   その結果、親テーブルと子テーブル間のデータが関連付けられます。  
  
 **OrderDetail** が **Order** 要素の子要素であることを示すスキーマの例を次に示します。  
  
```  
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
  
 XML スキーマの割り当て処理によって **DataSet** に作成される内容は、次のとおりです。  
  
-   **Order** および **OrderDetail** テーブル。  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   **Order** テーブルの UNIQUE 制約。  **IsPrimaryKey** プロパティは **True** に設定されるので注意してください。  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   **OrderDetail** テーブルの外部キー制約。  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   **Order** テーブルと **OrderDetail** テーブル間のリレーションシップ。  スキーマの **Order** 要素と **OrderDetail** 要素が入れ子になっているため、このリレーションシップの **Nested** プロパティは **True** に設定されます。  
  
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
  
## 参照  
 [XML スキーマ \(XSD\) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [XML スキーマ \(XSD\) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)