---
title: "既定の段落スタイルの検索 (C#)"
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
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 834654837b5c7fc747b0df1ee9dc645664a77351
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="188c8-102">既定の段落スタイルの検索 (C#)</span><span class="sxs-lookup"><span data-stu-id="188c8-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="188c8-103">「WordprocessingML ドキュメント内の情報の操作」チュートリアルでの最初のタスクは、ドキュメント内にある段落の既定のスタイルを検索することです。</span><span class="sxs-lookup"><span data-stu-id="188c8-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="188c8-104">例</span><span class="sxs-lookup"><span data-stu-id="188c8-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="188c8-105">説明</span><span class="sxs-lookup"><span data-stu-id="188c8-105">Description</span></span>  
 <span data-ttu-id="188c8-106">次の例では、Office Open XML WordprocessingML ドキュメントを開き、パッケージのドキュメント パーツとスタイル パーツを検索した後、既定のスタイル名を検索するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="188c8-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="188c8-107">Office Open XML ドキュメント パッケージおよびその構成パーツについて詳しくは、「[Office Open XML WordprocessingML ドキュメントの詳細 (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="188c8-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="188c8-108">このクエリは、値が "paragraph" である `w:style` という名前の属性と、値が "1" である `w:type` という名前の属性を持つ `w:default` という名前のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="188c8-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="188c8-109">これらの属性を持つ XML ノードは 1 つしかないため、このクエリは、<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> 演算子を使用してコレクションをシングルトンに変換します。</span><span class="sxs-lookup"><span data-stu-id="188c8-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="188c8-110">次に、`w:styleId` という名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="188c8-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="188c8-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="188c8-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="188c8-112">また、<xref:System.IO.Packaging?displayProperty=fullName> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="188c8-112">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="188c8-113">コード</span><span class="sxs-lookup"><span data-stu-id="188c8-113">Code</span></span>  
  
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
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="188c8-114">コメント</span><span class="sxs-lookup"><span data-stu-id="188c8-114">Comments</span></span>  
 <span data-ttu-id="188c8-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="188c8-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="188c8-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="188c8-116">Next Steps</span></span>  
 <span data-ttu-id="188c8-117">次の例では、ドキュメント内のすべての段落およびそのスタイルを検索する同様のクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="188c8-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="188c8-118">段落とそのスタイルの取得 (C#)</span><span class="sxs-lookup"><span data-stu-id="188c8-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="188c8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="188c8-119">See Also</span></span>  
 [<span data-ttu-id="188c8-120">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="188c8-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)

