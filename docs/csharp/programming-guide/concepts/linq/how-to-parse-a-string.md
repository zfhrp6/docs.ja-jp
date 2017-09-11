---
title: "方法: 文字列を解析する (C#)"
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
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
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
ms.openlocfilehash: 8aa6e0235a5a9e834167b74897121a1ab003078b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="3fa5b-102">方法: 文字列を解析する (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa5b-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="3fa5b-103">このトピックでは、C# で文字列を解析して XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3fa5b-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fa5b-104">例</span><span class="sxs-lookup"><span data-stu-id="3fa5b-104">Example</span></span>  
 <span data-ttu-id="3fa5b-105">次の C# コードは、文字列を解析する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3fa5b-105">The following C# code shows how to parse a string.</span></span>  
  
```csharp  
XElement contacts = XElement.Parse(  
    @"<Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type=""home"">206-555-0144</Phone>  
            <Phone type=""work"">425-555-0145</Phone>  
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
            <Phone Type=""mobile"">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>");  
Console.WriteLine(contacts);  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fa5b-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fa5b-106">See Also</span></span>  
 [<span data-ttu-id="3fa5b-107">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa5b-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

