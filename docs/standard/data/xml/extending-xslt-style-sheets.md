---
title: "XSLT スタイル シートの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8ccd1a95586bc92bcc712639eded135a69da1a36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="573f5-102">XSLT スタイル シートの拡張</span><span class="sxs-lookup"><span data-stu-id="573f5-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="573f5-103">このセクションでは、XSLT の機能を拡張するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="573f5-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="573f5-104">拡張オブジェクトまたはパラメーターは、<xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="573f5-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="573f5-105">その後、スタイル シートから拡張オブジェクトまたはパラメーターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="573f5-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="573f5-106">また、`msxsl:script` 要素を使用すると、スタイル シートにスクリプト ブロックを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="573f5-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="573f5-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="573f5-107">In This Section</span></span>  
 [<span data-ttu-id="573f5-108">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="573f5-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="573f5-109"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT 拡張オブジェクトを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="573f5-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="573f5-110">XSLT パラメーター</span><span class="sxs-lookup"><span data-stu-id="573f5-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="573f5-111"><xref:System.Xml.Xsl.XsltArgumentList> クラスを使用して XSLT パラメーターを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="573f5-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="573f5-112">スクリプト ブロックを使用して msxsl:script</span><span class="sxs-lookup"><span data-stu-id="573f5-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="573f5-113">`msxsl:script` 要素の使い方を説明します。</span><span class="sxs-lookup"><span data-stu-id="573f5-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="573f5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="573f5-114">Related Sections</span></span>  
 [<span data-ttu-id="573f5-115">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="573f5-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
