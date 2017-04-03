---
title: "方法: 名前空間内の XML に対するクエリを記述する (C#) | Microsoft Docs"
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
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 075f0dab486d773cd7dd0616a6432f065b5a5eb5
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>方法: 名前空間内の XML に対するクエリを記述する
名前空間内の XML に対するクエリを記述するには、正しい名前空間を持つ <xref:System.Xml.Linq.XName> オブジェクトを使用する必要があります。  
  
 C# での最も一般的な方法は、URI を含んだ文字列を使用して <xref:System.Xml.Linq.XNamespace> を初期化し、加算演算子オーバーロードを使用して名前空間をローカル名に連結することです。  
  
 このトピックの最初に示す一連の例では、既定の名前空間内に XML ツリーを作成する方法を示します。 2 つ目の例では、プレフィックスを持つ名前空間で XML ツリーを作成する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、既定の名前空間に含まれる XML ツリーを作成しています。 さらに、要素のコレクションを取得しています。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>例  
 C# では、プレフィックスを持つ名前空間を使用する XML ツリーでも、既定の名前空間を持つ XML ツリーでも、クエリを記述する方法は同じです。  
  
 次の例では、プレフィックスを持つ名前空間に含まれる XML ツリーを作成しています。 さらに、要素のコレクションを取得しています。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>関連項目  
 [XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
