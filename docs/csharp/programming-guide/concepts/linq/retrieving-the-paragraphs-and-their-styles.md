---
title: "段落とそのスタイルの取得 (C#)"
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
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: db420c0aca9edadb8009556ebf476f196ee7641a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="24d6d-102">段落とそのスタイルの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="24d6d-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="24d6d-103">この例では、WordprocessingML ドキュメントから段落ノードを取得するクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="24d6d-104">それぞれの段落のスタイルも特定します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="24d6d-105">このクエリの基になった前の例「[既定の段落スタイルの検索 (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)」のクエリでは、スタイルの一覧から既定のスタイルを取得しています。</span><span class="sxs-lookup"><span data-stu-id="24d6d-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="24d6d-106">スタイルが明示的に設定されていない段落のスタイルをクエリで特定するには、この情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="24d6d-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="24d6d-107">段落のスタイルは、`w:pPr` 要素を通して設定されます。この要素が含まれていない段落は、既定のスタイルを使用して書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="24d6d-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="24d6d-108">このトピックでは、クエリを構成するいくつかの要素の意味を説明し、完全な作業例の一部分であるクエリを紹介します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d6d-109">例</span><span class="sxs-lookup"><span data-stu-id="24d6d-109">Example</span></span>  
 <span data-ttu-id="24d6d-110">ドキュメント内のすべての段落とそのスタイルを取得するクエリのソースは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="24d6d-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="24d6d-111">この式は、前の例「[既定の段落スタイルの検索 (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)」のクエリのソースと似ています。</span><span class="sxs-lookup"><span data-stu-id="24d6d-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="24d6d-112">主な違いは、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸の代わりに <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用している点です。</span><span class="sxs-lookup"><span data-stu-id="24d6d-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="24d6d-113">クエリで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用しているのは、セクションが含まれているドキュメントの場合、段落が本文要素の直接の子とならず、階層内で 2 つ下のレベルに位置するためです。</span><span class="sxs-lookup"><span data-stu-id="24d6d-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="24d6d-114">コードで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用すると、ドキュメントでセクションが使用されているかどうかにかかわらず機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="24d6d-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d6d-115">例</span><span class="sxs-lookup"><span data-stu-id="24d6d-115">Example</span></span>  
 <span data-ttu-id="24d6d-116">クエリで `let` 句を使用して、スタイル ノードが含まれる要素を特定します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="24d6d-117">要素がない場合は、`styleNode` が `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="24d6d-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="24d6d-118">`let` 句は、まず <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用して `pPr` という名前の要素すべてを検索し、次に <xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用して `pStyle` という名前の子要素すべてを検索し、最後に <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準クエリ演算子を使用してコレクションをシングルトンに変換します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="24d6d-119">コレクションが空の場合は、`styleNode` が `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="24d6d-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="24d6d-120">これは、`pStyle` 子孫ノードを検索するのに便利な表現形式です。</span><span class="sxs-lookup"><span data-stu-id="24d6d-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="24d6d-121">`pPr` 子ノードが存在しない場合、コードが例外をスローして失敗することはなく、`styleNode` が `null` に設定されます。これは、この `let` 句で予期された動作です。</span><span class="sxs-lookup"><span data-stu-id="24d6d-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="24d6d-122">このクエリは、匿名型のコレクションを射影します。このコレクションには、`StyleName` および `ParagraphNode` の 2 つのメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="24d6d-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d6d-123">例</span><span class="sxs-lookup"><span data-stu-id="24d6d-123">Example</span></span>  
 <span data-ttu-id="24d6d-124">この例では、WordprocessingML ドキュメントを処理して、WordprocessingML ドキュメントから段落ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="24d6d-125">それぞれの段落のスタイルも特定します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="24d6d-126">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="24d6d-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="24d6d-127">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="24d6d-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="24d6d-128">この例のソース ドキュメントを作成する手順については、「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24d6d-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="24d6d-129">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="24d6d-130">また、<xref:System.IO.Packaging?displayProperty=fullName> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-130">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
```csharp  
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
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
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
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 <span data-ttu-id="24d6d-131">この例を「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」で説明されているドキュメントに適用すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="24d6d-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="24d6d-132">次の手順</span><span class="sxs-lookup"><span data-stu-id="24d6d-132">Next Steps</span></span>  
 <span data-ttu-id="24d6d-133">次のトピック (「[段落のテキストの取得 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)」) では、段落のテキストを取得するクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="24d6d-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d6d-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="24d6d-134">See Also</span></span>  
 [<span data-ttu-id="24d6d-135">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="24d6d-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)

