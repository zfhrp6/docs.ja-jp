---
title: "方法: 文字列内の文字をクエリする (LINQ) (C#)"
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
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e78ad4aa493a7f58c43e77772138900e2b20b18a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="aea3a-102">方法: 文字列内の文字をクエリする (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aea3a-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="aea3a-103"><xref:System.String> クラスはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装しているため、任意の文字列を文字のシーケンスとしてクエリできます。</span><span class="sxs-lookup"><span data-stu-id="aea3a-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="aea3a-104">ただし、これは LINQ の一般的な使用方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="aea3a-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="aea3a-105">複雑なパターン一致操作には、<xref:System.Text.RegularExpressions.Regex> クラスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="aea3a-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aea3a-106">例</span><span class="sxs-lookup"><span data-stu-id="aea3a-106">Example</span></span>  
 <span data-ttu-id="aea3a-107">次の例では、文字列を対象にクエリを実行して、その文字列に含まれる数字の数を特定します。</span><span class="sxs-lookup"><span data-stu-id="aea3a-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="aea3a-108">クエリは、最初に使用された後も "再利用" されます。</span><span class="sxs-lookup"><span data-stu-id="aea3a-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="aea3a-109">これができるのは、クエリ自体には実際の結果が格納されないためです。</span><span class="sxs-lookup"><span data-stu-id="aea3a-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aea3a-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="aea3a-110">Compiling the Code</span></span>  
 <span data-ttu-id="aea3a-111">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="aea3a-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea3a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="aea3a-112">See Also</span></span>  
 <span data-ttu-id="aea3a-113">[LINQ と文字列 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="aea3a-113">[LINQ and Strings (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
 [<span data-ttu-id="aea3a-114">方法: LINQ クエリと正規表現を組み合わせる (C#)</span><span class="sxs-lookup"><span data-stu-id="aea3a-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)

