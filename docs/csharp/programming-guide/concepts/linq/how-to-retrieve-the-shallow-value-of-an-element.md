---
title: "方法: 要素の浅い値を取得する (C#)"
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
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aad07fdba1d3df2b72f867e6845536300031146b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="363f6-102">方法: 要素の浅い値を取得する (C#)</span><span class="sxs-lookup"><span data-stu-id="363f6-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="363f6-103">このトピックでは、要素の浅い値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="363f6-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="363f6-104">浅い値は、特定の要素のみの値のことです。これに対し、深い値とは、すべての子孫要素の値が単一の文字列として連結された値をいいます。</span><span class="sxs-lookup"><span data-stu-id="363f6-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="363f6-105">キャストまたは <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> プロパティによって要素値を取得する場合は、深い値を取得することになります。</span><span class="sxs-lookup"><span data-stu-id="363f6-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> property, you retrieve the deep value.</span></span> <span data-ttu-id="363f6-106">浅い値を取得するには、次の例のように `ShallowValue` 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="363f6-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="363f6-107">浅い値を取得することは、要素をその内容に基づいて選択する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="363f6-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="363f6-108">次の例では、要素の浅い値を取得する拡張メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="363f6-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="363f6-109">次に、この拡張メソッドをクエリの中で使用して、計算値を含んだすべての要素をリストします。</span><span class="sxs-lookup"><span data-stu-id="363f6-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="363f6-110">例</span><span class="sxs-lookup"><span data-stu-id="363f6-110">Example</span></span>  
 <span data-ttu-id="363f6-111">次のテキスト ファイル (Report.xml) は、この例のソースです。</span><span class="sxs-lookup"><span data-stu-id="363f6-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="363f6-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="363f6-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="363f6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="363f6-113">See Also</span></span>  
 [<span data-ttu-id="363f6-114">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="363f6-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

