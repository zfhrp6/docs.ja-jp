---
title: "方法: 属性のコレクションを取得する (LINQ to XML) (C#)"
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
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5cfd1e46dd6ad261844bd7ba1715b382cbe6a870
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="af39c-102">方法: 属性のコレクションを取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="af39c-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="af39c-103">このトピックでは、<xref:System.Xml.Linq.XElement.Attributes%2A> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="af39c-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="af39c-104">このメソッドは、要素の属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="af39c-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af39c-105">例</span><span class="sxs-lookup"><span data-stu-id="af39c-105">Example</span></span>  
 <span data-ttu-id="af39c-106">次の例では、要素の属性のコレクションを反復処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af39c-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="af39c-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="af39c-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="af39c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="af39c-108">See Also</span></span>  
 [<span data-ttu-id="af39c-109">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="af39c-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

