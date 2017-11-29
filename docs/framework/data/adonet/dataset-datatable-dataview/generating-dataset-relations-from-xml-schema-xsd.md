---
title: "XML スキーマ (XSD) からの DataSet リレーションの生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bda9ff0052c6dc2462f007e3febb3cbf9ca7d5ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="fdddf-102">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="fdddf-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="fdddf-103"><xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。</span><span class="sxs-lookup"><span data-stu-id="fdddf-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="fdddf-104">3 つの方法を表す、**データセット**XML スキーマ定義言語 (XSD) スキーマ内の関係。</span><span class="sxs-lookup"><span data-stu-id="fdddf-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="fdddf-105">入れ子になった複合型を指定する方法</span><span class="sxs-lookup"><span data-stu-id="fdddf-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="fdddf-106">使用して、 **msdata:Relationship**注釈。</span><span class="sxs-lookup"><span data-stu-id="fdddf-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="fdddf-107">指定して、**います**せず、 **msdata:ConstraintOnly**注釈。</span><span class="sxs-lookup"><span data-stu-id="fdddf-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="fdddf-108">入れ子になった複合型</span><span class="sxs-lookup"><span data-stu-id="fdddf-108">Nested Complex Types</span></span>  
 <span data-ttu-id="fdddf-109">スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="fdddf-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="fdddf-110">次の XML スキーマ フラグメントことを示しています**OrderDetail**の子要素、**順序**要素。</span><span class="sxs-lookup"><span data-stu-id="fdddf-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="fdddf-111">XML スキーマの割り当て処理にテーブルが作成、**データセット**スキーマで入れ子になった複合型に対応します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="fdddf-112">親として使用されるその他の列も作成**-**生成されたテーブルの子列です。</span><span class="sxs-lookup"><span data-stu-id="fdddf-112">It also creates additional columns that are used as parent**-**child columns for the generated tables.</span></span> <span data-ttu-id="fdddf-113">これらの親を**-**子列は主キー/外部キー制約を指定することと同じではない、リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-113">Note that these parent**-**child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="fdddf-114">msdata:Relationship 注釈</span><span class="sxs-lookup"><span data-stu-id="fdddf-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="fdddf-115">**Msdata:Relationship**注釈では、入れ子になっていない、スキーマ内の要素間の親子関係を明示的に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="fdddf-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="fdddf-116">次の例の構造を示しています、**リレーションシップ**要素。</span><span class="sxs-lookup"><span data-stu-id="fdddf-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="fdddf-117">属性、 **msdata:Relationship**注釈としても、親子関係に関与する要素を識別する、 **parentkey**と**childkey**要素と属性、リレーションシップに関係します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="fdddf-118">マッピング プロセスでは、この情報を使用して、内のテーブルを生成する、**データセット**し、これらのテーブルの主キー/外部キーのリレーションシップを作成します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="fdddf-119">たとえば、次のスキーマ フラグメントを指定して**順序**と**OrderDetail**同じレベルの要素 (入れ子にできません)。</span><span class="sxs-lookup"><span data-stu-id="fdddf-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="fdddf-120">スキーマを指定します、 **msdata:Relationship**注釈で、これら 2 つの要素間の親子リレーションシップを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="fdddf-121">この例では、明示的なリレーションシップを指定してくださいを使用して、 **msdata:Relationship**注釈。</span><span class="sxs-lookup"><span data-stu-id="fdddf-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="fdddf-122">マッピング プロセスを使用して、**リレーションシップ**要素間の親子リレーションシップを作成する、 **OrderNumber**内の列、**順序**テーブルと、 **OrderNo**内の列、 **OrderDetail**テーブルに、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="fdddf-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="fdddf-123">割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fdddf-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="fdddf-124">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fdddf-124">In This Section</span></span>  
 [<span data-ttu-id="fdddf-125">入れ子になったスキーマ要素間の暗黙的なリレーションのマップ</span><span class="sxs-lookup"><span data-stu-id="fdddf-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="fdddf-126">制約およびリレーションで暗黙的に作成された説明、**データセット**XML スキーマで入れ子になった要素が発生したとき。</span><span class="sxs-lookup"><span data-stu-id="fdddf-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="fdddf-127">入れ子になった要素に指定されたリレーションシップを割り当てください。</span><span class="sxs-lookup"><span data-stu-id="fdddf-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="fdddf-128">リレーションを明示的に設定する方法について説明、**データセット**XML スキーマで入れ子になった要素。</span><span class="sxs-lookup"><span data-stu-id="fdddf-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="fdddf-129">入れ子になっていない要素間のリレーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="fdddf-130">リレーションシップを作成する方法について説明します、**データセット**入れ子になっていない XML スキーマの要素の間です。</span><span class="sxs-lookup"><span data-stu-id="fdddf-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="fdddf-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdddf-131">Related Sections</span></span>  
 [<span data-ttu-id="fdddf-132">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="fdddf-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="fdddf-133">リレーショナル構造体、またはスキーマについて説明します、**データセット**XML スキーマ定義言語 (XSD) スキーマから作成します。</span><span class="sxs-lookup"><span data-stu-id="fdddf-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="fdddf-134">制約の DataSet 制約への XML スキーマ (XSD) 制約のマッピング</span><span class="sxs-lookup"><span data-stu-id="fdddf-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fdddf-135">一意制約と外部キー制約の作成に使用される XML スキーマの要素について説明します、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="fdddf-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdddf-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdddf-136">See Also</span></span>  
 [<span data-ttu-id="fdddf-137">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="fdddf-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
