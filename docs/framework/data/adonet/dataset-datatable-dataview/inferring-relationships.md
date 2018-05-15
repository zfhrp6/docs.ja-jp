---
title: リレーションシップの推論
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 9833966fa5a16bef70a6ae2b9ca618fde0e05fbb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-relationships"></a><span data-ttu-id="22a48-102">リレーションシップの推論</span><span class="sxs-lookup"><span data-stu-id="22a48-102">Inferring Relationships</span></span>
<span data-ttu-id="22a48-103">テーブルとして推論される要素に、同じくテーブルとして推論される子の要素が含まれている場合には、2 つのテーブル間に <xref:System.Data.DataRelation> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="22a48-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="22a48-104">新しい列の名前を持つ**ParentTableName_Id**親要素に対して作成されたテーブルと子要素に対して作成されたテーブルの両方に追加されます。</span><span class="sxs-lookup"><span data-stu-id="22a48-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="22a48-105">**ColumnMapping**この id 列のプロパティ設定されます**MappingType.Hidden**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="22a48-106">列は、親テーブルの自動インクリメントの主キーになりに使用される、 **DataRelation** 2 つのテーブルです。</span><span class="sxs-lookup"><span data-stu-id="22a48-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="22a48-107">追加される id 列のデータ型になります**System.Int32**、これは他のすべての推論された列のデータ型とは異なり**System.String**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="22a48-108">A<xref:System.Data.ForeignKeyConstraint>で**DeleteRule** = **Cascade**親と子の両方のテーブルに新しい列を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="22a48-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="22a48-109">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="22a48-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="22a48-110">推論プロセスが 2 つのテーブルに生成されます: **Element1**と**ChildElement1**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="22a48-111">**Element1**テーブルが 2 つの列になります: **Element1_Id**と**ChildElement2**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="22a48-112">**ColumnMapping**のプロパティ、 **Element1_Id**列に設定されます**MappingType.Hidden**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="22a48-113">**ColumnMapping**のプロパティ、 **ChildElement2**列に設定されます**MappingType.Element**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="22a48-114">**Element1_Id**としての主キー列が設定されます、 **Element1**テーブル。</span><span class="sxs-lookup"><span data-stu-id="22a48-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="22a48-115">**ChildElement1**テーブルは 3 つの列になります: **attr1**、 **attr2**と**Element1_Id**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="22a48-116">**ColumnMapping**プロパティを**attr1**と**attr2**列を設定すること**MappingType.Attribute**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="22a48-117">**ColumnMapping**のプロパティ、 **Element1_Id**列に設定されます**MappingType.Hidden**です。</span><span class="sxs-lookup"><span data-stu-id="22a48-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="22a48-118">A **DataRelation**と**ForeignKeyConstraint**を使用して作成されます、 **Element1_Id**両方のテーブルの列です。</span><span class="sxs-lookup"><span data-stu-id="22a48-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="22a48-119">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="22a48-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="22a48-120">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="22a48-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="22a48-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="22a48-121">Element1_Id</span></span>|<span data-ttu-id="22a48-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="22a48-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="22a48-123">0</span><span class="sxs-lookup"><span data-stu-id="22a48-123">0</span></span>|<span data-ttu-id="22a48-124">Text2</span><span class="sxs-lookup"><span data-stu-id="22a48-124">Text2</span></span>|  
  
 <span data-ttu-id="22a48-125">**Table:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22a48-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="22a48-126">attr1</span><span class="sxs-lookup"><span data-stu-id="22a48-126">attr1</span></span>|<span data-ttu-id="22a48-127">attr2</span><span class="sxs-lookup"><span data-stu-id="22a48-127">attr2</span></span>|<span data-ttu-id="22a48-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="22a48-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="22a48-129">value1</span><span class="sxs-lookup"><span data-stu-id="22a48-129">value1</span></span>|<span data-ttu-id="22a48-130">value2</span><span class="sxs-lookup"><span data-stu-id="22a48-130">value2</span></span>|<span data-ttu-id="22a48-131">0</span><span class="sxs-lookup"><span data-stu-id="22a48-131">0</span></span>|  
  
 <span data-ttu-id="22a48-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22a48-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="22a48-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="22a48-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="22a48-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="22a48-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="22a48-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22a48-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="22a48-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="22a48-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="22a48-137">**入れ子になった:** は True。</span><span class="sxs-lookup"><span data-stu-id="22a48-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="22a48-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22a48-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="22a48-139">**列:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="22a48-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="22a48-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="22a48-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="22a48-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="22a48-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="22a48-142">**DeleteRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="22a48-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="22a48-143">**AcceptRejectRule:** なし</span><span class="sxs-lookup"><span data-stu-id="22a48-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a48-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="22a48-144">See Also</span></span>  
 [<span data-ttu-id="22a48-145">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="22a48-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="22a48-146">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="22a48-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="22a48-147">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="22a48-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="22a48-148">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="22a48-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="22a48-149">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="22a48-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="22a48-150">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="22a48-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="22a48-151">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="22a48-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
