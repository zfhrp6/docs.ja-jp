---
title: "XPathDocument および XmlDocument を使用した XML データの読み取り"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 607d9d3616db0d0bd431fa2ca0b6aee03a85f896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="6f850-102">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="6f850-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="6f850-103"><xref:System.Xml.XPath?displayProperty=nameWithType> 名前空間で XML ドキュメントを読み取る方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="6f850-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6f850-104">1 つは読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスを使用して XML ドキュメントを読み取る方法で、もう 1 つは、<xref:System.Xml.XmlDocument> 名前空間で編集可能な <xref:System.Xml?displayProperty=nameWithType> クラスを使用して XML ドキュメントを読み取る方法です。</span><span class="sxs-lookup"><span data-stu-id="6f850-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="6f850-105">XPathDocument クラスを使用した XML ドキュメントの読み取り</span><span class="sxs-lookup"><span data-stu-id="6f850-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="6f850-106"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルによる XML ドキュメントの高速、読み取り専用のメモリ内表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="6f850-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="6f850-107"><xref:System.Xml.XPath.XPathDocument> クラスのインスタンスは、その 6 つのコンストラクターの 1 つを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="6f850-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="6f850-108">これらのコンストラクターでは、<xref:System.IO.Stream>、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> オブジェクトを使用して XML ドキュメントを読み取ることも、XML ファイルへの `string` パスを使用して XML ドキュメントを読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="6f850-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="6f850-109">以下は、<xref:System.Xml.XPath.XPathDocument> クラスの `string` コンストラクターを使用して XML ドキュメントを読み取る例です。</span><span class="sxs-lookup"><span data-stu-id="6f850-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="6f850-110">XmlDocument クラスを使用した XML ドキュメントの読み取り</span><span class="sxs-lookup"><span data-stu-id="6f850-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="6f850-111"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) の DOM Level 1 Core および DOM Level 2 Core を実装する XML ドキュメントの編集可能なメモリ内表現です。</span><span class="sxs-lookup"><span data-stu-id="6f850-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="6f850-112"><xref:System.Xml.XmlDocument> クラスのインスタンスは、その 3 つのコンストラクターの 1 つを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="6f850-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="6f850-113"><xref:System.Xml.XmlDocument> クラス コンストラクターをパラメーターなしで呼び出すことによって、新しい空の <xref:System.Xml.XmlDocument> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="6f850-114">コンストラクターの呼び出し後、<xref:System.Xml.XmlDocument.Load%2A> メソッドを使用するか、XML ファイルへの <xref:System.Xml.XmlDocument> パスを使用して、<xref:System.IO.Stream>、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> オブジェクトから新しい `string` オブジェクトに XML データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="6f850-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="6f850-115">以下は、パラメーターなしの <xref:System.Xml.XmlDocument> クラス コンストラクターと <xref:System.Xml.XmlDocument.Load%2A> メソッドを使用して XML ドキュメントを読み込む例です。</span><span class="sxs-lookup"><span data-stu-id="6f850-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="6f850-116">XML ドキュメントのエンコーディングの判定</span><span class="sxs-lookup"><span data-stu-id="6f850-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="6f850-117">前に示されているように、<xref:System.Xml.XmlReader> オブジェクトを使用して XML ドキュメントを読み取り、<xref:System.Xml.XPath.XPathDocument> および <xref:System.Xml.XmlDocument> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="6f850-118">ただし、<xref:System.Xml.XmlReader> オブジェクトは、エンコードされていないデータを読み取り、その結果、エンコード情報を提供しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f850-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="6f850-119"><xref:System.Xml.XmlTextReader> クラスは、<xref:System.Xml.XmlReader> クラスを継承し、その <xref:System.Xml.XmlTextReader.Encoding%2A> プロパティを使用してエンコード情報を提供します。また、このクラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクトの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="6f850-120"><xref:System.Xml.XmlTextReader> クラスよって提供されるエンコード情報に関する詳細については、<xref:System.Xml.XmlTextReader.Encoding%2A> クラスのリファレンス ドキュメントの「<xref:System.Xml.XmlTextReader>」プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f850-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="6f850-121">XPathNavigator オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="6f850-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="6f850-122"><xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクトのどちらからに XML ドキュメントを読み込んだ後、<xref:System.Xml.XPath.XPathNavigator> オブジェクト作成して、基になる XML データを選択、評価、移動、および (一部の状況で) 編集できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="6f850-123"><xref:System.Xml.XPath.XPathDocument> クラスに加えて、<xref:System.Xml.XmlDocument> および <xref:System.Xml.XmlNode> クラスは両方とも、<xref:System.Xml.XPath.IXPathNavigable> 名前空間の <xref:System.Xml.XPath?displayProperty=nameWithType> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="6f850-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6f850-124">結果として、3 つのクラスはすべて <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> オブジェクトを返す <xref:System.Xml.XPath.XPathNavigator> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6f850-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="6f850-125">XPathNavigator クラスによる XML ドキュメントの編集</span><span class="sxs-lookup"><span data-stu-id="6f850-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="6f850-126">XML データの選択、評価、および移動に加えて、<xref:System.Xml.XPath.XPathNavigator> クラスは、作成元のオブジェクトに基づき、一部の状況で XML ドキュメントの編集に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="6f850-127"><xref:System.Xml.XPath.XPathDocument> クラスは読み取り専用ですが、<xref:System.Xml.XmlDocument> クラスは編集可能です。その結果、<xref:System.Xml.XPath.XPathNavigator> オブジェクトから作成された <xref:System.Xml.XPath.XPathDocument> オブジェクトは XML ドキュメントの編集に使用できませんが、<xref:System.Xml.XmlDocument> オブジェクトから作成された場合は編集に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f850-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="6f850-128"><xref:System.Xml.XPath.XPathDocument> クラスは XML ドキュメントの読み取りだけに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f850-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="6f850-129">XML ドキュメントを編集する必要がある場合、またはイベント処理など <xref:System.Xml.XmlDocument> クラスによって提供される追加の機能が必要な場合は、<xref:System.Xml.XmlDocument> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f850-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="6f850-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> プロパテイは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが XML データを編集できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f850-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="6f850-131">各クラスの <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティ値についての説明を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6f850-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="6f850-132"><xref:System.Xml.XPath.IXPathNavigable> 実装</span><span class="sxs-lookup"><span data-stu-id="6f850-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="6f850-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 値</span><span class="sxs-lookup"><span data-stu-id="6f850-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="6f850-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f850-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="6f850-135">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="6f850-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="6f850-136">XPathNavigator による XML データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6f850-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="6f850-137">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="6f850-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="6f850-138">XPathNavigator を使用するスキーマの検証</span><span class="sxs-lookup"><span data-stu-id="6f850-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
