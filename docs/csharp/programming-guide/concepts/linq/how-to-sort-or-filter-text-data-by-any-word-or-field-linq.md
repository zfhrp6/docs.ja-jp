---
title: "方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)"
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
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b074f6f1a1c1e2e6528ed1e63ccbdff57057f374
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="422d2-102">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="422d2-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="422d2-103">次の例では、コンマ区切り値などの構造化されたテキストの行を、行の任意のフィールドで並べ替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="422d2-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="422d2-104">フィールドは、実行時に動的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="422d2-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="422d2-105">scores.csv 内のフィールドは、学生の ID 番号と、それに続く 4 つのテストの点を表しているものとします。</span><span class="sxs-lookup"><span data-stu-id="422d2-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="422d2-106">データを含むファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="422d2-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="422d2-107">「[方法: 異種ファイルのコンテンツを結合する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)」トピックから scores.csv のデータをコピーし、ソリューション フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="422d2-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="422d2-108">例</span><span class="sxs-lookup"><span data-stu-id="422d2-108">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="422d2-109">この例では、メソッドからクエリ変数を返す方法についても示します。</span><span class="sxs-lookup"><span data-stu-id="422d2-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="422d2-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="422d2-110">Compiling the Code</span></span>  
 <span data-ttu-id="422d2-111">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="422d2-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="422d2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="422d2-112">See Also</span></span>  
 [<span data-ttu-id="422d2-113">LINQ と文字列 (C#)</span><span class="sxs-lookup"><span data-stu-id="422d2-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)

