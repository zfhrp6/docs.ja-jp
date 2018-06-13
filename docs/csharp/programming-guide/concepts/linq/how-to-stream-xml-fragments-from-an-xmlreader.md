---
title: '方法: XmlReader から XML フラグメントをストリーム出力する (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321065"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="33f6e-102">方法: XmlReader から XML フラグメントをストリーム出力する (C#)</span><span class="sxs-lookup"><span data-stu-id="33f6e-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="33f6e-103">大きな XML ファイルを処理する必要があるときに、XML ツリー全体をメモリに読み込むことができない場合があります。</span><span class="sxs-lookup"><span data-stu-id="33f6e-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="33f6e-104">このトピックでは、<xref:System.Xml.XmlReader> を使用してフラグメントをストリーム出力する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="33f6e-105"><xref:System.Xml.XmlReader> を使用して <xref:System.Xml.Linq.XElement> オブジェクトを読み取るための最も効果的な方法の 1 つは、カスタムの軸メソッドを独自に記述することです。</span><span class="sxs-lookup"><span data-stu-id="33f6e-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="33f6e-106">一般に軸メソッドは、このトピックの例で示すように、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> などのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="33f6e-107">カスタムの軸メソッドでは、<xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドを呼び出して XML フラグメントを作成した後に、`yield return` を使用してコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="33f6e-108">これにより、カスタムの軸メソッドに遅延実行セマンティクスが付加されます。</span><span class="sxs-lookup"><span data-stu-id="33f6e-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="33f6e-109"><xref:System.Xml.XmlReader> オブジェクトから XML ツリーを作成する場合は、<xref:System.Xml.XmlReader> を要素に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33f6e-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="33f6e-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> メソッドは、要素の終了タグを読み取るまで制御を戻しません。</span><span class="sxs-lookup"><span data-stu-id="33f6e-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="33f6e-111">部分ツリーを作成する場合は、<xref:System.Xml.XmlReader> をインスタンス化し、<xref:System.Xml.Linq.XElement> ツリーに変換するノード上にリーダーを配置し、<xref:System.Xml.Linq.XElement> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="33f6e-112">トピック「[方法: ヘッダー情報にアクセスして XML フラグメントをストリーム出力する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md)」には、より複雑なドキュメントをストリーム出力する方法とその例が示されています。</span><span class="sxs-lookup"><span data-stu-id="33f6e-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="33f6e-113">トピック「[方法: 大きな XML ドキュメントのストリーミング変換を実行する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md)」には、LINQ to XML を使って、メモリ使用量を低く抑えながら非常に大きな XML ドキュメントを変換する例が示されています。</span><span class="sxs-lookup"><span data-stu-id="33f6e-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33f6e-114">例</span><span class="sxs-lookup"><span data-stu-id="33f6e-114">Example</span></span>  
 <span data-ttu-id="33f6e-115">次の例では、カスタムの軸メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-115">This example creates a custom axis method.</span></span> <span data-ttu-id="33f6e-116">このメソッドに対してクエリを実行するには、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="33f6e-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="33f6e-117">カスタムの軸メソッド `StreamRootChildDoc` は、`Child` 要素が繰り返し出現するドキュメントを読み取るために特に設計されたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="33f6e-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="33f6e-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="33f6e-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="33f6e-119">この例のソース ドキュメントは、非常に小さなドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="33f6e-119">In this example, the source document is very small.</span></span> <span data-ttu-id="33f6e-120">ただし、何百万の `Child` 要素があっても、この例で使用されるメモリは非常に少量です。</span><span class="sxs-lookup"><span data-stu-id="33f6e-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f6e-121">参照</span><span class="sxs-lookup"><span data-stu-id="33f6e-121">See Also</span></span>  
 [<span data-ttu-id="33f6e-122">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="33f6e-122">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
