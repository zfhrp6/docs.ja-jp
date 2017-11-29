---
title: "方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07fe45bb54c0d8b867cd3ae03fc3ed940243a538
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="3593a-102">方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)</span><span class="sxs-lookup"><span data-stu-id="3593a-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="3593a-103">大きな XML ファイルを任意に読み取り、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3593a-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="3593a-104">大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="3593a-105">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3593a-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="3593a-106">これを実現する 1 つの選択肢として、<xref:System.Xml.XmlReader> を使用してアプリケーションを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="3593a-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3593a-107">ただし、場合によっては、XML ツリーに対してクエリを実行するとき、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] の使用が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="3593a-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="3593a-108">このような場合は、カスタムの軸メソッドを独自に記述します。</span><span class="sxs-lookup"><span data-stu-id="3593a-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="3593a-109">詳しくは、「[方法 : LINQ to XML 軸メソッドを記述する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3593a-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="3593a-110">独自の軸メソッドを記述するには、<xref:System.Xml.XmlReader> を使用して、対象となるノードの 1 つに到達するまでノードを読み取る小さなメソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="3593a-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="3593a-111">このメソッドから <xref:System.Xml.Linq.XNode.ReadFrom%2A> が呼び出され、これにより <xref:System.Xml.XmlReader> からデータが読み取られ、XML フラグメントがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="3593a-112">さらに、カスタムの軸メソッドを列挙するメソッドに対しては、`yield return` を使用して各フラグメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="3593a-113">これで、カスタムの軸メソッド上に LINQ クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3593a-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="3593a-114">ストリーミングの手法は、ソース ドキュメントを 1 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="3593a-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="3593a-115"><xref:System.Linq.Enumerable.OrderBy%2A> などの一部の標準クエリ演算子では、ソースが反復処理され、すべてのデータが収集され並べ替えられて、最終的にはシーケンス内の最初の項目が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="3593a-116">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、メモリ使用量を低く維持することができないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="3593a-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3593a-117">例</span><span class="sxs-lookup"><span data-stu-id="3593a-117">Example</span></span>  
 <span data-ttu-id="3593a-118">ストリーム出力は関心の高い問題となる場合があるため、例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="3593a-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="3593a-119">次の XML ドキュメントでは、カスタムの軸メソッドのコンシューマーが、各項目が属している顧客の名前も認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3593a-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="3593a-120">この例で採用している方法では、ヘッダー情報の監視と保存が行われ、その後でヘッダー情報と列挙される詳細情報の両方が含まれている小さな XML ツリーが構築されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="3593a-121">次に、軸メソッドによってこの新しい小さな XML ツリーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="3593a-122">これでクエリは、詳細情報だけでなくヘッダー情報にもアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3593a-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="3593a-123">この方法で使用されるメモリは少量です。</span><span class="sxs-lookup"><span data-stu-id="3593a-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="3593a-124">詳細な XML フラグメントが個々に生成されるときに、前のフラグメントへの参照は保持されず、そのフラグメントはガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="3593a-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="3593a-125">この手法を使用すると、存続期間の短いオブジェクトがヒープ上に多数作成されるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="3593a-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="3593a-126">次の例では、URI で指定されたファイルから XML フラグメントをストリーム出力する、カスタムの軸メソッドを実装して使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3593a-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="3593a-127">このカスタムの軸は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、上記の `Source.xml` ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="3593a-128">これは単純な実装です。</span><span class="sxs-lookup"><span data-stu-id="3593a-128">It is a simplistic implementation.</span></span> <span data-ttu-id="3593a-129">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="3593a-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="3593a-130">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3593a-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3593a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3593a-131">See Also</span></span>  
 [<span data-ttu-id="3593a-132">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="3593a-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
