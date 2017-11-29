---
title: "方法 : XML 子孫要素にアクセスする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="497bc-102">方法 : XML 子孫要素にアクセスする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="497bc-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="497bc-103">この例では、descendant 軸のプロパティを使用して、指定した名前を持ち、XML 要素に含まれるすべての XML 要素にアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="497bc-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="497bc-104">具体的を使用して、`Value`プロパティをコレクション内の最初の要素の値を取得、 `name` descendant 軸のプロパティを返します。</span><span class="sxs-lookup"><span data-stu-id="497bc-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="497bc-105">`name`子孫軸プロパティというすべての要素を取得する`name`に含まれる、`contacts`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="497bc-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="497bc-106">またこの例では、`phone`という名前のすべての子孫にアクセスする子孫軸プロパティ`phone`に含まれる、`contacts`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="497bc-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="497bc-107">例</span><span class="sxs-lookup"><span data-stu-id="497bc-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="497bc-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="497bc-108">Compiling the Code</span></span>  
 <span data-ttu-id="497bc-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="497bc-109">This example requires:</span></span>  
  
-   <span data-ttu-id="497bc-110"><xref:System.Xml.Linq> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="497bc-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497bc-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="497bc-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="497bc-112">XML 子孫軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="497bc-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="497bc-113">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="497bc-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="497bc-114">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="497bc-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="497bc-115">XML</span><span class="sxs-lookup"><span data-stu-id="497bc-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
