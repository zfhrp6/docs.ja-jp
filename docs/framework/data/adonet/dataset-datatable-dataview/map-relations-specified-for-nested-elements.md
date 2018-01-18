---
title: "入れ子になっている要素に指定したリレーションシップの割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c23e951ee2fd6f5956ab41d4425c9e8af8f12b95
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="map-relations-specified-for-nested-elements"></a>入れ子になっている要素に指定したリレーションシップの割り当て
スキーマを含めることができます、 **msdata:Relationship**注釈をスキーマ内にある 2 つの要素間のマッピングを明示的に指定します。 2 つの要素で指定された**msdata:Relationship**スキーマでは、入れ子にすることができますが、する必要はありません。 マッピング プロセスを使用して**msdata:Relationship**を 2 つの列の間で主キー/外部キーのリレーションシップを生成するスキーマです。  
  
 次の例を XML スキーマを示しています、 **OrderDetail**要素は、子要素の**順序**です。 **Msdata:Relationship**この親子リレーションシップを識別し、指定する、 **OrderNumber**列と生成された**順序**に関連するテーブル、**OrderNo**列と生成された**OrderDetail**テーブル。  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 XML スキーマの割り当て処理によって <xref:System.Data.DataSet> に作成される内容は、次のとおりです。  
  
-   **順序**と**OrderDetail**テーブル。  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   間のリレーションシップ、**順序**と**OrderDetail**テーブル。 **入れ子になった**このリレーションシップのプロパティに設定されて**True**ため、**順序**と**OrderDetail**スキーマ内の要素が入れ子になった.  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 割り当て処理によって制約は作成されません。  
  
## <a name="see-also"></a>参照  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
