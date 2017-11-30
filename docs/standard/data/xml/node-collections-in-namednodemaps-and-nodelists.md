---
title: "NamedNodeMaps と NodeLists のノード コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7eeed46782eb6c55af23559035fb8b6bcb14301f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a><span data-ttu-id="c9c1f-102">NamedNodeMaps と NodeLists のノード コレクション</span><span class="sxs-lookup"><span data-stu-id="c9c1f-102">Node Collections in NamedNodeMaps and NodeLists</span></span>
<span data-ttu-id="c9c1f-103">ノードのセットを取得し、順序付けられた、または順序付けられていないコレクションに格納できます。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-103">You can retrieve a set of nodes and put it in an ordered or unordered collection.</span></span> <span data-ttu-id="c9c1f-104">ノード セットが格納された順序付けられていないコレクションは、W3C (World Wide Web Consortium) では NamedNodeMap と呼ばれています。このタイプのコレクションからは、名前またはインデックスによってデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-104">When putting a set of nodes into an unordered collection, the set is called a NamedNodeMap by the World Wide Web Consortium (W3C); you can retrieve the data by name or index in this type of collection.</span></span> <span data-ttu-id="c9c1f-105">ノード セットが格納された順序付けられたコレクションは、W3C では NodeList と呼ばれています。このコレクションのデータは、0 から始まるインデックスによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-105">Putting a set of nodes in an ordered collection is called a NodeList by the W3C, and the data can be retrieved by a zero-based index.</span></span> <span data-ttu-id="c9c1f-106">NamedNodeMaps および NodeLists は、W3C で規定されています。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-106">NamedNodeMaps and NodeLists are described by the W3C.</span></span> <span data-ttu-id="c9c1f-107">Microsoft .NET Framework での namednodemap の実装は、 **XmlNamedNodeMap**、NodeList はによって実装されると、 **XmlNodeList**です。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-107">The implementations in the Microsoft .NET Framework for the NamedNodeMap is the **XmlNamedNodeMap**, and the NodeList is implemented by the **XmlNodeList**.</span></span>  
  
 <span data-ttu-id="c9c1f-108">順序付けられていないコレクションについては、次を参照してください。[名前またはインデックスによる順序付けられていないノードの取得](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-108">For information on the unordered collection, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span> <span data-ttu-id="c9c1f-109">順序付けられたコレクションについては、次を参照してください。[インデックスによる順序付けられたノードの取得](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9c1f-109">For information on the ordered collection, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c1f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9c1f-110">See Also</span></span>  
 [<span data-ttu-id="c9c1f-111">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="c9c1f-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
