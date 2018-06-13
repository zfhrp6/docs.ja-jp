---
title: XML スキーマ (XSD) からの DataSet リレーションの生成
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: fdf22c311ef7b4267f4a4da8566e4ea59504b103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758439"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーションの生成
<xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。 3 つの方法を表す、**データセット**XML スキーマ定義言語 (XSD) スキーマ内の関係。  
  
-   入れ子になった複合型を指定する方法  
  
-   使用して、 **msdata:Relationship**注釈。  
  
-   指定して、**います**せず、 **msdata:ConstraintOnly**注釈。  
  
## <a name="nested-complex-types"></a>入れ子になった複合型  
 スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。 次の XML スキーマ フラグメントことを示しています**OrderDetail**の子要素、**順序**要素。  
  
```xml  
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
  
 XML スキーマの割り当て処理にテーブルが作成、**データセット**スキーマで入れ子になった複合型に対応します。 親として使用されるその他の列も作成**-** 生成されたテーブルの子列です。 これらの親を**-** 子列は主キー/外部キー制約を指定することと同じではない、リレーションシップを指定します。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 注釈  
 **Msdata:Relationship**注釈では、入れ子になっていない、スキーマ内の要素間の親子関係を明示的に指定することができます。 次の例の構造を示しています、**リレーションシップ**要素。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 属性、 **msdata:Relationship**注釈としても、親子関係に関与する要素を識別する、 **parentkey**と**childkey**要素と属性、リレーションシップに関係します。 マッピング プロセスでは、この情報を使用して、内のテーブルを生成する、**データセット**し、これらのテーブルの主キー/外部キーのリレーションシップを作成します。  
  
 たとえば、次のスキーマ フラグメントを指定して**順序**と**OrderDetail**同じレベルの要素 (入れ子にできません)。 スキーマを指定します、 **msdata:Relationship**注釈で、これら 2 つの要素間の親子リレーションシップを指定します。 この例では、明示的なリレーションシップを指定してくださいを使用して、 **msdata:Relationship**注釈。  
  
```xml  
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
  
 マッピング プロセスを使用して、**リレーションシップ**要素間の親子リレーションシップを作成する、 **OrderNumber**内の列、**順序**テーブルと、 **OrderNo**内の列、 **OrderDetail**テーブルに、**データセット**です。 割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。  
  
### <a name="in-this-section"></a>このセクションの内容  
 [入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 制約およびリレーションで暗黙的に作成された説明、**データセット**XML スキーマで入れ子になった要素が発生したとき。  
  
 [入れ子になっている要素に指定したリレーションシップの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 リレーションを明示的に設定する方法について説明、**データセット**XML スキーマで入れ子になった要素。  
  
 [入れ子になっていない要素間のリレーションの指定](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 リレーションシップを作成する方法について説明します、**データセット**入れ子になっていない XML スキーマの要素の間です。  
  
### <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 リレーショナル構造体、またはスキーマについて説明します、**データセット**XML スキーマ定義言語 (XSD) スキーマから作成します。  
  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 一意制約と外部キー制約の作成に使用される XML スキーマの要素について説明します、**データセット**です。  
  
## <a name="see-also"></a>関連項目  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
