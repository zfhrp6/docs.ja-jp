---
title: 純粋関数によるリファクタリング (C#)
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: ac0cd63790d5600a96c868a8c7f446ceda737eb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340685"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="d00f2-102">純粋関数によるリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="d00f2-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="d00f2-103">次の例では、前の例 (「[拡張メソッドを使用したリファクタリング (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)」) をリファクタリングして、純粋関数を使用するようにします。この例では、段落のテキストを検索するコードが純粋静的メソッド `ParagraphText` に移動されています。</span><span class="sxs-lookup"><span data-stu-id="d00f2-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d00f2-104">例</span><span class="sxs-lookup"><span data-stu-id="d00f2-104">Example</span></span>  
 <span data-ttu-id="d00f2-105">この例では、WordprocessingML ドキュメントを処理して、WordprocessingML ドキュメントから段落ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="d00f2-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d00f2-106">それぞれの段落のスタイルも特定します。</span><span class="sxs-lookup"><span data-stu-id="d00f2-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="d00f2-107">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d00f2-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="d00f2-108">リファクタリングされたコードについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="d00f2-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="d00f2-109">この例のソース ドキュメントを作成する方法の詳細については、「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d00f2-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="d00f2-110">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d00f2-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="d00f2-111">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="d00f2-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
    // This is a new method that assembles the paragraph text.  
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
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
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
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="d00f2-112">この例では、リファクタリング前と同じ出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d00f2-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="d00f2-113">次の手順</span><span class="sxs-lookup"><span data-stu-id="d00f2-113">Next Steps</span></span>  
 <span data-ttu-id="d00f2-114">次の例では、XML を別の形式に射影する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d00f2-114">The next example shows how to project XML into a different shape:</span></span>  
  
-   [<span data-ttu-id="d00f2-115">異なる構造の XML の射影 (C#)</span><span class="sxs-lookup"><span data-stu-id="d00f2-115">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="d00f2-116">参照</span><span class="sxs-lookup"><span data-stu-id="d00f2-116">See Also</span></span>  
 [<span data-ttu-id="d00f2-117">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="d00f2-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="d00f2-118">拡張メソッドを使用したリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="d00f2-118">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
 [<span data-ttu-id="d00f2-119">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="d00f2-119">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
