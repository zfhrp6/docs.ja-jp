---
title: "XML スキーマ (XSD) からの DataSet リレーショナル構造の派生"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0aae23c295401d4b9565c35d4d47c5ab913029d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。 一般に、それぞれの`complexType`で、テーブルが生成されて、スキーマ要素の子要素、`DataSet`です。 テーブル構造は、複合型の定義に基づいて決定されます。 テーブルに作成されます、`DataSet`スキーマ内の最上位要素です。 ただし、テーブルを最上位の作成のみ`complexType`要素と、`complexType`要素が別の内部に入れ子に`complexType`を内の要素が入れ子になった場合`complexType`に要素がマップされて、`DataTable`内で、`DataSet`です。  
  
 について、XSD の詳細については、World Wide Web Consortium (W3C) XML Schema Part 0: Primer 推奨設定、XML Schema Part 1: 構造の推奨事項、および XML Schema Part 2: Datatypes recommendation 』 にある[http://www.w3.org/](http://www.w3.org/TR/)です。  
  
 次の例では、XML スキーマ、`customers`の子要素、`MyDataSet`である要素、**データセット**要素。  
  
```xml  
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
  
 上記の例では、`customers` 要素は複合型の要素です。 したがって、複合型の定義が解析され、割り当て処理によって次のテーブルが作成されます。  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 テーブルの各列のデータ型は、それに対応する指定された要素または属性の XML スキーマ型から派生します。  
  
> [!NOTE]
>  場合、要素`customers`などの単純な XML スキーマ データ型は**整数**テーブルは生成されません。 テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 次の XML スキーマで、**スキーマ**要素が 2 つの子要素、`InStateCustomers`と`OutOfStateCustomers`です。  
  
```xml  
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
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。 したがって、マッピング プロセスを生成で次の 2 つの同一テーブル、`DataSet`です。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [制約の DataSet 制約への XML スキーマ (XSD) 制約のマッピング](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 一意制約と外部キー制約の作成に使用される XML スキーマの要素について説明します、`DataSet`です。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 テーブルの列間のリレーションを作成するために使用する XML スキーマの要素について説明します、`DataSet`です。  
  
 [XML スキーマ制約およびリレーションシップ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 作成方法を説明のリレーションが暗黙的に XML スキーマの要素を使用して、内の制約を作成するときに、`DataSet`です。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 読み込んで、リレーショナル構造とデータを永続化する方法について説明、 `DataSet` XML データとして。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
