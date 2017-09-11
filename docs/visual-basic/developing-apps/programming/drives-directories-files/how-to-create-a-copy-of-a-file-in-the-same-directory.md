---
title: "方法 : Visual Basic でファイルのコピーを同じディレクトリに作成する"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
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
ms.openlocfilehash: 7e15b85a72c9b2504551174f5b104bdbb01cf3f3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="d1164-102">方法 : Visual Basic でファイルのコピーを同じディレクトリに作成する</span><span class="sxs-lookup"><span data-stu-id="d1164-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="d1164-103">ファイルをコピーするには、`My.Computer.FileSystem.CopyFile` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1164-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="d1164-104">このパラメーターでは、既存のファイルの上書き、ファイルの名前変更、操作の進行状況の表示、ユーザーによる操作のキャンセルが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d1164-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="d1164-105">ファイルのコピーを同じフォルダーに作成するには</span><span class="sxs-lookup"><span data-stu-id="d1164-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="d1164-106">ターゲット ファイルと場所を指定し、`CopyFile` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1164-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="d1164-107">次の例では、`test2.txt` という `test.txt` のコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1164-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     <span data-ttu-id="d1164-108">[!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d1164-108">[!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="d1164-109">同じフォルダーにファイルのコピーを、既存のファイルを上書きして作成するには</span><span class="sxs-lookup"><span data-stu-id="d1164-109">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="d1164-110">ターゲット ファイルと場所を指定し、`overwrite` を `True` に設定して、`CopyFile` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1164-110">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="d1164-111">次の例では、`test2.txt` という `test.txt` のコピーを、既存のファイルをその名前で上書きして作成します。</span><span class="sxs-lookup"><span data-stu-id="d1164-111">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     <span data-ttu-id="d1164-112">[!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d1164-112">[!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d1164-113">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d1164-113">Robust Programming</span></span>  
 <span data-ttu-id="d1164-114">次の条件を満たす場合は、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1164-114">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="d1164-115">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d1164-116">システムが絶対パスを取得できなかった (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-116">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d1164-117">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="d1164-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d1164-118">ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d1164-119">結合したパスが、既存のディレクトリを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-119">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d1164-120">リンク先ファイルが存在し、`overwrite` が `False` に設定されている (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-120">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d1164-121">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-121">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d1164-122">同じ名前がターゲット フォルダー内のファイルで使用されている (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-122">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d1164-123">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-123">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d1164-124">`ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException`に設定され、ユーザーが操作をキャンセルしている (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-124">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="d1164-125">`ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定され、未指定の I/O エラーが発生する (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-125">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="d1164-126">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-126">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d1164-127">ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="d1164-127">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="d1164-128">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="d1164-128">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1164-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1164-129">See Also</span></span>  
 <span data-ttu-id="d1164-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="d1164-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="d1164-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span><span class="sxs-lookup"><span data-stu-id="d1164-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span></span>   
 <span data-ttu-id="d1164-132"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span><span class="sxs-lookup"><span data-stu-id="d1164-132"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span></span>   
 <span data-ttu-id="d1164-133">[方法: 特定のパターンを持つファイルをディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md) </span><span class="sxs-lookup"><span data-stu-id="d1164-133">[How to: Copy Files with a Specific Pattern to a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md) </span></span>  
 <span data-ttu-id="d1164-134">[方法: ファイルのコピーを別のディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span><span class="sxs-lookup"><span data-stu-id="d1164-134">[How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span></span>  
 <span data-ttu-id="d1164-135">[方法: ディレクトリを別のディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md) </span><span class="sxs-lookup"><span data-stu-id="d1164-135">[How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md) </span></span>  
 [<span data-ttu-id="d1164-136">方法: ファイルの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="d1164-136">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

