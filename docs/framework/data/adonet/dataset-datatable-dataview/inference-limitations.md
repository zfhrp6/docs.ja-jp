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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: af344055e511a2657007e216e1df304e2243362c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="inference-limitations"></a><span data-ttu-id="4722e-102">推論の制限事項</span><span class="sxs-lookup"><span data-stu-id="4722e-102">Inference Limitations</span></span>
<span data-ttu-id="4722e-103">各ドキュメントに含まれている XML 要素によっては、XML から <xref:System.Data.DataSet> のスキーマを推論するプロセスにより、異なるスキーマが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4722e-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="4722e-104">たとえば、次のような XML ドキュメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="4722e-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="4722e-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="4722e-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4722e-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="4722e-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4722e-107">推論プロセスによって生成される「document1"について、」、**データセット**"Element1"が繰り返し要素であるために、"DocumentElement"と"Element1、"という名前のテーブルをという名前です。</span><span class="sxs-lookup"><span data-stu-id="4722e-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="4722e-108">**データセット:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4722e-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4722e-109">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="4722e-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4722e-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="4722e-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="4722e-111">Text1</span><span class="sxs-lookup"><span data-stu-id="4722e-111">Text1</span></span>|  
|<span data-ttu-id="4722e-112">Text2</span><span class="sxs-lookup"><span data-stu-id="4722e-112">Text2</span></span>|  
  
 <span data-ttu-id="4722e-113">ただし、"Document2、"用の推論プロセスによって生成される、**データセット**"NewDataSet"と"DocumentElement"という名前のテーブルの名前</span><span class="sxs-lookup"><span data-stu-id="4722e-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="4722e-114">この場合、属性も子要素も持たない "Element1" は列として推論されます。</span><span class="sxs-lookup"><span data-stu-id="4722e-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="4722e-115">**データセット:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="4722e-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="4722e-116">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4722e-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="4722e-117">Element1</span><span class="sxs-lookup"><span data-stu-id="4722e-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="4722e-118">Text1</span><span class="sxs-lookup"><span data-stu-id="4722e-118">Text1</span></span>|  
  
 <span data-ttu-id="4722e-119">これらの 2 つの XML ドキュメントは、同じスキーマを生成することを意図して記述されていますが、推論プロセスでは、各ドキュメントに含まれる要素を基にまったく異なるスキーマが生成されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="4722e-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="4722e-120">XML ドキュメントからスキーマを生成するときに発生する不整合を避けるためをお勧めの読み込み時に、XML スキーマ定義言語 (XSD) または Xml-data Reduced (XDR) を使用してスキーマを明示的に指定すること、**データセット**からXML です。</span><span class="sxs-lookup"><span data-stu-id="4722e-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="4722e-121">明示的な指定の詳細については、**データセット**スキーマと XML スキーマを参照してください[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。</span><span class="sxs-lookup"><span data-stu-id="4722e-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4722e-122">参照</span><span class="sxs-lookup"><span data-stu-id="4722e-122">See Also</span></span>  
 [<span data-ttu-id="4722e-123">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="4722e-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="4722e-124">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="4722e-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="4722e-125">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="4722e-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="4722e-126">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="4722e-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="4722e-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="4722e-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="4722e-128">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="4722e-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
