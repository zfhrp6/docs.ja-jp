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
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="782e2-102">DOM を読み込むときの空白および有意の空白の処理</span><span class="sxs-lookup"><span data-stu-id="782e2-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="782e2-103">ドキュメントを読み込む場合は、空白を保持し、作成するオプションを設定できます**XmlWhitespace**ドキュメント ツリーにおいてノード。</span><span class="sxs-lookup"><span data-stu-id="782e2-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="782e2-104">空白のノードを作成するには、設定、 **PreserveWhitespace**プロパティを true にします。</span><span class="sxs-lookup"><span data-stu-id="782e2-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="782e2-105">プロパティ設定されている場合**false**が既定値である空白ノードは作成されません。</span><span class="sxs-lookup"><span data-stu-id="782e2-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="782e2-106">有意の空白ノードは常に保持、および**XmlSignificantWhitespace**ノードは常にメモリの設定に関係なく、このデータを表すために作成、 **PreserveWhitespace**フラグです。</span><span class="sxs-lookup"><span data-stu-id="782e2-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="782e2-107">ドキュメントがリーダーから読み込まれている場合、設定、 **PreserveWhitespace**フラグ プロパティ、 **XmlDocument**クラスの作成に影響**XmlWhitespace**ノード場合にのみ、 **WhitespaceHandling**プロパティを**XmlTextReader**に設定されていない**WhitespaceHandling.None**です。</span><span class="sxs-lookup"><span data-stu-id="782e2-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="782e2-108">値では、 **WhitespaceHandling**プロパティでそのフラグの設定よりも優先するリーダーを**XmlDocument**です。</span><span class="sxs-lookup"><span data-stu-id="782e2-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="782e2-109">詳細については**XmlSignificantWhitespace**を参照してください<xref:System.Xml.XmlSignificantWhitespace>です。</span><span class="sxs-lookup"><span data-stu-id="782e2-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782e2-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="782e2-110">See Also</span></span>  
 [<span data-ttu-id="782e2-111">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="782e2-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
