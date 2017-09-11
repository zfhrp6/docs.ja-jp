---
title: "方法: 大きな XML ドキュメントのストリーミング変換を実行する (C#)"
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
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
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
ms.openlocfilehash: 952fad19f9abdea464e2763b721446ab5fe68301
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a><span data-ttu-id="df020-102">方法: 大きな XML ドキュメントのストリーミング変換を実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="df020-102">How to: Perform Streaming Transform of Large XML Documents (C#)</span></span>
<span data-ttu-id="df020-103">大きな XML ファイルを変換して、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="df020-103">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="df020-104">非常に大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="df020-104">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="df020-105">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df020-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="df020-106">ストリーミングの手法は、ソース ドキュメントを 1 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="df020-106">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="df020-107"><xref:System.Linq.Enumerable.OrderBy%2A> などの一部の標準クエリ演算子では、ソースが反復処理され、すべてのデータが収集され並べ替えられて、最終的にはシーケンス内の最初の項目が生成されます。</span><span class="sxs-lookup"><span data-stu-id="df020-107">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="df020-108">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、アプリケーションのメモリ使用量を低く維持することができないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="df020-108">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint for your application.</span></span>  
  
 <span data-ttu-id="df020-109">「[方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)」の手法を使用しても、変換されたドキュメントが含まれた XML ツリーをアセンブルしようとすると、メモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="df020-109">Even if you use the technique described in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>  
  
 <span data-ttu-id="df020-110">主な方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="df020-110">There are two main approaches.</span></span> <span data-ttu-id="df020-111">1 つは、<xref:System.Xml.Linq.XStreamingElement> の遅延処理の特性を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="df020-111">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="df020-112">もう 1 つは、<xref:System.Xml.XmlWriter> を作成し、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の機能を使用して <xref:System.Xml.XmlWriter> に要素を書き込む方法です。</span><span class="sxs-lookup"><span data-stu-id="df020-112">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="df020-113">このトピックでは、両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df020-113">This topic demonstrates both approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df020-114">例</span><span class="sxs-lookup"><span data-stu-id="df020-114">Example</span></span>  
 <span data-ttu-id="df020-115">「[方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)」の例を基に構築した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="df020-115">The following example builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="df020-116">この例では、<xref:System.Xml.Linq.XStreamingElement> の遅延実行機能を使用してストリーム出力しています。</span><span class="sxs-lookup"><span data-stu-id="df020-116">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="df020-117">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="df020-117">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="df020-118">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="df020-118">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="df020-119">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="df020-119">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="df020-120">ソース ドキュメント Source.xml を次に示します。</span><span class="sxs-lookup"><span data-stu-id="df020-120">The following is the source document, Source.xml:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 <span data-ttu-id="df020-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="df020-121">This code produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="df020-122">例</span><span class="sxs-lookup"><span data-stu-id="df020-122">Example</span></span>  
 <span data-ttu-id="df020-123">次の例も、「[方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)」の例を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="df020-123">The following example also builds on the example in [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).</span></span>  
  
 <span data-ttu-id="df020-124">この例では、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の機能を使用して <xref:System.Xml.XmlWriter> に要素を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="df020-124">This example uses the capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="df020-125">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="df020-125">This example can transform a very large document while maintaining a small memory footprint.</span></span>  
  
 <span data-ttu-id="df020-126">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="df020-126">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="df020-127">ただし、より堅牢に実装する場合は、ソース ドキュメントを XSD で検証するか、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="df020-127">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>  
  
 <span data-ttu-id="df020-128">この例でも、このトピックの前の例と同じソース ドキュメント Source.xml を使用します。</span><span class="sxs-lookup"><span data-stu-id="df020-128">This example uses the same source document, Source.xml, as the previous example in this topic.</span></span> <span data-ttu-id="df020-129">生成される出力も同じになります。</span><span class="sxs-lookup"><span data-stu-id="df020-129">It also produces exactly the same output.</span></span>  
  
 <span data-ttu-id="df020-130"><xref:System.Xml.Linq.XStreamingElement> に書き込むよりも、<xref:System.Xml.XmlWriter> を使用して出力 XML をストリーミングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="df020-130">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred over writing to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 <span data-ttu-id="df020-131">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="df020-131">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df020-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="df020-132">See Also</span></span>  
 [<span data-ttu-id="df020-133">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="df020-133">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

