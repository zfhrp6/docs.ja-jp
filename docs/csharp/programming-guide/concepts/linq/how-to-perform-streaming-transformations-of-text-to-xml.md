---
title: '方法: テキストから XML へのストリーミング変換を実行する (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 4313c5263b6a219ec3c8d05a7b7938c41c7cc028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328189"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="2baae-102">方法: テキストから XML へのストリーミング変換を実行する (C#)</span><span class="sxs-lookup"><span data-stu-id="2baae-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="2baae-103">テキスト ファイルを処理する方法の 1 つは、`yield return` 構造を使用して、テキスト ファイルを一度に 1 行ずつストリーム出力する拡張メソッドを記述することです。</span><span class="sxs-lookup"><span data-stu-id="2baae-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="2baae-104">その後、テキスト ファイルをレイジー遅延方式で処理する LINQ クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="2baae-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="2baae-105">次に <xref:System.Xml.Linq.XStreamingElement> を使用してストリーム出力すると、ソース テキスト ファイルのサイズにかかわらず、メモリを最小限しか使用しないテキスト ファイルから XML への変換を作成できます。</span><span class="sxs-lookup"><span data-stu-id="2baae-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="2baae-106">ストリーミング変換に関しては、いくつかの注意事項があります。</span><span class="sxs-lookup"><span data-stu-id="2baae-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="2baae-107">ストリーミング変換は、ファイル全体の処理を 1 回で行うことが可能で、かつソース ドキュメント内の順番どおりに行を処理できる場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="2baae-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="2baae-108">ファイルを 2 回以上処理する必要がある場合、または処理前に行を並べ替える必要がある場合は、ストリーミングの手法が持つ多くの利点を活かすことはできません。</span><span class="sxs-lookup"><span data-stu-id="2baae-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2baae-109">例</span><span class="sxs-lookup"><span data-stu-id="2baae-109">Example</span></span>  
 <span data-ttu-id="2baae-110">次のテキスト ファイル (People.txt) は、この例のソースです。</span><span class="sxs-lookup"><span data-stu-id="2baae-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="2baae-111">次のコードには、このテキスト ファイルの行を遅延方式でストリーム出力する拡張メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2baae-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 <span data-ttu-id="2baae-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2baae-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2baae-113">参照</span><span class="sxs-lookup"><span data-stu-id="2baae-113">See Also</span></span>  
 <xref:System.Xml.Linq.XStreamingElement>  
 [<span data-ttu-id="2baae-114">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2baae-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
