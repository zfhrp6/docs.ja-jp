---
title: "方法: 文字列 (LINQ) (Visual Basic) での単語の出現回数をカウント |Microsoft ドキュメント"
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
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5697e52729287a09f1afe993c7b1c1d0c9a6507b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="d7574-102">方法: 文字列 (LINQ) (Visual Basic) での単語の出現回数をカウント</span><span class="sxs-lookup"><span data-stu-id="d7574-102">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="d7574-103">この例では、LINQ クエリを使用して、文字列内の指定した単語の出現回数をカウントする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d7574-103">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="d7574-104">最初に、カウントを実行することに注意してください、<xref:System.String.Split%2A>単語の配列を作成するメソッドが呼び出されます</xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="d7574-104">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="d7574-105">パフォーマンス コストは、<xref:System.String.Split%2A>メソッド</xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="d7574-105">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="d7574-106">単語数をカウントする、文字列に対してのみ操作がある場合は、使用を検討する必要があります、<xref:System.Text.RegularExpressions.Regex.Matches%2A>または<xref:System.String.IndexOf%2A>メソッド代わりにします</xref:System.String.IndexOf%2A></xref:System.Text.RegularExpressions.Regex.Matches%2A>。</span><span class="sxs-lookup"><span data-stu-id="d7574-106">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="d7574-107">ただし、パフォーマンスが重大な問題ではない、または上にあるその他の種類のクエリを実行するために、センテンスを既に分割した場合、し理にかなって LINQ を使用して単語や語句もをカウントします。</span><span class="sxs-lookup"><span data-stu-id="d7574-107">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7574-108">例</span><span class="sxs-lookup"><span data-stu-id="d7574-108">Example</span></span>  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7574-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d7574-109">Compiling the Code</span></span>  
 <span data-ttu-id="d7574-110">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d7574-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7574-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7574-111">See Also</span></span>  
 [<span data-ttu-id="d7574-112">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7574-112">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
