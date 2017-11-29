---
title: "Visual Basic における LINQ to XML の概要"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: baa60939654857f40d323b6412978ed4ff918177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="cbd5a-102">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="cbd5a-102">Overview of LINQ to XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cbd5a-103">サポートを提供[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML リテラルと XML 軸プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-103"> provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="cbd5a-104">これにより、内の XML を操作するための使い慣れた便利な構文を使用して、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-104">This enables you to use a familiar, convenient syntax for working with XML in your [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span> <span data-ttu-id="cbd5a-105">*XML リテラル*コード内で直接、XML を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="cbd5a-106">*XML 軸プロパティ*access ノードが子、子孫ノード、および XML リテラルの属性を有効にします。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="cbd5a-107">詳細については、次を参照してください。 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-107">For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="cbd5a-108">メモリ内 XML プログラミング API を具体的に活用するために設計されています[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-108"> is an in-memory XML programming API designed specifically to take advantage of [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="cbd5a-109">呼び出すことができます、 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Api を直接のみ[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルを宣言および XML 軸のプロパティに直接アクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-109">Although you can call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs directly, only [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbd5a-110">ASP.NET ページ内の宣言型コードでは、XML リテラルおよび XML 軸プロパティがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="cbd5a-111">Visual Basic の XML の機能を使用するには、ASP.NET アプリケーションの分離コード ページで、コードを配置します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="cbd5a-112">![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")関連のビデオ デモンストレーションでは、次を参照してください。 [LINQ to XML による開始操作方法?](http://go.microsoft.com/fwlink/?LinkId=143034)と[方法 Excel スプレッドシートを作成する LINQ to XML を使用して?](http://go.microsoft.com/fwlink/?LinkId=143536)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For related video demonstrations, see [How Do I Get Started with LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) and [How Do I Create Excel Spreadsheets using LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).</span></span>  
  
## <a name="creating-xml"></a><span data-ttu-id="cbd5a-113">XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-113">Creating XML</span></span>  
 <span data-ttu-id="cbd5a-114">2 つの方法で XML ツリーを作成する[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-114">There are two ways to create XML trees in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="cbd5a-115">直接コードでは、リテラル XML を宣言することができますか、使用して、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ツリーを作成するための Api です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-115">You can declare an XML literal directly in code, or you can use the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs to create the tree.</span></span> <span data-ttu-id="cbd5a-116">両方のプロセスには、XML ツリーの最終構造を反映するようにコードが有効にします。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="cbd5a-117">たとえば、次のコード例では、XML 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 <span data-ttu-id="cbd5a-118">詳細については、次を参照してください。 [Visual Basic における XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-118">For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="cbd5a-119">アクセスして、XML を移動します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-119">Accessing and Navigating XML</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cbd5a-120">アクセスして XML 構造を移動するためには、XML 軸プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-120"> provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="cbd5a-121">これらのプロパティを使用すると、XML 子要素の名前を指定することによって XML 要素と属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="cbd5a-122">代わりに、明示的に呼び出すできます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]を移動して、要素と属性を検索するためのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-122">Alternatively, you can explicitly call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="cbd5a-123">たとえば、次のコード例は、属性および XML 要素の子要素を参照する XML 軸のプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="cbd5a-124">コード例では、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリに子要素を取得し、それらを効率的に変換を実行する、XML 要素として出力します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-124">The code example uses a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 <span data-ttu-id="cbd5a-125">詳細については、次を参照してください。 [Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-125">For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="cbd5a-126">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="cbd5a-126">XML Namespaces</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="cbd5a-127">使用してグローバル XML 名前空間のエイリアスを指定することができます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-127"> enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="cbd5a-128">次の例を使用する方法を示しています、 `Imports` XML 名前空間をインポートするステートメント。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 <span data-ttu-id="cbd5a-129">XML 軸プロパティにアクセスし、XML ドキュメントと xml 要素の XML リテラルを宣言するときに、XML 名前空間の別名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="cbd5a-130">取得することができます、<xref:System.Xml.Linq.XNamespace>を使用して特定の名前空間プレフィックスのオブジェクト、 [GetXmlNamespace 演算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="cbd5a-131">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-131">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="cbd5a-132">XML リテラルの XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="cbd5a-132">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="cbd5a-133">次の例を作成する方法を示しています、<xref:System.Xml.Linq.XElement>をグローバル名前空間を使用するオブジェクト`ns`:</span><span class="sxs-lookup"><span data-stu-id="cbd5a-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 <span data-ttu-id="cbd5a-134">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラがコードで XML 名前空間を使用するための XML 表記を使用する同等のコードに XML 名前空間エイリアスを含む XML リテラルに変換、`xmlns`属性。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-134">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="cbd5a-135">コンパイルすると、前のセクションの例のコードには、次の例として本質的に同じ実行可能コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="cbd5a-136">XML 軸のプロパティでの XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="cbd5a-136">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="cbd5a-137">XML リテラルで宣言されている XML 名前空間では、XML 軸のプロパティで使用するため使用できません。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="cbd5a-138">ただし、XML 軸プロパティを持つグローバル名前空間を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="cbd5a-139">コロンを使用して、ローカルの要素名から XML 名前空間プレフィックスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="cbd5a-140">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cbd5a-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cbd5a-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbd5a-141">See Also</span></span>  
 [<span data-ttu-id="cbd5a-142">XML</span><span class="sxs-lookup"><span data-stu-id="cbd5a-142">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="cbd5a-143">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="cbd5a-143">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="cbd5a-144">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="cbd5a-144">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="cbd5a-145">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="cbd5a-145">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
