---
title: "段落のテキストの取得 (C#)"
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
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b0a6e842359ae42be9e00ba35f6878d3a2a4aac4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="3b43a-102">段落のテキストの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b43a-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="3b43a-103">この例は、前の例の「[段落とそのスタイルの取得 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)」を基にしています。</span><span class="sxs-lookup"><span data-stu-id="3b43a-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="3b43a-104">この新しい例では、各段落のテキストを文字列として取得します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="3b43a-105">テキストを取得するため、この例で追加するクエリでは、匿名型のコレクションを反復処理し、新しいメンバー `Text` を追加して匿名型の新しいコレクションを射影します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="3b43a-106">また、<xref:System.Linq.Enumerable.Aggregate%2A> 標準クエリ演算子を使用して、複数の文字列を 1 つの文字列に連結します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="3b43a-107">この手法 (まず匿名型のコレクションに射影した後、このコレクションを使用して匿名型の新しいコレクションに射影する) は、一般的で便利な表現形式です。</span><span class="sxs-lookup"><span data-stu-id="3b43a-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="3b43a-108">最初の匿名型に射影せずに、このクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3b43a-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="3b43a-109">また、レイジー評価のため、その射影を行うことによって追加使用される処理能力は大きくありません。</span><span class="sxs-lookup"><span data-stu-id="3b43a-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="3b43a-110">この表現形式を使用すると、ヒープ上に作成される存続期間の短いオブジェクトが増加しますが、それによってパフォーマンスが大幅に低下することはありません。</span><span class="sxs-lookup"><span data-stu-id="3b43a-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="3b43a-111">もちろん、段落、各段落のスタイル、および各段落のテキストを取得する機能を持つ 1 つのクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3b43a-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="3b43a-112">しかし、多くの場合、比較的複雑なクエリは複数のクエリに分割した方が便利です。コードのモジュール性が高まり、保守が簡単になるためです。</span><span class="sxs-lookup"><span data-stu-id="3b43a-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="3b43a-113">また、クエリの一部を再利用する必要がある場合、クエリを分割して記述すると、リファクタリングが容易になります。</span><span class="sxs-lookup"><span data-stu-id="3b43a-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="3b43a-114">連結されたこれらのクエリでは、「[チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)」で詳しく説明されている処理モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b43a-115">例</span><span class="sxs-lookup"><span data-stu-id="3b43a-115">Example</span></span>  
 <span data-ttu-id="3b43a-116">この例では、WordprocessingML ドキュメントを処理して、要素ノード、スタイル名、および各段落のテキストを特定します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="3b43a-117">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="3b43a-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="3b43a-118">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="3b43a-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="3b43a-119">この例のソース ドキュメントを作成する方法の詳細については、「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b43a-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="3b43a-120">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="3b43a-121">また、<xref:System.IO.Packaging?displayProperty=fullName> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-121">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
```csharp  
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
        where (string)style.Attribute(w + "type") == "paragraph"&&  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="3b43a-122">この例を「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」で説明されているドキュメントに適用すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3b43a-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="3b43a-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="3b43a-123">Next Steps</span></span>  
 <span data-ttu-id="3b43a-124">次の例では、<xref:System.Linq.Enumerable.Aggregate%2A> の代わりに拡張メソッドを使用して、複数の文字列を 1 つの文字列に連結する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3b43a-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
-   [<span data-ttu-id="3b43a-125">拡張メソッドを使用したリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="3b43a-125">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b43a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b43a-126">See Also</span></span>  
 <span data-ttu-id="3b43a-127">[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span><span class="sxs-lookup"><span data-stu-id="3b43a-127">[Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span></span>  
 [<span data-ttu-id="3b43a-128">LINQ to XML における遅延実行とレイジー評価 (C#)</span><span class="sxs-lookup"><span data-stu-id="3b43a-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)

