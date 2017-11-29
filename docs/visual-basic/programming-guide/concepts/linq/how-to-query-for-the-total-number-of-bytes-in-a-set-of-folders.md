---
title: "方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数をクエリ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b200581f4876400727c63e86e3ccf4a44c67914b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="d82d3-102">方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数をクエリ</span><span class="sxs-lookup"><span data-stu-id="d82d3-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="d82d3-103">この例では、指定したフォルダーとそのすべてのサブフォルダーに格納されている全ファイルの合計バイト数を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d82d3-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82d3-104">例</span><span class="sxs-lookup"><span data-stu-id="d82d3-104">Example</span></span>  
 <span data-ttu-id="d82d3-105"><xref:System.Linq.Enumerable.Sum%2A> は、`select` 句で選択されたすべての項目の値を加算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d82d3-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="d82d3-106">このクエリに少し変更を加え、<xref:System.Linq.Enumerable.Sum%2A> の代わりに <xref:System.Linq.Enumerable.Min%2A> メソッドまたは <xref:System.Linq.Enumerable.Max%2A> メソッドを呼び出せば、指定したディレクトリ ツリーの最大ファイルまたは最小ファイルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="d82d3-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="d82d3-107">指定したディレクトリ ツリー内のバイト数をカウントするだけならば、LINQ クエリを作成せずに行う方が効率的です。LINQ クエリでは、データ ソースとしてリスト コレクションを作成する際のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="d82d3-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="d82d3-108">LINQ を使ったアプローチは、クエリが複雑化するか、同じデータ ソースに対して複数のクエリを実行する必要があるときに利便性が増します。</span><span class="sxs-lookup"><span data-stu-id="d82d3-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="d82d3-109">このクエリは、ファイルの長さを取得するために別のメソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="d82d3-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="d82d3-110">その理由は、`GetFiles` の呼び出しで <xref:System.IO.FileInfo> オブジェクトが作成された後に別のスレッドでファイルが削除された場合に発生する可能性のある例外を処理するためです。</span><span class="sxs-lookup"><span data-stu-id="d82d3-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="d82d3-111"><xref:System.IO.FileInfo> オブジェクトの作成後であっても、例外は発生する可能性があります。<xref:System.IO.FileInfo> オブジェクトは、<xref:System.IO.FileInfo.Length%2A> プロパティが最初にアクセスされたときに最新の長さに基づいてそのプロパティを更新しようと試みるためです。</span><span class="sxs-lookup"><span data-stu-id="d82d3-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="d82d3-112">この操作をクエリの外側の try-catch ブロックに置くことで、"副作用の原因となりうるような操作はクエリ内では行わない" という原則に従っているのです。</span><span class="sxs-lookup"><span data-stu-id="d82d3-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="d82d3-113">一般に、アプリケーションが不明な状態に陥ることのないよう、例外を処理する際には十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="d82d3-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d82d3-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d82d3-114">Compiling the Code</span></span>  
 <span data-ttu-id="d82d3-115">.NET Framework version 3.5 以降では、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメント。</span><span class="sxs-lookup"><span data-stu-id="d82d3-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82d3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d82d3-116">See Also</span></span>  
 [<span data-ttu-id="d82d3-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d82d3-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="d82d3-118">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d82d3-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
