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
ms.workload: dotnet
ms.openlocfilehash: 3053d4e83233027f28357d8c45087df71c21ca18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inference-limitations"></a><span data-ttu-id="dabb8-102">推論の制限事項</span><span class="sxs-lookup"><span data-stu-id="dabb8-102">Inference Limitations</span></span>
<span data-ttu-id="dabb8-103">各ドキュメントに含まれている XML 要素によっては、XML から <xref:System.Data.DataSet> のスキーマを推論するプロセスにより、異なるスキーマが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dabb8-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="dabb8-104">たとえば、次のような XML ドキュメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="dabb8-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="dabb8-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="dabb8-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dabb8-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="dabb8-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="dabb8-107">推論プロセスによって生成される「document1"について、」、**データセット**"Element1"が繰り返し要素であるために、"DocumentElement"と"Element1、"という名前のテーブルをという名前です。</span><span class="sxs-lookup"><span data-stu-id="dabb8-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="dabb8-108">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dabb8-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="dabb8-109">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="dabb8-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="dabb8-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="dabb8-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="dabb8-111">Text1</span><span class="sxs-lookup"><span data-stu-id="dabb8-111">Text1</span></span>|  
|<span data-ttu-id="dabb8-112">Text2</span><span class="sxs-lookup"><span data-stu-id="dabb8-112">Text2</span></span>|  
  
 <span data-ttu-id="dabb8-113">ただし、"Document2、"用の推論プロセスによって生成される、**データセット**"NewDataSet"と"DocumentElement"という名前のテーブルの名前</span><span class="sxs-lookup"><span data-stu-id="dabb8-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="dabb8-114">この場合、属性も子要素も持たない "Element1" は列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="dabb8-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="dabb8-115">**データセット:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="dabb8-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="dabb8-116">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="dabb8-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="dabb8-117">Element1</span><span class="sxs-lookup"><span data-stu-id="dabb8-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="dabb8-118">Text1</span><span class="sxs-lookup"><span data-stu-id="dabb8-118">Text1</span></span>|  
  
 <span data-ttu-id="dabb8-119">これらの 2 つの XML ドキュメントは、同じスキーマを生成することを意図して記述されていますが、推論プロセスでは、各ドキュメントに含まれる要素を基にまったく異なるスキーマが生成されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="dabb8-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="dabb8-120">XML ドキュメントからスキーマを生成するときに発生する不整合を避けるためをお勧めの読み込み時に、XML スキーマ定義言語 (XSD) または Xml-data Reduced (XDR) を使用してスキーマを明示的に指定すること、**データセット**からXML です。</span><span class="sxs-lookup"><span data-stu-id="dabb8-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="dabb8-121">明示的な指定の詳細については、**データセット**スキーマと XML スキーマを参照してください[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。</span><span class="sxs-lookup"><span data-stu-id="dabb8-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabb8-122">参照</span><span class="sxs-lookup"><span data-stu-id="dabb8-122">See Also</span></span>  
 [<span data-ttu-id="dabb8-123">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="dabb8-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="dabb8-124">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="dabb8-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="dabb8-125">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="dabb8-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="dabb8-126">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="dabb8-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="dabb8-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="dabb8-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="dabb8-128">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="dabb8-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
