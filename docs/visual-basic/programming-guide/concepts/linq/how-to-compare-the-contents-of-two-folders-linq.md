---
title: "方法: 2 つのフォルダー (LINQ) (Visual Basic) の内容の比較"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a65b5f74e872cb4d2e459bc7ff866ca332706ef9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="bbe34-102">方法: 2 つのフォルダー (LINQ) (Visual Basic) の内容の比較</span><span class="sxs-lookup"><span data-stu-id="bbe34-102">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="bbe34-103">この例では、2 つのファイル リストを比較する 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bbe34-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
-   <span data-ttu-id="bbe34-104">2 つのファイル リストが同一であるかどうかを指定するブール値をクエリする方法</span><span class="sxs-lookup"><span data-stu-id="bbe34-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
-   <span data-ttu-id="bbe34-105">両方のフォルダー内にあるファイルを取得するために、共通部分をクエリする方法</span><span class="sxs-lookup"><span data-stu-id="bbe34-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
-   <span data-ttu-id="bbe34-106">1 つのフォルダーにあり、もう 1 つのフォルダーにはないファイルを取得するために、差集合をクエリする方法</span><span class="sxs-lookup"><span data-stu-id="bbe34-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bbe34-107">ここに示す方法は、任意の型のオブジェクトのシーケンスを比較するために適用させることができます。</span><span class="sxs-lookup"><span data-stu-id="bbe34-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="bbe34-108">ここに示す `FileComparer` クラスは、標準クエリ演算子と共に、カスタム比較演算子クラスを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bbe34-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="bbe34-109">このクラスは、実際のシナリオで使用することは想定されていません。</span><span class="sxs-lookup"><span data-stu-id="bbe34-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="bbe34-110">各フォルダーの内容が同一であるかどうかを判断するために、各ファイルの名前と長さ (バイト) を使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="bbe34-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="bbe34-111">実際のシナリオでは、この比較演算子を変更して、より厳密に等しいかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="bbe34-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbe34-112">例</span><span class="sxs-lookup"><span data-stu-id="bbe34-112">Example</span></span>  
  
```vb  
Module CompareDirs  
    Public Sub Main()  
  
        ' Create two identical or different temporary folders   
        ' on a local drive and add files to them.  
        ' Then set these file paths accordingly.  
        Dim pathA As String = "C:\TestDir"  
        Dim pathB As String = "C:\TestDir2"  
  
        ' Take a snapshot of the file system.   
        Dim dir1 As New System.IO.DirectoryInfo(pathA)  
        Dim dir2 As New System.IO.DirectoryInfo(pathB)  
  
        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the FileCompare object we'll use in each query  
        Dim myFileCompare As New FileCompare  
  
        ' This query determines whether the two folders contain  
        ' identical file lists, based on the custom file comparer  
        ' that is defined in the FileCompare class.  
        ' The query executes immediately because it returns a bool.  
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)  
        If areIdentical = True Then  
            Console.WriteLine("The two folders are the same.")  
        Else  
            Console.WriteLine("The two folders are not the same.")  
        End If  
  
        ' Find common files in both folders. It produces a sequence and doesn't execute  
        ' until the foreach statement.  
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)  
  
        If queryCommonFiles.Count() > 0 Then  
  
            Console.WriteLine("The following files are in both folders:")  
            For Each fi As System.IO.FileInfo In queryCommonFiles  
                Console.WriteLine(fi.FullName)  
            Next  
        Else  
            Console.WriteLine("There are no common files in the two folders.")  
        End If  
  
        ' Find the set difference between the two folders.  
        ' For this example we only check one way.  
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)  
        Console.WriteLine("The following files are in dirA but not dirB:")  
        For Each fi As System.IO.FileInfo In queryDirAOnly  
            Console.WriteLine(fi.FullName)  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This implementation defines a very simple comparison  
    ' between two FileInfo objects. It only compares the name  
    ' of the files being compared and their length in bytes.  
    Public Class FileCompare  
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)  
  
        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _  
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals  
  
            If (x.Name = y.Name) And (x.Length = y.Length) Then  
                Return True  
            Else  
                Return False  
            End If  
        End Function  
  
        ' Return a hash that reflects the comparison criteria. According to the   
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must  
        ' also be equal. Because equality as defined here is a simple value equality, not  
        ' reference identity, it is possible that two or more objects will produce the same  
        ' hash code.  
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _  
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode  
            Dim s As String = fi.Name & fi.Length  
            Return s.GetHashCode()  
        End Function  
    End Class  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbe34-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bbe34-113">Compiling the Code</span></span>  
 <span data-ttu-id="bbe34-114">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll および System.Linq 名前空間の `Imports` ステートメントを参照設定します。</span><span class="sxs-lookup"><span data-stu-id="bbe34-114">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe34-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbe34-115">See Also</span></span>  
 [<span data-ttu-id="bbe34-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbe34-116">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="bbe34-117">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbe34-117">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
