---
title: "XDocument クラスの概要 (C#)"
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
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
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
ms.openlocfilehash: 2e8513c8c969f7522866454838c6c08da528c1b6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="7c4b2-102">XDocument クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c4b2-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="7c4b2-103">このトピックでは、<xref:System.Xml.Linq.XDocument> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="7c4b2-104">XDocument クラスの概要</span><span class="sxs-lookup"><span data-stu-id="7c4b2-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="7c4b2-105"><xref:System.Xml.Linq.XDocument> クラスには、有効な XML ドキュメントに必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="7c4b2-106">これには、XML 宣言、処理命令、コメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="7c4b2-107"><xref:System.Xml.Linq.XDocument> クラスが提供する特定の機能が必要な場合は、<xref:System.Xml.Linq.XDocument> オブジェクトを作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="7c4b2-108">多くの場合、<xref:System.Xml.Linq.XElement> を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="7c4b2-109"><xref:System.Xml.Linq.XElement> を直接操作するのは、比較的単純なプログラミング モデルです。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="7c4b2-110"><xref:System.Xml.Linq.XDocument> は、<xref:System.Xml.Linq.XContainer> から派生します。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="7c4b2-111">したがって子ノードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="7c4b2-112">ただし、<xref:System.Xml.Linq.XDocument> オブジェクトに格納できる子 <xref:System.Xml.Linq.XElement> ノードは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="7c4b2-113">これは、XML ドキュメントにルート要素を 1 つしか持てないという XML 標準を反映しています。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="7c4b2-114">XDocument のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="7c4b2-114">Components of XDocument</span></span>  
 <span data-ttu-id="7c4b2-115"><xref:System.Xml.Linq.XDocument> には、次の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="7c4b2-116">1 つの <xref:System.Xml.Linq.XDeclaration> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="7c4b2-117"><xref:System.Xml.Linq.XDeclaration> では、XML 宣言の関連部分である XML バージョン、ドキュメントのエンコード、および XML ドキュメントがスタンドアロンかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="7c4b2-118">1 つの <xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="7c4b2-119">これは XML ドキュメントのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="7c4b2-120">任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="7c4b2-121">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="7c4b2-122">任意の数の <xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="7c4b2-123">コメントは、ルート要素の兄弟になります。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="7c4b2-124">XML ドキュメントをコメントで始めることは無効であるため、<xref:System.Xml.Linq.XComment> オブジェクトをリストの最初の引数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="7c4b2-125">DTD 用の 1 つの <xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="7c4b2-126"><xref:System.Xml.Linq.XDocument> をシリアル化すると、`XDocument.Declaration` が `null` である場合でも、作成者が `Writer.Settings.OmitXmlDeclaration` を `false` (既定値) に設定していれば、出力には XML 宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="7c4b2-127">既定では、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] によってバージョンが "1.0" に、エンコードが "utf-8" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="7c4b2-128">XDocument なしでの XElement の使用</span><span class="sxs-lookup"><span data-stu-id="7c4b2-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="7c4b2-129">既に説明したように、<xref:System.Xml.Linq.XElement> クラスは [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスのメイン クラスです。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="7c4b2-130">多くの場合、アプリケーションはドキュメントの作成を必要としません。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="7c4b2-131"><xref:System.Xml.Linq.XElement> クラスを使用することで、XML ツリーを作成し、そのツリーに他の XML ツリーを追加し、その XML ツリーを変更し、さらにそのツリーを保存できます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="7c4b2-132">XDocument の使用</span><span class="sxs-lookup"><span data-stu-id="7c4b2-132">Using XDocument</span></span>  
 <span data-ttu-id="7c4b2-133"><xref:System.Xml.Linq.XDocument> を構築するには、<xref:System.Xml.Linq.XElement> オブジェクトを構築する場合と同様に関数型構築を使用します。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="7c4b2-134">次のコードは、<xref:System.Xml.Linq.XDocument> オブジェクトおよび関連する格納されるオブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="7c4b2-135">ファイル test.xml を調べると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c4b2-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c4b2-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c4b2-136">See Also</span></span>  
 [<span data-ttu-id="7c4b2-137">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c4b2-137">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

