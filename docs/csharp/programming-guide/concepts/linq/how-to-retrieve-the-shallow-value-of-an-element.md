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
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>方法: 要素の浅い値を取得する (C#)
このトピックでは、要素の浅い値を取得する方法について説明します。 浅い値は、特定の要素のみの値のことです。これに対し、深い値とは、すべての子孫要素の値が単一の文字列として連結された値をいいます。  
  
 キャストまたは <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> プロパティによって要素値を取得する場合は、深い値を取得することになります。 浅い値を取得するには、次の例のように `ShallowValue` 拡張メソッドを使用します。 浅い値を取得することは、要素をその内容に基づいて選択する必要がある場合に役立ちます。  
  
 次の例では、要素の浅い値を取得する拡張メソッドを宣言しています。 次に、この拡張メソッドをクエリの中で使用して、計算値を含んだすべての要素をリストします。  
  
## <a name="example"></a>例  
 次のテキスト ファイル (Report.xml) は、この例のソースです。  
  
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
  
 この例を実行すると、次の出力が生成されます。  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

