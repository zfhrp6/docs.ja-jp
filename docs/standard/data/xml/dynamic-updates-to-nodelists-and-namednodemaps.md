---
title: NodeLists および NamedNodeMaps の動的更新
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568967"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="780cf-102">NodeLists および NamedNodeMaps の動的更新</span><span class="sxs-lookup"><span data-stu-id="780cf-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="780cf-103">**XmlNodeList** と **XmlNamedNodeMap** にはノード セットが格納されますが、XML ドキュメントはメモリに読み込まれ、変更されるため、W3C (World Wide Web Consortium) では、ノード セットが格納されるこれらのオブジェクトは動的でなければならないと規定しています。</span><span class="sxs-lookup"><span data-stu-id="780cf-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="780cf-104">つまり、基になっているドキュメントが変更されたら、これら 2 つのオブジェクトも変更される必要があります。</span><span class="sxs-lookup"><span data-stu-id="780cf-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="780cf-105">したがって、特定の要素 (たとえば要素 X) のすべての子要素が **XmlNodeList** に格納されている場合、別の要素である要素 Q は、要素 X の下のドキュメントに追加されます。**XmlNodeList** のコレクションにも、その新しい要素 Q を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="780cf-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="780cf-106">逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="780cf-106">The same is true in reverse.</span></span> <span data-ttu-id="780cf-107">**XmlNodeList** にノードが追加された場合は、基になっているドキュメントも同様に更新されます。</span><span class="sxs-lookup"><span data-stu-id="780cf-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780cf-108">参照</span><span class="sxs-lookup"><span data-stu-id="780cf-108">See Also</span></span>  
 [<span data-ttu-id="780cf-109">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="780cf-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
