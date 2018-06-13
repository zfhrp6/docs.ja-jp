---
title: '方法: Visual Basic でディレクトリにあるファイルのコレクションを取得する'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: c498928bd5fc58b8264e9098f49aabafc68c7fe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586560"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="2c368-102">方法: Visual Basic でディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="2c368-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="2c368-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> メソッドのオーバーロードは、ディレクトリ内のファイルの名前を表す、文字列の読み取り専用のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="2c368-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="2c368-104">指定されたディレクトリ内を検索し、サブディレクトリを検索しない単純なファイル検索には <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c368-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="2c368-105">検索に追加オプションを指定するには、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c368-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="2c368-106">`wildCards` パラメーターを使用して、検索パターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2c368-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="2c368-107">検索にサブディレクトリを含めるには、`searchType` パラメーターを <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType> に設定します。</span><span class="sxs-lookup"><span data-stu-id="2c368-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2c368-108">指定したパターンに一致するファイルがない場合は、空のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="2c368-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="2c368-109">ディレクトリ内のファイルをリストするには</span><span class="sxs-lookup"><span data-stu-id="2c368-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="2c368-110"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> メソッドのオーバーロードのいずれかを使用して、検索するディレクトリの名前とパスを `directory` パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="2c368-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="2c368-111">次の例では、ディレクトリ内のすべてのファイルが返され、`ListBox1` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c368-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2c368-112">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="2c368-112">Robust Programming</span></span>  
 <span data-ttu-id="2c368-113">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c368-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2c368-114">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2c368-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="2c368-115">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2c368-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="2c368-116">`directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="2c368-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="2c368-117">`directory` が既存のファイルを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2c368-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2c368-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="2c368-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="2c368-119">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="2c368-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="2c368-120">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="2c368-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="2c368-121">ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="2c368-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c368-122">参照</span><span class="sxs-lookup"><span data-stu-id="2c368-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [<span data-ttu-id="2c368-123">方法: 特定のパターンに一致するファイルを検索する</span><span class="sxs-lookup"><span data-stu-id="2c368-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [<span data-ttu-id="2c368-124">方法: 特定のパターンに一致するサブディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="2c368-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
