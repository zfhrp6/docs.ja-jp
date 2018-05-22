---
title: '方法 : Visual Basic でファイルの名前を変更する'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: ef024f90567d8d69bdd432499db96e4f67578ce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="dfa15-102">方法 : Visual Basic でファイルの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="dfa15-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="dfa15-103">`My.Computer.FileSystem` オブジェクトの `RenameFile` メソッドは、現在の場所、ファイル名、および新しいファイル名を指定して、ファイルの名前を変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="dfa15-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="dfa15-104">このメソッドは、ファイルを移動する目的には使用できません。ファイルを移動して名前を変更するには、`MoveFile` メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="dfa15-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="dfa15-105">ファイル名を変更するには</span><span class="sxs-lookup"><span data-stu-id="dfa15-105">To rename a file</span></span>  
  
-   <span data-ttu-id="dfa15-106">`My.Computer.FileSystem.RenameFile` メソッドを使用して、ファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="dfa15-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="dfa15-107">この例では、 `Test.txt` というファイル名を `SecondTest.txt` に変更しています。</span><span class="sxs-lookup"><span data-stu-id="dfa15-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 <span data-ttu-id="dfa15-108">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="dfa15-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dfa15-109">コード スニペット ピッカーでは、スニペットは **[ファイル システム - ドライブ、フォルダー、およびファイルの処理]** にあります。</span><span class="sxs-lookup"><span data-stu-id="dfa15-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="dfa15-110">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfa15-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dfa15-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="dfa15-111">Robust Programming</span></span>  
 <span data-ttu-id="dfa15-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dfa15-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="dfa15-113">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="dfa15-114">`newName` にパス情報が含まれている (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="dfa15-115">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="dfa15-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="dfa15-116">`newName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="dfa15-117">ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="dfa15-118">`newName` で指定された名前のファイルまたはディレクトリが既に存在する (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="dfa15-119">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="dfa15-120">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="dfa15-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="dfa15-121">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="dfa15-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="dfa15-122">ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="dfa15-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa15-123">参照</span><span class="sxs-lookup"><span data-stu-id="dfa15-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [<span data-ttu-id="dfa15-124">方法: ファイルを移動する</span><span class="sxs-lookup"><span data-stu-id="dfa15-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [<span data-ttu-id="dfa15-125">ファイルおよびディレクトリの作成、削除、および移動</span><span class="sxs-lookup"><span data-stu-id="dfa15-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [<span data-ttu-id="dfa15-126">方法: ファイルのコピーを同じディレクトリに作成する</span><span class="sxs-lookup"><span data-stu-id="dfa15-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="dfa15-127">方法: ファイルのコピーを別のディレクトリに作成する</span><span class="sxs-lookup"><span data-stu-id="dfa15-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
