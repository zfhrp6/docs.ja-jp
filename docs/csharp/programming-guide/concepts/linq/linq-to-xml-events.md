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
# <a name="linq-to-xml-events-c"></a>LINQ to XML イベント (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] イベントを使うと、XML ツリーが変更されるときに通知を受けることができます。  
  
 イベントは、任意の <xref:System.Xml.Linq.XObject> のインスタンスに追加できます。 イベント ハンドラーは、その <xref:System.Xml.Linq.XObject> およびその任意の子孫に対する変更のイベントを受け取ります。 たとえば、イベント ハンドラーをツリーのルートに追加して、そのツリーに対するすべての変更をイベント ハンドラーから処理できます。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] イベントの例については、<xref:System.Xml.Linq.XObject.Changing> および <xref:System.Xml.Linq.XObject.Changed> を参照してください。  
  
## <a name="types-and-events"></a>型とイベント  
 イベントを使用する場合は、次の型を使用できます。  
  
|種類|説明|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<xref:System.Xml.Linq.XObject.Changing> イベントおよび <xref:System.Xml.Linq.XObject.Changed> イベントのデータを提供します。|  
  
 XML ツリーを変更するときに次のイベントが発生します。  
  
|Event|説明|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更される直前に発生します。|  
|<xref:System.Xml.Linq.XObject.Changed>|<xref:System.Xml.Linq.XObject> またはその子孫のいずれかが変更されたときに発生します。|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 XML ツリー内の集計情報を維持する場合に、イベントは便利です。 たとえば、請求書の品目の合計である請求合計を維持する場合があります。 この例では、イベントを使用して、複合要素の `Items` の下にあるすべての子要素の合計を維持します。  
  
### <a name="code"></a>コード  
  
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
  
### <a name="comments"></a>コメント  
 このコードを実行すると、次の出力が生成されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [高度な LINQ to XML プログラミング (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
