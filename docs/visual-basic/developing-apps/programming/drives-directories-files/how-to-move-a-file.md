---
title: "方法: ファイルを移動する (Visual Basic)"
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
- files, moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5a2623ec7e440e8fdf85138cd0b3de9ab18b773c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="0ff84-102">方法: ファイルを移動する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ff84-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="0ff84-103">`My.Computer.FileSystem.MoveFile` メソッドは、ファイルを別のフォルダーに移動するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ff84-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="0ff84-104">ターゲットの構造が存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="0ff84-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="0ff84-105">ファイルを移動するには</span><span class="sxs-lookup"><span data-stu-id="0ff84-105">To move a file</span></span>  
  
-   <span data-ttu-id="0ff84-106">`MoveFile` メソッドを使用し、ソース ファイルおよびターゲット ファイル両方のファイル名と場所を指定して、ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="0ff84-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="0ff84-107">この例では、 `test.txt` という名前のファイルを `TestDir1` から `TestDir2`に移動します。</span><span class="sxs-lookup"><span data-stu-id="0ff84-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="0ff84-108">ソース ファイル名と同じでも、ターゲット ファイル名を指定することにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="0ff84-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     <span data-ttu-id="0ff84-109">[!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ff84-109">[!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]</span></span>  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="0ff84-110">ファイルを移動し、その名前を変更するには</span><span class="sxs-lookup"><span data-stu-id="0ff84-110">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="0ff84-111">`MoveFile` メソッドを使用してファイルを移動します。その際、ソース ファイルのファイル名と場所、ターゲットの場所、ターゲットの場所での新しい名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ff84-111">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="0ff84-112">この例では、 `test.txt` という名前のファイルを `TestDir1` から `TestDir2` に移動し、 `nexttest.txt`という名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="0ff84-112">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     <span data-ttu-id="0ff84-113">[!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0ff84-113">[!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0ff84-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="0ff84-114">Robust Programming</span></span>  
 <span data-ttu-id="0ff84-115">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0ff84-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="0ff84-116">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="0ff84-117">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="0ff84-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="0ff84-118">`destinationFileName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-118">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="0ff84-119">ソース ファイルが正しくないか、存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-119">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="0ff84-120">パスを組み合わせると既存のディレクトリと同じになる、移動先のファイルが既に存在し `overwrite` が `False`に設定されている、移動先ディレクトリにある同じ名前のファイルが使用中である、またはユーザーがファイルにアクセスするのに必要なアクセス許可がない (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-120">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="0ff84-121">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="0ff84-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="0ff84-122">`showUI` が `True`に設定され、 `onUserCancel` が `ThrowException`に設定されている状態で、ユーザーが操作をキャンセルしたか、または指定されていない I/O エラーが発生した (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-122">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="0ff84-123">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-123">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="0ff84-124">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="0ff84-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="0ff84-125">ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="0ff84-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff84-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ff84-126">See Also</span></span>  
 <span data-ttu-id="0ff84-127"><xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A></span><span class="sxs-lookup"><span data-stu-id="0ff84-127"><xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A></span></span>   
 <span data-ttu-id="0ff84-128">[方法: ファイルの名前を変更する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="0ff84-128">[How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span></span>  
 <span data-ttu-id="0ff84-129">[方法: ファイルのコピーを別のディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span><span class="sxs-lookup"><span data-stu-id="0ff84-129">[How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span></span>  
 [<span data-ttu-id="0ff84-130">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="0ff84-130">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

