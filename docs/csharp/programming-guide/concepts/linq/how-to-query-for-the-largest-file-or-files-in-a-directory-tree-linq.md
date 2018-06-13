---
title: '方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 20c8a917-0552-4514-b489-0b8b6a4c3b4c
ms.openlocfilehash: 004726c4df1af5a12a411d26c4dc36e1836597ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325358"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="2d177-102">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2d177-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>
<span data-ttu-id="2d177-103">この例では、ファイル サイズ (バイト単位) に関連した 5 つのクエリを紹介しています。</span><span class="sxs-lookup"><span data-stu-id="2d177-103">This example shows five queries related to file size in bytes:</span></span>  
  
-   <span data-ttu-id="2d177-104">最もサイズ (バイト単位) の大きいファイルを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="2d177-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
-   <span data-ttu-id="2d177-105">最もサイズ (バイト単位) の小さいファイルを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="2d177-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
-   <span data-ttu-id="2d177-106">指定したルート フォルダー配下のフォルダーから <xref:System.IO.FileInfo> オブジェクトの最大ファイルまたは最小ファイルを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="2d177-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
-   <span data-ttu-id="2d177-107">サイズが上位 10 番目までのファイルなど、一定の条件に該当するファイルを取得する方法。</span><span class="sxs-lookup"><span data-stu-id="2d177-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
-   <span data-ttu-id="2d177-108">指定サイズ未満のファイルを無視しながらバイト単位のサイズに基づいてファイルをグループ化する方法。</span><span class="sxs-lookup"><span data-stu-id="2d177-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d177-109">例</span><span class="sxs-lookup"><span data-stu-id="2d177-109">Example</span></span>  
 <span data-ttu-id="2d177-110">以下のコードでは 5 つのクエリを使用して、バイト単位のサイズに基づいてファイルを照会し、グループ化しています。</span><span class="sxs-lookup"><span data-stu-id="2d177-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="2d177-111">サンプル コードを参考にして、<xref:System.IO.FileInfo> オブジェクトが備えている他のさまざまなプロパティを簡単に照会することができます。</span><span class="sxs-lookup"><span data-stu-id="2d177-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```csharp  
class QueryBySize  
{  
    static void Main(string[] args)  
    {  
        QueryFilesBySize();  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    private static void QueryFilesBySize()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Return the size of the largest file  
        long maxSize =  
            (from file in fileList  
             let len = GetFileLength(file)  
             select len)  
             .Max();  
  
        Console.WriteLine("The length of the largest file under {0} is {1}",  
            startFolder, maxSize);  
  
        // Return the FileInfo object for the largest file  
        // by sorting and selecting from beginning of list  
        System.IO.FileInfo longestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len descending  
             select file)  
            .First();  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, longestFile.FullName, longestFile.Length);  
  
        //Return the FileInfo of the smallest file  
        System.IO.FileInfo smallestFile =  
            (from file in fileList  
             let len = GetFileLength(file)  
             where len > 0  
             orderby len ascending  
             select file).First();  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes",  
                            startFolder, smallestFile.FullName, smallestFile.Length);  
  
        //Return the FileInfos for the 10 largest files  
        // queryTenLargest is an IEnumerable<System.IO.FileInfo>  
        var queryTenLargest =  
            (from file in fileList  
             let len = GetFileLength(file)  
             orderby len descending  
             select file).Take(10);  
  
        Console.WriteLine("The 10 largest files under {0} are:", startFolder);  
  
        foreach (var v in queryTenLargest)  
        {  
            Console.WriteLine("{0}: {1} bytes", v.FullName, v.Length);  
        }  
  
        // Group the files according to their size, leaving out  
        // files that are less than 200000 bytes.   
        var querySizeGroups =  
            from file in fileList  
            let len = GetFileLength(file)  
            where len > 0  
            group file by (len / 100000) into fileGroup  
            where fileGroup.Key >= 2  
            orderby fileGroup.Key descending  
            select fileGroup;  
  
        foreach (var filegroup in querySizeGroups)  
        {  
            Console.WriteLine(filegroup.Key.ToString() + "00000");  
            foreach (var item in filegroup)  
            {  
                Console.WriteLine("\t{0}: {1}", item.Name, item.Length);  
            }  
        }  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the FileInfo.Length property.  
    // In this particular case, it is safe to swallow the exception.  
    static long GetFileLength(System.IO.FileInfo fi)  
    {  
        long retval;  
        try  
        {  
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
  
 <span data-ttu-id="2d177-112">このクエリは、完全な <xref:System.IO.FileInfo> オブジェクトを返すために、まずデータ ソース内の各ファイルを調べ、それらのファイルを Length プロパティの値で並べ替えています。</span><span class="sxs-lookup"><span data-stu-id="2d177-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="2d177-113">そうすることで、長さが最大である単一のファイルまたは一連のファイルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="2d177-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="2d177-114">リスト内の最初の要素は、<xref:System.Linq.Enumerable.First%2A> を使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="2d177-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="2d177-115">先頭から n 件の要素を取得するには、<xref:System.Linq.Enumerable.Take%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d177-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="2d177-116">並べ替え順序に Descending を指定することによって、最小の要素がリストの先頭に来るようにしています。</span><span class="sxs-lookup"><span data-stu-id="2d177-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="2d177-117">このクエリでは、`GetFiles` の呼び出しで <xref:System.IO.FileInfo> オブジェクトが作成された後に別のスレッドでファイルが削除された場合に発生する例外の可能性に対処するために、別途設けられたメソッドを呼び出してファイル サイズ (バイト単位) を取得しています。</span><span class="sxs-lookup"><span data-stu-id="2d177-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="2d177-118"><xref:System.IO.FileInfo> オブジェクトの作成後であっても、例外は発生する可能性があります。<xref:System.IO.FileInfo> オブジェクトは、<xref:System.IO.FileInfo.Length%2A> プロパティが最初にアクセスされたときに最新のサイズ (バイト単位) に基づいてそのプロパティを更新しようと試みるためです。</span><span class="sxs-lookup"><span data-stu-id="2d177-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="2d177-119">この操作をクエリの外側の try-catch ブロックに置くことで、"副作用の原因となりうるような操作はクエリ内では行わない" という原則に従っているのです。</span><span class="sxs-lookup"><span data-stu-id="2d177-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="2d177-120">一般に、アプリケーションが不明な状態に陥ることのないよう、例外を処理する際には十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="2d177-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2d177-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2d177-121">Compiling the Code</span></span>  
 <span data-ttu-id="2d177-122">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="2d177-122">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d177-123">参照</span><span class="sxs-lookup"><span data-stu-id="2d177-123">See Also</span></span>  
 [<span data-ttu-id="2d177-124">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="2d177-124">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="2d177-125">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="2d177-125">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
