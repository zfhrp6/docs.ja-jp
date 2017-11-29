---
title: "XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f5247d0ccfd2ceec641ff29d29b889a55c1a5e12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て
スキーマで要素にキー制約を指定したり、属性を使用して、**キー**要素。 キー制約を指定する要素または属性の値は、スキーマ インスタンス内で一意になる必要があります。また、null 値にすることはできません。  
  
 キー制約を定義する列の値を null 値にできない点を除くと、キー制約は UNIQUE 制約と同じです。  
  
 次の表にアウトライン、 **msdata**属性で指定できる、**キー**要素。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合、**名前**属性は、制約の名前の値を提供します。|  
|**msdata:PrimaryKey**|場合`PrimaryKey="true"`が含まれている、 **IsPrimaryKey**制約のプロパティに設定されている**true**、ようになり、主キー。 **AllowDBNull**列のプロパティに設定されている**false**、主キーが null 値を持つことはできません。|  
  
 キーの制約が指定されているスキーマを変換するで、マッピング プロセスが含まれているテーブルに unique 制約を作成、 **AllowDBNull**設定された column プロパティ**false**の各列に対して、制約です。 **IsPrimaryKey** 、unique 制約のプロパティ設定されても**false**指定した場合を除き、`msdata:PrimaryKey="true"`上、**キー**要素。 これは、スキーマに `PrimaryKey="true"` が指定される UNIQUE 制約と同じです。  
  
 次のスキーマの例では、**キー**要素のキーの制約を指定する、 **CustomerID**要素。  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 **キー**要素には、ことを指定の値、 **CustomerID**の子要素、**顧客**要素の一意の値が必要し、null 値を持つことはできません。 XML スキーマ定義言語 (XSD) スキーマの変換では、割り当て処理によって次のテーブルが作成されます。  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 XML スキーマのマッピングも作成、 **UniqueConstraint**上、 **CustomerID**列で、次に示すように<xref:System.Data.DataSet>です。 (わかりやすいように、関連するプロパティだけを示します)。  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 **データセット**、生成される、 **IsPrimaryKey**のプロパティ、 **UniqueConstraint**に設定されている**true**のためスキーマ指定`msdata:PrimaryKey="true"`で、**キー**要素。  
  
 値、 **ConstraintName**のプロパティ、 **UniqueConstraint**で、**データセット**の値は、 **msdata:ConstraintName**指定された属性、**キー**スキーマ内の要素。  
  
## <a name="see-also"></a>関連項目  
 [制約の DataSet 制約への XML スキーマ (XSD) 制約のマッピング](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
