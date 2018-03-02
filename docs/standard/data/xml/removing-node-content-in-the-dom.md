---
title: "DOM のノード コンテンツの削除"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45a8d5006599b23165a174770f4d72974ea0e5ec
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="64261-102">DOM のノード コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="64261-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="64261-103"><xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="64261-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="64261-104">コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="64261-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="64261-105">ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="64261-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="64261-106">ノードのコンテンツを変更する方法については、「[XML ドキュメントのノード、コンテンツ、値の変更](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64261-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64261-107">参照</span><span class="sxs-lookup"><span data-stu-id="64261-107">See Also</span></span>  
 [<span data-ttu-id="64261-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="64261-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
