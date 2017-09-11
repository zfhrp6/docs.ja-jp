---
title: "LINQ to XML およびその他の XML テクノロジ3"
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
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
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
ms.openlocfilehash: fac7fc1d902352b02215e9156954a23b553e5049
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-vs-other-xml-technologies"></a><span data-ttu-id="b4181-102">LINQ to XML およびその他の XML テクノロジ</span><span class="sxs-lookup"><span data-stu-id="b4181-102">LINQ to XML vs. Other XML Technologies</span></span>
<span data-ttu-id="b4181-103">ここでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を他の XML テクノロジ (<xref:System.Xml.XmlReader>、XSLT、MSXML、および XmlLite) と比較します。</span><span class="sxs-lookup"><span data-stu-id="b4181-103">This topic compares [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to the following XML technologies: <xref:System.Xml.XmlReader>, XSLT, MSXML, and XmlLite.</span></span> <span data-ttu-id="b4181-104">使用するテクノロジを決定するときに、ここで説明する情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4181-104">This information can help you decide which technology to use.</span></span>  
  
 <span data-ttu-id="b4181-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] とドキュメント オブジェクト モデル (DOM) の比較については、「[LINQ to XML およびDOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4181-105">For a comparison of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to the Document Object Model (DOM), see [LINQ to XML vs. DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).</span></span>  
  
## <a name="linq-to-xml-vs-xmlreader"></a><span data-ttu-id="b4181-106">LINQ to XML およびXmlReader</span><span class="sxs-lookup"><span data-stu-id="b4181-106">LINQ to XML vs. XmlReader</span></span>  
 <span data-ttu-id="b4181-107"><xref:System.Xml.XmlReader> は、高速、前方参照専用、非キャッシュのパーサーです。</span><span class="sxs-lookup"><span data-stu-id="b4181-107"><xref:System.Xml.XmlReader> is a fast, forward-only, non-caching parser.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b4181-108"> は <xref:System.Xml.XmlReader> の上位に実装され、緊密に統合されています。</span><span class="sxs-lookup"><span data-stu-id="b4181-108"> is implemented on top of <xref:System.Xml.XmlReader>, and they are tightly integrated.</span></span> <span data-ttu-id="b4181-109">ただし、<xref:System.Xml.XmlReader> は単独で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b4181-109">However, you can also use <xref:System.Xml.XmlReader> by itself.</span></span>  
  
 <span data-ttu-id="b4181-110">たとえば、1 秒間に何百もの XML ドキュメントを解析する Web サービスを構築する際に、これらのドキュメントの構造が同じであるため、XML を解析するために実装するコードの作成が 1 つだけで済む場合は、</span><span class="sxs-lookup"><span data-stu-id="b4181-110">For example, suppose you are building a Web service that will parse hundreds of XML documents per second, and the documents have the same structure, meaning that you only have to write one implementation of the code to parse the XML.</span></span> <span data-ttu-id="b4181-111"><xref:System.Xml.XmlReader> を単独で使用することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="b4181-111">In this case, you would probably want to use <xref:System.Xml.XmlReader> by itself.</span></span>  
  
 <span data-ttu-id="b4181-112">一方、多数の小さい XML ドキュメントを解析するシステムを構築する際に、ドキュメントがそれぞれ異なる場合は、生産性の向上という観点から [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="b4181-112">In contrast, if you are building a system that parses many smaller XML documents, and each one is different, you would want to take advantage of the productivity improvements that [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides.</span></span>  
  
## <a name="linq-to-xml-vs-xslt"></a><span data-ttu-id="b4181-113">LINQ to XML およびXSLT</span><span class="sxs-lookup"><span data-stu-id="b4181-113">LINQ to XML vs. XSLT</span></span>  
 <span data-ttu-id="b4181-114">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] と XSLT は、どちらも広範な XML ドキュメント変換機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="b4181-114">Both [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and XSLT provide extensive XML document transformation capabilities.</span></span> <span data-ttu-id="b4181-115">XSLT は、ルール ベースの宣言型の方法です。</span><span class="sxs-lookup"><span data-stu-id="b4181-115">XSLT is a rule-based, declarative approach.</span></span> <span data-ttu-id="b4181-116">高度な XSLT プログラミングでは、ステートレスな方法が重視される関数型のプログラミング スタイルで XSLT を記述します。</span><span class="sxs-lookup"><span data-stu-id="b4181-116">Advanced XSLT programmers write XSLT in a functional programming style that emphasizes a stateless approach.</span></span> <span data-ttu-id="b4181-117">変換は、副作用なしで実装される純粋関数を使用して記述できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-117">Transformations can be written using pure functions that are implemented without side effects.</span></span> <span data-ttu-id="b4181-118">このルール ベース (関数型) の方法に精通している開発者は多くありません。また、修得するのは難しく、相当の学習時間を要する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b4181-118">This rule-based or functional approach is unfamiliar to many developers, and can be difficult and time-consuming to learn.</span></span>  
  
 <span data-ttu-id="b4181-119">XSLT は、パフォーマンスの高いアプリケーションを生成する、生産性の高いシステムとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-119">XSLT can be a very productive system that yields high-performance applications.</span></span> <span data-ttu-id="b4181-120">たとえば、Web 関連の大企業の中には、さまざまなデータ ソースを基に取得した XML から HTML を生成するための手段として XSLT を使用している企業もあります。</span><span class="sxs-lookup"><span data-stu-id="b4181-120">For example, some big Web companies use XSLT as a way to generate HTML from XML that has been pulled from a variety of data stores.</span></span> <span data-ttu-id="b4181-121">XSLT を CLR コードにコンパイルするマネージ XSLT エンジンは、一部のシナリオではネイティブ XSLT エンジンより高いパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="b4181-121">The managed XSLT engine compiles XSLT to CLR code, and performs even better in some scenarios than the native XSLT engine.</span></span>  
  
 <span data-ttu-id="b4181-122">ただし、XSLT では、多くの開発者が持っている C# や Visual Basic の知識は活かされません。</span><span class="sxs-lookup"><span data-stu-id="b4181-122">However, XSLT does not take advantage of the C# and Visual Basic knowledge that many developers have.</span></span> <span data-ttu-id="b4181-123">開発者は、別の複雑なプログラミング言語でコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4181-123">It requires developers to write code in a different and complex programming language.</span></span> <span data-ttu-id="b4181-124">C# (または Visual Basic) と XSLT など、統合されていない 2 つの開発システムを使用すると、ソフトウェア システムの開発や保守が困難になります。</span><span class="sxs-lookup"><span data-stu-id="b4181-124">Using two non-integrated development systems such as C# (or Visual Basic) and XSLT results in software systems that are more difficult to develop and maintain.</span></span>  
  
 <span data-ttu-id="b4181-125">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の変換は、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のクエリ式を修得すれば、使いやすいテクノロジとして威力を発揮します。</span><span class="sxs-lookup"><span data-stu-id="b4181-125">After you have mastered [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query expressions, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] transformations are a powerful technology that is easy to use.</span></span> <span data-ttu-id="b4181-126">基本的には、関数型構築を使用して、さまざまなソースからデータを取り込んで <xref:System.Xml.Linq.XElement> オブジェクトを動的に構築し、全体をまとめて新しい XML ツリーを作成することによって XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4181-126">Basically, you form your XML document by using functional construction, pulling in data from various sources, constructing <xref:System.Xml.Linq.XElement> objects dynamically, and assembling the whole into a new XML tree.</span></span> <span data-ttu-id="b4181-127">変換では、まったく新しいドキュメントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-127">The transformation can generate a completely new document.</span></span> <span data-ttu-id="b4181-128">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用すると、変換を比較的簡単かつ直感的に構築でき、結果のコードも読みやすいものになります。</span><span class="sxs-lookup"><span data-stu-id="b4181-128">Constructing transformations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is relatively easy and intuitive, and the resulting code is readable.</span></span> <span data-ttu-id="b4181-129">このため、開発と保守のコストを削減できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-129">This reduces development and maintenance costs.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b4181-130"> は、XSLT に置き換わることを目的としていません。</span><span class="sxs-lookup"><span data-stu-id="b4181-130"> is not intended to replace XSLT.</span></span> <span data-ttu-id="b4181-131">複雑なドキュメント中心の XML 変換 (特に、ドキュメントの構造が明確に定義されていない場合) では、引き続き XSLT が最適なツールになります。</span><span class="sxs-lookup"><span data-stu-id="b4181-131">XSLT is still the tool of choice for complicated and document-centric XML transformations, especially if the structure of the document is not well defined.</span></span>  
  
 <span data-ttu-id="b4181-132">XSLT には、W3C (World Wide Web Consortium) 標準という利点があります。</span><span class="sxs-lookup"><span data-stu-id="b4181-132">XSLT has the advantage of being a World Wide Web Consortium (W3C) standard.</span></span> <span data-ttu-id="b4181-133">標準となっている技術を使用するだけで十分な場合は、XSLT の方が適切といえます。</span><span class="sxs-lookup"><span data-stu-id="b4181-133">If you have a requirement that you use only technologies that are standards, XSLT might be more appropriate.</span></span>  
  
 <span data-ttu-id="b4181-134">XSLT は XML であるため、プログラムで操作できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-134">XSLT is XML, and therefore can be programmatically manipulated.</span></span>  
  
## <a name="linq-to-xml-vs-msxml"></a><span data-ttu-id="b4181-135">LINQ to XML およびMSXML</span><span class="sxs-lookup"><span data-stu-id="b4181-135">LINQ to XML vs. MSXML</span></span>  
 <span data-ttu-id="b4181-136">MSXML は、Microsoft Windows に付属する、XML 処理のための COM ベース テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="b4181-136">MSXML is the COM-based technology for processing XML that is included with Microsoft Windows.</span></span> <span data-ttu-id="b4181-137">MSXML は DOM をネイティブで実装し、XPath と XSLT をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b4181-137">MSXML provides a native implementation of the DOM with support for XPath and XSLT.</span></span> <span data-ttu-id="b4181-138">MSXML には、非キャッシュの SAX2 イベントベース パーサーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="b4181-138">It also contains the SAX2 non-caching, event-based parser.</span></span>  
  
 <span data-ttu-id="b4181-139">MSXML はパフォーマンスが高く、セキュリティもほとんどのシナリオで既定で確保されます。また、Internet Explorer でアクセスできるため、AJAX スタイルのアプリケーションでクライアント側での XML の処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-139">MSXML performs well, is secure by default in most scenarios, and can be accessed in Internet Explorer for performing client-side XML processing in AJAX-style applications.</span></span> <span data-ttu-id="b4181-140">MSXML は、C++、JavaScript、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0 など、COM をサポートするすべてのプログラミング言語から使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4181-140">MSXML can be used from any programming language that supports COM, including C++, JavaScript, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0.</span></span>  
  
 <span data-ttu-id="b4181-141">ただし共通言語ランタイム (CLR) に基づくマネージ コードで使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b4181-141">MSXML is not recommended for use in managed code based on the common language runtime (CLR).</span></span>  
  
## <a name="linq-to-xml-vs-xmllite"></a><span data-ttu-id="b4181-142">LINQ to XML およびXmlLite</span><span class="sxs-lookup"><span data-stu-id="b4181-142">LINQ to XML vs. XmlLite</span></span>  
 <span data-ttu-id="b4181-143">XmlLite は、非キャッシュ、前方参照専用のプル パーサーで、</span><span class="sxs-lookup"><span data-stu-id="b4181-143">XmlLite is a non-caching, forward only, pull parser.</span></span> <span data-ttu-id="b4181-144">主に C++ で使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4181-144">Developers primarily use XmlLite with C++.</span></span> <span data-ttu-id="b4181-145">マネージ コードで使用することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b4181-145">It is not recommended for developers to use XmlLite with managed code.</span></span>  
  
 <span data-ttu-id="b4181-146">XmlLite の最大の利点は、ほとんどのシナリオで、軽量かつ高速で安全な XML パーサーとして利用できることです。</span><span class="sxs-lookup"><span data-stu-id="b4181-146">The main advantage of XmlLite is that it is a lightweight, fast XML parser that is secure in most scenarios.</span></span> <span data-ttu-id="b4181-147">XmlLite は脅威の対象となる要素がほとんどないため、</span><span class="sxs-lookup"><span data-stu-id="b4181-147">Its threat surface area is very small.</span></span> <span data-ttu-id="b4181-148">信頼されていないドキュメントを解析し、サービス拒否攻撃やデータ漏洩攻撃などからの保護が必要な場合は、優れた方法となります。</span><span class="sxs-lookup"><span data-stu-id="b4181-148">If you have to parse untrusted documents and you want to protect against attacks such as denial of service or exposure of data, XmlLite might be a good option.</span></span>  
  
 <span data-ttu-id="b4181-149">XmlLite は、[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] と統合されていません。</span><span class="sxs-lookup"><span data-stu-id="b4181-149">XmlLite is not integrated with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="b4181-150">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の利用動機となるプログラミングの生産性の向上はもたらされません。</span><span class="sxs-lookup"><span data-stu-id="b4181-150">It does not yield the programmer productivity improvements that are the motivating force behind [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4181-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4181-151">See Also</span></span>  
 [<span data-ttu-id="b4181-152">はじめに (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b4181-152">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

