---
title: "テーブルの推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="32469-102">テーブルの推論</span><span class="sxs-lookup"><span data-stu-id="32469-102">Inferring Tables</span></span>
<span data-ttu-id="32469-103">XML ドキュメントから <xref:System.Data.DataSet> のスキーマを推論するときには、ADO.NET では、テーブルを表す XML 要素を最初に決定します。</span><span class="sxs-lookup"><span data-stu-id="32469-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="32469-104">次の XML 構造の結果のテーブルに、**データセット**スキーマ。</span><span class="sxs-lookup"><span data-stu-id="32469-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="32469-105">属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="32469-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="32469-106">子要素を持つ要素</span><span class="sxs-lookup"><span data-stu-id="32469-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="32469-107">繰り返し出現する要素</span><span class="sxs-lookup"><span data-stu-id="32469-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="32469-108">属性を持つ要素</span><span class="sxs-lookup"><span data-stu-id="32469-108">Elements with Attributes</span></span>  
 <span data-ttu-id="32469-109">要素に属性が指定されている場合は、それらの要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="32469-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="32469-110">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="32469-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="32469-111">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="32469-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="32469-112">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="32469-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="32469-113">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="32469-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="32469-114">attr1</span><span class="sxs-lookup"><span data-stu-id="32469-114">attr1</span></span>|<span data-ttu-id="32469-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="32469-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="32469-116">value1</span><span class="sxs-lookup"><span data-stu-id="32469-116">value1</span></span>||  
|<span data-ttu-id="32469-117">value2</span><span class="sxs-lookup"><span data-stu-id="32469-117">value2</span></span>|<span data-ttu-id="32469-118">Text1</span><span class="sxs-lookup"><span data-stu-id="32469-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="32469-119">子要素を持つ要素</span><span class="sxs-lookup"><span data-stu-id="32469-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="32469-120">子要素を持つ要素は、テーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="32469-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="32469-121">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="32469-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="32469-122">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="32469-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="32469-123">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="32469-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="32469-124">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="32469-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="32469-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="32469-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="32469-126">Text1</span><span class="sxs-lookup"><span data-stu-id="32469-126">Text1</span></span>|  
  
 <span data-ttu-id="32469-127">ドキュメント (ルート) 要素に属性または子要素があり、それらが列として推論される場合には、そのドキュメント要素はテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="32469-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="32469-128">要素として推論ドキュメントの要素に属性がありません。 や列として推論される子要素がある場合、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="32469-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="32469-129">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="32469-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="32469-130">推論プロセスにより、"DocumentElement" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="32469-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="32469-131">**データセット:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="32469-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="32469-132">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="32469-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="32469-133">Element1</span><span class="sxs-lookup"><span data-stu-id="32469-133">Element1</span></span>|<span data-ttu-id="32469-134">Element2</span><span class="sxs-lookup"><span data-stu-id="32469-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="32469-135">Text1</span><span class="sxs-lookup"><span data-stu-id="32469-135">Text1</span></span>|<span data-ttu-id="32469-136">Text2</span><span class="sxs-lookup"><span data-stu-id="32469-136">Text2</span></span>|  
  
 <span data-ttu-id="32469-137">または、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="32469-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="32469-138">推論プロセスが生成される、**データセット**"Element1"という名前のテーブルを含む"DocumentElement"という名前</span><span class="sxs-lookup"><span data-stu-id="32469-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="32469-139">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="32469-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="32469-140">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="32469-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="32469-141">attr1</span><span class="sxs-lookup"><span data-stu-id="32469-141">attr1</span></span>|<span data-ttu-id="32469-142">attr2</span><span class="sxs-lookup"><span data-stu-id="32469-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="32469-143">value1</span><span class="sxs-lookup"><span data-stu-id="32469-143">value1</span></span>|<span data-ttu-id="32469-144">value2</span><span class="sxs-lookup"><span data-stu-id="32469-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="32469-145">繰り返し出現する要素</span><span class="sxs-lookup"><span data-stu-id="32469-145">Repeating Elements</span></span>  
 <span data-ttu-id="32469-146">繰り返し出現する要素は、単一のテーブルとして推論されます。</span><span class="sxs-lookup"><span data-stu-id="32469-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="32469-147">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="32469-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="32469-148">推論プロセスにより、"Element1" という名前のテーブルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="32469-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="32469-149">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="32469-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="32469-150">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="32469-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="32469-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="32469-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="32469-152">Text1</span><span class="sxs-lookup"><span data-stu-id="32469-152">Text1</span></span>|  
|<span data-ttu-id="32469-153">Text2</span><span class="sxs-lookup"><span data-stu-id="32469-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32469-154">参照</span><span class="sxs-lookup"><span data-stu-id="32469-154">See Also</span></span>  
 [<span data-ttu-id="32469-155">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="32469-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="32469-156">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="32469-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="32469-157">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="32469-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="32469-158">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="32469-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="32469-159">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="32469-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="32469-160">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="32469-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
