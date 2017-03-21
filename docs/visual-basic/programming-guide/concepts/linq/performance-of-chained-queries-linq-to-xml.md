---
title: "連結クエリ (LINQ to XML) のパフォーマンス (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dd5b63f255107c5864108cfbb87bef6e53a971a0
ms.lasthandoff: 03/13/2017


---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>連結クエリ (LINQ to XML) のパフォーマンス (Visual Basic)
LINQ (および LINQ to XML) の重要な利点の&1; つは、連結クエリが、大きい複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。  
  
 連結クエリとは、別のクエリをソースとして使用するクエリです。 たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
4  
```  
  
 この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>軸にリンクされたリストを反復処理すると同等のパフォーマンスに本質的にします</xref:System.Xml.Linq.XContainer.Elements%2A>。 <xref:System.Xml.Linq.XContainer.Elements%2A>遅延実行のある反復子として実装されます。</xref:System.Xml.Linq.XContainer.Elements%2A> つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。 この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の&2; つのカテゴリに分けることができます。 設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。  
  
-   `query1`、`Where`句によってクエリを呼び出して、<xref:System.Linq.Enumerable.Where%2A>メソッド</xref:System.Linq.Enumerable.Where%2A>。 このメソッドも反復子として実装されています。 設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。 反復ごとに、デリゲートが呼び出されて述語を実行します。 設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。  
  
-   `query1`、Select 句によってを呼び出すクエリ、<xref:System.Linq.Enumerable.Select%2A>メソッド</xref:System.Linq.Enumerable.Select%2A>。 このメソッドと同じパフォーマンス プロファイルには、<xref:System.Linq.Enumerable.Where%2A>メソッド</xref:System.Linq.Enumerable.Where%2A>。  
  
-   `query2` では、`Where` 句と `Select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。  
  
 したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
