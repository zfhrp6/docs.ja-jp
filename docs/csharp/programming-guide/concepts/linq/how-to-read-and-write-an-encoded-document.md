---
title: '方法: エンコードされたドキュメントを読み書きする (C#)'
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: 9fc6a7beaa4a7b9de21961e1095dd41fe2e407dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="7c923-102">方法: エンコードされたドキュメントを読み書きする (C#)</span><span class="sxs-lookup"><span data-stu-id="7c923-102">How to: Read and Write an Encoded Document (C#)</span></span>
<span data-ttu-id="7c923-103">エンコードされた XML ドキュメントを作成するには、<xref:System.Xml.Linq.XDeclaration> を XML ツリーに追加し、エンコーディングを目的のコード ページ名に設定します。</span><span class="sxs-lookup"><span data-stu-id="7c923-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="7c923-104"><xref:System.Text.Encoding.WebName%2A> から返される値はすべて有効な値です。</span><span class="sxs-lookup"><span data-stu-id="7c923-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="7c923-105">エンコードされたドキュメントを読み込むと、<xref:System.Xml.Linq.XDeclaration.Encoding%2A> プロパティがコード ページ名に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7c923-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="7c923-106"><xref:System.Xml.Linq.XDeclaration.Encoding%2A> を有効なコード ページ名に設定すると、指定したエンコーディングで [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="7c923-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c923-107">例</span><span class="sxs-lookup"><span data-stu-id="7c923-107">Example</span></span>  
 <span data-ttu-id="7c923-108">次の例では、UTF-8 エンコーディングのドキュメントと UTF-16 エンコーディングのドキュメントを 1 つずつ作成します。</span><span class="sxs-lookup"><span data-stu-id="7c923-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="7c923-109">次に、ドキュメントを読み込み、エンコーディングをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="7c923-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="7c923-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c923-110">This example produces the following output:</span></span>  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c923-111">参照</span><span class="sxs-lookup"><span data-stu-id="7c923-111">See Also</span></span>  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7c923-112">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="7c923-112">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
