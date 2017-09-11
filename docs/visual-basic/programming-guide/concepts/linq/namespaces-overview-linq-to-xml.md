---
title: "名前空間の概要 (LINQ to XML) |Microsoft ドキュメント"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7e9536615871b83099a11e46125ed85b44d9335d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="441c9-102">名前空間の概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="441c9-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="441c9-103">このトピック<xref:System.Xml.Linq.XName>クラス、および<xref:System.Xml.Linq.XNamespace>クラス</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>の名前空間が導入されています</span><span class="sxs-lookup"><span data-stu-id="441c9-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="441c9-104">XML 名</span><span class="sxs-lookup"><span data-stu-id="441c9-104">XML Names</span></span>  
 <span data-ttu-id="441c9-105">XML 名は、多くの場合、XML プログラミングを複雑にしている原因です。</span><span class="sxs-lookup"><span data-stu-id="441c9-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="441c9-106">XML 名は、XML 名前空間 (XML 名前空間 URI) とローカル名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="441c9-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="441c9-107">XML 名前空間は、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] ベースのプログラムにおける名前空間と似ています。</span><span class="sxs-lookup"><span data-stu-id="441c9-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]-based program.</span></span> <span data-ttu-id="441c9-108">これを使用すると、要素と属性の名前を一意に修飾できます。</span><span class="sxs-lookup"><span data-stu-id="441c9-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="441c9-109">このため、XML ドキュメントのさまざまな部分の間で、名前の競合を回避するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="441c9-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="441c9-110">XML 名前空間を宣言した後は、その名前空間内でのみ一意であるローカル名を選択できます。</span><span class="sxs-lookup"><span data-stu-id="441c9-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="441c9-111">XML 名の別の要素が XML*名前空間プレフィックス*します。</span><span class="sxs-lookup"><span data-stu-id="441c9-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="441c9-112">XML プレフィックスは、XML 名の複雑さの主要な原因です。</span><span class="sxs-lookup"><span data-stu-id="441c9-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="441c9-113">このプレフィックスを使用すると、XML 名前空間に対するショートカットを作成できるため、XML ドキュメントがより簡潔でわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="441c9-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="441c9-114">ただし XML プレフィックスはコンテキストによって意味が異なり、これが複雑さの原因となります。</span><span class="sxs-lookup"><span data-stu-id="441c9-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="441c9-115">たとえば、XML プレフィックス `aw` に関連付けられている XML 名前空間が、同じ XML ツリー内でも部分によって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="441c9-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="441c9-116">使用する場合[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Visual Basic および XML リテラルと名前空間内のドキュメントを操作するときに、名前空間プレフィックスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="441c9-116">When using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="441c9-117">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、XML 名を表すクラスが<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="441c9-117">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="441c9-118">XML 名は、全体で頻繁に表示、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API、XML 名が必要な場所にして見つかります、<xref:System.Xml.Linq.XName>パラメーター</xref:System.Xml.Linq.XName> 。</span><span class="sxs-lookup"><span data-stu-id="441c9-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="441c9-119">ただし、ほとんどを使用する直接<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="441c9-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="441c9-120"><xref:System.Xml.Linq.XName>文字列からの暗黙的な変換が含まれています。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="441c9-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="441c9-121">詳細については、「 <xref:System.Xml.Linq.XNamespace> <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XNamespace>の使用」を参照していますください。</span><span class="sxs-lookup"><span data-stu-id="441c9-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441c9-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="441c9-122">See Also</span></span>  
 [<span data-ttu-id="441c9-123">XML 名前空間 (Visual Basic) の使用</span><span class="sxs-lookup"><span data-stu-id="441c9-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
