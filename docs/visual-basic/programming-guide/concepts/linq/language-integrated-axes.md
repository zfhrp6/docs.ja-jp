---
title: "Visual Basic (LINQ to XML) での統合言語軸 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7ca88aed0772f4fb93ab561af4bd9a1129cbf3c5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="e2b09-102">Visual Basic の統合言語軸 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e2b09-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="e2b09-103">ここに直接組み込まれている機能について説明します[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]言語 XML にアクセスするが簡単にします。</span><span class="sxs-lookup"><span data-stu-id="e2b09-103">This section describes features built directly into the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="e2b09-104">LINQ to XML のドキュメントに記載されている多くの例では、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 統合軸を使用しています。</span><span class="sxs-lookup"><span data-stu-id="e2b09-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2b09-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e2b09-105">In This Section</span></span>  
  
|<span data-ttu-id="e2b09-106">トピック</span><span class="sxs-lookup"><span data-stu-id="e2b09-106">Topic</span></span>|<span data-ttu-id="e2b09-107">説明</span><span class="sxs-lookup"><span data-stu-id="e2b09-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e2b09-108">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2b09-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="e2b09-109">次のいずれかの子にアクセス:<xref:System.Xml.Linq.XElement>オブジェクト、 <xref:System.Xml.Linq.XDocument>、オブジェクトのコレクション<xref:System.Xml.Linq.XElement>オブジェクト、または一連の<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="e2b09-110">この軸は、<xref:System.Xml.Linq.XContainer.Elements%2A>軸</xref:System.Xml.Linq.XContainer.Elements%2A>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="e2b09-111">XML 子孫軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2b09-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="e2b09-112">次の子孫へのアクセスを提供:<xref:System.Xml.Linq.XElement>オブジェクト、<xref:System.Xml.Linq.XDocument>オブジェクト、または一連の<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e2b09-113">この軸は、<xref:System.Xml.Linq.XContainer.Descendants%2A>軸</xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="e2b09-114">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2b09-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="e2b09-115">属性にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="e2b09-116">この軸はほぼ同じ、<xref:System.Xml.Linq.XElement.Attribute%2A>軸</xref:System.Xml.Linq.XElement.Attribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="e2b09-117">この軸とは異なります、<xref:System.Xml.Linq.XElement.Attribute%2A>しない属性の値が返されることで、軸、<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement.Attribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="e2b09-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="e2b09-118">拡張インデクサー プロパティ</span><span class="sxs-lookup"><span data-stu-id="e2b09-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="e2b09-119">コレクション内の個々の要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e2b09-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2b09-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2b09-120">See Also</span></span>  
 [<span data-ttu-id="e2b09-121">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2b09-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
