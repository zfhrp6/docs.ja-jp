---
title: "既存のノードのコピー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11f3915dfebd7ad9d3144c9bedcd7f42b4754359
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="520ff-102">既存のノードのコピー</span><span class="sxs-lookup"><span data-stu-id="520ff-102">Copy Existing Nodes</span></span>
<span data-ttu-id="520ff-103">多くのメソッドとプロパティで、XML ドキュメント オブジェクト モデル (DOM) など、ノードの選択を行うこともできますが**SelectSingleNode**、 **ChildNodes [int i]**、**属性 [int i]**.</span><span class="sxs-lookup"><span data-stu-id="520ff-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="520ff-104">ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="520ff-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="520ff-105">ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。</span><span class="sxs-lookup"><span data-stu-id="520ff-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="520ff-106">既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。</span><span class="sxs-lookup"><span data-stu-id="520ff-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520ff-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="520ff-107">See Also</span></span>  
 [<span data-ttu-id="520ff-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="520ff-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
