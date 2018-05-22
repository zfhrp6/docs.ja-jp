---
title: DOM のノード コンテンツの削除
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4acbdb53b20c10362385b468c2eb13ab9b17eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="7bf25-102">DOM のノード コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="7bf25-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="7bf25-103"><xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="7bf25-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="7bf25-104">コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="7bf25-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="7bf25-105">ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="7bf25-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="7bf25-106">ノードのコンテンツを変更する方法については、「[XML ドキュメントのノード、コンテンツ、値の変更](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bf25-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf25-107">参照</span><span class="sxs-lookup"><span data-stu-id="7bf25-107">See Also</span></span>  
 [<span data-ttu-id="7bf25-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="7bf25-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
