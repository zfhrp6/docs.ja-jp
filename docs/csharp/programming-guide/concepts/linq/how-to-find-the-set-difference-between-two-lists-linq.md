---
title: '方法: 2 つのリストの差集合を見つける (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 8a0f7a06a226c0fee1f0174e187060e4b25faea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="fa8d5-102">方法: 2 つのリストの差集合を見つける (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fa8d5-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="fa8d5-103">この例では、LINQ を使用して、2 つの文字列リストを比較し、names2.txt ではなく names1.txt でそれらの行を出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fa8d5-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="fa8d5-104">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="fa8d5-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="fa8d5-105">「[方法: 文字列コレクションを結合および比較する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)」に示されているように、ソリューション フォルダーに names1.txt と names2.txt をコピーします。</span><span class="sxs-lookup"><span data-stu-id="fa8d5-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa8d5-106">例</span><span class="sxs-lookup"><span data-stu-id="fa8d5-106">Example</span></span>  
  
```csharp  
class CompareLists  
{          
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="fa8d5-107"><xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A>、および <xref:System.Linq.Enumerable.Concat%2A> など、C# のいくつかの種類のクエリ操作は、メソッド ベースの構文でのみ表すことができます。</span><span class="sxs-lookup"><span data-stu-id="fa8d5-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa8d5-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="fa8d5-108">Compiling the Code</span></span>  
 <span data-ttu-id="fa8d5-109">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="fa8d5-109">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8d5-110">参照</span><span class="sxs-lookup"><span data-stu-id="fa8d5-110">See Also</span></span>  
 [<span data-ttu-id="fa8d5-111">LINQ と文字列 (C#)</span><span class="sxs-lookup"><span data-stu-id="fa8d5-111">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
