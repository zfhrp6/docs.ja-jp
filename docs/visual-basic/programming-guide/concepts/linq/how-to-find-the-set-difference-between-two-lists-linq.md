---
title: '方法: 2 つのリスト (LINQ) (Visual Basic) の差集合を検索'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 77ff74788adddcd28e23028b034cd682f2d94233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a><span data-ttu-id="43b8f-102">方法: 2 つのリスト (LINQ) (Visual Basic) の差集合を検索</span><span class="sxs-lookup"><span data-stu-id="43b8f-102">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="43b8f-103">この例では、LINQ を使用して、2 つの文字列リストを比較し、names2.txt ではなく names1.txt でそれらの行を出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43b8f-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="43b8f-104">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="43b8f-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="43b8f-105">Names1.txt と names2.txt は、のように、ソリューション フォルダーにコピー[する方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)です。</span><span class="sxs-lookup"><span data-stu-id="43b8f-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b8f-106">例</span><span class="sxs-lookup"><span data-stu-id="43b8f-106">Example</span></span>  
  
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
  
 <span data-ttu-id="43b8f-107">一部の種類のクエリ Visual basic での操作など<xref:System.Linq.Enumerable.Except%2A>、 <xref:System.Linq.Enumerable.Distinct%2A>、 <xref:System.Linq.Enumerable.Union%2A>、および<xref:System.Linq.Enumerable.Concat%2A>、メソッド ベースの構文でのみ公開できます。</span><span class="sxs-lookup"><span data-stu-id="43b8f-107">Some types of query operations in Visual Basic, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43b8f-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="43b8f-108">Compiling the Code</span></span>  
 <span data-ttu-id="43b8f-109">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll および System.Linq 名前空間の `Imports` ステートメントを参照設定します。</span><span class="sxs-lookup"><span data-stu-id="43b8f-109">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b8f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="43b8f-110">See Also</span></span>  
 [<span data-ttu-id="43b8f-111">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b8f-111">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
