---
title: "方法: 一連のフォルダーの合計バイト数を照会する (LINQ) (C#)"
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
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
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
ms.openlocfilehash: 7eabb1b04a708e0b6f443552cdb07540b4d970dc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="eb200-102">方法: 一連のフォルダーの合計バイト数を照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="eb200-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>
<span data-ttu-id="eb200-103">この例では、指定したフォルダーとそのすべてのサブフォルダーに格納されている全ファイルの合計バイト数を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eb200-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb200-104">例</span><span class="sxs-lookup"><span data-stu-id="eb200-104">Example</span></span>  
 <span data-ttu-id="eb200-105"><xref:System.Linq.Enumerable.Sum%2A> は、`select` 句で選択されたすべての項目の値を加算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="eb200-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="eb200-106">このクエリに少し変更を加え、<xref:System.Linq.Enumerable.Sum%2A> の代わりに <xref:System.Linq.Enumerable.Min%2A> メソッドまたは <xref:System.Linq.Enumerable.Max%2A> メソッドを呼び出せば、指定したディレクトリ ツリーの最大ファイルまたは最小ファイルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="eb200-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="eb200-107">指定したディレクトリ ツリー内のバイト数をカウントするだけならば、LINQ クエリを作成せずに行う方が効率的です。LINQ クエリでは、データ ソースとしてリスト コレクションを作成する際のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="eb200-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="eb200-108">LINQ を使ったアプローチは、クエリが複雑化するか、同じデータ ソースに対して複数のクエリを実行する必要があるときに利便性が増します。</span><span class="sxs-lookup"><span data-stu-id="eb200-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="eb200-109">このクエリは、ファイルの長さを取得するために別のメソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="eb200-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="eb200-110">その理由は、`GetFiles` の呼び出しで <xref:System.IO.FileInfo> オブジェクトが作成された後に別のスレッドでファイルが削除された場合に発生する可能性のある例外を処理するためです。</span><span class="sxs-lookup"><span data-stu-id="eb200-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="eb200-111"><xref:System.IO.FileInfo> オブジェクトの作成後であっても、例外は発生する可能性があります。<xref:System.IO.FileInfo> オブジェクトは、<xref:System.IO.FileInfo.Length%2A> プロパティが最初にアクセスされたときに最新の長さに基づいてそのプロパティを更新しようと試みるためです。</span><span class="sxs-lookup"><span data-stu-id="eb200-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="eb200-112">この操作をクエリの外側の try-catch ブロックに置くことで、"副作用の原因となりうるような操作はクエリ内では行わない" という原則に従っているのです。</span><span class="sxs-lookup"><span data-stu-id="eb200-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="eb200-113">一般に、アプリケーションが不明な状態に陥ることのないよう、例外を処理する際には十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb200-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb200-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="eb200-114">Compiling the Code</span></span>  
 <span data-ttu-id="eb200-115">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="eb200-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb200-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb200-116">See Also</span></span>  
 <span data-ttu-id="eb200-117">[LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="eb200-117">[LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
 [<span data-ttu-id="eb200-118">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="eb200-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)

