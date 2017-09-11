---
title: "方法: 文字列 (Visual Basic) を解析 |Microsoft ドキュメント"
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
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
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
ms.openlocfilehash: d06a0ca84650a860a7528cefafaa1c3158e5949a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="14eaf-102">方法: 文字列 (Visual Basic) を解析</span><span class="sxs-lookup"><span data-stu-id="14eaf-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="14eaf-103">このトピックでは、C# の場合、XML ツリーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="14eaf-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14eaf-104">例</span><span class="sxs-lookup"><span data-stu-id="14eaf-104">Example</span></span>  
 <span data-ttu-id="14eaf-105">文字列を解析する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を使用して、`XElement.Parse`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="14eaf-105">You can parse a string in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using the `XElement.Parse` method.</span></span> <span data-ttu-id="14eaf-106">ただし、次のコードに示すように XML リテラルを使用する方が効率的です。これは、XML リテラルでは、文字列から XML を解析する場合のようなパフォーマンスの低下がないためです。</span><span class="sxs-lookup"><span data-stu-id="14eaf-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="14eaf-107">XML リテラルを使用すると、XML を [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] プログラムに単にコピーして貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="14eaf-107">By using XML literals, you can just copy and paste your XML into your [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14eaf-108">テキストの解析やテキスト ファイルからの XML ドキュメントの読み込みは、関数型構築より非効率です。</span><span class="sxs-lookup"><span data-stu-id="14eaf-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="14eaf-109">XML ツリーをコードから初期化すると、関数型構築で必要となるプロセッサ時間は、テキストの解析に比べて短くなります。</span><span class="sxs-lookup"><span data-stu-id="14eaf-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14eaf-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="14eaf-110">See Also</span></span>  
 [<span data-ttu-id="14eaf-111">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="14eaf-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
