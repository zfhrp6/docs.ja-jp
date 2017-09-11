---
title: "拡張メソッドを使用したリファクタリング (C#)"
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
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c4145e38a6fc49d53d274520dd155cffb5e7f9d5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="d60f7-102">拡張メソッドを使用したリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="d60f7-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="d60f7-103">ここに示す例は、前の例「[段落のテキストの取得 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)」に基づいており、拡張メソッドとして実装される純粋関数を使って文字列の連結をリファクターしています。</span><span class="sxs-lookup"><span data-stu-id="d60f7-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="d60f7-104">前の例では、<xref:System.Linq.Enumerable.Aggregate%2A> 標準クエリ演算子を使用して、複数の文字列が 1 つの文字列に連結されていました。</span><span class="sxs-lookup"><span data-stu-id="d60f7-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="d60f7-105">ただし、拡張メソッドでこの処理を記述した方が、結果のクエリが小さく簡単になるので便利です。</span><span class="sxs-lookup"><span data-stu-id="d60f7-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60f7-106">例</span><span class="sxs-lookup"><span data-stu-id="d60f7-106">Example</span></span>  
 <span data-ttu-id="d60f7-107">この例では、WordprocessingML ドキュメントを処理して、段落、各段落のスタイル、および各段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="d60f7-108">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d60f7-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="d60f7-109">この例には、`StringConcatenate` メソッドの複数のオーバーロードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d60f7-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="d60f7-110">この例のソース ドキュメントを作成する手順については、「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d60f7-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="d60f7-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="d60f7-112">また、<xref:System.IO.Packaging?displayProperty=fullName> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-112">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="d60f7-113">例</span><span class="sxs-lookup"><span data-stu-id="d60f7-113">Example</span></span>  
 <span data-ttu-id="d60f7-114">`StringConcatenate` メソッドには 4 つのオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="d60f7-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="d60f7-115">あるオーバーロードは、文字列のコレクションを受け取って 1 つの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="d60f7-116">別のオーバーロードは、任意の型のコレクション、および単一のコレクションを文字列に射影するデリゲートを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d60f7-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="d60f7-117">残りの 2 つのオーバーロードでは、区切り文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d60f7-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="d60f7-118">次のコードでは、4 つのオーバーロードがすべて使用されています。</span><span class="sxs-lookup"><span data-stu-id="d60f7-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="d60f7-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d60f7-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="d60f7-120">例</span><span class="sxs-lookup"><span data-stu-id="d60f7-120">Example</span></span>  
 <span data-ttu-id="d60f7-121">ここで、新しい拡張メソッドを利用するように例を変更します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="d60f7-122">この例を「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」で説明されているドキュメントに適用すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d60f7-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="d60f7-123">このリファクタリングは、純粋関数へのリファクタリングの変化形であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d60f7-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="d60f7-124">次のトピックでは、純粋関数へのリファクタリングに関する考え方について詳しく紹介します。</span><span class="sxs-lookup"><span data-stu-id="d60f7-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d60f7-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="d60f7-125">Next Steps</span></span>  
 <span data-ttu-id="d60f7-126">次の例は、純粋関数を使用してこのコードをリファクターする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d60f7-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
-   [<span data-ttu-id="d60f7-127">純粋関数によるリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d60f7-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="d60f7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d60f7-128">See Also</span></span>  
 <span data-ttu-id="d60f7-129">[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span><span class="sxs-lookup"><span data-stu-id="d60f7-129">[Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) </span></span>  
 [<span data-ttu-id="d60f7-130">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="d60f7-130">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

