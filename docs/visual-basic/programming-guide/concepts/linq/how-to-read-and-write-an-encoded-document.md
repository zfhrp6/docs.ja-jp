---
title: "方法: エンコードされたドキュメント (Visual Basic) を読み書き |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5bfc825ca32aaa365b7cc2d0347834a796d3598b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="758ca-102">方法: 読み取りし、書き込みのエンコードされたドキュメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758ca-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>
<span data-ttu-id="758ca-103">追加するエンコードされた XML ドキュメントを作成する、 <xref:System.Xml.Linq.XDeclaration>XML ツリーに必要なコード ページ名にエンコーディングを設定します</xref:System.Xml.Linq.XDeclaration>。</span><span class="sxs-lookup"><span data-stu-id="758ca-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="758ca-104">任意の値によって返される<xref:System.Text.Encoding.WebName%2A>有効な値です</xref:System.Text.Encoding.WebName%2A>。</span><span class="sxs-lookup"><span data-stu-id="758ca-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="758ca-105">エンコードされたドキュメントを読み取る場合、<xref:System.Xml.Linq.XDeclaration.Encoding%2A>プロパティは、コード ページ名に設定されます</xref:System.Xml.Linq.XDeclaration.Encoding%2A>。</span><span class="sxs-lookup"><span data-stu-id="758ca-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="758ca-106">設定した場合<xref:System.Xml.Linq.XDeclaration.Encoding%2A>に有効なコード ページ名では、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]が、指定したエンコーディングでシリアル化します</xref:System.Xml.Linq.XDeclaration.Encoding%2A>。</span><span class="sxs-lookup"><span data-stu-id="758ca-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="758ca-107">例</span><span class="sxs-lookup"><span data-stu-id="758ca-107">Example</span></span>  
 <span data-ttu-id="758ca-108">次の例では、UTF-8 エンコーディングのドキュメントと UTF-16 エンコーディングのドキュメントを&1; つずつ作成します。</span><span class="sxs-lookup"><span data-stu-id="758ca-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="758ca-109">次に、ドキュメントを読み込み、エンコーディングをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="758ca-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```vb  
Console.WriteLine("Creating a document with utf-8 encoding")  
Dim encodedDoc8 As XDocument = _  
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>  
        <Root>Content</Root>   
  
encodedDoc8.Save("EncodedUtf8.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Console.WriteLine("Creating a document with utf-16 encoding")  
Dim encodedDoc16 As XDocument = _  
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>  
        <Root>Content</Root>  
  
encodedDoc16.Save("EncodedUtf16.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)  
```  
  
 <span data-ttu-id="758ca-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="758ca-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="758ca-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="758ca-111">See Also</span></span>  
 <span data-ttu-id="758ca-112"><xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName></xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="758ca-112"><xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="758ca-113"> [高度な LINQ to XML のプログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span><span class="sxs-lookup"><span data-stu-id="758ca-113"> [Advanced LINQ to XML Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span></span>
