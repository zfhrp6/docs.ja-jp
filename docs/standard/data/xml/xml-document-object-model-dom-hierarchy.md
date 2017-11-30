---
title: "XML ドキュメント オブジェクト モデル (DOM) の階層構造"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="4c84e-102">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="4c84e-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="4c84e-103">XML ドキュメント オブジェクト モデル (DOM) のクラスの階層構造を次の図に示します。クラス名に続くかっこ内の名前は、W3C (World Wide Web Consortium) 名です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="4c84e-104">![XML ドキュメント オブジェクト モデル &#40;DOM&#41;階層](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="4c84e-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="4c84e-105">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="4c84e-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="4c84e-106">次のクラスを継承しない、 **XmlNode**:</span><span class="sxs-lookup"><span data-stu-id="4c84e-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="4c84e-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="4c84e-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="4c84e-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="4c84e-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="4c84e-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="4c84e-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="4c84e-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="4c84e-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="4c84e-111">**XmlImplementation**クラスは XML ドキュメントの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="4c84e-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="4c84e-112">詳細については、次を参照してください。 [XML ドキュメントの作成](../../../../docs/standard/data/xml/xml-document-creation.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="4c84e-113">**XmlNamedNodeMap**クラスは、順序付けられていないノードのセットを処理します。</span><span class="sxs-lookup"><span data-stu-id="4c84e-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="4c84e-114">詳細については、次を参照してください。[名前またはインデックスによる順序付けられていないノードの取得](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="4c84e-115">**XmlNodeList**クラスは、ノードの順序付きリストを処理します。</span><span class="sxs-lookup"><span data-stu-id="4c84e-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="4c84e-116">詳細については、次を参照してください。[インデックスによる順序付けられたノードの取得](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="4c84e-117">**XmlNodeChangedEventArgs**クラスに登録されたイベント ハンドラーの処理、 **XmlDocument**です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="4c84e-118">詳細については、次を参照してください。 [XmlNodeChangedEventArgs による XML ドキュメントでのイベント処理](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="4c84e-119">**XmlLinkedNode**クラスから継承**XmlNode**です。</span><span class="sxs-lookup"><span data-stu-id="4c84e-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="4c84e-120">その目的は、2 つのメソッドをオーバーライドする**XmlNode**: **PreviousSibling**と**NextSibling**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4c84e-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="4c84e-121">これらのオーバーライドされたメソッドは、によって継承および使用**XmlCharacterData**、 **XmlDeclaration**、 **XmlDocumentType**、 **XmlElement**、 **XmlEntityReference**、および**XmlProcessingInstruction**、これらは前または次の兄弟を持つクラス。</span><span class="sxs-lookup"><span data-stu-id="4c84e-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c84e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c84e-122">See Also</span></span>  
 [<span data-ttu-id="4c84e-123">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="4c84e-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
