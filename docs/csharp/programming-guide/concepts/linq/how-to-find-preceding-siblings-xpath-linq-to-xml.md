---
title: "方法: 先行する兄弟を検索する (XPath-LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 964a85548b7cf5fd7334c46f21e2d50a9ff17987
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>方法: 先行する兄弟を検索する (XPath-LINQ to XML) (C#)
このトピックでは、XPath の `preceding-sibling` 軸と [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の子 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> 軸を比較します。  
  
 XPath 式を次に示します。  
  
 `preceding-sibling::*`  
  
 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> と <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> の結果はドキュメント順になることに注意してください。  
  
## <a name="example"></a>例  
 次の例では、`FullAddress` 要素を検索し、次に `preceding-sibling` 軸を使用して前の要素を取得します。  
  
 この例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>関連項目  
 [XPath ユーザー向けの LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
