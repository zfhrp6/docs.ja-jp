---
title: '方法: 解析 (String) (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d0fd7c7adcfbd7e2136d1a652017d470634016b9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-parse-a-string-visual-basic"></a><span data-ttu-id="d5d6b-102">方法: 解析 (String) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d6b-102">How to: Parse a String (Visual Basic)</span></span>
<span data-ttu-id="d5d6b-103">このトピックでは、C# の場合、XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-103">This topic shows how to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5d6b-104">例</span><span class="sxs-lookup"><span data-stu-id="d5d6b-104">Example</span></span>  
 <span data-ttu-id="d5d6b-105">使用して Visual Basic で文字列を解析することができます、`XElement.Parse`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-105">You can parse a string in Visual Basic by using the `XElement.Parse` method.</span></span> <span data-ttu-id="d5d6b-106">ただし、次のコードに示すように XML リテラルを使用する方が効率的です。これは、XML リテラルでは、文字列から XML を解析する場合のようなパフォーマンスの低下がないためです。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-106">However, it is more efficient to use XML literals, as shown in following code, because XML literals do not suffer from the same performance penalties as parsing XML from a string.</span></span>  
  
 <span data-ttu-id="d5d6b-107">XML リテラルを使用すると、だけコピーして、Visual Basic プログラムに XML を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-107">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5d6b-108">テキストの解析やテキスト ファイルからの XML ドキュメントの読み込みは、関数型構築より非効率です。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-108">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="d5d6b-109">XML ツリーをコードから初期化すると、関数型構築で必要となるプロセッサ時間は、テキストの解析に比べて短くなります。</span><span class="sxs-lookup"><span data-stu-id="d5d6b-109">If you are initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5d6b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5d6b-110">See Also</span></span>  
 [<span data-ttu-id="d5d6b-111">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="d5d6b-111">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
