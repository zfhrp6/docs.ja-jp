---
title: "方法: Visual Basic でファイルを削除する"
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.openlocfilehash: e4b0b87fd403556777e0ab5a1edd517687360374
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="37b5f-102">方法: Visual Basic でファイルを削除する</span><span class="sxs-lookup"><span data-stu-id="37b5f-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="37b5f-103">`My.Computer.FileSystem` オブジェクトの `DeleteFile` メソッドを使用すると、ファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="37b5f-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="37b5f-104">削除したファイルを**ごみ箱**に送るかどうか、ファイルを削除することをユーザーに確認するかどうか、ユーザーが操作をキャンセルした場合の処理方法などが、オプションとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="37b5f-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="37b5f-105">テキスト ファイルを削除するには</span><span class="sxs-lookup"><span data-stu-id="37b5f-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="37b5f-106">`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="37b5f-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="37b5f-107">次のコードは、`test.txt` という名前のファイルを削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="37b5f-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     <span data-ttu-id="37b5f-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="37b5f-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="37b5f-109">テキスト ファイルを削除して、ユーザーがファイルを削除することを確認するには</span><span class="sxs-lookup"><span data-stu-id="37b5f-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="37b5f-110">`showUI` を `AllDialogs` に設定し、`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="37b5f-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="37b5f-111">次のコードは、`test.txt` という名前のファイルを、ユーザーに削除するファイルを確認した上で削除する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="37b5f-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     <span data-ttu-id="37b5f-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="37b5f-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="37b5f-113">テキスト ファイルを削除してごみ箱に送るには</span><span class="sxs-lookup"><span data-stu-id="37b5f-113">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="37b5f-114">`recycle` パラメーターに `SendToRecycleBin` を指定し、`DeleteFile` メソッドを使用してファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="37b5f-114">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="37b5f-115">次のコードは、`test.txt` という名前のファイルを削除して**ごみ箱**に送る方法の例です。</span><span class="sxs-lookup"><span data-stu-id="37b5f-115">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     <span data-ttu-id="37b5f-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="37b5f-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="37b5f-117">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="37b5f-117">Robust Programming</span></span>  
 <span data-ttu-id="37b5f-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="37b5f-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="37b5f-119">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="37b5f-120">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="37b5f-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="37b5f-121">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="37b5f-122">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-122">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="37b5f-123">ファイルが使用中の場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-123">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="37b5f-124">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="37b5f-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="37b5f-125">ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-125">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="37b5f-126">ファイルの削除に必要なアクセス許可がユーザーにないか、またはファイルが読み取り専用である (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-126">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="37b5f-127">部分信頼の状況下で、必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-127">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="37b5f-128">ユーザーが操作を取り消し、`onUserCancel` が `ThrowException` に設定されている (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="37b5f-128">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b5f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="37b5f-129">See Also</span></span>  
 <span data-ttu-id="37b5f-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span><span class="sxs-lookup"><span data-stu-id="37b5f-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span></span>   
 <span data-ttu-id="37b5f-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="37b5f-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="37b5f-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span><span class="sxs-lookup"><span data-stu-id="37b5f-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span></span>   
 <span data-ttu-id="37b5f-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span><span class="sxs-lookup"><span data-stu-id="37b5f-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span></span>   
 [<span data-ttu-id="37b5f-134">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="37b5f-134">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

