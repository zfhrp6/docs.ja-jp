---
title: XAttribute クラスの概要 (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: e0020a8cd8841ef9a35781b534c82db5e15c257f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324419"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="cc827-102">XAttribute クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="cc827-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="cc827-103">属性は、要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="cc827-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="cc827-104"><xref:System.Xml.Linq.XAttribute> クラスは、XML 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="cc827-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cc827-105">概要</span><span class="sxs-lookup"><span data-stu-id="cc827-105">Overview</span></span>  
 <span data-ttu-id="cc827-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] での属性の操作は、要素の操作に似ています。</span><span class="sxs-lookup"><span data-stu-id="cc827-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="cc827-107">コンストラクターはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="cc827-107">Their constructors are similar.</span></span> <span data-ttu-id="cc827-108">それぞれのコレクションの取得に使用するメソッドもほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="cc827-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="cc827-109">属性のコレクションの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式は、要素のコレクションの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="cc827-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="cc827-110">属性が要素に追加された順序は保持されます。</span><span class="sxs-lookup"><span data-stu-id="cc827-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="cc827-111">つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc827-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="cc827-112">XAttribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="cc827-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="cc827-113">最もよく使用する <xref:System.Xml.Linq.XAttribute> クラスのコンストラクターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc827-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="cc827-114">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="cc827-114">Constructor</span></span>|<span data-ttu-id="cc827-115">説明</span><span class="sxs-lookup"><span data-stu-id="cc827-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="cc827-116">
          <xref:System.Xml.Linq.XAttribute> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="cc827-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="cc827-117">`name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc827-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="cc827-118">属性を持つ要素の作成</span><span class="sxs-lookup"><span data-stu-id="cc827-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="cc827-119">次のコードは、属性を含む要素を作成する一般的なタスクを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc827-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="cc827-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cc827-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="cc827-121">属性の関数型構築</span><span class="sxs-lookup"><span data-stu-id="cc827-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="cc827-122"><xref:System.Xml.Linq.XAttribute> オブジェクトは、<xref:System.Xml.Linq.XElement> オブジェクトの構築と共にインラインで構築できます。</span><span class="sxs-lookup"><span data-stu-id="cc827-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="cc827-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cc827-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="cc827-124">属性はノードではない</span><span class="sxs-lookup"><span data-stu-id="cc827-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="cc827-125">属性と要素には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="cc827-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="cc827-126"><xref:System.Xml.Linq.XAttribute> オブジェクトは、XML ツリーのノードではありません。</span><span class="sxs-lookup"><span data-stu-id="cc827-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="cc827-127">属性は、XML 要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="cc827-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="cc827-128">ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。</span><span class="sxs-lookup"><span data-stu-id="cc827-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="cc827-129"><xref:System.Xml.Linq.XAttribute> オブジェクトは実際には XML ツリーのノードではありませんが、<xref:System.Xml.Linq.XAttribute> オブジェクトの操作は <xref:System.Xml.Linq.XElement> オブジェクトの操作とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="cc827-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cc827-130">属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="cc827-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="cc827-131">多くの開発者は、この区別を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cc827-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc827-132">参照</span><span class="sxs-lookup"><span data-stu-id="cc827-132">See Also</span></span>  
 [<span data-ttu-id="cc827-133">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="cc827-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
