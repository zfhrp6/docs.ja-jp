---
title: '方法: クエリ (LINQ) (Visual Basic) のフォルダー内のファイルの内容'
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: e0f5e07065ebe210a927491a3f55f891f9934e60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="f58e3-102">方法: クエリ (LINQ) (Visual Basic) のフォルダー内のファイルの内容</span><span class="sxs-lookup"><span data-stu-id="f58e3-102">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="f58e3-103">この例では、指定したディレクトリ ツリーに含まれるすべてのファイルを照会し、個々のファイルを開いて、その内容を調べています。</span><span class="sxs-lookup"><span data-stu-id="f58e3-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="f58e3-104">同様の手法を使えば、ディレクトリ ツリーの内容に対するインデックスや逆インデックスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f58e3-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="f58e3-105">この例で行っているのは単純な文字列検索です。</span><span class="sxs-lookup"><span data-stu-id="f58e3-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="f58e3-106">しかし正規表現を使うと、もっと複雑なパターン マッチングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f58e3-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="f58e3-107">詳細については、次を参照してください。[する方法: 正規表現 (Visual Basic) での LINQ クエリの結合](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="f58e3-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f58e3-108">例</span><span class="sxs-lookup"><span data-stu-id="f58e3-108">Example</span></span>  
  
```vb  
Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "c:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        Dim searchTerm = "Visual Studio"  
  
        ' Search the contents of each file.  
        ' A regular expression created with the RegEx class  
        ' could be used instead of the Contains method.  
        Dim queryMatchingFiles = From file In fileList _  
                                 Where file.Extension = ".htm" _  
                                 Let fileText = GetFileText(file.FullName) _  
                                 Where fileText.Contains(searchTerm) _  
                                 Select file.FullName  
  
        Console.WriteLine("The term " & searchTerm & " was found in:")  
  
        ' Execute the query.  
        For Each filename In queryMatchingFiles  
            Console.WriteLine(filename)  
        Next  
  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit")  
        Console.ReadKey()  
  
    End Sub  
  
    ' Read the contents of the file. This is done in a separate  
    ' function in order to handle potential file system errors.  
    Function GetFileText(ByVal name As String) As String  
  
        ' If the file has been deleted, the right thing  
        ' to do in this case is return an empty string.  
        Dim fileContents = String.Empty  
  
        ' If the file has been deleted since we took   
        ' the snapshot, ignore it and return the empty string.  
        If System.IO.File.Exists(name) Then  
            fileContents = System.IO.File.ReadAllText(name)  
        End If  
  
        Return fileContents  
  
    End Function  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f58e3-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f58e3-109">Compiling the Code</span></span>  
 <span data-ttu-id="f58e3-110">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll および System.Linq 名前空間の `Imports` ステートメントを参照設定します。</span><span class="sxs-lookup"><span data-stu-id="f58e3-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58e3-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f58e3-111">See Also</span></span>  
 [<span data-ttu-id="f58e3-112">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f58e3-112">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="f58e3-113">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f58e3-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
