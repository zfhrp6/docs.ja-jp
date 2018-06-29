---
title: '方法: 複数のソース (LINQ) (Visual Basic) からオブジェクトのコレクションへの追加'
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: 6560f853874f9b9a9aeb53bd0678540004fdfcc1
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37070864"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="f2594-102">方法: 複数のソース (LINQ) (Visual Basic) からオブジェクトのコレクションへの追加</span><span class="sxs-lookup"><span data-stu-id="f2594-102">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="f2594-103">この例では、さまざまなソースから一連の新しい型にデータをマージする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f2594-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="f2594-104">データベースに残っているデータをファイル システムでメモリ内データまたはデータへの参加しないでください。</span><span class="sxs-lookup"><span data-stu-id="f2594-104">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="f2594-105">このようなドメイン間結合を行うと、データベース クエリと他の種類のソースとで結合操作の定義方法に違いがあることが原因で、結果が未定義になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f2594-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="f2594-106">また、データベース内に大量のデータが存在すると、こうした操作によってメモリ不足例外が発生するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="f2594-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="f2594-107">データベースのデータをメモリ内データに結合するには、まずデータベース クエリで `ToList` または `ToArray` を呼び出してから、返されたコレクションで結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="f2594-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="f2594-108">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2594-108">To create the data file</span></span>

- <span data-ttu-id="f2594-109">説明に従って、プロジェクトのフォルダーに、names.csv および scores.csv ファイルをコピー[する方法: Join コンテンツから複数の異なるファイル (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2594-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2594-110">例</span><span class="sxs-lookup"><span data-stu-id="f2594-110">Example</span></span>

<span data-ttu-id="f2594-111">次の例は、2 つのメモリ内文字列コレクションからマージされたデータを、名前付きの型 `Student` を使用して格納する方法を示しています。各コレクションは、.csv 形式のスプレッドシート データをシミュレートしています。</span><span class="sxs-lookup"><span data-stu-id="f2594-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="f2594-112">1 つ目の文字列コレクションは学生の名前と ID を表し、2 つ目のコレクションは学生 ID (最初の列) と 4 つの試験の点数を表しています。</span><span class="sxs-lookup"><span data-stu-id="f2594-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="f2594-113">外部キーとして ID が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2594-113">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Omelchenko Svetlana is 82.5
' The average score of O'Donnell Claire is 72.25
' The average score of Mortensen Sven is 84.5
' The average score of Garcia Cesar is 88.25
' The average score of Garcia Debra is 67
' The average score of Fakhouri Fadi is 92.25
' The average score of Feng Hanying is 88
' The average score of Garcia Hugo is 85.75
' The average score of Tucker Lance is 81.75
' The average score of Adams Terry is 85.25
' The average score of Zabokritski Eugene is 83
' The average score of Tucker Michael is 92
```

<span data-ttu-id="f2594-114">[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)句、オブジェクト初期化子を使ってそれぞれの新しいインスタンスを作成する`Student`2 つのソースからデータを使用してオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f2594-114">In the [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="f2594-115">クエリの結果を格納することも、匿名型は名前付きの型よりも簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="f2594-115">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="f2594-116">クエリが実行されたメソッドの外部にクエリ結果を渡す場合は、名前付きの型が必要になります。</span><span class="sxs-lookup"><span data-stu-id="f2594-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="f2594-117">次の例では、前の例と同じタスクを実行しますが、名前付きの型ではなく匿名型が使用します。</span><span class="sxs-lookup"><span data-stu-id="f2594-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="compiling-the-code"></a><span data-ttu-id="f2594-118">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f2594-118">Compiling the code</span></span>

<span data-ttu-id="f2594-119">作成し、次のオプションのいずれかを対象とするプロジェクトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f2594-119">Create and compile a project that targets one of the following options:</span></span>

- <span data-ttu-id="f2594-120">.NET framework バージョン 3.5 System.Core.dll への参照。</span><span class="sxs-lookup"><span data-stu-id="f2594-120">.NET Framework version 3.5 with a reference to System.Core.dll.</span></span>
- <span data-ttu-id="f2594-121">.NET framework 4.0 またはそれ以降のバージョン。</span><span class="sxs-lookup"><span data-stu-id="f2594-121">.NET Framework version 4.0 or higher.</span></span>
- <span data-ttu-id="f2594-122">.NET core バージョン 1.0 以降。</span><span class="sxs-lookup"><span data-stu-id="f2594-122">.NET Core version 1.0 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2594-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2594-123">See also</span></span>

[<span data-ttu-id="f2594-124">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2594-124">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
