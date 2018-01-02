---
title: "要素のテキストの推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 00a66a1f995ac4d705af2bf39993cb387e3bf25d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inferring-element-text"></a><span data-ttu-id="0a6bd-102">要素のテキストの推論</span><span class="sxs-lookup"><span data-stu-id="0a6bd-102">Inferring Element Text</span></span>
<span data-ttu-id="0a6bd-103">要素のテキストが含まれています (要素の属性を持つ) や、繰り返される要素など、名前の新しい列をテーブルとして推論される子要素が存在しない場合**TableName_Text**要素に対して推論されるテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="0a6bd-104">要素に含まれているテキストはテーブルの行に追加され、新しい列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="0a6bd-105">**ColumnMapping**新しい列のプロパティが設定されます**MappingType.SimpleContent**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="0a6bd-106">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0a6bd-107">推論プロセスという名前のテーブルが生成されます**Element1** 2 つの列を含む: **attr1**と**Element1_Text**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="0a6bd-108">**ColumnMapping**のプロパティ、 **attr1**列に設定されます**MappingType.Attribute**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="0a6bd-109">**ColumnMapping**のプロパティ、 **Element1_Text**列に設定されます**MappingType.SimpleContent**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="0a6bd-110">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a6bd-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a6bd-111">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a6bd-112">attr1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-112">attr1</span></span>|<span data-ttu-id="0a6bd-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="0a6bd-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="0a6bd-114">value1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-114">value1</span></span>|<span data-ttu-id="0a6bd-115">Text1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-115">Text1</span></span>|  
  
 <span data-ttu-id="0a6bd-116">要素にテキストだけでなく、テキストを含む子の要素も含まれている場合は、その要素に含まれているテキストを格納するための列はテーブルに追加されません。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="0a6bd-117">要素に含まれるテキストは無視されますが、子の要素のテキストはテーブルの行に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="0a6bd-118">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="0a6bd-119">推論プロセスという名前のテーブルが生成されます**Element1**という 1 つの列を持つ**ChildElement1**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="0a6bd-120">テキスト、 **ChildElement1**要素は、テーブルの行に含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="0a6bd-121">その他のテキストは無視されます。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-121">The other text will be ignored.</span></span> <span data-ttu-id="0a6bd-122">**ColumnMapping**のプロパティ、 **ChildElement1**列に設定されます**MappingType.Element**です。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="0a6bd-123">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a6bd-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a6bd-124">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a6bd-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="0a6bd-126">Text2</span><span class="sxs-lookup"><span data-stu-id="0a6bd-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a6bd-127">参照</span><span class="sxs-lookup"><span data-stu-id="0a6bd-127">See Also</span></span>  
 [<span data-ttu-id="0a6bd-128">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="0a6bd-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="0a6bd-129">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="0a6bd-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="0a6bd-130">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="0a6bd-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="0a6bd-131">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="0a6bd-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="0a6bd-132">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="0a6bd-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="0a6bd-133">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="0a6bd-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
