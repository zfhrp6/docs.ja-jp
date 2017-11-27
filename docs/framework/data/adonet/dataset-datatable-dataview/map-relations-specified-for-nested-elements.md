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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9866b556f2ba09cef7616fea4a2a6d8135e6b8e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="d17d0-102">入れ子になっている要素に指定したリレーションシップの割り当て</span><span class="sxs-lookup"><span data-stu-id="d17d0-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="d17d0-103">スキーマを含めることができます、 **msdata:Relationship**注釈をスキーマ内にある 2 つの要素間のマッピングを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="d17d0-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="d17d0-104">2 つの要素で指定された**msdata:Relationship**スキーマでは、入れ子にすることができますが、する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d17d0-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="d17d0-105">マッピング プロセスを使用して**msdata:Relationship**を 2 つの列の間で主キー/外部キーのリレーションシップを生成するスキーマです。</span><span class="sxs-lookup"><span data-stu-id="d17d0-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="d17d0-106">次の例を XML スキーマを示しています、 **OrderDetail**要素は、子要素の**順序**です。</span><span class="sxs-lookup"><span data-stu-id="d17d0-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="d17d0-107">**Msdata:Relationship**この親子リレーションシップを識別し、指定する、 **OrderNumber**列と生成された**順序**に関連するテーブル、**OrderNo**列と生成された**OrderDetail**テーブル。</span><span class="sxs-lookup"><span data-stu-id="d17d0-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
  
 <span data-ttu-id="d17d0-108">XML スキーマの割り当て処理によって <xref:System.Data.DataSet> に作成される内容は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d17d0-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="d17d0-109">**順序**と**OrderDetail**テーブル。</span><span class="sxs-lookup"><span data-stu-id="d17d0-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="d17d0-110">間のリレーションシップ、**順序**と**OrderDetail**テーブル。</span><span class="sxs-lookup"><span data-stu-id="d17d0-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="d17d0-111">**入れ子になった**このリレーションシップのプロパティに設定されて**True**ため、**順序**と**OrderDetail**スキーマ内の要素が入れ子になった.</span><span class="sxs-lookup"><span data-stu-id="d17d0-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="d17d0-112">割り当て処理によって制約は作成されません。</span><span class="sxs-lookup"><span data-stu-id="d17d0-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17d0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d17d0-113">See Also</span></span>  
 [<span data-ttu-id="d17d0-114">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="d17d0-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="d17d0-115">制約の DataSet 制約への XML スキーマ (XSD) 制約のマッピング</span><span class="sxs-lookup"><span data-stu-id="d17d0-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="d17d0-116">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d17d0-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
