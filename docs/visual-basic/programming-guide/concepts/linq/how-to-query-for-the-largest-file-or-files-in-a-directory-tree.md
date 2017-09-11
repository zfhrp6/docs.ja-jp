---
title: "方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会 |Microsoft ドキュメント"
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
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
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
ms.openlocfilehash: 95c5197b2cb66745201ceac89b78fe67b95ecb75
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="b40ba-102">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b40ba-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="b40ba-103">この例では、ファイルのサイズ (バイト単位) に関連する&5; つのクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="b40ba-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="b40ba-104">最大ファイルのバイト単位のサイズを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="b40ba-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="b40ba-105">最も小さいファイルのバイト単位のサイズを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="b40ba-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="b40ba-106">取得する方法、 <xref:System.IO.FileInfo>、指定したルート フォルダーの下の&1; つまたは複数のフォルダーから、オブジェクトの最大値または最小ファイル</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="b40ba-107">10 個のファイルなどのシーケンスを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="b40ba-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="b40ba-108">指定したサイズよりも小さいファイルを無視して、ファイル サイズ (バイト単位) に基づくグループにファイルを注文する方法。</span><span class="sxs-lookup"><span data-stu-id="b40ba-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b40ba-109">例</span><span class="sxs-lookup"><span data-stu-id="b40ba-109">Example</span></span>  
 <span data-ttu-id="b40ba-110">次の例には、クエリを実行する方法と、ファイル サイズ (バイト単位) に応じて、グループのファイルを表示する&5; つの独立したクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b40ba-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="b40ba-111">これらの例をいくつかの他のプロパティの基にクエリを簡単に変更することができます、<xref:System.IO.FileInfo>オブジェクト</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="b40ba-112">1 つまたは複数の完了を返す<xref:System.IO.FileInfo>オブジェクトの場合、クエリは最初に&1; つずつでデータを調べる必要がありますソースで実行され、Length プロパティの値で並べ替えます</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="b40ba-113">1 つまたはシーケンスの最大の長さを返すことできます。</span><span class="sxs-lookup"><span data-stu-id="b40ba-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="b40ba-114">使用<xref:System.Linq.Enumerable.First%2A>をリスト内の最初の要素を返します</xref:System.Linq.Enumerable.First%2A>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="b40ba-115">使用する<xref:System.Linq.Enumerable.Take%2A>要素の最初の n の数を返します</xref:System.Linq.Enumerable.Take%2A>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="b40ba-116">リストの先頭にある最も小さい要素を配置する降順の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="b40ba-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="b40ba-117">クエリの場合は、ファイルが以降の時間内に別のスレッドで削除された場所に表示されるだけは例外を使用するために、ファイル サイズ (バイト単位) を取得する個別のメソッドを呼び出す、<xref:System.IO.FileInfo>への呼び出しでオブジェクトが作成された`GetFiles`</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="b40ba-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="b40ba-118"><xref:System.IO.FileInfo>オブジェクトが既に作成されて、例外が発生する可能性があるため、<xref:System.IO.FileInfo>オブジェクトは、更新しようとしますその<xref:System.IO.FileInfo.Length%2A>初めてプロパティにアクセス (バイト単位) の最新のサイズを使用してプロパティ。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 。</span><span class="sxs-lookup"><span data-stu-id="b40ba-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="b40ba-119">クエリの外部の try-catch ブロックでこの操作を配置することで、副作用を引き起こす可能性のあるクエリでの操作を防ぐための規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="b40ba-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="b40ba-120">一般に、十分な注意する必要があります、例外を使用するときにために実行するアプリケーションが不明な状態で残っていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b40ba-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b40ba-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b40ba-121">Compiling the Code</span></span>  
 <span data-ttu-id="b40ba-122">.NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b40ba-122">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40ba-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b40ba-123">See Also</span></span>  
 <span data-ttu-id="b40ba-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="b40ba-124">[LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="b40ba-125"> [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span><span class="sxs-lookup"><span data-stu-id="b40ba-125"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)</span></span>
