---
title: '方法: 解析エラー (Visual Basic) をキャッチ'
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: aa72b914d4640410a4d47ba49e774dcee31a54c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643523"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="f51b0-102">方法: 解析エラー (Visual Basic) をキャッチ</span><span class="sxs-lookup"><span data-stu-id="f51b0-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="f51b0-103">このトピックでは、形式が正しくないか無効な XML を検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f51b0-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f51b0-104"> は、<xref:System.Xml.XmlReader> を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="f51b0-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="f51b0-105">形式が正しくない XML や無効な XML が [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] に渡されると、基になる <xref:System.Xml.XmlReader> クラスから例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f51b0-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="f51b0-106">XML を解析するさまざまなメソッド (<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType> など) はこの例外をキャッチしません。この例外は、アプリケーションでキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="f51b0-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="f51b0-107">XML リテラルを使用する場合は、解析エラーを検出できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f51b0-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="f51b0-108">Visual Basic コンパイラは、形式が正しくないか無効な XML をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="f51b0-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f51b0-109">例</span><span class="sxs-lookup"><span data-stu-id="f51b0-109">Example</span></span>  
 <span data-ttu-id="f51b0-110">次のコードでは、無効な XML の解析を試行します。</span><span class="sxs-lookup"><span data-stu-id="f51b0-110">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="f51b0-111">このコードを実行すると、次の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f51b0-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="f51b0-112"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>、および <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> メソッドによってスローされる例外の詳細については、<xref:System.Xml.XmlReader> のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f51b0-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51b0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f51b0-113">See Also</span></span>  
 [<span data-ttu-id="f51b0-114">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="f51b0-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
