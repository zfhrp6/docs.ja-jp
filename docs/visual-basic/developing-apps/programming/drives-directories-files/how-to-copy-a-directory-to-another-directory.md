---
title: "方法 : Visual Basic でディレクトリを別のディレクトリにコピーする"
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
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
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
ms.openlocfilehash: 7bcc7f924d26247b0d0ab30a9ea0fc6d6333b652
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="4d777-102">方法 : Visual Basic でディレクトリを別のディレクトリにコピーする</span><span class="sxs-lookup"><span data-stu-id="4d777-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="4d777-103">ディレクトリを別のディレクトリにコピーするには、<xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d777-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="4d777-104">このメソッドでは、ディレクトリ自体とその内容がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="4d777-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="4d777-105">コピー先のディレクトリが存在しない場合は作成されます。</span><span class="sxs-lookup"><span data-stu-id="4d777-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="4d777-106">コピー先の場所に同じ名前のディレクトリが存在し、`overwrite` が `False` に設定されている場合は、2 つのディレクトリの内容がマージされます。</span><span class="sxs-lookup"><span data-stu-id="4d777-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="4d777-107">操作中に、ディレクトリに新しい名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="4d777-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="4d777-108">ディレクトリ内でファイルをコピーするとき、特定のファイルが原因で例外がスローされることがあります。たとえば、`overwrite` が `False` に設定されていて、マージ中に、既にファイルが存在する場合などです。</span><span class="sxs-lookup"><span data-stu-id="4d777-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="4d777-109">こうしてスローされた例外は、単一の例外に統合され、その `Data` プロパティにエントリが保持されます。それらのエントリでは、ファイルまたはディレクトリ パスがキーとなり、固有の例外メッセージがそれに対応した値に格納されます。</span><span class="sxs-lookup"><span data-stu-id="4d777-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="4d777-110">ディレクトリを別のディレクトリにコピーするには</span><span class="sxs-lookup"><span data-stu-id="4d777-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="4d777-111">`CopyDirectory` メソッドを使用し、コピー元とコピー先のディレクトリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="4d777-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="4d777-112">次の例では、`TestDirectory1` という名前のディレクトリを `TestDirectory2` にコピーし、既存のファイルは上書きします。</span><span class="sxs-lookup"><span data-stu-id="4d777-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     <span data-ttu-id="4d777-113">[!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4d777-113">[!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]</span></span>  
  
     <span data-ttu-id="4d777-114">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="4d777-114">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4d777-115">コード スニペット ピッカーでは、コード例は [**ファイル システム - ドライブ、フォルダー、およびファイルの処理**] にあります。</span><span class="sxs-lookup"><span data-stu-id="4d777-115">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="4d777-116">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d777-116">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4d777-117">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="4d777-117">Robust Programming</span></span>  
 <span data-ttu-id="4d777-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d777-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4d777-119">ディレクトリに指定された新しい名前にコロン (:) またはスラッシュ (\ または /) が含まれている (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-119">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4d777-120">次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-120">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4d777-121">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="4d777-121">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="4d777-122">`destinationDirectoryName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-122">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="4d777-123">ソース ディレクトリが存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-123">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="4d777-124">ソース ディレクトリがルート ディレクトリである (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-124">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4d777-125">パスを組み合わせると、既存のファイルと同じになる (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-125">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4d777-126">コピー元のパスとコピー先のパスが同じである (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-126">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4d777-127">`ShowUI` が `UIOption.AllDialogs` に設定されており、ユーザーが操作をキャンセルした、またはディレクトリ内の 1 つ以上のファイルをコピーできなかった (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-127">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="4d777-128">操作が循環している (<xref:System.InvalidOperationException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-128">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="4d777-129">パスにコロン (:) が含まれている (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-129">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="4d777-130">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-130">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="4d777-131">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-131">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="4d777-132">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="4d777-132">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4d777-133">コピー先のファイルは存在するが、アクセスできない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="4d777-133">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d777-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d777-134">See Also</span></span>  
 <span data-ttu-id="4d777-135"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="4d777-135"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A></span></span>   
 <span data-ttu-id="4d777-136">[方法: 特定のパターンに一致するサブディレクトリを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="4d777-136">[How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span></span>  
 [<span data-ttu-id="4d777-137">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="4d777-137">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

