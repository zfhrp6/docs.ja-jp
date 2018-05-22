---
title: 保持されるエンティティ参照
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 652a044bf1b5293bc9c36477a46a78d9851f1810
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="b818d-102">保持されるエンティティ参照</span><span class="sxs-lookup"><span data-stu-id="b818d-102">Entity References are Preserved</span></span>
<span data-ttu-id="b818d-103">エンティティ参照を展開せずに保持する場合、XML ドキュメント オブジェクト モデル (DOM) は、エンティティ参照を検出すると **XmlEntityReference** ノードを構築します。</span><span class="sxs-lookup"><span data-stu-id="b818d-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="b818d-104">たとえば、次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="b818d-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="b818d-105">DOM は、`&publisher;` 参照を検出すると **XmlEntityReference** ノードを構築します。</span><span class="sxs-lookup"><span data-stu-id="b818d-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="b818d-106">**XmlEntityReference** には、エンティティ宣言のコンテンツからコピーされた子ノードが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b818d-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="b818d-107">上記のコード サンプルでは、エンティティ宣言にテキストが含まれているため、エンティティ参照ノードの子ノードとして **XmlText** ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b818d-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="b818d-108">![保持されているエンティティ参照のツリー構造](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="b818d-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="b818d-109">エンティティ参照が保持される場合のツリー構造</span><span class="sxs-lookup"><span data-stu-id="b818d-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="b818d-110">**XmlEntityReference** の子ノードは、エンティティ宣言が検出されたときに **XmlEntity** ノードから作成されたすべての子ノードのコピーです。</span><span class="sxs-lookup"><span data-stu-id="b818d-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b818d-111">**XmlEntity** からコピーされたノードは、エンティティ参照ノードの下に配置されると、必ずしも元のノードの完全なコピーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="b818d-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="b818d-112">エンティティ参照ノードが現れた位置のスコープに名前空間が適用されていると、それが子ノードの最終的な構成に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b818d-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="b818d-113">既定では、`&abc;` のような一般エンティティは保持され、常に **XmlEntityReference** ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b818d-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b818d-114">参照</span><span class="sxs-lookup"><span data-stu-id="b818d-114">See Also</span></span>  
 [<span data-ttu-id="b818d-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="b818d-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
