---
title: "方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる |Microsoft ドキュメント"
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
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
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
ms.openlocfilehash: bda25acd3065898eeb61dce83d46d7526e825add
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="6af03-102">方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる</span><span class="sxs-lookup"><span data-stu-id="6af03-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="6af03-103">この例では、指定したフォルダー内のすべてのファイルとそのすべてのサブフォルダーで使用されるバイトの総数を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6af03-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af03-104">例</span><span class="sxs-lookup"><span data-stu-id="6af03-104">Example</span></span>  
 <span data-ttu-id="6af03-105"><xref:System.Linq.Enumerable.Sum%2A>メソッドを追加で選択されているすべてのアイテムの値、`select`句</xref:System.Linq.Enumerable.Sum%2A>。</span><span class="sxs-lookup"><span data-stu-id="6af03-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="6af03-106"><xref:System.Linq.Enumerable.Min%2A>または<xref:System.Linq.Enumerable.Max%2A><xref:System.Linq.Enumerable.Sum%2A>。</xref:System.Linq.Enumerable.Sum%2A>の代わりにメソッド</xref:System.Linq.Enumerable.Max%2A></xref:System.Linq.Enumerable.Min%2A>を呼び出すことによって指定されたディレクトリ ツリー内の最大または最小のファイルを取得するには、このクエリを簡単に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="6af03-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
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
  
 <span data-ttu-id="6af03-107">指定したディレクトリ ツリー内のバイト数をカウントするした場合これより効率的にデータ ソースとしてリスト コレクションを作成するオーバーヘッドが発生し、LINQ クエリを作成しなくても実行できます。</span><span class="sxs-lookup"><span data-stu-id="6af03-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="6af03-108">LINQ アプローチの有用性は、クエリがより複雑なまたは同じデータ ソースに対して複数のクエリを実行するときに増加します。</span><span class="sxs-lookup"><span data-stu-id="6af03-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="6af03-109">クエリは、ファイル長を取得する別のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6af03-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="6af03-110">これは、ファイルが別のスレッドの後で削除された場合に発生する例外を使用するために、<xref:System.IO.FileInfo>への呼び出しでオブジェクトが作成された`GetFiles`</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="6af03-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="6af03-111">にもかかわらず、<xref:System.IO.FileInfo>オブジェクトが既に作成されて、例外が発生する可能性があるため、<xref:System.IO.FileInfo>オブジェクトは、更新しようとしますその<xref:System.IO.FileInfo.Length%2A>プロパティへのアクセスは、最初に、最新の長さを持つプロパティです。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 。</span><span class="sxs-lookup"><span data-stu-id="6af03-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="6af03-112">クエリの外部の try-catch ブロックでこの操作を配置することでコードは、副作用を引き起こす可能性のあるクエリでの操作を防ぐためのルールに従います。</span><span class="sxs-lookup"><span data-stu-id="6af03-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="6af03-113">一般に、アプリケーションが不明な状態で残っていないことを確認する例外を処理する時は、十分な注意を考慮しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6af03-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6af03-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6af03-114">Compiling the Code</span></span>  
 <span data-ttu-id="6af03-115">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6af03-115">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a   `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af03-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6af03-116">See Also</span></span>  
 <span data-ttu-id="6af03-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="6af03-117">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="6af03-118"> [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="6af03-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
