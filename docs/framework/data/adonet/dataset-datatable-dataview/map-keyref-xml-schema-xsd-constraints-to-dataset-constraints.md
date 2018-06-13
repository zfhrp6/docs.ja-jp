---
title: XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: a3a5033292db2b47e7a9811e36c0a4af016951fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758556"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="27c39-102">XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="27c39-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="27c39-103">**Keyref**要素では、ドキュメント内の要素間のリンクを確立することができます。</span><span class="sxs-lookup"><span data-stu-id="27c39-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="27c39-104">これは、リレーショナル データベースの外部キーのリレーションシップと同様です。</span><span class="sxs-lookup"><span data-stu-id="27c39-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="27c39-105">スキーマを指定する場合、 **keyref**要素で、要素がのテーブル内の列に対応する外部キー制約にスキーマの割り当て処理中に変換された、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="27c39-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="27c39-106">既定では、 **keyref**要素に、リレーションも生成されます、 **ParentTable**、 **ChildTable**、 **ParentColumn**、および**ChildColumn**リレーションに指定されたプロパティ。</span><span class="sxs-lookup"><span data-stu-id="27c39-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="27c39-107">次の表にアウトライン、 **msdata**属性で指定することができます、 **keyref**要素。</span><span class="sxs-lookup"><span data-stu-id="27c39-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="27c39-108">属性名</span><span class="sxs-lookup"><span data-stu-id="27c39-108">Attribute name</span></span>|<span data-ttu-id="27c39-109">説明</span><span class="sxs-lookup"><span data-stu-id="27c39-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="27c39-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="27c39-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="27c39-111">場合**ConstraintOnly ="true"** で指定された、 **keyref**スキーマ内の要素、制約は作成されますが、リレーションシップは作成されません。</span><span class="sxs-lookup"><span data-stu-id="27c39-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="27c39-112">この属性が指定されていない場合 (またはに設定されている**False**)、制約とリレーションシップの両方に作成されます、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="27c39-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="27c39-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="27c39-114">場合、 **ConstraintName**属性を指定すると、その値は、制約の名前として使用します。</span><span class="sxs-lookup"><span data-stu-id="27c39-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="27c39-115">それ以外の場合、**名前**の属性、 **keyref**スキーマ内の要素に制約名を提供する、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="27c39-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="27c39-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="27c39-117">場合、 **UpdateRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **UpdateRule**制約プロパティに、 **データセット**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="27c39-118">それ以外の場合、 **UpdateRule**プロパティに設定されている**Cascade**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="27c39-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="27c39-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="27c39-120">場合、 **DeleteRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **DeleteRule**制約プロパティに、 **データセット**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="27c39-121">それ以外の場合、 **DeleteRule**プロパティに設定されている**Cascade**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="27c39-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="27c39-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="27c39-123">場合、 **AcceptRejectRule**属性が指定した、 **keyref**スキーマ内の要素、その値は、 **AcceptRejectRule**制約プロパティに、 **データセット**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="27c39-124">それ以外の場合、 **AcceptRejectRule**プロパティに設定されている**None**です。</span><span class="sxs-lookup"><span data-stu-id="27c39-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="27c39-125">次の例に示すスキーマが含まれています、**キー**と**keyref**間のリレーションシップ、 **OrderNumber**の子要素、**順序**要素および**OrderNo**の子要素、 **OrderDetail**要素。</span><span class="sxs-lookup"><span data-stu-id="27c39-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="27c39-126">例では、 **OrderNumber**の子要素、 **OrderDetail**要素を指す、 **OrderNo**のキーの子要素、**順序**要素。</span><span class="sxs-lookup"><span data-stu-id="27c39-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="27c39-127">結果は次の XML スキーマ定義言語 (XSD) スキーマの割り当て処理**データセット**2 つのテーブルで。</span><span class="sxs-lookup"><span data-stu-id="27c39-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="27c39-128">さらに、**データセット**は次の制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="27c39-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="27c39-129">Unique 制約、**順序**テーブル。</span><span class="sxs-lookup"><span data-stu-id="27c39-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="27c39-130">間のリレーションシップ、**順序**と**OrderDetail**テーブル。</span><span class="sxs-lookup"><span data-stu-id="27c39-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="27c39-131">**入れ子になった**プロパティに設定されている**False**スキーマの 2 つの要素が入れ子になっていないためです。</span><span class="sxs-lookup"><span data-stu-id="27c39-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="27c39-132">外部キー制約、 **OrderDetail**テーブル。</span><span class="sxs-lookup"><span data-stu-id="27c39-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27c39-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="27c39-133">See Also</span></span>  
 [<span data-ttu-id="27c39-134">XML スキーマ (XSD) 制約の DataSet 制約への割り当て</span><span class="sxs-lookup"><span data-stu-id="27c39-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="27c39-135">XML スキーマ (XSD) からの DataSet リレーションの生成</span><span class="sxs-lookup"><span data-stu-id="27c39-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="27c39-136">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="27c39-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
