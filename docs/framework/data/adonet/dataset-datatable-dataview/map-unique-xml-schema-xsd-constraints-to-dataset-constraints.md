---
title: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8aed9830d613eeb7d49d2339a8ac1892c0e28e93
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) スキーマで、**一意**要素が要素または属性の一意性制約を指定します。 XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataTable> に対応する <xref:System.Data.DataSet> の UNIQUE 制約に割り当てられます。  
  
 次の表にアウトライン、 **msdata**属性で指定できる、**一意**要素。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合、**名前**属性は、制約の名前の値を提供します。|  
|**msdata:PrimaryKey**|場合`PrimaryKey="true"`に存在、**一意**要素、unique 制約が作成され、 **IsPrimaryKey**プロパティに設定**true**です。|  
  
 次の例を使用する XML スキーマ、**一意**一意性制約を指定する要素。  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 **一意**スキーマ内の要素を指定するすべての**顧客**ドキュメント内の要素のインスタンスの値、 **CustomerID**子要素を一意にする必要があります。 ビル、**データセット**、マッピング プロセスがこのスキーマを読み込み、次の表を生成します。  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 マッピング プロセスで、unique 制約も作成されます、 **CustomerID**列で、次に示すように**データセット**です。 (わかりやすいように、関連するプロパティだけを示します)。  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 **データセット**、生成される、 **IsPrimaryKey**プロパティに設定されている**False**一意制約。 **一意**、列のプロパティを示す、 **CustomerID**列の値は一意である必要があります (null 参照で指定された可能性があるが、 **AllowDBNull**列のプロパティ)。  
  
 スキーマを変更し、省略可能な**msdata:PrimaryKey**属性に値**True**テーブルに unique 制約を作成します。 **AllowDBNull**列のプロパティに設定されている**False**、および**IsPrimaryKey**プロパティに設定する制約の**True**のため、**CustomerID**列、主キー列です。  
  
 XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。 次の例は、ことを指定する方法の組み合わせを示します**CustomerID**と**CompanyName**値はすべて一意である必要があります**顧客**任意のインスタンスで、追加する**xs:field**スキーマ内の要素。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 これは、結果として得られるで作成された制約**データセット**です。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>関連項目  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
