---
title: "XDocument クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
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
ms.openlocfilehash: 3f51808a64d51fb354159df1a7323ad2fc26eedc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="b7f11-102">XDocument クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f11-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b7f11-103">このトピックに<xref:System.Xml.Linq.XDocument>クラス</xref:System.Xml.Linq.XDocument>が導入されています</span><span class="sxs-lookup"><span data-stu-id="b7f11-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="b7f11-104">XDocument クラスの概要</span><span class="sxs-lookup"><span data-stu-id="b7f11-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="b7f11-105"><xref:System.Xml.Linq.XDocument>クラスには、有効な XML ドキュメントに必要な情報が含まれています</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="b7f11-106">これには、XML 宣言、処理命令、コメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b7f11-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="b7f11-107"><xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument>クラス</xref:System.Xml.Linq.XDocument>によって提供される特定の機能を必要とする場合のオブジェクト</xref:System.Xml.Linq.XDocument>を作成する必要がだけに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b7f11-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="b7f11-108">多くの状況では、 <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="b7f11-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b7f11-109">直接操作<xref:System.Xml.Linq.XElement>は比較的単純なプログラミング モデル</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="b7f11-110"><xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>から派生します。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="b7f11-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="b7f11-111">したがって子ノードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b7f11-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="b7f11-112">ただし、<xref:System.Xml.Linq.XDocument>オブジェクトが&1; つだけの子を持つ<xref:System.Xml.Linq.XElement>ノード</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="b7f11-113">これは、XML ドキュメントにルート要素を&1; つしか持てないという XML 標準を反映しています。</span><span class="sxs-lookup"><span data-stu-id="b7f11-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="b7f11-114">XDocument のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="b7f11-114">Components of XDocument</span></span>  
 <span data-ttu-id="b7f11-115"><xref:System.Xml.Linq.XDocument>、次の要素を含めることができます:</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="b7f11-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="b7f11-116">1 つ<xref:System.Xml.Linq.XDeclaration>オブジェクト</xref:System.Xml.Linq.XDeclaration>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="b7f11-117"><xref:System.Xml.Linq.XDeclaration>XML 宣言の関連部分を指定することができます。 XML バージョン、ドキュメントのエンコードおよび XML ドキュメントがスタンドアロンかどうか。</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="b7f11-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="b7f11-118">1 つ<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b7f11-119">これは XML ドキュメントのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="b7f11-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="b7f11-120">任意の数の<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="b7f11-121">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="b7f11-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="b7f11-122">任意の数の<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="b7f11-123">コメントは、ルート要素の兄弟になります。</span><span class="sxs-lookup"><span data-stu-id="b7f11-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="b7f11-124"><xref:System.Xml.Linq.XComment>オブジェクトは、XML ドキュメントのコメントで始めることはできませんので、一覧の最初の引数にすることはできません</xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="b7f11-125">1 つ<xref:System.Xml.Linq.XDocumentType>DTD 用</xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="b7f11-126">シリアル化すると、<xref:System.Xml.Linq.XDocument>場合でも、`XDocument.Declaration`は`null`、ライターがある場合、出力は XML 宣言には`Writer.Settings.OmitXmlDeclaration`に設定`false`(既定値).</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="b7f11-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="b7f11-127">既定では、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] によってバージョンが "1.0" に、エンコードが "utf-8" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b7f11-127">By default, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="b7f11-128">XDocument なしでの XElement の使用</span><span class="sxs-lookup"><span data-stu-id="b7f11-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="b7f11-129">既に触れましたが、<xref:System.Xml.Linq.XElement>クラスが主なクラスで、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]プログラミング インターフェイスです</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface.</span></span> <span data-ttu-id="b7f11-130">多くの場合、アプリケーションはドキュメントの作成を必要としません。</span><span class="sxs-lookup"><span data-stu-id="b7f11-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="b7f11-131">使用して、<xref:System.Xml.Linq.XElement>クラス、XML ツリーを作成、他の XML ツリーを追加して、XML ツリーを変更および保存すればすべて</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b7f11-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="b7f11-132">XDocument の使用</span><span class="sxs-lookup"><span data-stu-id="b7f11-132">Using XDocument</span></span>  
 <span data-ttu-id="b7f11-133">構築する、 <xref:System.Xml.Linq.XDocument>、構築する場合と同じように、関数型構築を使用して<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b7f11-134">次のコード作成、<xref:System.Xml.Linq.XDocument>オブジェクトおよびそれに関連する格納されるオブジェクト</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="b7f11-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
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
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="b7f11-135">ファイル test.xml を調べると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b7f11-135">When you examine the file test.xml, you get the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7f11-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7f11-136">See Also</span></span>  
 [<span data-ttu-id="b7f11-137">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f11-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
