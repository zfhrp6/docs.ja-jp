---
title: "XML スキーマ (XSD) からの DataSet リレーションの生成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XML スキーマ (XSD) からの DataSet リレーションの生成
<xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。  XML スキーマ定義言語 \(XSD\) スキーマ内で **DataSet** のリレーションを表すには、次の 3 つの方法があります。  
  
-   入れ子になった複合型を指定する方法  
  
-   **msdata:Relationship** 注釈を使用する方法  
  
-   **msdata:ConstraintOnly** 注釈を使用せずに **xs:keyref** を指定する方法  
  
## 入れ子になった複合型  
 スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。  **OrderDetail** が **Order** 要素の子要素であることを示す XML スキーマのフラグメントを次に示します。  
  
```  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 XML スキーマの割り当て処理によって、スキーマの入れ子になった複合型に対応する **DataSet** にテーブルが作成されます。  また、生成されたテーブルの親子列として使用される追加列も作成されます。  その親子列ではリレーションシップが指定されますが、主キー制約や外部キー制約の指定とは異なるため注意してください。  
  
## msdata:Relationship 注釈  
 **msdata:Relationship** 注釈を使用すると、入れ子になっていないスキーマの要素間の親子のリレーションシップを明示的に指定できます。  **Relationship** 要素の構造を示す例を次に示します。  
  
```  
  
  <msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 **msdata:Relationship** 注釈の属性は、リレーションシップに必要な **parentkey** 要素と **childkey** 要素、および属性と同様に親子のリレーションシップに必要な要素を示します。  割り当て処理では、その情報に基づいて **DataSet** にテーブルを作成し、それらのテーブル間に主キー\/外部キーのリレーションシップを作成します。  
  
 たとえば、同じレベルで \(入れ子にせずに\) **Order** 要素と **OrderDetail** 要素を指定するスキーマのフラグメントを次に示します。  スキーマに **msdata:Relationship** 注釈を指定すると、その 2 つの要素間に親子のリレーションシップが指定されます。  この場合、**msdata:Relationship** 注釈を使用してリレーションシップを明示的に指定する必要があります。  
  
```  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
  
```  
  
 割り当て処理では、**Relationship** 要素を使用して、**DataSet** にある **Order** テーブルの **OrderNumber** 列と **OrderDetail** テーブルの **OrderNo** 列に親子のリレーションシップが生成されます。  割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。  
  
### このセクションの内容  
 [入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 XML スキーマ内で要素が入れ子になっている場合に、**DataSet** 内に暗黙的に作成される制約とリレーションについて説明します。  
  
 [入れ子になっている要素に指定したリレーションシップの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 XML スキーマで入れ子になっている要素に対して、**DataSet** におけるリレーションを明示的に設定する方法について説明します。  
  
 [入れ子になっていない要素間のリレーションの指定](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 XML スキーマで入れ子になっていない要素間に、**DataSet** におけるリレーションを作成する方法について説明します。  
  
### 関連項目  
 [XML スキーマ \(XSD\) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML スキーマ定義言語 \(XSD\) スキーマから作成された **DataSet** のリレーショナル構造 \(スキーマ\) について説明します。  
  
 [XML スキーマ \(XSD\) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet** での UNIQUE 制約および外部キー制約の作成に使用する XML スキーマの要素について説明します。  
  
## 参照  
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)