---
title: "保持されるエンティティ参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="49848-102">保持されるエンティティ参照</span><span class="sxs-lookup"><span data-stu-id="49848-102">Entity References are Preserved</span></span>
<span data-ttu-id="49848-103">エンティティ参照が展開せずに保持されます、XML ドキュメント オブジェクト モデル (DOM) をビルド、 **XmlEntityReference**ノード、エンティティ参照を検出するとします。</span><span class="sxs-lookup"><span data-stu-id="49848-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="49848-104">たとえば、次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="49848-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="49848-105">DOM のビルド、 **XmlEntityReference**ノードに到達したときに、`&publisher;`参照します。</span><span class="sxs-lookup"><span data-stu-id="49848-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="49848-106">**XmlEntityReference**エンティティ宣言のコンテンツからコピーされた子ノードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="49848-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="49848-107">ため、上記のコード例に、エンティティ宣言内のテキストが含まれています、 **XmlText**エンティティ参照ノードの子ノードとしてノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="49848-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="49848-108">![ツリー構造が保持されているエンティティ参照の](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="49848-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="49848-109">エンティティ参照が保持される場合のツリー構造</span><span class="sxs-lookup"><span data-stu-id="49848-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="49848-110">子ノード、 **XmlEntityReference**ノードから作成されたすべての子のコピーである、 **XmlEntity**ノード、エンティティ宣言が発生したとき。</span><span class="sxs-lookup"><span data-stu-id="49848-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49848-111">コピーされたノード、 **XmlEntity**常に、エンティティ参照ノードの下に配置される正確なコピーではありません。</span><span class="sxs-lookup"><span data-stu-id="49848-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="49848-112">エンティティ参照ノードが現れた位置のスコープに名前空間が適用されていると、それが子ノードの最終的な構成に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="49848-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="49848-113">既定では、一般エンティティと同様に`&abc;`は保持されますと**XmlEntityReference**ノードは常に作成します。</span><span class="sxs-lookup"><span data-stu-id="49848-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49848-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="49848-114">See Also</span></span>  
 [<span data-ttu-id="49848-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="49848-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
