---
title: '方法: フォルダー内のテキスト ファイルの内容を照会する (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 4e421e1bdb5008816989c26b725faaf2b4ae8caf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="d93b6-102">方法: フォルダー内のテキスト ファイルの内容を照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d93b6-102">How to: Query the Contents of Text Files in a Folder (LINQ) (C#)</span></span>
<span data-ttu-id="d93b6-103">この例では、指定したディレクトリ ツリーに含まれるすべてのファイルを照会し、個々のファイルを開いて、その内容を調べています。</span><span class="sxs-lookup"><span data-stu-id="d93b6-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="d93b6-104">同様の手法を使えば、ディレクトリ ツリーの内容に対するインデックスや逆インデックスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="d93b6-105">この例で行っているのは単純な文字列検索です。</span><span class="sxs-lookup"><span data-stu-id="d93b6-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="d93b6-106">しかし正規表現を使うと、もっと複雑なパターン マッチングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d93b6-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="d93b6-107">詳細については、「[方法: LINQ クエリと正規表現を組み合わせる (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d93b6-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d93b6-108">例</span><span class="sxs-lookup"><span data-stu-id="d93b6-108">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took   
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d93b6-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d93b6-109">Compiling the Code</span></span>  
 <span data-ttu-id="d93b6-110">.NET Framework Version 3.5 以降を対象とするプロジェクトを作成します。System.Core.dll を参照設定し、System.Linq 名前空間と System.IO 名前空間を `using` ディレクティブで指定します。</span><span class="sxs-lookup"><span data-stu-id="d93b6-110">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d93b6-111">参照</span><span class="sxs-lookup"><span data-stu-id="d93b6-111">See Also</span></span>  
 [<span data-ttu-id="d93b6-112">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="d93b6-112">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [<span data-ttu-id="d93b6-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="d93b6-113">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
