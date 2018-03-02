---
title: "DOM を読み込むときの空白および有意の空白の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a16f90b6d48bc2ffabfd678722fa9b6e61328cd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="29090-102">DOM を読み込むときの空白および有意の空白の処理</span><span class="sxs-lookup"><span data-stu-id="29090-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="29090-103">ドキュメントを読み込むときには、空白を保持するオプションを設定して、ドキュメント ツリーに **XmlWhitespace** ノードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="29090-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="29090-104">空白ノードを作成するには、**PreserveWhitespace** プロパティを true に設定します。</span><span class="sxs-lookup"><span data-stu-id="29090-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="29090-105">このプロパティが既定の **false** に設定されている場合、空白ノードは作成されません。</span><span class="sxs-lookup"><span data-stu-id="29090-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="29090-106">**PreserveWhitespace** フラグの設定に関係なく、有意の空白ノードは常に保持され、そのデータを表す **XmlSignificantWhitespace** ノードが常にメモリ内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="29090-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="29090-107">ドキュメントがリーダーから読み込まれた場合は、**XmlTextReader** の **WhitespaceHandling** プロパティが **WhitespaceHandling.None** に設定されていない場合にのみ、**XmlDocument** クラスの **PreserveWhitespace** フラグ プロパティの設定が **XmlWhitespace** ノードの作成に影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="29090-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="29090-108">リーダーの **WhitespaceHandling** プロパティの値の方が **XmlDocument** のこのフラグの設定より優先されます。</span><span class="sxs-lookup"><span data-stu-id="29090-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="29090-109">**XmlSignificantWhitespace** の詳細については、「<xref:System.Xml.XmlSignificantWhitespace>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29090-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29090-110">参照</span><span class="sxs-lookup"><span data-stu-id="29090-110">See Also</span></span>  
 [<span data-ttu-id="29090-111">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="29090-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
