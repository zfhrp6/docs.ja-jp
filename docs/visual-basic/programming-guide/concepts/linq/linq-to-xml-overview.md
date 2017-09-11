---
title: "LINQ to XML の概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
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
ms.openlocfilehash: 4732aaa64119ba98ab11205e8c93dd8d3eb62d4b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="b7e68-102">LINQ to XML の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7e68-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="b7e68-103">XML は、多くのコンテキストでデータを書式設定する方法として広く採用されてきました。</span><span class="sxs-lookup"><span data-stu-id="b7e68-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="b7e68-104">たとえば、Web、構成ファイル、Microsoft Office Word ファイル、データベースで XML が使用されています。</span><span class="sxs-lookup"><span data-stu-id="b7e68-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="b7e68-105"> は、XML によるプログラミングのために再設計された最新の方法です。</span><span class="sxs-lookup"><span data-stu-id="b7e68-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="b7e68-106">ドキュメント オブジェクト モデル (DOM) のメモリ内ドキュメント変更機能を備え、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリ式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b7e68-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query expressions.</span></span> <span data-ttu-id="b7e68-107">このクエリ式は、XPath と構文は異なりますが、機能が似ています。</span><span class="sxs-lookup"><span data-stu-id="b7e68-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="b7e68-108">LINQ to XML の開発者</span><span class="sxs-lookup"><span data-stu-id="b7e68-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="b7e68-109"> は、さまざまな開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b7e68-109"> targets a variety of developers.</span></span> <span data-ttu-id="b7e68-110">何らかの処理を行うだけの平均的な開発者にとっては、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] によって SQL と同じようにクエリを作成できるので、XML の操作がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="b7e68-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="b7e68-111">プログラマは、短時間の学習で簡潔かつ強力なクエリを、選択したプログラミング言語で記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b7e68-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="b7e68-112">熟練した開発者は、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用することで生産性を大きく高めることができます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-112">Professional developers can use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="b7e68-113">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用すると、より少ないコードで、表現性と簡潔性に優れた強力なコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-113">With [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="b7e68-114">また、同時に複数のデータ ドメインからクエリ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="b7e68-115">LINQ to XML とは</span><span class="sxs-lookup"><span data-stu-id="b7e68-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="b7e68-116"> は、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] プログラミング言語から XML を操作できるようにする、LINQ に対応したメモリ内 XML プログラミング インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b7e68-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="b7e68-117">XML ドキュメントをメモリに読み込むという点では、ドキュメント オブジェクト モデル (DOM) のようなです。</span><span class="sxs-lookup"><span data-stu-id="b7e68-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="b7e68-118">ドキュメントに対するクエリや変更を行うことができ、変更したドキュメントをファイルに保存したり、シリアル化してインターネット経由で送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="b7e68-119">ただし、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] DOM と異なります: 軽量である新しいオブジェクト モデルを提供し、容易に扱う、利用している言語機能の Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="b7e68-119">However, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="b7e68-120">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の最も重要な利点は、[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] と統合されていることです。</span><span class="sxs-lookup"><span data-stu-id="b7e68-120">The most important advantage of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is its integration with [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].</span></span> <span data-ttu-id="b7e68-121">この統合により、メモリ内の XML ドキュメントに対するクエリを記述して、要素および属性のコレクションを取得できます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="b7e68-122">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] のクエリ機能は、構文は異なりますが、XPath および XQuery と機能面で互換性があります。</span><span class="sxs-lookup"><span data-stu-id="b7e68-122">The query capability of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="b7e68-123">統合[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]Visual Basic より強力な型指定とコンパイル時チェック、およびデバッガー サポートの強化を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7e68-123">The integration of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="b7e68-124">別の利点[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]へのパラメーターとしてクエリ結果を使用する機能は、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XAttribute>オブジェクト コンス トラクターにより、XML ツリーを作成するための強力な方法です</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b7e68-124">Another advantage of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="b7e68-125">呼ばれるこのアプローチ*関数型構築*の形式で XML ツリーを簡単に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="b7e68-126">たとえば、注文書」の説明に従って、典型的な XML がある[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348)します。</span><span class="sxs-lookup"><span data-stu-id="b7e68-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="b7e68-127">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用することで、次のクエリを実行して購買発注書のすべての品目要素の部品番号属性を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-127">By using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="b7e68-128">もう&1; つの例として、金額が $100 を超える品目を部品番号順に並べた一覧が必要であるとします。</span><span class="sxs-lookup"><span data-stu-id="b7e68-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="b7e68-129">この情報を取得するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b7e68-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="b7e68-130">これらに加えて[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]機能、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] XML プログラミング インターフェイスを機能強化を提供します。</span><span class="sxs-lookup"><span data-stu-id="b7e68-130">In addition to these [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] capabilities, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="b7e68-131">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用すると、次のことを実行できます。</span><span class="sxs-lookup"><span data-stu-id="b7e68-131">Using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can:</span></span>  
  
-   <span data-ttu-id="b7e68-132">ファイルまたはストリームからの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="b7e68-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="b7e68-133">ファイルまたはストリームへの XML のシリアル化</span><span class="sxs-lookup"><span data-stu-id="b7e68-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="b7e68-134">関数型構築を使用した XML の新規作成</span><span class="sxs-lookup"><span data-stu-id="b7e68-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="b7e68-135">XPath に類似した軸を使用した XML に対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="b7e68-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="b7e68-136">などのメソッドを使用して、メモリ内の XML ツリーを操作<xref:System.Xml.Linq.XContainer.Add%2A>、 <xref:System.Xml.Linq.XNode.Remove%2A>、 <xref:System.Xml.Linq.XNode.ReplaceWith%2A>、 <xref:System.Xml.Linq.XElement.SetValue%2A>.</xref:System.Xml.Linq.XElement.SetValue%2A> </xref:System.Xml.Linq.XNode.ReplaceWith%2A> </xref:System.Xml.Linq.XNode.Remove%2A> </xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="b7e68-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="b7e68-137">XSD を使用した XML ツリーの検証</span><span class="sxs-lookup"><span data-stu-id="b7e68-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="b7e68-138">上記の機能を組み合わせて使用した XML ツリーの構造の変換</span><span class="sxs-lookup"><span data-stu-id="b7e68-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="b7e68-139">XML ツリーの作成</span><span class="sxs-lookup"><span data-stu-id="b7e68-139">Creating XML Trees</span></span>  
 <span data-ttu-id="b7e68-140">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] でのプログラミングで最も重要な利点の&1; つは、XML ツリーを簡単に作成できるという点です。</span><span class="sxs-lookup"><span data-stu-id="b7e68-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="b7e68-141">たとえば、小さな XML ツリーを作成するにすることができますように記述コード。</span><span class="sxs-lookup"><span data-stu-id="b7e68-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 <span data-ttu-id="b7e68-142">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラに XML リテラルを変換する[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]メソッドの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="b7e68-142">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler translates XML literals into [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] method calls.</span></span>  
  
 <span data-ttu-id="b7e68-143">詳細については、次を参照してください。 [XML ツリーを作成する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)します。</span><span class="sxs-lookup"><span data-stu-id="b7e68-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e68-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7e68-144">See Also</span></span>  
 <span data-ttu-id="b7e68-145"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="b7e68-145"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="b7e68-146"> [はじめに (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b7e68-146"> [Getting Started (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md) </span></span>  
<span data-ttu-id="b7e68-147"> [Visual Basic における LINQ to XML の概要](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b7e68-147"> [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md) </span></span>  
<span data-ttu-id="b7e68-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="b7e68-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
