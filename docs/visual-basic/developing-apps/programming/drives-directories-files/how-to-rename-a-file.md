---
title: "方法 : Visual Basic でファイルの名前を変更する"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files, renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f003cfc7c7880a47515f7328a0503072f3b02cbf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="d18f5-102">方法 : Visual Basic でファイルの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="d18f5-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="d18f5-103">`My.Computer.FileSystem` オブジェクトの `RenameFile` メソッドは、現在の場所、ファイル名、および新しいファイル名を指定して、ファイルの名前を変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d18f5-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="d18f5-104">このメソッドは、ファイルを移動する目的には使用できません。ファイルを移動して名前を変更するには、`MoveFile` メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d18f5-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="d18f5-105">ファイル名を変更するには</span><span class="sxs-lookup"><span data-stu-id="d18f5-105">To rename a file</span></span>  
  
-   <span data-ttu-id="d18f5-106">`My.Computer.FileSystem.RenameFile` メソッドを使用して、ファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="d18f5-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="d18f5-107">この例では、 `Test.txt` というファイル名を `SecondTest.txt` に変更しています。</span><span class="sxs-lookup"><span data-stu-id="d18f5-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     <span data-ttu-id="d18f5-108">[!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d18f5-108">[!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]</span></span>  
  
 <span data-ttu-id="d18f5-109">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="d18f5-109">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d18f5-110">コード スニペット ピッカーでは、スニペットは [**ファイル システム - ドライブ、フォルダー、およびファイルの処理**] にあります。</span><span class="sxs-lookup"><span data-stu-id="d18f5-110">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="d18f5-111">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18f5-111">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d18f5-112">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d18f5-112">Robust Programming</span></span>  
 <span data-ttu-id="d18f5-113">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d18f5-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d18f5-114">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d18f5-115">`newName` にパス情報が含まれている (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-115">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d18f5-116">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="d18f5-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d18f5-117">`newName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-117">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d18f5-118">ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d18f5-119">`newName` で指定された名前のファイルまたはディレクトリが既に存在する (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-119">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d18f5-120">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d18f5-121">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="d18f5-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d18f5-122">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="d18f5-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d18f5-123">ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="d18f5-123">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18f5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d18f5-124">See Also</span></span>  
 <span data-ttu-id="d18f5-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A></span><span class="sxs-lookup"><span data-stu-id="d18f5-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A></span></span>   
 <span data-ttu-id="d18f5-126">[方法: ファイルを移動する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="d18f5-126">[How to: Move a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md) </span></span>  
 <span data-ttu-id="d18f5-127">[ファイルおよびディレクトリの作成、削除、および移動](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="d18f5-127">[Creating, Deleting, and Moving Files and Directories](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md) </span></span>  
 <span data-ttu-id="d18f5-128">[方法: ファイルのコピーを同じディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md) </span><span class="sxs-lookup"><span data-stu-id="d18f5-128">[How to: Create a Copy of a File in the Same Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md) </span></span>  
 [<span data-ttu-id="d18f5-129">方法: ファイルのコピーを別のディレクトリに作成する</span><span class="sxs-lookup"><span data-stu-id="d18f5-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)

