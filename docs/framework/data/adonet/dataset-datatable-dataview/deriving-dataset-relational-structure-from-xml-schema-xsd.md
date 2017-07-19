---
title: "XML スキーマ (XSD) からの DataSet リレーショナル構造の派生 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 \(XSD\) スキーマ ドキュメントから <xref:System.Data.DataSet> のリレーショナル スキーマを生成する方法についての概要を説明します。  一般的には、スキーマの要素の各 **complexType** 子要素に対して、テーブルが **DataSet** に生成されます。  テーブル構造は、複合型の定義に基づいて決定されます。  テーブルは、スキーマのトップレベル要素の **DataSet** に作成されます。  ただし、**complexType** 要素が別の **complexType** 要素内で入れ子になっている場合、テーブルはトップレベルの **complexType** 要素にだけ作成されます。その場合、入れ子になった **complexType** 要素は、**DataSet** 内の <xref:System.Data.DataTable> に割り当てられます。  
  
 XSD の詳細については、World Wide Web Consortium \(W3C\) XML スキーマ パート 0:Primer Recommendation、XML スキーマ パート 1:Structures Recommendation、XML スキーマ パート 2:Datatypes Recommendation \([http:\/\/www.w3.org\/](http://www.w3.org/TR/) にあります\) を参照してください。  
  
 `customers` 要素が `MyDataSet` 要素の子要素である XML スキーマの例を次に示します。この `MyDataSet` 要素が **DataSet** 要素に該当します。  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 上記の例では、`customers` 要素は複合型の要素です。  したがって、複合型の定義が解析され、割り当て処理によって次のテーブルが作成されます。  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 テーブルの各列のデータ型は、それに対応する指定された要素または属性の XML スキーマ型から派生します。  
  
> [!NOTE]
>  `customers` 要素が **integer** のような単純な XML スキーマ データ型である場合、テーブルは生成されません。  テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 **Schema** 要素に `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素を持つ XML スキーマの例を次に示します。  
  
```  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です \(`customerType`\)。  したがって、割り当て処理によって **DataSet** に次の 2 つの同じテーブルが生成されます。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## このセクションの内容  
 [XML スキーマ \(XSD\) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet** での UNIQUE 制約および外部キー制約の作成に使用する XML スキーマの要素について説明します。  
  
 [XML スキーマ \(XSD\) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 **DataSet** でのテーブル列間のリレーションの生成に使用する XML スキーマの要素について説明します。  
  
 [XML スキーマ制約およびリレーションシップ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 XML スキーマの要素を使用して **DataSet** に制約を作成するときに、リレーションが暗黙的に生成される方法について説明します。  
  
## 関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 **DataSet** のリレーショナル構造とデータを XML データとして読み込んで、永続化する方法について説明します。  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)