---
title: '方法: LINQ to XML を使用してディクショナリを操作する (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 3f3b2a19f2527ef5d2fececf916c09256e90af7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="d43cb-102">方法: LINQ to XML を使用してディクショナリを操作する (C#)</span><span class="sxs-lookup"><span data-stu-id="d43cb-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="d43cb-103">さまざまなデータ構造と XML を相互に変換すると便利な場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="d43cb-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="d43cb-104">このトピックでは、<xref:System.Collections.Generic.Dictionary%602> と XML を相互に変換することによる、一般的な相互変換の実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="d43cb-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d43cb-105">例</span><span class="sxs-lookup"><span data-stu-id="d43cb-105">Example</span></span>  
 <span data-ttu-id="d43cb-106">この例では、新しい <xref:System.Xml.Linq.XElement> オブジェクトをクエリが射影する、関数型構築の形式を使用します。結果のコレクションは、引数としてルート <xref:System.Xml.Linq.XElement> オブジェクトのコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d43cb-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d43cb-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d43cb-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="d43cb-108">例</span><span class="sxs-lookup"><span data-stu-id="d43cb-108">Example</span></span>  
 <span data-ttu-id="d43cb-109">次のコードは、XML からディクショナリを作成します。</span><span class="sxs-lookup"><span data-stu-id="d43cb-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="d43cb-110">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d43cb-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="d43cb-111">参照</span><span class="sxs-lookup"><span data-stu-id="d43cb-111">See Also</span></span>  
 [<span data-ttu-id="d43cb-112">プロジェクションと変換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d43cb-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
