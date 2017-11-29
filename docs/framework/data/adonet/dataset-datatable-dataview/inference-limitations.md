---
title: "推論の制限事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 98ea3d5fa4427b391ef06b3fc6ace9a05dfb819a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="inference-limitations"></a><span data-ttu-id="8c623-102">推論の制限事項</span><span class="sxs-lookup"><span data-stu-id="8c623-102">Inference Limitations</span></span>
<span data-ttu-id="8c623-103">各ドキュメントに含まれている XML 要素によっては、XML から <xref:System.Data.DataSet> のスキーマを推論するプロセスにより、異なるスキーマが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8c623-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="8c623-104">たとえば、次のような XML ドキュメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8c623-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="8c623-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="8c623-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8c623-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="8c623-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8c623-107">推論プロセスによって生成される「document1"について、」、**データセット**"Element1"が繰り返し要素であるために、"DocumentElement"と"Element1、"という名前のテーブルをという名前です。</span><span class="sxs-lookup"><span data-stu-id="8c623-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="8c623-108">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8c623-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8c623-109">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="8c623-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8c623-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="8c623-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="8c623-111">Text1</span><span class="sxs-lookup"><span data-stu-id="8c623-111">Text1</span></span>|  
|<span data-ttu-id="8c623-112">Text2</span><span class="sxs-lookup"><span data-stu-id="8c623-112">Text2</span></span>|  
  
 <span data-ttu-id="8c623-113">ただし、"Document2、"用の推論プロセスによって生成される、**データセット**"NewDataSet"と"DocumentElement"という名前のテーブルの名前</span><span class="sxs-lookup"><span data-stu-id="8c623-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="8c623-114">この場合、属性も子要素も持たない "Element1" は列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="8c623-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="8c623-115">**データセット:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="8c623-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="8c623-116">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8c623-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="8c623-117">Element1</span><span class="sxs-lookup"><span data-stu-id="8c623-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="8c623-118">Text1</span><span class="sxs-lookup"><span data-stu-id="8c623-118">Text1</span></span>|  
  
 <span data-ttu-id="8c623-119">これらの 2 つの XML ドキュメントは、同じスキーマを生成することを意図して記述されていますが、推論プロセスでは、各ドキュメントに含まれる要素を基にまったく異なるスキーマが生成されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="8c623-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="8c623-120">XML ドキュメントからスキーマを生成するときに発生する不整合を避けるためをお勧めの読み込み時に、XML スキーマ定義言語 (XSD) または Xml-data Reduced (XDR) を使用してスキーマを明示的に指定すること、**データセット**からXML です。</span><span class="sxs-lookup"><span data-stu-id="8c623-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="8c623-121">明示的な指定の詳細については、**データセット**スキーマと XML スキーマを参照してください[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c623-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c623-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c623-122">See Also</span></span>  
 [<span data-ttu-id="8c623-123">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="8c623-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="8c623-124">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="8c623-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="8c623-125">XML からの DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="8c623-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="8c623-126">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="8c623-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="8c623-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="8c623-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="8c623-128">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="8c623-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
