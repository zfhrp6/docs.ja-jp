---
title: "方法: 解析エラーをキャッチする (C#)"
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
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 240bc9770475bdf7b6da2102bd8b552a0991eea6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="abaed-102">方法: 解析エラーをキャッチする (C#)</span><span class="sxs-lookup"><span data-stu-id="abaed-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="abaed-103">このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abaed-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="abaed-104"> は、<xref:System.Xml.XmlReader> を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="abaed-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="abaed-105">形式が正しくない XML や無効な XML が [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="abaed-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="abaed-106">XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="abaed-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abaed-107">例</span><span class="sxs-lookup"><span data-stu-id="abaed-107">Example</span></span>  
 <span data-ttu-id="abaed-108">次のコードでは、無効な XML の解析を試行します。</span><span class="sxs-lookup"><span data-stu-id="abaed-108">The following code tries to parse invalid XML:</span></span>  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 <span data-ttu-id="abaed-109">このコードを実行すると、次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="abaed-109">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="abaed-110"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、および <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> メソッドによってスローされる例外の詳細については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="abaed-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abaed-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="abaed-111">See Also</span></span>  
 [<span data-ttu-id="abaed-112">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="abaed-112">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

