---
title: "NodeLists および NamedNodeMaps の動的更新"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="ca7fd-102">NodeLists および NamedNodeMaps の動的更新</span><span class="sxs-lookup"><span data-stu-id="ca7fd-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="ca7fd-103">**XmlNodeList**と**XmlNamedNodeMap** XML ドキュメントがメモリに読み込まれますが変更されている、まだ、ノードのセットを含む、World Wide Web コンソーシアム (W3C) の状態をこれらのオブジェクト動的であるノードの必要性の設定が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="ca7fd-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="ca7fd-104">つまり、基になっているドキュメントが変更されたら、これら 2 つのオブジェクトも変更される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca7fd-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="ca7fd-105">したがってがある場合、 **XmlNodeList**特定の要素 (たとえば、要素 X) のすべての子要素を格納している、要素 X 下のドキュメントに要素 Q は、要素を追加します。**XmlNodeList**その新しい要素 Q をそのコレクションに追加された必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ca7fd-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="ca7fd-106">逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="ca7fd-106">The same is true in reverse.</span></span> <span data-ttu-id="ca7fd-107">ノードが追加された場合、 **XmlNodeList**、基になるドキュメントが同様に更新します。</span><span class="sxs-lookup"><span data-stu-id="ca7fd-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7fd-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca7fd-108">See Also</span></span>  
 [<span data-ttu-id="ca7fd-109">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="ca7fd-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
