---
title: '方法: 拡張子別にファイルをグループ化する (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 4b2200799a7623bf9d47540f922798f5161be1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="071cb-102">方法: 拡張子別にファイルをグループ化する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="071cb-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="071cb-103">この例では、LINQ を使用して、ファイルまたはフォルダーの一覧に対して、高度なグループ化および並べ替えを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="071cb-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="071cb-104">また、<xref:System.Linq.Enumerable.Skip%2A> メソッドと <xref:System.Linq.Enumerable.Take%2A> メソッドを使用して、出力をページごとにコンソール ウィンドウに表示する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="071cb-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="071cb-105">例</span><span class="sxs-lookup"><span data-stu-id="071cb-105">Example</span></span>  
 <span data-ttu-id="071cb-106">次のクエリは、指定されたディレクトリ ツリーの内容を、ファイル名の拡張子別にグループ化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="071cb-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="071cb-107">このプログラムの出力は、ローカル ファイル システムの詳細と `startFolder` の設定内容に応じて長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="071cb-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="071cb-108">すべての結果を確認できるように、次の例では、結果をページごとに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="071cb-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="071cb-109">同じ手法を Windows アプリケーションや Web アプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="071cb-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="071cb-110">このコードでは、グループ内の項目をページごとに処理するため、`foreach` ループを入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="071cb-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="071cb-111">また、一覧内での現在位置を計算し、ユーザーがページングを停止してプログラムを終了できるようにするロジックも追加されています。</span><span class="sxs-lookup"><span data-stu-id="071cb-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="071cb-112">この場合、ページング クエリは、元のクエリからキャッシュされた結果に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="071cb-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="071cb-113">LINQ to SQL などの他のコンテキストでは、このようなキャッシュは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="071cb-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="071cb-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="071cb-114">Compiling the Code</span></span>  
 <span data-ttu-id="071cb-115">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="071cb-115">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="071cb-116">参照</span><span class="sxs-lookup"><span data-stu-id="071cb-116">See Also</span></span>  
 [<span data-ttu-id="071cb-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="071cb-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="071cb-118">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="071cb-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
