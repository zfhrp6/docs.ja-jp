---
title: "方法: 要素名をフィルター処理する (LINQ to XML) (C#)"
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
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 03f1be79322882e49b7cb619ff4578fda94450a7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a>方法: 要素名をフィルター処理する (LINQ to XML) (C#)
<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> を返すメソッドのいずれかを呼び出す際に、要素名をフィルター処理できます。  
  
## <a name="example"></a>例  
 この例では、指定した名前を持つ子孫だけが含まれるようにフィルター処理された子孫のコレクションを取得します。  
  
 この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <xref:System.Collections.Generic.IEnumerable%601> コレクションの <xref:System.Xml.Linq.XElement> を返す他のメソッドは、同じパターンに従います。 そのシグネチャは、<xref:System.Xml.Linq.XContainer.Elements%2A> および <xref:System.Xml.Linq.XContainer.Descendants%2A> と似ています。 類似するシグネチャを持つメソッドの一覧を次に示します。  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。 詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。  
  
 この例では、XML ドキュメントの「[サンプル XML ファイル : 名前空間内の一般的な購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)」を使用します。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

