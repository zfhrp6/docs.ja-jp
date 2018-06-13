---
title: '方法: 文字列内の文字をクエリする (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: db535f55822fa40d8589ddf95f9f78adfa1b6f1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323080"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="66bb9-102">方法: 文字列内の文字をクエリする (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="66bb9-102">How to: Query for Characters in a String (LINQ) (C#)</span></span>
<span data-ttu-id="66bb9-103"><xref:System.String> クラスはジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装しているため、任意の文字列を文字のシーケンスとしてクエリできます。</span><span class="sxs-lookup"><span data-stu-id="66bb9-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="66bb9-104">ただし、これは LINQ の一般的な使用方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="66bb9-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="66bb9-105">複雑なパターン一致操作には、<xref:System.Text.RegularExpressions.Regex> クラスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="66bb9-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66bb9-106">例</span><span class="sxs-lookup"><span data-stu-id="66bb9-106">Example</span></span>  
 <span data-ttu-id="66bb9-107">次の例では、文字列を対象にクエリを実行して、その文字列に含まれる数字の数を特定します。</span><span class="sxs-lookup"><span data-stu-id="66bb9-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="66bb9-108">クエリは、最初に使用された後も "再利用" されます。</span><span class="sxs-lookup"><span data-stu-id="66bb9-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="66bb9-109">これができるのは、クエリ自体には実際の結果が格納されないためです。</span><span class="sxs-lookup"><span data-stu-id="66bb9-109">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="66bb9-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="66bb9-110">Compiling the Code</span></span>  
 <span data-ttu-id="66bb9-111">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="66bb9-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66bb9-112">参照</span><span class="sxs-lookup"><span data-stu-id="66bb9-112">See Also</span></span>  
 [<span data-ttu-id="66bb9-113">LINQ と文字列 (C#)</span><span class="sxs-lookup"><span data-stu-id="66bb9-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="66bb9-114">方法: LINQ クエリと正規表現を組み合わせる (C#)</span><span class="sxs-lookup"><span data-stu-id="66bb9-114">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
