---
title: Visual Basic の統合言語軸 (LINQ to XML)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8360281d1d8de0cad243297cd78e97958530bae4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="f81d4-102">Visual Basic の統合言語軸 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f81d4-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="f81d4-103">このセクションでは、XML にアクセスするが簡単に、Visual Basic 言語に直接組み込まれている機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f81d4-103">This section describes features built directly into the Visual Basic language to make it easy to access XML.</span></span> <span data-ttu-id="f81d4-104">例では、LINQ to XML のドキュメントの多くは、Visual Basic の統合軸を使用します。</span><span class="sxs-lookup"><span data-stu-id="f81d4-104">Many of the examples in the LINQ to XML documentation use these integrated Visual Basic axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f81d4-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f81d4-105">In This Section</span></span>  
  
|<span data-ttu-id="f81d4-106">トピック</span><span class="sxs-lookup"><span data-stu-id="f81d4-106">Topic</span></span>|<span data-ttu-id="f81d4-107">説明</span><span class="sxs-lookup"><span data-stu-id="f81d4-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f81d4-108">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="f81d4-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="f81d4-109"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、<xref:System.Xml.Linq.XElement> オブジェクトのコレクション、または <xref:System.Xml.Linq.XDocument> オブジェクトのコレクションのいずれかの子にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f81d4-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="f81d4-110">この軸は <xref:System.Xml.Linq.XContainer.Elements%2A> 軸に相当します。</span><span class="sxs-lookup"><span data-stu-id="f81d4-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="f81d4-111">XML 子孫軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="f81d4-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="f81d4-112"><xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、または <xref:System.Xml.Linq.XElement> オブジェクトのコレクションの子孫にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f81d4-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f81d4-113">この軸は <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸に相当します。</span><span class="sxs-lookup"><span data-stu-id="f81d4-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="f81d4-114">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="f81d4-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="f81d4-115"><xref:System.Xml.Linq.XElement> オブジェクトの属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f81d4-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="f81d4-116">この軸は <xref:System.Xml.Linq.XElement.Attribute%2A> 軸にほぼ相当します。</span><span class="sxs-lookup"><span data-stu-id="f81d4-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="f81d4-117">この軸は、<xref:System.Xml.Linq.XElement.Attribute%2A> オブジェクトではなく属性の値を返すという点で、<xref:System.Xml.Linq.XAttribute> 軸とは異なります。</span><span class="sxs-lookup"><span data-stu-id="f81d4-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="f81d4-118">拡張インデクサー プロパティ</span><span class="sxs-lookup"><span data-stu-id="f81d4-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="f81d4-119">コレクション内の個々の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f81d4-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f81d4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f81d4-120">See Also</span></span>  
 [<span data-ttu-id="f81d4-121">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f81d4-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
