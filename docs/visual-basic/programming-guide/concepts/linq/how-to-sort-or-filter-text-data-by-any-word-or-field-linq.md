---
title: "方法: 任意の単語またはフィールド (LINQ) (Visual Basic) でのフィルター テキスト データの並べ替えまたは |Microsoft ドキュメント"
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
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
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
ms.openlocfilehash: e13cdc32b40f1c16d4c8fa27f3c3af15a80c33d7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="565ad-102">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ad-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="565ad-103">次の例では、行の任意のフィールドのコンマ区切りの値などの構造化テキストの行を並べ替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="565ad-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="565ad-104">フィールドは、実行時に動的に指定可能性があります。</span><span class="sxs-lookup"><span data-stu-id="565ad-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="565ad-105">Scores.csv 内のフィールドが区切られた&4; つの試験の点数の一連のスチューデントの ID 番号を表すことを想定しています。</span><span class="sxs-lookup"><span data-stu-id="565ad-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="565ad-106">データを含むファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="565ad-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="565ad-107">トピックから scores.csv データをコピー[方法: コンテンツを結合から複数の異なるファイル (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)し、ソリューション フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="565ad-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="565ad-108">例</span><span class="sxs-lookup"><span data-stu-id="565ad-108">Example</span></span>  
  
```vb  
Class SortLines  
  
    Shared Sub Main()  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' Change this to any value from 0 to 4  
        Dim sortField As Integer = 1  
  
        Console.WriteLine("Sorted highest to lowest by field " & sortField)  
  
        ' Demonstrates how to return query from a method.  
        ' The query is executed here.  
        For Each str As String In SortQuery(scores, sortField)  
            Console.WriteLine(str)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    Shared Function SortQuery(  
        ByVal source As IEnumerable(Of String),   
        ByVal num As Integer) As IEnumerable(Of String)  
  
        Dim scoreQuery = From line In source   
                         Let fields = line.Split(New Char() {","})   
                         Order By fields(num) Descending   
                         Select line  
  
        Return scoreQuery  
    End Function  
End Class  
' Output:  
' Sorted highest to lowest by field 1  
' 116, 99, 86, 90, 94  
' 120, 99, 82, 81, 79  
' 111, 97, 92, 81, 60  
' 114, 97, 89, 85, 82  
' 121, 96, 85, 91, 60  
' 122, 94, 92, 91, 91  
' 117, 93, 92, 80, 87  
' 118, 92, 90, 83, 78  
' 113, 88, 94, 65, 91  
' 112, 75, 84, 91, 39  
' 119, 68, 79, 88, 92  
' 115, 35, 72, 91, 70  
```  
  
 <span data-ttu-id="565ad-109">この例では、関数から、クエリ変数を取得する方法についても示します。</span><span class="sxs-lookup"><span data-stu-id="565ad-109">This example also demonstrates how to return a query variable from a Function.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="565ad-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="565ad-110">Compiling the Code</span></span>  
 <span data-ttu-id="565ad-111">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="565ad-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565ad-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="565ad-112">See Also</span></span>  
 [<span data-ttu-id="565ad-113">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="565ad-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
