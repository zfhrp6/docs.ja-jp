---
title: "Visual Basic における LINQ to XML の概要 |Microsoft ドキュメント"
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
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cab0c219fe62064c62af4bd93e445107d73974db
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="32646-102">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="32646-102">Overview of LINQ to XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="32646-103">サポートを提供[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]XML リテラルと XML 軸プロパティです。</span><span class="sxs-lookup"><span data-stu-id="32646-103"> provides support for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="32646-104">これにより、内の XML を操作するための使い慣れた便利な構文を使用して、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。</span><span class="sxs-lookup"><span data-stu-id="32646-104">This enables you to use a familiar, convenient syntax for working with XML in your [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span> <span data-ttu-id="32646-105">*XML リテラル*XML をコード内で直接有効にします。</span><span class="sxs-lookup"><span data-stu-id="32646-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="32646-106">*XML 軸プロパティ*access 子ノードが、子孫ノードは、XML リテラルの属性に有効にします。</span><span class="sxs-lookup"><span data-stu-id="32646-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="32646-107">詳細については、次を参照してください。 [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)と[Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="32646-107">For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="32646-108">メモリ内 XML プログラミング API を利用するには、特別に設計された[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="32646-108"> is an in-memory XML programming API designed specifically to take advantage of [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].</span></span> <span data-ttu-id="32646-109">呼び出すことができますが、 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] Api を直接のみ[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルを宣言し、XML 軸プロパティに直接アクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="32646-109">Although you can call the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs directly, only [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32646-110">ASP.NET ページ内の宣言型コードでは、XML リテラルと XML 軸プロパティがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="32646-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="32646-111">Visual Basic の XML の機能を使用するには、コードを ASP.NET アプリケーションでは分離コード ページに配置します。</span><span class="sxs-lookup"><span data-stu-id="32646-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="32646-112">![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")関連のビデオ デモンストレーションでは、次を参照してください。 [LINQ to XML の使用方法ですか?](http://go.microsoft.com/fwlink/?LinkId=143034)と[LINQ to XML を使用して作成する Excel ワークシートの操作方法?](http://go.microsoft.com/fwlink/?LinkId=143536)します。</span><span class="sxs-lookup"><span data-stu-id="32646-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For related video demonstrations, see [How Do I Get Started with LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) and [How Do I Create Excel Spreadsheets using LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).</span></span>  
  
## <a name="creating-xml"></a><span data-ttu-id="32646-113">XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="32646-113">Creating XML</span></span>  
 <span data-ttu-id="32646-114">2 つの方法で XML ツリーを作成する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="32646-114">There are two ways to create XML trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="32646-115">直接コードでは、リテラル XML を宣言することができますか、使用して、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]ツリーを作成する Api。</span><span class="sxs-lookup"><span data-stu-id="32646-115">You can declare an XML literal directly in code, or you can use the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs to create the tree.</span></span> <span data-ttu-id="32646-116">両方のプロセスには、XML ツリーの最後の構造を反映するようにコードが有効にします。</span><span class="sxs-lookup"><span data-stu-id="32646-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="32646-117">たとえば、次のコード例では、XML 要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="32646-117">For example, the following code example creates an XML element:</span></span>  
  
 <span data-ttu-id="32646-118">[!code-vb[VbXmlSamples&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-118">[!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="32646-119">詳細については、次を参照してください。 [Visual Basic における XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="32646-119">For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="32646-120">アクセスして、XML 内の移動</span><span class="sxs-lookup"><span data-stu-id="32646-120">Accessing and Navigating XML</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="32646-121">アクセスと、XML 構造を移動するには、XML 軸プロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="32646-121"> provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="32646-122">これらのプロパティを使用すると、XML 子要素の名前を指定することによって XML 要素と属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="32646-122">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="32646-123">また、明示的に呼び出せる、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]内の移動および要素と属性を検索するためのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="32646-123">Alternatively, you can explicitly call the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="32646-124">たとえば、次のコード例は XML 軸プロパティを使用して、属性および XML 要素の子要素を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32646-124">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="32646-125">コード例では、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]子要素を取得し、それらを効率的に変換を実行する XML 要素として出力をクエリします。</span><span class="sxs-lookup"><span data-stu-id="32646-125">The code example uses a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 <span data-ttu-id="32646-126">[!code-vb[VbXmlSamples&#8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-126">[!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]</span></span>  
  
 <span data-ttu-id="32646-127">詳細については、次を参照してください。 [Visual Basic における XML のへのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="32646-127">For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="32646-128">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="32646-128">XML Namespaces</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="32646-129">使用してグローバル XML 名前空間のエイリアスを指定することができます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="32646-129"> enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="32646-130">次の例では、使用する方法、 `Imports` XML 名前空間をインポートするステートメント。</span><span class="sxs-lookup"><span data-stu-id="32646-130">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 <span data-ttu-id="32646-131">[!code-vb[VbXMLSamples&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-131">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]</span></span>  
  
 <span data-ttu-id="32646-132">XML 軸プロパティにアクセスし、XML ドキュメントと要素の XML リテラルを宣言する場合は、XML 名前空間の別名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="32646-132">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="32646-133">取得することができます、<xref:System.Xml.Linq.XNamespace>を使用して特定の名前空間プレフィックスのオブジェクト、 [GetXmlNamespace 演算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="32646-133">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="32646-134">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="32646-134">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="32646-135">XML リテラルでの XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="32646-135">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="32646-136">次の例では、作成する方法、<xref:System.Xml.Linq.XElement>グローバル名前空間を使用するオブジェクト`ns`:</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="32646-136">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 <span data-ttu-id="32646-137">[!code-vb[VbXMLSamples&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-137">[!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]</span></span>  
  
 <span data-ttu-id="32646-138">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラで XML 名前空間を使用するための XML 表記を使用する同等のコードを XML 名前空間エイリアスを含む XML リテラルを変換する、`xmlns`属性です。</span><span class="sxs-lookup"><span data-stu-id="32646-138">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="32646-139">コンパイルされると、前のセクションの例のコードには、次の例として本質的に同じ実行可能コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="32646-139">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 <span data-ttu-id="32646-140">[!code-vb[VbXMLSamples&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-140">[!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]</span></span>  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="32646-141">XML 軸プロパティ XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="32646-141">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="32646-142">XML リテラルで宣言されている XML 名前空間では、XML 軸プロパティで使用するため使用できません。</span><span class="sxs-lookup"><span data-stu-id="32646-142">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="32646-143">ただし、XML 軸プロパティを持つグローバル名前空間を使用できます。</span><span class="sxs-lookup"><span data-stu-id="32646-143">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="32646-144">コロンを使用して、ローカルの要素名からの XML 名前空間プレフィックスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="32646-144">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="32646-145">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="32646-145">Following is an example:</span></span>  
  
 <span data-ttu-id="32646-146">[!code-vb[VbXMLSamples&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="32646-146">[!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32646-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="32646-147">See Also</span></span>  
 <span data-ttu-id="32646-148">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="32646-148">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="32646-149"> [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="32646-149"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="32646-150"> [Visual Basic における XML へのアクセス](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span><span class="sxs-lookup"><span data-stu-id="32646-150"> [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span></span>  
<span data-ttu-id="32646-151"> [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="32646-151"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span></span>
