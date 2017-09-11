---
title: "方法: Office Open XML ドキュメントを変更する (C#)"
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
ms.assetid: 467d489c-2b1b-453b-a757-8ac180e82a96
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 21a82e6ff71c9f8c4882eeab266275627e2c2cd0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-an-office-open-xml-document-c"></a><span data-ttu-id="9e13c-102">方法: Office Open XML ドキュメントを変更する (C#)</span><span class="sxs-lookup"><span data-stu-id="9e13c-102">How to: Modify an Office Open XML Document (C#)</span></span>
<span data-ttu-id="9e13c-103">このトピックでは、Office Open XML ドキュメントを開き、それを変更して保存する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="9e13c-104">Office Open XML の詳細については、[www.openxmldeveloper.org](http://go.microsoft.com/fwlink/?LinkID=95573) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e13c-104">For more information on Office Open XML, see [www.openxmldeveloper.org](http://go.microsoft.com/fwlink/?LinkID=95573).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e13c-105">例</span><span class="sxs-lookup"><span data-stu-id="9e13c-105">Example</span></span>  
 <span data-ttu-id="9e13c-106">この例では、ドキュメント内の最初の段落要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="9e13c-107">次に、段落からテキストを取得し、段落内のテキスト ランをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="9e13c-108">また、大文字に変換された最初の段落のテキストから構成される新しいテキスト ランを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="9e13c-109">最後に、変更した XML を Open XML パッケージにシリアル化して閉じます。</span><span class="sxs-lookup"><span data-stu-id="9e13c-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="9e13c-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="9e13c-111">また、<xref:System.IO.Packaging?displayProperty=fullName> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e13c-111">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
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
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                XDocument xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                PackagePart stylePart = null;  
                XDocument styleDoc = null;  
  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
  
                XElement paraNode = xDoc  
                                    .Root  
                                    .Element(w + "body")  
                                    .Descendants(w + "p")  
                                    .FirstOrDefault();  
  
                string paraText = ParagraphText(paraNode);  
  
                // remove all text runs  
                paraNode.Descendants(w + "r").Remove();  
  
                paraNode.Add(  
                    new XElement(w + "r",  
                        new XElement(w + "t", paraText.ToUpper())  
                    )  
                );  
  
                //  Save the XML into the package  
                using (XmlWriter xw =  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write)))  
                {  
                    xDoc.Save(xw);  
                }  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper());  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9e13c-112">このプログラムを実行した後で `SampleDoc.docx` を開くと、このプログラムによってドキュメント内の最初の段落が大文字に変換されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9e13c-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="9e13c-113">この例で「[ソースとなる Office Open XML ドキュメントの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」に記載されているサンプルの Open XML ドキュメントを使用して実行すると、次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="9e13c-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e13c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e13c-114">See Also</span></span>  
 [<span data-ttu-id="9e13c-115">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9e13c-115">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

