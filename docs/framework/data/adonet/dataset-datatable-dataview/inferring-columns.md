---
title: "列の推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9690359fdd288ea58de72f30a3dc5d6222b9f933
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-columns"></a><span data-ttu-id="fae36-102">列の推論</span><span class="sxs-lookup"><span data-stu-id="fae36-102">Inferring Columns</span></span>
<span data-ttu-id="fae36-103">ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。</span><span class="sxs-lookup"><span data-stu-id="fae36-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="fae36-104">ADO.NET 2.0 導入ごとに厳密に型指定されたデータ型を推測する新しいスキーマ推論エンジン**simpleType**要素。</span><span class="sxs-lookup"><span data-stu-id="fae36-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="fae36-105">以前のバージョンで、データ型、推論された**simpleType**要素が常に**xsd:string**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="fae36-106">移行および下位互換性</span><span class="sxs-lookup"><span data-stu-id="fae36-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="fae36-107">**ReadXml**メソッドが型の引数を受け取る**InferSchema**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="fae36-108">この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="fae36-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="fae36-109">使用可能な値、 **InferSchema**列挙体は、次の表に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="fae36-110">単純型を <xref:System.String> として常に推論することで下位互換性を提供します。</span><span class="sxs-lookup"><span data-stu-id="fae36-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="fae36-111">厳密に型指定されたデータ型を推論します。</span><span class="sxs-lookup"><span data-stu-id="fae36-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="fae36-112"><xref:System.Data.DataTable> で使用した場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="fae36-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="fae36-113">インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。</span><span class="sxs-lookup"><span data-stu-id="fae36-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="fae36-114">属性</span><span class="sxs-lookup"><span data-stu-id="fae36-114">Attributes</span></span>  
 <span data-ttu-id="fae36-115">定義されている[テーブルの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)属性を持つ要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="fae36-116">その要素の属性は、そのテーブルの列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="fae36-117">**ColumnMapping**列のプロパティ設定されます**MappingType.Attribute**スキーマが XML に書き戻さか、列名が属性として書き込まれますことを確認するためです。</span><span class="sxs-lookup"><span data-stu-id="fae36-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="fae36-118">属性の値は、テーブルの行に格納されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="fae36-119">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fae36-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fae36-120">推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**attr1**と**attr2**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="fae36-121">**ColumnMapping**両方の列のプロパティ設定されます**MappingType.Attribute**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="fae36-122">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fae36-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fae36-123">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="fae36-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fae36-124">attr1</span><span class="sxs-lookup"><span data-stu-id="fae36-124">attr1</span></span>|<span data-ttu-id="fae36-125">attr2</span><span class="sxs-lookup"><span data-stu-id="fae36-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="fae36-126">value1</span><span class="sxs-lookup"><span data-stu-id="fae36-126">value1</span></span>|<span data-ttu-id="fae36-127">value2</span><span class="sxs-lookup"><span data-stu-id="fae36-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="fae36-128">属性または子の要素を持たない要素</span><span class="sxs-lookup"><span data-stu-id="fae36-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="fae36-129">要素に子の要素または属性がない場合、その要素は列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="fae36-130">**ColumnMapping**列のプロパティ設定されます**MappingType.Element**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="fae36-131">子の要素のテキストは、テーブルの行に格納されます。</span><span class="sxs-lookup"><span data-stu-id="fae36-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="fae36-132">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="fae36-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fae36-133">推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**ChildElement1**と**ChildElement2**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="fae36-134">**ColumnMapping**両方の列のプロパティ設定されます**MappingType.Element**です。</span><span class="sxs-lookup"><span data-stu-id="fae36-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="fae36-135">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fae36-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fae36-136">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="fae36-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fae36-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fae36-137">ChildElement1</span></span>|<span data-ttu-id="fae36-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="fae36-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="fae36-139">Text1</span><span class="sxs-lookup"><span data-stu-id="fae36-139">Text1</span></span>|<span data-ttu-id="fae36-140">Text2</span><span class="sxs-lookup"><span data-stu-id="fae36-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fae36-141">参照</span><span class="sxs-lookup"><span data-stu-id="fae36-141">See Also</span></span>  
 [<span data-ttu-id="fae36-142">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="fae36-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="fae36-143">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="fae36-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="fae36-144">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="fae36-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="fae36-145">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="fae36-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="fae36-146">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="fae36-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="fae36-147">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="fae36-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
