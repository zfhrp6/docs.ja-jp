---
title: "連結クエリのパフォーマンス (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3429da268df07900ebe59ed206b927d209b1cf7f
ms.lasthandoff: 03/13/2017


---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>連結クエリのパフォーマンス (LINQ to XML) (C#)
LINQ (および LINQ to XML) の重要な利点の 1 つは、連結クエリが、大きい複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。  
  
 連結クエリとは、別のクエリをソースとして使用するクエリです。 たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
4  
```  
  
 この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> 軸のパフォーマンスは、基本的にリンク リストの反復と同じです。 <xref:System.Xml.Linq.XContainer.Elements%2A> は遅延実行のある反復子として実装されます。 つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。 この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の 2 つのカテゴリに分けることができます。 設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。  
  
-   `query1` では、`where` 句によってクエリで <xref:System.Linq.Enumerable.Where%2A> メソッドが呼び出されます。 このメソッドも反復子として実装されています。 設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。 反復ごとに、デリゲートが呼び出されて述語を実行します。 設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。  
  
-   `query1` では、select 句によってクエリで <xref:System.Linq.Enumerable.Select%2A> メソッドが呼び出されます。 このメソッドのパフォーマンス プロファイルは <xref:System.Linq.Enumerable.Where%2A> メソッドと同じです。  
  
-   `query2` では、`where` 句と `select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。  
  
 したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。 対応する Visual Basic の例でも、同じパフォーマンス プロファイルがあります。  
  
 反復子の詳細については、「[yield](../../../../csharp/language-reference/keywords/yield.md)」を参照してください。  
  
 クエリの連結に関する詳細なチュートリアルについては、「[チュートリアル: クエリの連結](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
