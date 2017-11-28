---
title: "方法: 属性のコレクションを取得する (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 165c807735bfc73375d4ddec125786750ad08ad1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>方法: 属性のコレクションを取得する (LINQ to XML) (C#)
このトピックでは、<xref:System.Xml.Linq.XElement.Attributes%2A> メソッドについて説明します。 このメソッドは、要素の属性を取得します。  
  
## <a name="example"></a>例  
 次の例では、要素の属性のコレクションを反復処理する方法を示します。  
  
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
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
