---
title: "方法: 解析エラー (Visual Basic) をキャッチ |Microsoft ドキュメント"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
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
ms.openlocfilehash: 6065bb7656151392e4a5b7ad1078706284ba5616
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="6a32f-102">方法: 解析エラー (Visual Basic) をキャッチ</span><span class="sxs-lookup"><span data-stu-id="6a32f-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="6a32f-103">このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6a32f-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="6a32f-104"><xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="6a32f-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="6a32f-105">形式が正しくないか、無効な XML が渡された場合[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、基になる<xref:System.Xml.XmlReader>クラスは例外をスローします</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="6a32f-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="6a32f-106">さまざまな方法など、XML を解析する<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、例外をキャッチしませんアプリケーションで例外をキャッチし、ことができます。</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="6a32f-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="6a32f-107">XML リテラルを使用する場合は、解析エラーを検出できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a32f-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="6a32f-108">Visual Basic コンパイラは、形式が正しくないか無効な XML をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="6a32f-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a32f-109">例</span><span class="sxs-lookup"><span data-stu-id="6a32f-109">Example</span></span>  
 <span data-ttu-id="6a32f-110">次のコードでは、無効な XML の解析を試行します。</span><span class="sxs-lookup"><span data-stu-id="6a32f-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="6a32f-111">このコードを実行すると、次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6a32f-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="6a32f-112">予期される例外について、 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、および<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>をスローするメソッドを参照してください、<xref:System.Xml.XmlReader>ドキュメント</xref:System.Xml.XmlReader></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="6a32f-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a32f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a32f-113">See Also</span></span>  
 [<span data-ttu-id="6a32f-114">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="6a32f-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
