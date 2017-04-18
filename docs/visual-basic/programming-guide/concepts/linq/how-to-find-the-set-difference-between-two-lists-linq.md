---
title: "方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を見つける |Microsoft ドキュメント"
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
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2e67a03d5826d7d93e04b6c20a09cbbcabc8629
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を検索
この例では、LINQ を使用して、2 つの文字列のリストを比較し、names2.txt ではなく names1.txt でそれらの行を出力する方法を示します。  
  
### <a name="to-create-the-data-files"></a>データ ファイルを作成するには  
  
1.  ように names1.txt と names2.txt をソリューション フォルダーにコピー[方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)します。  
  
## <a name="example"></a>例  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 一部の種類のなどの Visual basic での操作のクエリ<xref:System.Linq.Enumerable.Except%2A>、 <xref:System.Linq.Enumerable.Distinct%2A>、 <xref:System.Linq.Enumerable.Union%2A>、および<xref:System.Linq.Enumerable.Concat%2A>、メソッド ベースの構文で表現できるのみです</xref:System.Linq.Enumerable.Concat%2A></xref:System.Linq.Enumerable.Union%2A></xref:System.Linq.Enumerable.Distinct%2A></xref:System.Linq.Enumerable.Except%2A>。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
