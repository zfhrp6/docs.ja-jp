---
title: Word 文書内のテキストの検索 (C#)
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: bd9f128fd50587b88fd899d0180e3d2ca8a8df6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333929"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="f74f9-102">Word 文書内のテキストの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="f74f9-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="f74f9-103">このトピックでは、以前のクエリを拡張して、ドキュメント内で特定の文字列の出現箇所をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f74f9-104">例</span><span class="sxs-lookup"><span data-stu-id="f74f9-104">Example</span></span>  
 <span data-ttu-id="f74f9-105">この例では、WordprocessingML ドキュメントを処理して、ドキュメント内で特定のテキストの出現箇所をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-105">This example processes a WordprocessingML document, to find all the occurences of a specific piece of text in the document.</span></span> <span data-ttu-id="f74f9-106">ここではそのために、"Hello" という文字列を検索するクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="f74f9-107">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f74f9-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="f74f9-108">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="f74f9-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="f74f9-109">この例のソース ドキュメントを作成する方法の詳細については、「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f74f9-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="f74f9-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f74f9-111">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Following is the new query that retrieves all paragraphs  
        // that have specific text in them.  
        var helloParagraphs =  
            from para in paraWithText  
            where para.Text.Contains("Hello")  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in helloParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="f74f9-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f74f9-112">This example produces the following output:</span></span>  
  
```  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="f74f9-113">この検索に変更を加えて、特定のスタイルの行を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="f74f9-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="f74f9-114">次のクエリは、Code スタイルの空白行をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-114">The following query finds all blank lines that have the Code style:</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Retrieve all paragraphs that have no text and are styled Code.  
        var blankCodeParagraphs =  
            from para in paraWithText  
            where para.Text == "" && para.StyleName == "Code"  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in blankCodeParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="f74f9-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f74f9-115">This example produces the following output:</span></span>  
  
```  
StyleName:Code ><  
```  
  
 <span data-ttu-id="f74f9-116">この例はさまざまな形で強化できます。</span><span class="sxs-lookup"><span data-stu-id="f74f9-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="f74f9-117">たとえば、正規表現を使用してテキストを検索したり、特定のディレクトリにあるすべての Word ファイルを反復処理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f74f9-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="f74f9-118">この例は、1 つのクエリとして記述された場合とほぼ同程度のパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="f74f9-119">各クエリはレイジー遅延方式で実装されているため、反復処理されるまで結果は生成されません。</span><span class="sxs-lookup"><span data-stu-id="f74f9-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="f74f9-120">実行とレイジー評価について詳しくは、「[LINQ to XML における遅延実行とレイジー評価 (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f74f9-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f74f9-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="f74f9-121">Next Steps</span></span>  
 <span data-ttu-id="f74f9-122">次のセクションでは、WordprocessingML ドキュメントについて詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="f74f9-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
-   [<span data-ttu-id="f74f9-123">Office Open XML WordprocessingML ドキュメントの詳細 (C#)</span><span class="sxs-lookup"><span data-stu-id="f74f9-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)  
  
## <a name="see-also"></a><span data-ttu-id="f74f9-124">参照</span><span class="sxs-lookup"><span data-stu-id="f74f9-124">See Also</span></span>  
 [<span data-ttu-id="f74f9-125">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f74f9-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="f74f9-126">純粋関数によるリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="f74f9-126">Refactoring Using a Pure Function (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
 [<span data-ttu-id="f74f9-127">LINQ to XML における遅延実行とレイジー評価 (C#)</span><span class="sxs-lookup"><span data-stu-id="f74f9-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
