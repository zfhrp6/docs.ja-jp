---
title: メモリ内の XML データの処理
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 317021318153cc87b2eab3db508a9dede9dc05e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="1b383-102">メモリ内の XML データの処理</span><span class="sxs-lookup"><span data-stu-id="1b383-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="1b383-103">Microsoft .NET Framework には、XML データを処理するためのモデルとして、<xref:System.Xml.XmlDocument> クラス、<xref:System.Xml.XPath.XPathDocument> クラス、[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) の 3 つが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1b383-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="1b383-104"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core および DOM Level 2 Core を実装しています。</span><span class="sxs-lookup"><span data-stu-id="1b383-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="1b383-105">DOM は XML ドキュメントのメモリ内 (キャッシュ) ツリー表現です。</span><span class="sxs-lookup"><span data-stu-id="1b383-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="1b383-106"><xref:System.Xml.XmlDocument> およびその関連クラスを使用すると、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。</span><span class="sxs-lookup"><span data-stu-id="1b383-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="1b383-107"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づく、読み取り専用のメモリ内データ ストアです。</span><span class="sxs-lookup"><span data-stu-id="1b383-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="1b383-108"><xref:System.Xml.XPath.XPathNavigator> クラスは、読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラス内の XML ドキュメント全体にカーソル モデルを使用して、いくつかの編集オプションとナビゲーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="1b383-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="1b383-109">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) は、XML データの処理を目的とした Microsoft .NET Framework version 3.5 の新しいモデルです。</span><span class="sxs-lookup"><span data-stu-id="1b383-109">[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="1b383-110">[LINQ (統合言語クエリ)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) を活用するメモリ内モデルです。</span><span class="sxs-lookup"><span data-stu-id="1b383-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="1b383-111">LINQ では C# および Visual Basic の言語構文を拡張することで、新しいクエリ機能を実現しています。</span><span class="sxs-lookup"><span data-stu-id="1b383-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b383-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1b383-112">In This Section</span></span>  
 [<span data-ttu-id="1b383-113">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="1b383-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="1b383-114"><xref:System.Xml.XmlDocument> とその関連クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b383-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="1b383-115">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="1b383-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="1b383-116"><xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument>、および <xref:System.Xml.XPath.XPathNavigator> クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="1b383-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="1b383-117">LINQ to XML を使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="1b383-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="1b383-118">LINQ to XML の概要を簡単に説明し、LINQ to XML に関する参照先のリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="1b383-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b383-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b383-119">Related Sections</span></span>  
 [<span data-ttu-id="1b383-120">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="1b383-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
