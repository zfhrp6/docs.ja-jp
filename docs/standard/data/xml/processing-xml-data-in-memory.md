---
title: "メモリ内の XML データの処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec4ccbff095071b279e07cee6a1aab3ca830423f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="47ae6-102">メモリ内の XML データの処理</span><span class="sxs-lookup"><span data-stu-id="47ae6-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="47ae6-103">Microsoft .NET Framework には、XML データを処理するための 3 つのモデルが含まれています。<xref:System.Xml.XmlDocument>クラス、<xref:System.Xml.XPath.XPathDocument>クラス、および[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)です。</span><span class="sxs-lookup"><span data-stu-id="47ae6-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="47ae6-104"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core および DOM Level 2 Core を実装しています。</span><span class="sxs-lookup"><span data-stu-id="47ae6-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="47ae6-105">DOM は XML ドキュメントのメモリ内 (キャッシュ) ツリー表現です。</span><span class="sxs-lookup"><span data-stu-id="47ae6-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="47ae6-106"><xref:System.Xml.XmlDocument> およびその関連クラスを使用すると、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。</span><span class="sxs-lookup"><span data-stu-id="47ae6-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="47ae6-107"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づく、読み取り専用のメモリ内データ ストアです。</span><span class="sxs-lookup"><span data-stu-id="47ae6-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="47ae6-108"><xref:System.Xml.XPath.XPathNavigator> クラスは、読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラス内の XML ドキュメント全体にカーソル モデルを使用して、いくつかの編集オプションとナビゲーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="47ae6-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="47ae6-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) .NET Framework version 3.5 XML データを処理するために新しいモデルです。</span><span class="sxs-lookup"><span data-stu-id="47ae6-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="47ae6-110">利用する、インメモリ モデルである[クエリ (LINQ: Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)です。</span><span class="sxs-lookup"><span data-stu-id="47ae6-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="47ae6-111">LINQ では C# および Visual Basic の言語構文を拡張することで、新しいクエリ機能を実現しています。</span><span class="sxs-lookup"><span data-stu-id="47ae6-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47ae6-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="47ae6-112">In This Section</span></span>  
 [<span data-ttu-id="47ae6-113">DOM モデルを使用して XML データの処理</span><span class="sxs-lookup"><span data-stu-id="47ae6-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="47ae6-114"><xref:System.Xml.XmlDocument> とその関連クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="47ae6-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="47ae6-115">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="47ae6-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="47ae6-116"><xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument>、および <xref:System.Xml.XPath.XPathNavigator> クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="47ae6-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="47ae6-117">LINQ to XML を使用して XML データの処理</span><span class="sxs-lookup"><span data-stu-id="47ae6-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="47ae6-118">LINQ to XML の概要を簡単に説明し、LINQ to XML に関する参照先のリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="47ae6-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47ae6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="47ae6-119">Related Sections</span></span>  
 [<span data-ttu-id="47ae6-120">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="47ae6-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
