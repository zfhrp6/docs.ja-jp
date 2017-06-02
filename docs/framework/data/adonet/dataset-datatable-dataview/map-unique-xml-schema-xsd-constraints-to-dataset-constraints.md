---
title: "XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
XML スキーマ定義言語 \(XSD\) スキーマでは、**unique** 要素を使用して要素または属性の UNIQUE 制約を指定します。  XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataSet> に対応する <xref:System.Data.DataTable> の UNIQUE 制約に割り当てられます。  
  
 **unique** 要素で指定できる **msdata** 属性を次の表に示します。  
  
|属性名|説明|  
|---------|--------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。  それ以外の場合は、**name** 属性によって制約名の値が設定されます。|  
|**msdata:PrimaryKey**|**unique** 要素に `PrimaryKey="true"` がある場合、UNIQUE 制約は、**IsPrimaryKey** プロパティが **true** に設定された状態で作成されます。|  
  
 **unique** 要素を使用して UNIQUE 制約を指定する XML スキーマの例を次に示します。  
  
```  
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
   <xs:unique      
msdata:ConstraintName="UCustID"      
name="UniqueCustIDConstr" >        
<xs:selector xpath=".//Customers" />        
<xs:field xpath="CustomerID" />      
</xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 スキーマの **unique** 要素を使用して、ドキュメント インスタンスのすべての **Customers** 要素に unique 要素を指定します。**CustomerID** 子要素の値は一意になる必要があります。  **DataSet** を作成する場合は、割り当て処理によってスキーマが読み込まれ、次のテーブルが生成されます。  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 次の **DataSet** に示すように、割り当てプロセスによって **CustomerID** 列に対して UNIQUE 制約を作成することもできます   \(わかりやすいように、関連するプロパティだけを示します\)。  
  
```  
  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID  
      Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 生成される **DataSet** は UNIQUE 制約のために **IsPrimaryKey** プロパティが **False** に設定されます。  列の **unique** プロパティは、**CustomerID** 列の値が一意であることを示します \(ただし、列の **AllowDBNull** プロパティで指定されているように、CustomerID の値は null 参照となります\)。  
  
 スキーマを変更し、オプションの **msdata:PrimaryKey** 属性を **True** に設定すると、UNIQUE 制約がテーブルに作成されます。  **AllowDBNull** 列のプロパティが **False** に、制約の **IsPrimaryKey** プロパティが **True** に設定されると、**CustomerID** 列が主キー列になります。  
  
 XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。  スキーマに別の xs:field 要素を追加することにより、Customer**ID** の値と **CompanyName** の値の組み合わせを任意のインスタンスのすべての **Customers** に対して必ず一意になるように指定する方法を次の例で示します。  
  
```  
  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 その結果、**DataSet** に作成される制約を次に示します。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## 参照  
 [XML スキーマ \(XSD\) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)   
 [XML スキーマ \(XSD\) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)