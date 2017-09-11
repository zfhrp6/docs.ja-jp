---
title: "LINQ to XML の概要 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e85e61b29b9a97469c84abba4e4149b1967e601f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="4a5c3-102">LINQ to XML の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="4a5c3-102">LINQ to XML Overview (C#)</span></span>
<span data-ttu-id="4a5c3-103">XML は、多くのコンテキストでデータを書式設定する方法として広く採用されてきました。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="4a5c3-104">たとえば、Web、構成ファイル、Microsoft Office Word ファイル、データベースで XML が使用されています。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4a5c3-105"> は、XML によるプログラミングのために再設計された最新の方法です。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="4a5c3-106">ドキュメント オブジェクト モデル (DOM) のメモリ内ドキュメント変更機能を備え、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="4a5c3-107">このクエリ式は、XPath と構文は異なりますが、機能が似ています。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="4a5c3-108">LINQ to XML の開発者</span><span class="sxs-lookup"><span data-stu-id="4a5c3-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4a5c3-109"> は、さまざまな開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-109"> targets a variety of developers.</span></span> <span data-ttu-id="4a5c3-110">何らかの処理を行うだけの平均的な開発者にとっては、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] によって SQL と同じようにクエリを作成できるので、XML の操作がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="4a5c3-111">プログラマは、短時間の学習で簡潔かつ強力なクエリを、選択したプログラミング言語で記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="4a5c3-112">熟練した開発者は、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用することで生産性を大きく高めることができます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="4a5c3-113">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用すると、より少ないコードで、表現性と簡潔性に優れた強力なコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="4a5c3-114">また、同時に複数のデータ ドメインからクエリ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="4a5c3-115">LINQ to XML とは</span><span class="sxs-lookup"><span data-stu-id="4a5c3-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4a5c3-116"> は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] プログラミング言語から XML を操作できるようにする、LINQ に対応したメモリ内 XML プログラミング インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="4a5c3-117"> は、XML ドキュメントをメモリに読み込むという点で、ドキュメント オブジェクト モデル (DOM) に似ています。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="4a5c3-118">ドキュメントに対するクエリや変更を行うことができ、変更したドキュメントをファイルに保存したり、シリアル化してインターネット経由で送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="4a5c3-119">ただし、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] が提供する新しいオブジェクト モデルは、より軽量で操作しやすく、C# の言語機能を利用している点で、DOM と異なります。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>  
  
 <span data-ttu-id="4a5c3-120">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の最も重要な利点は、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] と統合されていることです。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="4a5c3-121">この統合により、メモリ内の XML ドキュメントに対するクエリを記述して、要素および属性のコレクションを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="4a5c3-122">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のクエリ機能は、構文は異なりますが、XPath および XQuery と機能面で互換性があります。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="4a5c3-123">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] に C# が統合されていることで、厳密な型指定とコンパイル時のチェックが可能となり、デバッガー サポートが強化されます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="4a5c3-124">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のもう 1 つの利点は、クエリの結果を <xref:System.Xml.Linq.XElement> および <xref:System.Xml.Linq.XAttribute> オブジェクト コンストラクターに対するパラメーターとして使用できるので、XML ツリーを作成するための強力な方法が利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="4a5c3-125">*関数型構築*と呼ばれるこの方法では、開発者が XML ツリーの構造を簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="4a5c3-126">たとえば、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348)」で説明されているように、典型的な XML の購買発注書を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="4a5c3-127">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用することで、次のクエリを実行して購買発注書のすべての品目要素の部品番号属性を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 <span data-ttu-id="4a5c3-128">もう 1 つの例として、金額が $100 を超える品目を部品番号順に並べた一覧が必要であるとします。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="4a5c3-129">この情報を取得するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-129">To obtain this information, you could run the following query:</span></span>  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 <span data-ttu-id="4a5c3-130">これらの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 機能に加え、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では XML プログラミング インターフェイスが機能強化されています。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="4a5c3-131">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用すると、次のことを実行できます。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="4a5c3-132">ファイルまたはストリームからの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="4a5c3-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="4a5c3-133">ファイルまたはストリームへの XML のシリアル化</span><span class="sxs-lookup"><span data-stu-id="4a5c3-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="4a5c3-134">関数型構築を使用した XML の新規作成</span><span class="sxs-lookup"><span data-stu-id="4a5c3-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="4a5c3-135">XPath に類似した軸を使用した XML に対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="4a5c3-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="4a5c3-136"><xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、<xref:System.Xml.Linq.XElement.SetValue%2A> などのメソッドを使用した、メモリ内の XML ツリーの操作</span><span class="sxs-lookup"><span data-stu-id="4a5c3-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="4a5c3-137">XSD を使用した XML ツリーの検証</span><span class="sxs-lookup"><span data-stu-id="4a5c3-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="4a5c3-138">上記の機能を組み合わせて使用した XML ツリーの構造の変換</span><span class="sxs-lookup"><span data-stu-id="4a5c3-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="4a5c3-139">XML ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="4a5c3-139">Creating XML Trees</span></span>  
 <span data-ttu-id="4a5c3-140">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でのプログラミングで最も重要な利点の 1 つは、XML ツリーを簡単に作成できるという点です。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="4a5c3-141">たとえば、小さな XML ツリーを作成するには、次のようにコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-141">For example, to create a small XML tree, you can write code as follows:</span></span>  
  
```csharp  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 <span data-ttu-id="4a5c3-142">詳しくは、「[XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4a5c3-142">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5c3-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a5c3-143">See Also</span></span>  
 <span data-ttu-id="4a5c3-144"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="4a5c3-144"><xref:System.Xml.Linq></span></span>   
 [<span data-ttu-id="4a5c3-145">はじめに (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4a5c3-145">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

