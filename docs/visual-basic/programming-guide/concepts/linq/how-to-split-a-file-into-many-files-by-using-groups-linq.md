---
title: "方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割 |Microsoft ドキュメント"
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
ms.assetid: 5e8b2a2b-0b1d-4933-8a2b-03e91dfaf77f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 753f4c5035a642175cf47a5b0af32158c3eb44dd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-split-a-file-into-many-files-by-using-groups-linq-visual-basic"></a><span data-ttu-id="5b961-102">方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割</span><span class="sxs-lookup"><span data-stu-id="5b961-102">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="5b961-103">この例では、2 つのファイルの内容をマージし、一連の新しい方法でデータを整理する新しいファイルを作成するための&1; つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b961-103">This example shows one way to merge the contents of two files and then create a set of new files that organize the data in a new way.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="5b961-104">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="5b961-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="5b961-105">Names1.txt という名前のテキスト ファイルに次の名前をコピーし、プロジェクト フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="5b961-105">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2.  <span data-ttu-id="5b961-106">プロジェクト フォルダーに次の名前をコピーし、names2.txt という名前のテキスト ファイルに保存します。 注&2; つのファイルがあるいくつかの共通の名前。</span><span class="sxs-lookup"><span data-stu-id="5b961-106">Copy these names into a text file that is named names2.txt and save it in your project folder: Note that the two files have some names in common.</span></span>  
  
    ```  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="5b961-107">例</span><span class="sxs-lookup"><span data-stu-id="5b961-107">Example</span></span>  
  
```vb  
Class SplitWithGroups  
  
    Shared Sub Main()  
  
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Concatenate and remove duplicate names based on  
        Dim mergeQuery As IEnumerable(Of String) = fileA.Union(fileB)  
  
        ' Group the names by the first letter in the last name  
        Dim groupQuery = From name In mergeQuery   
                     Let n = name.Split(New Char() {","})   
                     Order By n(0)   
                     Group By groupKey = n(0)(0)   
                     Into groupName = Group  
  
        ' Create a new file for each group that was created  
        ' Note that nested foreach loops are required to access  
        ' individual items with each group.  
        For Each gGroup In groupQuery  
            Dim fileName As String = "..'..'..'testFile_" & gGroup.groupKey & ".txt"  
            Dim sw As New System.IO.StreamWriter(fileName)  
            Console.WriteLine(gGroup.groupKey)  
            For Each item In gGroup.groupName  
                Console.WriteLine("   " & item.name)  
                sw.WriteLine(item.name)  
            Next  
            sw.Close()  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Files have been written. Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Class  
' Console Output:  
' A  
'    Aw, Kam Foo  
' B  
'    Bankov, Peter  
'    Beebe, Ann  
' E  
'    El Yassir, Mehdi  
' G  
'    Garcia, Hugo  
'    Garcia, Debra  
'    Giakoumakis, Leo  
'    Gilchrist, Beth  
'    Guy, Wey Yuan  
' H  
'    Holm, Michael  
' L  
'    Liu, Jinghao  
' M  
'    McLin, Nkenge  
'    Myrcha, Jacek  
' N  
'    Noriega, Fabricio  
' P  
'    Potra, Cristina  
' T  
'    Toyoshima, Tim  
```  
  
 <span data-ttu-id="5b961-108">プログラムでは、データ ファイルと同じフォルダー内の各グループの別のファイルを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5b961-108">The program writes a separate file for each group in the same folder as the data files.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5b961-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5b961-109">Compiling the Code</span></span>  
 <span data-ttu-id="5b961-110">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5b961-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b961-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b961-111">See Also</span></span>  
 <span data-ttu-id="5b961-112">[LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="5b961-112">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="5b961-113"> [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="5b961-113"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
