---
title: "方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会 |Microsoft ドキュメント"
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
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
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
ms.openlocfilehash: 31561d586c9c05f502002efdfc455acb55159fed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a>方法 : 指定された単語のセットを含む文章を照会する (LINQ) (Visual Basic)
この例では、各単語の指定されたセットに一致するものを含むテキスト ファイルに文を検索する方法を示します。 検索語句の配列では、この例では、ハードコーディングは、その可能性がありますも作成される動的に実行時にします。 この例では、クエリを「従来、」という単語を含む文章を返します。"データ"と"統合"です。  
  
## <a name="example"></a>例  
  
```vb  
Class FindSentences  
  
    Shared Sub Main()  
        Dim text As String = "Historically, the world of data and the world of objects " &   
        "have not been well integrated. Programmers work in C# or Visual Basic " &   
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &   
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &   
        "are tables, columns, rows, nodes, and separate languages for dealing with " &   
        "them. Data types often require translation between the two worlds; there are " &   
        "different standard functions. Because the object world has no notion of query, a " &   
        "query can only be represented as a string without compile-time type checking or " &   
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &   
        "objects in memory is often tedious and error-prone."  
  
        ' Split the text block into an array of sentences.  
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})  
  
        ' Define the search terms. This list could also be dynamically populated at runtime  
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}  
  
        ' Find sentences that contain all the terms in the wordsToMatch array  
        ' Note that the number of terms to match is not specified at compile time  
        Dim sentenceQuery = From sentence In sentences   
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                   StringSplitOptions.RemoveEmptyEntries)   
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()   
                            Select sentence  
  
        ' Execute the query  
        For Each str As String In sentenceQuery  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Class  
' Output:  
' Historically, the world of data and the world of objects have not been well integrated  
```  
  
 クエリは、まず、テキストを文に分割したり、文章を分割して各単語を含む文字列の配列にによって機能します。 これらの配列の各、<xref:System.Linq.Enumerable.Distinct%2A>メソッドは、すべての重複する単語を削除し、クエリを実行、<xref:System.Linq.Enumerable.Intersect%2A>単語の配列で操作し、`wordsToMatch`配列</xref:System.Linq.Enumerable.Intersect%2A></xref:System.Linq.Enumerable.Distinct%2A>。 交差する位置の数が数と同じかどうか、`wordsToMatch`配列、言葉で検出されたすべての単語と、元の文章が返されます。  
  
 呼び出しで<xref:System.String.Split%2A>、区切り記号は、文字列から削除するために区切り記号として使用されます</xref:System.String.Split%2A>。 場合なら、文字列「従来」例については、これを実行するいると一致しません「従来」で、`wordsToMatch`配列。 ソース テキストに見つかった区切り記号の種類に応じて、追加の区切り記号を使用する必要があります。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
