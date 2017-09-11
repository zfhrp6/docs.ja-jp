---
title: "XAttribute クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
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
ms.openlocfilehash: 741e73987a9339a320114d74187c0056c7150924
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="31352-102">XAttribute クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31352-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="31352-103">属性は、要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="31352-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="31352-104"><xref:System.Xml.Linq.XAttribute>クラスは XML 属性を表します</xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="31352-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="31352-105">概要</span><span class="sxs-lookup"><span data-stu-id="31352-105">Overview</span></span>  
 <span data-ttu-id="31352-106">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] での属性の操作は、要素の操作に似ています。</span><span class="sxs-lookup"><span data-stu-id="31352-106">Working with attributes in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is similar to working with elements.</span></span> <span data-ttu-id="31352-107">コンストラクターはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="31352-107">Their constructors are similar.</span></span> <span data-ttu-id="31352-108">それぞれのコレクションの取得に使用するメソッドもほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="31352-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="31352-109">A[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]属性のコレクションのクエリ式によく似た、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]要素のコレクションの式をクエリします。</span><span class="sxs-lookup"><span data-stu-id="31352-109">A [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="31352-110">属性が要素に追加された順序は保持されます。</span><span class="sxs-lookup"><span data-stu-id="31352-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="31352-111">つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="31352-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="31352-112">XAttribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="31352-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="31352-113">次のコンス トラクター、<xref:System.Xml.Linq.XAttribute>クラスは、最もよく使用するもの:</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31352-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="31352-114">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="31352-114">Constructor</span></span>|<span data-ttu-id="31352-115">説明</span><span class="sxs-lookup"><span data-stu-id="31352-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="31352-116">作成、<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="31352-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="31352-117">`name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="31352-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="31352-118">属性を持つ要素の作成</span><span class="sxs-lookup"><span data-stu-id="31352-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="31352-119">次のコードは、Visual Basic で XML リテラルを使用して、属性を含む要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="31352-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="31352-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31352-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="31352-121">属性の関数型構築</span><span class="sxs-lookup"><span data-stu-id="31352-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="31352-122">構築する<xref:System.Xml.Linq.XAttribute>の構築と共にインラインで<xref:System.Xml.Linq.XElement>オブジェクトを次のように:</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31352-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="31352-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31352-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="31352-124">属性はノードではない</span><span class="sxs-lookup"><span data-stu-id="31352-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="31352-125">属性と要素には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="31352-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="31352-126"><xref:System.Xml.Linq.XAttribute>オブジェクトは、XML ツリー内のノードではありません。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31352-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="31352-127">属性は、XML 要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="31352-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="31352-128">ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。</span><span class="sxs-lookup"><span data-stu-id="31352-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="31352-129"><xref:System.Xml.Linq.XAttribute>オブジェクトが実際に、この XML ツリーの操作でノードではない<xref:System.Xml.Linq.XAttribute>オブジェクトは、操作に非常に似て<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="31352-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="31352-130">属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="31352-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="31352-131">多くの開発者は、この区別を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="31352-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31352-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="31352-132">See Also</span></span>  
 [<span data-ttu-id="31352-133">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31352-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
