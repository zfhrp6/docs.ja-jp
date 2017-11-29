---
title: "LINQ to XML イベント (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90e868c7de8c4eb8f252a914acf4bffe2fd8a6ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="c050a-102">LINQ to XML イベント (C#)</span><span class="sxs-lookup"><span data-stu-id="c050a-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c050a-103"> イベントを使うと、XML ツリーが変更されるときに通知を受けることができます。</span><span class="sxs-lookup"><span data-stu-id="c050a-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="c050a-104">イベントは、任意の <xref:System.Xml.Linq.XObject> のインスタンスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c050a-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="c050a-105">イベント ハンドラーは、その <xref:System.Xml.Linq.XObject> およびその任意の子孫に対する変更のイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c050a-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="c050a-106">たとえば、イベント ハンドラーをツリーのルートに追加して、そのツリーに対するすべての変更をイベント ハンドラーから処理できます。</span><span class="sxs-lookup"><span data-stu-id="c050a-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="c050a-107">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] イベントの例については、<xref:System.Xml.Linq.XObject.Changing> および <xref:System.Xml.Linq.XObject.Changed> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c050a-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="c050a-108">型とイベント</span><span class="sxs-lookup"><span data-stu-id="c050a-108">Types and Events</span></span>  
 <span data-ttu-id="c050a-109">イベントを使用する場合は、次の型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c050a-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="c050a-110">種類</span><span class="sxs-lookup"><span data-stu-id="c050a-110">Type</span></span>|<span data-ttu-id="c050a-111">説明</span><span class="sxs-lookup"><span data-stu-id="c050a-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="c050a-112"><xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c050a-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="c050a-113"><xref:System.Xml.Linq.XObject.Changing> イベントおよび <xref:System.Xml.Linq.XObject.Changed> イベントのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="c050a-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="c050a-114">XML ツリーを変更するときに次のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="c050a-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="c050a-115">Event</span><span class="sxs-lookup"><span data-stu-id="c050a-115">Event</span></span>|<span data-ttu-id="c050a-116">説明</span><span class="sxs-lookup"><span data-stu-id="c050a-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="c050a-117"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更される直前に発生します。</span><span class="sxs-lookup"><span data-stu-id="c050a-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="c050a-118"><xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="c050a-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c050a-119">例</span><span class="sxs-lookup"><span data-stu-id="c050a-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c050a-120">説明</span><span class="sxs-lookup"><span data-stu-id="c050a-120">Description</span></span>  
 <span data-ttu-id="c050a-121">XML ツリー内の集計情報を維持する場合に、イベントは便利です。</span><span class="sxs-lookup"><span data-stu-id="c050a-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="c050a-122">たとえば、請求書の品目の合計である請求合計を維持する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c050a-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="c050a-123">この例では、イベントを使用して、複合要素の `Items` の下にあるすべての子要素の合計を維持します。</span><span class="sxs-lookup"><span data-stu-id="c050a-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c050a-124">コード</span><span class="sxs-lookup"><span data-stu-id="c050a-124">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="c050a-125">コメント</span><span class="sxs-lookup"><span data-stu-id="c050a-125">Comments</span></span>  
 <span data-ttu-id="c050a-126">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c050a-126">This code produces the following output:</span></span>  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c050a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c050a-127">See Also</span></span>  
 [<span data-ttu-id="c050a-128">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="c050a-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
